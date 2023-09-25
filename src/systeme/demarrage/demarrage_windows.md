# Démarrage Windows

Ici est décrit le processus de démarrage pour Windows verion Vista et au delà en démarrage à froid (Donc, pas en veille ni hybernation)

Dans le cas d'un système démarrant par UEFI, ce dernier va charger l'image efi "bootmgfw.efi" qui contient le Windows Boot manager.
Une fois exécuté, ce dernier va tout d'abord chercher un OS qu'il peut démarrer, cette recherche se fait en deux temps:

- Premièrement, recherche d'un fichier "hiberfil.sys" (Qui correspond au contenu de la mémoire compréssé, ce fichier est créé si le système entre en hybernation)
Si ce dernier est trouvé, le WBM va charger son contenu, et démarrer l'OS en appelant "winresume.exe"
- Sinon, le WBM va chercher une liste des OS installés, si plusieurs sont trouvés, un choix sera proposé à l'utilisateur pour savoir quel OS démarrer. Le système choisi est démarré par "winload.exe"

winload.exe va initier le démarrage de l'OS, il va également récupérer les informations sur le hardware du système.
Il va ensuite charger en mémoire différents composants du noyau, et notemment "ntoskrnl.exe", ainsi qu'une des ruches du registre : config\system

Après ça, "winload.exe" passe la main à "ntoskrnl.exe".

"ntoskrnl.exe" est ce qu'on appelle l'image du noyau, il contient le noyau de Windows ainsi que que d'autres modules tels que l'ordonnanceur et le gestionnaire de mémoire)

Celui ça va se charger de tout d'abord initialiser le gestionnaire de mémoire, et de démarrer les premiers processus du système: "System" et "System idle process".
Il va ensuite charger les drivers des périphériques qui ont été précédemment découverts.

Une fois les drivers chargés, le noyau démarre le Session Manager Subsystem ("smss.exe"), il a plusieurs rôles:

- Créer les variables d'environnement système
- Démarrer les sous-systèmes windows en mode kernel et utilisateur (le sous-système est ce qui permet aux applications de faire appel à des fonctions de l'OS telles que celles de l'API Windows)

Une fois cela fait, il va lancer le gestionnaire d'identification "winlogon.exe" qui va :
- Lancer le système de services "Servics.exe"
- Lancer le processus de sécurité local "Lsass.exe" (Permet de s'authentifier)
- Initialiser, et mettre en oeuvre les Group Policy
- Lancer les programmes au démarrage.

Il attend ensuite une connexion d'un utilisateur. Ce dernier se connecte à l'aide de son identifiant + mot de passse.
Une fois cela fait, il lance "userinit.exe"

Ce programme est le premier à tourner avec les droits de l'utilisateur connecté, il charge le profil utilisateur, les programmes au démarrage sont alncés, puis démarre l'environnement "explorer.exe"
Après ça, l'utilisateur est libre d'utiliseson système.

## Schéma simplifié

UEFI => bootmgfw.efi => winload.exe => ntoskrnl.exe => smss.exe => winlogon.exe => userinit.exe

### bootmgfw.efi
- Recherche OS en hibernation (présence de hiberfil.sys) si existe => winresume.exe
- Si pas d'os en hibernation, on passe à la recherche d'un OS que l'on peut démarrer => winload.exe

### winload.exe
- Récupération des informations du système
- Chargement de certaines librairies (dll) telles que hal.dll (hardware abstraction layer)
- Chargement d'une ruche du registre : config\system
- Chargement et lancement de ntoskrnl.exe

### ntoskrnl.exe
Image du noyau, contient le noyau de Windows ainsi que que d'autres modules tels que l'ordonnanceur et le gestionnaire de mémoire.
- Initialise la mémoire (pagination)
- Charge les drivers des périphériques découverts
- Démarre les processus "System" et "System idle process"
- Démarre smss.exe

### smss.exe
Session Manager Subsystem
- Crée les variables d'environnement système
- Démarre les sous-systèmes windows en mode kernel et utilisateur (le sous-système est ce qui permet aux applications de faire appel à des fonctions de l'OS telles que celles de l'API Windows)
- Donne la main à winlogon.exe

### winlogon.exe
- Lance le système de services "Services.exe"
- Lance le processus de sécurité local "Lsass.exe" (Permet de s'authentifier)
- Initialise, et met en oeuvre les Group Policy
- Lance les programmes au démarrage de la machine.
- Attend une connexion utilisateur
- une fois qu'un utilisateur s'authentifie, lance userinit.exe

### userinit.exe
- Charge le profil utilisateur
- Lance les programmes au démarrage de l'utilisateur
- lance le shell par défaut (explorer.exe)




