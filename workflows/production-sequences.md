# Parcours de production

Une invocation isolée s’arrête au résultat et au relais de son skill. Une demande
de tâche complète autorise la poursuite des étapes applicables du parcours dans
le périmètre demandé. Les artefacts précèdent leurs revues ; ni un relais ni un
verdict ne donnent d’autorisation de publication supplémentaire.

## Code d’abord

1. Pour un nouveau service dont le brief retient Arclith, terminer [service-initialization.md](service-initialization.md).
2. Définir la stratégie de tests pertinente sans rédiger prématurément toute la suite ; produire le code par composants et ses revues intermédiaires selon [feature-implementation.md](feature-implementation.md).
3. Exécuter les contrôles statiques et tests existants pendant le développement. Passer les revues de structure applicables.
4. Écrire et exécuter les nouveaux tests pertinents : unitaires, intégration, contrats, crash ou mesures de performance selon le risque. Faire `review-tests`.
5. Exécuter les revues finales de code, de tests et de risques sélectionnées selon [review-sequences.md](review-sequences.md), avec preuves comportementales. Réserver `review-documentation` et `review-delivery` aux étapes 6 et 7, après préparation de leurs artefacts. Une mesure manquante ne devient pas une garantie.
6. Produire ou actualiser la documentation validée, puis `review-documentation`.
7. Préparer les artefacts de livraison nécessaires, puis `review-delivery`, avant leur publication autorisée.

## Tests d’abord

Après validation du socle, définir les comportements, écrire les tests pertinents et faire une revue préliminaire de leur intention. Un échec attendu dû au code absent est une preuve de reproduction, pas un succès final. Un échec d’environnement ou un test défectueux bloque cette étape.

Implémenter ensuite les composants dans leur ordre, faire passer les tests et reprendre aux revues finales de tests et de risques. Documentation et livraison restent après validation. Tout défaut découvert renvoie à la [boucle de correction](correction-loop.md).
