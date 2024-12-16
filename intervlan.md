# Création des vlan#


````
switch# vlan [numero du vlan]
switch(config)# name [nom du vlan]
switch(config)# exit
switch#interface fa[numero du port]
switch(config-if)#switchport mode trunk 
switch(config-if)#no shutdown
````

````
router#interface gigabit [numero du port]
router(config-if)#no shutdown

router#interface gigabit [numero du port].[numero de la sous interface]
Router(config-subif)#encapsulation dot1Q [numero du vlan de preference]
Router(config-subif)#ip address [ip gataway] [masque]
Router(config-subif)#no shutdown

````
