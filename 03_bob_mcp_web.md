# Ajouter la recherche web à Bob — MCP Tavily
> Fiche 03 · Hackathon IA for Impact 2026

📚 **Doc officielle Bob MCP** : [Using MCP in Bob](https://bob.ibm.com/docs/ide/features/mcp/using-mcp-in-bob)
📚 **Tavily** : [tavily.com](https://tavily.com) · [Documentation](https://docs.tavily.com)
📚 **uv** : [docs.astral.sh/uv](https://docs.astral.sh/uv/getting-started/installation/)

---

## Pourquoi Bob ne peut pas chercher sur internet par défaut

Bob ne dispose d'aucun accès réseau sans configuration explicite. Sans MCP web :
- Il ne peut pas vérifier une API externe
- Il ne peut pas lire une documentation qui n'est pas dans ses données d'entraînement
- Il ne peut pas chercher les bases réglementaires publiques (défi Lallemand), les horaires SNCF ou les formats de remboursement MSA

Le MCP Tavily connecte Bob à un moteur de recherche web optimisé pour les agents IA.

---

## ⚖️ Règle d'or : Tavily MCP vs Google manuel

> **Principe** : laisser Bob chercher lui-même coûte des BobCoin. Chercher toi-même sur Google et coller le résultat dans le chat ne coûte rien de plus.

| Situation | Que faire | Coût BobCoin |
|---|---|---|
| Tu sais exactement quelle page tu veux | Google → coller l'URL ou le texte dans le chat | 0 supplémentaire |
| Tu connais l'URL → Bob doit lire la page | `@https://url-que-tu-connais.com` dans le chat | Peu (fetch unique) |
| Tu veux explorer un sujet large sans URL précise | Tavily via Bob | Coins supplémentaires |
| Tu veux que Bob synthétise plusieurs sources | Tavily via Bob | Coins supplémentaires |

> 📚 La syntaxe `@url` est documentée : [Context mentions — URL mentions](https://bob.ibm.com/docs/ide/features/context-mentions#url-mentions)

### Exemples concrets pour ce hackathon

| Besoin | Méthode recommandée |
|---|---|
| Lire la doc de l'API SNCF Open Data | Google → trouver l'URL → `@https://...` dans Bob |
| "Quelles bases de données réglementaires existent pour les pesticides en Europe ?" | Tavily via Bob |
| Lire la page EPPO dont tu as déjà l'URL | `@https://gd.eppo.int/...` dans Bob |
| "Quels formats de justificatifs les mutuelles acceptent-elles ?" | Tavily via Bob |

---

## Prérequis — Installer `uv`

Le serveur MCP Tavily nécessite `uvx` (inclus dans `uv`), un gestionnaire de paquets Python rapide.

> 📚 Source : [docs.astral.sh/uv/getting-started/installation](https://docs.astral.sh/uv/getting-started/installation/)

### macOS / Linux
```
curl -LsSf https://astral.sh/uv/install.sh | sh
```

### Windows (PowerShell)
```
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

### Vérifier l'installation
```
uvx --version
```

Si la commande répond avec un numéro de version, `uvx` est prêt.

---

## Option A — Tavily avec clé API (recommandé)

### Étape 1 — Créer un compte Tavily gratuit

1. Aller sur [app.tavily.com](https://app.tavily.com)
2. S'inscrire (email ou GitHub)
3. Copier la clé API : format `tvly-xxxxxxxxxxxxxxxx`

> **Limite gratuite** : 1 000 crédits/mois. Une recherche Tavily coûte 1 crédit.
> Source : [PyPI tavily-python](https://pypi.org/project/tavily-python/) — *"Tavily is free for personal use for up to 1,000 credits per month."*

### Étape 2 — Configurer `.bob/mcp.json`

Créer ou éditer le fichier `.bob/mcp.json` à la racine du projet :

```
{
  "mcpServers": {
    "tavily-mcp": {
      "command": "uvx",
      "args": ["tavily-mcp"],
      "env": {
        "TAVILY_API_KEY": "VOTRE-CLE-TAVILY-ICI"
      }
    }
  }
}
```

> ⚠️ **Ne commitez JAMAIS ce fichier avec la clé en dur.** Voir la section "Partage en équipe" ci-dessous.

### Étape 3 — Vérifier dans Bob

1. Redémarrer Bob (ou recharger la fenêtre)
2. Aller dans **Settings → MCP** — le serveur `tavily-mcp` doit apparaître avec un statut vert
3. Tester dans le chat :

```
Recherche sur le web : quelles sont les principales bases de données 
d'homologation de pesticides en Europe accessibles publiquement ?
```

Bob devrait utiliser l'outil Tavily et citer ses sources.

---

## Option B — Sans clé API (mode dégradé)

Tavily propose un mode sans clé, mais il est **limité et rate-limité** :

> Source PyPI : *"Keyless usage is rate-limited. For higher limits and the full set of endpoints, sign up for a Tavily API key."*

Pour un hackathon avec 4–5 personnes qui cherchent en parallèle, **le mode sans clé atteindra rapidement ses limites**. Privilégiez la clé API gratuite.

---

## Partage de la config en équipe sans exposer la clé

### Ce qui va dans Git (`.bob/mcp.json` sans la clé)

```
{
  "mcpServers": {
    "tavily-mcp": {
      "command": "uvx",
      "args": ["tavily-mcp"],
      "env": {
        "TAVILY_API_KEY": "${TAVILY_API_KEY}"
      }
    }
  }
}
```

### Ce qui reste local (variable d'environnement)

Chaque membre définit la variable d'environnement sur sa machine :

**macOS / Linux** — ajouter dans `~/.zshrc` ou `~/.bashrc` :
```
export TAVILY_API_KEY="VOTRE-CLE-TAVILY-ICI"
```
Puis `source ~/.zshrc` (ou ouvrir un nouveau terminal).

**Windows** (PowerShell) :
```
[System.Environment]::SetEnvironmentVariable("TAVILY_API_KEY","VOTRE-CLE-TAVILY-ICI","User")
```

**Ajouter `.bob/mcp.json` au `.gitignore`** si vous préférez ne pas partager la config du tout :
```
.bob/mcp.json
```

> **Stratégie hackathon recommandée** : une seule clé Tavily partagée en équipe via un message privé (Slack/WhatsApp), chacun la configure en variable d'environnement locale. Ne pas l'écrire dans le code ou le chat public.

---

## Utilisation efficace dans le chat Bob

### Syntaxe recommandée

```
Recherche web : [votre question précise]
```

Bob comprend qu'il doit utiliser Tavily. Soyez précis pour limiter le nombre de recherches (= crédits Tavily + BobCoin).

### Exemples de prompts pour le hackathon

**Défi Lallemand — Veille réglementaire :**
```
Recherche web : liste des bases de données officielles d'homologation 
de produits phytosanitaires accessibles par API ou en téléchargement 
pour le Canada (Santé Canada), les États-Unis (EPA) et l'Europe (EPPO)
```

**Défi SNCF — Données horaires :**
```
Recherche web : API open data SNCF pour horaires TER Occitanie, 
ponctualité et capacité des trains — documentation développeur
```

**Défi iMSA — Formats documents :**
```
Recherche web : formats standards des feuilles de soins et 
justificatifs de remboursement en France — spécifications techniques
```

### Limiter le coût : demander un résumé, pas une exploration

❌ **Coûteux** :
```
Recherche web sur tout ce qui existe sur les APIs de transport en France
```

✅ **Économique** :
```
Recherche web : URL de la documentation officielle de l'API SNCF 
open data pour les horaires TER
```

---

## Vérifier que Tavily fonctionne

Dans Bob, tapez :
```
Utilise Tavily pour chercher la date du dernier hackathon de La Mêlée Numérique
```

Si Bob répond avec une date sourcée et cite une URL, Tavily est opérationnel.

---

## Checklist avant le hackathon

- [ ] `uv` installé (`uvx --version` répond)
- [ ] Compte Tavily créé sur [app.tavily.com](https://app.tavily.com)
- [ ] Clé API copiée
- [ ] Variable d'environnement `TAVILY_API_KEY` définie
- [ ] `.bob/mcp.json` créé avec la config
- [ ] Bob redémarré — serveur `tavily-mcp` vert dans Settings → MCP
- [ ] Test de recherche réussi dans le chat
- [ ] `.bob/mcp.json` commité **sans la clé** (utiliser `${TAVILY_API_KEY}`)
- [ ] Clé partagée en privé avec l'équipe (pas dans le dépôt)

---

*Voir aussi : `01_bob_bobcoin.md` — gérer son budget · `02_bob_projet_equipe.md` — configuration partagée*
