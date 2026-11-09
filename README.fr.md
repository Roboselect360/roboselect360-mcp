# RoboSelect360 - Intelligence indépendante sur les robots humanoïdes (MCP)

**Intelligence indépendante sur les robots humanoïdes - capacités prouvées, coût réel, chaîne d'approvisionnement et nomenclatures - disponible en serveur [MCP](https://modelcontextprotocol.io).**

Les robots humanoïdes passent du laboratoire à l'usine, mais l'information qui permet de décider reste dispersée, invérifiable ou écrite par les constructeurs eux-mêmes. RoboSelect360 est un acteur indépendant de l'écosystème des robots humanoïdes : il aide les décideurs industriels, les acheteurs, les intégrateurs et les développeurs à passer de la démonstration au déploiement.

| Question | Ce que RoboSelect360 y répond |
|---|---|
| Que sait réellement faire ce robot ? | Capacités observées, chacune appuyée sur une source datée - échecs compris, jamais une promesse de constructeur prise pour une preuve |
| Que coûte-t-il vraiment ? | Specs, prix, disponibilité et score de viabilité ; TCO et ROI côté acheteur |
| Qu'y a-t-il dedans, et d'où ça vient ? | Nomenclatures semi-conducteurs, mécanique et logiciel, avec risque de dépendance d'approvisionnement et géopolitique |
| Que demande la réglementation ? | Alertes réglementaires selon le pays du site dans l'outil de préparation de pilote ; dossiers de readiness par pays (UE, France, Royaume-Uni, États-Unis, Chine, Inde) |

Connectez un client compatible MCP et interrogez les données directement - voir [Clients supportés](#clients-supportés) plus bas.

---

## Démarrage rapide (offre gratuite)

**Aucune clé, aucun compte, aucune installation.** Vous collez une adresse dans votre client MCP.

```
https://mcp.roboselect360.com/mcp
```

**Claude Desktop ou claude.ai** - Paramètres, Connecteurs, Ajouter un connecteur personnalisé, collez l'adresse. Laissez les champs OAuth vides. Les 32 outils apparaissent aussitôt : 11 répondent gratuitement, les autres indiquent quel robot acheter pour y accéder.

**Autres clients MCP** - même adresse, sans en-tête. Les clients sans écran de connecteur peuvent passer par [`mcp-remote`](https://www.npmjs.com/package/mcp-remote) (nécessite [Node.js](https://nodejs.org)) :

```bash
npx -y mcp-remote https://mcp.roboselect360.com/mcp
```

Une clé `rbs_` gratuite reste nécessaire pour l'**API REST** (`api.roboselect360.com`, en-tête `X-API-Key`). Demandez-la sur [roboselect360.com/contact.html](https://roboselect360.com/contact.html).

Voir [QUICKSTART.md](./QUICKSTART.md) pour le pas à pas et [examples/](./examples/) pour des appels d'exemple.

---

### Clients supportés

**Vérifié avec de vrais utilisateurs :** Claude (desktop et web) se connecte sans clé, sans compte et sans fichier de configuration : l'adresse complète du connecteur suffit. **ChatGPT** (connecteur personnalisé) et **Codex** (`codex mcp add roboselect --url https://mcp.roboselect360.com/mcp`) fonctionnent de la même façon sur l'accès gratuit, tout comme **Kimi**. L'adresse doit porter le chemin `/mcp` : le nom d'hôte seul renvoie 404.

Pour l'accès payant avec une clé `rbs_`, **Claude est le client vérifié** (clé dans l'en-tête `X-API-Key` du connecteur). Le passage de la clé depuis ChatGPT ou Codex n'est pas encore validé. **Perplexity** se connecte sur l'accès gratuit par OAuth (vérifié le 2026-10-18) : il ne reçoit que les données publiques, un robot acheté ne s'ouvre donc pas depuis Perplexity.

Le serveur est du MCP standard en Streamable HTTP : tout client qui accepte un serveur distant sans authentification devrait fonctionner. Si vous y parvenez ailleurs, écrivez-nous à **contact@roboselect360.com** et nous le documenterons.

---

## Ce que donne l'offre gratuite

Les 32 outils sont listés ; **11 répondent sans clé** - le catalogue de robots, les profils et le statut système sur les trois couches de teardown, plus le manifeste d'accès et l'outil de préparation de pilote :

- `*_list_robots` - le catalogue complet des robots
- `*_get_robot` - profil commercial complet d'un robot, avec les étiquettes de ses capacités observées (la force de la meilleure preuve par capacité)
- `*_get_system_status` - couverture et fraîcheur des données
- `get_access_manifest` - ce qui vous est ouvert, et comment ouvrir le reste
- `prepare_pilot` - la méthode G.R.O.U.N.D. : une fiche besoin pour un premier pilote de robot humanoïde, une question à la fois

(où `*` vaut `hardware_`, `mechanical_` ou `software_`).

**L'accès payant** débloque les couches profondes - nomenclatures détaillées, profils de dépendance, risque géopolitique et matières critiques, comparaison inter-robots, les capacités observées de chaque robot avec chaque observation datée, et son profil de support après-vente. Il se vend **par robot, 390 € HT**, sur [roboselect360.com/tarifs.html](https://roboselect360.com/tarifs.html), et ouvre toute l'analyse de ce robot. Vous recevez une clé `rbs_` : ajoutez-la en en-tête `X-API-Key` de votre connecteur, sur la même adresse. La même clé sert pour l'API REST.

Le **dossier de décision de pilote** (`build_pilot_decision_file`, la suite payante de `prepare_pilot`) s'ouvre par son propre droit d'accès, distinct de l'accès aux robots : à demander sur [roboselect360.com/preparer-un-pilote-robot.html](https://roboselect360.com/preparer-un-pilote-robot.html).

Les en-têtes d'un connecteur ne se saisissent qu'à sa création : pour ajouter votre clé, supprimez le connecteur gratuit et recréez-le avec l'en-tête. Gardez un seul connecteur RoboSelect360 - deux connecteurs exposent les mêmes noms d'outils et empêchent votre client de savoir lequel appeler.

---

## Également disponible

- **API REST** - `https://api.roboselect360.com` (même `X-API-Key`)
- **Site & fiches techniques** - [roboselect360.com](https://roboselect360.com)

## Licence

Le code d'exemple de ce dépôt est publié sous [licence MIT](./LICENSE). Les données RoboSelect360, la méthodologie de scoring et les analyses de teardown sont propriétaires et **ne figurent pas** ici - elles sont servies via l'API.

---

*RoboSelect360 - intelligence indépendante sur les robots humanoïdes.*
