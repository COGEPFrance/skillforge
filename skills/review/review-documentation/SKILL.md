---
name: review-documentation
description: "Examiner l’exactitude et l’utilité d’un document pour son public. Produire une revue spécialisée sans corriger les fichiers."
---

# review-documentation

## Périmètre

Examiner l’exactitude et l’utilité d’un document pour son public. Identifier les fichiers, contrats et preuves utiles ; ne pas élargir cette revue en audit général.

## Critères partagés

- [documentation](../../../references/documentation.md)

## Examen

1. Identifier la révision examinée et la phase demandée : préliminaire ou finale.
2. Comparer affirmations et exemples aux sources propriétaires. Si la documentation précède le code, examiner le contrat proposé et ses réserves explicites ; ne pas exiger de produire le code pour valider cette phase préliminaire. À la clôture, confronter le document au comportement vérifié.
3. Vérifier liens, commandes, prérequis et informations obsolètes ; distinguer proposition, exemple non exécuté et procédure vérifiée.
4. Utiliser les contrôles pertinents disponibles, dans un environnement de test isolé et autorisé, sans mutation de la production. Relier les constats à un emplacement et un effet ; séparer faits et hypothèses.

## Configuration et architecture

Comparer exemples et variables documentées aux déclarations et consommateurs réels, avec les mêmes valeurs par défaut. Après un changement d’architecture, rechercher les noms retirés et confronter les descriptions à la version finale, sans supprimer l’historique légitime.

## Restitution

Appliquer le [format de résultat](../../../workflows/review-result.md) : `PASS`, `FAIL` ou `BLOCKED`, preuves, limites et corrections attendues. Une preuve indispensable manquante ne vaut pas validation. Préciser les garanties reportées lors d’une revue préliminaire.

Ne pas corriger le code ni lancer le prochain agent. Le workflow décide du passage suivant et applique la [boucle de correction](../../../workflows/correction-loop.md).
