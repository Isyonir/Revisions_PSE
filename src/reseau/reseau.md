# Couche 1 : Réseau
## Principe IP v4 et masques de sous-réseaux
L'adresse IP est composée de 4 octets de 8 bits (0-255) soit 32 bits. Il existe 4 294 967 296 adresses maximum. 
L'adresse IP est associée à un masque, elle permet de couper l'adresse en deux partie un NetID et un HostID

Exemple : 
- Adresse IP :   192.168.0.1
- Masque :       255.255.255.0
- NetId  :       192.168.0
- HostId :       1

En notation CIDR 255.255.255.0 -> /24 (24 bits à "1")
L'association adresse/masque donne plusieurs informations importantes comme le nombre de machines adressables. 
Plus le masque est grand moins on à d'adresses.

L'adresse réseau est l'identifiant du réseau, on l'obtient quand tous les bits du HostId sont à 0

L'adresse de broadcast, utilisée pour communiquer à tous les membres du réseau s'obtient quand tous les bits du HostID sont à 1.

Exemple :
- Adresse IP :   192.168.0.1
- Masque :       255.255.255.0
- @ Réseau:      192.168.0.0
- @ Broadcast:   192.168.0.255

Le nombre de machines adressables est égal à 2^8 -2 = 254 

Les classes d'adresses : 
<table>
  <tr>
    <th>Classe</th>
    <th>Bits de départ</th>
    <th>Début</th>
    <th>Fin</th>
    <th>CIDR</th>
    <th>Masque</th>
    <th>Machines</th>
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
    <td>E : Réservée IANA</td>
    <td>1111</td>
    <td>240.0.0.0</td>
    <td>255.255.255.255</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</table>

## Adresses réservées
Type d'adresses
- Adresses réservées
Adresses particulières, réservées au fonctionnement du réseau.
- Adresses privées
Adresses non routables, utilisables uniquement sur le réseau local. Uniques sur le réseau local, mais pas globalement. À choisir parmi les plages d'adresses privées en fonction du nombre de machines.
- Adresses publiques
Toutes les adresses qui ne sont ni réservées ni privées. Adresses routables et uniques sur Internet Fournies par le Fournisseur d'Accès Internet (FAI)

Adresses réservées
<table>
  <tr>
    <th>Adresse</th>
    <th>Début</th>
    <th>Fin</th>
    <th>CIDR</th>
    <th>Masque</th>
  </tr>
  <tr>
    <td>Adresse nulle</td>
    <td>0.0.0.0</td>
    <td>0.0.0.0</td>
    <td>/32</td>
    <td>255.255.255.255</td>
  </tr>
  <tr>
    <td>Broadcast général</td>
    <td>255.255.255.255</td>
    <td>255.255.255.255</td>
    <td>/32</td>
    <td>255.255.255.255</td>
  </tr>
  <tr>
    <td>Loopback</td>
    <td>127.0.0.0</td>
    <td>127.255.255.255</td>
    <td>/8</td>
    <td>255.0.0.0</td>
  </tr>
  <tr>
    <td>Apipa (auto-configurée)</td>
    <td>169.254.0.0</td>
    <td>169.254.255.255</td>
    <td>/16</td>
    <td>255.255.0.0</td>
  </tr>
  <tr>
    <td>Multicast</td>
    <td>224.0.0.0</td>
    <td>239.255.255.255</td>
    <td>/4</td>
    <td>240.0.0.0</td>
  </tr>
  <tr>
    <td>NAT à grande échelle (RIE)</td>
    <td>100.64.0.0</td>
    <td>100.127.255.255</td>
    <td>/10</td>
    <td>255.192.0.0</td>
  </tr>
</table>

Pour chaque classes(A,B et C) des adresses sont dites privées, elles sont utilisées pour un usage interne et privé. Ces adresses ne sont donc pas routables sur internet.
Elles sont donc unique localement (LAN ou WAN interne) mais à un niveau mondial plusieurs périphériques peuvent avoir la même adresse locale.

<table>
  <tr>
    <th>Classe</th>
    <th>Début</th>
    <th>Fin</th>
  </tr>
  <tr>
    <td>A</td>
    <td>10.0.0.0</td>
    <td>10.255.255.255</td>
  </tr>
  <tr>
    <td>B</td>
    <td>172.16.0.0</td>
    <td>172.31.255.255</td>
  </tr>
  <tr>
    <td>C</td>
    <td>192.168.0.0</td>
    <td>192.168.255.255</td>
  </tr>
</table>

## CIDR et subnetting
Le CIDR (Classless Inter-Domain Routing) remplace le mécanisme des classes 
Sa notation se fait en comptant le nombre de bits à 1 du masque 
Exemple : 
- En décimal : 255.255.255.0
- En binaire : 1111 1111.1111 1111.1111 1111.0
- En CIDR    : /24

Le CIDR permet d'utiliser des masques hors classe pour plus de granularité. (Variable Lenght Subnet Mask VLSM)
Quelques exemples : 
- /17 : 32766 hôte,
- /22 : 1022 hotes
- /30 : 2 hôtes
- /32 : 1 hôte

Le CIDR introduit la notion de subnetting et de suppernetting.

### Le subnetting 

Le subnetting consite à couper un réseau en plusieurs sous-réseaux. Le découpage se fait toujours de manière égale.
<table style="width:100%;text-align:center;">
  <tr>
    <td colspan="8">172.16.0.0/16</td>
  </tr>
  <tr>
    <td colspan="4" style="width:50%">172.16.0.0/17</td>
    <td colspan="4" style="width:50%">172.168.128.0/17</td>
  </tr>
  <tr>
    <td colspan="4" style="width:50%">172.16.0.0/17</td>
    <td colspan="2">172.16.128.0/18</td>
    <td colspan="2">172.16.192.0/18</td>
  </tr>
  <tr>
    <td colspan="4" style="width:50%">172.16.0.0/17</td>
    <td colspan="1">172.16.128.0/19</td>
    <td colspan="1">172.16.160.0/19</td>
    <td colspan="2">172.16.192.0/18</td>
  </tr>  
</table>


## ARP et ICMP

## Fragmentation

## Routage et NAT

## Principes IP v6
