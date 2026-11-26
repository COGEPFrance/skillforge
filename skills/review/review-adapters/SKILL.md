---
name: review-adapters
description: "Confronter le comportement technique réel aux garanties du contrat, y compris conversions, absences, erreurs et moment du succès. Produire une revue sans corriger les fichiers."
---

# review-adapters

## Périmètre

Confronter le comportement technique réel aux garanties du contrat, y compris conversions, absences, erreurs et moment du succès.

## Critères partagés

- [architecture](../../../references/architecture.md)
- [compatibility](../../../references/compatibility.md)

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

1. Identifier le contrat servi, ses consommateurs et les garanties pertinentes de la dépendance technique, en recherchant les preuves du projet et de la version utilisée.
2. Comparer résultats, conversions, valeurs absentes et erreurs réelles aux promesses du port. Vérifier les pertes d’information et les distinctions métier effacées.
3. Suivre le moment où le succès est annoncé : une mise en mémoire, un envoi ou un acquittement ne prouve pas à lui seul la garantie attendue. Examiner cycle de vie et libération des ressources lorsque pertinents.
4. Vérifier que l’adapter traduit la technique sans décider à la place du métier. Identifier les garanties de concurrence, atomicité ou reprise nécessaires au contrat, sans imposer un mécanisme systématique.
5. Utiliser les contrôles pertinents, sur dépendances réelles lorsqu’ils sont nécessaires et disponibles, en environnement isolé et autorisé. Un mock ne prouve pas une garantie du fournisseur ; réserver ou bloquer la garantie indispensable non vérifiable selon la phase.

## Restitution

Appliquer le [format de résultat](../../../workflows/review-result.md) : `PASS`, `FAIL` ou `BLOCKED`, preuves, limites et corrections attendues. Une preuve indispensable manquante ne vaut pas validation. Préciser les garanties reportées lors d’une revue préliminaire.

Préciser les sources du contrat et distinguer faits et hypothèses. Pour chaque défaut, donner la promesse violée, le scénario, l’emplacement, la preuve, l’effet et le principe de correction ; séparer dette indépendante et suggestions.

Ne pas corriger le code ni lancer le prochain agent. Le workflow décide du passage suivant et applique la [boucle de correction](../../../workflows/correction-loop.md).
