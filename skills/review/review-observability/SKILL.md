---
name: review-observability
description: "Examiner les logs, métriques et traces réellement exploitables. Produire une revue spécialisée sans corriger les fichiers."
---

# review-observability

## Périmètre

Examiner les logs, métriques et traces réellement exploitables. Identifier les fichiers, contrats et preuves utiles ; ne pas élargir cette revue en audit général.

## Critères partagés

- [observability](../../../references/observability.md)

## Examen

1. Identifier la révision examinée et la phase demandée : préliminaire ou finale.
2. Suivre succès, échec, retry et reprise à travers les signaux disponibles et leur corrélation interservices.
3. Vérifier émission, exploitation, coût, cardinalité et données sensibles ; signaler un collecteur indisponible au lieu de certifier la chaîne.
4. Utiliser les contrôles pertinents disponibles, sans mutation de l’environnement réel. Relier les constats à un emplacement et un effet ; séparer faits et hypothèses.

## Restitution

Appliquer le [format de résultat](../../../workflows/review-result.md) : `PASS`, `FAIL` ou `BLOCKED`, preuves, limites et corrections attendues. Une preuve indispensable manquante ne vaut pas validation. Préciser les garanties reportées lors d’une revue préliminaire.

Ne pas corriger le code ni lancer le prochain agent. Le workflow décide du passage suivant et applique la [boucle de correction](../../../workflows/correction-loop.md).
