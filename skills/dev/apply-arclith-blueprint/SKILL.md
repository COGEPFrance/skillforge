---
name: apply-arclith-blueprint
description: "Appliquer un blueprint Arclith existant à un squelette de service identifié."
---

# apply-arclith-blueprint

## Références

Lire les sections pertinentes de ces références pour le changement ; elles portent les critères communs à la production et à la revue.

- [service-foundation](../../../references/service-foundation.md)
- [profiles/python-arclith](../../../references/profiles/python-arclith.md)

## Exécution

1. Vérifier que le scaffold est disponible et identifier le blueprint et ses prérequis.
2. Appliquer le blueprint compatible au travers des procédures Arclith disponibles ; ne pas concevoir un blueprint de remplacement si aucun ne convient.
3. Vérifier assemblage, configuration, démarrage et signaux de base sans implémenter de fonctionnalité métier.

## Résultat et passage de relais

Blueprint et versions identifiés, changements appliqués et preuves de vérification du socle.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-service-foundation`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Suivre le [parcours de production](../../../workflows/production-sequences.md). Exécuter les vérifications existantes pertinentes ; ne pas enchaîner automatiquement création des tests, documentation ou livraison hors de cette étape.
