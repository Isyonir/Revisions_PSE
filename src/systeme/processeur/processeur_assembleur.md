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


## Big et Little Endian

Le concept d'endianness désigne l'organisation en mémoire d'une information sur plusieurs octets:
- Pour le big endian : l'octet de poids **fort** est situé à l'**adresse mémoire la plus petite**
- Pour le little endian : l'octet de poids **faible** est situé à l'**adresse mémoire la plus petite**

Ex :
```
Pour une donnée de 4 octets dont la valeur est : 0x0A0B0C0D
                                                   |     |
                                                   |     |
                      Octet de poids fort ---------+     |
Octet de poids faible ---------------+

| Adresse en mémoire | 0x01 | 0x02 | 0x03 | 0x04 |
|--------------------|------|------|------|------|
| Little endian      | 0D   | 0C   | 0B   | 0A   |
| Big endian         | 0A   | 0B   | 0C   | 0D   |
```
Dans les architectures modernes (x86-64) les données sont stockées sous le format de little-endian.

