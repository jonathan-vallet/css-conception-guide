# 2.2. Accessibilité

L’accessibilité est souvent abrégée en _a11y_ ce qui représente “a” suivi du nombre de lettres entre “a” et “y” dans le mot \*
_accessibility_, puis “y”. Dès la naissance du web il y a plus de 30 ans maintenant (le 12 mars 1989), son créateur Tim Berners-Lee, aujourd’hui directeur du W3C (World Wide Web consortium), voulait en faire un bien commun à tous. Selon lui:

> "The power of the Web is in its universality. Access by everyone regardless of disability is an essential aspect."

<p style="text-align: right">
<em>-- Tim Berners-Lee, directeur du W3C inventeur du World Wide Web</em></p>

L’accessibilité numérique doit être prise en compte dès la conception matérielle. La plupart des distributeurs de billets de métro ne permettent pas la synthèse vocale, les rendant inaccessibles aux non-voyants. Au niveau logiciel, les systèmes d’exploitation et navigateurs récents sont conformes aux règles d’accessibilité. Là où il reste du travail à faire, c’est sur l’accessibilité des contenus, et notamment des pages webs.

On confond souvent par abus de langage le handicap et la déficience. La déficience est le constat de la perte ou l’altération d’une structure ou fonction psychologique, physiologique ou anatomique. les déficiences engendrent des incapacités:

