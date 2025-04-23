Configuration requise
1. Création de routes statiques sur le routeur physique

Afin de permettre au pare-feu de communiquer avec le réseau distant via une passerelle, vous devez configurer deux routes statiques sur votre routeur physique :

ip route 192.168.110.0 255.255.255.0 192.168.207.1  
ip route 192.168.207.0 255.255.255.0 192.168.110.0

2. Configuration du pare-feu pfSense

    Création et assignation du VLAN

        Accédez à Interfaces > Assignments.

        Créez un nouveau VLAN et associez-le à l’interface LAN.

        Activez l’interface VLAN nouvellement créée et attribuez-lui une adresse IP correspondant au sous-réseau du VLAN.

    Ajout d’une passerelle par défaut

        Accédez à System > Routing.

        Ajoutez une nouvelle passerelle par défaut pointant vers 192.168.207.254.

    Définition d’une route statique

        Toujours dans System > Routing > Static Routes, ajoutez une route vers le sous-réseau du VLAN en utilisant comme passerelle 192.168.207.254.

    Configuration du NAT sortant (Outbound NAT)

        Rendez-vous dans Firewall > NAT > Outbound.

        Créez une règle NAT pour permettre l’accès Internet depuis le VLAN via l’interface WAN.

    Ajout de règles de pare-feu

        Allez dans Firewall > Rules.

        Sur l’interface VLAN, créez une règle autorisant la communication vers l’ensemble du réseau.
