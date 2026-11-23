---
name: review-lib
description: "Examiner la nécessité et le contrat d’un composant réutilisable ajouté ou modifié. Produire une revue spécialisée sans corriger les fichiers."
---

# review-lib

## Périmètre

Examiner la nécessité et le contrat d’un composant réutilisable ajouté ou modifié. Identifier les fichiers, contrats et preuves utiles ; ne pas élargir cette revue en audit général.

## Critères partagés

- [architecture](../../../references/architecture.md)
- [code-quality](../../../references/code-quality.md)
- [profiles/python-arclith](../../../references/profiles/python-arclith.md)

## Examen

1. Identifier la révision examinée et la phase demandée : préliminaire ou finale.
2. Vérifier la capacité manquante et les possibilités de réutilisation Arclith ou des dépendances.
3. Examiner cohésion, contrat, couplage et consommateurs réels ; détecter un paquet ou une abstraction créé sans besoin.
4. Utiliser les contrôles pertinents disponibles, sans mutation de l’environnement réel. Relier les constats à un emplacement et un effet ; séparer faits et hypothèses.

## Restitution

Appliquer le [format de résultat](../../../workflows/review-result.md) : `PASS`, `FAIL` ou `BLOCKED`, preuves, limites et corrections attendues. Une preuve indispensable manquante ne vaut pas validation. Préciser les garanties reportées lors d’une revue préliminaire.

Ne pas corriger le code ni lancer le prochain agent. Le workflow décide du passage suivant et applique la [boucle de correction](../../../workflows/correction-loop.md).
