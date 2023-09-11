# Processus

## Synchronisation

### Data Race

Une Data Race survient quand une donnée partagée est accédée par au moins deux threads dont au moins un en écriture et ce, sans synchronisation.
Dans ce cas, il peut y avoir modification de la donnée par un des deux processus alors qu'elle est déjà utilisée par un autre.
Une des conséquences peut être le mauvais fonctionnement du programme (bugs) 

La synchronistion doit gérer les problématiques suivantes:

- L'exclusion mutuelle (mutual exclusion): Un seul processus à la foit peut avoir accès à la ressource, les autres doivent attendre que la resource soit libérée avant de pouvoir l'utiliser
- L'interbloquage (deadlock): Plusieurs processus attendent à l'infini que le processus qui utilise la ressource la libère, entraînant un arrêt du programme.
- La famine (starvation): Un processus n'arrive pas à avoir accès à la ressource dont il a besoin (la ressource se fait tout le temps bloquer par un nouveau processus)
- L'inversion de priorité: Un processus A de basse priorité est en cours d'exécution, et acquiert la ressource. L'ordonnanceur passe la main à un processus de haute priorité B qui veut la même ressource.  Ce dernier ne peut pas l'acquérir, car A la possède déjà, mais A ne sera pas appelé par le scheduler, car il est de priorité plus basse que B. B est donc bloqué.
- L'attente active (busy waiting): Un processus retente fréqument d'acquérir la ressource tant que celle-ci est déjà acquise, ce qui consomme du temps processeur, et donc ce qui relentit le système.

 Les principales implémentations de synchronisation:

| Méthode                | Description                                                                                                                                                                                                                                                                                   | Avantages                                                             | Inconvénients                                                                                                 |
|------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------|
| Spinlock               | Basé sur l'attente active (chaque processus vérifie de façon périodique si il peut accéder à la ressource)                                                                                                                                                                                    | Simple à mettre en oeuvre (une boucle while infinie suffit)           | Consomme du temps de calcul du processeur pour rien                                                           |
| Verrou (lock ou mutex) | A chaque fois qu'un processus utilise la ressource, il acquiert ce qu'on appelle un verrou. Lorsque un processus veut accéder à la ressource, il vérifie si le verrou est libre, si ce n'est pas le cas, il attend. Une fois que le processus qui a la ressource a fini, il libère le verrou. | Simple à mettre en oeuvre (on a juste à créer une variable booléenne) | Peut mener à du deadlock si le processus oublie de libérer le verrou. Peut mener à une inversion de priorité. |
| Sémaphore              | Mécanisme qui repose sur les signaux. Une sémaphore peut autoriser plus d'un processus à accéder à une ou plusieurs ressources.                                                                                   |                                                                       |                                                                                                               |
 
 
### Race condition

Un autre challenge que la synchronisation doit aider à surmonter est la situation de compétition (race condition).
Dans le cas où plusieurs threads d'un même processus s'exécutent en parallèle, l'ordre de complétion des threads n'est pas défini à l'avance.
Cela peut conduire à un comportement erroné du programme (Le thread B s'exécute avant le thread A alors qu'il avait besoin de lui pour faire quelquechose vant son exécution)

Une des manières pour remédier aux race condition sont les barrières:

Une barrière est définie pour un groupe de threads. Chaque thread de ce groupe doit attendre à la barrière le temps que les autres threads du groupe y soient aussi avant de pouvoir continuer.
Il peut y avaoir plusieurs barrières les unes à la suite des autres.
L'inconvénient majeur est le ralentissement de l'exécution du programme, à chaque fois les threads doivent s'attendre entre eux avant de pouvoir continuer leur exécution.
