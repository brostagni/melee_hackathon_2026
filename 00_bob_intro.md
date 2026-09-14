# C'est quoi Bob ?
> Fiche 00 · Hackathon IA for Impact 2026

📚 **Doc officielle** : [bob.ibm.com](https://bob.ibm.com) · [IBM Bob — Welcome](https://bob.ibm.com/docs/ide)

---

## En une phrase

> **IBM Bob est un assistant IA de développement logiciel qui agit directement dans votre projet** : il lit vos fichiers, écrit du code, exécute des commandes, et peut utiliser des outils externes — tout ça depuis une interface de chat.

Ce n'est pas un chatbot. C'est un **agent** capable d'agir sur votre codebase.

---

## Bob vs les autres — ce qui est différent

> ⚠️ Ce tableau compare les capacités documentées publiquement. Les outils évoluent vite — vérifiez les sources officielles pour les nouveautés.

| Capacité | Bob (IBM) | Claude (Anthropic) | GitHub Copilot | Gemini (Google) |
|---|---|---|---|---|
| **Lit vos fichiers locaux** | ✅ natif | ⚠️ via Projects/upload | ✅ dans VS Code | ⚠️ via upload |
| **Écrit et modifie des fichiers** | ✅ natif | ❌ (suggère seulement) | ✅ dans IDE | ❌ (suggère seulement) |
| **Exécute des commandes terminal** | ✅ natif | ❌ | ⚠️ limité | ❌ |
| **Outils externes via MCP** | ✅ natif | ✅ (Claude Desktop) | ❌ | ❌ |
| **Règles projet partagées en équipe** | ✅ `.bob/rules/` | ⚠️ Project instructions | ❌ | ❌ |
| **Modes distincts (Ask/Plan/Agent)** | ✅ | ❌ | ❌ | ❌ |
| **Commande `/init` projet** | ✅ | ❌ | ❌ | ❌ |
| **Budget de consommation (BobCoin)** | ✅ transparent | ❌ (abonnement fixe) | ❌ (abonnement fixe) | ❌ (abonnement fixe) |

**Ce qui rend Bob unique pour un hackathon :**
- Il travaille *dans* votre projet, pas *à côté*
- Il partage sa configuration via Git → toute l'équipe est synchronisée
- Les modes évitent de gaspiller du budget sur des tâches qui n'en ont pas besoin

---

## Les 3 modes essentiels

> 📚 Doc : [Modes — IBM Bob](https://bob.ibm.com/docs/ide/features/modes)

Bob a trois modes built-in. **Choisir le bon mode est la première décision à prendre avant chaque interaction.**

### 💬 Mode Ask — *"Explique-moi"*
- Répond à des questions, explique du code, donne des conseils
- **Ne modifie aucun fichier**
- Consomme le moins de BobCoin
- → À utiliser pour : comprendre un concept, analyser un défi, poser une question

### 🗺️ Mode Plan — *"On réfléchit ensemble"*
- Conçoit des architectures, compare des options, produit des spécifications
- **Ne modifie aucun fichier**
- Consomme moins qu'Agent (pas d'exécution d'outils)
- → À utiliser pour : choisir une stack, concevoir un schéma de données, planifier l'implémentation

### 🤖 Mode Agent — *"Fais-le"*
- Lit, écrit et modifie vos fichiers, exécute des commandes, appelle des MCPs
- **Modifie réellement votre projet** — demande confirmation avant chaque action (sauf si auto-approuvé)
- Consomme le plus de BobCoin
- → À utiliser pour : générer du code, corriger un bug, créer des fichiers

> **Règle d'or** : Ask → Plan → Agent. Ne passez en Agent que quand vous savez exactement ce que vous voulez. Voir fiche `01_bob_bobcoin.md`.

---

## Ce que Bob peut faire concrètement

Basé sur la [documentation officielle](https://bob.ibm.com/docs/ide) :

### Outils natifs
- **Lire des fichiers** : Bob lit votre codebase entier si nécessaire
- **Écrire et modifier des fichiers** : avec des diffs précis, pas de réécriture brutale
- **Exécuter des commandes** : `npm install`, `python script.py`, `git commit`…
- **Rechercher dans le code** : grep, recherche de symboles, références croisées

### Via MCP (Model Context Protocol)
- **Recherche web** : avec un serveur MCP comme Tavily ou mcp-server-fetch
- **APIs externes** : n'importe quelle API peut être connectée via MCP
- **Outils custom** : vous pouvez écrire votre propre serveur MCP

> 📚 Doc MCP : [Using MCP in Bob](https://bob.ibm.com/docs/ide/features/mcp/using-mcp-in-bob)

### Via Skills
- Des instructions spécialisées activables à la demande (ex : "carbon-builder", "terraform"…)
- Étendent les capacités de Bob sans configuration supplémentaire

---

## L'interface en 30 secondes

```
┌─────────────────────────────────────────────────┐
│  Explorateur de fichiers     │  Éditeur de code  │
│  (votre projet)              │                   │
│                              │                   │
├──────────────────────────────┤                   │
│  Chat Bob (sidebar droite)   │                   │
│  ┌──────────────────────┐    │                   │
│  │ [Ask] [Plan] [Agent] │ ←  Sélecteur de mode  │
│  └──────────────────────┘    │                   │
│  > Votre message ici...      │                   │
└─────────────────────────────────────────────────┘
```

- Le **sélecteur de mode** est en bas à droite du chat
- Le **compteur de tokens** (context window) est en haut à droite du chat
- Le **bouton `+`** ouvre une nouvelle conversation (remet le contexte à zéro)

---

## Les 3 premières actions sur un nouveau projet

```
1. Ouvrir le projet dans Bob
2. Taper /init  →  Bob génère AGENTS.md et .bob/ automatiquement
3. Vérifier AGENTS.md  →  corriger si Bob a mal interprété la stack
```

> `/init` ne coûte pas de BobCoin. C'est la base de tout.
> 📚 Doc : [Start a project with /init](https://bob.ibm.com/docs/ide/getting-started/tutorials/start-a-project)

---

## Ce que Bob ne fait pas

- ❌ **Il ne se souvient pas d'une conversation à l'autre** — chaque nouvelle conversation repart de zéro (d'où l'importance de `AGENTS.md`)
- ❌ **Il n'a pas accès à internet par défaut** — il faut ajouter un MCP web (voir fiche `03_bob_mcp_web.md`)
- ❌ **Il ne valide pas que le code fonctionne** — il génère, vous testez
- ❌ **Il ne remplace pas la réflexion de l'équipe** — il accélère l'exécution d'une décision déjà prise

---

*Voir aussi : `01_bob_bobcoin.md` — gérer son budget · `02_bob_projet_equipe.md` — configurer Bob en équipe*
