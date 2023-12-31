# Linux

## La gestion des utilisateurs

La configuration des utilisateurs est basée sur 3 fichiers :
- /etc/passwd : Liste des utilisateurs
- /etc/group : Liste des groupes d'utilisateurs
- /etc/shadow : Informations sur les mots de passe

Seul root peut modifier ces fichiers

UID : Numéro d'identifiant d'utilisateur
GID : Numéro d'identifiant de groupe

Différents types d'utilisateurs :
- Privilégiés : UID = 0
- Système : UID entre 200 et 999
- Standard : UID entre 1000 et 60 000

Structure du fichier /etc/passwd :
```
  .------------------------------------------------ Login
  |  .--------------------------------------------- Ancien champ plus utilisé qui contenant le mot de passe
  |  |   .----------------------------------------- UID
  |  |   |   .------------------------------------- GID du groupe primaire
  |  |   |   |      .------------------------------ Commentaire
  |  |   |   |      |          .------------------- Répertoire de connexion
  |  |   |   |      |          |          .-------- Chemin du shell utilisé
  |  |   |   |      |          |          |
  |  |   |   |      |          |          |
karl:x:1242:700:sauvegarde:/home/karl:/bin/bash
```
Un utilisateur peut appartenir à plusieurs groupes, dans tous les cas il a un groupe primaire, et le cas échéant un ou plusieurs groupes secondaires.

Structure du fichier /etc/group
```
  .-------------------- Nom du groupe
 |  .------------------ Mot de passe du groupe
 |  |   .-------------- GID
 |  |  |      .-------- Liste des utilisateurs du groupe (uniquement les utilisateurs pour lesquels ce groupe est secondaire)
 |  |  |      |
 |  |  |      |
imp:x:1242:marc,tom
```
Le fichier /etc/groups ne liste que les utilisateurs pour lesquels ce groupe est secondaire.  
Pour avoir le groupe primaire d'un utilisateur, il faut passer par /etc/passwd

Structure du fichier /etc/shadow
```
  .------------------------------------------------------ Nom d'utilisateur
 |        .---------------------------------------------- Mot de passe hashé
 |        |                       .---------------------- Date du dernier changement du mot de passe
 |        |                       |   .------------------ Temps minimum avant prochain changement de mot de passe
 |        |                       |   |  .--------------- Temps maximum de validité du mot de passe (en jours)
 |        |                       |   |  |  .------------ Nombre de jours à partir duquel l'utilisateur averti de l'expiration de son mot depasse (ici 14 jours avant expiration)
 |        |                       |   |  |  | .---------- Date d'expiration du compte (en jours depuis le 1er Janvier 1970)
 |    ____|___________________    |   |  |  | | .-------- Réservé, non utilisé
 |   |                        |   |   |  |  | | |
john:$6$iTEFbMTM$CXmxPwErbEef9/:17707:0:90:14:_:_:
```

## Le superutilisateur

Sous Linux l'utilisateur dont le UID est 0 est considéré comme étant le superutilisateur.  
En général cet utilisateur s'appelle root, il possède tous les droits, et peut lire, modifier et supprimer n'importe quel fichier.

Il est déconseillé d'utiliser le compte root pour les activités quotidiennes.

Un utilisateur classique peut exécuter une commande en tant que root via la commande sudo. Pour ça, il doit être présent dans le fichier /etc/sudoers.  

## Le fichier sudoers

Fichier contenant les règles en rapport avec la commande sudo (qui peut faire quoi).  
Ce fichier est éditable via la commande visudo.

```

      ______________________________________________________________________________ Utilisateur ou groupe (%groupe)
     |        ______________________________________________________________________ Machines sur lesquelles la règle s'applique
     |       |       _______________________________________________________________ Utilisateur dont on prend les droits (peut être ALL)
     |       |      |                            ___________________________________ Commandes (chemins absolus recommandés) une commande commençant par "!" est interdite
     |       |      |                           |
     |       |      |      _____________________|_____________________________
     |       |      |     |                                                   | 
identifiant	ALL = (user) /chemin/complet/commande,/chemin/complet/autrecommande
```

## Astuce : changement de mot de passe root 

On peut modifier le mot de pase de root, même sans le connaître en faisant la manipulation suivante (uniquement valable su GRUB est installé):

- Démarrer la machine
- Lors du démarrage de GRUB, appuyer sur "e" our entrer en mode édition
- Scroller jusqu'à la ligne commençant par "linux", à la fin de la ligne remplacer "ro quiet" par "rw quiet", puis ajouter "init=/bin/bash" à la fin de la ligne
- Appuyer sur F10 pour passer sur un shell
- Remonter le système de fichiers en mode écriture : "mount -n -o remount,rw /"
- Changer le mot de passe root : passwd root

[Reset mot de passe root](../../images/os_linux_reset_passwd.png)
