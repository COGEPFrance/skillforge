# Assemblage et parcours effectif

## Graphe réellement utilisé

Partir du point d’entrée du service et de sa factory ou de son bootstrap réel,
selon le projet et le framework retenus. Identifier instances, configuration,
implémentations injectées, registres ou handlers et durée de vie. Vérifier les
variantes supportées pertinentes, pas seulement le défaut. Un composant présent
dans le dépôt, construit mais inutilisé ou utilisé uniquement dans un test ne
prouve pas son intégration au parcours du service.

Un test qui assemble lui-même les bons composants peut contourner un défaut du
bootstrap ; confronter sa construction au point d’entrée réellement livré.
Pour Arclith, utiliser les mécanismes et preuves propriétaires adaptés à la
version retenue, sans les réimplémenter ici.

## Parcours et cycle de vie

Suivre une entrée représentative, son traitement, les appels aux dépendances,
le résultat et l’effet attendu. Le démarrage d’un processus ne démontre pas une
fonctionnalité opérationnelle. Choisir aussi un échec pertinent pour vérifier
propagation, absence de faux succès et état observable, sans certifier toute la
résilience ou la cohérence transactionnelle.

Examiner ordre d’initialisation, partage des instances, ouverture et fermeture
des ressources, arrêt normal et nettoyage après démarrage partiellement échoué.
Respecter la propriété des ressources : ne pas exiger de fermer une ressource
que le contrat confie à l’appelant. Si le service annonce son état prêt, vérifier
qu’il correspond aux capacités effectivement disponibles selon son contrat.

## Preuves et limites

Employer les dépendances réelles lorsque leur comportement est indispensable à
la garantie examinée et qu’un environnement de test autorisé est disponible.
Les mocks peuvent démontrer sélection, transmission ou ordre des appels ; ils
ne certifient pas le comportement du fournisseur. Ne pas tester sur une
infrastructure de production ni contacter un service externe hors autorisation.

Une dépendance indispensable indisponible bloque la garantie qui en dépend ;
ne pas certifier le parcours final avec un assemblage fictif. Distinguer ces
garanties des éléments indépendants déjà vérifiables et de la phase préliminaire.
Une capacité optionnelle absente ne bloque pas automatiquement un parcours
fonctionnel démontré, si le contrat autorise son absence.

L’architecture vérifie les responsabilités et dépendances attendues ; la
configuration vérifie les valeurs ; cette revue vérifie leur assemblage effectif.
La review du socle couvre l’initialisation avant fonctionnalité. Observabilité,
résilience et cohérence des données approfondissent leurs garanties : vérifier
les branchements et signaux pertinents ici, sans annoncer leur validation globale.
