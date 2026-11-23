---
name: define-test-strategy
description: "Définir les scénarios et niveaux de tests adaptés aux comportements et risques d’un changement."
---

# define-test-strategy

## Références

Lire les sections pertinentes de ces références pour le changement ; elles portent les critères communs à la production et à la revue.

- [testing](../../../references/testing.md)
- [resilience](../../../references/resilience.md)
- [compatibility](../../../references/compatibility.md)

## Exécution

1. Relier les comportements et risques du changement aux composants et contrats concernés ; consulter les tests existants.
2. Choisir les preuves utiles : unité pour la logique isolée, intégration pour les garanties du système réel, contrats pour les consommateurs identifiés. Ajouter crash ou charge seulement si les effets ou objectifs le justifient.
3. Définir scénarios nominaux, erreurs, limites, assertions et prérequis nécessaires. Dans un parcours tests d’abord, distinguer échec attendu du comportement absent, test défectueux et environnement indisponible.

## Résultat et passage de relais

Plan de tests ciblé avec scénarios, niveau, prérequis et critères de réussite.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-tests`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Respecter la phase et le périmètre du [parcours de production](../../../workflows/production-sequences.md). Ne pas enchaîner une publication ou une modification externe non autorisée.
