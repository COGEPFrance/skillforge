---
name: review-data-consistency
description: "Examiner la cohérence des effets durables et des publications. Produire une revue spécialisée sans corriger les fichiers."
---

# review-data-consistency

## Périmètre

Examiner la cohérence des effets durables et des publications. Identifier les fichiers, contrats et preuves utiles ; ne pas élargir cette revue en audit général.

## Critères partagés

Appliquer d’abord la [méthode commune de revue](../../../references/review-method.md)
pour cadrer le dépôt, les sources et la comparaison, même en invocation seule.

- [data-consistency](../../../references/data-consistency.md)

## Examen

1. Identifier la révision examinée et la phase demandée : préliminaire ou finale.
2. Identifier transactions, concurrence, conversions et propriétaire des données modifiées.
3. Examiner coupures entre écritures et messages, migrations et rejeu ; demander les preuves des garanties annoncées.
4. Utiliser les contrôles pertinents disponibles, dans un environnement de test isolé et autorisé, sans mutation de la production. Relier les constats à un emplacement et un effet ; séparer faits et hypothèses.

## Contrôles ciblés

- Pour un garde historique, comparer son prédicat à l’[identité métier exacte](../../../references/data-consistency.md#identité-métier-et-historique).
- Pour unicité, réservations ou écritures multiples, parcourir le [cycle de vie applicable](../../../references/data-consistency.md#cycle-de-vie-des-réservations-et-de-lunicité), y compris refus, échecs et nettoyage.
- Examiner les [entrelacements concurrents](../../../references/data-consistency.md#entrelacements-concurrents) et les preuves de l’état durable complet après la fin de toutes les opérations.

## Restitution

Appliquer le [format de résultat](../../../workflows/review-result.md) : `PASS`, `FAIL` ou `BLOCKED`, preuves, limites et corrections attendues. Une preuve indispensable manquante ne vaut pas validation. Préciser les garanties reportées lors d’une revue préliminaire.

Ne pas corriger le code ni lancer le prochain agent. Le workflow décide du passage suivant et applique la [boucle de correction](../../../workflows/correction-loop.md).
