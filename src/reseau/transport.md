# Couche 4 : Transport

## TCP : Transmission Control Protocol

### Généralités
Le protocole TCP introduit la notion de port TCP (0->65535)
Il assure le transport fiable des données en controllant si les données sont erronnées ou non reçues, dans ces cas, le protocole redemande ces données.

Il fonctionne en mode connecté, ordonné et bi-directionnel.
Le TCP est utilisé pour le HTTP, FTP, SMB...

### Les ports
Les ports viennent s'ajouter à l'adresse IP pour céer un couplé appelé "Socket TCP", il permet d'identifier un canal de communication sur une machine.
Il existe plusieurs types de ports :
  - Les ports connus de 0 à 1023 : ils sont reservés à certaines application (HTTP: 80)
  - Les ports enregistrés, de 1024 à 49151
  - Les ports dynamiques ou privés , de 49152 à 65535 

### Ouverture de session (3 way handshake)
- Pour ouvrir une session, la machine envoie un paquet avec le drapeau SYN (synchronisation) à 1.
- Le serveur répond avec un accusé de réception ACK (acknoledge) ainsi que le drapeau SYN à 1
- La machine confirme la connexion avec un ACK 
- La session TCP est ouverte 

### Numéro de séquence
Le TCP fonctionne en mode connecté, il utilise un numéro de séquence pour tracer les envois, si un segment manque il est renvoyé : 





## UDP

## QUIC
