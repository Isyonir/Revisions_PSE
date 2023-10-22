# Les processus

## Généralités

Un processus est l'instance d'un programme qui est exécuté par un ou plusieurs threads (fils d'execution)

Il ne faut pas confondre un programme qui est le fichier présent sur le disque dur et qui contient les instructions d'execution et le processus qui est une instance en mémoire de ce programme.

Il peut s'exécuter soit en mode "kernel" (privilégié) et dans ce cas il a accès aux instructions privilégiées qui permettent notamment l'accès direct au matériel, soit en mode "user" dans ce cas, le processus est limité, et ne peut exécuter que ses propres instructions et il n'a pas accès direct au matériel.
Un processus exécuté en mode "user" peut passer en mode "kernel" pour exécuter certaines instructions.

La plage mémoire allouée pour chaque processus par l'OS est découpé en plusieurs parties. Leur nombre et leur arrangement peut dépendre de l'OS (Windows, Linux) et de la méthode de gestion mémoire utilisée (pagination ou segmentation).

On retrouve dans tous les cas:
 - Le stack (la pile) Variables locales
 - Le heap (le tas) Allocation dynamique de mémoire (Ex: Objet créé durant l'exécution)
 - Data: Contient les variables initialisées (Ex: int nb = 5;)
 - BSS: Contient les variables non initilisées (Ex: int nb;)
 - Text: Instructions du programme en mémoire 

 Exemple de la structure mémoire d'un processus sur un OS utilisant la segmentation
 
![Structure mémoire processus](../../images/processus_memoire.png)
 
Les processus possèdent ce que l'on appelle des "états".
 - Créé
 - Prêt: Le processus est chargé en mémoire et attend d'être exécuté par le CPU (scheduler)
 - En cours d'execution : Le processus est choisi par le scheduler et est exécuté
 - En attente : Le processus attend son tour pour être exécuté
 - Bloqué: Le processus attend quelque chose (Ex: Communication avec une imprimante, ou attente d'une saisie utilisateur)
 - Terminé: Le passage à l'état terminé se fait soit si le processus a fini de dérouler ses instructions, soit s'il a été "kill". Le processus ne s'exécute plus, mais est toujours présent en mémoire (processus zombie) jusqu'à ce que le processus parent l'ait enlevé de la table des processus.
 - Swapped out: Si le processus est en état "En attente" ou "Bloqué", il peut être déplacé dans le swap (partition ou fichier page.sys).
 
![Etats processus](../../images/processus_etats.png)

Un processus zombie est un processus toujours présent en mémoire mais qu ne s'exécute plus.
L'accumulation de processus zombies peut entraîner une pénurie de RAM, et donc un crash ou un ralentissement du système.
