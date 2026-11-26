---
name: review-lib
description: "Examiner l’utilité et les garanties d’un composant partagé, de sa fonction à son API, sans imposer une abstraction supplémentaire. Produire une revue sans corriger les fichiers."
---

# review-lib

## Périmètre

Examiner l’utilité et les garanties d’un composant partagé, de sa fonction à son API, sans imposer une abstraction supplémentaire.

## Critères partagés

- [architecture](../../../references/architecture.md)
- [code-quality](../../../references/code-quality.md)
- Si le brief retient Arclith : [profil et délégation](../../../references/profiles/python-arclith.md)

## Cadrage du contrat

Identifier le besoin, les consommateurs et les sources applicables : instructions,
brief, documentation des contrats, décisions et usages existants. Distinguer
promesses explicites, comportement observé et hypothèses ; une implémentation
existante ne suffit pas à définir le comportement attendu.

Préciser révision, phase et périmètre : changement ou projet. Pour un changement,
lire les dépendances utiles mais séparer la dette indépendante des défauts qui
bloquent ce changement ; pour une revue globale, inclure les défauts existants
du périmètre annoncé. L’absence de documentation ne bloque pas automatiquement.
Une décision indispensable non déterminable produit `BLOCKED`, avec le besoin
d’arbitrage ; un défaut démontré produit `FAIL`. Ne pas créer une couche ou un
composant pour satisfaire le parcours.

## Examen

1. Identifier la capacité attendue et examiner la réutilisation du socle, de la bibliothèque standard et des dépendances déjà retenues.
2. Comparer le contrat à ses consommateurs : entrées, résultats, erreurs, effets secondaires, état partagé et cycle de vie pertinents.
3. Suivre un usage réel et les cas limites ou échecs qui peuvent contredire une promesse ; vérifier que le composant ne perd pas d’information ou ne masque pas un échec en succès.
4. Justifier cohésion et dépendances par le besoin : un consommateur peut suffire, plusieurs consommateurs ne prouvent pas une bonne abstraction. Accepter une fonction simple sans exiger paquet, classe ou interface.
5. Utiliser les contrôles disponibles dans un environnement isolé et autorisé ; relier les défauts au contrat et à leurs conséquences.

## Contrôles ciblés

Justifier abstraction, héritage ou mixin par un contrat et des consommateurs réels. Pour un [dispatch](../../../references/architecture.md#contrats-python-et-dispatch), vérifier typage, initialisation explicite, rejet des types inconnus et couverture des configurations supportées. Ne pas imposer un registre à une famille petite et stable.

## Restitution

Appliquer le [format de résultat](../../../workflows/review-result.md) : `PASS`, `FAIL` ou `BLOCKED`, preuves, limites et corrections attendues. Une preuve indispensable manquante ne vaut pas validation. Préciser les garanties reportées lors d’une revue préliminaire.

Préciser les sources du contrat et distinguer faits et hypothèses. Pour chaque défaut, donner la promesse violée, le scénario, l’emplacement, la preuve, l’effet et le principe de correction ; séparer dette indépendante et suggestions.

Ne pas corriger le code ni lancer le prochain agent. Le workflow décide du passage suivant et applique la [boucle de correction](../../../workflows/correction-loop.md).
