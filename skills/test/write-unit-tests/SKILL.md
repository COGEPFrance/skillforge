---
name: write-unit-tests
description: "Écrire des tests unitaires des comportements d’un composant isolé."
---

# write-unit-tests

## Références

Lire les sections pertinentes de ces références pour le changement ; elles portent les critères communs à la production et à la revue.

- [testing](../../../references/testing.md)

## Exécution

1. Identifier comportement public et défaut que les assertions doivent détecter ; consulter les tests existants sans recopier la structure interne du code.
2. Isoler les dépendances sans simuler la logique testée ; couvrir erreurs et limites pertinentes. Une garantie de transaction, de broker ou de protocole réel relève d’une intégration.
3. Exécuter avec les outils configurés, conserver commande et résultat. Vérifier que les assertions différencient le comportement incorrect sans imposer une campagne de mutations à chaque changement.

## Résultat et passage de relais

Tests unitaires, commande et résultats ; comportements couverts et limites.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-tests`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Respecter la phase et le périmètre du [parcours de production](../../../workflows/production-sequences.md). Ne pas enchaîner une publication ou une modification externe non autorisée.
