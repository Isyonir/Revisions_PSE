# Couche 2 : Liaison
### Principes 
L'adresse MAC (Media Access Control) est l'adresse physique d'une carte réseau (Ethernet, wifi...) cette adresse est codée sur 6 octets en paire de deux chiffres hexadécimaux séparés par des deux-points.
Les trois premiers octets de l'adresse correspondent à un constructeur, la deuxième partie de l'adresse correspond à la carte.
| Adresse | Fabriquant |
|---------|---------|
|08:00:20:0a:15:db| Carte réseau Oracle Corporation|
|f0:1f:af:16:0f:df| Carte réseau Dell Inc.|
|00:07:cb:c4:e8:0c| Carte réseau Freebox SAS|

L'adresse MAC est normalement unique, mais ce n'est pas le cas, les constructeurs utilisent souvent des adresses déjà utilisées.

Certaines adresses MAC sont réservées 
| Adresse | Description |
|---------|---------|
|FF:FF:FF:FF:FF:FF |Adresse de broadcast Ethernet|
|00:00:00:00:00:00 |Adresse vide ou non attribuée|
|01:00:5E:xx:xx:xx |Adresse de multicast IPv4    |
|33:33:xx:xx:xx:xx |Adresse de multicast IPv6    |
|01:80:C2:00:00:00 |Adresse de « spanning tree » |
|00:00:5E:00:01:xx |Protocole VRRP               |
