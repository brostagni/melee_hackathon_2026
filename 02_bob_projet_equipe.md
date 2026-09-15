# Ouvrir Bob et travailler en équipe
> Fiche 02 · Hackathon IA for Impact 2026

📚 **Documentation Bob** : [Quickstart — Set up your workspace](https://bob.ibm.com/docs/ide/getting-started/quickstart) · [Start a project with `/init`](https://bob.ibm.com/docs/ide/getting-started/tutorials/start-a-project) · [Règles projet](https://bob.ibm.com/docs/ide/configuration/rules) · [Configuration MCP](https://bob.ibm.com/docs/ide/configuration/mcp/mcp-in-bob)

---

## Vocabulaire de base (à lire une fois)

| Terme | Ce que c'est |
|---|---|
| **IBMid** | Compte personnel IBM. Un par personne. Ne se partage pas. Sert à s'identifier sur Bob et les services IBM associés à votre compte. |
| **Bob** | L'application installée sur votre ordinateur. Chaque membre l'installe sur sa propre machine. |
| **Workspace Bob** | Le dossier ouvert dans Bob. Bob travaille dans le périmètre de ce dossier : c'est là qu'il lit les fichiers et applique les règles projet. Ouvrir le bon dossier est indispensable. |
| **Dépôt Git (repo)** | Le lieu de stockage partagé du code, hébergé sur GitHub. C'est le seul endroit que tout le monde partage. Bob ne se partage pas — le dépôt Git, si. |
| **`.bob/`** | Sous-dossier du dépôt contenant les fichiers de configuration de Bob destinés à l'équipe. Versionné avec Git : quand un membre pousse ses modifications, tous les autres les reçoivent au prochain `git pull`. |
| **`AGENTS.md`** | Fichier de contexte projet à la racine, chargé automatiquement par Bob comme contexte projet. Coût faible si concis — voir fiche [`01_bob_bobcoin.md`](01_bob_bobcoin.md). |

> 💡 Les termes Git (commit, push, pull, clone…) sont définis dans le lexique de la [fiche `00_bob_intro.md`](00_bob_intro.md).

---

## Créer son accès Bob (à faire avant le hackathon)

Avant de pouvoir utiliser Bob, il faut un **IBMid** — le compte qui permet de s'identifier sur les services IBM.

**Étapes :**

1. Aller sur **[bob.ibm.com](https://bob.ibm.com)** et cliquer sur **Get free trial**.
2. Sur la page de connexion, deux cas :
   - **Vous avez déjà un IBMid** (compte IBM Cloud, IBM Marketplace, etc.) → utilisez-le directement.
   - **Vous n'en avez pas** → l'email saisi lors de l'inscription deviendra votre IBMid. L'accès effectif aux services IBM dépend des abonnements et autorisations associés à votre compte.
3. Télécharger et installer l'application Bob (macOS ou Windows).
4. Se connecter avec l'IBMid créé ou existant.

> **Conseil hackathon** : faites ceci la veille. L'activation peut prendre quelques minutes. Si vous avez déjà un IBM Cloud ID, c'est le même IBMid — pas besoin d'en créer un nouveau.

---

## 1. Préparer son poste de travail

### Où créer le dossier de travail ?

Avant de cloner ou d'ouvrir quoi que ce soit dans Bob, il faut décider **où ranger le projet** sur votre machine. Un mauvais emplacement (bureau, racine du disque, dossier Téléchargements) complique les commandes et crée de la confusion.

**Conseil : créer un dossier `BobIA` dans votre dossier personnel**, puis y mettre tous les projets du hackathon :

```
Mac/Linux :   ~/Documents/BobIA/
Windows :     C:\Users\votre-prenom\Documents\BobIA\
```

Créer ce dossier une fois, avant le hackathon :

```bash
# Mac/Linux — dans n'importe quel terminal :
mkdir -p ~/Documents/BobIA

# Windows PowerShell :
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\Documents\BobIA"
```

Tous les projets clonés s'y retrouveront dans des sous-dossiers :
```
~/Documents/BobIA/
├── Melee_Hackaton/              ← ce dossier de préparation
└── hackathon-2026-equipe/       ← le projet d'équipe créé le soir du hackathon
```

### Quel terminal utiliser ?

**Utiliser le terminal intégré à Bob** — il s'ouvre directement dans le dossier du projet ouvert, ce qui évite d'avoir à naviguer avec `cd` à chaque fois.

Ouvrir le terminal Bob : menu **Terminal → New Terminal**.

> Si vous préférez un terminal externe (Terminal macOS, PowerShell, Git Bash), assurez-vous d'y avoir navigué dans le bon dossier avec `cd` avant de lancer des commandes Git.

---

## 2. Ouvrir un projet dans Bob

Bob travaille dans le dossier ouvert sur votre machine. Il n'existe pas de « projet Bob en ligne » : tout passe par un dossier local. Il y a deux situations distinctes dans le hackathon.

Le raccourci pour ouvrir le chat Bob : `Option + Cmd + B` sur Mac, `Ctrl + Alt + B` sur Windows. 📚 [Quickstart Bob](https://bob.ibm.com/docs/ide/getting-started/quickstart)

---

### Situation A — Avant le hackathon : workspace de préparation individuelle

**Pour qui** : chaque membre de l'équipe, individuellement, pour se familiariser avec les fiches et explorer les défis. Pas de GitHub, pas de partage — chacun travaille sur sa propre copie locale des fiches de préparation.

> 💡 Chacun explore les défis à son propre rythme, selon son rôle. Ce qui limite les doublons, c'est de se répartir les sujets et de partager les synthèses — pas de faire les mêmes recherches en parallèle. Les décisions validées sont à consigner dans `bob-notes.md` (voir §8).

1. Lancer Bob et se connecter avec son IBMid.
2. **File → Open Folder** → naviguer jusqu'à `~/Documents/BobIA/Melee_Hackaton` (ou l'emplacement où vous avez placé ces fiches) → sélectionner ce dossier.
3. Vérifier que `Défis/` est visible dans l'explorateur de Bob.
4. Ouvrir le chat Bob → tester une question en mode Ask.

---

### Situation B — Le soir du hackathon : rejoindre le projet d'équipe

**Pour qui** : les membres de l'équipe (pas le Lead Dev — il crée le projet, voir §11). À faire dès que le Lead Dev a pushé et partagé l'URL dans le chat d'équipe.

**Étape 1 — Se placer dans le bon dossier**

Ouvrir le terminal Bob (ou un terminal externe) et se placer dans le dossier `BobIA` :

```bash
cd ~/Documents/BobIA        # Mac/Linux
cd $env:USERPROFILE\Documents\BobIA   # Windows PowerShell
```

**Étape 2 — Télécharger le projet**

Remplacer l'URL ci-dessous par celle communiquée par le Lead Dev dans le chat d'équipe :

```bash
git clone https://github.com/equipe/hackathon-2026-equipe.git
# → crée un sous-dossier hackathon-2026-equipe/ avec tout le projet dedans

cd hackathon-2026-equipe
# → entre dans ce dossier
```

> Si vous avez déjà cloné le dépôt, ouvrez votre copie existante et récupérez les mises à jour ; ne le clonez pas une seconde fois.

**Étape 3 — Ouvrir le projet dans Bob**

Dans Bob : **File → Open Folder** → naviguer jusqu'à `~/Documents/BobIA/hackathon-2026-equipe` → sélectionner ce dossier.

Si Bob demande *"Do you trust the authors ?"* → **Yes, I trust the authors**.

**Étape 4 — Vérifier**

Vérifier que `AGENTS.md` et `.bob/` sont visibles dans l'explorateur Bob.

> ⚠️ Ouvrir le bon dossier est critique. Si vous ouvrez `BobIA/` au lieu de `BobIA/hackathon-2026-equipe/`, `AGENTS.md` peut ne pas être chargé automatiquement comme contexte projet par Bob.

---

## 3. Préparer les documents du défi

Avant l'analyse, placer dans le dossier `Défis/` les supports remis par l'organisation ou les sponsors. Conserver les fichiers dans leur format d'origine et utiliser un nom explicite. Ce dossier devient la source locale de travail de l'équipe.

---

## 4. Pourquoi configurer Bob en équipe

Sans configuration partagée, chaque membre de l'équipe Bob :
- Reçoit des réponses dans des styles différents
- Doit réexpliquer le contexte du projet à chaque nouvelle conversation
- Génère du code avec des conventions différentes (nommage, langue, structure)
- Ne bénéficie pas du travail de configuration fait par les autres membres

**La solution :** un dossier `.bob/` commité dans le dépôt Git du projet. Tout le monde le clone, tout le monde dispose des mêmes fichiers de configuration automatiquement.

---

## 5. Architecture des fichiers Bob d'un projet

```
hackathon-2026-equipe/
├── AGENTS.md                        ← Contexte global projet (chargé par Bob au démarrage)
├── docs/
│   └── bob-notes.md                 ← Décisions d'équipe partagées (voir §8)
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

> Les fichiers de configuration destinés à l'équipe sont versionnés avec Git. Un `git clone` partage ces fichiers — les dépendances locales, identifiants et outils système (ex : `uvx`) doivent être installés séparément par chaque membre.

---

## 6. Générer le contexte projet avec `/init`

La commande `/init` est à lancer **après avoir créé le squelette applicatif minimal** — pas sur un dépôt vide, où elle ne trouverait rien à analyser.

### Comment ça marche

1. Ouvrir Bob (mode **Agent**)
2. Taper `/init` dans le chat
3. Bob analyse les fichiers du projet et génère automatiquement :
   - `AGENTS.md` à la racine — résumé de la structure, stack, conventions détectées
   - Des fichiers de contexte dans `.bob/rules-agent/`, `.bob/rules-plan/`, `.bob/rules-ask/`

> **Note sur les fichiers générés** : les noms exacts (`AGENTS-agent.md`, `AGENTS-plan.md`…) peuvent varier selon la version de Bob installée. Vérifiez ce qui a été créé dans `.bob/` après `/init` avant de commiter.

### Ce que `AGENTS.md` contient typiquement

```
# Mon Projet — Contexte Bob

## Stack
- Backend : Python / FastAPI
- Frontend : React + TypeScript
- IA : API OpenAI (modèle : à confirmer avec votre compte hackathon)
- Base de données : SQLite en dev, PostgreSQL en prod

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

> Le modèle mentionné dans `AGENTS.md` est celui que **votre application** appelle via l'API OpenAI — il est distinct du modèle qu'utilise Bob en interne pour générer du code.

### Quand relancer `/init`

- Après avoir ajouté un module majeur
- Après un changement de stack
- Si Bob ne semble plus comprendre la structure du projet

> La consommation de `/init` dépend du volume de fichiers à analyser — à observer sur votre projet. C'est un investissement ponctuel qui structure toute la session. Voir fiche [`01_bob_bobcoin.md`](01_bob_bobcoin.md).

---

## 7. Créer les règles d'équipe dans `.bob/rules/`

Les rules sont des fichiers Markdown chargés automatiquement par Bob à **chaque conversation**, dans **tous les modes**.

### Règle de priorité

```
~/.bob/rules/          ← règles globales personnelles (sur votre machine)
    ↓ (surchargées par)
.bob/rules/            ← règles projet partagées (dans le dépôt Git)
```

Les règles projet ont la priorité. Elles s'appliquent à tous les membres de l'équipe.

> 💡 Garder les fichiers de rules **courts et denses** : ils sont chargés à chaque conversation. Des rules verbeuses consomment des BobCoins à chaque échange.

---

### Exemple de fichier `.bob/rules/01_stack.md`

```
# Stack & Conventions de code

## Stack technique
- Backend : Python 3.12 / FastAPI
- Frontend : React 18 + TypeScript 5
- IA : appels à l'API OpenAI (modèle : à confirmer avec votre compte hackathon)
- Base de données : SQLite en dev, PostgreSQL en prod

## Conventions de code
- Nommage : snake_case pour Python, camelCase pour TypeScript
- Documenter les interfaces et comportements non évidents (pas de docstring mécanique sur chaque fonction)
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
- Branche principale : main (protégée après le premier push)
- Format des branches : feat/nom-feature, fix/nom-bug
- Commits : "feat: description", "fix: description", "docs: description"
- Pas de push direct sur main — Pull Request obligatoire

## Périmètres
- Alice et Bob-dev coordonnent avec Carol avant de toucher /frontend
- Carol coordonne avec Alice avant de toucher /backend/api
- David est responsable de /docs et /pitch — coordonner avec lui avant toute modification
```

---

## 8. Partager les résultats de Bob avec l'équipe

### Ce que Bob ne partage pas nativement

Chaque conversation Bob est **locale et privée**. Il n'existe pas de « chat Bob partagé » en temps réel : si Alice obtient une réponse utile, Carol n'en voit rien — sauf si Alice la partage explicitement. Bob ne voit pas non plus les messages du chat d'équipe ni les décisions prises à l'oral.

### Ce qui mérite d'être partagé

Pendant le hackathon, chacun peut obtenir de Bob des réponses utiles à toute l'équipe : une architecture validée, un prompt qui fonctionne, la cause d'un bug. Partager ces découvertes évite que plusieurs personnes posent la même question et que le contexte commun se fragmente.

**Ce qui mérite d'être partagé :**
- Une décision technique validée (stack, format de données, convention)
- Un prompt ou paramètre de modèle qui fonctionne bien
- La cause et le correctif d'un bug bloquant
- Une règle à ajouter dans `.bob/rules/` pour toute l'équipe

**Ce qui n'a pas besoin d'être partagé :** questions de compréhension personnelles, explorations sans résultat utile — sauf si l'essai infructueux lui-même fait gagner du temps à l'équipe (ex. : « j'ai essayé X, ça ne fonctionne pas avec notre stack »).

### Comment partager : chat d'équipe + une personne désignée

**Étape 1 — Partager dans le chat d'équipe** (WhatsApp, Slack…)

Chaque membre poste dans le chat d'équipe les découvertes utiles, en quelques lignes. Exemple :
> *« Prompt validé — fonctionne sur nos données de test. »*
> *« Bug parsing CSV : séparateur `;` pas `,` — corrigé dans /backend/parser.py ligne 42. »*

**Étape 2 — Une personne désignée consigne les décisions validées**

Une seule personne (le Lead Dev, ou une personne désignée en début de hackathon) est responsable de `docs/bob-notes.md`. Elle lit les décisions partagées dans le chat, consigne celles que l'équipe a validées, et les publie selon la procédure Git commune (voir §11).

> **Pourquoi une seule personne ?** Si plusieurs membres modifient `bob-notes.md` en même temps sur des branches différentes, les décisions se retrouvent dispersées et difficiles à réconcilier sous pression hackathon.

**Étape 3 — Les autres membres récupèrent les notes**

Après fusion de la PR, les notes sont disponibles dans `main`. Elles arrivent lors de la synchronisation habituelle du projet — par exemple au moment de mettre à jour sa branche de travail depuis `main`. Un `git pull` sur une branche personnelle ne récupère pas automatiquement les changements de `main`.

### Format recommandé pour `bob-notes.md`

```markdown
# Bob Notes — Décisions équipe

## [Ven 22h15] Architecture retenue
- Backend : FastAPI + SQLite
- Pas de Redis, trop complexe pour 24h
- Validé par l'équipe

## [Sam 02h30] Prompt OpenAI
Paramètres validés sur nos données de test — vérifier l'identifiant exact du modèle avec votre compte hackathon

## [Sam 07h00] Bug parsing CSV
Séparateur `;` pas `,` — corrigé dans /backend/parser.py ligne 42
```

---

## 9. Règles spécifiques par mode

Certaines règles ne s'appliquent qu'à un mode précis.

### `.bob/rules-agent/agent_rules.md` — Mode Agent (génération de code)

```
# Règles Agent

- Produire le changement minimal qui résout le problème
- Ne pas refactoriser du code non lié à la tâche
- Indiquer les fichiers modifiés en début de réponse
- Après chaque modification, résumer en 1 phrase ce qui a changé et pourquoi
- Exécuter les vérifications disponibles (tests, lint) et signaler celles qui n'ont pas été réalisées
```

### `.bob/rules-plan/plan_rules.md` — Mode Plan (architecture, conception)

```
# Règles Plan

- Proposer 2-3 options quand un arbitrage réel existe
- Inclure les compromis (trade-offs) pour chaque option
- Format de sortie : titres H2, listes à puces, tableau comparatif si pertinent
- Penser "démo hackathon" : préférer la simplicité à l'élégance
```

---

## 10. Partager la configuration MCP

Le fichier `.bob/mcp.json` configure les serveurs MCP (outils externes : recherche web, APIs…) **au niveau projet**, partagés avec toute l'équipe.

```json
{
  "mcpServers": {
    "fetch": {
      "command": "uvx",
      "args": ["mcp-server-fetch"]
    }
  }
}
```

> **Prérequis** : `uvx` fait partie de `uv` (gestionnaire Python). Chaque membre doit l'avoir installé ([docs uv](https://docs.astral.sh/uv/)). Après avoir ouvert le projet dans Bob, vérifier dans l'onglet MCP que le serveur s'initialise correctement, puis tester avec un appel simple.

### Gérer les secrets MCP (clés API)

Partager `mcp.json` ne suffit pas si le serveur nécessite une clé API. Procédure recommandée :

1. **Versionner un fichier modèle** : `.bob/mcp.json.example` avec la structure mais sans valeur secrète (utiliser un marqueur comme `TAVILY_API_KEY_ICI` à la place de la vraie clé — vérifier dans la [documentation IBM MCP](https://bob.ibm.com/docs/ide/configuration/mcp/mcp-in-bob) si votre version de Bob supporte l'injection de variables d'environnement).
2. **Chaque membre** copie `.bob/mcp.json.example` en `.bob/mcp.json` et renseigne sa propre clé.
3. **Ajouter `.bob/mcp.json` au `.gitignore` ET au `.bobignore`** — pour que ni Git ni Bob n'indexent le fichier contenant la vraie clé.
4. **Documenter dans le README** quelle variable fournir et comment l'obtenir.

> ⚠️ Une variable d'environnement définie dans un terminal n'est **pas nécessairement disponible dans Bob lancé depuis l'interface graphique** (Finder, Launchpad, menu Démarrer). Configurer les variables d'environnement au niveau système ou via les mécanismes documentés par Bob.

📚 [Sécurité MCP](https://bob.ibm.com/docs/ide/configuration/mcp/understanding-mcp) · [Sécurité Bob](https://bob.ibm.com/docs/ide/security/bob-security-guidance) · Voir aussi fiche [`03_bob_mcp_web.md`](03_bob_mcp_web.md).

---

## 11. Séquence complète — qui fait quoi, dans quel ordre

📚 [Standardize Bob's behavior across your team](https://bob.ibm.com/docs/ide/getting-started/tutorials/standardize-bobs-behavior)

### Rappel : la logique Git en 3 temps

Modifier un fichier ne suffit pas à le partager. Git fonctionne toujours dans cet ordre :

```
git add      → sélectionner les fichiers à inclure ("je veux mettre ça dans la photo")
git commit   → prendre la photo et lui donner un nom ("j'enregistre cet état")
git push     → envoyer la photo sur GitHub, visible par toute l'équipe ("je publie")
```

Sans `push`, personne d'autre ne voit vos modifications. Sans `commit`, vous ne pouvez pas `push`.

> **Procédure normale après l'initialisation :** toute modification passe par une branche, un commit, un push de cette branche, puis une Pull Request vers `main`. Le bloc Lead Dev ci-dessous est l'unique exception : le tout premier push se fait directement sur `main` avant que la protection soit activée.

---

### Bloc Lead Dev — à faire une seule fois, dès 22h (fin d'étape 1)

> **Si le dépôt n'a pas déjà été créé à l'étape 1** (fiche 05 § 4b), commencer par les étapes 1 et 2 ci-dessous. Si le dépôt existe déjà, passer directement à l'étape 3.

```bash
# 0. Se placer dans le bon dossier de travail
cd ~/Documents/BobIA        # Mac/Linux
# cd $env:USERPROFILE\Documents\BobIA   # Windows PowerShell

# 1. Créer le dépôt sur GitHub
#    → github.com → "New repository" → nom du projet → Create
#    → inviter les membres de l'équipe (Settings → Collaborators)
#    → copier l'URL HTTPS affichée (ex : https://github.com/equipe/hackathon-2026-equipe.git)

# 2. Cloner en local (une seule fois — on reste dans BobIA/)
git clone https://github.com/equipe/hackathon-2026-equipe.git
cd hackathon-2026-equipe
# → on est maintenant dans ~/Documents/BobIA/hackathon-2026-equipe/

# 3. Ouvrir ce dossier dans Bob : File → Open Folder → BobIA/hackathon-2026-equipe
#    Puis ouvrir le terminal Bob : Terminal → New Terminal

# 4. Créer le squelette minimal du projet avec Bob (mode Agent)
#    → prompt : voir fiche 06 §4
#    → critère de succès : le projet démarre avec une commande

# 5. Vérifier que l'application démarre
#    → ex : npm run dev, python main.py…
#    → ne pas passer à la suite si ça ne démarre pas

# 6. Lancer /init dans le chat Bob (mode Agent)
#    → Bob analyse le squelette et génère AGENTS.md et .bob/ automatiquement
#    → NE PAS lancer /init sur un repo vide : il ne trouverait rien à analyser

# 7. Relire AGENTS.md et corriger si Bob a mal interprété la stack

# 8. Créer les fichiers de rules (voir exemples §7 ci-dessus)
#    Terminal Bob — Mac/Linux :
mkdir -p .bob/rules .bob/rules-agent .bob/rules-plan
#    Windows PowerShell :
#    New-Item -ItemType Directory -Force -Path .bob/rules, .bob/rules-agent, .bob/rules-plan

# 9. Créer .bob/mcp.json.example si utilisation d'outils web
#    Ajouter .bob/mcp.json à .gitignore ET .bobignore

# 10. Vérifier ce qui sera inclus dans le commit
git status
#     → s'assurer qu'aucun fichier sensible (.env, données locales, secrets)
#     → ne figure pas dans la liste — compléter .gitignore si nécessaire

# 11. Préparer le commit et inspecter son contenu
git add .
git diff --cached
#     → affiche ligne par ligne ce qui sera commité
#     → vérifier qu'aucune clé, mot de passe ou donnée locale n'apparaît
#     → Ctrl+Q (ou q) pour quitter l'affichage
git commit -m "feat: squelette initial + configuration Bob"
git push

# 12. Configurer la protection de main sur GitHub
#     → Settings → Branches → Add rule → "main" → Require pull request
#     → À faire APRÈS le premier push, pas avant
```

**Dès que le push est visible sur GitHub**, prévenir l'équipe (chat, WhatsApp…) avec l'URL du dépôt.

---

### Bloc membres — à faire dès que le Lead Dev a pushé

```bash
# 0. Se placer dans le bon dossier de travail
cd ~/Documents/BobIA        # Mac/Linux
# cd $env:USERPROFILE\Documents\BobIA   # Windows PowerShell

# 1. Télécharger le projet (une seule fois)
#    Remplacer l'URL par celle communiquée par le Lead Dev dans le chat d'équipe
git clone https://github.com/equipe/hackathon-2026-equipe.git
cd hackathon-2026-equipe
# → on est maintenant dans ~/Documents/BobIA/hackathon-2026-equipe/

# 2. Ouvrir ce dossier dans Bob : File → Open Folder → BobIA/hackathon-2026-equipe
#    Si Bob demande "Do you trust the authors ?" → Yes, I trust the authors
#    Puis ouvrir le terminal Bob : Terminal → New Terminal

# 3. Vérifier que .bob/ et AGENTS.md sont visibles dans l'explorateur Bob

# 4. Installer les dépendances du projet (dans le terminal Bob)
#    → ex : npm install  /  pip install -r requirements.txt

# 5. Vérifier que l'application démarre
#    → ex : npm run dev, python main.py

# 6. Configurer les MCP si utilisés
#    → Copier .bob/mcp.json.example en .bob/mcp.json
#    → Renseigner sa propre clé API
#    → Installer uvx si nécessaire : pip install uv
#    → Vérifier l'onglet MCP dans Bob : le serveur doit s'initialiser

# 7. Ouvrir le chat Bob (Option+Cmd+B sur Mac, Ctrl+Alt+B sur Windows)
#    → Poser une question sur le projet en mode Ask
#    → Vérifier que Bob mentionne la stack et les conventions

# 8. Vérifier que vous pouvez contribuer
#    → Créer une branche de test : git checkout -b test/mon-prenom
#    → Pousser : git push origin test/mon-prenom
#    → La branche est visible sur GitHub = tout fonctionne
```

> Si Bob ne mentionne pas la stack ou répond en anglais → vérifier que le bon dossier est ouvert comme workspace (pas `BobIA/` mais bien `BobIA/hackathon-2026-equipe/`).

---

## Ce que ça change concrètement pendant le hackathon

| Sans config partagée | Avec `.bob/` versionné |
|---|---|
| Bob répond en anglais pour l'un, en français pour l'autre | Les règles **orientent** vers des réponses cohérentes en français |
| Chaque dev redemande le contexte projet à chaque conv | Bob dispose du contexte projet dès l'ouverture |
| Code généré avec des conventions différentes | Les règles **favorisent** des conventions communes |
| Un membre configure un MCP, les autres n'y ont pas accès | Le `mcp.json.example` partagé fournit la configuration — chaque membre installe ses prérequis locaux |
| Décisions Bob perdues dans les conversations individuelles | `docs/bob-notes.md` versionné centralise les décisions |
| Impossible de savoir comment la configuration a évolué | Les commits de rules tracent l'évolution de la configuration |

---

## Configuration Bob et BobCoins

> La configuration `.bob/` contribue au contexte chargé à chaque conversation. Des règles **concises et ciblées peuvent réduire les répétitions et les corrections** — et donc la consommation globale. Elles ne garantissent pas une réduction automatique. 📚 [Context window management](https://bob.ibm.com/docs/ide/core-concepts/context-window-management)

Un `AGENTS.md` de 500 lignes ou des `rules/` verbeux se retrouvent dans chaque requête et alourdissent le contexte à chaque échange.

---

## 12. Checklist avant de démarrer le hacking (Ven 22h)

### Lead Dev
- [ ] Dossier `~/Documents/BobIA/` créé sur sa machine
- [ ] Dépôt créé sur GitHub et accès donnés aux membres
- [ ] Dépôt cloné dans `BobIA/` (une seule fois)
- [ ] Squelette applicatif créé et fonctionnel (l'app démarre)
- [ ] `/init` lancé après le squelette (pas sur repo vide)
- [ ] `AGENTS.md` relu et corrigé si Bob a mal interprété la stack
- [ ] `.bob/rules/01_stack.md` créé avec la vraie stack (cohérente avec `AGENTS.md`)
- [ ] `.bob/rules/02_langue.md` créé
- [ ] `.bob/rules/03_equipe.md` créé avec rôles et périmètres
- [ ] `docs/bob-notes.md` créé avec une première entrée de décision
- [ ] `.bob/mcp.json.example` créé si MCP utilisé ; `.bob/mcp.json` dans `.gitignore` et `.bobignore`
- [ ] Code **et** configuration commités et pushés ensemble (`git add .`)
- [ ] Protection de `main` configurée sur GitHub après le premier push

### Chaque membre
- [ ] Dossier `~/Documents/BobIA/` créé sur sa machine
- [ ] Dépôt cloné dans `BobIA/` et projet ouvert dans Bob (`BobIA/mon-projet/` — pas le dossier parent)
- [ ] Terminal Bob ouvert et positionné dans le bon dossier
- [ ] Dépendances installées (`npm install`, `pip install -r requirements.txt`…)
- [ ] Application démarrée localement
- [ ] `AGENTS.md` et `.bob/` visibles dans l'explorateur Bob
- [ ] Bob mentionne la stack et les conventions dans ses réponses (mode Ask)
- [ ] Serveur MCP actif dans l'onglet MCP Bob (si utilisé) — test d'appel simple réalisé
- [ ] Capable de créer une branche, commiter et ouvrir une PR

---

*Voir aussi : [`00_bob_intro.md`](00_bob_intro.md) — lexique Git et concepts · [`01_bob_bobcoin.md`](01_bob_bobcoin.md) — économiser ses coins · [`03_bob_mcp_web.md`](03_bob_mcp_web.md) — ajouter la recherche web*
