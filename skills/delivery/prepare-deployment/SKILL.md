---
name: prepare-deployment
description: "Préparer un déploiement avec ordre, configuration, migrations et moyens de reprise."
---

# prepare-deployment

## Références

Lire les sections pertinentes de ces références pour le changement ; elles portent les critères communs à la production et à la revue.

- [delivery](../../../references/delivery.md)
- [configuration](../../../references/configuration.md)
- [compatibility](../../../references/compatibility.md)
- [resilience](../../../references/resilience.md)

## Exécution

1. Identifier artefact ou révision exacts, environnement cible, dépendances et autorisations de la tâche.
2. Préparer ordre, configuration, migrations, signaux de vérification et critères de réussite ou d’arrêt ; distinguer rollback du code, réversibilité des données et effets externes irréversibles.
3. Transmettre le plan à `review-delivery`. Le plan seul ne déclenche pas le déploiement ; son exécution requiert `PASS`, prérequis effectifs et autorisation pour la cible.

## Résultat et passage de relais

Plan exécutable, prérequis, validations et stratégie de reprise.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-delivery`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Respecter la phase et le périmètre du [parcours de production](../../../workflows/production-sequences.md). Ne pas enchaîner une publication ou une modification externe non autorisée.
