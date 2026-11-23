---
name: review-service-foundation
description: "Examiner le socle d’un service avant la première fonctionnalité. Produire une revue spécialisée sans corriger les fichiers."
---

# review-service-foundation

## Périmètre

Examiner le socle d’un service avant la première fonctionnalité. Identifier les fichiers, contrats et preuves utiles ; ne pas élargir cette revue en audit général.

## Critères partagés

- [service-foundation](../../../references/service-foundation.md)
- [profiles/python-arclith](../../../references/profiles/python-arclith.md)

## Examen

1. Identifier la révision examinée et la phase demandée : préliminaire ou finale.
2. Comparer versions et blueprint au socle généré, sans lancer une nouvelle génération.
3. Vérifier assemblage, validation de configuration, démarrage et signaux réellement émis ; limiter le verdict à ce socle.
4. Utiliser les contrôles pertinents disponibles, sans mutation de l’environnement réel. Relier les constats à un emplacement et un effet ; séparer faits et hypothèses.

## Restitution

Appliquer le [format de résultat](../../../workflows/review-result.md) : `PASS`, `FAIL` ou `BLOCKED`, preuves, limites et corrections attendues. Une preuve indispensable manquante ne vaut pas validation. Préciser les garanties reportées lors d’une revue préliminaire.

Ne pas corriger le code ni lancer le prochain agent. Le workflow décide du passage suivant et applique la [boucle de correction](../../../workflows/correction-loop.md).
