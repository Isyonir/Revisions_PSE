# Couche 7 : Application

## DHCP (Dynamic Host Configuration Protocol)## DNS (Domain Name Service)

Le DHCP permet l'attribution automatique de la configuration réseau au démarrage d'une machine.

Elle se fait en plusieurs étapes : 
- DHCP DISCOVER : Le client émet une requête DHCP de demande d'adresseIP en broadcast uniquement sur le réseau local.
- DHCP OFFER : Un serveur DHCP à l'écoute sur le port UDP 67 répond en offrant une adresse IP disponible.
- DHCP REQUEST :le client sélectionne la 1ère réponse reçue et demande l'utilisation de cette adresse au serveur DHCP. 
Ce broadcast permet aussi de prévenir les serveurs DHCP non choisis afin qu'ils puissent libérer les adresses proposées.
- DHCP ACK : Le serveur DHCP accuse réception et accorde l'adresse IP pour une durée déterminée (bail). Ce message peut aussi contenir des paramètres de configuration supplémentaires (passerelle, serveur DNS...)

## DNS (Domaine Name Service)

Le DNS est une base de donnée distribuée accessible via un système de client-serveur. Cette base de donnée contient les correpondances IP - nom de domaine des sites internet.

Le système est basée sur une hierarchie de noms de domaines partant d'une racine, représenté par un point , qui n'apparait que dans la configuration des serveurs DNS.
On trouve ensuite au 1er niveau les TLD (Top Level Domains) qui sont gérés par l'ICANN. À partir de ces TLD, on va trouver les domaines inférieurs et sous-domaines dont la gestion est décentralisée.

### Les serveurs racines (Root Servers)
Les serveurs DNS racines gèrent les délégations pour les noms de domaine de premier niveau (TLD). 
Il existe 13 groupes de serveurs racines, pour des raisons de fiabilité et de performance. Chaque groupe est un ensemble de serveurs DNS.
En 2022, sont opérationnels 1548 serveurs DNS racines.

## HTTP (HyperText Transfer Protocol)


## FTP (File Transfer Protocol)
## SMTP / POP3 / IMAP
## LDAP (Lightweight Directory Access Protocol)
## SNMP (Simple Network Management Protocol)
