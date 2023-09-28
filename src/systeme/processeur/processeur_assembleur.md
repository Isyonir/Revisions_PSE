# Processeur

## Généralités sur l'assembleur

Quelques exemples de codes en assembleur avec leur équivalent Python pour comprendre comment les registres fonctionnent:
Il faut bien comprendre que les registres se comportant comme des variables dans un langage de programmation.
Un registre peut soit contenir une données brute (par exemple un nombre) soit l'adresse mémoire où se trouve une donnée.

### Affectation d'une variable

| Python | Assembleur |
|--------|------------|
| x = 5  | mov rax 5  |

L'opération "mov" déplace une valeur dans un registre donné.

### Opération arithmétique sur une variable

| Python           | Assembleur                       |
|------------------|----------------------------------|
| x = 5 </br> y = x + 10 | mov rax 5 </br> mov rbx rax </br> add rbx 10 |

L'opération "add" ajoute un nombre au registre, le résultat est conservé dans le registre donné.
Pour éviter de perdre la valeur de RAX (et donc de x), on copie la valeur dans un autre registre (RBX) avant de procéder à l'addition.

### Récupération d'un Objet

| Python       | Assembleur         |
|--------------|--------------------|
| x = MonObjet | lea edx [esp + 16] |

Les objets étant des structures qui peuvent être grandes, leurs données ne rentrent pas en entier dans un registre.
Dans ce cas, le registre contiendra l'adresse mémoire des données de l'objet.
L'instruction lea (load effective address) charge dans le registre edx l'adresse contenue dans esp (le stack pointer) + 16 (décalage de 16).
Les valeurs utilisées dans cet exemple sont arbitraires.




