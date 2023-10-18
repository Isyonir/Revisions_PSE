# Virtualisation et conteneurisation 


## La virtualisation 
La virtualisation s'appuie sur des logiciels pour simuler une fonctionnalité matérielle et ainsi créer un système informatique virtuel. La virtualisation permet d'exécuter plusieurs systèmes virtuels avec des systèmes d'exploitation différents avec pour chacun, leur propre applications et services 

La virtualisation permet d'utiliser au maximum les capacités et ressources d'un serveur. Chaque machine virtuelle est autonome et indépendante
La création de la gestion des machines virtuelles se fait à l'aide d'un hyperviseur, il en existe deux types:
  - Type-1 natif : Ces hyperviseurs s'exécutent directement sur le matériel de l'hôte pour contrôler le matériel et gérer les systèmes d'exploitation invités.
  - Type-2 hébergés (virtualbox, Hyper-v) : Ces hyperviseurs s'exécutent sur un système d'exploitation conventionnel comme n'importe quel autre programme. Un système d'exploitation invité s'exécute en tant que processus de l'hôte. Les hyperviseurs de type-2 créent une abstraction pour les systèmes d'exploitation invités depuis le système d'exploitation hôte.

## La conteneurisation 

La conteneurisation consiste à rassembler le code du logiciel et tous ses composants (bibliothèques, frameworks et autres dépendances) de manière à les isoler dans leur propre 
« conteneur ».
Le logiciel ou l'application dans le conteneur peut ainsi être déplacé et exécuté de façon cohérente dans tous les environnements et sur toutes les infrastructures, 
indépendamment de leur système d'exploitation. Le conteneur fonctionne comme une sorte de bulle, ou comme un environnement de calcul qui enveloppe l'application et 
l'isole de son entourage. C'est en fait un environnement de calcul portable complet.

Les avantages de la conteneurisation sont multiples : 
  - Portabilité : un conteneur créé un package exécutable de logiciels qui est extrait du système d'exploitation hébergeur. Ce package est donc capable de fonctionner sur une autre plateforme car toutes ces dépendances sont comprises dans le package.
  - Agilité : le docker engine qui exécute les conteneurs est open source et à lancé la norme en matière de conteneur avec des outils de developpement compatibles sur plusieurs
OS.
  - Vitesse : Les conteneurs sont qualifiés de "léger" car ils partagent le noyau du système d'exploitation de la machine. De ce fait, les serveurs sont beaucoup moins gourmants en ressources mais aussi en licence. Le temps de démarrage en est aussi accéléré.
  - Isolation des erreurs : chaque application conteneurisé est isolée dans son propre conteneur et fonctionne de façon indépendante. Le disfonctionnement d'un conteneur n'affecte donc pas le fonctionnement des autres conteneurs.
  - Facilité de gestion : Une plateforme d'orchestration de conteneur peut automatiser l'installation, la gestion de la charge de travail et des services conteneurisés.
  - Sécurité : L'isolement des applications en tant que conteneurs empêche l'invasion de code malveillant d'affecter d'autres conteneurs ou le système hébergeur.




![image](https://github.com/Isyonir/Revisions_PSE/assets/143949453/c44712c8-8c5e-4870-ba9a-ebb642a4569f)
