# Linux

## Gestion des disques

### Le partitionnement

Représentation:
- Disques : /dev/hda ou /dev/sda
- Partitions : /dev/sda1, /dev/sda2

La partitionnement : Création de régions sur la mémoire secondaire, c'est la première chose que l'on fait avant le formatage.  
Chaque partition est considérée comme étant un disque logique par l'OS.

On utilise la commande parted pour gérer le partitionnement

### Le formatage
C'est l'action d'installer un système de fichiers spécifique sur une partition, on utilise pour cela la commande mkfs

### Le montage
Le but est de rattacher une partition formatée au système de fichiers de l'OS.  
Pour ça on attache la racine ("/") de la partition à un répertoire du système de fichiers déjà actif.

Pour la gestion du montage, on utilise les commandes mount et umount.  
A noter que lors d'un reboot, les montages sont perdus.

Pour les pérénniser, on doit modifier le fichier /etc/fstab:
```
    .-------------------------------------- Partition à monter
    |         .---------------------------- Point de montage (Répertoire dans lequel sera monté la partition)
    |         |      .--------------------- Système de fichiers
    |         |      |     .--------------- Options de montage supplémentaires
    |         |      |     |     .--------- Dump du système de fichier , 1 = oui , 0 = non
    |         |      |     |     | .------- Ordre de vérification du système de fichiers lots du boot
    |         |      |     |     | |
/dev/sda1 /mnt/disk xfs defaults 1 2
```

![Schéma montage](../../images/os_linux_montage.png)
