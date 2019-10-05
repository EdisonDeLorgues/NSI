## Terminologie et généralités

En toute généralité, un **réseau** est un ensemble de **nœuds** ou composants reliés entre eux par des **liens**. Un réseau permet la distribution de flux (électricité, eau, etc.) ou de quantité discrètes (information, courriers, personnes) entre les nœuds qui le composent.

Un **réseau informatique** est un réseau dont
* les nœuds sont des équipements informatiques (ordinateurs, routeurs, concentrateurs, etc.) et
* les liens peuvent être de nature diverse (câbles de cuivres, fibre optique, liaisons satellites, ondes radios, etc.).

Les réseaux informatiques permettent l'échange d’information entre les nœuds.

Une **interface** est le point de raccordement entre un lien et un nœud. Elle peut être matérielle (une carte réseau intégrée à l’ordinateur est une interface matérielle) ou logicielle (l’ensemble des fonctions systèmes permettant d'envoyer et recevoir des données forment une interface logicielle).

Un **protocole** est un ensemble de règles permettant d'établir, mener et terminer une communication entre deux entités. Dans le cadre des réseaux informatiques, les protocoles sont utilisés pour garantir différentes propriétés lors de la transmission de données, comme l’absence d’erreur (l'information est transmise sans perte de données), l'efficacité (l'information est transmise le plus rapidement possible), ou encore la confidentialité (seul le destinataire peut obtenir l'information).

De manière informelle, lorsque que des données sont envoyées à travers le réseau en utilisant un protocole, ce dernier va y ajouter des méta-données, c’est-à-dire de l’information permettant de s’assu-
rer que la communication se passe bien.

Par exemple, on peut faire précéder les données par un entier représentant leur longueur en octets.

Un **service réseau** est une application capable de communiquer en réseau et proposant des fonctionnalités.

Par exemple,
* un service Web fournit à des
programmes spéciaux (les navigateurs Web) les ressources qu’ils demandent (des pages Web au format HTML).
* Un service de messagerie instantanée
(communément appelé « chat » et francisé en « tchat ») propose des salons de discussions.
* Des applications spéciales (par exemple sur téléphone)
se connectent au service et permettent à leurs utilisateurs d'échanger des messages.

Un **serveur** est un dispositif matériel ou logiciel exécutant un service.

On utilise le même mot pour désigner à la fois la machine où s'exécute le service et le logiciel qui permet son exécution.

Par exemple, le serveur Web Apache est un logiciel offrant le service de distribution de pages Web via
le protocole HTTP. Il s'exécute sur un serveur matériel.

De manière duale, on appelle client à la fois la machine et l’application se connectant par le réseau à un serveur.

Par exemple, le navigateur Web est l’application cliente
se connectant au serveur Web.

Enfin, le modèle client-serveur est la principale manière de concevoir des applications en réseau sur Internet. Dans ce modèle, un serveur (logiciel)
propose un service (par exemple la distribution de page Web).

* Le serveur est perpétuellement en attente de connexions.
* Les clients se connectent à tout moment et sont traités de manière individuelle. En particulier, ils ne communiquent qu’avec le serveur et ne communiquent pas entre eux.

Cela donne une architecture en étoile, le serveur s’exécutant quelque part sur le réseau et les clients s’y connectant de n’importe quel endroit et à n’importe quel moment.
