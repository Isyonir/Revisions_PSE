# La mémoire

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

![Image mémoire virtuelle](./images/memoire_virtuelle.jpg)

La mémoire virtuelle peut être implémentée de deux façons:

### Pagination mémoire

La mémoire physique est découpée en "frames" de même taille, tandis que la mémoire virtuelle est découpée en "pages" de la même taille que les "frames".
Le MMU associe les pages de mémoires virtuelles aux frames de mémoire physique dans une table des pages.

Pour avoir l'adresse physique d'une donnée dans une page, on a besoin du couple: 
Numéro de frame + Offset (déplacement)

![Image pagination](./images/pagination.jpeg)


### Segmentation mémoire

La mémoire physique est divisée en segments de tailles variables. Ces segments en général correspondent à des groupes logiques d'informations (Ex: Les différentes régions mémoire d'un processus "Text", "Data" ...).
A la différence de la pagination, où la taille des frames et des pages est d'une longueur fixe arbitraire, la taille des segments correspondent à la taille réelle des données à stocker à l'intérieur, ce qui permet d'économiser de la mémoire.

Pour avoir l'adresse physique d'une donnée, on a besoin du couple:
Numéro de segment + Offset (déplacement)

En pratique, les techniques de pagination et de segmentation sont utilisées de façon conjointe.

### La Pagination segmentée

Le programme est découpé en segments. Chaque segment contient une table de pages, et chaque page dans ces tables contient l'adresse d'une frame.

![Image pagination segmentee](./images/pagination_segmentee.png)



