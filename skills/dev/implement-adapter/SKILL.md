---
name: implement-adapter
description: "Implémenter un port à la frontière d’un transport, stockage ou service externe."
---

# implement-adapter

## Références

Commencer par la [sélection des exigences communes](../../../references/quality-criteria.md#sélection-des-exigences-en-production), même pour une invocation isolée, puis lire les références spécialisées ci-dessous.

- [architecture](../../../references/architecture.md)
- [compatibility](../../../references/compatibility.md)
- [profiles/python-arclith](../../../references/profiles/python-arclith.md)

## Exécution

1. Lire le port et les garanties attendues ; réutiliser un adapter Arclith s’il répond au besoin.
2. Isoler protocole, conversions et erreurs techniques dans l’adapter sans y déplacer la décision métier.
3. Prévoir les défaillances de la dépendance et exposer les erreurs attendues au consommateur.

## Résultat et passage de relais

Adapter conforme au port, conversions et erreurs ; vérifications d’intégration nécessaires.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-adapters`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Suivre le [parcours de production](../../../workflows/production-sequences.md). Exécuter les vérifications existantes pertinentes ; ne pas enchaîner automatiquement création des tests, documentation ou livraison hors de cette étape.
