# La mémoire

## Hiérarchie de la mémoire

![Schéma hiérarchie mémoire](../../images/memoire_hierarchie.png)

- Les registres : Mémoire utilisée par le processeur pour effectuer ses opérations
- Mémoire cache : Mémoire intermédiaire entre la RAM et les registres, en général elle permet de stocker les données dont les registres vont avoir besoin.
- Mémoire centrale : Aussi appelée mémoire primaire, il s'agit de la RAM, elle contient en mémoire les données essentielles à l'exécution de différents processus de la machine
- Mémoire secondaire : Elle correspond au stockage de masse couremment utilisé : Disque dur ou SSD
- Mémoire tertiaire : Stockage utilisé pour l'archivage  : Bande magnétiques

| Type de mémoire    | Taille                                               | Vitesse d'accès                                            |
|--------------------|------------------------------------------------------|------------------------------------------------------------|
| Registres          | 8 octets par registre (16 pour certains)             | 1 cycle de CPU                                             |
| Mémoire cache      | L0 : 6Ko, L1 : 128ko, L2 : 1Mo, L3 : 6Mo, L4 : 128Mo | L1 : 700Go/s, L2 : 200Go/s, L3 : 100Go/s, L4 : 40 Go/s     |
| Mémoire primaire   | Dans les Go                                          | DDR3 : 10Go/s, DDR4 : 20 à 30 Go/s, DDR5 : Jusqu'à 50 Go/s |
| Mémoire secondaire | Dans les To                                          | HDD : Jusqu'à 200 Mo/s, SSD : Jusqu'à 5 Go/s               |
| Mémoire tertiaire  | De 10 à 500 To                                       | 160 à 400 Mo/s                                             |

## L'accès à la mémoire

L'accès à la mémoire se fait via les bus :
- le bus de contrôle (système) permet au processeur de communiquer avec les différents périphériques
- le bus d'adresse est celui dans lequel sera spécifié l'adresse mémoire qui doit être chargée ou écrite
- le bus de données est celui par lequel les données transitent

![Schéma bus](../../images/memoire_bus.png)

### Le MMU
Memory Management Unit

Composant présent en général dans le processeur, c'est lui qui est en charge de "traduire" les adresses mémoire virtuelles en adresses réelles.  

![Schéma MMU](../../images/materiel_mmu.png)

### Le DMA
Direct Memory Access

Permet à un périphérique d'accéder directement à la mémoire primaire (RAM) sans passer par le processeur.  
Cele permet d'éviter de surcharger le processeur.


## Mémoire virtuelle

La mémoire virtuelle permet de faire abstraction du matériel.
L'OS attribue aux processus des adresses mémoire virtuelles qui sont ensuite traduites par le matériel en adresses mémoire physiques.

Le MMU (Memory Management Unit) est le matériel qui est responsable de la traduction adresse virtuelle vers adresse physique.
Il se réfère pour cela à une table.

La mémoire virtuelle allouée au processus se fera toujours de manière contigue (toutes les adresses se suivent), alors que ce n'est pas le cas sur la mémoire physique (On peut avoir des "blocs" de mémoire d'un même processus dispersés sur la RAM) 

L'avantage de la mémoire virtuelle est qu'on peut donner l'illusion que le système possède plus de mémoire vive qu'il n'en a.
Pour cela, il suffit de faire correspondre une plage d'adresse virtuelle à une plage d'adresse physique présente sur un disque dur.

Un autre intérêt est que la mémoire virtuelle permet d'implémenter tout ce qui est en rapport avec la sécurité d'accès à la mémoire.
Avant l'utilisation de la mémoire virtuelle, tous les processus qui tournaient sur une machine pouvaient avoir accès à toutes les adresses mémoires physiques de la machine, ce qui représentait un risque de sécurité et de stabilité.

![Image mémoire virtuelle](../../images/memoire_virtuelle.jpg)

La mémoire virtuelle peut être implémentée de deux façons:

### Pagination mémoire

La mémoire physique est découpée en "frames" de même taille arbitraire, tandis que la mémoire virtuelle est découpée en "pages" de la même taille que les "frames".
Le MMU associe les pages de mémoires virtuelles aux frames de mémoire physique dans une table des pages.

Pour avoir l'adresse physique d'une donnée dans une page, on a besoin du couple: 
Numéro de frame + Offset (déplacement)

![Image pagination](../../images/pagination.jpeg)


### Segmentation mémoire

La mémoire physique est divisée en segments de tailles variables. Ces segments en général correspondent à des groupes logiques d'informations (Ex: Les différentes régions mémoire d'un processus "Text", "Data" ...).

**A la différence de la pagination**, où la taille des frames et des pages est d'une longueur fixe arbitraire, **la taille des segments correspondent à la taille réelle des données à stocker** à l'intérieur, ce qui permet d'économiser de la mémoire.

Pour avoir l'adresse physique d'une donnée, on a besoin du couple:
Numéro de segment + Offset (déplacement)

![Image segmentation](../../images/processus_memoire.png)

### Différences entre pagination et segmentation

| Pagination                                            | Segmentation                                                                |
|-------------------------------------------------------|-----------------------------------------------------------------------------|
| La taille des pages est fixe                          | La taille des segments dépend de celle des données à stocker                |
| Géré par l'OS                                         | Géré par le compilateur                                                     |
| Plus rapide                                           | Plus lent                                                                   |
| Les pages doivent avoir la même taille que les frames | Pas de contraintes                                                          |
| On perd un peu d'espace en RAM                        | Pas de perte d'espace : la taille des segments dépend des données à stocker |
|                                                       |                                                                             |

Linux utilise la pagination pour gérer la mémoire.

### Big et Little Endian

Le concept d'endianness désigne l'organisation en mémoire d'une information sur plusieurs octets:
- Pour le big endian : l'octet de poids **fort** est situé à l'**adresse mémoire la plus petite**
- Pour le little endian : l'octet de poids **faible** est situé à l'**adresse mémoire la plus petite**

Ex :
```
Pour une donnée de 4 octets dont la valeur est : 0x0A0B0C0D
                                                   |     |
                                                   |     |
                      Octet de poids fort ---------+     |
                    Octet de poids faible ---------------+

| Adresse en mémoire | 0x01 | 0x02 | 0x03 | 0x04 |
|--------------------|------|------|------|------|
| Little endian      | 0D   | 0C   | 0B   | 0A   |
| Big endian         | 0A   | 0B   | 0C   | 0D   |
```
Dans les architectures modernes (x86-64) les données sont stockées sous le format de little-endian.


