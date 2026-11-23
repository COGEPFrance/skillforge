---
name: review-messaging
description: "Examiner les contrats et garanties d’un flux asynchrone. Produire une revue spécialisée sans corriger les fichiers."
---

# review-messaging

## Périmètre

Examiner les contrats et garanties d’un flux asynchrone. Identifier les fichiers, contrats et preuves utiles ; ne pas élargir cette revue en audit général.

## Critères partagés

- [messaging](../../../references/messaging.md)
- [compatibility](../../../references/compatibility.md)

## Examen

1. Identifier la révision examinée et la phase demandée : préliminaire ou finale.
2. Suivre producteur, consommateur, contrat, acquittement, retries et échec définitif.
3. Examiner doublons, ordre utile et coexistence de versions ; transmettre les défauts de cohérence ou de reprise aux revues concernées sans en présumer le résultat.
4. Utiliser les contrôles pertinents disponibles, sans mutation de l’environnement réel. Relier les constats à un emplacement et un effet ; séparer faits et hypothèses.

## Restitution

Appliquer le [format de résultat](../../../workflows/review-result.md) : `PASS`, `FAIL` ou `BLOCKED`, preuves, limites et corrections attendues. Une preuve indispensable manquante ne vaut pas validation. Préciser les garanties reportées lors d’une revue préliminaire.

Ne pas corriger le code ni lancer le prochain agent. Le workflow décide du passage suivant et applique la [boucle de correction](../../../workflows/correction-loop.md).
