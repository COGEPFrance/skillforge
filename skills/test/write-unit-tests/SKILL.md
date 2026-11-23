---
name: write-unit-tests
description: "Écrire des tests unitaires des comportements d’un composant isolé."
---

# write-unit-tests

## Références

Lire les sections pertinentes de ces références pour le changement ; elles portent les critères communs à la production et à la revue.

- [testing](../../../references/testing.md)

## Exécution

1. Identifier les comportements et tests existants ; conserver réel le composant testé et les données, entités, DTO et objets valeur manipulés.
2. Pour les nouveaux TU Python, utiliser `unittest.mock` pour les dépendances simulées, sans créer ni réutiliser de fakes : autospec contraint si l’interface le permet, `AsyncMock` pour les opérations asynchrones et injection avant `patch`. Lire les [détails mocks et fixtures](../../../references/testing.md#tests-unitaires-python) pour leur portée et leurs pièges.
3. Configurer seulement le scénario ; vérifier résultats, erreurs, effets et interactions contractuelles, sans tester une valeur préconfigurée du mock ou un ordre sans signification métier. Couvrir les refus et l’état inchangé après mise à jour invalide.
4. Exécuter les tests pertinents, dont la suite métier isolée si concernée, et conserver commandes, résultats et limites. Ne pas modifier la production pour adapter un double ; un défaut de production découvert se transmet au responsable du composant. Une migration de fakes n’est pas déclenchée par leur seule présence.

## Résultat et passage de relais

Tests unitaires, commande et résultats ; comportements couverts et limites.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-tests`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Respecter la phase et le périmètre du [parcours de production](../../../workflows/production-sequences.md). Ne pas enchaîner une publication ou une modification externe non autorisée.
