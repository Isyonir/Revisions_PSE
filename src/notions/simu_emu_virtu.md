# Simulation, Emulation et Virtualisation

## La simulation  : 
La simulation, en général, est une représentation fictive de la réalité. Il s’agit d’imiter une situation.
En informatique la simulation passe par un logiciel qui calcule et prédit donc les évènements qui pourraient se produire, un exemple avec Cisco Packet Tracer qui permet de simuler
un réseau et les echanges entre les différents périphériques réseau comme les routeurs, switchs, hubs et terminaux. 

## L'émulation : 
L'émulation n'a pas pour but de simuler mais de reproduire à l'identique le comportament d'un logiciel et de son architecture matériel.
Un exemple simple est l'émulation de console de jeu sur un ordinateur ou le comportement de la console et du jeu est reproduit sur l'ordinateur.

En informatique on peut retrouver des émulateurs réseaux comme GNS3 qui permet d'émuler le fonctionnement de plusieurs périphériques comme les switchs, firewalls...

## La virtualisation : 
La virtualisation reprend les concepts de l'émulation à la différence ou la virtualisation utilise l'architecture du système hôte alors que l'émulation la recréée de façon 
logicielle. 

Il existe deux type de virtualisation : 
  - La virtualisation de niveau 1 : Un hyperviseur (logiciel responsable de la virtualisation et du fonctionnement des machines virtuelles) est directement installé sur le matériel.
Ce qui est le cas pour les serveur VMware esxi.
  - La virtualisation de niveau 2 : L'hyperviseur est installé directement sur la machine hôte, comme pour virtualbox ou Hyper-V pourles serveurs Windows.
