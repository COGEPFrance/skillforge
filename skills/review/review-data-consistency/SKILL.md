---
name: review-data-consistency
description: "Examiner la cohérence des effets durables et des publications. Produire une revue spécialisée sans corriger les fichiers."
---

# review-data-consistency

## Périmètre

Examiner la cohérence des effets durables et des publications. Identifier les fichiers, contrats et preuves utiles ; ne pas élargir cette revue en audit général.

## Critères partagés

- [data-consistency](../../../references/data-consistency.md)

## Examen

1. Identifier la révision examinée et la phase demandée : préliminaire ou finale.
2. Identifier transactions, concurrence, conversions et propriétaire des données modifiées.
3. Examiner les fenêtres entre effets durables, les garanties transactionnelles réelles, migrations et rejeu. Distinguer rollback du code, données transformées et effets irréversibles ; ne pas imposer un pattern de publication si une garantie plus simple suffit.
4. Utiliser les contrôles pertinents disponibles dans un environnement de test isolé et autorisé ; ne pas modifier la production ni les systèmes partagés hors du périmètre de la tâche. Relier les constats à un emplacement et un effet ; séparer faits et hypothèses.

## Restitution

Appliquer le [format de résultat](../../../workflows/review-result.md) : `PASS`, `FAIL` ou `BLOCKED`, preuves, limites et corrections attendues. Une preuve indispensable manquante ne vaut pas validation. Préciser les garanties reportées lors d’une revue préliminaire.

Ne pas corriger le code ni lancer le prochain agent. Le workflow décide du passage suivant et applique la [boucle de correction](../../../workflows/correction-loop.md).
