---
name: resolve-conflicts
description: "Résoudre les conflits Git d’une intégration autorisée en préservant les comportements des branches."
---

# resolve-conflicts

## Références

Lire les sections pertinentes de ces références pour le changement ; elles portent les critères communs à la production et à la revue.

- [delivery](../../../references/delivery.md)
- [compatibility](../../../references/compatibility.md)

## Exécution

1. Identifier opération, branches et intentions des modifications en conflit.
2. Résoudre par le comportement attendu, sans choisir mécaniquement un côté ni écraser des changements indépendants.
3. Vérifier le diff résultant, les contrats et les validations affectées ; ne pas réécrire un historique partagé sans autorisation.

## Résultat et passage de relais

Conflits résolus et preuves de cohérence ; état exact de l’intégration.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-delivery`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Respecter la phase et le périmètre du [parcours de production](../../../workflows/production-sequences.md). Ne pas enchaîner une publication ou une modification externe non autorisée.
