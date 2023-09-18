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


## HTTP (HyperText Transfer Protocol)

Le protocole HTTP est basé sur un principe requête/réponse :
- HTTP Request : Un client établit une connexion TCP vers un serveur (pardéfaut sur le port 80) et lui envoie une requête sous la forme d'une méthodee d'une URI, d'un protocole, suivi d'un message
- HTTP Response : Le serveur répond, au travers de la connexion TCP ouverte par le client, par une ligne d'état, incluant la version de protocole et un message de succès ou d'erreur, suivi d'un message contenant l'information souhaitée.

### La requête HTTP
Une requête HTTP consiste en une phrase comportant certains éléments :
  - Une méthode, elle peut être GET, HEAD, POST
    - GET : pour récupérer une ressource
    - HEAD : pareil que GET sauf qu'elle ne demande que la transmission de l'entête de la ressource (Taille d'un fichier avant téléchargement par exemple)
    - POST : utilisée pour indiquer au serveur de soumettre l'entité contenue dans le message à la ressource identifiée par l'URI-visée.
    - D'autres méthodes existent, mais sont moins utilisées sur les sites ordinaires.
  - Une URI
    - L'URI est l'identifiant de la ressource , dans le cas d'un serveur il s'agit du chemin vers la ressource.
  - Un protocole ainsi que sa version

Exemple :
  GET /pub/WWW/index.html HTTP/1.0
  - GET : Methode
  - /pub/WWW/index.html : chemin de la ressource
  - HTTP/1.0 : protocole et version du protocole

### La réponse HTTP

Une fois la requête reçue et interprétée, le serveur répond par un message HTTP. 
La première ligne d'une réponse HTTP contient une phrase avec plusieurs éléments : 
  - Le protocole et sa version
  - Un code de réponse
  - Un message décrivant la raison de ce code.

Les codes de retour sont rangés par catégories :
  - 1xx - Information : Non utilisé, pour usage futur
  - 2xx - Succès : L'action a été correctement reçue, interprétée, et exécutée.
  - 3xx - Redirection : Une décision supplémentaire doit être prise pour terminer la requête
  - 4xx - Erreur Client : La requête présente une erreur de forme et ne peut être satisfaite
  - 5xx - Erreur Serveur : La requête est valide, mais le serveur ne peut la satisfaire

Exemple :
  - HTTP/1.1 200 Ok
  - HTTP/1.1 404 Not Found

### Les entêtes 
Elle permettent au client et au serveur de transmettre des informations supplémentaires avec la requête ou la réponse.

Elles ne sont pas visibles dans le code de la page, mais elles sont interprétées par le client ou le serveur.

### Sécurité 
HTTP circule en clair sur le réseau, n'importe qui peut intercepter les données.
HTTPS permet d'échanger des informations confidentielles, ce n'est pas un nouveau protocole en tant que tel mais l'utilisation du HTTP avec une couche sécurisée SSL .
Le port par défaut est le 443.
### Certificats : 
HTTPS utilise des certificats qui sont authentifés par des autorités de Certification qui signent le certificat. Le navigateur vérifie l'authenticité du certificat lors de son usage.
![Schéma certicat](../images/certificatweb.png)

## FTP (File Transfer Protocol)
## SMTP / POP3 / IMAP
## LDAP (Lightweight Directory Access Protocol)
## SNMP (Simple Network Management Protocol)
