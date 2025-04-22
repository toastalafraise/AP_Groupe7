Mise en place d’un serveur NAS pour la sauvegarde des données sensibles de l’hôpital

Dans le cadre de la sécurisation et de la centralisation des données sensibles et des configurations du système informatique de l’hôpital, un serveur NAS (Network Attached Storage) a été mis en place à l’aide de la solution OpenMediaVault (OMV).
1. Préparation et installation du serveur NAS

Configuration matérielle et logicielle :

    Utilisation de l’image ISO OpenMediaVault version 6.5.

    Ajout de trois disques durs SATA de 25 Go chacun pour la configuration d’un RAID 5.

    Installation et configuration initiale de la machine.

    Connexion à l’interface d’administration via un navigateur en saisissant l’adresse IP suivante : 192.168.110.8.

2. Configuration du RAID 5

Étapes de mise en œuvre :

    Accéder à l’interface OMV > Stockage > Disques : s’assurer que tous les disques sont bien détectés.

    Aller dans RAID logiciel, créer un nouveau RAID 5 en sélectionnant les trois disques SATA.

    Vérifier que le RAID 5 est bien opérationnel.

3. Configuration du système de fichiers

Création et montage du système de fichiers :

    Se rendre dans Stockage > Systèmes de fichiers, créer un système de fichiers au format EXT4, puis le monter.

    Créer les dossiers partagés nécessaires à l'organisation des données.

Activation des services de partage :

    Activer le protocole SAMBA pour le partage de fichiers sur le réseau.

    Associer les dossiers partagés au service SAMBA afin de les rendre accessibles aux utilisateurs autorisés.

4. Gestion des utilisateurs

Création et attribution des droits :

    Ajouter les différents utilisateurs via l’interface OMV.

    Attribuer à chacun les dossiers appropriés et les droits d’accès correspondants (lecture, écriture, etc.).

5. Vérification et test d’accès

Procédure de test :

    Depuis un poste client, ouvrir l’explorateur de fichiers et saisir l’adresse IP du serveur NAS.

    Se connecter avec les identifiants d’un utilisateur créé.

    Vérifier l’accès aux dossiers partagés, créer un fichier test.

Recommandation :

    Créer des raccourcis vers les dossiers partagés directement sur les bureaux des utilisateurs pour faciliter l’enregistrement des fichiers.

6. Mise en place d’un serveur FTP

Afin de permettre un accès distant sécurisé aux fichiers du NAS, un serveur FTP est également configuré.

Configuration du service FTP :

    Installer l’extension openmediavault-ftp via l’interface OMV.

    Accéder à Services > FTP et activer le serveur FTP.

    Associer les dossiers partagés au service FTP.

    Redémarrer la machine OMV (recommandé en cas de problèmes liés au service FTP).

7. Automatisation des sauvegardes

Utilisation de Rsync :

    Aller dans Services > Rsync.

    Créer une tâche de sauvegarde automatisée :

        Définir le ou les dossiers sources.

        Spécifier le dossier de destination principal.

        Configurer la fréquence de la tâche (quotidienne, hebdomadaire, etc.).

Sources : https://thomas-portfolio.fr/Chap%209%20Sauvegarde%20NAS%20Thomas%20G.pdf
          https://thomas-portfolio.fr/Backup%20Thomas%20Grzesinski.pdf
          