- une déficience visuelle (malvoyant, aveugle, daltonien…) engendre une incapacité à voir correctement ou à correctement distinguer les couleurs;
- une déficience auditive (sourd, malentendant…) engendre une incapacité à entendre correctement;
- des troubles moteurs engendrent une difficulté ou impossibilité à utiliser certains membres…
- des déficiences intellectuelles (alzheimer, sclérose en plaque, troubles "dys" comme la dyslexie, trouble de l'attention...) qui engendrent diverses incapacités, notamment de concentration, compréhension ou mémorisation.

Une déficience devient un handicap lorsque le contexte ne permet pas de réaliser une action. C’est pour ça qu’on parle de situation de handicap. Par exemple une personne non-voyante a une déficience visuelle, pourtant dans un contexte d’obscurité il ne se trouve pas dans une situation de handicap.

Les handicaps sont classifiés en 5 grandes catégories :

- le handicap **moteur**,
- le handicap **sensoriel** (visuel, auditif),
- le handicap **psychique** (pathologies perturbant la personnalité),
- le handicap **mental** (déficiences intellectuelles)
- et les **maladies invalidantes**.

En rendant un site accessible, on permet qu’il soit utilisable par tous et adapté à tous les types de déficience. Quand une personne présentant une déficience navigue sur un site, sa déficience ne doit pas l'empêcher pas de faire l'action voulue.

Le Web ne doit pas être ce contexte handicapant. Au contraire il doit permettre à la personne en situation de handicap de réaliser plus facilement des actions (commander en ligne, joindre un service client, communiquer avec ses proches, etc…).

Il existe différents outils de compensation suivant le type de handicap commes la synthèse vocale pour les non-voyants, des polices d’écritures adaptées aux dyslexiques, des outils de suivi du regard pour les handicaps moteurs.

> D'après les chiffres de l'INSEE en 2007, il y a 12 millions de personnes se déclarant en situation de handicap en France, soit 20% de la population :
>
> - 5.4 millions de personnes avec un handicap auditif
> - 3.5 million de personnes à mobilité réduite
> - 1.7 million avec un handicap visuel
> - 700 000 personnes avec une déficience mentale
>   ([source](https://www.insee.fr/fr/statistiques/1373648))
>
> Ce chiffre monte à 40% si on prend en compte les situations de handicap temporaire, soit fracture empêchant l'utilisation de souris, des lunettes cassées empêchant la bonne lisibilité d'un site…
>
> D'après le rapport établi par l'OMS en 2011, le handicap concernerait 15% de la population mondiale.
> ([source](https://www.who.int/publications/i/item/9789241564182))
>
> Il faut également prendre en compte le fait que la population est vieillissante dans de nombreux pays.
>
> 80% des handicaps sont invisibles. On ne remarquera pas de prime abord qu'une personne est daltonienne ou malentendante par exemple.

## 2.2.1. Les WCAG

L’accessibilité est définie par les **WCAG** (Web Content Accessibility Guidelines), recommandations publiées par la WAI (Web Accessibility Initiative) qui est le groupe de travail spécialisé sur l’accessibilité du W3C. Le but est de fournir aux concepteurs de sites web (UI / UX, développeurs, chefs de projets, rédacteurs etc) un certain nombre de conseils et recommandations afin de rendre les sites accessibles aux personnes en situation de handicap.

Les WCAG sont enregistrées en norme internationale ISO (ISO/IEC 40500:2012), ce qui est intéressant pour propager les recommandations aux grandes entreprises qui respectent les normes ISO. Ses spécifications reposent que 4 grands principes:

- Perceptibilité: donner un moyen alternatif aux utilisateurs de percevoir une information, comme un texte alternatif sur une image.
- utilisabilité: ne pas proposer un unique moyen d’utiliser un site web, comme la souris; et laisser le temps aux utilisateurs de lire le contenu. Pas de rechargements intempestifs, de changement de focus ou de temps limité sur l’affichage d’un contenu.
- compréhensibilité: indiquer de façon claire les éléments d’un site. Éviter le jargon technique non expliqué, informer au plus tôt que l’utilisateur a mal rempli un formulaire.
- robustesse: assurer la compatibilité avec les agents utilisateurs comme les technologies d’assistance, les navigateurs, les différentes résolutions...

Au niveau historique, il y a eu 3 versions des WCAG:

(source: [http://www.accessibilite-numerique.wikibis.com/wcag.php#cite_note-3](http://www.accessibilite-numerique.wikibis.com/wcag.php#cite_note-3)):

- WCAG 1.0, en 1999, qui propose 14 directives dont le but est de proposer un contenu compréhensible et navigable suivant différents contextes utilisateurs. Ces directives sont accompagnées de 65 points de contrôle, qui représentent ce qui doit être validé pour s’assurer de l’accessibilité d’un site. Chaque point de contrôle a un certain degré d’importance:
  - Ce qui doit être fait, qui correspond au niveau A;
  - Ce qui devrait être fait, le niveau AA;
  - Ce qui peut être fait, le niveau AAA.
- WCAG 2.0, en 2009, qui s’étend à toutes les technologies actuelles et futures de conception de page web, alors que les WCAG 1.0 concernait principalement le HTML. Les spécifications sont plus claires, avec un guide d’implémentation et des critères de succès plus simple à vérifier que ça soit humainement ou via des logiciels. Les 12 directives sont également découpées en critères de succès de niveau A, AA et AAA, mais en prenant en compte la faisabilité technique:
  - des critères de succès essentiels pouvant s’appliquer raisonnablement pour atteindre le niveau d’accessibilité minimum A;
  - des critères de succès supplémentaires pour atteindre un niveau d’accessibilité plus avancé AA;
  - des critères de succès plus compliqués à mettre en oeuvre, ne pouvant pas s’appliquer à toutes les ressources, pour atteindre un niveau d’accessibilité supérieur AAA.
- WCAG 2.1, en juin 2018, se base sur la 2.0 en ajoutant 17 nouveaux critères portant sur l’accessibilité mobile, la malvoyance et les handicaps cognitifs. S’il s’est écoulé 10 ans entre les 2 versions, c’est grâce à la stabilité des principes de WCAG qui n’évoluent pas et sa neutralité par rapport aux technologies.

[https://www.w3.org/WAI/standards-guidelines/wcag/new-in-21/](https://www.w3.org/WAI/standards-guidelines/wcag/new-in-21/)

Aujourd’hui le standard adopté est la WCAG 2.1 avec un niveau AA, ce qui équivaut à répondre à tous les critères de niveau A et de niveau AA.

Les WCAG sont accompagnées d’une partie technique sur la façon d’appliquer les critères normatifs dans des langages spécifiques.

## 2.2.2. L’application

Le W3C recommande de respecter le niveau d’accessibilité AA. Concernant le niveau AAA, certaines des règles peuvent être prises en compte, comme les alternatives aux médias, ne pas mettre de texte sur les images…

Mais d’autres peuvent être très complexes comme le fait que le contenu doit être compréhensible par toute personne de 2nd cycle (niveau lycée): même si on parle d’un sujet pointu, le propos devrait être suffisamment vulgarisé pour être compris de tous.

En France, les sites de l’État, des collectivités territoriales et des administrations publique doivent être accessibles depuis 2012. Depuis 2019 la loi s’est étendue aux entreprises de plus de 250 millions d’euros de chiffre d’affaire.

Ils respectent le RGAA 4.0 (Référentiel Général d’Amélioration de l’Accessibilité, anciennement Référentiel Général d’Accessibilité pour les Administrations jusqu’à la RGAA 3.0), alignées sur les WCAG. Les référentiels retiennent des techniques pour rendre l’application des WCAG plus simple à aborder. Les critères du RGAA sont formulés en questions binaires pour vérifier leur application simplement.

[https://blog.clever-age.com/fr/2019/04/26/a11y-paris-2019/](https://blog.clever-age.com/fr/2019/04/26/a11y-paris-2019/)

[https://www.numerique.gouv.fr/publications/rgaa-accessibilite/](https://www.numerique.gouv.fr/publications/rgaa-accessibilite/)

Aux États-Unis d’Amérique, l’accessibilité est régie par le CVAA (Communications and Video Accessibility Act). Il n’y a pas de distinction entre privé et public. Beaucoup de procédures de discrimination sont lancées par des collectifs de personnes en situation de handicap en cas de non accessibilité des sites de grosses sociétés, ce qui pousse un grand nombre d’acteurs à respecter les règles d’accessibilité.

> Depuis début 2019, le CVAA s'applique également aux jeux vidéos. Dans ce domaine, de nombreux jeux proposent déjà différentes options pour gérer la plupart des handicaps :
>
> - **Des sous-titres sur tous les dialogues pour les malentendants.** En 2004, _Half Life 2_ avait même une option où tous les sons ambiants étaient retranscrits en texte à l'écran;
> - **Le grossissement de l'interface du jeu et des textes pour les malvoyants;**
> - **Des manettes et contrôleurs adaptés aux handicaps moteurs.** Le _Steam controller_, configurable intégralement, permet à certains joueurs de jouer avec une seule main. Ou encore la _manette Xbox Adaptive Controller_ de Microsoft;
> - **La désactivation d'effets visuels et flashs pour l'épilepsie;**
> - **Une difficulté adaptable pour que le jeu soit accessible à tout public.** _Céleste_ permettait un mode "assist" pour simplifier l'expérience si besoin en réduisant la vitesse du jeu, un saut supplémentaire…
>
> On trouve aussi des initiatives de certains jeux comme A blind legend, jeu sans aucune image où on incarne un chevalier aveugle, guidé par les sons environnants et la voix de sa fille qui l'accompagne. Le son binaural permettant de se très bien se repérer dans l'espace, le jeu sensibilise grandement au ressenti des non-voyants.
> Dans un autre genre, un des tous premiers mod créé sur le jeu Skyrim avait été de remplacer toutes les araignées géantes qu'on rencontrait par des oursons, ce qui avait été acclamé par tous les arachnophobes.

## 2.2.3. Vérification des critères

Pour être conforme au exigences des WCAG, il faut satisfaire les critères de succès. Depuis la WCAG 2.0, ces critères sont testables fonctionnellement, ce qui permet de déterminer objectivement si ils sont effectivement satisfaits.

Mais ce n’est pas parce qu’un critère de succès sera respecté que la fonctionnalité sera accessible. L’idéal étant de faire des tests d’utilisabilité avec des utilisateurs présentant différents handicaps pour déterminer à quel point ils peuvent utiliser nos fonctionnalités et accéder à notre contenu. On estime qu’un tiers des critères peuvent être testés par le code, et les deux tiers testables par des humains uniquement.

> Une personne valide pourra difficilement tester et avoir le bon ressenti sur la navigation avec certains handicaps. Des outils permettent de simuler les couleurs de différents types de daltonismes, ou de la synthèse vocale pour naviguer à l'aveugle.
>
> Mais pour avoir eu l'occasion de voir des personnes non voyante naviguer sur différents sites webs, notre ressenti n'est vraiment pas le même. Avec l'oreille entraînée et un bon lecteur d'écran, un non voyant peut assimiler du contenu et naviguer plus vite qu'une personne valide si le site est accessible! Et c'était impossible pour moi de comprendre ce que lisait le lecteur d'écran tant il parlait vite.

## 2.2.4. Amélioration progressive

L’amélioration progressive, (_progressive enhancement_ dans la langue de Ozzy Osbourne) vise à concevoir un site en séparant la stack front de manière à prendre en compte l’accessibilité et le référencement.

- La couche sémantique, en HTML, est réalisée en premier pour présenter le fond, et la façon de hiérarchiser le contenu;
- La couche visuelle en CSS permet la mise en forme et enjolive le contenu;
- La couche événementielle en Javascript permet l’interactivité.

Ces couches sont développées de la plus simple à la plus complexe, en _bottom-up_, à l’inverse de la dégradation élégante, en _top-down_, qui vise à faire son développement puis d’étendre la compatibilité au plus grand nombre de devices après (impliquant un grand nombre de _polyfill_).

Avec une conception en amélioration progressive, la couche sémantique correctement balisée est normalement accessible pour tous.

L’accessibilité a très longtemps été dénigrée par les développeurs, pourtant elle a un impact majeur sur l’expérience de tous les utilisateurs sur vos sites. C’est aujourd’hui un élément indispensable à prendre en compte lors de la création d’un site, et ce dès la conception.

Il existe de nombreuses bonnes pratiques à mettre en place au niveau de la sémantique de vos pages et du développement, mais il faut aussi que les parties créatives prennent en compte les besoins d’accessibilité dès la conception pour un grand nombre de critères, comme le respect des ratios de couleurs, les effets de focus, les champs de formulaire...
