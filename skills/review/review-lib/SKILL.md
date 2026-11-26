---
name: review-lib
description: "Examiner la nécessité et le contrat d’un composant réutilisable ajouté ou modifié. Produire une revue spécialisée sans corriger les fichiers."
---

# review-lib

## Périmètre

Examiner la nécessité et le contrat d’un composant réutilisable ajouté ou modifié. Identifier les fichiers, contrats et preuves utiles ; ne pas élargir cette revue en audit général.

## Critères partagés

Appliquer d’abord la [méthode commune de revue](../../../references/review-method.md)
pour cadrer le dépôt, les sources et la comparaison, même en invocation seule.

- [architecture](../../../references/architecture.md)
- [code-quality](../../../references/code-quality.md)
- Si le brief retient Arclith : [profil et délégation](../../../references/profiles/python-arclith.md)

## Examen

1. Identifier la révision examinée et la phase demandée : préliminaire ou finale.
2. Vérifier la capacité manquante et les possibilités de réutilisation du socle, de la bibliothèque standard et des dépendances retenus.
3. Examiner cohésion, contrat, couplage et consommateurs réels ; détecter un paquet ou une abstraction créé sans besoin.
4. Utiliser les contrôles pertinents disponibles, dans un environnement de test isolé et autorisé, sans mutation de la production. Relier les constats à un emplacement et un effet ; séparer faits et hypothèses.

## Contrôles ciblés

Justifier abstraction, héritage ou mixin par un contrat et des consommateurs réels. Pour un [dispatch](../../../references/architecture.md#contrats-python-et-dispatch), vérifier typage, initialisation explicite, rejet des types inconnus et couverture des configurations supportées. Ne pas imposer un registre à une famille petite et stable.

## Restitution

Appliquer le [format de résultat](../../../workflows/review-result.md) : `PASS`, `FAIL` ou `BLOCKED`, preuves, limites et corrections attendues. Une preuve indispensable manquante ne vaut pas validation. Préciser les garanties reportées lors d’une revue préliminaire.

Ne pas corriger le code ni lancer le prochain agent. Le workflow décide du passage suivant et applique la [boucle de correction](../../../workflows/correction-loop.md).
