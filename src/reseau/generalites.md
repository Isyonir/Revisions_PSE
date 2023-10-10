# Réseau

## Notions générales sur le réseau

### Le lien 

On parle de lien pour décrire les différents médiums de transmission utilisés pour relier les appareils entre eux afin de former un réseau informatique.
Ils peuvent être de différentes natures, on retrouve des câbles (Ethernet/RTC) ou de la fibre optique. 

Certaines ondes peuvent aussi être utilisées pour transporter les informations, c’est le cas du WIFI (2,4 GHz, 5 GHz et 6 GHz) mais aussi des ponts radio ou des faisceaux laser qui permettent d'interconnecter deux réseaux sans utiliser de fibre ou de câbles de cuivre. Les satellites peuvent aussi être utilisées.

Dans le modèle OSI, les liens correspondent à la couche physique (1) et liaison (2).

### Les nœuds 

Les nœuds d’un réseau sont les différents points de connexion liant le médium aux différents appareils. Ils peuvent être : 
- <b>Une interface réseau</b> : Un contrôleur d’interface réseau (NIC) est un matériel fournissant à un ordinateur la capacité d’accéder au média de transmission. Il possède la capacité de traiter les signaux reçus correspondant aux informations réseaux de bas niveau. L’interface réseau peut être une carte Ethernet, fibre ou WIFI.
- <b>Répéteurs et concentrateur</b> : le répéteur est un matériel permettant de recevoir un signal pour le diffuser, par exemple un répéteur WIFI récupère un signal afin de l'amplifier. Un concentrateur (ou HUB) permet de récupérer un signal électrique (sur câble Ethernet) et le diffuse sur tous les liens connectés au HUB. Le HUB n'est plus utilisé pour des raisons de sécurité.
- <b>Commutateurs</b> : ils permettent de recevoir, filtrer et de transmettre les signaux qu'ils reçoivent au bon destinataire.
- <b>Modems (ou modulateur-démodulateur)</b>, il permet de transformer un signal numérique en signal analogique. 
- <b>Pare-feux</b> : il s'agit d'un appareil permettant de protéger un réseau. Il se place en intermédiaire entre deux réseaux (LAN et WAN par exemple) et filtre le trafic entrant et sortant. 
  
### Les types de topologie 

Il existe un certains nombres de topologie basiques pour un réseau : 
- <b>Point à point</b> : Il s'agit de la plus basique des topologies réseaux : deux appareils directement reliés entre eux en deux points.
- <b>Daisy chain</b> : Les équipements réseaux sont reliés entre eux en série.
- <b>Bus</b> : Chaque nœud (équipement ou ordinateur) est connecté directement à un câble principal et ce directement entre eux. Très vulnérable si l'une des connexions est défectueuse, car l'ensemble du réseau est impacté
- <b>Étoile</b> : Chaque nœud est connecté à un nœud central appelé concentrateur ou commutateur (Switch). Le point central est sensible car s'il tombe en panne le réseau est totalement coupé.
- <b>Anneaux</b> : Daisy chain mais en boucle fermée. Les machines parlent chacune leur tour.
- <b>Maille</b> : Chaque nœud est interconnecté partiellement ou totalement avec les autres nœuds du réseau.
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
    
### Les types de réseaux 
  - LAN (Local Area Network) : Réseau local limité à un seul site géographique, dans une entreprise. Toutes les machines de ce réseau sont reliées directement via des commutateurs (switches).

  - WAN (Wide Area Network) : Réseau grande distance, par opposition au LAN. Constitué de plusieurs LAN reliés entre eux par des routeurs. Exemples : Internet.

  - MAN (Metropolitan Area Network) : Réseau de LANs reliés et distants de quelques kilomètres.
Le but étant de relier les différents sites en très haut débit.
