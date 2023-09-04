# Processus et mécanismes de communication

### Signaux

Un signal est une forme de communication entre des processus utilisée par les systèmes unix et ceux qui respectent les standars POSIX.
Il s'agit d'une notification asynchrone envoyée à un processus pour lui signaler un événement.
Quand un signal est envoyé à un processus, le système d'exploitation interrompt son exécution. Si le processus possède une routine pour le signal reçu, il l'exécute sinon il exécute les routines par défaut.

La norme POSIX ainsi que la documentation de linux limitent les fonctions directement et indirectement appelables depuis cette routine de traitement des signaux.

Les exceptions comme les erreurs de segmentation ou les divisions par zéro génèrent des signaux. Ici les signaux générés seront respectivement SIGSEGV et SIGFPE. Un processus recevant ces signaux se terminera et générera un core dump par défaut.
Cette norme donne une liste exhaustive de fonctions primitives dites async-signal safe (en pratique les appels systèmes) qui sont les seules à pouvoir être appelées depuis une routine de traitement de signal sans avoir un comportement indéfini.
Le noyau peut générer des signaux pour notifier les processus que quelque chose s'est passé. Par exemple, SIGPIPE est envoyé à un processus qui essaye d'écrire dans un pipe qui a été fermé par celui qui lit. Par défaut, le programme se termine alors. Ce comportement rend la construction de pipeline en shell aisée.