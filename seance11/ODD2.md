# Séance 12 : ODD (2) – Documenter et personnaliser
---
## I-Documenter son ODD

L’ODD comporte :
- un élément racine TEI ; 
- un teiHeader ;
- un élément text ;

L’élément body peut contenir des div à niveau (div1, div2, etc.)
On peut structurer sa documentation dans une première div1 et placer ses spécifications.

---

L’intégralité des spécifications XML est englobée dans un **schemaSpec**

- Les déclarations sont organisées grâce aux éléments suivants (liste non exhaustive)  :
	- **moduleSpec** (spécification de module) documente la structure, le contenu et les fonctions d’un module.
	- **moduleRef** (référence de module) référence un module qui doit être incorporé dans un schéma.
	- **elementSpec** (spécification d’élément) documente la structure, le contenu et l’emploi d’un élément.
	- **classSpec** (spécification de classe) contient des informations de référence pour une classe d’éléments TEI, c’est-à-dire un groupe d’éléments qui figurent ensemble dans des modèles de contenu ou qui partagent un attribut commun, ou qui ont l’un et l’autre.

---

### 1-Les éléments structurants de la documentation

Dans l’introduction (première div1), au sein d’un texte rédigé :

- **specList** (liste de spécification) marque l’endroit où insérer une liste de descriptions dans le texte documentaire ;
- **specDesc** (specification description) indique qu’une description de l’élément particulier ou de la classe particulière doit être incluse à ce point dans un document ;
- **egXML** et **@xmlns="http://www.tei-c.org/ns/Examples** permettent d’insérer des exemples en XML dans sa documentation ;

---
#### Exemple : 
`<head>`Le fileDesc`</head>`
`<p>`Le `<gi>`fileDesc`</gi>` comporte lui-même :
`<specList>`
`<specDesc key="titleStmt"/>`
[...]
`</specList>`
Le `<gi>`sourceDesc`</gi>` contient toutes les informations nécessaires sur le manuscrit de base, C`<hi rend="exp">`1`</hi>``<note>`Le sigle correspond au manuscrit 412 de la Bibliothèque Nationale de France`</note>`.`</p>`
`<egXML xmlns="http://www.tei-c.org/ns/Examples">`
  `<msIdentifier>`
  `<country>`Paris`</country>`
  `<settlement>`Bibliothèque nationale de France`</settlement>`
                                [...]
 `</egXML>`
 
 ---
 Dans les déclarations d’éléments 
 
- Dans **elementSpec** ou **attDef**.
	**gloss** (glose) identifie une expression ou un mot utilisé pour fournir une glose ou une définition à quelque autre mot ou expression.
	**desc** (description) contient une courte description de l’objet documenté par son élément parent, qui comprend son utilisation prévue, son but, ou son application là où c’est approprié.
`<elementSpec ident="lem" mode="change">`
 `<gloss>Lemme</gloss>`
 `<desc>Permet de signaler la leçon choisie dans le texte édité.</desc>`
 [...]
 `</elementSpec>`

---
### 2- Syntaxe des éléments XML à signaler dans sa documentation

**att** (attribut) contient le nom d’un attribut apparaissant dans le courant du texte.
**gi** (identifiant générique) contient le nom d’un élément.
**tag** (balise) le contenu d’une balise ouvrante ou fermante, avec éventuellement des spécifications d’attributs, mais à l’exclusion des caractères marquant l’ouverture et la fermeture de la balise.
**val** (valeur) contient une seule valeur d’attribut.

---
Exemple :

Le corpus présente trois cas de figure. Dans le premier cas, la ponctuation originale est supprimée dans l’édition normalisée. L’ajout de l’attribut `<att>`type`</att>` de valeur `<val>`orig`</val>` sur l’élément `<gi>`pc`</gi>` signale que le signe est issu de la ponctuation du manuscrit et qu’il ne doit pas apparaître dans la version normalisée.

---

## II- Personnaliser son ODD, niveau 2

---

### 1-Définir les modalités d’apparition d’un élément

La règle définissant une séquence apparaît directement en dessus de la balise ouvrante de l’**elementSpec** dans un élément **content**.

La séquence est contenue dans un élément **sequence** avec un attribut **preserveOrder** qui permet de spécifier si l’ordre de déclaration des éléments de la séquence est signifiant.

