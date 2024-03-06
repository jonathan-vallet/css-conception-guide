# Guide de conception de sites web frontend

Le but de ce guide n’est pas de vous apprendre les bases de la CSS. Vous n’apprendrez pas les propriétés une par une ou comment créer votre première feuille de style. Je considère que si vous lisez ceci, vous avez déjà des bases sur l’écriture des règles CSS et sur la mise en page générale d’un site.  
Ce qui m’a poussé à écrire, c’est pour expliquer comment.

Comment concevoir d’abord. Le passage de la réception de maquettes au début de l’intégration est trop souvent bâclé, on trouve de nombreuses répétitions de code qui pourraient être évitées à cause d’erreurs de conception.  
Comment bien structurer son code, utiliser les propriétés les plus adaptés suivant chaque besoin. J’ai fait mes premiers pas sur le web avec de la mise en page en tableau, puis en CSS 2 avant Internet Explorer 7, avec des float car on n’avait même pas de display : inline-block… Aujourd’hui entre les inline-block, flex, grid, columns… j’ai vu trop souvent des développeurs se prendre la tête sur des problématiques qui aujourd’hui peuvent être résolues très simplement.  
Comment ça fonctionne également. CSS est rempli de subtilités qui peuvent être frustrantes quand on débute en intégration, et j’ai souvent vu des développeurs complexifier leur code alors qu’une meilleure compréhension du fonctionnement des règles entre elles aurait largement simplifié le code.

## Disclaimer

Ce guide est le fruit de mon expérience personnelle, et de mes lectures. Il n’a pas pour but d’être exhaustif, et je ne prétends pas détenir la vérité absolue. Je l'ai écrit il y a quelques années déjà, il est possible que des recommandations soient obsolètes ou le soient dans quelques années, ou que vous ne soyez pas d’accord avec certaines d’entre elles. Je vous invite à me contacter pour en discuter, et à me faire part de vos remarques.

## Table des matières

### Comment concevoir

- [Eco-conception](/01-conception/01-ecoconception.md)
- [Accessibilité](/01-conception/02-accessibilite.md)
- [Comprendre son client](/01-conception/03-comprendre-son-client.md)
- [Découpage des maquettes](/01-conception/04-decoupage-des-maquettes.md)
- [Design Atomique](/01-conception/05-design-atomique.md)
- [Retours sur les maquettes](/01-conception/06-retours-maquettes.md)
- [Conventions de nommage](/01-conception/07-conventions.md)
- [Styleguide](/01-conception/08-styleguide.md)
- [Tests automatisés](/01-conception/09-tests.md)

### Conception de jeux vidéos vs le web d’aujourd’hui

- [Intro](/02-jeux-videos/01-intro.md)
- [Signs &amp; Feedbacks](/02-jeux-videos/02-signs-feedbacks.md)
- [Prototypage et étapes de conception](/02-jeux-videos/03-prototypage.md)
- [3C](/02-jeux-videos/04-3c.md)

### Comment ça fonctionne

- [Intro](/03-fonctionnement/01-intro.md)
- [Comment s'affichage une page web](03-fonctionnement/02-affichage-page.md)
- [Le viewport](03-fonctionnement/03-viewport.md)
- [L’empilement et le z-index](03-fonctionnement/04-empilement.md)
- [Le flow](03-fonctionnement/05-flow.md)

## Contact

Si vous voulez suivre les mises à jour de ce guide, ou me contacter pour discuter de son contenu, vous pouvez me suivre sur Twitter [@joevallet](https://twitter.com/joevallet)

## Licence

Ce guide est sous licence [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.fr). Vous êtes libre de le partager et de l’adapter, à condition de citer l’auteur et de ne pas en faire une utilisation commerciale.

© 2024 Jonathan Vallet (Satanimax). Tous droits réservés.
