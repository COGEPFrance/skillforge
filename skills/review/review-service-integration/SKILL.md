---
name: review-service-integration
description: "Vérifier le point d’entrée réel, les composants injectés, leurs parcours et leur cycle de vie, y compris les échecs de démarrage. Produire une revue sans corriger les fichiers."
---

# review-service-integration

## Périmètre

Vérifier que les bons composants sont effectivement assemblés et réalisent le comportement attendu. Identifier révision, phase et périmètre changement ou projet ; pour un changement, distinguer ses conséquences de la dette indépendante. Respecter les choix et contrats du projet sans imposer l’hexagonal ou un framework.

## Critères partagés

Appliquer d’abord la [méthode commune de revue](../../../references/review-method.md)
pour cadrer le dépôt, les sources et la comparaison, même en invocation seule.

- [architecture](../../../references/architecture.md)
- [configuration](../../../references/configuration.md)
- [assemblage, parcours et preuves](../../../references/service-integration.md)
- Pour les signaux concernés : [observability](../../../references/observability.md), selon les capacités et exigences retenues par le projet.

## Examen

1. Partir du vrai point d’entrée, de sa factory ou du bootstrap. Identifier le graphe construit et utilisé, ses contrats et les variantes supportées ; comparer le montage des tests à celui du service.
2. Suivre les implémentations réellement injectées et les valeurs qui les sélectionnent. Repérer mauvaise instance, handler absent, composant inutilisé ou initialisation dépendante d’un ordre d’import implicite.
3. Exercer un parcours représentatif de l’entrée à son résultat et ses effets, avec les dépendances nécessaires disponibles en environnement isolé et autorisé. Ne pas déduire le comportement de la seule réussite du démarrage ou d’un montage manuel différent.
4. Examiner initialisation, partage, propriété et fermeture des ressources ; inclure arrêt normal et démarrage partiellement échoué. Vérifier l’état prêt s’il fait partie du contrat.
5. Examiner un échec pertinent, sa propagation et les capacités qui restent disponibles. Distinguer dépendance indispensable et capacité optionnelle ; ne pas masquer une garantie non vérifiée derrière un mock ou bloquer des garanties indépendantes par principe.

## Restitution

Appliquer le [format de résultat](../../../workflows/review-result.md) : `PASS`, `FAIL` ou `BLOCKED`, preuves, limites et corrections attendues. Une preuve indispensable manquante ne vaut pas validation. Préciser les garanties reportées lors d’une revue préliminaire.

Identifier le point d’entrée, les instances et modes suivis, les ressources et les preuves statiques, dynamiques ou simulées. Pour chaque défaut, relier le mauvais assemblage ou cycle de vie au scénario et à son effet. Réserver explicitement les garanties dont le fournisseur manque ; ne pas attribuer à cette revue une certification générale d’observabilité, résilience ou cohérence des données.

Ne pas corriger le code ni lancer le prochain agent. Le workflow décide du passage suivant et applique la [boucle de correction](../../../workflows/correction-loop.md).
