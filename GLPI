Mise en place de GLPI avec docker: 

Crée un dossier pour GLPI: 
mkdir -p /opt/glpi && cd /opt/glpi

Crée un fichier docker-compose.yml: 
nano docker-compose.yml


Et y mettre ceci: 
--------------------------------------------------------------------------------------------
version: '3.8'

services:
  db:
    image: mariadb:10.5
    container_name: glpi-db
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: rootpassword
      MYSQL_DATABASE: glpi
      MYSQL_USER: glpi
      MYSQL_PASSWORD: glpipassword
    volumes:
      - db_data:/var/lib/mysql

  glpi:
    image: diouxx/glpi
    container_name: glpi
    restart: always
    depends_on:
      - db
    ports:
      - "8081:80"  # ⚠️ Attention : on évite 8080 car Zabbix l'utilise déjà
    environment:
      TIMEZONE: Europe/Paris
    volumes:
      - glpi_data:/var/www/html

volumes:
  db_data:
  glpi_data:
----------------------------------------------------------------------------------------------------

Maintenant lancer le conteneur avec la commande: docker compose up -d

Aller dans votre navigateur web et entre @ip:8081

Ensuite lors de l'installation de glpi vous devez :


Etape 1

serveur sql: db
uilisateur sql: glpi
mot de passe sql: glpipassword

etape 2 : selectyionner la base de données glpi

etape 3 : ok 

etape 4 : continuer 

etyape 5 : continuer 

etape 6 : utiliser glpi 

Connectez vous : id et mdp : glpi 



Installation du plugin fusion inventory :

Etape 1:
Entrer tout d'abord dans le contenur de glpi avec la commande 

Entrer dans le conteneur glpi à l'aide de la commande docker docker exec -t glpi /bin/bash


Etape 2: 
Télécharger le paquets : wget https://github.com/glpi-project/glpi-inventory-plugin/releases/download/1.3.4/glpi-glpiinventory-1.3.4.tar.bz2 pour s'assuré de la comptabilité avec la version de glpi en 10.0.18


Etape 3:
Il faut extraire le fichier avec la commande : tar -xjf glpi-glpiinventory-1.3.4.tar.bz2

Etape 4:
Il faut maintenant déplacer vos ficher dans le dossier mv glpiinventory /var/www/html/plugins/

Etape 5:
Changer les permissions avec la commande : chown -R www-data:www-data /var/www/html/plugins/glpiinventory

Etape 6:
Aller dans GLpi et dans plugins et activer votre plugins

