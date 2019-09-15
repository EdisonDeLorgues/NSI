### Balises neutres, classes et identifiants.

Il existe en HTML deux balises neutres, c’est-à-dire qui n’ont pas de rôle particulier. La première, ```<div>```, est une balise de structure et son comportement par défaut est identique à celui de la balise ```<p>``` (elle représente un bloc de texte). La seconde, ``` <span>```, est une balise de texte, similaire à ```<b>``` ou ```<i>```, mais qui laisse le texte inchangé.

Pour chaque balise d’une page Web, il est possible d'ajouter deux attributs, **id** et **class**.

* L’attribut **id** représente un identifiant et doit être unique dans le fichier, c’est-à-dire qu’il ne doit pas exister un autre attribut id dans le fichier ayant la même valeur.

* L’attribut **class** contient une suite de noms
de classes séparés par des espaces. Un identifiant permet de désigner un élément HTML dans tout le document. Les classes permettent d’étiqueter
certains éléments. Ces étiquettes seront utilisées dans la définition du style graphique des éléments.

```HTML
<h1 id="titrel">À faire</h1>
<ul>
    <li class="pair">Acheter du pain</li>
    <li class="impair">Arroser les plantes</li>
    <li class="pair urgent">Apprendre HTML</li>
    <li class="impair">Dormir</li>
</ul>
```

<h1 id="titrel">À faire</h1>
<ul>
  <li class="pair">Acheter du pain</li>
  <li class="impair">Arroser les plantes</li>
  <li class="pair urgent">Apprendre HTML</li>
  <li class="impair">Dormir</li>
</ul>

Comme on peut le constater, les informations de classe et d'identifiant n’ont aucun impact sur l'affichage.

# CSS

