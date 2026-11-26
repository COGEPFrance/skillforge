# Changelog

## Non publié

### PR [#12 — Méthode et contrôles des revues de PR](https://github.com/COGEPFrance/skillforge/pull/12)

- Cadre les dépôts, sources applicables et diffs complets depuis le merge-base
  dans une méthode commune chargée par les 20 skills de revue.
- Précise la compatibilité des valeurs et validations, l’identité des gardes
  historiques, le cycle de vie des réservations et les entrelacements concurrents.
- Exige les preuves de non-régression, de normalisation et d’état durable complet,
  et la réutilisation des contrats et réponses d’erreur adaptés au flux existant.
- Définit les gravités et commentaires prêts à publier, sans publication
  automatique ; conserve les verdicts, contrôles autorisés et choix de tests.

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
