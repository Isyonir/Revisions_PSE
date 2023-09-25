### Architecture logicielle

## Client - Serveur 
Le modèle client serveur est une structure d'application distribué qui sépare les tâches ou charges de travail entre fournisseurs de ressource ou service, 
appelés serveurs, et les demandeurs de ce service, appelés clients. Les clients et les serveurs communiquent souvent à travers un réseau informatique sur des matériels séparés, 
mais les deux peuvent également se trouver sur la même machine. Un serveur hôte exécute un ou plusieurs programmes serveurs, qui partagent leurs ressources avec des clients. 
Un client ne partage habituellement aucune de ses ressources, mais demande le contenu ou le service au serveur. 
Par conséquent, les clients initient la session de communication avec les serveurs, qui attendent les requêtes entrantes.



## Trois niveaux

Une architecture à trois niveaux ou architecture trois tiers ajoute un niveau supplémentaire à l'architecture à 2 niveaux, 
permettant de spécialiser les serveurs dans une tâche précise, ce qui donne un avantage de flexibilité, de sécurité et de performance :
- un client qui demande une ressource via une interface utilisateur chargée de la présentation de la ressource ;
- un serveur d'application (appelé middleware) qui fournit la ressource, mais en faisant appel aux ressources d'un autre serveur ;
- un serveur de données qui fournit au serveur d'application les ressources requises pour répondre au client.

## N-Tiers
Une architecture à N niveaux ou architecture N-tiers n'ajoute pas de niveaux supplémentaires à l'architecture à 3 niveaux mais introduit la notion d'objets qui offre la 
possibilité de distribuer les services entre les 3 niveaux selon N couches, permettant ainsi de davantage spécialiser les serveurs.

## Modele-Vue-Contrôleur

Molèle-vue-contrôleur est un motif d'architecture typique utilisé afin de développer des interfaces utilisateur qui sépare la logique liée du programme en trois 
éléments inter-connectés. Cela est réalisé en séparant les représentations internes de l'information des façons dont l'information est présentée et acceptée par l'utilisateur.

Beaucoup de langages de programmation disposent de quadriciels MVC qui facilitent son implémentation.

Les trois composants du motifs sont :
  - Le modèle : Le composant central. Il s'agit de la structure de données dynamique de l'application, indépendant de l'interface utilisateur. Il gère directement la donnée, la logique et les règles de l'application. Il reçoit l'entrée utilisateur du contrôleur.
  - La vue : Une représentation de l'information (un graphique, un diagramme ou une table). Plusieurs vues de la même information sont possibles. C'est la présentation du modèle.
  - Le contrôleur : Accepte et optionnellement valide les entrées pour le modèle. Il permet l'exécution des intérations sur les objets du modèle de données.
