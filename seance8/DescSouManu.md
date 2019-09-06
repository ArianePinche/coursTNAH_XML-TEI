# Décrire les sources manuscrites

---

## EAD (Encoded Archival Description)

EAD est une DTD (un schéma d’utilisation) de XML.

* 2000, encodage en XML EAD du catalogue général des manuscrits des bibliothèques publiques de France.
* 2010, la DeMarch recommandation est publiée.
	* Attention : DeMArch est une règle de description indépendante du format informatique.
* 2012, deux tiers des manuscrits et documents d’archives conservés par les bibliothèques françaises sont décrits en EAD (« BnF archives et manuscrits », Calames, le sous-domaine « Manuscrits » du Catalogue collectif de France CCFr).	

---
### Quelques exemples 

* [Inventaire du fonds du Théâtre de Poche-Montparnasse (1942-2011)](https://ccfr.bnf.fr/portailccfr/jsp/index_view_direct_anonymous.jsp?record=eadcgm:EADC:BHPCT0200001)
	* [Voir le fichier XML](./InvThMontparnasse.xml)

* [Catalogue du fonds général, Ms 1 à Ms 721](https://ccfr.bnf.fr/portailccfr/jsp/public/index.jsp?action=public_direct_view&record=eadcgm:EADI:FRCGMBPF-751045102-01a.xml)
	* [Voir le fichier XML](./catMS.xml)

---
### Pour résumer

Extrait de Florent Palluault, « Informatiser des descriptions complexes : l’utilisation de l’EAD et de la TEI pour les manuscrits et les livres anciens en France », *IFLA 2012 (Helsinki)*, [en ligne : http://conference.ifla.org/past/2012/212-palluault-fr.pdf.

"La nécessité d’une arborescence est moindre pour ces documents que pour des ensembles d’archives, et la sémantique EAD n’est pas aussi développée que celle de la TEI-P5, utilisée pour les manuscrits médiévaux dans plusieurs pays d’Europe."

---
"Au-delà des manuscrits et archives, **l’EAD est pertinente pour tout ensemble de documents hiérarchisés, quelle que soit leur nature. Elle permet de visualiser aisément la structure de fonds ou de collections composites** comme celles du Département des Arts du Spectacle de la BnF, qui comprennent fréquemment scénarios manuscrits, programmes imprimés, costumes, objets de décor, etc."

---

## Naissance du msDesc

* 1999-2001 : projet européen MASTER (Manuscript Access through Standards for Electronic Records);
* 2001, la DTD Master, personnalisation de la TEI qui complète par l'ajout d'un élément msDesccription, et d'autres éléments spécialisés qui représentent un enrichissement des possibilités pour la description des manuscrits.
* 2007-2009 : lancement du projet ENRICH (European Networking Resources and Information concerning Cultural Heritage)

---
 
### Les éléments TEI de description des sources : `<msDesc>`

[**10.2 Manuscript Description Element**](http://www.tei-c.org/release/doc/tei-p5-doc/fr/html/MS.html#msov)

[Voir le fichier TEI](exSourceDesc.xml)


---

### Mise en pratique

- Reprendre le fichier de la séquence de sainte Eulalie
- Quels sont les éléments d'un teiHeader minimal ?
- Compléter les éléments du `<msDesc>` à l'aide des différents documents de la séance dernière.


