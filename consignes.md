# Comment réutiliser ce jeu

## Licence

Le jeu est placé sous licence libre (CC-by 4:0)

# quels sont les éléments constituant le jeu ?

## Le document plagiator.html

### Comment éditer ce document

Le document principal est [plagiator.html](plagiator.html)
Ce document est éditable avec le logiciel Twine en ligne ou avec l'éditeur Twine téléchargé sur votre machine. Nous vous recommandons la deuxième solution. 
Pour télécharger Twine, aller sur [le site de cet éditeur](https://twinery.org/).

Pour charger l'histoire dans Twine, aller sur Bibliothèque > import > importer le fichier plagiator.html là où vous l'avez téléchargé. 
Attention Twine utilise par défaut le dialecte Harlowe. Plagiator a été conçu avec le dialecte SugarCube dont [la documentation est en ligne](https://www.motoslave.net/sugarcube/2/docs/)
Pour changer le dialecte dans l'éditeur Twine. Ouvrir Plagiator dans Twine, aller sur Histoire > Détails > dans le menu déroulant, sélectionner "wSugarCube".

### Quels sont les codes informatiques utilisés dans cette histoire?

L'essentiel du document est écrit dans la syntaxe de SugarCube. 
Les passages peuvent contenir du Javascript, du html et du CSS.
Pour mettre en forme certains passages, nous avons utilisé le fichier CSS (\#feuille de style) rattaché à l'histoire. Les différentes classes CSS sont commentées pour être plus facilement modifiées. 

Afin de rendre les dialogues plus interactifs, nous avons eu recours à du Javascript pour permettre à l'utilisateur d'afficher au sein d'un même passage les parties du dialogue, réplique après réplique (fonction keydown en Javascript). Nous avons constaté que l'espace dédié dans l'éditeur Twine pour recevoir le bout de code Javascript ne fonctionnait pas de manière idéale. 

Nous avons fait figurer ce script au début de la plupart des passages : 

```javascript
<script src="https://code.jquery.com/jquery-3.6.4.min.js">    
    <script>
(function () {
  var i = 3;

  $(document).keyup(function (e) {
    var currentDiv = document.getElementById(i.toString()); // Convert the number to string

    if (currentDiv !== null) {
      currentDiv.style.display = "block";
      scrollToDiv(i.toString());
      i++;
    }
  });

  function scrollToDiv(divId) {
    var targetElement = document.getElementById(divId);

    if (targetElement) {
      targetElement.scrollIntoView({
        behavior: 'smooth',
        block: 'start'
      });
    }
  }
}());
</script>

```
La variable *i* correspond aux "divs" (morceaux de textes, présents en html dans les passages et qui apparaissent lorsque le joueur ou la joueuse frappe n'importe quelle touche). 
Cette variable est incrémentale. Le jeu comporte environ 130 *divs* numérotées. 
Lorsque ces *divs* ne sont pas incrémentées d'un passage à l'autre, il arrive qu'au début d'un passage, des divs s'affichent alors que les précédentes n'ont pas encore été déclenchées par l'utilisateurice. Nous avons donc décidé en dépit de la contrainte que cela représente et faut d'alternative à notre disposition d'incrémenter ces "divs" sur l'ensemble du jeu (pas de possibilité de procéder par tranches ou de laisser des espaces vacants dans cette énumération) Nous sommes à la recherche de développeurs connaissant le Javascript qui nous permettraient d'améliorer ce code.

## Les documents adjacents

### Sons et images

Les répertoires *sons*, *gifs* et *images* contiennent les sons, gifs et images qui sont utilisés dans le jeu. 
Au début du jeu, il est demandé à l'utilisateurice si iel souhaite jouer la version sonore ou muette du jeu. 
Si le fichier *plagiator.html* est ouvert dans le navigateur séparémment de ces dossiers, ni les sons, ni les images ou les gifs ne pourront apparaître.
Les sons sont appelés depuis le passage fonctionnel *StoryInit* dans les différents passages où ils sont joués.
Les crédits de ces sons et images sont disponibles dans le passage "Crédits".

### activités h5p

Les activités h5p sont sans effet sur la conduite du récit. Les tentatives des joueur/joueuses ne sont pas conservées. Ces activités ne comptent pas dans le score. Elles sont uniquement dévolues à ajouter de l'interactivité dans les passages.

Sous le dossier *H5P* on trouve des fichiers h5p qui correspondent aux différentes activités h5p proposées dans cette aventure Twine. Pour éditer, ces fichiers, on peut utiliser le logiciel [Logiquiz](https://ladigitale.dev/logiquiz/#telecharger) de la Digitale
Le dossier *Lib* contient les fichiers nécessaires à l'affichage des activités h5p dans des pages web. Le code emabarqué issu de ces pages webs (une page par activité) est ensuite chargé sous la forme d'un *iframe* dans le passage pertinent de Twine. Voir exemple ci-dessous:

```html
<iframe width="700" height="987" src="https://damienbelveze.github.io/plagiator/memoire_camille.html" frameBorder="0" scrolling="no" styles="width:100%"></iframe>
```

Si vous transférez le contenu de répertoire vers votre propre répertoire github, il faudra changer le lien dans les iframes en utilisant l'éditeur Twine : 

```html
 https://nomutilisateur.github.io/plagiator/memoire_camille.html 
 ```

La méthode pour conserver dans un repo github et le code qui va avec sont fournis par [Tupananda](https://github.com/tunapanda/h5p-standalone) lire également les explications de [Camilo Mora](https://github.com/Camilo-Mora/H5P?tab=readme-ov-file)

Github permet de fournir les pages web dans leur forme voulue au moyen de son infrastructure Github Actions. A chaque mise à jour d'un fichier dans l'entrepôt, l'ensemble des fichiers sont compilés et déployés au moyen de Github Actions.

# Comment l'installer dans Moodle

Téléchargez l'archive du présent répertoire et dézippez. 
Dans l'espace-cours Moodle où vous souhaitez déposer le jeu, créez une activité "fichier"(file)
A l'intérieur créez trois dossiers : 
- images
- sons
- gifs
Faites glisser depuis votre explorateur le contenu des trois dossiers correspondants vers leur emplacement sur Moodle. 
A la racine du dépôt Moodle, glisser-déposez le fichier plagiator.html et indiquez-le comme fichier principal

# Comment le cloner depuis Github

Connectez-vous à votre compte sur Github
Dans cet entrepôt, cliquez sur "use this template" (bouton vert en haut à droite)
Faites les modifications qui conviennent (chemins absolus dans les *iframes*, voir plus haut)

