## Modèle OSI

Les observations faites lors de la navigation sur un site Web font ressortir une propriété importante des réseaux informatiques : leur organisation en
différentes couches d’abstraction. En effet,
* certaines problématiques sont très proches du « matériel » et font intervenir des aspects de traitement du signal et plus généralement de physique.
* D’autres sont résolument orientées vers l’informatique, comme la structure particulière que doivent avoir les programmes qui communiquent en réseau.

Cette organisation en couches est un aspect fondamental dans l’étude et la définition de réseaux informatiques et a été formalisée en 1984 dans le modèle OSI (pour l’anglais Open Systems Interconnection) correspondant à la norme ISO 7498:1984 (L'ISO est l’organisation internationale de normalisation qui regroupe les organismes de normalisation nationaux de 165 pays, dont l'AFNOR pour la France).

Ce modèle est structuré en sept couches:

<table style="text-align:center">
    <thead>
        <tr>
            <th >n°</th>
            <th >nom</th>
            <th >PDU</th>
            <th >Exemple de protocole</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>7</td>
            <td>Application</td>
            <td>données</td>
            <td>HTTP,POP,IMAP</td>
        </tr>
        <tr>
            <td>6</td>
            <td>Présentation</td>
            <td>données</td>
            <td></td>
        </tr>
        <tr>
            <td>5</td>
            <td>Session</td>
            <td>données</td>
            <td></td>
        </tr>
        <tr>
            <td>4</td>
            <td>Transport</td>
            <td>segment</td>
            <td>TCP, UDP</td>
        </tr>
        <tr>
            <td>3</td>
            <td>Réseau</td>
            <td>paquet</td>
            <td>IPv4, IPv6, ICMP</td>
        </tr>
        <tr>
            <td>2</td>
            <td>Liaison</td>
            <td>trame</td>
            <td>Ethernet, Wi-fi, ATM</td>
        </tr>
        <tr>
            <td>1</td>
            <td>Physique</td>
            <td>bit</td>
            <td>Ethernet, Wi-fi, OTN</td>
        </tr>
    </tbody>
</table>

Dans l'esprit de cette norme,
* chaque couche est indépendante et possède un rôle bien défini.
* En particulier, elle offre des fonctionnalités que le niveau supérieur peut utiliser.
* Chaque couche définit une unité de données du protocole (PDU pour l’anglais Protocol Data Unit), qui est la quantité d’information que la couche est capable de transmettre « en un coup ».

Dans les couches 1 à 4, le protocole de la couche ignore absolument le contenu des messages qu’il transmet : ce sont de simples suites d’octets.

C’est généralement dans les trois couches les plus hautes (et en particulier la couche « application ») que le protocole a un lien direct avec l’utilisation
qui est faite de l’ordinateur par un utilisateur.

## Modèle Internet

Le modèle OSI peut être considéré comme une approche théorique aux réseaux. Il décrit avec minutie et rigueur les différentes problématiques à considérer lorsque l’on conçoit un nouveau protocole de communication et de quelle manière inscrire ce dernier dans l’une des sept couches du modèle.

Mais bien avant la publication de cette norme, un réseau informatique global s’est développé en suivant ses propres principes, le réseau Internet.

Initialement conçu en 1970 comme un projet militaire américain, le projet ARPANET a rapidement évolué pour devenir la paire de protocole TCP et IP en 1974.

* Le protocole IP (pour l’anglais Internet Protocol) a pour but l’adressage des machines sur le réseau ainsi que le routage des paquets (c’est-à-dire la manière d’envoyer des données entre deux nœuds distants en
passant par des nœuds intermédiaires).

* Le protocole TCP (pour l’anglais Transmission Control Protocol), quant à lui, réutilise les fonctionnalités offertes par IP pour permettre l'envoi de messages de longueur arbitraire et garantir à l’envoyeur que le destinataire a bien reçu l'information.

Ces protocoles ont rapidement été adoptés par les premiers utilisateurs du réseau, qui est devenu petit à petit ce que nous appelons aujourd’hui Internet, le réseau global. Ces protocoles sont d’ailleurs toujours ceux utilisés aujourd’hui, même s'ils ont subi des évolutions depuis 1974. Ces protocoles sont standardisés par l'Internet Engineering Task Force (IETF), une organisation mondiale à but non lucratif.

Cette dernière propose un modèle plus simple que le modèle OSI, nommé modèle Internet et constitué de quatre couches. Ces dernières correspondent approximativement à des couches du modèle OSI:

<table style="text-align:center">
    <thead>
        <tr>
            <th >n°</th>
            <th >n° OSI</th>
            <th >Nom</th>
            <th >Exemple de protocole</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>4</td>
            <td>5,6,7</td>
            <td>Application</td>
            <td>HTTP,POP,IMAP</td>
        </tr>
        <tr>
            <td>3</td>
            <td>4</td>
            <td>Transport</td>
            <td>TCP, UDP</td>
        </tr>
        <tr>
            <td>2</td>
            <td>3</td>
            <td>Réseau</td>
            <td>IPv4, Ipv6, ICMP</td>
        </tr>
        <tr>
            <td>1</td>
            <td>1,2</td>
            <td>Liaison</td>
            <td>Ethernet, Wi-Fi</td>
        </tr>
    </tbody>
</table>

Comme on le voit, dans ce modèle simplifié
* la couche 1 regroupe tous les aspects « bas niveaux »,
* les couches de réseau et de transport correspondent
à leur équivalent dans le modèle OSI et
* une couche générique « application » regroupe tous les aspects qui ne sont pas strictement liés à la transmission des données.

Attention, penser qu'il y a une correspondance exacte entre les deux modèles serait une erreur. Le modèle Internet est apparu en premier (et en parallèle d’autres réseaux et protocoles aujourd’hui tombés en désuétude) et s’est développé avec une architecture souple (les quatre couches n'étant pas strictement séparées en pratique). En réponse à ce développement rapide, et dicté par des considérations d’implémentation, le modèle OSI a été proposé, afin en particulier de servir de guide pour les processus de certification des réseaux informatiques. Il est donc normal que les deux modèles, aux objectifs différents, ne correspondent pas exactement l’un à l’autre. Nous faisons cependant l'hypothèse simplificatrice que le modèle In ternet est séparé en quatre couches bien distinctes et présentons en détail chacune des couches en donnant des exemple de protocoles.

