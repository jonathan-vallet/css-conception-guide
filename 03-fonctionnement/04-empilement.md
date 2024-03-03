# 3.4. L’empilement et le z-index

Lors de [l'affichage d'une page](02-affichage-page.md), les éléments sont dessinés les uns après les autres dans un ordre donné.

- D'abord, le background et les borders de l'élément.
- Ensuite, les éléments dans le flux normal (non positionnés, en static).
- Enfin, les éléments positionnés, en relative, absolute ou autre.

À chaque étape, les éléments sont affichés dans l'ordre défini dans le DOM – sauf en flex dans le cas où la propriété `order` est modifiée et que l'ordre des éléments doit changer.

Les éléments non positionnés seront affichés dans l'ordre du document et en dessous des éléments positionnés. La propriété `z-index` n'aura aucun effet sur eux.

Le `z-index` permet de modifier cet ordre avec un système de calques, comme dans les logiciels de traitement d'images. Par défaut, en auto, tout est rendu sur la couche 0, et on peut modifier la couche sur laquelle un élément sera affiché avec des valeurs positives ou négatives.

Quand on applique un `z-index` à un élément, cela crée un contexte d'empilement, que l'on pourrait comparer à un groupe dans un logiciel de traitement d'image. Les éléments à l'intérieur seront empilés selon les mêmes règles qu'énoncées précédemment, mais dans le cadre de cet élément uniquement.

Basiquement, si on a un élément de `z-index` 1 contenant un élément avec un `z-index` à 3, en dessous d'un élément avec un `z-index` à 2, le `z-index` 3 sera appliqué dans le contexte de son parent et ne sera pas comparé au niveau 2 ; il sera en dessous.

Mais en dehors du positionnement et du `z-index`, plusieurs propriétés créent également un nouveau contexte d'empilement quand elles sont appliquées. Basiquement, tout ce qui peut modifier les dimensions ou l'opacité d'un élément (une opacité différente de 1, transform, filter, perspective, mask…). En théorie, ce genre de situation arrivera rarement, mais c'est toujours bon de savoir que le contexte d'empilement peut être créé par plusieurs propriétés le jour où un `z-index` s'applique différemment de ce que vous pensiez.

## z-index négatif

Il est possible d'utiliser des `z-index` négatifs. Cela permet de placer un élément derrière un autre sans avoir à modifier l'ordre du DOM. Cela peut être utile pour des éléments de décoration, comme des ombres portées, ou pour des éléments qui doivent être en arrière-plan, comme un fond de page.

Dans ce cas, faites attention à ce que l'élément parent soit placé dans un contexte d'empilement, sinon l'élément avec un `z-index` négatif sera placé en dessous de tout le reste, ou du moins sous le background de son parent.

> Quelques conseils lors de l'utilisation du `z-index` :
>
> Vu que le `z-index` est contextualisé, généralement vous n'avez que quelques éléments à positionner les uns par-dessus les autres, dans le contexte d'un bloc ou d'un composant. Utiliser des `z-index` à 1 ou 2 suffit largement, pas besoin de mettre des valeurs à plusieurs milliers.
>
> Dans votre CSS, mettez toujours un commentaire à côté d'un `z-index`. Je mets toujours "over" ou "under" et la classe du ou des éléments au-dessus ou en dessous. Cela permet de se rappeler pourquoi l'ordre a été défini ainsi plus facilement et savoir comment changer la valeur quand un élément doit se placer entre les deux.
>
> Je l'ai mis juste avant, mais ça vaut le coup d'insister : pas besoin de `z-index` à plusieurs milliers. Vous avez beau mettre un `z-index: 9999999`, il ne sera pas plus devant visuellement qu'avec un `z-index: 10` si les autres couches ne sont pas utilisées. Et cela pourra vous poser des problèmes le jour où il faudra mettre un élément par-dessus, où ça sera la surenchère de `z-index` pour rien.
