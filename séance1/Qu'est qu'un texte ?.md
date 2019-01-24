# Qu’est-ce qu’un texte ?

## Matérialité du texte
- 	Le texte brut (.txt) / *plain text* se compose de caractères pour lesquels il existe plusieurs répertoires :
		- ASCII American Standard Code for Information Interchange)
		- ISO 8859-1 (Latin 1)
		- UTF-8 (Universal Character Set Transformation Format - 8 bits)

**Pour aller plus loin** : <https://www.youtube.com/watch?v=MijmeoH9LT4>

- Le texte « stylé » / *fancy text*: balises et mise en valeur typographique :
	- balisage LaTeX
	- balisage HTML
----


## La notion « texte »

- Quels peuvent être les différents aspects d’un texte ?

- Comment décrire les différents aspects d’un texte ?
	- Le balisage sémantique permet d’expliciter certains aspects du texte. **XML** (eXtended Markup langage) est très adapté pour ce type d’usage. 
---

***Exemple de balisage typographique et sémantique***

|Langage	 | Balise typographique | Balise sémantique
| :------- | :------------------: |----------------|
| LaTeX |	 \emph{ad hoc} | \selectlanguage{latin}{ad hoc} |
| HTML5 | `<i>ad hoc</i>` | `<i lang="la">ad hoc</i>` |
| XML-TEI	| `<hi rend="i">ad hoc</hi>` | `<foreign xml:lang="la">ad hoc</foreign>` |

*Pour réviser* : <https://github.com/architexte/cours-TEI/blob/master/1-text-balises.md>

----

- **Quel est l’intérêt d’un balisage sémantique ?**

	- Exemple d’édition scientifique : *The Shelley-Godwin Archive*, <http://shelleygodwinarchive.org/sc/oxford/frankenstein/volume/i/#/p1/mode/rdg>
	- Pour aller plus loin : *DH in Practice - Digital Scholarly Editions* par E. Pierazzo,
<https://www.youtube.com/watch?v=0DB51fblNWI>