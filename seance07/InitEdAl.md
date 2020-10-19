# Séance 7 : Initiation à l’édition scientifique

---

## Les enjeux et les métiers de l’édition

---

Les éditions ont pour but de rendre accessible et compréhensible un texte pour un lectorat donné.

Il existe différentes formes d'édition (liste non exhaustive) :

* Les éditions génétiques
	* [Madame Bovary  : l'histoire du texte à travers ses brouillons](http://www.bovary.fr/folio_visu.php?folio=458&mode=sequence&mot)
* Les éditions "paléographiques"
	* [Le Didascalicon d’Hugues de Saint-Victor](http://theleme.enc.sorbonne.fr/dossiers/vue100.php)
* Les éditions critiques
	* [La Queste del saint Graal](http://txm.ish-lyon.cnrs.fr/bfm)

---

## Les enjeux d'une édition "paléographique"

Geste: un corpus de chansons de geste, <http://dev.chartes.psl.eu/elec/geste/>

Corpus test : La séquence de sainte Eulalie

* Lecture interactive : <https://bibliotheque.ville-valenciennes.fr/iguana/www.main.cls?v=6bb63866-fa45-4563-a75e-626d3cccb43c>
* Voir le manuscrit sur Gallica : <https://gallica.bnf.fr/ark:/12148/btv1b84526286/f288.item>
* Obtenir le texte sur wikisource :
<https://fr.wikisource.org/wiki/Séquence_de_sainte_Eulalie>

---

### Définition des enjeux 

 - Identifier et délimiter les phénomènes à signaler;
 - Définir les futurs usages de l'édition;
 - Choisir son protocole d'encodage;
 
---

### Les éléments que l'on veut reproduire

- Mise en page;
- Mise en valeur typographique;
- Graphie originale du texte.


---

### Les éléments que l'on veut apporter :

- Résolutions des abréviations;
- Régularisations des graphies;
- Corrections (si nécessaires).

---

## Les solutions TEI 

---

### Le set pour la [structuration des textes](http://www.tei-c.org/release/doc/tei-p5-doc/fr/html/DS.html)

*Quelques balises courantes pour la structuration du texte*

* `<div>` contient un niveau de hiérarchie textuelle;
* `<p>` contient un paragraphe;
* `<l>` contient un seul vers;
* `<lg>` contient un groupe de vers fonctionnant comme une unité formelle, par exemple une strophe, un refrain, un paragraphe en vers;
* `<pc>`permet de signaler la ponctuation

---
*Quelques balises courantes pour signaler la mise en page du texte*

* `<lb>` permet de signaler un retour à la ligne;
* `<cb>` permet de signaler un changement de colonne;
* `<pb>` permet de signaler un changement de page/folio;

---

**Exercice 1**

À l’aide des documents sur la *Séquence de sainte Eulalie* :
- Structurer le texte selon ses caractéristiques textuelles;
- Encoder la structuration matérielle du texte dans le manuscrit;
- Lier le texte à l'image correspondante dans Gallica

---
### La [description des sources primaires](http://www.tei-c.org/release/doc/tei-p5-doc/fr/html/PH.html)

*Quelques balises courantes*

* Développements d’abréviation : `<choice><abbr></abbr><expan></expan></choice>`;
* Régularisations  : `<choice><orig></orig><reg></reg></choice>`;
* Corrections : `<choice><sic></sic><corr></corr></choice>`.

---
#### Traitement des variations graphiques dans un fichier TEI

[*Le module gaiji*](<http://www.tei-c.org/release/doc/tei-p5-doc/en/html/WD.html>)
`<encodingDesc>`
         `<charDecl>`
            `<char xml:id="q1">`
               `<charName>Q SEMICOLON</charName>`
               `<charProp>`
                  `<localName>entity</localName>`
                 `<value>&#61868;</value>`
               `</charProp>`
            `</char>`
         `</charDecl>`
`</encodingDesc>`
[...]
`<l>Niule cose non la pouret om<g ref="#q1">que</g> pleier.</l>`

---

*Déclaration d'entités*

Exemple : `<!ENTITY pbarre-pre "<choice><abbr>&#58981;</abbr><expan>pre</expan></choice>" >`

La déclaration se fait dans une DTD interne, soit dans une DTD externe.

---

NB : Dans une édition numérique, il est conseillé d'utiliser les caractères UTF-8. Il existe des [fontes spécialisées](https://folk.uib.no/hnooh/mufi/fonts/) dans la représentation des manuscrits : 

* Palemonas MUFI
* Junicode 

Pour les caractères qui n'existent pas dans toutes les fontes, passer par l'entité décimale XML.

Astuce : convertisseur pour les caractères http://hapax.qc.ca/conversion.fr.html

---

**Exercice 2**

- Reprendre le fichier XML de la *Séquence de sainte Eulalie*;
- Encoder les régularisations graphiques;
- Encoder les abréviations et leur développement.

---
## Lier son encodage à des zones d’un fac-similé

Ex : *Le Didascalicon* d’Hugues de Saint-Victor : <http://theleme.enc.sorbonne.fr/dossiers/vue100.php> 

Ex : Lexture interactive de la *Séquence de sainte Eulalie*
<https://bibliotheque.ville-valenciennes.fr/iguana/www.main.cls?v=6bb63866-fa45-4563-a75e-626d3cccb43c>

---

### Comment faire ?

TEIguidelines [11.1 Digital Facsimiles](http://www.tei-c.org/release/doc/tei-p5-doc/fr/html/PH.html#PHFAX)

* Déclarer un élément `<facsimile>` dans l'élément racine TEI;
* Déclarer en élément `<surface>`, enfant de `<facsimile>`
* Déclarer en élément `<graphic>`, enfant de `<surface>`
	* `<graphic url='adresse_image' width='largeur' height='longueur' />`

---

* Déclarer des éléments `<zone>`, enfants de `<surface>`, pour chacune des parties de l'image à identifier
	*  `<zone xml:id="<!-- identifiant -->" ulx="<!-- coordonnée -->" uly="<!-- coordonnée -->" lrx="<-- coordonnée -->" lry=" <!--coordonnée -->" />`
	
| @ | définition |
| :----------------- | :----------- |
| *ulx*  | donne la valeur x de l'abscisse du coin supérieur gauche d'un rectangle.|
|*uly* | donne la valeur y de l'ordonnée du coin supérieur gauche d'un rectangle. |
| *lrx* | donne la valeur x de l'abscisse du coin inférieur droit d'un rectangle. |
| *lry* | donne la valeur y de l'ordonnée du coin inférieur droit d'un rectangle.

---
Astuce pour les coordonnées : [TEIzoner](http://teicat.huma-num.fr/check.php)

**Exercice 3**

- Reprendre le fichier XML de la *Séquence de sainte Eulalie*;
- Récupérer l’image du folio où se trouve le texte;
- Lier l’encodage à des zones du folio.

