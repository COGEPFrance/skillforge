---
name: review-ports
description: "Examiner les contrats typés entre use cases et implémentations. Produire une revue spécialisée sans corriger les fichiers."
---

# review-ports

## Périmètre

Examiner les contrats typés entre use cases et implémentations. Identifier les fichiers, contrats et preuves utiles ; ne pas élargir cette revue en audit général.

## Critères partagés

- [architecture](../../../references/architecture.md)
- [domain-models](../../../references/domain-models.md)

## Examen

1. Identifier la révision examinée et la phase demandée : préliminaire ou finale.
2. Partir du besoin du consommateur et vérifier types, erreurs et garanties du port.
3. Rechercher fuites de protocole, stockage ou adapter concret ; vérifier que le contrat ne nécessite pas une capacité implicite absente.
4. Utiliser les contrôles pertinents disponibles, sans mutation de l’environnement réel. Relier les constats à un emplacement et un effet ; séparer faits et hypothèses.

## Restitution

Appliquer le [format de résultat](../../../workflows/review-result.md) : `PASS`, `FAIL` ou `BLOCKED`, preuves, limites et corrections attendues. Une preuve indispensable manquante ne vaut pas validation. Préciser les garanties reportées lors d’une revue préliminaire.

Ne pas corriger le code ni lancer le prochain agent. Le workflow décide du passage suivant et applique la [boucle de correction](../../../workflows/correction-loop.md).
