# Réseau

## Notions générales sur le réseau

### Le lien 

On parle de lien pour décrire les différents médiums de transmission utilisés pour relier les appareils entre eux afin de former un réseau informatique.
Ils peuvent être de différentes natures, on retrouve des cables (ethernet/RTC) ou de la fibre optique. 

Certaines ondes peuvent aussi être utilisées pour transporter les informations, c'est le cas du WIFI (2,4 Ghz, 5Ghz et 6Ghz) mais aussi des ponts radio ou des faisceaux laser qui permettent d'interconnecter deux réseaux sans utiliser de fibre ou de câbles de cuivre. Les satellites peuvent aussi être utilisées.

Dans le modèle OSI, les liens correspondent à la couche physique(1) et liaison (2).

### Les noeuds 

Les noeuds d'un réseau sont les différents points de connexion liant le médium aux différents appareils. Ils peuvent être : 
- <b>Une interface réseau</b>: Un contrôleur d'interface réseau (NIC) est un matériel fournissant à un ordinateur la capacité d'accéder au média de transmission. Il possède la capacité de traiter les signaux reçus correspondant aux informations réseaux de bas niveau. L'interface réseau peut être une carte ethernet, fibre ou WIFI.
- <b>Répéteurs et concentrateur</b>, le répéteur est un matériel permettant de recevoir un signal pour le diffuser, par exemple un répéteur WIFI récupère un signal afin de l'amplifier. Un concentrateur (ou HUB) permet de récupérer un signal electrique (sur câble ethernet) et le diffuse sur tous les liens connectés au HUB. Le HUB n'est plus utilisé pour des raisons de sécurité.
- <b>Commutateurs</b>, ils permettent de recevoir, filtrer et transmettrent les signaux qu'ils reçoivent au bon destinataire.
- <b>Modems (ou modulateur-démodulateur)</b>, il permet de transformer un signal numérique en signal analogique. 
- <b>Pare-feux</b>, il s'agit d'un appareil permettant de protéger un réseau. Il se place en intermédiaire entre deux réseaux (LAN et WAN par exemple) et filtre le traffic entrant et sortant. 
  
### Les types de topologie 

Il éxiste un certains nombre de topologie basiques pour un réseau : 
- <b>Point à point</b> : Il s'agit de la plus basique des topologie réseaux : deux appareils directements reliés entre eux en deux points.
- <b>Daisy chain</b> : Les équipements réseaux sont reliées entre eux en série.
- <b>Bus</b> : Chaque noeud (equipement ou ordinateur) est connecté directement à un câble principal et ce directemet entre eux. Très vulnérable si l'une des connexion est défecteuse car l'ensemble du réseau est impacté
- <b>Etoile</b> ; Chaque noeud est connecté à un noeud central appelé concentrateur ou commutateur (switch). Le point central est sensible car s'il tombe en panne le réseau est totalement coupé.
- <b>Anneaux</b> : Daisy chain mais en boucle fermée. Les machines parlent chacune leur tour.
- <b>Maille</b> : Chaque noeud est interconnecté partiellement ou totalement avec les autres noeuds du réseau.
- <b>Arbre</b> : Collection de réseaux étoiles arrangés hiérarchiquement.
- <b>Hybride</b> : Combine plusieurs topologies réseaux.

### Les types de transmission

  - Unicast : Transmission entre une machine et une seule autre.

  - Broadcast : Transmission entre une machine et toutes les autres.

  - Multicast : Transmission entre une machine et plusieurs autres

### Les sens de transmission

  - Simplex : Une station ne peut qu'émettre et l'autre que recevoir. (Quasiment inutilisé maintenant).

  - Half-duplex:Chaque station peut émettre, mais pas en même temps (Principe du Talkie-Walkie)

  - Full Duplex (ou simplement duplex):Chaque station peut émettre et recevoir en même temps.
