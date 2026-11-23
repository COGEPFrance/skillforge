# Exigences communes et sélection par le changement

Le brief du projet définit le besoin et le brief d’architecture technique définit
le socle, les bibliothèques et les frontières retenus. Les skills ne remplacent
pas ces choix. Pour les projets Python, Pydantic est le choix commun pour les
entités et une dépendance assumée du domaine, avec ou sans Arclith.
Si un brief manque, utiliser les conventions établies et demander
uniquement les décisions indispensables qui ne peuvent pas en être déduites.
Si un brief contredit explicitement un choix commun comme Pydantic pour les
entités Python, signaler le conflit et demander l’arbitrage nécessaire ; ne pas
remplacer silencieusement le choix du projet ni engager une migration implicite.
Le [profil Python / Arclith](profiles/python-arclith.md) s’applique lorsque ce
socle est retenu ; ses procédures sont portées par les skills d’Arclith.

## Sélection des exigences en production

Même en invocation isolée, lire le [filtre de sécurité](security.md) et appliquer
ses contrôles aux chemins touchés. Ne pas reporter une autorisation ou la
protection d’un secret à la seule review.

Puis choisir les détails utiles selon les effets du changement :

| Déclencheur | Détail à consulter |
| --- | --- |
| Frontières, responsabilité ou réutilisation | [Architecture](architecture.md), [qualité locale](code-quality.md) |
| Création ou mutation d’un modèle | [Modèles métier](domain-models.md) |
| Option ou source de configuration | [Configuration](configuration.md) |
| Message ou consommateur asynchrone | [Messages](messaging.md) |
| Concurrence, effets durables ou migration | [Cohérence](data-consistency.md) ; [résilience](resilience.md) si interruption ou rejeu |
| Appel distant ou traitement relancé | [Résilience](resilience.md) |
| Signaux ou nouveau chemin opérationnel | [Observabilité](observability.md) |
| Contrat ou dépendance pouvant affecter un consommateur | [Compatibilité](compatibility.md) |
| Objectif de charge ou risque sur un chemin critique | [Performance](performance.md) |

Ne pas lire tout le référentiel ni imposer tous les mécanismes. À la restitution,
transmettre les risques retenus, les preuves et les limites qui changent la
suite ; motiver une exclusion lorsqu’un risque plausible a été écarté. Pas de
matrice d’exclusions exhaustive pour une modification locale.

## Production et validation

Les instructions se trouvent dans les skills qui produisent ou examinent le
composant ; les références gardent les détails conditionnels et les critères de
preuve. [Tests](testing.md), [documentation](documentation.md) et
[livraison](delivery.md) accompagnent leurs étapes respectives.

Suivre le [parcours de production](../workflows/production-sequences.md) et les
[revues sélectionnées](../workflows/review-sequences.md). Les contrôles sont
proportionnés au changement ; un prérequis indispensable manquant bloque la
garantie concernée et les étapes qui en dépendent. Dans un parcours séquentiel
sélectionné, `FAIL` ou `BLOCKED` arrête les étapes suivantes jusqu’à correction
ou révision explicite du parcours ; cela ne constitue pas un verdict sur tout
le projet. Les limites restent visibles.
Les corrections invalident les validations affectées selon la
[boucle de reprise](../workflows/correction-loop.md).

Les fichiers `_rules/` restent historiques et hors de cette personnalisation.
Les [arbitrages](../docs/skill-personalization-decisions.md) retracent le traitement
des règles de cette version ; ce journal n’est pas un référentiel à charger par
les agents consommateurs.
