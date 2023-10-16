# Linux

Quelques commandes utiles sous Linux

# Sommaire
1. [Système de fichiers](#Système-de-fichiers)
2. [Gestion des tâches planifiées](#Gestion-des-tâches-planifiées)
3. [Gestion des utilisateurs](#Gestion-des-utilisateurs)
4. [Gestion des services](#Gestion-des-services)
5. [Gestion des disques](#Gestion-des-disques)

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

```
Lister tous les fichiers sous forme de liste du plus ancien au plus récent
```

```

### du
Permet de récupérer la taille d'un répertoire

-s : Ne récupère que la taille du répertoire
-h : Affiche avec une taille lisible pour un humain (en Mo, Go, ou To)

Ex:
```

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

### groupadd
Ajout d'un groupe

-g : Préciser le GID

Ex: 
```

```

### groupmod
Modification d'un groupe

-g : Préciser le GID

Ex: 
```

```

### groupdel
Suppression d'un groupe

Ex: 
```

```

### useradd
Ajout d'un utilisateur

-u : UID

-g : Groupe principal

-G : Groupe secondaire

-c : Commentaire

-d : Répertoire de connexion

-s : Shell utilisé par l'utilisateur

Ex: 
```

```

### usermod
Modification d'un utilisateur

-u : UID

-g : Groupe principal

-G : Groupe secondaire

-c : Commentaire

-d : Répertoire de connexion

-s : Shell utilisé par l'utilisateur

Ex: 
```

```

### userdel
Suppression d'un utilisateur

Ex: 
```

```

### whoami
Affiche le nom de l'utilisateur courant

Ex: 
```

```

### id
Affiche les informations (UID, GID et groupes secondaires) de l'utilisateur

Ex: 
```
-(mar sep 26 08:47:21)--(blip:~)-
[laen] $ id
uid=668(laen) gid=100(users) groupes=100(users)
```

### groups
Affiche la liste des groupes dans lesquels sont l'utilisateur

Ex: 
```
-(mar sep 26 08:47:30)--(blip:~)-
[laen] $ groups
users
```

### passwd
Modifie le mot de passe

Ex: 
```
-(mar sep 26 08:47:30)--(blip:~)-
[laen] $ groups
users
```

### chage
Permet de changer les paramètres d'expiration des mots de passe et comptes utilisateurs

-E : Modifie la date d'expiration du compte d'utilisateur

-m : Modifie le nombre de jours minimum entre deux changements de mot de passe

-M : Modifie le nombre de jours maximum entre deux changements de mot de passe avant expiration

-W : Modifie le nombre de jours avant expiration à partir duquel l'utilisateur est averti de l'expiration de son mot de passe

Ex: 
```

```

## su
Changement d'identifiant

\- : Prend les variables d'environnement de l'utilisateur ont on prend l'identifiant

-c : Permet de lancer directement une commande

Ex: 
```

```

## sudo
Exécution de commande en tant que superutilisateur

-l : Liste des droits présents dans le fichiers sudoers en rapport avec l'utilisateur courant

Ex: 
```

```

# Gestion des services

## service
Gestion des services (ancien système)

Ex: 
```

```

## chkconfig
Gestion des services au démarrage

--list : Liste les runlevels pour lesquels le service démarrera

--level : Permet de modifier les runlevels pour lesquels le service démarrera

--add : Active la possibilité de gérer le service par runlevel

--del Désactive la possibilité de gérer le service par runlevel

Ex: 
```

```

## systemctl
Gestion des services (systemd)

Ex: 
```

```

# Gestion des disques

## lsblk
Affiche les informations sur les volumes

Ex: 
```
-(mar. sept. 26 13:34:34)--(blip:~)-
[bam] $ lsblk
NAME                MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
vda                 252:0    0  100G  0 disk
├─vda1              252:1    0  512M  0 part /boot
├─vda2              252:2    0  200M  0 part /boot/efi
└─vda3              252:3    0 99,3G  0 part
  ├─vg00-lvroot     253:0    0    5G  0 lvm  /
  ├─vg00-lvswap     253:1    0    4G  0 lvm  [SWAP]
  ├─vg00-lvvtom     253:2    0    5G  0 lvm  /vtom
  ├─vg00-lvvarlog   253:3    0   10G  0 lvm  /var/log
  ├─vg00-lvvar      253:4    0   15G  0 lvm  /var
  ├─vg00-lvtmp      253:5    0    4G  0 lvm  /tmp
  ├─vg00-lvproduits 253:6    0    1G  0 lvm  /produits
  └─vg00-lvapp      253:7    0    5G  0 lvm  /app
```

## fdisk
Voir parted (actions appliquées en différé)

Ex: 
```

```

## parted
Manipulation des partitions (actions appliquées en **direct**)

Ex: 
```

```

## mkfs
Formatage dans un système de fichiers

Ex: 
```

```

## df
Informations sur l'espace utilisé 

Ex: 
```

```

## mount
Montage d'une partition

Ex: 
```

```

## umount
Démontage d'une partition

Ex: 
```

```
