Mise en place du user admin avec la commande:
adduser admin 
mot de passe sio2024

1) Installation du serveur:
- apt update
- apt install tftpd-hpa

démarrage automatique du serveur
- systemctl enable tftpd-hpa
- systemctl status tftpd-hpa pour vérifier son état 

2) Configuration du serveur TFTP
- nano /etc/default/tftpd-hpa
- Mettre ses valeurs:
https://private-user-images.githubusercontent.com/187489439/396019535-241cb4b5-dc45-4bf4-abd8-26cd2b0eeb48.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MzQzMzgyNjIsIm5iZiI6MTczNDMzNzk2MiwicGF0aCI6Ii8xODc0ODk0MzkvMzk2MDE5NTM1LTI0MWNiNGI1LWRjNDUtNGJmNC1hYmQ4LTI2Y2QyYjBlZWI0OC5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjQxMjE2JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI0MTIxNlQwODMyNDJaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT05NTI4YWExOTE4M2JlNzE5Y2EzMzg5MGVkNTk3NjUzZWY5MzY3MTdkYjg0MDMxNjI3NTY3Mzc1MTk1Zjg4NzMzJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.Pa6Qerbbkeof7mPGjGoLzm9M2QNa0b_IWVQIL_eOBLI
- On définit les droits chown -R admin:admin /srv/tftp
                        chmod -R 700 /srv/tftp
- On redémarre le serveur avec la commande systemctl restart tftpd-hpa
- on test en faisant tftp @IP


Lien du tuto: https://fr.linux-console.net/?p=29370
