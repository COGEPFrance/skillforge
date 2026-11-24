---
name: review-delivery
description: "Examiner le contenu et les prérequis d’un commit, d’une PR, d’une release ou d’un déploiement. Produire une revue spécialisée sans corriger les fichiers."
---

# review-delivery

## Périmètre

Examiner le contenu et les prérequis d’un commit, d’une PR, d’une release ou d’un déploiement. Identifier les fichiers, contrats et preuves utiles ; ne pas élargir cette revue en audit général.

## Critères partagés

- [delivery](../../../references/delivery.md)
- [compatibility](../../../references/compatibility.md)

## Examen

1. Identifier la révision examinée et la phase demandée : préliminaire ou finale.
2. Identifier le type de livraison, la révision exacte, le périmètre et les validations préalables requises.
3. Examiner contenu, version, notes, configuration, migrations, ordre et reprise selon cet artefact ; ne pas publier pendant la revue.
4. Utiliser les contrôles pertinents disponibles, dans un environnement de test isolé et autorisé, sans mutation de la production. Relier les constats à un emplacement et un effet ; séparer faits et hypothèses.

## Contenu préparé

Vérifier les fichiers exacts à livrer et les contrôles applicables à cette révision, dont le formatage si pertinent. Contrôler un sujet cohérent par PR, le plus petit incrément livrable pertinent, ses dépendances et son rollback ou moyen de reprise. Vérifier le changelog : effets concrets, corrections, migrations/incompatibilités, PR et version ou statut non publié, sans avancement fictif. Une suggestion de modifier la CI, de publier une issue ou de migrer des tests ne vaut pas autorisation ; distinguer préparation et action effective.

## Restitution

Appliquer le [format de résultat](../../../workflows/review-result.md) : `PASS`, `FAIL` ou `BLOCKED`, preuves, limites et corrections attendues. Une preuve indispensable manquante ne vaut pas validation. Préciser les garanties reportées lors d’une revue préliminaire.

Ne pas corriger le code ni lancer le prochain agent. Le workflow décide du passage suivant et applique la [boucle de correction](../../../workflows/correction-loop.md).
