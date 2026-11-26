---
name: review-usecases
description: "Examiner l’orchestration et les effets d’un use case. Produire une revue spécialisée sans corriger les fichiers."
---

# review-usecases

## Périmètre

Examiner l’orchestration et les effets d’un use case. Identifier les fichiers, contrats et preuves utiles ; ne pas élargir cette revue en audit général.

## Critères partagés

Appliquer d’abord la [méthode commune de revue](../../../references/review-method.md)
pour cadrer le dépôt, les sources et la comparaison, même en invocation seule.

- [architecture](../../../references/architecture.md)
- [domain-models](../../../references/domain-models.md)
- [data-consistency](../../../references/data-consistency.md)

## Examen

1. Identifier la révision examinée et la phase demandée : préliminaire ou finale.
2. Suivre entrées, décisions, appels aux ports, résultat et erreurs de l’intention applicative.
3. Rechercher accès directs à l’infrastructure, invariants contournés et effets partiels incohérents ; rester sur ce use case.
4. Utiliser les contrôles pertinents disponibles, dans un environnement de test isolé et autorisé, sans mutation de la production. Relier les constats à un emplacement et un effet ; séparer faits et hypothèses.

## Points ciblés

Vérifier les contrats Pydantic pour Python, les autorisations au périmètre métier et leurs refus. Rechercher parsing de protocole, accès fichier/réseau et conversions de persistance dans l’orchestration. Une boucle simple ou plusieurs ports ne suffisent pas à imposer un nouveau service ; démontrer une responsabilité technique distincte.

Rechercher les [contrats et erreurs déjà produits dans le flux](../../../references/architecture.md#contrats-et-erreurs-existants)
avant de valider un nouveau mapping, DTO de transformation ou traitement d’erreur.

## Restitution

Appliquer le [format de résultat](../../../workflows/review-result.md) : `PASS`, `FAIL` ou `BLOCKED`, preuves, limites et corrections attendues. Une preuve indispensable manquante ne vaut pas validation. Préciser les garanties reportées lors d’une revue préliminaire.

Ne pas corriger le code ni lancer le prochain agent. Le workflow décide du passage suivant et applique la [boucle de correction](../../../workflows/correction-loop.md).
