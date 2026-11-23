# Tests et preuves

- Choisir des tests qui vérifient les comportements et risques du changement, plutôt que reproduire son implémentation.
- Distinguer tests unitaires, intégration entre composants réels, contrats entre services et scénarios de crash ou de charge.
- Isoler les dépendances des tests unitaires ; utiliser une infrastructure de test adaptée pour les garanties qui dépendent d’un système réel.
- Cibler cas nominaux, erreurs et limites pertinentes, avec des assertions capables de détecter le défaut recherché.
- Exécuter les tests existants dès le développement ; ne pas attendre la phase de création de nouveaux tests.
- Conserver commandes, environnement et résultats observés ; un test non exécuté ou une dépendance absente ne vaut pas réussite.
- Les tests peuvent précéder le code. Dans ce cas, distinguer un échec attendu sur le comportement absent d’un test lui-même défectueux.

## Preuves attendues

Relier les scénarios aux comportements et risques. Pour les tests de crash et de charge, lire aussi les référentiels de résilience et de performance.
