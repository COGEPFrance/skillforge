---
name: measure-performance
description: "Mesurer un chemin critique sous une charge identifiée, pour un objectif ou une exploration."
---

# measure-performance

## Références

Lire les sections pertinentes de ces références pour le changement ; elles portent les critères communs à la production et à la revue.

- [performance](../../../references/performance.md)
- [testing](../../../references/testing.md)
- [observability](../../../references/observability.md)

## Exécution

1. Définir chemin critique, scénario, volumes et environnement isolé ; identifier l’objectif ou annoncer une mesure exploratoire qui ne pourra pas certifier un objectif.
2. Mesurer latence individuelle, débit, accumulation et ressources utiles avec jeu de données, versions et instrumentation identifiés ; observer saturation et dépendances.
3. Comparer à l’objectif s’il est défini et à une référence disponible dans des conditions comparables. Décrire bruit et limites ; l’asynchronisme seul ou un déplacement du goulot ne prouve pas un gain.

## Résultat et passage de relais

Protocole, résultats et comparaison aux objectifs, avec limites.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-performance`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Respecter la phase et le périmètre du [parcours de production](../../../workflows/production-sequences.md). Ne pas enchaîner une publication ou une modification externe non autorisée.
