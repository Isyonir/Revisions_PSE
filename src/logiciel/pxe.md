# Boot PXE et déploiement par le réseau 

## Le PXE

Le PXE (pour Preboot eXecution Environment) est un protocole de démarrage réseau qui permet à un ordinateur local de démarrer à partir de données sur un serveur distant au lieu
de démarrer depuis des ressources locales comme un disque dur ou une clé USB. 

Le PXE est surtout utilisé pour déployer des postes de travail à partir du réseau, l'avantage de cette méthode est le gain de temps et la possibilité d'automatiser la 
configurationdes ordinateurs. 

Pour que le PXE fonctionne, il faut un serveur DHCP. Lorsqu'un ordinateur démarrer en mode réseau, il va demander une adresse IP au serveur DHCP. Ce dernier va répondre avec 
une adresse IP ainsi que la configuration du réseau, notamment l'adresse du serveur PXE. L'ordinateur va envoyer au serveur PXE une demande de boot PXE, le serveur répond en 
fournissant les fichiers necessaires pour le démarrage du système.

![Démarrage-PXE](https://github.com/Isyonir/Revisions_PSE/assets/143949453/5e0653dc-07a2-469d-9a05-b4baa8b4d5ed)


L'image envoyée par le serveur PXE peut correspondre à un système d'exploitation ou à un environnement de démarrage tel que WinPE qui est l'environnement de pré-installation de 
Windows.

Sous windows Serveur, le service WDS (Windows Deployment Service) s'occupe du role de serveur PXE, avec WDS il est possible d'installer des systèmes d'exploitation. Pour imager un ordinateur, il faut utiliser MDT (Microsoft Deployment Toolkit) qui permet d'automatiser la création, de façon personnalisée, d'un OS.
Sous linux, FOG est une solution open source pour cloner/imager un système afin de le deployer sur d'autres machines. FOG s'occuper aussi de partitionner, formatter les disques,
d'ajouter les ordinateur dans un domaine, d'installer des paquets ou même d'éxecuter des scripts.
