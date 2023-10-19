# Le Shell 

Le shell est un programme qui permet d'interpréter les commandes d'un utilisateur. C'est l'un des premiers moyen pour interagir avec un ordinateur. Il se présente sous la 
forme d'une interface en ligne de commande accessible depuis le terminal. L'utilisateur peut alors lancer des commandes sous forme de texte qui sont exécutées par le shell.


Sous linux il existe plusieurs type de shells, chacuns avec leur différences. Comme le sh, le bash ...

Le fichier passwd contient , pour chaque utilisateur son shell au démarrage. Ainsi si l'utilisateur lance un terminal, ce shell par défaut est exécuté. Mais l'utilisateur peut
aussi démarrer un autre shell directement depuis son terminal.

Selon le type de shell utilisé, certains fichiers de configuration sont lus . 
Pour le bash (Bourne Again Shell) il existe des fichiers de configurations dans le repertoire de l'utilisateur 
  - le fichier .bash_profile est exécuté au lancement du shell. Par défaut il source le fichier .bashrc s'il existe.
  - le fichier .bashrc contient des commandes qui peuvent être exécutées grace au fichier .bash_profile. Il est alors possible d'initialiser des variables d'environnement
    ou d'ajouter des alias de commandes.
  - le fichier .bash_aliases, par défaut le fichier n'existe pas, mais il peut être créé pour utiliser des alias de commande. 
    
