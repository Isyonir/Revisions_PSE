# Démarrage

## Différences entre BIOS et UEFI

### BIOS
Basic Input/Output System
Il a deux rôles principaux:
- Assurer le démarrage de la machine
- Fournir des services à l'OS sous la forme d'interruptions

Les interruptions du BIOS sont des "fonctions" que l'OS peut appeler pour interagir directement avec le matériel de manière basique sans avoir besoin de pilotes spécifiques.

 Cependant, les interruptions ne sont plus utilisées par les OS de nos jours à cause de plusieurs raisons:
 - Les interruptions ne peuvent s'exécuter que si le processeur est en mode réel. Dans le cas d'un appel à une interruption, il faut donc : Passer du mode protégé au mode réel, exécuter l'interruption, repasse en mode protégé, ce qui est long.
 - Le BIOS étant lent, le temps d'exécution de ces interruptions est trop élevé pour une utilisation pratique dans un OS moderne.
 - Les interruptions peuvent dépendre du BIOS utilisé, certines fonctionnalités peuvent changer d'un constructeur à un autre, et leur implémentation peut parfois être buggée

### UEFI
Unified Extensible Firmware Interface

Remplace le BIOS dans les machines "modernes" (années 2000)
Il a les même rôles que le BIOS, mais contrairement à lui, il possède plusieurs avantages:
- Possibilité de booter sur un disque utilisant une table de partitions GPT
- Possibilité d'utiliser une interface graphique dans les menus de l'UEFI
- Le processeur n'est pas limité au mode réel, et peut donc tourner en 32 ou 64 bits
- La programmation de l'UEFI peut se faire en C (contrairement au BIOS qui est écrit en assembleur)
- Il possède un shell utilisable

L'UEFI offre des fonctions appelées "services" qui peuvent être appelées par l'OS.

Une fonctionnalité bien connue de l'UEFI est le Secure Boot qui permet d'empêcher le chargement de bootloaders d'OS non signés. Ce qui avait à l'époque posé des soucis pour les distributions Linux.
