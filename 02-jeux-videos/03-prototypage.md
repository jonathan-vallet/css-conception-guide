## 2.2. Prototypage et étapes de conception

Comme je l’expliquais en introduction de cette partie, le web évolue dans le même sens que le jeu vidéo. À savoir qu’on pouvait faire un site ou un jeu seul aux début, mais qu’aujourd’hui il faut souvent une multitude de corps de métiers pour les réaliser.

Au début des jeux on avait un développeur seul, parfois un graphiste, puis avec l’apparition de la 3D il y a fallu se spécialiser une personne pour modéliser, une autre pour les textures, une pour l’animation... Aujourd’hui pour les gros jeux vidéos il y a des scénaristes, écrivains, réalisateurs, chorégraphes, créateurs de mode, décorateurs… Les reconversions sont fréquentes, j’ai déjà vu un archéologue qui a participé au développement d’un jeu pour apporter un détail historique, et qui finalement est resté dans le secteur de la 3D dans les jeux par la suite.

Pour les plus gros jeux aujourd’hui il y a au coeur de la production plusieurs centaines de personnes réparties sur plusieurs studios dans différents pays. Et pourtant ça ne les empêche pas de sortir des produits relativement stables. Pour réaliser des sites web on devrait s’inspirer un peu plus de certaines méthodes du jeu vidéo.

### 2.2.1. Dans les jeux vidéos

#### 2.2.1.1. La conception

Au début on part d’une idée. Le game designer établit quelques documents permettant de présenter ce que sera le jeu souhaité. Ça permet de cadrer et borner son concept, et évite de partir dans toutes les directions avec plein d’idées qui semblent cool parce qu’elles fonctionnent ailleurs, mais qui ajouteraient juste de la complexité sans procurer de fun au joueur.

Le principal document est le GCD: **Game Concept Document**. Il se doit d’être clair et concis, en texte entre 1 et 3 pages, ou sous forme de slides entre 5 et 10; pour avoir uniquement l’essentiel, à savoir:

- Une fiche d’identité avec un nom (souvent provisoire), le genre, le public-cible, la technologie, le support...
- Un pitch: il résume l’intention du concept en une phrase simple. Cette phrase peut être de la forme : "C'est un jeu de ... où le joueur doit ... en ... .". Cet exercice est un des plus compliqué, puisqu’on est toujours tenté de vouloir détailler son idée.
- Un scénario, pour exprimer l’ambiance et l’univers du jeu pour être capable de le situer, rien de plus. On ne va pas détailler les personnages ou le monde, juste être capable de s’imaginer à quoi il pourrait ressembler.
- Le Core gameplay, qui explique comment le joueur va interagir avec le monde suivant ses actions. Il se focalise un, voire deux, mécanismes principaux qui vont constituer le coeur de votre jeu.
- Le gameplay secondaire : si le jeu propose énormément d’actions différentes on peut en expliquer une partie qui sont importantes sans être le cœur du jeu.
- La mise en situation: si vous avez quelques exemples à donner de situation qu’on pourra retrouver dans votre jeu avec quelques ébauches graphiques
- Les inspirations : avec quelques images, puisque dans un jeu il va y avoir maximum 5 à 10% d’innovation, il va essentiellement mélanger quelques inspirations. On peut en choisir 3 majeures dont on va reprendre une partie bien précise dans notre jeu, que ça soit sur la direction artistique, une certaine mécanique ou un univers.
- Les Key Selling Points (KSP) : 3 points qui sont là pour convaincre un joueur d’acheter votre jeu. En quoi il est génial et fait la différence avec les autres jeux à leur disposition. Ces points sont là pour clore votre document, il faut qu’ils restent dans les esprits.

> Chaque partie de ce document peut-être lié à une cible différente :
>
> Pour le pitch, il faut imaginer qu'on prenne l'ascenseur avec un inconnu qui nous demande ce qu'on fait. Avant que vous ne soyez arrivé à votre étage, la personne doit avoir compris ce que vous faites.
> Les KSP seront au début surtout à destination du marketing ou de l'éditeur pour avoir des raisons de financer votre concept.
> La fiche d'identité servira aux journalistes
> Les inspirations serviront aux joueurs pour se projeter dans un univers qui leur sera familier et leur plaira.
> Le core gameplay permettra aux développeurs de faire les premiers prototypes.

#### 2.2.1.2. La pré-production

Avant de lancer la production, voire même de présenter son concept à un éditeur, il faut passer par une longue étape de pré-production qui couvre souvent **1/3 du temps du projet**. La préproduction se fait généralement en comité restreint, les besoins techniques étant souvent plus limités.

Une des premières étapes est d’établir la **storyline**. L’écriture de ce document de scénario est un processus extrêmement important car il définit les personnages principaux, l'intrigue, les paramètres et le thème général.

L’étape suivante, c’est le **storyboard**. On reprend son scénario, et on va découper chaque partie en scènes, détailler l’action qui s’y passe, et commencer à entrer dans le détail du concept à chaque section.

