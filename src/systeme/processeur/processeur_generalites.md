# Processeur

## Généralités

Le processeur est l'équipement physique d'une machine qui sert à exécuter des instructions.
Les processeurs ont des jeux d'instructions (commandes possibles) qui dépendent de leur architecture.
Quelques architectures:
- x86_64 (Extension 64 bits de l'architecture x86)
- ARM (Utilisé notemment sur les processeurs mobiles)
- z/Architecture (mainframe IBM)

## Les registres

Les registres sont de petites zones mémoire situées à l'intérieur du processeur, leur accès est très rapide.
Les instructions qu'un processeur execute se font uniquement sur les registres. Les données à manipuler sont donc déplacées 
de la RAM vers les registres quand le processeur en a besoin.
Dans le cas d'une architecture x86_64, les registres peuvent être séparés en plusieurs catégories.

### Les registres généraux
Ce sont les registres les plus utilisés, ce sont eux que l'on manipule le plus souvent, le nombre de bits d'un processeur 
(16, 32 ou 64) se refère à la taille de ces registres (un processeur 64 bits aura des registres généraux d'une taille de 64 bits).
Leur nom dépend de leur taille:
- Préfixe "R" => 64 bits
- Préfixe "E" => 32 bits
- Pas de préfixe => 16 bits

![Organisation rgistres](../../images/processeur_registres.png)

### Les registres de segment
Ces registres sont principalement utilisés pour contenir des adresses de segment de la RAM.
Pour rappel dans le cas d'une mémoire segmentée, une adresse mémoire se compose de deux parties:
- Le segment
- L'offset (décalage)

### Le registre d'instruction
Appelé RIP, EIP ou IP (Instruction pointer), ce registre garde en mémoire l'adresse mémoire de la prochaine instruction à être exécutée.

### Les flags
Registres utilisés en interne par le processeur pour connaitre le résultat des opérations précédentes.
Ils ont une taille de 1 bit (vrai ou faux)

Quelques flags :

|Nom | Nom complet   | Description                                                                                                    |
|----|---------------|----------------------------------------------------------------------------------------------------------------|
| CF | Carry flag    | Indicateur de retenue (1 si une retenue, sinon 0)                                                              |
| PF | Parity flag   | Indique si le résultat est pair (1 = pair 0 = impair)                                                          |
| ZF | Zero flag     | Indique si le résultat est égal à 0 (1 = vrai 0 = faux)                                                        |
| SF | Sign flag     | Indique si le résultat d'une opération sur des nombres signés est positif ou négatif (1 = négatif 0 = positif) |

