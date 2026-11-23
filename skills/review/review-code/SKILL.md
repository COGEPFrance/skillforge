---
name: review-code
description: "Examiner la qualité locale du code modifié, sans remplacer les revues de risques spécialisées. Produire une revue spécialisée sans corriger les fichiers."
---

# review-code

## Périmètre

Examiner la qualité locale du code modifié, sans remplacer les revues de risques spécialisées. Identifier les fichiers, contrats et preuves utiles ; ne pas élargir cette revue en audit général.

## Critères partagés

- [code-quality](../../../references/code-quality.md)

## Examen

1. Identifier la révision examinée et la phase demandée : préliminaire ou finale.
2. Examiner contrats typés, erreurs actionnables et complexité utile au besoin avec les outils configurés. SRP/KISS/DRY/SOTA seuls ne motivent pas un défaut : démontrer une responsabilité incohérente, un couplage ou une duplication de concept préjudiciable.
3. Relier chaque demande de correction à un défaut concret ; distinguer refactoring nécessaire et dette indépendante.
4. Utiliser les contrôles pertinents disponibles dans un environnement de test isolé et autorisé ; ne pas modifier la production ni les systèmes partagés hors du périmètre de la tâche. Relier les constats à un emplacement et un effet ; séparer faits et hypothèses.

## Restitution

Appliquer le [format de résultat](../../../workflows/review-result.md) : `PASS`, `FAIL` ou `BLOCKED`, preuves, limites et corrections attendues. Une preuve indispensable manquante ne vaut pas validation. Préciser les garanties reportées lors d’une revue préliminaire.

Ne pas corriger le code ni lancer le prochain agent. Le workflow décide du passage suivant et applique la [boucle de correction](../../../workflows/correction-loop.md).
