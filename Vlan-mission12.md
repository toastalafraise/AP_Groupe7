
# Création des VLAN


## Proxmox 

sur l'interface du proxmox on vas sur :

Proxmox7 -> Network -> Create -> LinuxVlan  
.
![](https://media.discordapp.net/attachments/1313041657389781042/1313041657641304194/image.png?ex=674eb0d6&is=674d5f56&hm=3aab12f1d3f6e4aa67f373a9a62556a31d25fa98768ec18606974384c551ae5e&=&format=webp&quality=lossless)
.  
.

Dans l'interface de création dans name on inscrit le nom de notre brige point, le numéro du vlan souhaité

![](https://media.discordapp.net/attachments/1313041657389781042/1313043462320554014/image.png?ex=674eb284&is=674d6104&hm=e92251c00591ae1e1e1496faaf20f465d85fa9744ffee3af8fa51465281253d6&=&format=webp&quality=lossless&width=550&height=299)

.  
.  

### Mise en place dans le cadre de l'AP


![](https://media.discordapp.net/attachments/1313041657389781042/1313044940523049020/image.png?ex=674eb3e5&is=674d6265&hm=e518ce32d8fb4483731c09b5abaef3168c5d380ebba6f028ef586c06789a3423&=&format=webp&quality=lossless)

## switch

### Creation du port trunk
````
configure terminal
interface [fastethernet ou gigabitethernet] [numero de la carte / numero du port]
switchport mode trunk
no shutdown
exit
````
  
  ### Création des vlan
```` 
configure terminal	  	
vlan[numero du vlan]	  	
name [nom du vlan]	 	
exit
    ````
    


























