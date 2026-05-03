# galerie-virtuelle

# Guide : ARCGIS Storymaps et URL sur mesure

Ce guide explique comment utiliser ARCGIS Storymaps pour créer une carte interactive (similaire à la structure utilisée pour [chris-bacon.ca/galerie](http://chris-bacon.ca/galerie)) et comment configurer une URL personnalisée pour contourner les limitations de la plateforme.

## 1. ARCGIS Storymaps

ARCGIS Storymaps est essentiellement une interface web permettant de créer une "histoire" liée à des données géographiques. Ici, la plateforme est utilisée pour localiser des œuvres dans l'espace public, mais il est absolument possible d'utiliser d'autres sources, comme l'API de Google Maps, pour créer un site de toutes pièces ou utiliser un autre outil de cartographie (voir la section **Autres outils**).

### Comment commencer :

1. **Étape 1 :** Allez sur [storymaps.arcgis.com](https://storymaps.arcgis.com/).
2. **Étape 2 :** Créez-vous un compte (il y a une option gratuite).
   * À partir de là, vous aurez accès à un tableau de bord où se trouvent vos "histoires".
   * Pour un descriptif détaillé de chaque fonction de la plateforme, consultez la documentation officielle : [Partager le récit d’une expédition](https://learn.arcgis.com/fr/projects/share-the-story-of-an-expedition/).
3. **Étape 3 :** Publiez et le tour est joué !

*Note : ARCGIS Storymaps est un choix intéressant de par sa simplicité, mais rien n'empêche de faire quelque chose de plus complexe selon les besoins du projet.*

---

## 2. Donner un URL sur mesure à votre Storymaps

ARCGIS Storymaps ne permet pas nativement de créer une URL sur mesure. Par contre, il est possible de passer outre cette limitation à l'aide d'une `iframe`.

Pour ce faire, vous devez avoir votre propre nom de domaine (à se procurer chez un hébergeur) ainsi que l'URL fournie par ARCGIS.

### Création du fichier HTML

Avec ces informations, vous pouvez créer un document HTML à l'aide d'un éditeur de texte (tel que Notepad++). 

Pour nommer le fichier correctement, vous devez suivre la nomenclature de votre hébergeur web :
* Si votre page doit s'afficher à la racine de votre site web (ex: `monexpo.ca`), votre fichier doit se nommer `index.html`.
* Si votre page se trouve dans un sous-répertoire (ex: `monexpo.ca/monexpo`), alors votre fichier doit se nommer `monexpo.html`.

*Chaque hébergeur ayant ses propres directives, l'endroit exact où placer le fichier peut changer, mais les indications devraient être claires sur le site de votre hébergeur.*

### Le Code

Voici le code à insérer. Prenez soin de modifier la section prévue pour l'URL (située juste après `src=`) avec l'URL de votre Storymap. Entre les balises `<title>` et `</title>`, insérez le titre que vous voulez voir apparaître au haut de l'onglet du navigateur.

```html
<!DOCTYPE html>
<html>
<head>
<title>MON EXPO</title>
<style type="text/css">
   html, body, div, iframe { margin:0; padding:0; height:100%; }
   iframe { position:fixed; display:block; width:100%; border:none; }
</style>
</head>

<body>
<iframe src="VOTRE URL DE ARCGIS" width="100%" height="100%" frameborder="0" allowfullscreen allow="geolocation"></iframe>
</body>
</html>
````

Je n'ai pas utilisé la fonction "embed" générée par ARCGIS puisque ce code personnalisé est, à mon avis, plus complet. ARCGIS Storymaps supporte les commandes iframe. Si vous utilisez une autre plateforme de cartographie, il est possible que cette commande ne soit pas supportée et donc que le code ci-haut ne fonctionne pas.

## 3. D'autres outils
Si ARCGIS ne convient pas à vos besoins, voici quelques alternatives utiles pour la cartographie et l'interaction.

Cartographie

[KnightLab StoryMap](https://storymap.knightlab.com/)

[odiyssey.js](https://cartodb.github.io/odyssey.js/index.html)


Interaction et Communication

Discord : Idéal pour les communautés et facile à mettre en place.

Rocket.Chat : Plateforme open-source (vous devez avoir un moyen d'héberger le tout sur un serveur, que ce soit un serveur loué ou le vôtre).
