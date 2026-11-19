# Référentiel commun de qualité

Ce document est le point d’entrée des règles retenues collectivement pour
Skillforge. Les règles détaillées sont portées par les références ci-dessous,
utilisées par les skills de production et de revue sans copie concurrente.

Les anciens fichiers Markdown à la racine ne sont pas intégrés à cette première
version. Leur contenu sera examiné progressivement. Le cadrage et la conception
ne sont pas des thèmes du catalogue ; la vérification de l’architecture et la
mise en place du socle font partie du développement et de sa revue.

## Références

| Sujet | Référence commune |
| --- | --- |
| Frontières hexagonales, microservices et réutilisation | [Architecture](architecture.md) |
| Scaffold, blueprint et validation avant implémentation | [Socle du service](service-foundation.md) |
| SRP, KISS, DRY, SOTA, typage et périmètre | [Qualité du code](code-quality.md) |
| Entités, invariants et mutations | [Modèles métier](domain-models.md) |
| Variations utiles, sources, validation et secrets | [Configuration](configuration.md) |
| Asynchronisme, contrats et acquittements | [Messages](messaging.md) |
| Transactions, concurrence, migrations et publications | [Cohérence des données](data-consistency.md) |
| Défaillances, état durable et reprise après crash | [Résilience](resilience.md) |
| Logs, métriques, traces et corrélation | [Observabilité](observability.md) |
| Objectifs, charge et mesures | [Performance](performance.md) |
| Autorisations, frontières et protection des secrets | [Sécurité](security.md) |
| Contrats et transitions entre versions | [Compatibilité](compatibility.md) |
| Scénarios, niveaux et preuves d’exécution | [Tests](testing.md) |
| Public, exactitude et comportement validé | [Documentation](documentation.md) |
| Commits, PR, releases, déploiements et reprise | [Livraison](delivery.md) |
| Arclith comme base du code, Pydantic et délégation | [Profil Python / Arclith](profiles/python-arclith.md) |

## Production et validation

Arclith est la base des services visés. Le [parcours d’initialisation](../workflows/service-initialization.md)
valide le socle avant la première fonctionnalité. L’[implémentation par composants](../workflows/feature-implementation.md)
sépare lib si nécessaire, entités, ports, use cases, adapters et assemblage.

Le [parcours de production](../workflows/production-sequences.md) distingue
première validation du code, tests, validation du comportement et des risques,
documentation, puis livraison. Les tests peuvent précéder le code et les tests
existants continuent à être exécutés pendant le développement.

Sécurité, performance et compatibilité sont prises en compte dès la production
et approfondies par des revues distinctes. Résilience et observabilité demandent
également des preuves applicatives, même si Arclith fournit les mécanismes.

Chaque revue décrit son périmètre et rend un [verdict avec preuves](../workflows/review-result.md).
Un échec ou un prérequis indispensable manquant bloque la suite. Les corrections
invalident les validations affectées selon la [boucle de reprise](../workflows/correction-loop.md).
Ces fichiers décrivent les méthodes ; ils ne constituent pas un moteur d’agents.
