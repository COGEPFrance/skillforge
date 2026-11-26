---
name: review-usecases
description: "Examiner si l’orchestration réalise l’intention métier, avec des décisions, refus et effets ordonnés conformément aux contrats. Produire une revue sans corriger les fichiers."
---

# review-usecases

## Périmètre

Examiner si l’orchestration réalise l’intention métier, avec des décisions, refus et effets ordonnés conformément aux contrats.

## Critères partagés

- [architecture](../../../references/architecture.md)
- [domain-models](../../../references/domain-models.md)
- [data-consistency](../../../references/data-consistency.md)

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

1. Reconstituer intention, préconditions, autorisations, résultats et refus attendus à partir du besoin et des contrats utilisés.
2. Suivre le scénario nominal puis les chemins de refus et d’échec : ordre des décisions et appels, invariants, état observable et résultat annoncé.
3. Vérifier qu’un refus intervient avant les effets qu’il doit empêcher ; qu’un échec nécessaire ne devient pas un succès ; et que les promesses des ports suffisent aux effets attendus.
4. Rechercher accès directs à l’infrastructure et décisions ou conversions techniques déplacées dans l’orchestration, selon l’architecture retenue. Ne pas imposer un nouveau service pour une boucle simple ou plusieurs ports.
5. Exercer les chemins utiles dans un environnement isolé et autorisé ; identifier les fenêtres d’effets partiels. Confier leur garantie transactionnelle détaillée à la revue de cohérence des données sans l’annoncer acquise ici.

## Points ciblés

Vérifier les contrats Pydantic pour Python, les autorisations au périmètre métier et leurs refus. Rechercher parsing de protocole, accès fichier/réseau et conversions de persistance dans l’orchestration. Une boucle simple ou plusieurs ports ne suffisent pas à imposer un nouveau service ; démontrer une responsabilité technique distincte.

## Restitution

Appliquer le [format de résultat](../../../workflows/review-result.md) : `PASS`, `FAIL` ou `BLOCKED`, preuves, limites et corrections attendues. Une preuve indispensable manquante ne vaut pas validation. Préciser les garanties reportées lors d’une revue préliminaire.

Préciser les sources du contrat et distinguer faits et hypothèses. Pour chaque défaut, donner la promesse violée, le scénario, l’emplacement, la preuve, l’effet et le principe de correction ; séparer dette indépendante et suggestions.

Ne pas corriger le code ni lancer le prochain agent. Le workflow décide du passage suivant et applique la [boucle de correction](../../../workflows/correction-loop.md).
