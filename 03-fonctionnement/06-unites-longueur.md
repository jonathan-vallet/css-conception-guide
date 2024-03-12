# 3.6. Les unités de longueur

Quand on fait la mise en page d'un site, on peut utiliser différentes unités pour exprimer les dimensions pour un même rendu. Dans ce chapitre, on va détailler les unités qu'on retrouve, ce qu'elles signifient et quand les utiliser.

Généralement, les propriétés CSS acceptent toutes les unités, qui sont ensuite calculées et converties en pixel (px), l'unité la plus commune et conçue spécifiquement pour le CSS. Quand on inspecte la CSS calculée dans un navigateur, toutes les valeurs sont converties en pixel pour l'affichage sur nos écrans.

## 3.6.1. Les unités absolues

Les unités absolues représentent une mesure physique et sont utilisées principalement pour l'impression, à savoir :

- `in` pour inch (pouce en anglais) qui vaut 2.54 cm
- `pt` pour point qui vaut 1/72ème de pouce
- `pc` pour pica qui vaut 12 points
- `mm` pour millimètre
- `cm` pour centimètre, qui vaut 10 mm
- `px` pour pixel, l'unité de référence pour les écrans, qui vaut 1/96ème de pouce

On peut en déduire la relation suivante :

**1in = 72pt = 6pc = 25.4mm = 2.54cm = 96px**

Vous pouvez vérifier ces valeurs avec une règle lors de l'impression. Sur un écran, un `in` ne représente pas un pouce physique mais 96px. Cela signifie que quelle que soit la densité de pixels de l'écran ([vue dans le chapitre sur le viewport](03-viewport.md)), elle est supposée correspondre à 96dpi. Si le terminal a une densité de pixel supérieure, `1in` fera moins de 1 pouce physique. C'est pour cela qu'on évite d'utiliser les unités absolues autre que le pixel pour la mise en page sur un écran.

> Il faut toujours essayer de fournir une feuille de style dédiée à l'impression quand on développe un site. On peut simplement cacher le header et le footer, cacher la plupart des images et des SVG et afficher le texte brut avec une taille de police convenable.
>
> C'est notamment une des recommandations dans le cadre de l'éco-conception, puisque l'utilisateur consommera moins d'encre s'il souhaite imprimer un article par exemple.

## 3.6.2. Les unités relatives

Ces unités permettent d'obtenir des longueurs basées sur la taille de l'élément courant, d'un élément parent, ou relative à la taille du viewport.

### 3.6.2.1. em et rem

`EM` est une unité de mesure de longueur des espaces — le cadratin en français — tirant son nom de la lettre “M” majuscule. À la naissance de l'imprimerie à caractère mobile au XVe siècle, 1em vaut 16pt.

Les lettres sont des objets graphiques entretenant un rapport étroit avec le dessin. La proportion des lettres a été établie grâce au nombre d'or et à l'Homme de Vitruve de Léonard de Vinci.

Le “M” majuscule fait à l'origine 1em de haut et de large. D'autres caractères comme l'espace ( ), le tiret cadratin (—) font également 1em de large, et tous les caractères font 1em de hauteur.

> En CSS, seule la hauteur de la lettre est utilisée, et par défaut 1em vaut 16 px.

L'em est une unité relative qui va permettre d'exprimer les tailles de police des différents textes en fonction de la taille du contenu normal du corps du document.

L'em s'applique proportionnellement à la taille de son élément parent. Prenons un élément avec une taille définie à 1em. Un élément avec une taille de 2em à l'intérieur sera 2 fois plus gros. Un élément à l'intérieur de celui-ci avec une taille de 1.5em apparaîtra 150% plus gros, soit 3 fois plus que la taille initiale.

Pour remédier à ce problème, CSS a introduit le rem en 2013, pour “root em”. Le rem est constant dans un document car il se fonde sur la taille de l'élément racine du document.

> J'ai indiqué précédemment que 1em = 16px par défaut. On voit souvent le font-size de l'élément racine "html" défini à 62.5%, ce qui permet d'avoir un ratio 1rem = 10px, plus facile pour les conversions.

Qu'ils soient définis en px ou en rem, la taille du texte augmente proportionnellement sur tous les navigateurs récents. Firefox, qui permet de faire un “zoom texte uniquement”, fonctionne aussi pour les polices définies en pixel.

Mais il faut bien utiliser des em ou rem pour les tailles de police et non des px. En plus d'avoir une distinction plus nette entre les unités de taille de texte et les unités de longueur, on prend surtout en compte les paramètres utilisateurs pour faciliter l'accessibilité du site aux malvoyants. En effet, dans les préférences des navigateurs, il est possible de modifier la taille par défaut des textes afin de les réduire ou de les grossir. La valeur par défaut des tailles de texte est ainsi modifiée, ce qui impacte la valeur des em et rem, mais ces préférences n'ont pas d'effet si on a écrit les règles de typographie en px.

