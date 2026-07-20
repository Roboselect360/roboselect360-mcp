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

1. **Obtenez une clé gratuite** sur [roboselect360.com/contact.html](https://roboselect360.com/contact.html) - section "Commencer gratuitement". Vous recevez une clé qui commence par `rbs_` (sans carte, aucun crédit consommé).
2. **Connectez** votre client - deux façons :

   **Claude Desktop (le plus rapide)** - téléchargez [`roboselect360-free.mcpb`](https://github.com/Roboselect360/roboselect360-mcp/releases/latest) depuis la dernière release, ouvrez-le, et collez votre clé quand elle est demandée. Aucun fichier de config à éditer.

   **Les autres clients MCP** (non testés, voir plus bas) - pointez-les vers le serveur :
   - Endpoint : `https://mcp-free.roboselect360.com/mcp`
   - Header : `X-API-Key: rbs_votre_cle_ici`

   Ces clients se connectent via [`mcp-remote`](https://www.npmjs.com/package/mcp-remote) (nécessite [Node.js](https://nodejs.org)) :

   ```bash
   npx -y mcp-remote https://mcp-free.roboselect360.com/mcp --header "X-API-Key: rbs_votre_cle_ici"
   ```

Voir [QUICKSTART.md](./QUICKSTART.md) pour les deux chemins pas à pas et [examples/](./examples/) pour des exemples d'appels.

### Clients supportés

**Claude Desktop est le seul client que nous ayons testé à ce jour**, sous Windows et macOS.

Le bundle `.mcpb` est un format d'extension Claude Desktop : ce chemin lui est donc propre. Le serveur, lui, est du MCP standard en Streamable HTTP, donc d'autres clients MCP peuvent fonctionner avec l'endpoint et le header ci-dessus - nous n'en avons vérifié aucun. Si vous y parvenez ailleurs, écrivez-nous à **contact@roboselect360.com** et nous le documenterons.

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