Le langage **CSS** (pour l'anglais Cascading Style Sheets ou feuilles de style en cascade) est un langage permettant de définir les propriétés graphiques
des éléments HTML constituant une page Web.

## Un exemple

Voici un exemple de document HTML utilisant le langage CSS.

```HTML
<p style="text-align:right;">
On écrit
  <span style="border:1pt solid black;">
    paragraphe
  </span>
de texte, mais cette fois on
  <span style="color:gray">
    modifie
  </span>
le style graphique
  <span style="border:1pt solid black;">
    des éléments.
  </span>
</p>
```

<p style="text-align:right;">
On écrit
  <span style="border:1pt solid black;">
    paragraphe
  </span>
de texte, mais cette fois on
  <span style="color:gray">
    modifie
  </span>
le style graphique
  <span style="border:1pt solid black;">
    des éléments.
  </span>
</p>

On remarque en premier lieu l’ajout de l’attribut **style** à plusieurs éléments. Cet attribut, autorisé pour tous les éléments, permet de définir des propriétés
CSS pour l’élément concerné.

Ici, on indique que le texte contenu dans l’élément p doit être justifié à droite. On remarque ensuite l’utilisation de trois
éléments span dans le texte.

Le premier et le troisième ajoutent une bordure noire à leur contenu. Le second change la couleur du texte. L'écriture de feuilles de style CSS comprend deux aspects.

* Le premier est la définition du style graphique via des propriétés et leur valeurs.
* Le second, plus complexe, consiste à décrire à quels éléments s’applique ces styles. Comme on peut le constater ici, l’utilisation de l’attribut style rend le code HTML peu lisible. De plus, l’attribut style permettant de mettre une bordure est dupliqué, ce qui rend la maintenance du code du document compliquée. En effet, si l’on souhaite maintenant modifier la bordure de tous ces éléments afin qu’elle soit plus épaisse et grise, nous devons éditer le fichier en deux endroits. On imagine facilement que, si notre page comporte des dizaines d'éléments avec bordure, faire se travail de remplacement sera fastidieux.

CSS propose une manière alternative par le biais de sélecteurs CSS. En utilisant les sélecteurs, le document précédent peut être écrit de la façon suivante :

```HTML
<!DOCTYPE html>
<html lang="fr">

<head>
<title>CSS 2</title>
<meta charset="utf-8" />

<style>
p { text-align: right; }
-bord { border:ipt solid black; }
#n42 { color: gray; }
</style>

</head>

<body>
  <p>
      On écrit un <span class="bord">paragraphe</span>
      de texte, mais cette fois on <span id="n42">modifie</span>
      le style graphique <span class="bord">des éléments.</span>
  </p>
</body>

</html>
```

Le document ci-dessus produirait le même rendu graphique que précédemment. (On rappelle que dans la balise ```<p>```, les retours à la ligne et les espaces
blancs sont ignorés et donc que l’indentation différente utilisée ici n’a pas d’incidence sur le rendu.) Dans le corps du document, les informations de
style ont disparu. Elles ont été remplacées par endroit par des attributs class et id qui, comme nous l’avons déjà expliqué, ne modifient pas par eux-mêmes le rendu graphique. Ils permettent en revanche de déporter les
informations de style dans une balise **style** présente dans l’entête du document. Dans cette balise,
* la ligne

```css
p { text-align: right; }
```

indique que toutes les balises ```<p>``` du document ont leur texte justifié à droite (ce style s'applique donc à l’unique balise du document ```<p>```).

* La seconde ligne
```css
.bord { border: ipt solid black; }
```

indique que toutes les balises possédant la valeur "bord" dans leur attribut class, quel que soit leur nom, ont une bordure d’une épaisseur de un point, en trait plein et noire. Ce style est appliqué au premier et troisième élément span du document, car tous les deux possèdent un attribut class="bordure".

* Enfin, la troisième ligne
```css
#n42 { color: gray; }
```

indique que l’unique balise dont l’attribut id vaut "n42" doit avoir un texte de couleur grise. Cette approche est plus « propre » que celle utilisant l’at-
tribut style : elle sépare en effet la structure du document (HTML) de sa présentation graphique (CSS). Elle permet aussi de factoriser les styles communs à plusieurs éléments en se basant soit sur le nom de la balise, soit sur la valeur de l’attribut class. Un inconvénient subsiste cependant. Si l'on possède plusieurs fichiers HTML pour lesquels on souhaite appliquer le même style graphique, on souhaiterait ne pas dupliquer la balise style dans tous les fichiers, ce qui encore une fois rendrait la modification de style
peu aisée. Il est possible de rajouter dans l’entête d’un fichier HTML une balise ```<link>``` de la manière suivante

```HTML
<!DOCTYPE html>
<html lang="fr">

<head>
  <title>CSS 3</title>
  <meta charset="utf-8" />
  <link href="style.css" rel="stylesheet" type="text/css" />
</head>

<body>
</body>

</html>
```

L'attribut href permet, comme pour une balise ```<a>```, de donner l’emplacement du fichier style.css (ici, le fichier est simplement dans le même répertoire que le fichier HTML). Le fichier CSS est écrit avec la même syntaxe que le contenu de la balise style. Cette manière d'associer une page à un fichier de style est la plus propre. Elle respecte intégralement le principe de séparation entre présentation des données et structuration du contenu. Sauf dans des cas très particuliers, l’utilisation de l’attribut style est à
proscrire.

## Quelques propriétés CSS

Tout comme HTML, le format CSS est standardisé par le W3C. La spécification est découpée en différents modules traitant d’aspects spécifiques :
couleurs, sélecteurs, disposition des éléments. Nous donnons un aperçu de
quelques propriétés.

### Modèle de boîte.
Tout élément HTML possède une boîte rectangulaire
qui délimite son contenu. Prenons l’exemple d’un lien.

```HTML
<a href="https://www.monsite.org">Mon lien</a>
```

Lorsque le navigateur dessine ce dernier, il définit une boîte rectangulaire possédant plusieurs zones distinctes.

* La première zone est la zone interne dans laquelle le contenu de la balise est dessiné (ici le texte « Mon lien »).
* Il est possible de définir pour chaque boîte une bordure grâce à la propriété CSS **border**.
* La zone entre le contenu et la bordure s’appelle l'ajustement. Sa taille est modifiable grâce à la propriété **padding**.

* Enfin, la zone au delà dela bordure est appelée la marge. Sa taille est définissable via la propriété
**margin**.

Comme nous l’avons vu, il existe en HTML deux catégories d'éléments textuels : les balises de structures (telles que ```<p>```, ```<ul>```, etc.) qui créent une
boîte et forcent un retour à la ligne et les balises de textes (telles ```<a>```, ```<b>```,```<i>```, etc.) qui placent leur contenu dans le flot du texte. Ce comportement est dirigé par la propriété CSS display. La valeur peut être inline (la boîte est affichée dans le corps du texte), block (la boîte impose un retour à la
ligne) ou none (la boîte est masquée, elle n'apparaît donc plus à l'écran!).

###Longueurs, couleurs.

De nombreuses propriétés CSS indiquent des longueurs (taille d’une bordure, d’un ajustement, taille de police). Leur valeur est toujours un nombre, suivi d’une unité. Parmi les unités légales en CSS, on retrouve le pixel (px) et le point (pt, qui est la même unité que celle utilisée pour les polices de caractères dans de nombreux logiciels). On peut aussi donner la taille de certains éléments de manière relative, en pourcentage (%)
de la taille de l’élément contenant.

Pour ce qui concerne les couleurs, il est possible d'utiliser soit leur nom en anglais (red, gray, blue, LightGreen, etc.), soit en notation hexadécimale #rruubb où rr, vu et bb représente des valeurs sur deux chiffres entre 00 et FF (soit 255 en base 10). Par exemple, le noir se note #000000 et le violet peut s’obtenir avec #ff00ff. Étant donnée une boîte, on peut définir sa
couleur de fond par la propriété background et la couleur de son texte par la propriété color.

Nous donnons dans le tableau ci-après quelques propriétés CSS.

<table>
  <tr>
    <td><b>Propriété</b></td>
      <td><b>Valeur</b></td>
      <td><b>Description</b></td>
  </tr>
  <tr>
    <td>display</td>
    <td>none, block ou inline</td>
    <td>mode d'affichage de la boîte</td>
  </tr>
  <tr>
    <td>background</td>
    <td> couleur</td>
    <td>couleur de fond de la boîte</td>
  </tr>
  <tr>
    <td>color</td>
    <td>couleur</td>
    <td>couleur de texte</td>
  </tr>
  <tr>
    <td>border</td>
    <td>taille motif couleur ou none</td>
    <td>Si none la bordure est masquée. Sinon, on donne la taille, le motif (solid, doted ou dashed) et la couleur séparés par des espaces</td>
  </tr>
  <tr>
    <td>margin</td>
    <td>longueur</td>
    <td>taille des marges</td>
  </tr>
  <tr>
    <td>padding</td>
    <td>longueur</td>
    <td> taille des ajustements</td>
  </tr>
  <tr>
    <td>text-decoration</td>
    <td>none, underline, overline ou line-through</td>
    <td> décoration du texte</td>
  </tr>
  <tr>
    <td>text-align</td>
    <td>left, right, center ou justify</td>
    <td> justification du texte</td>
  </tr>
  <tr>
    <td>font-family</td>
    <td>fixed, serif ou sans-serif</td>
    <td> nom de la police</td>
  </tr>
  <tr>
    <td>font-weight</td>
    <td>normal, light, bold ou bolder</td>
    <td> graisse de la police</td>
  </tr>
  <tr>
    <td>font-style</td>
    <td>normal ou italic</td>
    <td> style de la police</td>
  </tr>
  <tr>
    <td>font-size</td>
    <td>longueur ou xx-small, x-small, small, normal,  large, x-large ou xx-large</td>
    <td> taille de la police</td>
  </tr>
</table>

## Sélecteurs CSS

Le langage CSS définit une notion de sélecteur, c’est-à-dire un moyen d'identifier à quels éléments s’applique une propriété. La syntaxe des sélecteurs étant très complexe, et faisant l’objet à elle seule d’une spécification, nous ne donnons ici qu’un sous-ensemble de ces fonctionnalités.

Dans une feuille de style (1.e. dans un fichier CSS ou dans la balise style d’un document HTML), une règle CSS est donnée sous la forme suivante :

P<sub>1</sub> P<sub>2</sub> ... P<sub>n</sub> {
Prop<sub>1</sub> : v<sub>1</sub>;
Prop<sub>2</sub> : v<sub>2</sub>;
...
prop<sub>k</sub> : v<sub>k</sub>;
}

La partie P<sub>1</sub> ... P<sub>n</sub>, est le sélecteur CSS. Il est constitué d’un certain nombre
de pas ou étapes. L'étape p1 sélectionne tous les éléments situés sous la balise html qui vérifient ces conditions. L'étape P<sub>2</sub> sélectionne tous les éléments qui
vérifient P<sub>2</sub> et qui sont contenus dans les balises des éléments renvoyés par P<sub>1</sub>. On répète le processus jusqu’à arriver au dernier pas. La syntaxe d’un pas peut être :

* un nom de balise comme a, div ou li. Le pas sélectionne alors toutes les balises ayant ce nom;

* un nom de classe, préfixé par un point, comme .pair, .impair, .encadrer. Le pas sélectionne alors toutes les balises dont l’attribut class contient le nom de la classe donnée, indépendamment du nom de la balise ;

* un identifiant, préfixé par un dièse, comme #n42, #toto ou #menu. Le pas sélectionne alors l’unique balise dont l’attribut id est donné;

* le symbole \*. Le pas sélectionne n'importe quelle balise.

Dans un pas, on peut combiner nom de classe et nom de balise ou identifiant et nom de balise, en les concaténant sans espace. Par exemple, li.pair
sélectionne toutes les balises ```<li>``` dont l’attribut class contient pair.

On peut donc former des sélecteurs complexes tels que

```css
div#menu li a { color: pink; background: yellow; }
```

On indique ici que l’on souhaite trouver tous les liens (balise ```<a>```) qui sont à l'intérieur d'éléments ```<li>``` qui sont eux-mêmes à l’intérieur de l’unique balise ```<div>``` dont l'identifiant est menu. Attention, on notera la différence entre « div#menu » et « div #menu » (remarquer l’absence d’espace dans le premier cas).

* Dans le premier cas, il s’agit d’un unique pas qui sélectionne l’unique élément dont l'identifiant est menu et dont la balise doit être div.
* Dans le deuxième cas, on sélectionne l’unique élément dont l'identifiant est menu s’il est contenu dans une balise div (mais ce n’est pas forcément la balise div qui a l’identifiant menu). En d’autres termes, le premier sélecteur sélectionne un élément tel que :

```HTML  
<div id="menu"> ... </div>
```
  alors que le second fonctionne sur un document contenant

```HTML  
<div>
... contenu arbitraire ...
... <p id="menu" > ... </p> ...
</div>
```

C’est alors l’élément p interne qui est sélectionné.

## Cascades ?

Nous abordons enfin le dernier aspect des feuilles de style CSS, à savoir l’aspect cascade évoqué dans leur nom. Ce dernier est lié à la manière dont sont gérées les priorités. En effet, lorsque plusieurs règles s'appliquent en même temps sur le même élément, lesquelles choisir ? Cette situation peut par exemple se produire si on a dans le document HTML un paragraphe  comme ceci

```HTML   
<p style="color:red;font-weight:bold">Du texte</p>
```
  et dans l’entête du même fichier

```HTML
<style>
 p {
   color: blue;
   border:1pt solid black;
  }
</style>
```

  Le paragraphe aura son texte en gras et une bordure noire. En effet, les deux propriétés étant indépendantes, la propriété de bordure est donnée par la balise style de l’entête alors que la propriété de graisse de la police est donnée par l’attribut style.
  La couleur du texte, en revanche, sera rouge. La règle générale (simplifiée) est que l’attribut style est plus prioritaire que la balise style. Un fichier inclus au moyen d’une balise Link avant une balise style est moins prioritaire que cette dernière. S’il est inclus après, il est plus prioritaire (pour les propriétés en conflit).

  La dernière situation de conflit possible est celle où deux règles dans un même fichier ou dans une même balise style s'appliquent au même élément. Considérons l’élément suivant et les trois règles CSS associées.

```html
<div id="divi">
  <p id="p2" class="para" >Du texte</p>
</div>
```

```css
#p2 { color: red; text-decoration: underline; }
div p { color: blue; border: 1pt solid black; }
div .para { color: green; font-family: monospace; }
```

Ces trois sélecteurs sélectionnent l’élément p du document : le premier car il a l'identifiant p2; le second car c’est bien un p se trouvant à l’intérieur
d’un div; et le troisième car c’est un élément ayant la classe para et se trouvant à l’intérieur d’un div. Le texte de ce paragraphe sera souligné, avec une bordure noire et en police fixe, car les trois propriétés sont indépendantes. La couleur de texte, en revanche, sera le rouge, ce qui peut sembler surprenant. Le standard CSS définit une règle précise pour lever de telles ambiguïtés. Pour chacun des sélecteurs en conflit, on calcule un triplet (i,c,b) où à est le nombre d’identifiants dans le sélecteur, c le nombre de
classes dans le sélecteur et b le nombre de balises (le symbole * ne compte pas comme une balise). On compare alors les triplets, d’abord selon les 5, puis en cas d’ex-aequo selon les c, puis selon les b (donc en utilisant l’ordre lexicographique). Le sélecteur le plus grand est celui qui s’applique. S’il reste deux sélecteurs ayant le même triplet, alors seul le dernier dans l’ordre du fichier est choisi. Pour notre exemple ci-dessus, les triplets sont respectivement (1,0,0), (0,0,2) et (0,1,1). C’est donc la première règle qui l’emporte, car son triplet est supérieur aux autres sur la première composante.

# À retenir
Le langage HTML est le langage de description des pages
Web. Ces dernières sont des documents structurés par des balises suivant un ensemble de règles de bonne formation. Après avoir défini la structure d’une page, on peut définir sa charte graphique au moyen du
langage CSS qui permet d’ajuster finement toutes les caractéristiques graphique d’une page Web.
