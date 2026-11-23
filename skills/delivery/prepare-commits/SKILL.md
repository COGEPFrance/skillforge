---
name: prepare-commits
description: "Préparer des commits cohérents à partir du changement validé et de son périmètre."
---

# prepare-commits

## Références

Lire les sections pertinentes de ces références pour le changement ; elles portent les critères communs à la production et à la revue.

- [delivery](../../../references/delivery.md)
- [code-quality](../../../references/code-quality.md)

## Exécution

1. Examiner diff et état du dépôt ; isoler les fichiers de la tâche sans emporter les changements d’autrui.
2. Vérifier les validations requises et organiser le contenu et les messages selon les conventions du dépôt.
3. Distinguer contenu préparé et commit effectivement créé ; créer le commit uniquement si la demande l’autorise.

## Résultat et passage de relais

Contenu exact des commits proposés ou créés et vérifications.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-delivery`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Respecter la phase et le périmètre du [parcours de production](../../../workflows/production-sequences.md). Ne pas enchaîner une publication ou une modification externe non autorisée.
