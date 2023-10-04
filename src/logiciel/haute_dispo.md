# Haute disponibilité 

La haute disponibilité est une caractéristique d'un système qui vise à assurer un certain niveau de performance opérationnelle, généralement l'uptime 
(ou durée de fonctionnement), durant une période plus longue que celle attendue habituellement.

Il existe trois principes de conception système en ingénierie de fiabilité permettant d'atteindre une haute disponibilité :

- L'élimination des points de défaillances uniques. Cela signifie ajouter ou construire une redondance dans le système pour que la défaillance d'un composant ne signifie
pas la défaillance du système en entier.
- Fiabilité des points de croisements. Au niveau des systèmes redondants, le point de croisement lui-même tend à devenir un point de défaillance unique.
Les systèmes fiables doivent fournir des points de croisement fiables.
- Détection des défaillances lors de leurs occurrences. Si les deux principes ci-dessus sont observés, alors un utilisateur pourra ne jamais voir de défaillance -
mais l'activité de maintenance le doit.


## Failover et IP virtuelle 
Le failover est un terme générique pour définir est la capacité d'un équipement à basculer automatiquement vers un réseau ou un système alternatif ou en veille. 
Pour un serveur il est possible de configurer ses interfaces réseaux en "bond" pour fusionner deux cartes réseaux pour en former une seule logique. Ainsi si une carte tombe en panne, le serveur garde la connexion ainsi que sa configuration IP.

Pour éviter les points de défaillances uniques il faut faire une redondance des équipemets réseaux et des serveurs, cependant pour l'accès à certains services ,comme un serveur web par exemple, le point d'entrée est unique : soit une adresse IP soit un nom de domaine. Un Haproxy s'occupe de rediriger la requête vers un serveur ou un autre. 
Pour éviter que le Haproxy devienne un point de défaillance unique il doit être aussi redondé, mais dans ce cas là un haproxy est principal et l'autre secondaire. 
Pour que la bascule se fasse de façon invisible pour les clients, les deux serveurs doivent avoir la même adresse IP, pour cela il faut utiliser une adresse IP virtuelle et Keepalived. 

L'adresse IP virtuelle est configurée sur les n serveurs avec un certain niveau de priorité, le serveur le plus prioritaire garde l'IP virtuelle. 
De temps en temps les serveurs vont faire des tests de vie, pour vérifier que les autres serveurs répondent bien. Si jamais le serveur qui possède l'adresse IP virtuelle tombe en panne, le serveur le plus haut des les priorités récupère l'adresse IP virtuelle.

Il est aussi possible de configurer des évènements lors d'un changement d'état pour lancer un script, démarer un serveur, procéder à un test ... 
