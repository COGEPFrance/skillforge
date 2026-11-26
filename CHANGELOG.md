# Changelog

## Non publié

### PR [#10 — Review d’architecture et cas d’essai](https://github.com/COGEPFrance/skillforge/pull/10)

- Fait partir la revue d’architecture des décisions documentées et du besoin du
  projet ; rend les critères hexagonaux et microservices conditionnels.
- Ajoute une lecture globale des responsabilités, dépendances et scénarios,
  avec distinction entre review de changement et review globale du projet.
- Précise le traitement des décisions absentes ou contradictoires, de la dette
  indépendante et des frontières avec les autres reviewers.
- Définit l’évaluation progressive des skills avec le dépôt local séparé
  `skillforge-tests`, ses cas et ses attentes. L’outillage de préparation ne
  remplace ni une exécution du reviewer ni l’évaluation de ses constats.

### PR [#9 — Personnalisation des skills](https://github.com/COGEPFrance/skillforge/pull/9)

- Intègre les règles partagées dans les références de production et de revue,
  notamment contrats typés, modèles Pydantic, invariants et mises à jour validées.
- Impose `Field` avec description et exemples synthétiques sur chaque champ
  Pydantic déclaré, en production et en revue ; conserve les métadonnées des
  champs hérités. Retire les exemples métier et suffixes des critères génériques
  de modèles, ainsi que le récit du revert dans le journal d’arbitrages.
- Rend l’ordre des phases code, tests et documentation libre tout en imposant
  une seule phase active, terminée et validée avant la suivante. Clarifie les
  validations préliminaires, les réserves de preuves et les reprises après correction.
- Limite chaque PR à un sujet cohérent et privilégie de petites livraisons
  autonomes avec dépendances, rollback et avancement traçables dans le changelog.
- Conserve les mocks pour les nouveaux TU et le minimum de couverture de 80 %
  (90 % visés). Prévoit une suite métier isolée en CI, une couverture métier
  distincte et l’intégration sur base/infrastructure et jeux de données dédiés.
- Retire du catalogue `scaffold-arclith-service` et `apply-arclith-blueprint` :
  les consommateurs doivent utiliser les skills propriétaires Arclith. Le
  catalogue passe de 48 à 46 skills ; les workflows communs conservent le routage
  et les validations, sans dupliquer les procédures du framework.
- Retire les conventions locales de chemins et suffixes des règles de modèles
  métier. Rend les références autonomes et les liens des sources historiques
  indépendants du dossier local d’anciennes règles, dont la suppression reste à venir.

Cette section décrit le contenu proposé par la PR ; aucune version ni release
n’est publiée par cette entrée. Le changement porte sur des instructions et
n’introduit ni moteur d’agents, ni installation automatique, ni CI de service
consommateur. Pour revenir au catalogue précédent, rétablir ensemble ses skills
et les workflows/références associés.
