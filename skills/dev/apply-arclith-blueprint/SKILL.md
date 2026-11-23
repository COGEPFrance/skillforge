---
name: apply-arclith-blueprint
description: "Appliquer un blueprint Arclith existant à un squelette de service identifié."
---

# apply-arclith-blueprint

Le brief d’architecture technique doit retenir Arclith pour ce parcours. Pour ses opérations propres, utiliser les skills Arclith disponibles ou sa documentation correspondant aux versions du projet.

## Références

Même en invocation isolée, appliquer le [filtre transverse](../../../references/quality-criteria.md), puis consulter uniquement les détails pertinents ci-dessous.

- [service-foundation](../../../references/service-foundation.md)
- [profiles/python-arclith](../../../references/profiles/python-arclith.md)

## Exécution

1. Vérifier scaffold, blueprint existant et compatibilité des versions à partir des procédures Arclith disponibles.
2. Appliquer le blueprint demandé sans architecture de remplacement. Blueprint absent ou incompatible : bloquer ce parcours Arclith et préciser le prérequis manquant.
3. Vérifier structure, assemblage, configuration, démarrage et signaux de base ; enregistrer versions, blueprint, fichiers et commandes. Ne pas ajouter de fonctionnalité métier ni conclure sur les garanties futures du service.

## Résultat et passage de relais

Blueprint et versions identifiés, changements appliqués et preuves de vérification du socle.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-service-foundation`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Suivre le [parcours de production](../../../workflows/production-sequences.md). Exécuter les vérifications existantes pertinentes ; ne pas enchaîner automatiquement création des tests, documentation ou livraison hors de cette étape.
