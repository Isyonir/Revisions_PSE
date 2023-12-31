# Sauvegarde et restauration 

## Notions 

Le but de la sauvegarde est de se protéger des pertes de données volontaires ou accidentelles. Il ne faut pas confondre sauvegarde et archivage.

Il éxiste plusieurs types de sauvegardes : 
  - Totale (full) : Une sauvegarde complète (autrement dit de tout ce qui est dans les répertoires listés).
  - Différencielle : Une sauvegarde qui inclut tous les fichiers modifiés depuis le lancement de la dernière sauvegarde complète (Full).
  - Incrementale : Une sauvegarde qui inclut tous les fichiers modifiés depuis le lancement de la dernière sauvegarde complète (Full), différentielle, ou incrémentale.

Sur linux il existe plusieurs logiciels pour faire de la sauvegarde, voici quelques exemples :  

## RSYNC 

Rsync est un logiciel de synchronisation de fichiers. c'est-à-dire qu'il synchronise, copie ou actualise les données d'une source (locale ou distante) vers une destination 
locale ou distante) en ne transférant que les octets des fichiers qui ont été modifiés. 
Rsync utilise le SSH par défaut.

Rsync est hautement personnalisable, il est possible d'exclure des dossiers ou des fichiers avec "--exclude="fichier" mais aussi avec un fichier qui contient ce qui est à 
exclure : "--exclude-from=fichier_exclusion"
Ce fichier pourra ressembler à ceci : 
```
tmp
.Trash
.cache
```


Exemple de commande : 

``` 
rsync -az source/ test@serveur.org:/destination/
```
Dans cet exemple, on copie du dossier source/ en local vers un serveur avec l'utilisateur test vers le dossier /destination/
-a permet d'activer le mode "archive", qui permet d'avoir la récursivité et de sauvegarder pratiquement tout. 
-z (ou --ompress) permet de compresser les données lors du transfert, le processeur sera plus utilisé, mais le réseau sera moins utilisé. Cette option n'est pas très utile 
en réseau local avec un bon débit


### Bacula 
Bacula est un logiciel open source de sauvegarde professionnel. Il permet de sauvegarder le contenu d'un PC (ou serveur), ou plusieurs PC en réseau.
La configuration de Bacula se fait via un fichier de conf, dans ce dernier il est possible de renseigner les dossiers a sauvegarder, les fichiers à ne pas sauvegarder, la fréquence des sauvegardes, leur durée de rétention ainsique leur types.
Bacula est différent de Rsync, Rsync va faire une copie exacte des ficheiers et prend uniquement la version la plus récente. Bacula fonctionne avec une base de données pour avoir des informations supplémentaires sur les fichiers et dossiers. Ainsi il est possible de gérer plusieurs version d'un même fichier. Ce qui est assez utile quand un fichier a été modifié mais non supprimé, et que l'on souhaite revenir à une version antérieure. 


