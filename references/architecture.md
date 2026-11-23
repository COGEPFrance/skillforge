# Frontières et réutilisation

Les instructions opérationnelles sont dans [`implement-lib`](../skills/dev/implement-lib/SKILL.md), [`implement-port`](../skills/dev/implement-port/SKILL.md), [`implement-usecase`](../skills/dev/implement-usecase/SKILL.md), [`implement-adapter`](../skills/dev/implement-adapter/SKILL.md), [`integrate-service-components`](../skills/dev/integrate-service-components/SKILL.md), [`review-architecture`](../skills/review/review-architecture/SKILL.md).

Consulter cette aide lorsqu’un changement touche les frontières de composants ou de services.

Dans le profil hexagonal retenu par le brief technique, suivre les dépendances vers les contrats et le domaine ; garder transport et stockage dans les adapters et assembler hors du métier. Pour les projets Python, Pydantic reste une dépendance assumée du domaine. Ne pas imposer ce découpage à un projet dont le brief retient une autre architecture.

Lorsqu’une frontière de service change, `review-architecture` examine responsabilité métier, propriétaire des données et autonomie de déploiement. Un accès direct aux données internes d’un autre service constitue un couplage à expliciter et corriger selon les contrats du projet. Cela ne justifie pas de découper un monolithe hors périmètre.

Pour la revue, présenter les dépendances réellement modifiées et justifier une abstraction par une responsabilité ou un consommateur concret. Une structure de dossiers seule ne prouve pas ces frontières.
