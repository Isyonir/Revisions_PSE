# Processus et mécanisme de communication 

### Algorithmes d'ordonnancement 

L'ordonnanceur est le composant du noyau du système d'exploitation qui décide de l'ordre d'exécution des processus sur le processeur d'un ordinateur.

Pour fonctionner, un processus a besoin de ressources processeur pour effectuer des calculs. Il abandonne cette ressource en cas d'interruption, etc. Certains processeurs (monocoeurs, monothread) ne peuvent exécuter qu'un seul traitement à la fois. Pour les autres processeurs un ordonnanceur est obligatoire pour déterminer quel processus sera effectué sur quel coeur du processeur (c'est la notion d'affinité, pour éviter la perte de performance). L'hyperthrading rend la question de l'ordonnancement encore plus complèxe puisqu'elle permet d'exécuter deux tâches par coeurs du processeur. 

A un instant T, il éxiste très souvent plus de processus à exécuter que de coeurs de processeur. 