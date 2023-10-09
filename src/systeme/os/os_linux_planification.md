# Linux

## Planification des tâches avec "at"
Il est possible de planifier une commande pour qu'elle s'exécute une seule fois à un instant T grâce à la commande at 

```
at [OPTION...] heure/date
```
Une fois la commande lancée, elle exécute son shell ou il faut renseigner la commande à lancer puis quitter avec CTRL + D 

Il est possible de renseigner les formats de temps sous les formats suivants : 
- Une heure spécifique de la journée : On peut préciser le temps sous le format HH:MM. Si l’heure spécifiée est déjà passée, alors la tâche est exécutée le lendemain à la même heure
- Un indicateur de temps : il existe des mots-clés reconnus qui peuvent être utilisés pour désigner l’heure comme noon (12:00), midnight (00:00), ou teatime (16:00)
- Un jour spécifique : pour planifier une tâche spécifique à plus de 24H, il faut ajouter une date sous la forme MMDDYY, MM/DD/YY, ou DD.MM.YY.
- Une période spécifique dans un futur proche : Il est possible de préciser la période avec les mots-clés now, ou le signe + suivi de la période.

Il est possible de lister les tâches en attente avec la commande 
```
atq
at -l
```

Pour supprimer une tache il faut exécuter la commande 
```
atrm <id_de_la_tache>
```
L'ID s'obtient en listant les tâches.

## Planification des tâches avec Crontab

Pour planifier des tâches, on utilise l'utilitaire crond.  
Les tâches planifiées sont placées dans le dossier /etc/cron.d/ pour les tâches système et /var/spool/cron pour les tâches créés par la commande crontab.
Les fichiers crontab doivent être des fichiers clssiques, et ne doivent pas être exécutables ou en écriture sauf pour le propriétaire.

L'ajout de tâches se fait via la commande "crontab -e".  
On peut spécifier les utilisateurs qui ont le droit ou non de créer des tâches planifiées via la présence de deux fichiers "/etc/cron.deny" et "/etc/cron.allow".  

- Fichier cron.deny seul : Système de blacklist, les utilisateurs qui ne sont **pas** dans ce fichier peuvent créer des tâches
- Fichier cron.allow seul : Système de whitelist, les utilisateurs qui ne sont **pas** dans le fichier ne peuvent **pas** créer de tâches
- Aucun des deux fichiers n'existe : Seul root peut créer des tâches

Les tâches lancées sont lancées dans un nouveau shell, les alias ne sont donc pas forcément connus : (Ex un ll pourrait ne pas fonctionner dans une crontab)  
On peut créer une crontab pour un autre utilisateur via la commande crontab -u USER -e.  
La commande crontab -l permet de lister les tâches (pour l'utilisateur courant)

Exemple d'affichage de la commande crontab -e

```
# COMMANTAIRE
 .---------------- Minutes (0 - 59)
 |  .------------- Heures (0 - 23)
 |  |  .---------- Jour du mois (1 - 31)
 |  |  |  .------- Mois (1 - 12) OU jan,feb,mar,apr ...
 |  |  |  |  .---- Jour de la semaine (0 - 6) (Dimanche = 0 ou 7) OU sun,mon,tue,wed,thu,fri,sat
 |  |  |  |  |
 *  *  *  *  *  utilisateur Commande à exécuter
```
On peut utiliser les notations suivantes :
- X-Y : De X à Y
- */X : Tous les X
- X, Y : X et Y
- @daily : Tous les jours à 00:00
- @weekly : Tous les DImanches à 00:00
- @monthly : Tous les premiers jours du mois à 00:00
- @yearly : Tous les premiers jours du mois de janvier à 00:00
- @ reboot : Au prochain redémarrage

Attention, si l'on précise le jour du mois et le jour de la semaine en même temps, on peut avoir des effets de bord.  

