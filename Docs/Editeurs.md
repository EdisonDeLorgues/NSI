# L’éditeur de textes (en anglais text editor) :

C’est un outil qui permet de manipuler un fichier au format texte brut (en anglais plain text), c’est à dire uniquement des caractères 
alphanumériques. Le plus connu est le bloc-notes de Windows. Les éditeurs les plus simples proposent les fonctions
suivantes:
* taper du texte ;
* effacer ;
* copier/couper/coller ;
* enregistrer, enregistrer sous ;
* imprimer (en caractères machine à écrire).

Et c’est tout ! Pas de choix de fontes, de taille de caractère, etc. Les éditeurs plus évolués incluront la recherche 
de texte, la coloration syntaxique (pour la programmation et les langages basés sur le texte brut comme HTML ou LaTeX),
et pour les éditeurs les plus puissants (Vim,Emacs...) ils n’ont quasiment pas de limites, sinon qu’ils travaillent
toujours uniquement sur du texte brut.

L’éditeur est donc un logiciel indispensable à tous ceux qui travaillent sur ce type de fichier:
* les programmeurs ;
* les administrateurs système ;
* les webmasters.

# Le traitement de texte (en anglais word processing) :

C’est un outil qui permet de mettre en forme un texte d'un point de vue typographique (en anglais formated text).
Un logiciel de traitement de texte contient de multiples fonctions, permettant
* la saisie; 
* la correction ;
* la mise en forme d'un texte; 
* regroupant par la même occasion tout type 
  * de polices ;
  * de couleurs ; 
  * de typographies ; 
  * de paragraphe ; 
  * de mise en page .
  
 # 1.2  Formateur de textes :
 
 Le formateur de textes est un outil qui comme son nom l’indique, met en forme un texte, à partir d’un fichier source
 en texte brut mais contenant des indications de structure (balises). C’est à dire que, mélangées au texte, 
 se trouvent des indications de structure:
 * titre ; 
 * chapitre ;
 * section ;
 * sous-section etc.

Le formateur de textes sait reconnaître ces balises et les interpréter. C’est ainsi que procède 
l'interprétateur HTML de votre navigateur internet ou le logiciel Latex.
 
Exemple HTML:

```html
My <span style="color:red">Important</span> Heading
Voici deux <span style="font-size:160%;">Gros mots</span>.
```

L'interpréteur html du navigateur donnera le résultat suivant:

My <span style="color:red">Important</span> Heading
Voici deux <span style="font-size:160%;">Gros mots</span>.
 
Exemple Latex:
 
 ```latex
 \documentclass{minimal}
\begin{document}
  \[\sum_{n=1}^{+\infty}\frac{1}{n^2}=\frac{\pi^2}{6}.\]
\end{document}
```
L'interpréteur latex engendrera le  résultat suivant:

<img src="./latex.svg" alt="rendu latex" height="50"/>
