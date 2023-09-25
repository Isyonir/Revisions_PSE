# Linux

## Planification des tâches

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
 .---------------- minute (0 - 59)
 |  .------------- hour (0 - 23)
 |  |  .---------- day of month (1 - 31)
 |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...
 |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7) OR sun,mon,tue,wed,thu,fri,sat
 |  |  |  |  |
 *  *  *  *  *  user command to be executed
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

