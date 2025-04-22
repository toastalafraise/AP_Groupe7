- Créer un utilisateur avec la commande adduser (utilisateur victor mdp sio2024)

FTP: 

- Installation de vsftpd avec la commande apt install vsftpd
- Lancer le serveur avec la commande systemctl start vsftpd
- Démarrer le serveur a chaque lancement avec la commande systemctl enable vsftpd
- Installer ufw avec la commande apt install ufw
- Ouvrir les ports 20 et 21 de notre serveur avec la commande ufw allow 20 ou 21
-Copier votre fichier de configuration en cas de problème cp /etc/vsftpd.conf
/etc/vsftpd.bak
-Modifier votre fichier de configuration nano /etc/vsftpd.conf
-Modifier les lignes : - anonymous_enable=NO
- locale_enable=YES
- write_enable=YES
- pam_service_name=vsftpd
Ne surtout pas modifier la ligne« listen=NO » car elle peut entrainer des erreurs par la suite sur le serveur
- Ajouter notre utilisateur à la liste de vsftp avec la commande echo "victor" | tee-a /etc/vsftpd.userlist

Source : https://www.youtube.com/watch?v=6LNibes6lWQ&feature=youtu.be


Lamp:

Mettez a jour les paquets de votre machine
- Installer le avec la commande apt install –y apache2
- Vérifier son installation avec la commande systemctl status apache2
- Attribuer les droits d’écriture lecture et d’exécution a victor sur le chemin /var/www
- Il faut créer le groupe dev avec la commande addgroup dev
- Ajouter victor a notre groupe avec la commande usermod -aG dev victor
-Rendre le groupe dev propriétaire du chemin /var/www/html avec la commande chown -R:dev /var/www/html3
-Donner les droits de lecture et exécution au groupe avec la commande chmod -R 777 /var/www/html
- Modifier la racine poruque chaque dev accède directement au chemin /var/www pour faire ceci aller dans le fichier nano /etcpasswd et modifier la racine de la ligne victo
- Mettre en place des permissions sur le chemin html avec la commande chmod –R
775 /var/www/html
- chown –R www-data:www-data /var/www/html
-Aller dans le fichier nano/apache2/apache2.conf
-Aller jusqu’à cette ligne et configurer cette partie :

<Directory />
  Options Indexes FollowSymLinks
  AllowOveriide None
  Require all granted
</Directory>
-Relancer le serveur aache avec la commande systemctl restart apache 2
- Ajouter un fichier index.html dans le dossier /var/www/html
- Aller sur internet votre adresse IP et vous verrez votre site mis en route


phpmyadmin :

Pour installer phpmyadmin vous devez:
- Installer mariadb (SyMariaDB est un système de gestion de base de données édité sous licence
GPL. Il s'agit d'un embranchement communautaire de MySQL) grâce à la commande apt install
mariadb-server mariadb-client
- Installer Php grâce a la commande apt install phpmyadmin apache2 php-zip php-gd php-
json php-curl libapache2-mod-php
- Configurer un mot de passe sur votre mariadb pour le sécuriser, pour faire ceci entrer la
commande: - mysql –u root –p ensuite entrer les commandes SQL suivantes :
◦ - Use mysql;
◦ - SET PASSWORD FOR 'root'@'localhost' = PASSWORD(‘Mot2pass’)
◦ - flush privileges; ( prendre en compte les modifications)
Configurer le site phpMyAdmin grâce au commande :
◦ s /etc/phpmyadmin/apache.conf /etc/apache2/conf-available/phpmyadmin.conf
◦ a2enconf phpmyadmin.conf
Redémarrer le service grâce à la commande systemctl reload apache2.service
- Aller dans votre base de donnée mariadb et créer l'utilisateur dev avec la commande CREATE USER 'dev'à'%' IDENTIFIED BY 'Sio2024';
- Donner les droits d'accés avec la commande GRANT ALL PRIVILEGES ON *.* TO 'dev'@'%' WITH GRANT OPTION;
- Aller sur le site  http://@ip/phpmyadmin/index.php 
