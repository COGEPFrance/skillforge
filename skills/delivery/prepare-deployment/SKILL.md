---
name: prepare-deployment
description: "Préparer un déploiement avec ordre, configuration, migrations et moyens de reprise."
---

# prepare-deployment

## Références

Lire les sections pertinentes de ces références pour le changement ; elles portent les critères communs à la production et à la revue.

- [delivery](../../../references/delivery.md)
- [configuration](../../../references/configuration.md)
- [compatibility](../../../references/compatibility.md)
- [resilience](../../../references/resilience.md)

## Exécution

1. Identifier artefact ou révision, environnement cible, dépendances et autorisations de la tâche.
2. Définir ordre, configuration, migrations, observabilité et critères de réussite ou d’arrêt.
3. Préparer retour arrière ou correction en distinguant code et données ; ne pas lancer un déploiement par simple préparation du plan.

## Résultat et passage de relais

Plan exécutable, prérequis, validations et stratégie de reprise.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-delivery`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Respecter la phase et le périmètre du [parcours de production](../../../workflows/production-sequences.md). Ne pas enchaîner une publication ou une modification externe non autorisée.
