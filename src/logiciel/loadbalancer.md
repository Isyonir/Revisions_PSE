# Load Balancer

Un load balancer ou répartiteur de charger permet , comme son nom l'indique, de répartir un flux vers un serveur.
Ainsi plusieurs serveurs webs peuvent fonctionner en parallèle pour permettre un plus grand nombre d'accès simultané.

Un loadbalancer possède plusieurs modes de fonctionnement : 
  - Round robin : les connexions sont dirigés vers les serveurs les uns à la suite des autres.
  - Leastconn, le serveur avec le moins de connexions et le moins utilisé est alors utilisé.
  - source : le serveur de destination dépend de l'adresse IP source.
  - URI : le serveur destination dépend de l'URI de la ressource demandée.
  - hdr : le serveur de destination dépend du contenu du header HTTP
  - first : pour les VM à temps de vie court, tout le traffi est envoyé sur le plus petit nombre de machines disponibles, ce qui permet d'éteindre les autres.

    
### Haproxy

Haproxy est une solution disponible sous linux capable d'occuper le rôle de load balancer.

Voici un exemple de fichier de configuration 

'
#---------------------------------------------------------------------
# main frontend which proxys to the backends
#---------------------------------------------------------------------
frontend main
    bind *:80
    acl rule1 hdr_dom(host) -i site.test
    acl rule2 hdr_dom(host) -i supervision.test
    use_backend bk_2 if rule2
    use_backend bk_1 if rule1
    default_backend bk_1
#---------------------------------------------------------------------
# static backend for serving up images, stylesheets and such
#---------------------------------------------------------------------
backend bk_1
    balance     roundrobin
    server      node1 192.168.0.10:80 check
    server		  node2 192.168.0.11:80 check

backend bk_2
    server		node1 192.168.0.15:80 check
'

Dans la configuration frontend main, le Haproxy écoute quelque soit l'adresse IP, mais uniquement sur le port 80.
La configuration fait attention au domaine de destination, si au souhaite accéder au site.test alors on est dans la rule1, si on souhaite accéder au site supervision.test 
on est dans la rule2. 
Par défaut, le backend utilisé est le bk_1.

Dans le cas de la rule1 on utilise le backend1, dans le cas de la rule2 on utilise le backend2

Ensuite dans la configuration des backends, on retrouve le backend1 , il correspond à une ferme de deux serveurs web, pour l'hébergement d'un site internet.
  - Son mode de fonctionnement est en roundrobin (redirection vers un serveur puis l'autre)
  - Il possède un premier serveur "node1", dans cet exemple son adresse est 192.168.0.10 et le port de destination, le 80
  - Il possède un second serveur "node2", dans cet exemple son adresse est 192.168.0.11 et le port de destination, le 80

Le backend2 lui, correspond au serveur de supervision;
  - Il n'y a qu'un seul serveur de destination, donc pas de loadbalancer entre plusieurs serveurs.
  - Le seul serveur est 192.168.0.15 et son port de destination est le 80.
