Mise en place et configuration d’un environnement serveur FTP et LAMP avec gestion des droits automatisée

Ce guide présente les étapes détaillées pour configurer un environnement serveur complet, incluant un serveur FTP sécurisé avec vsftpd, un serveur web LAMP, l’interface de gestion phpMyAdmin, ainsi que l'automatisation des droits pour l'utilisateur Victor, garantissant un environnement stable, sécurisé et adapté aux besoins de développement.
1. Création de l'utilisateur

Création de l'utilisateur Victor avec un mot de passe sécurisé :

adduser victor
# Mot de passe : sio2024

2. Configuration du serveur FTP (vsftpd)

Étapes d'installation et de configuration :

    Installation de vsftpd :

apt install vsftpd

    Lancement et activation au démarrage :

systemctl start vsftpd
systemctl enable vsftpd

    Sécurisation avec le pare-feu UFW :

apt install ufw
ufw allow 20/tcp
ufw allow 21/tcp

    Sauvegarde du fichier de configuration :

cp /etc/vsftpd.conf /etc/vsftpd.bak

    Modification du fichier de configuration :

nano /etc/vsftpd.conf

Modifier les lignes suivantes :

anonymous_enable=NO
local_enable=YES
write_enable=YES
pam_service_name=vsftpd

⚠️ Ne pas modifier la ligne listen=NO pour éviter des erreurs au démarrage du service.

    Ajout de l'utilisateur à la liste autorisée :

echo "victor" | tee -a /etc/vsftpd.userlist

3. Mise en place du serveur LAMP
3.1. Installation d’Apache

    Mettre à jour les paquets :

apt update && apt upgrade

    Installer Apache :

apt install -y apache2

    Vérifier le service :

systemctl status apache2

3.2. Gestion des droits et utilisateurs

    Attribuer les droits d’accès à Victor sur /var/www :

addgroup dev
usermod -aG dev victor
chown -R :dev /var/www/html
chmod -R 775 /var/www/html

    Changer le propriétaire web par défaut pour sécuriser :

chown -R www-data:www-data /var/www/html

    Modifier le chemin racine de l’utilisateur Victor (optionnel) :

nano /etc/passwd

Changer le répertoire personnel pour /var/www.

    Configurer Apache :

nano /etc/apache2/apache2.conf

Ajouter ou modifier le bloc suivant :

<Directory />
  Options Indexes FollowSymLinks
  AllowOverride None
  Require all granted
</Directory>

    Redémarrer Apache :

systemctl restart apache2

    Créer un fichier index.html pour tester le site :

echo "<h1>Site Web en ligne</h1>" > /var/www/html/index.html

Accéder au site via : http://<votre_ip_local>
4. Installation et configuration de phpMyAdmin
4.1. Installation de MariaDB et PHP

apt install mariadb-server mariadb-client
apt install phpmyadmin apache2 php-zip php-gd php-json php-curl libapache2-mod-php

4.2. Sécurisation de MariaDB

mysql -u root -p

Commandes SQL à entrer :

USE mysql;
SET PASSWORD FOR 'root'@'localhost' = PASSWORD('Mot2pass');
FLUSH PRIVILEGES;

4.3. Intégration de phpMyAdmin à Apache

cp /etc/phpmyadmin/apache.conf /etc/apache2/conf-available/phpmyadmin.conf
a2enconf phpmyadmin.conf
systemctl reload apache2.service

Accès à l’interface : http://<votre_ip_local>/phpmyadmin
4.4. Création d’un utilisateur base de données pour Victor

CREATE USER 'dev'@'%' IDENTIFIED BY 'Sio2024';
GRANT ALL PRIVILEGES ON *.* TO 'dev'@'%' WITH GRANT OPTION;

5. Script d’automatisation des permissions

Pour garantir que chaque modification ou ajout dans /var/www/html attribue automatiquement les bons droits à l’utilisateur Victor et au groupe dev, un script d’automatisation peut être mis en place avec inotify-tools :
Exemple de script (à adapter) :

#!/bin/bash
# Script à lancer en tâche de fond
inotifywait -m -r -e create,modify /var/www/html |
while read path action file; do
  echo "Fichier modifié : $file"
  chown victor:dev "$path$file"
  chmod 775 "$path$file"
done

Rendez-le exécutable :

chmod +x /usr/local/bin/auto_permission.sh

Et lancez-le au démarrage via crontab ou un service systemd.

Ce guide permet de mettre en place une infrastructure serveur robuste et sécurisée, avec des services FTP et LAMP opérationnels, tout en facilitant le travail des développeurs grâce à des droits gérés automatiquement.

Source : https://thomas-portfolio.fr/TP-Mise%20en%20place%20d%E2%80%99une%20architecture%20serveur.pdf
