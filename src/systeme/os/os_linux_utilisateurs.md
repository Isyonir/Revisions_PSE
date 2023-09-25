# Linux

## La gestion des utilisateurs

La configuration des utilisateurs est basée sur 3 fichiers :
- /etc/passwd : Liste des utilisateurs
- /etc/group : Miste des groupes d'utilisateurs
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
  |  |   |   |      |          |          .-------- Chemin de l'interpréteur bash utilisé
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
