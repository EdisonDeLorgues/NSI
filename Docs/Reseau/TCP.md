### La couche de transport, UDP et TCP

Le protocole IP permet la transmission d’un paquet de données, depuis une machine source vers une machine cible (en routant le paquet par des nœuds intermédiaires). Il permet donc de créer une communication entre deux machines physiques.

D’un point de vue pratique, ce que l’on essaye d'établir est une communication entre deux programmes qui s’exécutent, en particulier entre un client s’exécutant sur un poste client et un serveur s’exécutant sur un serveur physique.

Pour reprendre notre exemple initial, il y a un canal de communication entre le navigateur Web et le serveur Web (le programme qui distribue les pages Web). Mais sur une machine, il y a rarement un seul service réseau. En effet, sur le même ordinateur que notre serveur Web pourraient se trouver un serveur de mails, un serveur de bases de données, etc. Il nous faut donc un moyen d'identifier, pour une adresse IP donnée, avec quel service on souhaite communiquer.

C’est le premier rôle des protocoles de la couche de transport que sont **UDP** (pour User Datagram Protocol) et **TCP** déjà mentionnés. Ces deux protocoles définissent un numéro de port, c’est-à-dire un identifiant numérique associé à un service particulier.

Par exemple, le numéro de port par défaut pour le Web non sûr (protocole HTTP) est le 80, celui pour le Web sécurisé (protocole HTTPS) est le 443. Attention, ce ne sont que des conventions. Un serveur Web peut très bien attendre des connexions sur un tout autre port. Il faudra alors que le navigateur Web qui souhaite se connecter au serveur spécifie ce port.

Le protocole UDP se limite essentiellement à cette fonctionnalité. Lorsqu’une application souhaite communiquer à travers le réseau avec une autre application par le protocole UDP, sur une machine distante, elle spécifie l’adresse IP de la machine distante et le numéro de port sur lequel l’application serveur est en attente de connexion et envoie un datagramme UDP (la spécification du protocole parle de datagramme plutôt que de paquet pour UDP). Le paquet contient un entête (une suite d’octets précédant les aucune notification. Un autre défaut d’UDP est que si une application envoie deux datagrammes l’un à la suite de l’autre, elle n’a aucune garantie que l’application réceptrice les reçoive dans le même ordre.

Le protocole TCP résout ces problèmes grâce à un système d’accusés de réception. Le protocole permet d’envoyer à un programme destination des données de taille arbitraire, dans l’ordre, de détecter les erreurs de transmissions et, si besoin, de retransmettre automatiquement les fragments de données perdus ou corrompus. Lorsqu'un client souhaite se connecter à un  serveur avec le protocole TCP, il initie une mise en place de connexion en trois temps (three way handshake). La figure suivante décrit ce procédé:

<img src="./connexionTCP.jpg" alt="connexion  TCP" height="700"/>

* Dans un premier temps, le client choisit un numéro de séquence aléatoire (1234 dans la figure). Il envoie ensuite au serveur un paquet étiqueté SYN (synchronized, pour synchronisation) indiquant le numéro choisi.
* Le serveur, sur réception de ce paquet choisit lui aussi un numéro aléatoire (ici 201) et renvoie un paquet SYN-ACK (synchronized-acknowledgement, pour synchronisation et accusé de réception), contenant le numéro de séquence du client incrémenté et le numéro du serveur (ici 1235 et 201).
* Sur réception de ce paquet, le client est considéré comme connecté. Il renvoie un dernier paquet ACK au serveur contenant les numéros de séquences incrémentés de nouveau (donc 1236 et 202).
* Sur réception de ce dernier paquet, le serveur est considéré comme connecté au client.

Tout ce processus permet au client et au serveur de se mettre d’accord sur deux numéros qu’ils choisissent l’un et l’autre. En cas de problème de connexion (par exemple si le client ne reçoit pas le paquet SYN-ACK après un certain temps) client et serveur peuvent essayer de ré-émettre les paquets. Si la ré-émission échoue, la connexion échoue et le client ne peut pas se connecter au serveur. Si la mise en place réussit, alors le serveur et le client partagent une information commune (la paire de numéros de séquence).

 Ils peuvent maintenant garantir des échanges sans perte d’information et de taille arbitraire. Nous illustrons cela sur l'exemple (simplifié) d’un client souhaitant envoyer 3000 octets au serveur. On suppose que les numéros de séquence sont tels que dans la figure précédente en fin de connexion : le numéro de séquence client vaut 1236 et le numéro de séquence serveur vaut 202. Le client peut choisir (pour des raisons matérielles ou de performance) de découper les 3000 octets en trois paquets de 1000 octets, P<sub>1</sub>, P<sub>2</sub> et P<sub>3</sub>. Il envoie donc au serveur trois paquets l’un à la suite de l’autre, en augmentant le numéro de séquence client de la taille du paquet. Le client envoie donc (P<sub>1</sub>, 1236), (P<sub>2</sub>, 2236) et (P<sub>3</sub>,3336). Le serveur renvoie
en réponse des paquets ACK étiquetés par les numéros correspondant (1236,2236 et 3336). Cela permet d’effectuer des vérifications :

* Si le serveur reçoit les trois paquets dans le désordre, il peut les réordonner selon leur numéro croissant et reconstruire le groupe initial de
3000 octets.

* Si le serveur ne reçoit pas le paquet 2236, il n’envoie pas le ACK correspondant. Le client ne recevant pas le ACK , il peut choisir de ré-émettre
uniquement le paquet correspondant à P<sub>2</sub>».

* Si le serveur reçoit des paquets en double (par exemple parce que le client a ré-émis un paquet dont l’original est arrivé entre temps) alors il peut détruire les paquets ayant le même numéro de séquence.

Ce processus relativement simple permet de réaliser un canal de communication avec détection d’erreurs au-dessus du protocole IP. Il illustre aussi l'intérêt du découpage des données en paquets, qui permettent de ne retransmettre que les parties perdues et non pas l'intégralité du message.

