---
name: review-resilience
description: "Examiner les défaillances, crashes et possibilités de reprise d’un traitement. Produire une revue spécialisée sans corriger les fichiers."
---

# review-resilience

## Périmètre

Examiner les défaillances, crashes et possibilités de reprise d’un traitement. Identifier les fichiers, contrats et preuves utiles ; ne pas élargir cette revue en audit général.

## Critères partagés

Appliquer d’abord la [méthode commune de revue](../../../references/review-method.md)
pour cadrer le dépôt, les sources et la comparaison, même en invocation seule.

- [resilience](../../../references/resilience.md)
- [data-consistency](../../../references/data-consistency.md)

## Examen

1. Identifier la révision examinée et la phase demandée : préliminaire ou finale.
2. Examiner limites, tentatives, erreurs définitives, état durable et points de reprise.
3. Vérifier les scénarios de crash avant et après effets, acquittements et redémarrage ; distinguer lecture du code et reprise effectivement testée.
4. Utiliser les contrôles pertinents disponibles, dans un environnement de test isolé et autorisé, sans mutation de la production. Relier les constats à un emplacement et un effet ; séparer faits et hypothèses.

## Réservations et effets durables

Si le traitement modifie unicité, verrous, réservations ou plusieurs documents,
examiner le [cycle de vie des réservations](../../../references/data-consistency.md#cycle-de-vie-des-réservations-et-de-lunicité)
et les [entrelacements concurrents](../../../references/data-consistency.md#entrelacements-concurrents).
Vérifier l’état après interruption et reprise, au-delà de la réponse retournée.

## Restitution

Appliquer le [format de résultat](../../../workflows/review-result.md) : `PASS`, `FAIL` ou `BLOCKED`, preuves, limites et corrections attendues. Une preuve indispensable manquante ne vaut pas validation. Préciser les garanties reportées lors d’une revue préliminaire.

Ne pas corriger le code ni lancer le prochain agent. Le workflow décide du passage suivant et applique la [boucle de correction](../../../workflows/correction-loop.md).
