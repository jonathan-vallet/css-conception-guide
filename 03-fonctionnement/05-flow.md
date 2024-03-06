## 3.5. Le flow

Le _Flow layout_ correspond à la façon dont les éléments sont disposés dans la page avant toute application de style.

Dans le flux normal, les éléments _inline_ sont affichés dans la direction dans le sens d'écriture des mots du document, en incise ; tandis que les éléments _block_ sont affichés les uns après les autres selon le mode d'écriture du document. Les éléments sont imbriqués les uns dans les autres suivant cette même structure.

Cette définition, un peu pompeuse par rapport au mode d’écriture, est importante, puisqu'on peut retrouver tous les cas d’affichage possible suivant les langues :

- Pour un document en langue latine, les éléments en ligne sont affichés les uns à la suite des autres de gauche à droite et les éléments de bloc sont affichés les uns en dessous des autres.
- Pour les langues arabes, les éléments en ligne sont affichés de droite à gauche.
- En japonais, les éléments en ligne sont affichés verticalement et les blocs de droite à gauche.
- En mongol, les éléments en lignes sont affichés verticalement avec les blocs de gauche à droite.

L’orientation est en réalité gérée par 3 propriétés CSS :

- `writing-mode`, qui détermine la direction du flux du bloc, par défaut de haut en bas ;
- `direction`, qui détermine la direction du texte et des éléments inline, par défaut de gauche à droite ;
- `text-orientation`, qui change l’orientation du texte, mais uniquement pour les langues à affichage vertical.

### 3.5.1 Vecteurs et flow

Les interactions entre `writing-mode`, `direction`, et `text-orientation` peuvent être visualisées comme des vecteurs qui orientent le flux du contenu. Pensez à ces vecteurs comme des flèches pointant dans la direction où le texte et les éléments doivent s'aligner. Par exemple, dans un mode d'écriture horizontal et de gauche à droite (`writing-mode: horizontal-tb; direction: ltr;`), le vecteur principal pointe de gauche à droite. Lorsque `writing-mode` est vertical (`writing-mode: vertical-rl;`), le vecteur pointe de haut en bas. Cette visualisation aide à comprendre comment les propriétés CSS influencent le positionnement et l'alignement des éléments dans le flux de la page.

> Il existe des propriétés, malheureusement pas encore expérimentales, composées de margin, padding ou border ; inline ou block ; et start ou end. Par exemple, `margin-block-start`, `border-block-end`, `padding-inline-start`... Ainsi que `block-size` et `inline-size`. Elles permettent de gérer le modèle de boîte suivant l'orientation des éléments, parfait pour ne pas avoir à surcharger ses propriétés suivant la langue !
>
> Ce sont des synonymes des propriétés classiques de `width`, `margin-top`, `border-bottom`… dans le sens où, pour un affichage dans le flux normal, `margin-block-start` surcharge ou est surchargé par `margin-top` (selon le poids de la règle CSS).
>
> Je vous laisse vous amuser pour trouver de quel côté sera affiché un `margin-inline-start` suivant les différentes combinaisons de `writing-mode`, `direction` et `text-orientation` !

Pour les chapitres qui suivent, je considérerai le flux normal quand je parlerai des éléments en _block_ ou _inline_ pour simplifier, mais il me semblait important de préciser les variations possibles du flux d’affichage des documents.

Pour en apprendre plus sur le sujet, vous pouvez vous référer à la [MDN sur le CSS Flow Layout](https://developer.mozilla.org/fr/docs/Web/CSS/CSS_Flow_Layout).

### 3.5.2. Flow et accessibilité

Le _flow_ est un concept fondamental pour l'accessibilité. Les technologies d'assistance, comme les lecteurs d'écran, se basent sur le _flow_ pour lire le contenu d'une page. S'il n'est pas correctement géré, les technologies d'assistance peuvent avoir du mal à interpréter le contenu, ce qui peut rendre le site difficile à utiliser pour les personnes en situation de handicap.

Le [critère 10.3 du RGAA (Référentiel Général d'Accessibilité pour les Administrations)](https://accessibilite.numerique.gouv.fr/methode/criteres-et-tests/#10.3) demande de s'assurer que l'ordre dans lequel les éléments sont lus par un lecteur d'écran est cohérent avec l'ordre visuel. Cela signifie que le _flow_ doit être correctement géré pour garantir une bonne accessibilité.
