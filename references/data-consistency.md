# Effets durables et reprise

Les instructions opérationnelles sont dans [`implement-persistence`](../skills/dev/implement-persistence/SKILL.md), [`implement-usecase`](../skills/dev/implement-usecase/SKILL.md), [`implement-messaging`](../skills/dev/implement-messaging/SKILL.md), [`review-data-consistency`](../skills/review/review-data-consistency/SKILL.md).

Lire si concurrence, migration, plusieurs effets durables ou écriture suivie d’une publication sont concernés.

Tracer l’ordre réel des effets et les fenêtres de panne. Une transaction locale ne couvre pas implicitement un broker ou un service distant ; choisir la garantie selon le besoin sans imposer un pattern universel.

Pour la revue, examiner conflit, mise à jour partielle et reprise après chaque frontière pertinente ; vérifier les garanties réelles du stockage. Un rejeu doit maîtriser la perte et les duplications d’effets métier selon le contrat promis.

Lors d’une migration, distinguer rollback du code, données déjà transformées et effets externes irréversibles ; tenir compte des versions qui peuvent encore écrire. Une lecture sans effet durable n’exige pas ces mécanismes.
