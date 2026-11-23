---
name: prepare-release
description: "Préparer la version et les artefacts de release d’un changement validé."
---

# prepare-release

## Références

Lire les sections pertinentes de ces références pour le changement ; elles portent les critères communs à la production et à la revue.

- [delivery](../../../references/delivery.md)
- [compatibility](../../../references/compatibility.md)

## Exécution

1. Identifier conventions de version du dépôt, contenu depuis la dernière release et consommateurs affectés.
2. Préparer version, notes, dépendances et migrations nécessaires ; expliciter transitions et risques de reprise sans garanties non validées.
3. Transmettre les artefacts préparés à `review-delivery`. Après `PASS` et autorisation, distinguer création du tag, publication du tag et release ; vérifier l’état distant avant et après les actions qui en dépendent.

## Résultat et passage de relais

Version et notes proposées, contenu et prérequis ; publication seulement si autorisée.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-delivery`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Respecter la phase et le périmètre du [parcours de production](../../../workflows/production-sequences.md). Ne pas enchaîner une publication ou une modification externe non autorisée.
