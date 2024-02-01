## 2.7. Conventions de nommage

Quand vous commencez à coder, définissez une convention sur le nommage de vos classes CSS, la façon d’écrire en camelCase, hyphen-case, snake_case…

Il existe des conventions classiques comme le BEM (Block Element Modifier), avec le nom d’un élément, puis ses enfants séparés par \_\_ et les variations séparées par --.

```css
<a class="block-name__element-name block-name__element-name--variation-modifier">
Link
</a>
```

Ou si vous faites du design atomique, la syntaxe ABEM que j’aime beaucoup ([https://css-tricks.com/abem-useful-adaptation-bem/](https://css-tricks.com/abem-useful-adaptation-bem/)). En camelCase pour mieux regrouper la lecture, un préfixe a, o ou m pour _atom_, _organism \_ou \_molecule_, et pour les variation une classe qui commence par -.

```css
<a class="a-blockName__elementName -variationModifier">
Link
</a>
```

Cette syntaxe permet surtout de pouvoir ajouter des classes pour un changement d’état en JS bien plus facilement, le modificateur étant dans une classe générique. Par exemple en BEM pour définir un élément de menu actif on devrait mettre un modificateur comme

```css
<a class="menu__item">
Link
</a>
```

Mais si on veut ajouter une classe en JS pour gérer un état actif, on devrait faire:

```js
document.querySelector(".menu__item").classList.add("menu__item--active");
```

Alors qu’avec la syntaxe ABEM on peut faire

```js
document.querySelector(".a-menu__item").classList.add("-active");
```

La classe **-active** étant générique, on peut l’ajouter à n’importe quel élément, ce qui me semble plus logique.

Renseignez vous sur les différentes syntaxes pour trouver celle qui convient le mieux à votre façon de faire et celle de vos collègues, tant que vous avez une convention bien établie dès le début.

> Quand j'ai travaillé sur un gros projet où on était une quinzaine de développeurs en même temps, on avait définit les conventions précises pour chaque point, comme mettre les commentaires avant ou dans les _if_ et _else_; savoir si on devait mettre les accolades en fin de ligne ou sur une nouvelle...
> Il ne faut pas oublier que chacun doit faire des compromis sur ses habitudes pour que tout le monde puisse travailler de la même façon, et que le code soit le plus homogène possible. Evitez d'imposer vos habitudes à tout le monde, et soyez prêt à faire des compromis.