> Pour insister un peu plus sur l'accessibilité, c'est bien d'utiliser les rem pour permettre de grossir les textes, mais il faut faire en sorte que nos modèles de boîte s'adaptent correctement à ces changements.
>
> Quand on grossit le texte à 200%, il doit être parfaitement lisible pour répondre au [critère 10.4 du RGAA](https://accessibilite.numerique.gouv.fr/methode/criteres-et-tests/#10.4). Ce n'est pas très grave si certains éléments de la page sont déformés, mais il faut éviter d'avoir des boîtes avec des dimensions fixes, afin que le texte puisse déborder proprement et pas devenir illisible en superposition avec un autre texte ou un autre fond mal contrasté.

### 3.6.2.2. Les pourcentages

Les pourcentages permettent d'avoir une valeur proportionnelle à l'élément parent de celui pour lequel on l'utilise.

Pour la font-size, ça sera équivalent à une valeur en em.

Le line-height est par défaut relatif à la font-size quand on ne précise pas d'unité. En attribuant une valeur en pourcentage, elle reste relative à la font-size, et non à la hauteur de la boîte.

Quand on fait un translate en pourcentage, la valeur se base sur la taille de l'élément et non de son parent. C'est ce qui permet d'avoir une boîte centrée dans son conteneur quand on applique un `left: 50%` et un `transform: translate(-50%)`.

> Quand on applique une valeur en pourcentage au padding, border ou margin d'un élément, elle sera calculée par rapport à la largeur du parent, et non par rapport à la hauteur de l'élément pour les attributs top et bottom.
>
> En effet, dans le modèle de boîte, la largeur des enfants dépend de la largeur du parent, tandis que la hauteur du parent est calculée par celle des enfants. On ne peut alors pas avoir une valeur enfant qui dépende de la hauteur du parent sans avoir une boucle infinie dans le calcul de la hauteur. On peut utiliser cette spécificité pour avoir des éléments dont on conserve le ratio au redimensionnement (cf chapitre plus loin…).

## 3.6.3. Les unités relatives au viewport

Les unités `vw` et `vh` signifient respectivement viewport width et viewport height. Elles fonctionnent comme des pourcentages, mais par rapport au viewport et non par rapport à l'élément parent.

1vw = 1% du viewport

> Le `vw` se base sur la `outerwidth` et non sur la `innerwidth`. Il faut faire attention sur les navigateurs avec une scrollbar visible, puisque 100vw causeront un dépassement horizontal.
>
> Sur mobile, notamment les iPhone, la barre de navigation en bas visible avant de scroller est comprise dans les 100vh, ce qui peut masquer une partie de votre contenu. Cette spécificité a été voulue afin d'éviter de redimensionner le viewport et causer de nombreux repaint et reflow lorsque la barre va disparaître quand l'utilisateur va scroller dans la page.
>
> Source : https://medium.com/@susiekim9/how-to-compensate-for-the-ios-viewport-unit-bug-46e78d54af0d

`vmin` et `vmax` valent respectivement la plus petite et la plus grande valeur entre `vw` et `vh`.

Précédemment dans [le chapitre sur le flow](05-flow.md), on a vu les nouvelles propriétés qui se basent sur le _writing-mode_, ce que font les unités `vi` et `vb`. `1vi` vaut 1% du viewport dans le sens du flux des blocs, tandis que `1vb` vaut 1% du viewport dans le sens du flux du texte.

### 3.6.3.1. calc() et les maths

`calc()` n'est pas une unité de mesure, mais une fonction en CSS qui permet de mélanger différentes unités, offrant une grande souplesse pour définir les dimensions des éléments. Par exemple, pour créer une marge autour d'un élément qui occupe toujours le reste de l'espace disponible, vous pourriez utiliser `width: calc(100% - 20px);` pour soustraire `20px` de la largeur totale disponible. `calc()` est particulièrement puissant lorsqu'il est combiné avec des unités relatives, comme `vh` et `vw`, pour créer des designs fluides qui s'adaptent à la fois aux dimensions de l'écran et à des valeurs fixes, garantissant ainsi une mise en page cohérente et fonctionnelle.

Pendant très longtemps j'ai utilié [une mixin proposée par CSS-Tricks](https://css-tricks.com/snippets/css/fluid-typography/) utilisant `calc()` pour faire une augmentation fluide de la taille de la police en fonction de la largeur de l'écran. C'est une technique qui a été popularisée par Ethan Marcotte dans son article sur le _responsive web design_.

Maintenant on peut [utiliser des dimensions fluides bien plus simplement](https://css-tricks.com/simplified-fluid-typography/) en utilisant les fonctions `min()`, `max()` ou plus récemment `clamp()`. L'exemple est toujours montré pour les tailles de police, mais on peut l'appliquer à n'importe quelle propriété. Je l'utilise par exemple pour les marges et les paddings, pour avoir des espacements qui s'adaptent à la taille de l'écran dès que la différence entre les maquettes mobile et desktop est trop grande, évitant un saut brutal et assurant un rendu optimal sur toutes les tailles d'écran.
