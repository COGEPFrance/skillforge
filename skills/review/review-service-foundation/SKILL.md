---
name: review-service-foundation
description: "Examiner le socle d’un service avant la première fonctionnalité. Produire une revue spécialisée sans corriger les fichiers."
---

# review-service-foundation

Pour Arclith ou un autre framework, utiliser les preuves issues de ses skills propriétaires ; cette revue commune ne réimplémente pas leurs contrôles spécifiques.

## Périmètre

Examiner le socle d’un service avant la première fonctionnalité. Identifier les fichiers, contrats et preuves utiles ; ne pas élargir cette revue en audit général.

## Critères partagés

- [service-foundation](../../../references/service-foundation.md)
- [profiles/python-arclith](../../../references/profiles/python-arclith.md)

## Examen

1. Identifier la révision examinée et la phase demandée : préliminaire ou finale.
2. Comparer le socle au besoin, aux versions et aux choix retenus ; consulter les preuves du framework, dont le blueprint si applicable, sans relancer sa procédure propriétaire.
3. Vérifier assemblage, validation de configuration, démarrage et signaux réellement émis ; limiter le verdict à ce socle.
4. Utiliser les contrôles pertinents disponibles, dans un environnement de test isolé et autorisé, sans mutation de la production. Relier les constats à un emplacement et un effet ; séparer faits et hypothèses.

## Restitution

Appliquer le [format de résultat](../../../workflows/review-result.md) : `PASS`, `FAIL` ou `BLOCKED`, preuves, limites et corrections attendues. Une preuve indispensable manquante ne vaut pas validation. Préciser les garanties reportées lors d’une revue préliminaire.

Ne pas corriger le code ni lancer le prochain agent. Le workflow décide du passage suivant et applique la [boucle de correction](../../../workflows/correction-loop.md).
