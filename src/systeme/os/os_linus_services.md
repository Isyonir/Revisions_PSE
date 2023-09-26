# Linux

## Gestion des services (ou daemon)

Un service est un exécutable ou un script qui est lancé en arrière plan en permanence.  
Quelques exemples:
- Un serveur Web
- Un gestionnaire de réseau
- ...

### System V (ancien système)

La gestion des services se fait par la commande "service".  

Avant systemd, Linux pouvait démarrer avec différents niveaux de fonctionnement (ou runlevel), l'OS ne démarrait que les services qui étaient activés pour le runlevel selectionné.  
Dans /etc/ il y a un répertoire par runlevel nommé rcX.d, dans ce répertoire, il y a des liens symboliques qui pointent vers les exécutables des services.  
Lors du lancement de l'OS, chaque exécutable est lancé l'un à la suite de l'autre.

Le rattachement d'un service à un runlevel peut se faire via la commande chkconfig.

