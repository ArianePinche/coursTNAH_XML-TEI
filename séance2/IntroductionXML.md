# Séance 2 : Introduction à XML

Observer un document XML : *L’année 1437 dans la pratique de Pierre Christofle, notaire du Châtelet d’Orléans*, <http://elec.enc.sorbonne.fr/christofle/index.html>

-----

## Introduction

### Définition

XML est un format de données pur, très simple et documenté, conçu pour la *description* des documents textuels. XML ne possède pas de jeu de balises prédéfini.

---

### Un standard international

Depuis 1998, XML est un langage libre et documenté. XML est également un **langage standard** respectant les recommandations du **W3C** (World Wide Web Consortium), il facilite :

- la lisibilité par les machines ou par l’œil humain ;
- l’échange de données ;
- la migration vers d’autres plates-formes, d’autres logiciels, d’autres formats.

----

### Structure générale du XML

Les données sont incluses dans le document XML sous forme de chaînes de caractères délimitées par un balisage les décrivant. L’unité de base qui comprend données et balisage est appelée élément.

*Exemple* : `<nomElement>chaineCaracteres</nomElement>`

----

Les éléments XML suivent un principe d’arborescence par imbrication.

*Exemple* : `<elementParent><elementEnfant>chaineCaracteres</elementEnfant></elementParent>`

Ainsi les éléments *enfants* héritent des propriétés des éléments *parents*

----

### Un peu d'Histoire...

- SGML (1970), Standard Generalized Markup Language;
	- HTML, HyperText Markup Language: affiche des données notamment sur le Web ;
	- XML, eXtensible Markup Language: contient et structure des données textuelles.
---

## Les éléments XML

### Éléments et attributs

#### Les éléments
`<element>texte</element>` ou `<elementVide/>`

Les éléments doivent tous strictement respecter le principe d'imbrication. 

#### Les attributs
`<MiseEnValeur rendu=" rouge italique" position=" centrePage">texte</MiseEnValeur>`

----

**Quelques règles importantes :**
	
	- à chaque balise de début doit correspondre une fin de balise ;
	- les éléments peuvent être imbriqués, mais ils ne doivent pas se recouvrir ;
	- il ne doit y avoir qu’un seul élément racine ;
	- un élément ne doit pas avoir deux attributs avec le même nom.


Un encodage qui respecte ces grands principes du XML est dit __bien formé__.

---

### Les commentaires
`<!-- texteCommentaire -->`

### Les entités
`& entité;`

Les entités sont des appels pour insérer dans le XML des caractères interdits ou bien des séquences de code définies au préalable dans une DTD.

Astuce : convertisseur de caractères (pour obtenir le code hexadécimal), <http://hapax.qc.ca/conversion.fr.html> 

----

### Instruction de traitement et déclaration XML

`<?xml version="1.0" encoding="UTF-8"?>`

Les instructions de traitement sont un autre moyen de fournir des informations aux applications auxquelles est destiné le document. 
Une instruction de traitement commence par « < ? » et se termine par « ?> ».

Ces dernières sont des balises et pas des éléments. Elles doivent donc être en dehors d'une balise.

Les instructions de traitement les plus courantes sont l'appel d'une feuille de style, d'un schéma et l'appel d'une version de XML. Ces appels doivent être placés avant l'élément racine. 

-----

### Les sections CDATA

`<![CDATA [TexteBrut]]>`

Tout ce qui est compris dans ces balises est traité comme des données textuelles brutes

---

Pour aller plus loin : https://www.youtube.com/watch?v=R0ncI_rr1z4&list=PL77mHK9JuenN9NXeXQbVcUORz7HZk-9Pv&index=2 

