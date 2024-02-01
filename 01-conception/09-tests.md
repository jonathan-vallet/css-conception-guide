# 2.9. Tests automatisés

On parle souvent de tests unitaires pour des fonctionnalités côté serveur, et pendant longtemps le front n’avait pas trop d’outils de contrôle et de mesure de la qualité et non régression.

Depuis quelques années on trouve des outils de plus en plus simples à mettre en place. On va faire un petit tour de ce qu’il est largement conseillé de mettre en place sur chacun de vos projets dès sa conception.

## 2.9.1. Tests fonctionnels

Un test fonctionnel permet de tester une fonctionnalité (ne me remerciez pas pour cette information). Il ne sera pas là pour valider le rendu de votre site, mais plutôt un parcours utilisateur, une suite d’actions.

Ils permettent principalement de tester la saisie de formulaires, le clic sur certains éléments, des mouvements de souris. Il y a souvent un lien avec le JS côté front au niveau des interactions également.

Ces outils lancent un navigateur _headless _(sans interface graphique) dans lequel ils vont exécuter leur code.

Concrètement on peut par exemple tester:

- La validation d’un formulaire de login, avec les erreurs éventuelles et la bonne redirection vers la page souhaitée;
- Le passage du header en sticky au scroll, en vérifiant le changement de propriétés css et/ou l’ajout d’une classe;
- un effet de survol spécifique sur un élément...

Les tests fonctionnels sont à faire tout au long du projet dès le développement de la première fonctionnalité.

Pour réaliser des tests fonctionnels il y a des outils comme CasperJS, ou plus récemment Cypress, qui permet un export de mini vidéos sur les jeux de tests et est simple à prendre en main.

##

## 2.9.2. Tests de non régression visuelle

Ces outils de test sont là pour valider que d’une étape à une autre lors de l’intégration de votre site, il n’y ait pas de régression visuelle sur un bloc déjà finalisé.

Tout comme les tests fonctionnels, ils lancent un navigateur _headless_, puis font une capture d’écran d’une page ou de certains éléments de votre page. Il est d’ailleurs préférable de faire la capture par composant ou par bloc que sur l’ensemble de la page afin de mieux valider les différences potentielles d’une version à une autre.

Si d’une version à une autre un des écrans change, vous aurez un comparatif des 2 versions, il faudra alors soit valider la nouvelle version si le nouveau rendu est normal, soit faire les corrections pour ne plus avoir l’impact sur l’élément.

Ces outils deviennent terriblement efficace après avoir intégré plus d’une page, afin de s’assurer que des modifications sur une page n’ont pas affecté les autres, sans forcément avoir à retester manuellement l’ensemble du site.

J’aime beaucoup BackstopJS personnellement, mais il existe tout un tas d’outils différents comme Wraith, WebdriverCSS… chacun ayant ses points forts et ses faiblesses. Tout dépendra de vos besoins pour ce genre d’outils, entre un site statique ou un site dynamique, la plateforme de test que vous préférez, le langage utilisé pour la configuration, l’interface et les formats de rendu possibles…

##

## 2.9.3. Tests de performance

Un des outil les plus connu pour tester les performances d’un site est le _Google PageSpeed Insights_ ([https://developers.google.com/speed/pagespeed/insights](https://developers.google.com/speed/pagespeed/insights)).

Avoir un bon score ne garantit en rien la qualité de votre code, mais donne quelques axes de bonnes pratiques. Certains axes de performance ne sont pas liés directement au front (comme la configuration du .htaccess pour la mise en cache des médias), mais ça reste lié à notre coeur de métier.

Plus généralement, il faut limiter au maximum le nombre de requêtes, chacune demandant un temps de réponse du serveur. Il est souvent plus rapide de télécharger une seule ressource de 1Mo que 10 ressources de 50ko.

### 2.10.3.1. Optimisation des images

A chaque fois qu’une image est utilisée sur le site que vous développez, essayez d’avoir le meilleur dimensionnement possible entre la taille de l’écran et le poids de l’image. Si une image fait toute la largeur de l’écran, il faudra prévoir différentes tailles adaptées au tablettes et mobile avec d’autres dimension et l’utilisation de &lt;picture> et srcset. Il est inutile d’avoir une image de 1980px de large sur un téléphone.

Regroupez un maximum d’assets sur des sprites. Dans l’idéal utilisez des sprites SVG ([https://css-tricks.com/svg-sprites-use-better-icon-fonts/](https://css-tricks.com/svg-sprites-use-better-icon-fonts/)), qui ont un bon rendu, prennent peu de place et sont accessibles. Il faut les privilégier aux fonticon qui ont été longtemps utilisées, mais présentent quelques inconvénients, notamment pour l’accessibilité.

Pour toutes les images statiques de votre site, utilisez des outils – en ligne ou via des tasks runner comme Gulp ou Webpack – pour réduire le poids de vos images. Si votre site contient du contenu contribué et des images uploadées par les utilisateurs, il faut appliquer une solution côté serveur pour redimensionner et optimiser les images lors de l’upload.

### 2.9.3.2. Optimisation du nombre de ressources

Pour le CSS et le Javascript, il est conseillé d’avoir un fichier pour les éléments visibles au dessus de la ligne de flottaison, puis un autre fichier pour le reste de la page.

On peut aussi avoir un fichier avec les éléments communs à toutes les pages, facile à garder en cache sur tout le site, et un fichier pour le contenu spécifique à chaque page, pour éviter d’inclure du code inutile partout.

Les outils d’analytics sont d’énormes consommateurs de ressource. Souvent les gros sites en utilisent plusieurs en même temps, qui vont regarder des choses similaires, et ne seront pas forcément des indicateurs suivis. N’hésitez pas à conseillez ou sensibiliser vos clients sur ce sujet, pour avoir du tracking pertinent sans surcharger la bande passante. Si les utilisateurs perdent trop de temps à charger les pages, ils ne resteront pas sur votre site.

> Pour illustrer l'impact des outils d'analytics, voici l'état de chargement d'un site:
>
> Et le même site, dans les mêmes conditions sans éléments en cache, juste en désactivant les éléments d'analytics:
>
> On voit clairement la différence entre terme d'impact sur le chargement de la page (déjà assez peu optimisée)

### 2.9.3.3. Optimisation du poids des fichiers

Je l’ai déjà indiqué sur les images, mais on peut également réduire le poids d’autres fichiers. Les templates HTML, le CSS et le JS peuvent être minifiés une fois en production, et livrés sans les sourcemaps, pratiques pour le développement, mais qui prennent une place inutile une fois en ligne.

> J'ai participé plusieurs fois au concours [JS13K games](https://js13kgames.com/), qui consiste à créer un jeu sur un thème donné chaque année, avec comme contrainte une taille limitée à 13ko une fois zippé. (Il existe d'autres concours du genre avec d'autres contraintes de poids, parfois de 1ko, mais j'aime bien celui là).
> On est alors dans l'extrême au niveau de l'optimisation du poids des ressources. On limite notamment au maximum l'utilisation d'images en .jpg ou .png, qui, même optimisées, prennent une certaine place.
> On trouve souvent des alternatives en SVG ou en CSS pour pour limiter le chargement d'images. Il existe par exemple [A single div](https://a.singlediv.com/) avec plusieurs illustrations ou animations, tout étant fait en CSS dans un seul div, sans aucun autre élément HTML.
> Je vous invite fortement à regarder le code de ce genre de projets, qui sont de parfaits exemples de manières d'optimiser son code et ça fait réfléchir différemment.
