# 3.1. Comment une page web s’affiche-t-elle ?

## 3.1.1. La récupération des données

Pour qu'une page web s'affiche correctement dans un navigateur, plusieurs étapes sont nécessaires, depuis l'appel HTTP initial jusqu'au rendu final à l'écran. Optimiser les performances d'un site implique souvent d'améliorer le **chemin critique de rendu** (_critical rendering path_ en anglais). Comprendre le processus de rendu d'une page est essentiel pour y parvenir.

Lorsqu'une requête est effectuée, le navigateur reçoit des données sous forme d'octets. Ces octets sont ensuite convertis en caractères, visibles lorsque l'on consulte le code source d'une page.

Ces caractères sont analysés et transformés en _tokens_ (jetons), permettant de distinguer les balises HTML et les règles CSS. Chaque token contribue à la construction d'un nœud selon les spécifications, et ces nœuds forment ensuite un arbre : le DOM pour le HTML, et le CSSOM pour le CSS.

> **Important :** Le processus complet — octets → caractères → tokens → nœuds → modèle d'objet — n'est pas conservé en cache, contrairement aux résultats de vos requêtes. Cela signifie que ce traitement est répété à chaque chargement de page. Pour améliorer les performances, il est donc recommandé de simplifier autant que possible la structure HTML et de minimiser le nombre de règles CSS, afin que ces arbres puissent être construits rapidement.
>
> C'est une des raisons pour laquelle l'éco-conception appelle à la frugalité des pages et pourquoi les outils de mesure de l'écologie numérique prennent en compte la complexité de la strucutre HTML avec une pondération plus importante que le nombre de requêtes et le poids des ressources.

### 3.1.1.1 Chargement en cascade

Lors du processus de récupération des données, les navigateurs adoptent une approche "en cascade" pour télécharger les ressources nécessaires à l'affichage d'une page web. Ce processus commence par le téléchargement du document HTML principal, qui sert de squelette à la page. Une fois que le navigateur commence à lire le HTML, il découvre et initie le téléchargement d'autres ressources telles que les feuilles de style, les scripts, les images.

La lecture du CSS va elle-même déclencher le téléchargement d'autres ressources, telles que les polices de caractères, les images de fond, etc. Si on souhaite optimiser le chargement des polices, on peut utiliser une balise `link` avec l'attribut `rel="preload"` pour indiquer au navigateur de télécharger la police dès que possible dans le HTML sans attendre le chargement du CSS. Cela permet de réduire le temps d'attente pour le chargement de la police, améliorant ainsi l'expérience utilisateur.

```html
<link rel="preload" href="font.woff2" as="font" type="font/woff2" crossorigin />
```

Cependant, il est important de noter que les navigateurs ont des limites sur le nombre de requêtes HTTP qu'ils peuvent gérer en parallèle. Typiquement, cette limite est d'environ 6 requêtes simultanées par hôte, bien que ce chiffre puisse varier légèrement selon le navigateur et sa version. Cette contrainte peut introduire des délais si une page nécessite un grand nombre de ressources externes. Par exemple, si une page HTML fait référence à plusieurs feuilles de style, scripts et images, le navigateur peut être contraint de mettre en file d'attente certaines de ces requêtes, prolongeant ainsi le temps nécessaire pour charger complètement la page.

C'est pour ça qu'on essaye de minimiser le nombre de requêtes HTTP et de faire du chargement différé pour les images ou qu'on utilise du defer ou async pour les scripts.

## 3.1.2. Le DOM

Le **DOM** (_Document Object Model_) représente toute l'arborescence de façon structurée sous forme d'arbre, donc chaque balise HTML est un nœud.

Il est indépendant de toute plateforme et langage. On manipule le DOM avec des scripts, généralement du JavaScript (nextSibling, parentNode, appendChild…), qui permettent de le parcourir et de le manipuler.

Lorsqu'on inspecte la timeline de construction d'une page, avec Chrome par exemple, la construction du DOM est faite sous le label "Parse HTML".

> L'analyse se fait d'abord sur le HTML pour construire le DOM. Pendant sa construction, s'il trouve une indication de CSS à charger, il va la récupérer le plus rapidement possible pour la charger et l'analyser afin de construire le CSSOM, puisque chacune de ces étapes est bloquante pour le rendu final.
>
> C'est pour cette raison qu'on place les ressources CSS en début de page dans la partie `<head>`, afin que ces fichiers soient chargés le plus rapidement possible.

## 3.1.3. Le CSSOM

En parallèle, on trouve le **CSSOM** (_CSS Object Model_). Le fonctionnement de base est similaire au DOM, dans le sens où il va construire une arborescence avec les règles CSS de chaque élément et de leurs enfants, avec les bonnes valeurs en fonction du poids des règles si l'une d'elles est définie sur un même sélecteur par plusieurs règles. Tout ça dans le but de faciliter l'application des différents styles pour le navigateur.

Le navigateur construit un arbre qu'il va parcourir en cascade (d'où le _Cascading Style Sheet_), de l'élément racine jusqu'à chaque élément pour appliquer successivement les règles de chaque nœud parent. Dans l'inspecteur de Chrome, c'est la partie "_Recalculate Style_".

