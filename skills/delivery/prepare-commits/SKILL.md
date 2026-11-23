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

1. Examiner état du dépôt et diff exact ; préserver les modifications d’autrui et sélectionner uniquement le contenu de la tâche.
2. Préparer des ensembles cohérents et leurs messages selon les conventions du dépôt ; joindre les validations du contenu exact à `review-delivery`.
3. Créer les commits seulement après `PASS` de cette revue et dans le périmètre autorisé. Si le contenu change, faire réexaminer les validations affectées avant la livraison.

## Résultat et passage de relais

Contenu exact des commits proposés ou créés et vérifications.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-delivery`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Respecter la phase et le périmètre du [parcours de production](../../../workflows/production-sequences.md). Ne pas enchaîner une publication ou une modification externe non autorisée.
