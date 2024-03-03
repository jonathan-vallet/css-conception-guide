# 3.3. Le viewport

## 3.3.1. Définition et résolution

Avant de parler du viewport, faisons un petit point sur la résolution. En anglais le terme _resolution_ se traduit aussi bien par résolution (_display resolution_) que la définition (_pixel density_).

La définition, c’est le nombre de pixels présents sur la dalle. On la calcule en pixels en multipliant le nombre de pixels sur une ligne horizontal par une ligne verticale. La définition d’un écran d’ordinateur en HD est souvent de 1920 x 1080 pixels (soit 2073600 pixels, communément 2 Mégapixel pour les photos). Un écran 4K fera 3840 x 2160 pixels, soit 4 fois plus de pixels.

La résolution est le rapport entre la définition de la dalle, en pixel, et sa taille physique, exprimée en pouces. On parle de Point Par Pouce (PPP), ou en anglais de Dot Per Inch (DPI). Plus la résolution est élevée, plus la densité de pixels sera importante sur la dalle. Le terme “Retina” a été inventé par Apple pour désigner les smartphones dotés d’une résolution supérieure à 300ppp, densité jugée comme idéale pour la lecture sur une écran de smartphone.

## 3.3.2. Viewport

Nous en arrivons au viewport, qui désigne la surface de la fenêtre du navigateur. Depuis l'arrivée des écrans retina, 4k ou autre, il faut distinguer 2 notions de surface:

- La surface physique: le nombre réel de pixels qui composent l'écran (sa définition)
- La surface utilisable: le nombre de pixels qui composent l'écran pour le navigateur. Cette information est celle qu'on obtient avec le device-width/device-height. Un écran rétina aura plus de pixels sur sa dalle, mais le navigateur considérera qu’il y a moins de pixels pour lui.

Par défaut, la taille du viewport sur un terminal mobile est bien plus grande que la surface, ce qui fait qu'un site sera affiché avec un dézoom conséquent si on ne précise pas de viewport dans la balise meta. Ce paramètre est parfois réglable et **vient du navigateur**.

Pour des exemples certe datés mais représentatifs, voici les valeurs par défaut de quelques devices:

<table>
  <tr>
   <td><strong>Device</strong>
   </td>
   <td><strong>Surface réelle (définition)</strong>
   </td>
   <td><strong>Surface utilisable (navigateur)</strong>
   </td>
   <td><strong>Viewport</strong>
   </td>
  </tr>
  <tr>
   <td>iPhone 3
   </td>
   <td>320x480px
   </td>
   <td>320x480px
   </td>
   <td>980px
   </td>
  </tr>
  <tr>
   <td>iPhone 4
   </td>
   <td>640x960px
   </td>
   <td> 320x480px
   </td>
   <td>980px
   </td>
  </tr>
  <tr>
   <td>iPad
   </td>
   <td>768x1024px
   </td>
   <td>768x1024px
   </td>
   <td>980px
   </td>
  </tr>
  <tr>
   <td>iPad 2
   </td>
   <td>1536x2048px
   </td>
   <td>768x1024px
   </td>
   <td>980px
   </td>
  </tr>
</table>

En résumé, un iphone 4 dispose d'une définition de base de 640px, qui correspondent en css à 320px, mais par défaut le navigateur disposera de 980px pour afficher un site.

Pour permettre cet affichage, le niveau de zoom par défaut vaut device-width/taille du viewport. Notre iphone aura un niveau de zoom initial de 320/980 ~= 0.326.

Pour pallier ce problème il existe la balise meta `viewport`, qu'on utilise généralement ainsi:

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
```

Ça permet de définir la largeur du viewport à la largeur utilisable du device (320px pour notre iphone 4), et à un niveau de zoom de 1.

Libre à vous d'utiliser d'autres valeurs si besoin, maintenant que vous savez à quoi elles correspondent.

Pour des raisons d’accessibilité, il ne faut jamais mettre l’option user-scalable="no", qui empêche le zoom sur votre site. Si le texte n'était pas assez lisible pour un utilisateur, il ne serait pas en mesure de zoomer dessus.

Vous pouvez ajouter des informations minimum-scale ou maximum-scale pour définir un niveau de zoom minimum ou maximum si besoin.

On peut également définir la hauteur (`height`), mais elle est encore moins uniforme que la largeur des terminaux mobiles, c'est assez peu utilisé.
