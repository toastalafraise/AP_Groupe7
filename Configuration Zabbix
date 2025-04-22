Accéder au Zabbix sur internet avec l'IP 192.168.110.7:8080

Nous allons maintenant configuré nos hôtes :

Configuration d'un agent Zabbix sur Windows : 
  - Sur la machine Windows
    - Installer l'agent zabbix windows direcement sur le site Zabbix   https://cdn.zabbix.com/zabbix/binaries/stable/7.2/7.2.5/zabbix_agent-7.2.5-windows-amd64-openssl.msi
    - Sur votre machine démarrer l'agent zabbix et renseigné l'adresse IP sur votre serveur de monitoring
    - Retourner sur votre zabbix aller dans "Monitoring -> Hosts"
    - Ajouter un hôte
    - En modèles choisissez Windows by Zabbox Agent
    - En agent mettez l'IP de l'adresse Cliente

Configuration d'un agent Zabbix sur une machine Linux :
  - Installer l'agent apt insall zabbix-agent
  - Aller dans le fichier nano /etc/zabbix/zabbix_agentd.conf
  - Mettre l'IP du Zabbix 
  - Retourner sur votre zabbix aller dans "Monitoring -> Hosts"
  - Ajouter un hôte 
  - En modèles choisissez Zabbix agent
  - Mettre en agent l'adresse IP de la machine cliente

Configuration d'un SNMP sur un Windows Server :
  - Aller dans le gestionaire des services du serveur Windows et ajouter le service SNMP
  - Aller ensuite dans les services de votre ordinateur
  - Mettez en communauté public et l'adresse IP du serveur
  - Retournez sur Zabbix
  - Il faudra mettre en modèles Windows by SNMP
  - Mettre l'adresse IP de la machine cliente
  - En version de SNMP SNMPv2
  - Communauté SNMP {$SNMP_COMMUNITY}
  - Dans Macro il faudra mettre public 

Configuration d'un agent Zabbix sur pfSense : 
  - Aller dans les paquets le service SNMP
  - Configuré la communauté public
  - Retournez sur zabbix
  - Il faudra mettre en modèle PFSense by SNMP
  - Mettre l'adresse IP du pfSense
  - Mettre la version 2 de SNMP
  - SNMP community public


Configuration d'un SNMP sur un switch ou router
  - Aller sur votre switch
  - configure terminal
  - Vérifier la configuration SNMP de votre SWITCH CISCO : show running-config 
  - Activié la communauté à l'aide la commande snmp-server community public RO
  - Activez les traps SNMP à l'aide de la commande snmp-server enable traps ?
  - Activez les traps SNMP grâce à l a comande snmp-server enable traps <traps>
  - Et il faudra choisir la destination et la communauté à l'aide de la commande "snmp-server host 192.168.110.7 public"
  - exit
  - write memory
  - Configuré sur Zabbix
  - Choisissez en modèles Cisco IOS by SNMP
  - Mettre en SNMP l'IP du switch
  - Mettre la version 2 de SNMP
  - En communauté public


Confiugration de la messagerie SMTP
  - Sur votre adresse adresse mail activé le 2FA et il vous faudra configuré un mot de passe d'applications
  - Sur la machine Zabbix installer le service de messagerie
  - apt install ssmtp
  - Ensuite aller dans le fichier  nano /etc/ssmtp/ssmtp.conf
  - root = votre mail
    mailhub=smtp.gmail.com:465
    hostname=debian12
    FromLineOverride=YES
    AuthUser=votre mail
    AuthPass= votre mot de passe d'application
    useTLS= YES
  - Retourner sur zabbix et ensuite aller dans Administration
  - Media types
  - Email
  - Name Email
    SMTP server smtp.gmail.com
    SMTP server port 465
    SMTP helo debian12
    SMTP email votre mail
    Connection security SSL/TLS
    Authentication Username
    Username votre mail
    Password : mot de passe d'applications
    - Effectué un test
    - Sur la version actuel de Zabbix la création de script n'est plus possible


Sources : https://thomas-portfolio.fr/Supervision.pdf
