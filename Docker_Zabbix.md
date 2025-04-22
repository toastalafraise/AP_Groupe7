 ZABBIX installation depuis (Docker + Docker compse) de (Zabbix version 6.4.4 + agent-zabbix).

Pour l’installation de Zabbix avec Docker, nous allons utiliser un fichier docker-compose.yml, les containers suivants y seront déclarés :

    Le serveur Zabbix.
    La base de données (MariaDB).
    L’interface Web.
    Un agent de supervision pour le serveur Zabbix.

Prérequis :

Cette procédure a été testée depuis une machine sous (Debian 12) avec Docker, Docker compose v2 et Portainer.

Vous trouverez ici un tutoriel sur l’installation de Docker, Docker compose v2 & Portainer.

    Installation manuelle de Docker Engine et Docker-compose-plugin v2, disponible ici

    Installation manuelle de Portainer, disponible ici

Sur votre serveur, créer un dossier, qui va recevoir une copie des fichiers du dépôt et les données de Zabbix.

    Avant de commencer il fau installer et configurer (NTPsec).

Installer et configurer (NTPsec)

Création du dossier ~/zabbix/.

mkdir ~/zabbix/

cd ~/zabbix/

Aller dans ce dossier, entrer la commande ci-dessous pour récupérer les fichiers nécessaires à l'installation de Zabbix :

sudo git clone https://git.rdr-it.io/docker/zabbix.git .

Avant de récupérer les images et de les démarrer, je vous conseille de modifier les mots de passe pour la base MariaDB.

Aller dans le dossier (env_vars/) qui contient les différents fichiers de configuration.

cd env_vars

Éditer les fichiers (.MYSQL_PASSWORD) et (.MYSQL_ROOT_PASSWORD) changer par un mot de passe personnalisé.

Remonter d’un niveau dans les dossiers pour retourner où se trouve le fichier docker-compose.yml.

cd ..

Télécharger les différentes images :

sudo docker compose pull

Lancer les conteneurs pour démarrer Zabbix.

Pour le premier démarrage, je vous conseille de ne pas détacher l’exécution des conteneurs afin d’avoir le retour dans le terminal, pour cela ont démarré les conteneurs sans l’option -d.

Entrer la commande suivante :

sudo docker compose up

Le meilleur moyen de savoir si tout a fonctionné maintenant et d’essayer d’aller sur Zabbix depuis un navigateur.

Identifiant de connexion par défaut :

Admin / zabbix

Pour accéder a zabbix @IP:8080

Lien du tuto: https://github.com/0xCyberLiTech/Zabbix/blob/main/ZABBIX-installation-depuis-Docker-Docker-compse-de-Zabbix-version-6.4.4-agent-zabbix.md
