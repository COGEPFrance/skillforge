---
name: implement-adapter
description: "Implémenter un port à la frontière d’un transport, stockage ou service externe."
---

# implement-adapter

## Références

Même en invocation isolée, appliquer le [filtre transverse](../../../references/quality-criteria.md), puis consulter uniquement les détails pertinents ci-dessous.

- [architecture](../../../references/architecture.md)
- [compatibility](../../../references/compatibility.md)

## Exécution

1. Lire le port et les garanties attendues ; examiner les capacités du socle et des dépendances choisis par le projet avant de développer un équivalent.
2. Garder protocole, conversions de formats et erreurs techniques à la frontière ; restituer les erreurs prévues par le port sans déplacer la décision métier.
3. Valider les entrées non fiables et utiliser les privilèges nécessaires à cette intégration. Pour un appel distant, définir timeout et erreurs temporaires ou définitives ; ajouter des retries seulement si les effets peuvent être répétés sans danger.
4. Identifier les consommateurs touchés par un changement de format. Réserver les garanties dépendant du système réel à une vérification d’intégration adaptée.

## Résultat et passage de relais

Adapter conforme au port, conversions et erreurs ; vérifications d’intégration nécessaires.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-adapters`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Suivre le [parcours de production](../../../workflows/production-sequences.md). Exécuter les vérifications existantes pertinentes ; ne pas enchaîner automatiquement création des tests, documentation ou livraison hors de cette étape.
