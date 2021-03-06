<p>Dans la barre d'adresse de votre navigateur web vous trouverez, quand vous visitez un site, des choses du genre : "http://www.ac-grenoble.fr/disciplines/informatiquelycee/index.html". Nous aurons l'occasion de reparler du "http" et du "www.ac-grenoble.fr" plus tard. La partie "/disciplines/informatiquelycee/index.html" s'appelle une URL.</p>
<p>Une URL (Uniform Resource Locator) permet d'identifier une ressource (par exemple un fichier) sur un réseau.</p>
<p>L'URL indique « l'endroit » où se trouve une ressource sur un ordinateur. Un fichier peut se trouver dans un dossier qui peut lui-même se trouver dans un autre dossier...
On parle d'une structure en arborescence, car elle ressemble à un arbre à l'envers :</p>

<img src="url.jpg" alt="arbo" align="center"/>

<p>Comme vous pouvez le constater, la base de l'arbre s'appelle la racine de l'arborescence et se représente par un /</p>
<h4>Chemin absolu ou chemin relatif ?</h4>
<p>Pour indiquer la position d'un fichier (ou d'un dossier) dans l'arborescence, il existe 2 méthodes :
indiquer un chemin absolu ou indiquer un chemin relatif. Le chemin absolu doit indiquer « le chemin » depuis la racine.
Par exemple l'URL du fichier fichier3.jpg sera : /dossier2/dossier3/fichier3.jpg</p>
<p>Remarquez que nous démarrons bien de la racine / (attention les symboles de séparation sont aussi des /)</p>
<p>Imaginons maintenant que le fichier fichier1.css fasse appel au fichier fichier3.jpg (comme un fichier HTML peut
faire appel à un fichier CSS). Il est possible d'indiquer le chemin non pas depuis la racine,
mais depuis le dossier (dossier2) qui accueille le fichier1.css, nous parlerons alors de chemin relatif  :</p>
<p> dossier3/fichier3.jpg</p>
<p>Remarquez l’absence du / au début du chemin (c'est cela qui nous permettra de distinguer un chemin relatif et un chemin absolu).</p>
<p>Imaginons maintenant que nous désirions indiquer le chemin relatif du fichier fichier1.css depuis l'intérieur du dossier dossier4.</p>
<p>Comment faire ?</p>
<p>Il faut « remonter » d'un « niveau » dans l'arborescence pour se retrouver dans le dossier dossier2 et ainsi
pouvoir repartir vers la bonne « branche ». Pour ce faire il faut utiliser 2 points : ..</p>
<p>../dossier2/fichier1.css</p>
<p>Il est tout à fait possible de remonter de plusieurs « crans » : ../../ depuis le dossier dossier4 permet de « retourner » à la racine.</p>
<h4>À faire vous-même 1</h4>
<p>Soit la structure en arborescence suivante:</p>

<img src="url.jpg" alt="arbo" align="center"/>

<p>
Le contenu du fichier "fichier7.odp" utilise le fichier "fichier5.svg". Donnez le chemin relatif qui devra ẽtre renseigner dans le fichier "fichier7.odp" afin d'atteindre le fichier "fichier5.svg".
</p>
<p>
Donnez le chemin absolu permettant d'atteindre le fichier "fichier6.html".
</p>
<hr>
<p>Remarque : la façon d'écrire les chemins (avec des slash (/) comme séparateurs) est propre aux systèmes dits « UNIX »,
par exemple GNU/Linux ou encore Mac OS. Sous Windows, ce n'est pas le slash qui est utilisé,
mais l'antislash (\). Pour ce qui nous concerne ici, les chemins réseau (et donc le web), pas de problème, c'est le slash 
qui est utilisé. </p>
