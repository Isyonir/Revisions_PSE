# Processus et mécanisme de communication 

### Multitâche préemptif

Le multitâche préemptif désigne la capacité d'un système d'exploitation à exécuter ou arrêter une tâche planifiée en cours.

Un ordonnance préemptif possède une meilleure réactivité du système cependant un problème se pose lors de situation de compétition, c'est à dire quand plusieurs processus veulent accéder à une même ressource.
Dans un système d'exploitation multitâche préemptif, les processus ne peuvent s'exécuter pour une durée non définie. Le système accorde une quantité de temps définie à chaque processus, si le processus n'est pas terminé dans le temps accordé, le processus est alors renvoyé dans la pile pour laisser place au processus suivant dans la file d'attente qui est à son tour exécuté par le proesseur. Ce droit de préemption peut aussi survenir avec des interruptions matérielles.

Certaines tâches peuvent posséder une priorité, une tache peut aussi être spécifié comme préemptible ou non préemptible. Une tâche préemptible peut être suspendue (état "ready") au profit d'une tâche à priorité élevée ou d'une interruption. Avec une priorité élevée, le processus a droit à plus de temps et l'attente dans la file est plus courte.

Au fur et à mesure de l'évolution des systèmes d'exploitation, les concepteurs ont quitté la logique binaire "préemptible/non préemptible" au profit de systèmes plus fins de priorités multiples. Le principe est conservé, mais les priorités des programmes sont échelonnées.

Pendant la préemption, l'état du processus (drapeaux, registres et pointeurs d'instruction) est sauvé dans la mémoire. Il doit être rechargé dans le processeur pour que le code soit exécuté à nouveau : c'est la commutation de contexte.

Un système d'exploitation préemptif conserve en permanence la haute main sur les tâches exécutées par le processeur, contrairement à un système d'exploitation non préemptif, ou collaboratif, dans lequel c'est le processus en cours d'exécution qui prend la main et décide seul du moment où il la rend. L'avantage le plus évident d'un système préemptif est qu'il peut en permanence décider d'interrompre un processus, principalement si celui-ci échoue et provoque l'instabilité du système.

