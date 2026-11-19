---
name: prepare-pull-request
description: "Préparer une PR avec problème, comportement résultant, périmètre et preuves de validation."
---

# prepare-pull-request

## Références

Lire les sections pertinentes de ces références pour le changement ; elles portent les critères communs à la production et à la revue.

- [delivery](../../../references/delivery.md)
- [documentation](../../../references/documentation.md)

## Exécution

1. Vérifier branche source, cible, diff et état distant si accessible.
2. Décrire la modification finale pour un lecteur sans le contexte du chat, avec validations et limites matérielles.
3. Préparer titre et corps ; publier branche ou PR seulement si autorisé, puis vérifier le résultat distant.

## Résultat et passage de relais

Titre, description et branches ; lien si la PR a effectivement été ouverte.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-delivery`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Respecter la phase et le périmètre du [parcours de production](../../../workflows/production-sequences.md). Ne pas enchaîner une publication ou une modification externe non autorisée.
