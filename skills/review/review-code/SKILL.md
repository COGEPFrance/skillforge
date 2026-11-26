---
name: review-code
description: "Examiner la qualité locale du code modifié, sans remplacer les revues de risques spécialisées. Produire une revue spécialisée sans corriger les fichiers."
---

# review-code

## Périmètre

Examiner la qualité locale du code modifié, sans remplacer les revues de risques spécialisées. Identifier les fichiers, contrats et preuves utiles ; ne pas élargir cette revue en audit général.

## Critères partagés

Appliquer d’abord la [méthode commune de revue](../../../references/review-method.md)
pour cadrer le dépôt, les sources et la comparaison, même en invocation seule.

- [code-quality](../../../references/code-quality.md)

## Examen

1. Identifier la révision examinée et la phase demandée : préliminaire ou finale.
2. Examiner responsabilités, lisibilité, typage, erreurs et complexité utile au besoin.
3. Relier chaque demande de correction à un défaut concret ; distinguer refactoring nécessaire et dette indépendante.
4. Utiliser les contrôles pertinents disponibles, dans un environnement de test isolé et autorisé, sans mutation de la production. Relier les constats à un emplacement et un effet ; séparer faits et hypothèses.

## Contrôles ciblés

Vérifier les [suppressions de typage et erreurs](../../../references/code-quality.md#typage-python-et-contrôles), puis la complexité de chaque fonction touchée. Les repères 10 de complexité cyclomatique et deux niveaux d’imbrication déclenchent un examen, pas un FAIL autonome. Vérifier le format des fichiers touchés avec les outils/version configurés ; un slogan de qualité ou un nom long ne remplace pas un défaut concret.

## Restitution

Appliquer le [format de résultat](../../../workflows/review-result.md) : `PASS`, `FAIL` ou `BLOCKED`, preuves, limites et corrections attendues. Une preuve indispensable manquante ne vaut pas validation. Préciser les garanties reportées lors d’une revue préliminaire.

Ne pas corriger le code ni lancer le prochain agent. Le workflow décide du passage suivant et applique la [boucle de correction](../../../workflows/correction-loop.md).
