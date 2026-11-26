---
name: review-ports
description: "Examiner la sémantique des contrats attendus par les consommateurs, au-delà des signatures et du choix d’interface. Produire une revue sans corriger les fichiers."
---

# review-ports

## Périmètre

Examiner la sémantique des contrats attendus par les consommateurs, au-delà des signatures et du choix d’interface.

## Critères partagés

- [architecture](../../../references/architecture.md)
- [domain-models](../../../references/domain-models.md)

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

1. Partir du besoin du consommateur et identifier les opérations effectivement nécessaires, sans imposer de port supplémentaire.
2. Vérifier entrées, résultats, absence, erreurs et effets promis. Préciser si nécessaire création ou remplacement, moment du succès, ordre, atomicité, idempotence et concurrence ; ne pas exiger ces garanties sans besoin.
3. Confronter ces promesses aux usages : une capacité supposée par le consommateur doit être définie au contrat. Une signature ou une annotation ne démontre pas une garantie sémantique.
   Lire le contrat dans l’ensemble de ses sources applicables : une garantie explicite dans la documentation du projet n’a pas à être répétée dans chaque docstring. Distinguer un silence local d’une contradiction effective. Une implémentation témoin construite pour violer le contrat documenté ne démontre pas un défaut du port ou d’un adapter absent.
4. Rechercher fuites de protocole, document de stockage ou adapter concret, sans rejeter des types ou contraintes réellement imposés par le besoin.
5. Utiliser les preuves et contrôles disponibles dans un environnement isolé et autorisé ; signaler un contrat incompatible ou une décision indispensable manquante, sans réécrire le port.

## Points ciblés Python

Contrôler le [choix ABC / Protocol](../../../references/architecture.md#contrats-python-et-dispatch) selon le besoin réel. Signaler les documents de stockage ou objets métier connus cachés derrière `dict`/`Any` ; ne pas interdire une table de correspondance réellement dynamique.

## Restitution

Appliquer le [format de résultat](../../../workflows/review-result.md) : `PASS`, `FAIL` ou `BLOCKED`, preuves, limites et corrections attendues. Une preuve indispensable manquante ne vaut pas validation. Préciser les garanties reportées lors d’une revue préliminaire.

Préciser les sources du contrat et distinguer faits et hypothèses. Pour chaque défaut, donner la promesse violée, le scénario, l’emplacement, la preuve, l’effet et le principe de correction ; séparer dette indépendante et suggestions.

Ne pas corriger le code ni lancer le prochain agent. Le workflow décide du passage suivant et applique la [boucle de correction](../../../workflows/correction-loop.md).
