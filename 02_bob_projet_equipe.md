# Ouvrir Bob et travailler en équipe
> Fiche 02 · Hackathon IA for Impact 2026

📚 **Documentation Bob** : [Quickstart — Set up your workspace](https://bob.ibm.com/docs/ide/getting-started/quickstart) · [Start a project with `/init` and `AGENTS.md`](https://bob.ibm.com/docs/ide/getting-started/tutorials/start-a-project)

---

## 1. Ouvrir le projet dans Bob

Sur macOS ou Windows :

1. Lancer l'application IBM Bob et se connecter avec son IBMid.
2. Ouvrir l'explorateur de fichiers de Bob.
3. Pour un dépôt existant, choisir **Clone Repository**, coller l'URL Git, choisir le dossier local, puis cliquer sur **Open** lorsque Bob le propose.
4. Pour un projet déjà présent sur l'ordinateur, ouvrir son dossier comme workspace depuis l'explorateur de Bob.
5. Si Bob demande si les fichiers sont fiables, vérifier le dépôt puis choisir **Yes, I trust the authors**.
6. Vérifier que le dépôt, notamment `Défis/`, apparaît dans l'explorateur de fichiers.

Le panneau de chat Bob peut être ouvert avec `Option + Command + B` sur Mac ou `Ctrl + Alt + B` sur Windows. 📚 [Quickstart Bob](https://bob.ibm.com/docs/ide/getting-started/quickstart)

> Un workspace doit être ouvert avant d'utiliser Bob sur le projet ; sinon les fonctions liées au projet peuvent être indisponibles. 📚 [Bob Shell — no workspace folder open](https://bob.ibm.com/docs/shell/troubleshooting/troubleshoot)

## 2. Préparer les documents du défi

Avant l'analyse, placer dans le dossier `Défis/` les supports remis par l'organisation ou les sponsors. Conserver les fichiers dans leur format d'origine et utiliser un nom explicite. Ce dossier devient la source locale de travail de l'équipe.

## 3. Le problème sans cette fiche

Sans configuration partagée, chaque membre de l'équipe Bob :
- Reçoit des réponses dans des styles différents
- Doit réexpliquer le contexte du projet à chaque nouvelle conversation
- Génère du code avec des conventions différentes (nommage, langue, structure)
- Ne bénéficie pas du travail de configuration fait par les autres membres

**La solution :** un dossier `.bob/` commité dans le dépôt Git du projet. Tout le monde le clone, tout le monde bénéficie des mêmes règles automatiquement.

---

## Architecture des fichiers Bob d'un projet

```
mon-projet/
├── AGENTS.md                        ← Contexte global projet (lu par Bob en permanence)
├── .bob/
│   ├── rules/
│   │   ├── 01_stack.md              ← Stack technique, conventions de code
│   │   ├── 02_langue.md             ← Langue de réponse, ton, format
│   │   └── 03_equipe.md             ← Rôles, périmètres, conventions Git
│   ├── rules-agent/
│   │   └── agent_rules.md           ← Règles spécifiques au mode Agent
│   ├── rules-plan/
│   │   └── plan_rules.md            ← Règles spécifiques au mode Plan
│   └── mcp.json                     ← Serveurs MCP partagés (ex : Tavily web search)
└── ... (votre code)
```

> Tout ce qui est dans `.bob/` est **versionné avec Git**. Un `git clone` suffit pour que Bob soit configuré identiquement pour tous les membres.

---

## 4. Générer le contexte projet avec `/init`

La commande `/init` est **la première chose à faire** une fois le dépôt créé.

### Comment ça marche

1. Ouvrir Bob (mode **Agent** ou **Code**)
2. Taper `/init` dans le chat
3. Bob scanne les fichiers du projet et génère automatiquement :
   - `AGENTS.md` à la racine — résumé de la structure, stack, conventions détectées
   - `.bob/rules-agent/AGENTS-agent.md` — contexte pour le mode Agent
   - `.bob/rules-plan/AGENTS-plan.md` — contexte pour le mode Plan
   - `.bob/rules-ask/AGENTS-ask.md` — contexte pour le mode Ask

### Ce que `AGENTS.md` contient typiquement

```
# Mon Projet — Contexte Bob

## Stack
- Backend : Python / FastAPI
- Frontend : React + TypeScript
- IA : OpenAI API (gpt-4o)
- Base de données : PostgreSQL

## Structure
- /backend — API REST
- /frontend — Interface React
- /data — Jeux de données et scripts de traitement

## Conventions
- Langue du code : anglais (variables, fonctions, commentaires)
- Langue des réponses Bob : français
- Tests : pytest pour le back, Vitest pour le front
- Commits : format conventionnel (feat:, fix:, docs:...)
```

### Quand relancer `/init`

- Après avoir ajouté un module majeur
- Après un changement de stack
- Si Bob ne semble plus comprendre la structure du projet

> `/init` ne coûte **pas de BobCoin** — c'est une commande de configuration, pas une génération de contenu.

---

## 5. Créer les règles d'équipe dans `.bob/rules/`

Les rules sont des fichiers Markdown lus automatiquement par Bob à **chaque conversation**, dans **tous les modes**.

### Règle de priorité

```
~/.bob/rules/          ← règles globales personnelles (sur votre machine)
    ↓ (surchargées par)
.bob/rules/            ← règles projet partagées (dans le dépôt Git)
```

Les règles projet ont la priorité. Elles s'appliquent à tous les membres de l'équipe.

---

### Exemple de fichier `.bob/rules/01_stack.md`

```
# Stack & Conventions de code

## Stack technique
- Backend : Python 3.12 / FastAPI
- Frontend : React 18 + TypeScript 5
- IA : appels à l'API OpenAI (modèle : gpt-4o-mini pour économiser)
- Base de données : SQLite en dev, PostgreSQL en prod

## Conventions de code
- Nommage : snake_case pour Python, camelCase pour TypeScript
- Toutes les fonctions ont une docstring courte (1 ligne)
- Pas de `any` en TypeScript — typage explicite obligatoire
- Les constantes sont en UPPER_CASE

## Ce qu'on n'utilise PAS
- Pas de classes en Python sauf si nécessaire (préférer les fonctions)
- Pas de bibliothèques front supplémentaires sans accord de l'équipe
- Pas de `console.log` en prod — utiliser le logger configuré
```

---

### Exemple de fichier `.bob/rules/02_langue.md`

```
# Langue et format des réponses

- Répondre toujours en français
- Réponses concises : aller droit au but, éviter les introductions creuses
- Le code généré est commenté en anglais (cohérence avec les conventions)
- Format préféré : listes à puces pour les explications, blocs de code pour le code
- Toujours indiquer le nom du fichier concerné avant un bloc de code
```

---

### Exemple de fichier `.bob/rules/03_equipe.md`

```
# Organisation de l'équipe

## Rôles
- @alice : Lead Dev Backend (Python/FastAPI)
- @bob-dev : Dev IA/Data (pipelines, modèles)
- @carol : UI/UX + Frontend (React)
- @david : PM / Pitcher (pas de code — slides, démo, pitch)

## Conventions Git
- Branche principale : main (protégée)
- Format des branches : feat/nom-feature, fix/nom-bug
- Commits : "feat: description", "fix: description", "docs: description"
- Pas de push direct sur main — Pull Request obligatoire

## Périmètres
- Alice et Bob-dev ne touchent pas au dossier /frontend sans prévenir Carol
- Carol ne touche pas aux fichiers /backend/api sans prévenir Alice
- David prépare /docs et /pitch — personne d'autre ne modifie ces dossiers
```

---

## 6. Règles spécifiques par mode

Certaines règles ne s'appliquent qu'à un mode précis.

### `.bob/rules-agent/agent_rules.md` — Mode Agent (génération de code)

```
# Règles Agent

- Toujours produire le changement minimal qui résout le problème
- Ne pas refactoriser du code non lié à la tâche
- Indiquer les fichiers modifiés en début de réponse
- Après chaque modification, résumer en 1 phrase ce qui a changé et pourquoi
- Ne pas ajouter de gestion d'erreur pour des cas impossibles
```

### `.bob/rules-plan/plan_rules.md` — Mode Plan (architecture, conception)

```
# Règles Plan

- Toujours proposer 2-3 options avant de recommander
- Inclure les compromis (trade-offs) pour chaque option
- Format de sortie : titres H2, listes à puces, tableau comparatif si pertinent
- Penser "démo hackathon" : préférer la simplicité à l'élégance
```

---

## 7. Partager la configuration du projet

Le fichier `.bob/mcp.json` configure les serveurs MCP (outils externes : recherche web, APIs…) **au niveau projet**, partagés avec toute l'équipe.

```
{
  "mcpServers": {
    "fetch": {
      "command": "uvx",
      "args": ["mcp-server-fetch"]
    }
  }
}
```

> Voir la fiche `03_bob_mcp_web.md` pour la configuration complète du MCP de recherche web.

---

## 8. Partager le résultat de `/init` avec l'équipe

Le résultat de `/init` est partagé comme des fichiers du dépôt, pas comme une conversation Bob.

1. Le membre qui ouvre le projet lance `/init` dans le chat Bob en **Code mode**.
2. Bob génère `AGENTS.md` à la racine et les fichiers de contexte dans `.bob/`. 📚 [Start a project with `/init` and `AGENTS.md`](https://bob.ibm.com/docs/ide/getting-started/tutorials/start-a-project)
3. L'équipe relit les fichiers et corrige les informations erronées.
4. Ajouter les fichiers au dépôt, les committer et les pousser sur le dépôt partagé.
5. Les autres membres font `git clone` ou `git pull`, puis ouvrent le même dossier dans Bob.
6. Vérifier que `AGENTS.md`, `.bob/` et `Défis/` sont visibles dans l'explorateur.

Les règles de projet versionnées sont appliquées aux membres qui clonent le dépôt. 📚 [Standardize Bob's behavior across your team](https://bob.ibm.com/docs/ide/getting-started/tutorials/standardize-bobs-behavior)

## 9. Partager la configuration du projet

```
Étape 0 : Créer le dépôt Git et le partager avec l'équipe
    git init mon-projet && git remote add origin <url>

Étape 1 : Le Lead Dev lance /init dans Bob
    → AGENTS.md et .bob/ générés automatiquement

Étape 2 : Créer les fichiers de rules
    mkdir -p .bob/rules .bob/rules-agent .bob/rules-plan
    → Créer 01_stack.md, 02_langue.md, 03_equipe.md (voir exemples ci-dessus)

Étape 3 : Créer .bob/mcp.json avec les MCPs de l'équipe

Étape 4 : Commiter tout ça
    git add AGENTS.md .bob/
    git commit -m "docs: configuration Bob projet partagée"
    git push

Étape 5 : Chaque membre clone le dépôt
    git clone <url>
    → Bob est immédiatement configuré avec les règles d'équipe
```

---

## Ce que ça change concrètement pendant le hackathon

| Sans config partagée | Avec `.bob/` versionné |
|---|---|
| Bob répond en anglais pour l'un, en français pour l'autre | Tous reçoivent des réponses en français |
| Chaque dev redemande le contexte projet à chaque conv | Bob connaît la stack dès l'ouverture |
| Code généré avec des conventions différentes | Code homogène, même style |
| Un membre configure un MCP, les autres n'y ont pas accès | Le `mcp.json` partagé débloque tout le monde |
| Impossible de savoir qui a fait quoi avec Bob | Les commits de rules tracent l'évolution |

---

## Règle des BobCoin et configuration

> La configuration `.bob/` est un **investissement à coût nul en BobCoin** : les fichiers de rules et `AGENTS.md` sont lus automatiquement par Bob sans consommer de coins. Ce sont des instructions système, pas des messages.

**Conséquence :** une bonne configuration `.bob/` réduit la longueur de vos prompts → moins de tokens → moins de coins consommés sur l'ensemble du hackathon.

---

## 10. Checklist avant de démarrer le hacking (Ven 22h)

- [ ] `/init` lancé sur le projet
- [ ] `AGENTS.md` relu et corrigé si Bob a mal interprété la stack
- [ ] `.bob/rules/01_stack.md` créé avec la vraie stack choisie
- [ ] `.bob/rules/02_langue.md` créé (réponses en français, format concis)
- [ ] `.bob/rules/03_equipe.md` créé avec les rôles et périmètres
- [ ] `.bob/mcp.json` créé si utilisation d'outils web
- [ ] Tout commité et pushé sur le dépôt partagé
- [ ] Chaque membre a cloné et vérifié que Bob lit bien les règles

---

*Voir aussi : `01_bob_bobcoin.md` — économiser ses coins · `03_bob_mcp_web.md` — ajouter la recherche web*