Chaque élément est appelé à l’aide d’un **elementRef** et d’un attribut **key** qui permet de donner le nom de l’élément. On peut également définir les modalités d’apparition des éléments de la séquence à l’aide des attributs **minOccurs** et **maxOccurs**.

---
#### Exemple

`<elementSpec ident="div1" mode="change">`
   `<content>`
      `<sequence preserveOrder="true">`
         `<elementRef key="head" minOccurs="1" maxOccurs="1"/>`
		 `<elementRef key="p" minOccurs="1" maxOccurs="unbounded"/>`
          `<elementRef key="div2" minOccurs="0" maxOccurs="unbounded"/>`
        `</sequence>`
   `</content>`
`</elementSpec>`

NB : Pour autoriser du texte comme contenu, on peut ajouter dans la séquence : `<textNode/>`

---
Il est également possible de raffiner ses séquences avec l’élément `<alternate>`
*Exemple : définition du contenu de `<choice>` :*
 `<alternate>`
  `<sequence>`
   `<elementRef key="sic"/>`
   `<elementRef key="corr"/>`
  `</sequence>`
  `<sequence>`
   `<elementRef key="orig"/>`
   `<elementRef key="reg"/>`
  `</sequence>`
  `<sequence>`
   `<elementRef key="abbr"/>`
   `<elementRef key="expan"/>`
  `</sequence>`
 `</alternate>`
 
 ---
 
 ### 2-contraindre des valeurs d’attributs, des enchaînements en fonction du contexte (schematron)
 
- La contrainte est introduite par un élément `<constraintSpec>`. Le langage utilisé est déclaré dans l’attribut **scheme="schematron"**, la règle est nommée à l’aide de l’attribut *ident*.
- La règle est contenue dans une balise `<contraint>`. 

NB : Attention à bien déclarer le nom de domaine *schematron* dans le préambule : **xmlns:s="http://purl.oclc.org/dsdl/schematron"**

---

#### Exemple

`<constraintSpec ident="reforkeyorname" scheme="schematron">`
 `<constraint>`
  `<s:assert test="@ref or @key or @name">`One of the
     attributes 'name', 'ref' or 'key' must be supplied`</s:assert>`
 `</constraint>`
`</constraintSpec>`

**s:assert** permet la vérification de l’existence de la contrainte rédigée en Xpath.

---
Ajouter un contexte 

`<constraintSpec ident="subclauses"
 scheme="schematron">`
 `<constraint>`
  `<s:rule context="tei:div">`
   `<s:assert test="count( tei:div )!= 1">`
   if it contains any subdivisions,
   a division must contain at least two of them`</s:report>`
  `</s:rule>`
`</constraint>`
`/constraintSpec>`

---
Contraindre l’activation d’un élément ou d’un attribut en fonction d’un contexte donné

`<constraintSpec ident="fromTo" scheme="schematron">`
   `<constraint>`
     `<s :rule context="tei:app[@type='structure']">`
      `<s :assert test="@from and @to">`
      The beginning and the endpoint of the lemma have to be identified.`</s:assert>`
                        `</s :rule>`
                    `</constraint>`
                `</constraintSpec>`

---
Contraindre le type de contenu d’une valeur d’attribut :

`<constraintSpec ident="fromType" scheme="isoschematron">`
      `<constraint>`
         `<s:rule context="tei:app[@from]">`
           `<s:assert test="matches(@from, '^#w\d+$')">`
		@from='#w+nb'`</s:assert>`
           `</s :rule>`
                   ` </constraint>`
                `</constraintSpec>`

---
## Exercice

Reprendre le fichier XML de Lucain,

**1-Créer la documentation de votre projet**

- Insérer dans votre documentation au moins un exemple ;
- Modifier la documentation d’un élément en réécrivant sa description pour la faire correspondre au projet.

**2-Ajouter des règles à votre XML**
- rendre obligatoire la présence d’un seul `<lem>` ;
- rendre obligatoire la présence d’une ou plusieurs leçons ;
- Faire en sorte de @n de `<l>` ne puisse accepter que des valeurs numériques ;
- Générer votre schéma et l’associer à votre fichier XML.

**3-Générer vos guidelines en HTML**