---
name: measure-performance
description: "Mesurer un chemin critique sous une charge et des objectifs identifiés."
---

# measure-performance

## Références

Lire les sections pertinentes de ces références pour le changement ; elles portent les critères communs à la production et à la revue.

- [performance](../../../references/performance.md)
- [testing](../../../references/testing.md)
- [observability](../../../references/observability.md)

## Exécution

1. Définir scénario, volumes, objectifs et environnement de mesure isolé.
2. Exécuter des mesures reproductibles avec instrumentation adaptée ; relever latence, débit et ressources pertinentes.
3. Comparer aux objectifs et à la référence disponible ; expliciter bruit, limites et saturation sans extrapolation non mesurée.

## Résultat et passage de relais

Protocole, résultats et comparaison aux objectifs, avec limites.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-performance`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Respecter la phase et le périmètre du [parcours de production](../../../workflows/production-sequences.md). Ne pas enchaîner une publication ou une modification externe non autorisée.
