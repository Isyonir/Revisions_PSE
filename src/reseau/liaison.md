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

### La trame Ethernet
![Trame Ethernet](../images/trame_ethernet.png)

Champs de l'entête
- Préambule : 7 octets à 10101010 pour synchroniser les stations
- Start Frame delimiter (SFD) : 1 octet à 10101011 pour annoncer le début de la trame
- @MAC destination : 6 octets
- @MAC source : 6 octets
- Type : 2 octets indiquant le protocole de niveau 3
    - 0800 pour IPv4
    - 86DD pour IPV6
    - 0806 pour ARP
- Données : padding avec des zéros si taille < 46 octets
- Frame Check Sequence (FCS) : contient le CRC de la trame qui permet au destinataire d'en vérifier l'intégrité.

### Les commutateurs
