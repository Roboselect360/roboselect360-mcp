# RoboSelect360 - Intelligence robots humanoïdes (MCP)

**Intelligence supply-chain et teardown pour 34 robots humanoïdes, disponible en serveur [MCP](https://modelcontextprotocol.io).**

RoboSelect360 est une plateforme d'analyse indépendante à six couches couvrant le marché des robots humanoïdes :

| Couche | Contenu |
|---|---|
| Commercial | Specs, prix, disponibilité, score de viabilité pour 34 robots |
| Semi-conducteurs | Teardown BOM au niveau puce + risque de dépendance géopolitique |
| Mécanique | Actionneurs, roulements, aimants - BOM + risque matières critiques |
| Logiciel | Stack, licences, juridiction, lock-in et risque d'export control |
| Législation | Due diligence CE / AI Act / Cyber Resilience Act *(en cours)* |
| Rapports | Rapports TCO côté acheteur, automatisés |

Connectez un client compatible MCP et interrogez le catalogue directement. **Claude Desktop est le seul chemin testé à ce jour** - voir [Clients supportés](#clients-supportés) plus bas.

---

## Démarrage rapide (offre gratuite)

**Aucune clé, aucun compte, aucune installation.** Vous collez une adresse dans votre client MCP.

```
https://mcp-free.roboselect360.com/mcp
```

**Claude Desktop ou claude.ai** - Paramètres, Connecteurs, Ajouter un connecteur personnalisé, collez l'adresse. Laissez les champs OAuth vides. Les neuf outils apparaissent aussitôt.

**Autres clients MCP** - même adresse, sans en-tête. La plupart passent par [`mcp-remote`](https://www.npmjs.com/package/mcp-remote) (nécessite [Node.js](https://nodejs.org)) :

```bash
npx -y mcp-remote https://mcp-free.roboselect360.com/mcp
```

Une clé `rbs_` gratuite reste nécessaire pour l'**API REST** (`api.roboselect360.com`, en-tête `X-API-Key`). Demandez-la sur [roboselect360.com/contact.html](https://roboselect360.com/contact.html). Elle fonctionne aussi sur le serveur MCP, où elle n'est plus requise.

Voir [QUICKSTART.md](./QUICKSTART.md) pour le pas à pas et [examples/](./examples/) pour des appels d'exemple.

---

### Clients supportés

**Claude Desktop est le seul client où la connexion aboutit à ce jour**, sous Windows et macOS.

Vérifié le 2026-08-13 : **Claude Desktop se connecte avec la seule adresse.** **Perplexity refuse** - il exige OAuth avec enregistrement automatique du client, que ce serveur n'offre pas encore. **ChatGPT** n'expose les connecteurs personnalisés qu'en mode développeur sur un plan payant, nous n'avons donc pas pu le tester.

Le serveur est du MCP standard en Streamable HTTP : tout client qui accepte un serveur distant sans authentification devrait fonctionner. Si vous y parvenez ailleurs, écrivez-nous à **contact@roboselect360.com** et nous le documenterons.

---

## Ce que donne l'offre gratuite

L'offre gratuite expose **9 outils PUBLIC** - le catalogue de robots, les specs et le statut système sur les trois couches de teardown :

- `*_list_robots` - liste des 34 robots
- `*_get_robot` - profil commercial complet d'un robot
- `*_get_system_status` - couverture et fraîcheur des données

(où `*` vaut `hardware_`, `mechanical_` ou `software_`).

**Le premium** débloque les couches profondes - teardowns BOM, profils de dépendance, analyse de risque géopolitique / matières critiques et comparaison inter-robots (**27 outils** sur les trois couches). Le premium s'ouvre sur demande : écrivez à **contact@roboselect360.com** ou rendez-vous sur [roboselect360.com](https://roboselect360.com). Pour le MCP, vous recevez des **identifiants d'accès (un identifiant et un secret)** pour l'endpoint premium - pas une clé `rbs_`. Si vous utilisez aussi l'API REST, une clé `rbs_` premium l'accompagne. Les deux canaux puisent dans un solde de crédits unique.

Si vous utilisiez déjà le connecteur gratuit, **retirez-le en installant le premium**. Les deux exposent les mêmes noms d'outils, et les faire coexister empêche votre client de savoir lequel appeler.

---

## Également disponible

- **API REST** - `https://api.roboselect360.com` (même `X-API-Key`)
- **Site & fiches techniques** - [roboselect360.com](https://roboselect360.com)

## Licence

Le code d'exemple de ce dépôt est publié sous [licence MIT](./LICENSE). Les données RoboSelect360, la méthodologie de scoring et les analyses de teardown sont propriétaires et **ne figurent pas** ici - elles sont servies via l'API.

---

*RoboSelect360 - intelligence indépendante sur les robots humanoïdes.*
