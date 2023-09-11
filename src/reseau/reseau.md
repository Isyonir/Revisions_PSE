# Couche 1 : Réseau
### Principe IP v4 et masques de sous-réseaux
L'adresse IP est composée de 4 octets de 8 bits (0-255) soit 32 bits. Il existe 4 294 967 296 adresses maximum. 
L'adresse IP est associée à un masque, elle permet de couper l'adresse en deux partie un NetID et un HostID

Exemple : 
Adresse IP :   192.168.0.1
Masque :       255.255.255.0
NetId  :       192.168.0
HostId :       1

En notation CIDR 255.255.255.0 -> /24 (24 bits à "1")
L'association adresse/masque donne plusieurs informations importantes comme le nombre de machines adressables. 
Plus le masque est grand moins on à d'adresses.
L'adresse réseau est l'identifiant du réseau, on l'obtient quand tous les bits du HostId sont à 0
L'adresse de broadcast, utilisée pour communiquer à tous les membres du réseau s'obtient quand tous les bits du HostID sont à 1.
Exemple :
Adresse IP :   192.168.0.1
Masque :       255.255.255.0
@ Réseau:      192.168.0.0
@ Broadcast:   192.168.0.255

Le nombre de machines adressables est égal à 2^8 -2 = 254 

Les classes d'adresses : 
<table>
  <tr>
    <td>Classe</td>
    <td>Bits de départ</td>
    <td>Début</td>
    <td>Fin</td>
    <td>CIDR</td>
    <td>Masque</td>
    <td>Machines</td>
  </tr>
  <tr>
    <td>A</td>
    <td>0</td>
    <td>0.0.0.0</td>
    <td>127.255.255.255</td>
    <td>/8</td>
    <td>255.0.0.0</td>
    <td>16 777 214</td>
  </tr>
  <tr>
    <td>B</td>
    <td>10</td>
    <td>128.0.0.0</td>
    <td>191.255.255.255</td>
    <td>/16</td>
    <td>255.255.0.0</td>
    <td>65534</td>
  </tr>
  <tr>
    <td>C</td>
    <td>110</td>
    <td>192.0.0.0</td>
    <td>223.255.255.255</td>
    <td>/24</td>
    <td>255.255.255.0</td>
    <td>254</td>
  </tr>
  <tr>
    <td>D : Multicast</td>
    <td>1110</td>
    <td>224.0.0.0</td>
    <td>239.255.255.255</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>E Réservée IANA</td>
    <td1111</td>
    <td>240.0.0.0</td>
    <td>255.255.255.255</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</table>
### Adresses réservées
Type d'adresses
- Adresses réservées
Adresses particulières, réservées au fonctionnement du réseau.
- Adresses privées
Adresses non routables, utilisables uniquement sur le réseau local. Uniques sur le réseau local, mais pas globalement. À choisir parmi les plages d'adresses privées en fonction du nombre de machines.
- Adresses publiques
Toutes les adresses qui ne sont ni réservées ni privées. Adresses routables et uniques sur Internet Fournies par le Fournisseur d'Accès Internet (FAI)


### CIDR et subnetting

### ARP et ICMP

### Fragmentatio

### Routage et NAT

### Principes IP v6
