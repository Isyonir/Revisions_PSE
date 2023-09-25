# Linux

Quelques commandes utiles sous Linux

# Sommaire
1. [Système de fichiers](#Système-de-fichiers)
2. ![Gestion des tâches planifiées](#Gestion-des-tâches-planifiées)
3. ![Gestion des utilisateurs](#Gestion-des-utilisateurs)


## Système de fichiers

### pwd
Affichage de l'emplacement courant 

Ex :
```
-(ven sep 22 09:18:57)--(z4bpadm3:~/CQH)-
[g2a] $ pwd
/home/g2a/CQH
```

### cd
Déplacement dans l'arborescence

Ex:
```
-(ven sep 22 09:20:40)--(z4bpadm3:~)-
[g2a] $ pwd
/home/g2a
-(ven sep 22 09:20:43)--(z4bpadm3:~)-
[g2a] $ cd CQH/
-(ven sep 22 09:20:47)--(z4bpadm3:~/CQH)-
[g2a] $ pwd
/home/g2a/CQH
```
Retour dans le répertoire personnel
```
-(ven sep 22 09:20:49)--(z4bpadm3:~/CQH)-
[g2a] $ cd
-(ven sep 22 09:20:52)--(z4bpadm3:~)-
[g2a] $ pwd
/home/g2a
```

### ls
Lister le contenu d'un répertoire

-l : Lister sous forme de liste avec des infos en plus (type  du  fichier,  les  permissions d’accès, le nombre de liens physiques, le nom du propriétaire et du groupe, la taille en octets, et l’horodatage.)

-r : Inverse l'ordre d'affichage des fichiers

-t : Lister par date de création (du plus récent au plus ancien)

Ex:
```
-(ven sep 22 10:04:31)--(z4bpadm3:~/CQH)-
[g2a] $ ls
afe     fno     hyposcan  mistral  receptionR.pl      SNat20230620.log  swi
bambou  fno_zp  icm       noemie   retourFormuels.pl  snatLog.tar.gz    toa
ensap   gold    khq       par      r-odl              sshp
```
Lister tous les fichiers sous forme de liste du plus ancien au plus récent
```
-(ven sep 22 10:09:54)--(z4bpadm3:~/CQH)-
[g2a] $ ls -ltr
total 108
-rwxr-xr-x  1 g2a users 11216 jui 12  2017 sshp
drwxr-xr-x  2 g2a users  4096 déc  5  2022 afe
drwxr-xr-x  2 g2a users  4096 déc  6  2022 r-odl
drwxr-xr-x  2 g2a users  4096 jan 20  2023 swi
drwxr-xr-x  2 g2a users  4096 avr  2 03:00 khq
drwxr-xr-x  2 g2a users  4096 mai  6 03:00 noemie
drwxr-xr-x  2 g2a users  4096 jun 19 03:00 icm
-rw-r--r--  1 g2a users  2109 jun 19 09:12 snatLog.tar.gz
-rw-r--r--  1 g2a users 12625 jun 20 15:01 SNat20230620.log
drwxr-xr-x  4 g2a users  4096 jun 21 13:38 toa
-rw-r--r--  1 g2a users  1307 jun 27 12:32 receptionR.pl
-rw-r--r--  1 g2a users  2213 jun 27 13:48 retourFormuels.pl
drwxr-xr-x  2 g2a users  4096 jui  5 16:05 hyposcan
drwxr-xr-x  4 g2a users  4096 jui 28 10:58 par
drwxr-xr-x  2 g2a users  4096 aoû 31 10:20 gold
drwxr-xr-x 13 g2a users  4096 sep  7 10:24 ensap
drwxr-xr-x  2 g2a users 12288 sep  7 10:57 fno
drwxr-xr-x  2 g2a users  4096 sep 11 13:58 bambou
drwxr-xr-x  2 g2a users  4096 sep 20 09:32 fno_zp
drwxr-xr-x  3 g2a users  4096 sep 21 14:05 mistral
```

### cp
Copie de fichiers

-p : Conserve le propriétaire, le groupe, les permissions d'accès et l'horodatage du fichier original

-R ou -r : Copie récursive des répertoires

Ex:
```

```

### mv
Déplacement de fichier (préserve les droits)

Ex:
```

```

### touch
Modification de l'horodatage, peut être utilisé pour créer un fichier (déconseillé, lourd en terme de ressources)

Ex:
```

```

### mkdir
Création d'un répertoire

-p : Crée les répertoires parents le cas échéant

Ex:
```

```

### stat
Affiche les méta-données du fichier (horodatage)

Ex:
```

```

### rm
Suppression de fichiers / répertoires

-r : Récursif, supprime les répertoires
- f: Force, ne demande pas la confirmation /!\ dangereux /!\

Ex:
```

```

### ln 
Création de liens

-s : Création d'un lien symbolique

Ex:
```

```

### chmod
Modification des droits d'un fichier

Ex:
```

```

### chown
Modification du propriétaire ou groupe d'un fichier

Ex:
```

```

### umask
Affichage et modification de l'umask

-S: Affichage des droits en mode symbolique (rwx)

Ex:
```

```

### getfacl
Renvoie les permissions ACL d'un objet

Ex:
```

```

### setfacl
Manipulation des  ACL

-m : Ajout / modification de règles

Ex:
```

```

-x : Supprime une règle

Ex:
```

```

## Gestion des tâches planifiées

### crontab
Manipulation des tâches planifiées

-l : Lister les tâches de l'utilisateur courant
-e : Edition des tâches
-r : Suppression de toutes les tâches

Ex: 
```

```
## Gestion des utilisateurs

