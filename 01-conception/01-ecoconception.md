## 2.1. Éco-conception

Avant même de concevoir l’architecture d’un site, il faut dès aujourd’hui que les différents acteurs du développement de sites web soient sensibilisés à l’éco-conception. Il s’agit d’une méthodologie standardisée à l’échelle mondiale (ISO 14006 : 2011; ISO 14062: 2003). Appliquée au numérique, On parle plutôt de conception numérique responsable que d’éco-conception, ayant pour objectif de proposer de nouveaux services numériques moins impactants sur l'environnement tout au long de leur cycle de vie. La conception d’un service numérique doit donc intégrer les trois facettes du développement durable que sont le social, l’environnement, et bien évidemment l’économie (le triple résultat du 3 P: People, Planet, Profit).

> En quelques chiffres:
> 10 milliards de terminaux connectés, 17 en comptant l'iot.
> 1500TWh d'électricité, l'équivalent d'une cinquantaine de centrales nucléaires. Si c'était un pays, Internet serait le 6ème consommateur mondial d'électricité.
> Le poids moyen d'une page est de près de 2Mo, avec plus de 75 requêtes en moyenne.
> Sources:
> https://iot-analytics.com/state-of-the-iot-update-q1-q2-2018-number-of-iot-devices-now-7b/ > https://www.researchgate.net/publication/320225452_Total_Consumer_Power_Consumption_Forecast > https://sustainablewebdesign.org/ > https://httparchive.org/reports/state-of-the-web

Les enjeux de l’éco-conception sont:

- d’améliorer l’expérience utilisateur et la dimension sociale en développant des sites portés sur l’accessibilité;
- de réduire les coûts et la dette technique en réduisant la quantité de bande passant et en augmentant la durée de vie des terminaux;
- de réduire l’empreinte environnementale en réfléchissant à une conception fonctionnelle.

La démarche de conception numérique responsable vise à trouver le meilleur équilibre entre le niveau de performance, la qualité du service et les ressources. Elle s’applique à chaque étape d’un projet, de sa conception à sa réalisation, et en amont et avale du développement.

### 2.1.1. Le principe

#### 2.1.1.1. Conception UX/UI

- Se concentrer sur l’essentiel et supprimer les fonctionnalités qui ne servent pas ou peu;
- Penser mobile first;
- ne pas créer d’ambiguïtés dans l’interface, et faire gagner du temps à l’utilisateur dans son parcours;

#### 2.1.1.2. Accessibilité

- Inclure les utilisateurs déficients pour augmenter la dimension social;
- Exclure les animations et interactions pouvant léser les utilisateurs déficients

#### 2.1.1.3. Développement

- Utiliser des outils de minification du code pour réduire le poids des fichier, on a abordé le sujet dans la partie tests de performance;
- Utiliser des outils de linting pour éviter d’embarquer du code inutile (doublon, jamais appelé…) pour limiter au plus possible la dette technique.

#### 2.1.1.4. Hébergement

- Choisir un hébergeur écologique qui alimente ses datacenters via de l’énergie renouvelable.

  > Je ne peux que conseiller le livre énonçant 115 règles d'éco-conception pour le web. (https://ecoconceptionweb.com/), bien que pour la première règle ils partent du constat d'une étude de Standish Group
  > (https://www.standishgroup.com/sample_research_files/Exceeding%20Value_Layout.pdf, version plus récente de l'étude).
  > Il faut relativiser les résultats de cette étude puisque le scope est limité, il n'a été fait que sur 4 sites internes à 4 sociétés. Cela ne veut en aucun cas dire que cette étude est fausse bien sûr, et je pense que beaucoup de développeurs savent au cours du développement qu'ils réalisent du code qui sera très peu utilisé. Mais les résultats de cette étude ont été cités à tort et à travers pour promouvoir Scrum, je voulais juste rétablir leur relative fiabilité.
  > Les outils d'analytics sur vos sites devraient vous donner la tendance des fonctionnalités utilisées, il ne faut pas hésiter à récupérer ces informations pour vous faire une idées sur chacun de vos site de ce que les gens voient ou pas.
