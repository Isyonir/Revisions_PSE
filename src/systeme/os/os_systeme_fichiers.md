# Système de fichiers

Un système de fichiers est une façon de stocker des informations et de les organiser dans des fichiers sur une mémoire secondaire (disque dur, SSD, clé USB).  

Il assure un certain nombre de rôles:
- Le système de fichiers met à disposition de l'OS une API qui permet d'exécuter différentes actins telles que : L'ouverture d'un fichier, la lecture, l'écriture, la suppression, ...
- Gestion de l'espace : les fichiers étant de taille différente et cette taille pouvant être dynamique, il alloue à chaque fichier un nombre variable de granules de mémoire secondaire de taille fixe (blocs).
- Localisation des fichiers : Pour cela chaque fichier possède un nombre d'informations descriptives (nom, adresse, ...)
- Contrôle de l'accès aux fichiers : Il peut permettre de mettre en place des règles qui permettent de restreindre l'accès, la modification, etc à certains utilisateurs ou groupes
- Maintien de l'intégrité : Il doit permettre le maintien de l'intégrité des fichiers en cas d'évènement extérieur (média retiré pendant l'écriture, coupure de courant, plantage de l'OS)

## Structure interne d'un système de gestion de fichiers

On prend içi pour exemple un système de fichiers fonctionnant sour Linux

### Superbloc

Il contient:
- le nom du système de fichiers
- La taille des blocs de données
- Le nombre, et la liste des blocs libres
- Le nombre et la table des inodes

### Table des inodes

Référence l'inode de tous les fichiers présents sur le disque, chaque inode contient différentes informations (métadonnées):
- Propriétaire
- Groupe
- Type du fichier
- Droits
- Dates de modification, création, accès
- Nombre de liens
- Adresse sur le disque
- Taille du fichier

### La zone de blocs de données

Zone dans laquelle se trouvent les données.

![Schéma systeme de fichiers](../../images/schema_systeme_fichiers.png)

## Quelques exemples de systèmes de fichiers

### Systèmes journalisés
Ces systèmes enregistrent les modifications dans un journal avant de les effectuer sur les fichiers (un peu comme un WAL postgresql). On peut donc récupérer des modifications qui étaient en cours mais pas enregistrées dans le cas d'une coupure de courant par exemple.

- ext3
- ext4
- NTFS
- xfs

### Systèmes non journalisés
- FAT 12 16 ou 32
- exFAT
- ext et ext2

### Réseau
- nfs
