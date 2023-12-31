# Démarrage

## Différences GPT et MBR

### Le MBR
Master Boot Record

Il se situe tout au début du disque dur, d'une taille de 512 octets, il contient les informations sur la manière dont les blocks (ou secteurs) du disque sont organisés en partitions.
Il joue également le rôle de bootloader : c'est lui qui doit charger l'OS lors du démarrage.

La taille maximale qu'un MBR peut gérer est de 2 To.

L'organisation d'un MBR:
- Un bootstrap code qui est le code chargé de déterminer quelles partitions sont bootables, de les charger, et de les exécuter.
- Une table des partitions qui contient les informations sur la manière dont est partitionné le disque. Le MBR ne peut contenir des informations que sur 4 partitions au maximum. 

![Image mbr](../../images/mbr.jpg)

Pour augmenter le nombre de partitions possibles, on peut faire ce qu'on appelle des partitions étendues:
Dans une partition décrite dans le MBR, on va créer des "sous tables de partitions" qui décrivent l'arrangement de "sous-partitions". 

### Le GPT
GUID Partition Table

Permet de surpasser les limitations du MBR, et notemment la limitation de la taille maximale du disque (On passe de 2 To max à 75 Zo (Zettaoctet) max).
Le nombre maximal de partitions possibles est aussi augmenté : On passe de 4 à théoriquement illimité, mais en pratique on se limite en général à 128.

Structure d'un GPT
- Un MBR pour garantir la rétro-compatibilité avec les anciens systèmes
- Un header GPT qui contient différentes informations comme par exemple la version utilisée
- Une table des partitions, chaque partition possède notamment un GUID (Globally Unique Identifier) qui permet de savoir à quelle catégorie elle appartient (Par exemple : Une partition Microsoft réservée aura toujours pour GUID : "E3C9E316-0B5C-4DB8-817D-F92DF00215AE", ou encore : "933AC7E1-2EB4-4F13-B844-0E14E2AEF915" pour une partition /home de Linux)

A noter qu'il y a un second GPT (incluant le header et la table des partitions) qui est présent à la fin du disque, et ce afin de parer à une éventuelle corruption du premier.

![Image GPT](../../images/gpt.jpg)

