# Référentiel commun de qualité

Ce document est le point d’entrée des règles retenues collectivement pour
Skillforge. Les règles détaillées sont portées par les références ci-dessous,
utilisées par les skills de production et de revue sans copie concurrente.

Les règles de `_rules/` ont été examinées pour cette personnalisation ; les arbitrages
sont consignés dans le [journal](../docs/skill-personalization-decisions.md).
Ces sources restent conservées pour traçabilité, pas chargées comme un ancien
prompt à exécuter en bloc. Le cadrage et la conception
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
| Profil conditionnel Python / Arclith et délégation | [Profil Python / Arclith](profiles/python-arclith.md) |

## Sélection des exigences en production

Partir du brief projet, du brief d’architecture technique et des conventions
établies. Une répétition locale ne justifie pas une pratique défectueuse ; corriger
la dette liée à la tâche sans refonte générale. Faire préciser une contradiction
ou valider une divergence structurante avant de l’engager, sans redemander les
décisions déjà prises. Pour Python, les classes de données structurées utilisent
Pydantic explicitement typé, avec une dépendance assumée dans le domaine.
Pour du Python modifié, appliquer aussi les [contrôles de typage et outils](code-quality.md#typage-python-et-contrôles) ; aucune suppression globale ne doit masquer les erreurs de production.

Chaque skill de développement commence par cette sélection, y compris lorsqu’il
est invoqué seul. Lire les critères de [sécurité](security.md) et examiner leur
application au changement : autorisations métier, frontières, privilèges et
secrets. Les intégrer pendant l’implémentation ; ne pas attendre la revue finale.

Parcourir le tableau ci-dessus pour identifier les autres exigences applicables,
notamment compatibilité, cohérence des données, résilience, observabilité et
performance, puis lire les sections pertinentes des références retenues.
Consigner les critères retenus, les exclusions qui demandent une explication
et les preuves disponibles ou manquantes pour la revue, sans matrice exhaustive
pour une modification locale. Cette sélection reste
limitée au changement demandé ; elle ne déclenche pas un audit général.

## Production et validation

Le brief technique indique si Arclith est retenu. Dans ce cas, utiliser ses skills
spécialisés et le [parcours d’initialisation](../workflows/service-initialization.md)
pour un nouveau service. Sinon, vérifier le socle choisi par le projet sans
imposer Arclith ni ce parcours. L’[implémentation par composants](../workflows/feature-implementation.md)
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
