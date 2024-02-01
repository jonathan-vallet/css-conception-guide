# 2.8. Styleguide

Le Styleguide (ou guide style en français), est un document regroupant toutes les informations utiles du design d’un site. Pour ce qui nous intéresse, à savoir un styleguide pour l’intégration, on retrouve généralement une section avec l’ensemble des couleurs utilisées, les icônes à disposition, les éléments de typographie, les différents types de boutons…

L’intérêt d’un tel outil est qu’il est montrable et exportable très facilement. Un nouveau développeur sur le projet prendra rapidement connaissance de comment sont structurés les éléments. On identifiera rapidement les composants du site pour les réutiliser au maximum et avoir un design cohérent. Les graphistes réalisent souvent eux même un styleguide avec leurs outils.

Avec le design atomique on peut avoir un styleguide bien plus complet avec l’ensemble des atomes, molécules et organismes, pour finir par l’ensemble des templates avec des placeholders.

> Comme on a pu voir sur le découpage atomique, la différence entre un template et une page, c'est le contexte. Le styleguide représente le template d'une page, hors contexte. C'est l'occasion idéale pour rappeler des éléments de spécifications du site.
>
> Pour les images j'utilise des placeholders générés sur (https://placeholder.com/), ce qui évite de créer des images spécifiques, et surtout ces images indiquent les dimensions, ce qui donne une indication du ratio de l'image et du format attendu pour obtenir le rendu souhaité.
>
> Pour les titres, je reprends souvent le nom du bloc ou le type de titre, éventuellement avec une indication de longueur. Par exemple :
> Article title (24 chars)
> Very long article title (39 characters)
>
> N'hésitez pas à varier les tailles de contenu du minimum au maximum pour montrer des cas extrêmes qu'il sera possible de rencontrer à un moment une fois la page dynamisée.

## 2.8.1. Différents types de styleguides

Suivant la techno que vous utilisez vous préférerez plutôt un outil de styleguide à un autre. L’idéal est d’en trouver un adapté au langage de templating de votre site, pour éviter d’avoir à dupliquer vos blocs et devoir maintenir 2 templates différents, ce qui n’est pas viable à long terme pour qu’il reste maintenu.

Un styleguide adapté au design atomique serait celui de [Patternlab](https://demo.patternlab.io/). La démo présente bien la façon dont ils ont découpé les composants, cela peut aider à mieux appréhender le design atomique. Pour des projets PHP avec des templates twig on peut utiliser [Fractal](https://fractal.build/), ou [Storybook](https://storybook.js.org/) pour énormément de framwork comme VueJS ou React.

Une approche différente pour la génération du styleguide est proposée par [KSS](https://warpspire.com/kss/) par exemple, où on fait la documentation dans les fichiers .scss ou .less, et utilisant les pré-processeurs CSS pour générer le styleguide associé.

Un document bien plus complet qu’un styleguide qui est une sorte de bible que chaque développeur front devrait lire selon moi, c’est la documentation du [material design](https://m3.material.io/) mis en place par Google, généralisé à tous leurs produits depuis quelques années. Ils décrivent précisément le moindre détail de comment utiliser les couleurs, placer les boutons, comment gérer l’affichage de plusieurs boutons pour mettre l’emphase sur le plus important, comment faire des transitions simples mais qui procurent la meilleure expérience utilisateur possible tout en suggérant un ordre de lecture de l’information… En plus de ça il y a énormément d’exemple de comment faire et comment ne pas faire pour comparer avec des mini vidéos. En terme de design ils ont poussé la réflexion très loin, la plupart des sites n’ont pas besoin de ce niveau de détail, mais on peut s’inspirer de leurs bonnes pratiques et retour d’expérience.