Le CSSOM peut être parcouru via du JavaScript, quand on utilise la propriété style (_document.body.style_), ou avec _window.getComputedStyle()_. Article plus complet => [https://css-tricks.com/an-introduction-and-guide-to-the-css-object-model-cssom/](https://css-tricks.com/an-introduction-and-guide-to-the-css-object-model-cssom/)

## 3.1.4. L’arbre d’affichage

L’arbre d’affichage (_render tree_ dans la langue de Ronnie James Dio) combine le DOM et le CSSOM pour créer un nouvel arbre.

Le processus parcourt le DOM depuis l’élément racine et, pour chaque nœud, il récupère les informations de style correspondantes du CSSOM. Les éléments non visibles, tels que les balises `meta`, `link`, `script`, ainsi que tous les éléments avec `display: none`, sont exclus de cet arbre pour simplifier la structure.

Les règles CSS sont alors fusionnées et calculées. Cependant, à cette étape, les dimensions et la position exactes des éléments sur la page ne sont pas encore déterminées, ce qui sera résolu lors de l'étape suivante.

## 3.1.5. Mise en page

L'étape de mise en page, ou _layout_ (parfois appelée _reflow_ dans la langue de Lemmy Kilmister), utilise l'arbre d'affichage pour calculer la géométrie des éléments. Le navigateur parcourt à nouveau l'arbre, cette fois pour déterminer les dimensions exactes de chaque élément en transformant les styles calculés en valeurs absolues en pixels à l'intérieur de la fenêtre du navigateur.

La largeur des éléments est généralement déterminée par rapport à celle de leur élément parent, tandis que la hauteur d'un élément est calculée en fonction de la hauteur de ses enfants.

Après cette opération, chaque nœud de l'arbre a des informations précises sur le style et la géométrie, permettant ainsi leur rendu final à l'écran.

## 3.1.6. Pixellisation

L'étape de peinture ou de pixellisation des données (_painting_ ou _rasterizing_ dans la langue de Ian Gillan) est enfin le moment où nos éléments prennent vie à l'écran, se transformant en pixel scintillants. Cette étape cruciale dans le processus de rendu d'une page web se déroule en plusieurs étapes :

- repaint
- reflow
- composition

### Repaint ou Reflow?

Le **repaint** et le **reflow** sont deux processus majeurs dans le rendu d'une page, déclenchés chaque fois qu'une modification est apportée à un élément via JavaScript ou une animation CSS, nécessitant un recalcul du rendu de la page. Ces opérations sont bloquantes pour les actions de l'utilisateur et, bien que généralement transparentes, peuvent affecter les performances sur des pages complexes.

- **Repaint** se produit lorsqu'on modifie une propriété visuelle d'un élément sans affecter la disposition de la page, comme la couleur, la visibilité ou l'outline. C'est comme si on repeignait une pièce sans changer la disposition des meubles. Il est généralement moins coûteux en termes de performances que le reflow et peut se produire sans déclencher ce dernier.
- **Reflow** est déclenché par des modifications de la géométrie ou de la position des éléments, c'est-à-dire chaque fois que la disposition de la page change. Cela inclut des modifications de la `width`, `height`, `font-size`, `font-family`, etc. Le reflow permet aux navigateurs de recalculer la position et la géométrie des éléments pour le rendu de tout ou partie du document. C'est comme si on déplaçait les meubles dans une pièce, ce qui nécessite de réorganiser l'espace.

Si on souhaite optimiser les performances d'une page où il y a de nombreuses animations, il faut savoir que les éléments positionnés en `absolute` ou `fixed` limitent le reflow aux éléments qui les contiennent, ce qui peut être un moyen de limiter les opérations coûteuses.

### Composition

La composition est la dernière étape du processus de rendu, où les éléments sont combinés pour former l'image finale. C'est à ce moment que le navigateur assemble les différents calques pour former l'image finale, en tenant compte de la transparence, des filtres, des masques, etc.

### FOUC / FOIC

**FOUC (Flash of Unstyled Content)** désigne le moment où une page est visible sans les styles appliqués, ou lorsque le contenu est mal stylisé parce que les classes le stylisant sont appliquées via JavaScript, ce qui peut prendre plus de temps. Ce phénomène est particulièrement notable avec des éléments comme les carrousels, qui s'affichent en pleine page et tous visibles avant l'application du JavaScript, provoquant un repaint de la page.
C'est un état intermédiaire dans le processus de rendu.

Pour éviter le FOUC, assurez-vous de disposer correctement les éléments d'un carrousel avant l'ajout des classes par le slider, afin que le reflow soit le plus court possible.

**FOIC (Flash of Invisible Content)** est un phénomène similaire, mais qui se produit lorsque le contenu est caché par défaut et qu'il devient visible après l'application des styles.

Pour le texte, on peut utiliser la propriété `font-display` pour définir le comportement de la police de caractères. Par exemple, `font-display: swap` permet de charger une police de remplacement en attendant que la police principale soit chargée, ce qui évite le FOIC, mais peut provoquer un FOUC.

L'avantage du `font-display: swap` est que le texte est immédiatement lisible, même si la police principale n'est pas encore chargée. Ce qui est pratique lorsque le délai de chargement de la police est long, bien que cela force un reflow lorsque la police est chargée.

Pour plus d'informations, consultez :

- [Google Developers: Reflow](https://developers.google.com/speed/articles/reflow)
- [Mozilla Developer: Reflow](http://www-archive.mozilla.org/newlayout/doc/reflow.html)
