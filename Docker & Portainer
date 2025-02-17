Installation manuelle de Docker Engine & Docker compose (docker-compose-plugin v2)

Installation de Docker Engine & Docker-compose-plugin v2.

Installation de Docker sur Debian 12.

Il existe plusieurs façons d’installer Docker sur votre système Debian 12.

Il est disponible dans les dépôts officiels de Debian, où il peut être facilement installé avec une seule commande APT.

Cependant, un inconvénient de cette approche est que la version disponible n’est pas toujours la plus récente.

Pour cette raison, je vais vous montrer comment installer Docker sur Debian 12 à partir du dépôt officiel de Docker.

Cette approche garantit que vous obtenez toujours la dernière version à jour et que vous recevrez automatiquement toutes les futures mises à jour logicielles dès qu’elles seront disponibles.

Rappel sur la commande sudo, si celle-ci n'est pas installée :

su - root
apt install sudo
usermod -aG sudo cyberlitech
init 6

Étape 1 : Installer les composants requis.

Tout d’abord, exécutez les deux commandes ci-dessous pour mettre à jour l’index du package et installer les composants requis nécessaires pour ajouter et utiliser un nouveau référentiel HTTPS.

sudo apt update
sudo apt install apt-transport-https ca-certificates curl gnupg

Étape 2: Ajouter la clé GPG Repo de Docker.

Ensuite, importez la clé du dépôt Docker GPG dans votre système Debian.

Cette fonction de sécurité garantit l’authenticité du logiciel que vous installez.

curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker.gpg

Étape 3 : Ajouter le dépôt Docker à Debian 12.

Après avoir importé les clés GPG, nous ajouterons le dépôt officiel Docker à notre système Debian 12.

Cela implique que le package de mise à jour sera disponible avec le reste des mises à jour régulières de votre système si une nouvelle version est publiée.

echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker.gpg] https://download.docker.com/linux/debian bookworm stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

Comme pour la commande précédente, son exécution ne produit aucune sortie.

Ensuite, actualisez la liste des packages.

sudo apt update

Réception de :2 https://download.docker.com/linux/debian bookworm InRelease [43,3 kB]
Réception de :5 https://download.docker.com/linux/debian bookworm/stable amd64 Packages [11,9 kB]

Nous pouvons voir que notre nouveau référentiel Docker est maintenant disponible et prêt à être utilisé.
Étape 4 : Installer Docker sur Debian 12 (Bookworm).

Pour installer la dernière version de Docker sur Debian, exécutez la commande ci-dessous.

sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin

Cela installe les composants Docker suivants :

    docker-ce : Le moteur Docker lui-même.
    docker-ce-cli : Un outil de ligne de commande qui vous permet de parler au démon Docker.
    containerd.io : runtime de conteneur qui gère le cycle de vie du conteneur.
    docker-buildx-plugin : Un plugin CLI qui étend la version Docker avec de nombreuses nouvelles fonctionnalités.

C’est tout! Docker devrait maintenant être installé; Le service a démarré et activé pour démarrer automatiquement au démarrage.

En outre, vous pouvez vérifier l’état du service Docker à l’aide des éléments suivants :

sudo systemctl is-active docker

Étape 5 : Vérifier l’installation de Docker.

Vérifions maintenant si tout fonctionne correctement avec notre nouvelle installation Docker.

sudo docker version

sudo docker compose version

Nous allons exécuter une application simple appelée « hello-world ».

sudo docker run hello-world

lien du tuto : https://github.com/0xCyberLiTech/Docker/blob/main/DOCKER-et-DOCKER-COMPOSE-Installation-manuelle.md

Installation de Portainer : 
docker run -d -p 9000:9000 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock portainer/portainer-ce

Pour accéder a portainer entrer @IP/9000

Id : admin mdp : Thomasski-11

lien du tuto: https://github.com/0xCyberLiTech/Docker/blob/main/PORTAINER-Installation-manuelle.md
