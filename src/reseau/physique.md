# Couche 1 : Physique
## Principe

La couche physique correspond au support de transmission et les connecteurs, le signal peut être porté via
- Un câble de cuivre (Ethernet, RTC)
- Une fibre optique
- Des ondes (radio, wifi, Bluetooth...)

### Le cuivre 
Le câble de cuivre possède un nommage selon son blindage ou la forme de ses paires 
Exemple : F/UTP
F: Foil Shielded ,câble protégé avec un feuillard.
U : Unshielded : les paires ne sont pas protégées
TP : Twisted Paires : Paires torsadées

Le câble peut être : 
  - Sans protection (U)
  - Avec un feuillard (F)
  - Tressé (S)
  - Tressé avec un feuillard (SF)

Les paires peuvent être : 
  - Sans protection (U)
  - Avec feuillard (F)

La paire peut être torsadée (TP) ou non (rien).
#### Les classes de câbles.

| Catégorie | Debit max                          | Notes                |
|-----------|------------------------------------|----------------------|
| CAT5      | 100Mb/s sur 100m                   | Abandonné pour le 5e |
| CAT5e     | 2,5Gb/s sur 100m et 10Gb/s sur 30m | Le plus courant      |
| CAT6      | 5Gb/s sur 100m et 10Gb/s sur 55m   | Cœur de réseau       |
| CAT6a     | 10Gb/s sur 100m                    | Datacenter           |
| CAT7      | 40Gb/s sur 500m et 100Gb/s sur 15m |                      |

### La fibre
Une fibre optique est un fil dont l’âme, très fine et faite de verre ou de plastique, a la propriété de conduire la lumière.
Elle possède de nombreux avantages face au câble de cuivre.
  - Elle est insensible aux perturbations électromagnétiques.
  - Son débit est bien plus élevé sur de plus longues distances
  - Elle est résistante au piratage physique.

La fibre est plus évolutive et sécurisée que le cuivre.

Il existe plusieurs types de fibre , monomode et multimodes.

## Le WIFI
Le WIFI utilise des ondes de 2,4Ghz , 5Ghz ou 6Ghz (WIFI 6E) pour transmettre des informations sans fil.

Lors de la connexion : 
- Le périphérique tente de se connecter au réseau sans fil (SSID) diffusé par la borne.
- La demande d'authentification du périphérique est relayée au contrôleur WIFI par la borne.
- Le contrôleur WIFI demande au serveur RADIUS d'authentifier le certificat du périphérique.
- Le serveur RADIUS vérifie que le certificat ne figure pas dans la liste des certificats révoqués.
- Si le certificat est reconnu valide, le périphérique est autorisé à se connecter au réseau