Ensuite le game designer va écrire des documents de game design pour détailler chaque partie pendant que le reste de l’équipe crée et teste séparément chaque éléments de gameplay, pour voir s’ils sont réalisables techniquement, trouver la bonne manière de faire, et voir si ça fonctionne. Ce qui permet d’ajuster les documents de game design aux contraintes techniques.

Puis on réalise des **prototypes**. Peu importe que ça soit joli : on utilise des **placeholder**, éléments simples qui représentent ce qu’on veut sans avoir besoin de graphiste. L’essentiel étant de **voir si l’idée est réalisable**. Pas besoin que tout soit réaliste et parfait, pareil au niveau de la physique ou du comportement. Même s’il y a quelques bugs, ce n’est pas un soucis tant que la trame principale est jouable.

Le but est d’arriver à la **FPP: First Playable Prototype**, combinant les différents prototypes pour procurer une expérience de ce à quoi ressemblera le jeu final.

#### 2.2.1.3. La production

C’est là que le nombre de personnes sur le projet augmente. On y consacre 50% du temps du projet. Les producers sont là pour qu’on organise la planification et les estimations du temps de développement, et que tout le monde utilise bien tous les concepts de game design qui ont été définis en amont.

La majorité des contraintes techniques sont déjà éludées grâce aux recherches faites en pré-production, ce qui facilite le travail en équipe puisque tout le monde utilise les mêmes outils qui ont été définis en amont. On créé les animations, les modèles 3D, les textures…

C’est aussi là que les complications surviennent:

- Le game designer imagine des niveaux avec de nouveaux décors que le graphiste n’avait pas prévu de réaliser;
- Le graphiste a réalisé des modèles 3D gourmands en ressource que le programmeur n’arrive pas à intégrer sans perdre en performances;
- On va détecter qu’un élément de gameplay doit être revu, obligeant le game designer à imaginer de nouveaux niveaux… et ainsi de suite.

#### 2.2.1.4. Post-production

Une fois que tous les éléments sont assemblés et que toutes les fonctionnalités sont implémentées, le jeu passe en version alpha. Dans cette version il y a tous les éléments de gameplay, le jeu fonctionne si on suit la trame principale, mais il reste de nombreux bugs, éléments à caler, et performances à améliorer.

C’est à ce moment là qu’on fait des compromis entre améliorer les performances ou la qualité visuelle.

Une fois ces calages terminés le jeu passe en bêta: une version avec tous les éléments et calages, dans laquelle on cherche et on corrige les bugs sur les comportements qui sortent de la trame principale.

Et quand tous les bugs sont corrigés, le jeu passe finalement en version gold, prête au pressage et à la distribution.

### 2.2.2. Sur le web

J’espère que vous avez bien suivi la dernière partie sur la conception d’un jeu vidéo, je vais maintenant faire de nombreux parallèles avec la conception de sites web. N’hésitez pas à revenir en arrière si besoin.

#### 2.2.2.1. La conception

Cette étape correspond à un appel d’offre d’un client si vous êtes en agence, ou à la création d’un nouvel outil ou la refonte d’un site existant si vous êtes dans une start-up ou dans une société qui renouvelle régulièrement ses outils en ligne.

La réalisation d’un document similaire au GCD me semble indispensable, et pourtant les briefs sur lesquels on se base pour savoir ce qu’un client souhaite développer est bien souvent vide ou largement incomplet. Imaginons un tel document pour une demande de réalisation d’un site web:

- Une fiche d’identité avec le nom (de la marque ou du produit), le public-cible, la technologie (CMS souhaité, langage…), le support (quels navigateurs et terminaux avec quel degré d’importance)...
- Un pitch: demander au client de résumer la volonté derrière ce nouveau site ou cette refonte en une phrase aide à capter son objectif bien plus facilement.
- Un scénario, qu’on peut comparer à l’expérience utilisateur: il arrive sur la home, il recherche un produit, il commande… ou bien il passe par une landing de pays, ou lui propose des news adaptées à son profil, on l’invite à naviguer d’articles en articles...
- Le Core gameplay, avec les éléments clés que l’on retrouvera sur le site: des listes d’articles, la mise en avant d’un nouveau produit...
- Le gameplay secondaire : d’autres éléments qu’on retrouvera sur le site, mais moins mis en avant comme des contenus vidéos...
- La mise en situation: on définit un parcours utilisateur idéal pour qu’il trouve le bon contenu ou produit rapidement et préparer la rétention.
- Les inspirations : de quels sites on souhaite s’inspirer, que ça soit des concurrent ou juste des idées de design sympa qu’on a vu ailleurs sur le web.
- Les Key Selling Points (KSP) : 3 points clés qui font que notre site sera mieux que ceux de la concurrence, ou que les utilisateurs auront envie de venir le visiter ou d’utiliser notre interface plutôt qu’une autre.

#### 2.2.2.2. La pré-production

Cette étape est selon moi la plus sous-estimée lors du développement d’un site web.

La partie conception avec le découpage des maquettes et la création des composants
