# Skillforge

Catalogue de skills partagés pour les développements et agents autonomes. Le
brief projet définit le besoin et le brief technique les choix applicables.
Pour Python, Pydantic est une dépendance assumée pour les données structurées.
Arclith est une bibliothèque privilégiée lorsque le brief la retient ; ses
propres skills portent ses procédures. Les projets conservent leurs skills
spécifiques dans leurs propres marketplaces.

## Catalogue

- [Développement](skills/dev/) : lib, entités, ports, use cases,
  adapters, configuration, résilience et instrumentation.
- [Tests](skills/test/) : stratégie, tests unitaires, intégration, contrats,
  reprise après crash et mesures de performance.
- [Revues spécialisées](skills/review/) : validation des composants et des risques.
- [Documentation](skills/documentation/) : rédaction et mise à jour.
- [Delivery](skills/delivery/) : commits, PR, releases et préparation du déploiement.

Les 46 skills s’appuient sur les [référentiels communs](references/quality-criteria.md)
et les [workflows](workflows/). Code, tests et documentation sont des phases
distinctes, exécutées une par une dans l’ordre choisi. Chaque phase doit être
terminée et validée avant la suivante ; un échec bloque la suite et fait rejouer
les validations affectées. Cela n’impose ni une PR par composant ni un ordre
code/tests/documentation.

Pour Arclith, le [parcours de délégation](workflows/service-initialization.md)
utilise ses propres skills : ce catalogue ne réimplémente pas scaffold ou
blueprint. Les règles de [tests](references/testing.md) prévoient mocks pour les
nouveaux TU, suite métier isolée en CI et intégration sur infrastructure et
données dédiées. L’objectif de couverture reste 80 % minimum, 90 % visés.

Les [règles de livraison](references/delivery.md) limitent chaque PR à un sujet
cohérent et privilégient les plus petits incréments livrables pour faciliter le
suivi et le rollback. Le [changelog](CHANGELOG.md) distingue les changements non
publiés des versions effectivement livrées.

Le catalogue source doit rester accompagné de ses références. Le format
d’installation et le moteur d’agents restent à définir ; le diagnostic reste
optionnel et ses skills ne sont pas encore créés.

## Traçabilité

Le [journal des arbitrages](docs/skill-personalization-decisions.md) conserve
l’origine des décisions et pointe vers les sources historiques versionnées.
Les références maintenues sont autonomes : l’exécution des skills ne dépend pas
du dossier d’anciennes règles, destiné à disparaître.
