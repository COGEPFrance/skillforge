# Cohérence des données

- Identifier les données possédées par le service, les invariants persistés et les frontières transactionnelles.
- Garder les représentations de stockage et les conversions dans les adapters, derrière des ports typés.
- Définir le comportement en cas de concurrence, mise à jour partielle ou conflit.
- Expliciter la cohérence entre écriture durable et publication d’un message. Choisir un mécanisme adapté au besoin et aux capacités disponibles plutôt qu’un pattern systématique.
- Prévoir les migrations et reprises nécessaires ; considérer le déploiement progressif et les données écrites par plusieurs versions.
- Distinguer retour arrière du code, réversibilité des données et effets externes irréversibles.

## Preuves attendues

Identifier les fenêtres de panne entre effets, les garanties transactionnelles réelles et les scénarios de reprise. Montrer comment un rejeu évite perte et duplication d’effets métier.
