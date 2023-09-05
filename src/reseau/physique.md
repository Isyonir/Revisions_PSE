# Couche 1 : Physique
### Principe

La couche physique correspond au support de transmission et les connecteur, le signal peut ête porté via
- Un cable de cuivre (ethernet, RTC)
- Une fibre optique
- Des ondes (radio, wifi, bluetooth...)

#### Le cuivre 
Le câble de cuivre possède un nommage selon son blindage ou la forme de ses paires 
Exemple : F/UTP
F: Foil Shielded ,câble protégé avec un feuillard.
U : Unshielded : les paires ne sont pas protégées
TP : Twisted Pairr : Paires torsadées

Le câble peut être : 
  - Sans protection (U)
  - Avec un feuillard (F)
  - Tressé (S)
  - Tressé avec un feuillard (SF)

Les paires peuvent être : 
  - Sans protection (U)
  - Avec feuillard (F)

La paire peut être torsadée (TP) ou non (rien).


#### La fibre
Une fibre optique est un fil dont l’âme, très fine et faite de verre ou de plastique, a la propriété de conduire la lumière.
Elle possède de nombreux avantages face au câble de cuivre.
  - Elle est insensible aux perturbations électromagnétiques.
  - Son débit est bien plus élevés sur de plus longues distances
  - Elle est résistante au piratage physique.

La fibre est plus évolutive et sécurisé que le cuivre.

Il existe plusieurs types de fibre , monomode et multimodes.

### Le WIFI
Le WIFI utilise des ondes de 2,4Ghz , 5Ghz ou 6Ghz (WIFI 6E) pour transmettre des informations sans fil.

- Le PC tente de se connecter au réseau sans fil (SSID) diffusé par la borne.
- La demande d'authentification du PC est relayée au contrôleur WIFI par la borne.
- Le contrôleur WIFI demande au serveur RADIUS d'authentifier le certificat du PC.
- Le serveur RADIUS vérifie que le certificat ne figure pas dans la liste des certificats révoqués.
- Si le certificat est reconnu valide, le PC est autorisé à se connecter au réseau DGFIP.
