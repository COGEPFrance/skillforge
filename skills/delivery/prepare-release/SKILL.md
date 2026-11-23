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

1. Identifier conventions de version, contenu depuis la dernière release et consommateurs affectés.
2. Préparer notes, version, dépendances et migrations nécessaires, sans annoncer de garanties non validées.
3. Préciser reprise et risques ; distinguer préparation de tag, publication du tag et publication de release.

## Résultat et passage de relais

Version et notes proposées, contenu et prérequis ; publication seulement si autorisée.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-delivery`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Respecter la phase et le périmètre du [parcours de production](../../../workflows/production-sequences.md). Ne pas enchaîner une publication ou une modification externe non autorisée.
