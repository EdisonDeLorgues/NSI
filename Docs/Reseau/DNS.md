### DNS, l'annuaire d'Internet

En conclusion de cette présentation des réseaux, nous décrivons le système de résolution de noms (ou DNS pour Domain Name System), qui est un protocole de la couche d'application. Ce dernier (qui utilise en général UDP sur le port 53, mais peut aussi utiliser TCP) permet de maintenir des annuaires pour faire correspondre des noms symboliques, facilement utilisables par les humains, à des adresses IP. En effet, comme on l’a vu dans les paragraphes précédents, le seul moyen d'identifier une machine sur le réseau est son adresse IP.

Que se passe-t-il alors lorsque l’on indique au navigateur Web que l’on souhaite se connecter au site wuw.nsi-premiere.fr ? Les **serveurs DNS** sont un ensemble de serveurs hiérarchisés agissant comme des annuaires.

* Au sommet de la hiérarchie existent des serveurs dits « racines ». Ces derniers connaissent les serveurs à contacter pour les domaines de premier niveau (ou TLD pour l’anglais Top Level Domain). Ces derniers correspondent au .fr, .com, .edu, .net et toutes les autres extensions possibles.

* Les serveurs DNS des domaines de premier niveau connaissent l'adresse des serveurs contenant les adresses des domaines de second niveau (dans notre exemple nsi-premiere est le domaine de second niveau).

* Ces derniers permettent ensuite de contacter les serveurs connaissant les adresses des sous-domaines (dans notre exemple, www est le sous-domaine).

En pratique, lorsque l’on configure une connexion IP sur un ordinateur, on définit aussi l’adresse de serveurs DNS (par exemple ceux du fournisseur d’accès à Internet). Ces derniers agissent comme un « cache » :
* lorsqu'une machine leur demande l'IP pour un nom de domaine, ils la renvoient directement s’ils la connaissent déjà.
* Sinon, ils procèdent à la requête récursive décrite plus haut (en décomposant le nom demandé), puis une fois la réponse obtenue, ils mémorisent l’IP du nom de domaine complet pour pouvoir répondre plus rapidement aux prochaines requêtes.
