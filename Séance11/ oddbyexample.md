# Tutoriel Oddbyexample

- Mise à jour des add-on dans Oxygen :
	- Options/Préférences/Association de type de document;
		- Tout désactiver;
	- Add-ons;
		- Ajouter http://www.tei-c.org/release/oxygen/updateSite.oxygen;
		- Appliquer et accepter;
	- Aide/Gérer les Add-ons/Installer;
		- Tout activer et tout appliquer.
	- Options/Préférences/Association de type de document
		- Tout activer, appliquer, accepter
---

- Mise en place du scénario
	- Configurer un scénario de transformation (CTRL+MAJ+C ou menu Document/Transformation/Configurer...);
	- Créer un nouveau scénario : XML transformation with XSLT;
	- Renseigner le chemin de l'XSL;
		- `{framework}/tei/xml/tei/stylesheet/tools/oddbyexample.xsl`;
	- Sélectionner processeur Saxon 9.xX;
		- Options avancées, template (-it) : main;
		- Paramètres : corpus ${cfdu} (i.e. répertoire courant);
	- Configurer la sortie (onglet Sortie) : définir un nom et un emplacement pour la future ODD.