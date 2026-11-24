---
name: review-security
description: "Examiner les risques de sécurité atteignables du changement. Produire une revue spécialisée sans corriger les fichiers."
---

# review-security

## Périmètre

Examiner les risques de sécurité atteignables du changement. Identifier les fichiers, contrats et preuves utiles ; ne pas élargir cette revue en audit général.

## Critères partagés

- [security](../../../references/security.md)

## Examen

1. Identifier la révision examinée et la phase demandée : préliminaire ou finale.
2. Examiner frontières de confiance, autorisations, entrées et opérations sensibles concernées.
3. Relier les défauts à un chemin et à un effet démontrables ; vérifier les refus et la non-exposition des secrets sans modifier la production.
4. Utiliser les contrôles pertinents disponibles, dans un environnement de test isolé et autorisé, sans mutation de la production. Relier les constats à un emplacement et un effet ; séparer faits et hypothèses.

## Restitution

Appliquer le [format de résultat](../../../workflows/review-result.md) : `PASS`, `FAIL` ou `BLOCKED`, preuves, limites et corrections attendues. Une preuve indispensable manquante ne vaut pas validation. Préciser les garanties reportées lors d’une revue préliminaire.

Ne pas corriger le code ni lancer le prochain agent. Le workflow décide du passage suivant et applique la [boucle de correction](../../../workflows/correction-loop.md).
