# Séance 11 : ODD (1) – Présentation des basiques 

---
## I-Conformance

Comment obtenir un encodage TEI-conformant ? 

1. Le XML doit être bien formé;
2. L’encodage proposé doit pouvoir être validé avec un schéma TEI all;
3. L’encodage doit être conforme au modèle abstrait de la TEI;
4. L’encodage doit faire bon usage de l'espace de nom de la TEI (et des autres espaces de nom si besoin);
5. L’encodage doit être documenté.

--- 

## Les différents types de schémas

- DTD;
- ODD "One Document Does it all";
	- Voir les [TEIguidelines](http://www.tei-c.org/release/doc/tei-p5-doc/en/html/USE.html);
	- Voir la [documentation sur les ODD](http://www.tei-c.org/guidelines/customization/getting-started-with-p5-odds/)
- Relax NG;
- Schematron;
- XML schéma.

---
## Créer son ODD

- À l'aide de [Roma](https://roma.tei-c.org);
- À partir d'un ou de plusieurs fichiers XML.

---

## Structurer son ODD

- À l'aide des [modules TEI](http://www.tei-c.org/release/doc/tei-p5-doc/en/html/ST.html#STMA); 
	- `<moduleRef key="tei"/>`
	- Manipulation [Roma](http://roma.tei-c.org)
		- Créer une ODD pour décrire un manuscrit;
		- Appliquer le schéma au fichier XML de EulalieSourceDesc.xml de la séance 9.
---

- À l'aide des [classes TEI](http://www.tei-c.org/release/doc/tei-p5-doc/en/html/REF-CLASSES-ATTS.html);  
	- `<classRef key="att.textCritical"/>`
	- Manipulation [Roma](http://roma.tei-c.org)
		- Créer une ODD pour décrire un manuscrit;
		- Modifier la classe att.global en supprimant @facs;
		- Ouvrir l'ODD, chercher @facs.
---

- À l'aide des éléments TEI
	- `<elementSpec ident="msDesc" mode="change">`
	- Manipulation [Roma](http://roma.tei-c.org)
		- Créer une ODD pour décrire un manuscrit;
		- supprimer tous les attributs de l'élément msDesc;
		- Ouvrir l'ODD, chercher `<msDesc>`.
---
## Personnalisation du schéma

Pour personnaliser son schéma, il existe 4 manipulations principales :
- Ajouter des éléments ; 
- Supprimer des éléments ;
- Changer des éléments ;
- Personnaliser les attributs et les valeurs d’attribut d’un élément.
---
### Suppression d'un élément

1- Suppression simple d'un élément avec @mode="delete"
	- `<elementSpec ident="head" mode="delete"/>`
2- Suppression d'un élément ou une classe dans un module avec  @exclude
	- `<moduleRef key="textcrit" except="rdgGrp"/>`
3- Non insertion dans un module ou une classe avec @include
	- `<moduleRef key="textcrit" include="app lem rdg"/>`
	
- Modifier l'ODD de sainte Eulalie en interdisant l'utilisation de l'élément `<lem>`

---

Tutoriel "oddbyexample"

---

### Modification d'un élément

Modification d'un élément avec @mode="change"

`<elementSpec ident="lg" mode="change">`
               `<attList>`
                  `<attDef ident="part" mode="delete"/>`
                  `<attDef ident="type" mode="change"><valList mode="add" type="closed">`
                        `<valItem ident="quatrain"/>`
                        `<valItem ident="sizain"/>`
                        `<valItem ident="sonnet"/>`
                        `<valItem ident="tercet"/>`
                     `</valList></attDef>`
               `</attList>`
`</elementSpec>`

- Modifier dans l'ODD du texte de Verlaine l'élément `<l>`en lui ajoutant un attribut "n" obligatoire.

----
### Addition d'un élément 

- Déclaration d'un élément dans le `<moduleRef>` avec @include
	- `<moduleRef key="textstructure" include="TEI text body front"/>`

---
- Création d'un nouvel élément qui n'appartient pas au domaine TEI :
	`<elementSpec ident="alexandrin" mode="add" ns="http://www.example.com/ns/nonTEI">`
               `<classes>`
                  `<memberOf key="model.lLike"/>`
                  `<memberOf key="att.global.attributes"/>`
                  `<memberOf key="macro.paraContent"/>`
               `</classes>`
               `<content>`
                  `<textNode/>`
               `</content>`
            `</elementSpec>`
- Déclarer dans l'ODD du texte de Verlaine un attribut "subtype" (non TEI) non obligatoire avec une liste de valeurs close : "rime A | rime B | rime C"