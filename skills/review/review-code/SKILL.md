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
2. Examiner responsabilités, lisibilité, typage, erreurs et complexité utile au besoin.
3. Relier chaque demande de correction à un défaut concret ; distinguer refactoring nécessaire et dette indépendante.
4. Utiliser les contrôles pertinents disponibles, sans mutation de l’environnement réel. Relier les constats à un emplacement et un effet ; séparer faits et hypothèses.

## Restitution

Appliquer le [format de résultat](../../../workflows/review-result.md) : `PASS`, `FAIL` ou `BLOCKED`, preuves, limites et corrections attendues. Une preuve indispensable manquante ne vaut pas validation. Préciser les garanties reportées lors d’une revue préliminaire.

Ne pas corriger le code ni lancer le prochain agent. Le workflow décide du passage suivant et applique la [boucle de correction](../../../workflows/correction-loop.md).
