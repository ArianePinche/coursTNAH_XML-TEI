# Séance 10 : ODD (1) – Initiation 

---
## Conformance

Comment obtenir un encodage TEI-conformant ? 

1. Le XML doit être bien formé;
2. L’encodage proposé doit pouvoir être validé avec un schéma TEI all;
3. L’encodage doit être conforme au modèle abstrait de la TEI;
4. L’encodage doit faire bon usage de l'espace de nom de la TEI (et des autres espaces de nom si besoin);
5. L’encodage doit être documenté.

--- 

## Les différents types de schémas

- DTD
	- permet la création d’éléments, de sous-éléments, d’attributs, d’entités
	- pas de documentation du schéma directement dans le fichier
	- pas de typage précis du contenu des éléments (chaîne de caractères de texte, nombre entier, etc.)
	- pas de gestion des espaces de nom 
	- pas en XML
```xml
<!ELEMENT texte (chapitre+)>
<!ELEMENT chapitre (titre?, paragraphe+)>
<!ELEMENT titre (#PCDATA)>
<!ELEMENT paragraphe (#PCDATA)>
<!ATTLIST chapitre n CDATA #REQUIRED >
```
---
- XML schéma
	- permet de typer les données
	- permet de mettre en place une séquence d’éléments
	- XML Schema est lui-même un document XML
```XML
<xsd:element name="paragraphe" type="xsd:string" />
<xsd:element name="titre" type="xsd:string" />
<xsd:element name="n" type="xsd:int" />
```
---
- Relax NG
	- permet de typer les données
	- permet de mettre en place une séquence d’éléments
	- peut créer des contraintes d'enchaînement très précises grâce à l'intégration du langage **schematron**
	- supporte XML namespaces
	- écrit en syntaxe XML
	- compatible avec XML schéma
	- plus simple que XML schéma
	- peut s'appuyer sur les modules et les macros de la TEI
```XML
<define name="model.divPart">
      <choice>
         <ref name="model.lLike"/>
         <ref name="model.pLike"/>
         <ref name="lg"/>
      </choice>
   </define>
```

---
- ODD "One Document Does it all"
	-  un fichier pour générer un schéma relaxNG et une documentation du schéma 
	-  possibilité de définir précisément le nombre d’occurrences d’un élément, ainsi que des séquences ;
	-  possibilité de typer les données d’un élément
	-  supporte des espaces de noms
	-  peut d’appuyer sur le schéma tei_All et sa structure en modules et macros.
	-  intégralement en syntaxe XML

Voir : 
TEIguidelines : <http://www.tei-c.org/release/doc/tei-p5-doc/en/html/USE.html>
ODD : <http://www.tei-c.org/guidelines/customization/getting-started-with-p5-odds/>

---
## Créer son ODD

- À l'aide de [Roma](https://roma.tei-c.org);
- À partir d'un ou de plusieurs fichiers XML.

---

## Structurer son ODD

- À l'aide des [modules TEI](http://www.tei-c.org/release/doc/tei-p5-doc/en/html/ST.html#STMA); 

	- Manipulation [Roma](http://roma.tei-c.org)
		- Créer une ODD pour décrire une pièce de théâtre;
		- Appliquer le schéma au fichier XML de misanthropeTEI.xml.
---
- À l'aide des [classes TEI](http://www.tei-c.org/release/doc/tei-p5-doc/en/html/REF-CLASSES-ATTS.html);  
	
	- Manipulation [Roma](http://roma.tei-c.org)
		- Créer une ODD pour une pièce de théâtre;
		- Modifier la classe att.global en supprimant @n;
		- Ouvrir l'ODD, chercher @n.
		- Appliquer le schéma au fichier XML de misanthropeTEI.xml.
---
- Au niveau d'un élément  
	
	- Manipulation [Roma](http://roma.tei-c.org)
		- Créer une ODD pour une pièce de théâtre;
		- Supprimer l'élément speaker
		- Ouvrir l'ODD, chercher speaker.
		- Appliquer le schéma au fichier XML de misanthropeTEI.xml.
---
- Au niveau d'un attribut
	
    - Manipulation [Roma](http://roma.tei-c.org)
		- Créer une ODD pour une pièce de théâtre;
		- Contraindre les valeurs de l'attribut type sur les div dans une liste fermée
		- Rendre l'attribut obligatoire
		- Ouvrir l'ODD, chercher @type.
		- Appliquer le schéma au fichier XML de misanthropeTEI.xml. 
---
Exercice

À l'aide de Roma, créer une ODD pour la séquence de sainte Eulalie.

--- 
# Créer une ODD à partir de ODDbyExample

---

# Tutoriel Oddbyexample

- Mise à jour des add-on dans Oxygen :
	- Options/Préférences/Association de type de document
		- Tout désactiver
		- Bien vérifier que la ligne "options globales" est cochée
- Add-ons
		- aide/installer les nouveaux add-ons 
		- Ajouter https://www.tei-c.org/release/oxygen/updateSite.oxygen
		- Appliquer et accepter
	- Aide/Gérer les Add-ons/Installer
		- Tout activer et tout appliquer
	- Options/Préférences/Association de type de document
		- Tout activer, appliquer, accepter
---
# Appliquer ODDbyExample
- Mise en place du scénario
	- Configurer un scénario de transformation (CTRL+MAJ+C ou menu Document/Transformation/Configurer...)
	- Créer un nouveau scénario : XML transformation with XSLT;
	- Renseigner le chemin de l'XSL
		- `${frameworks}/tei/xml/tei/stylesheet/tools/oddbyexample.xsl`;
	- Sélectionner processeur Saxon 9.xX
		- Options avancées, template (-it) : main;
		- Paramètres : corpus ${cfdu} (i.e. répertoire courant)
	- Configurer la sortie (onglet Sortie) : définir un nom et un emplacement pour la future ODD.
	- Appliquer l'ODD sur le fichier Mon_reve_familierTEI.xml

---

