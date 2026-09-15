# Ajouter la recherche web à Bob — MCP Tavily
> Fiche 03 · Hackathon IA for Impact 2026

📚 **Configuration MCP Bob** : [Using MCP in Bob](https://bob.ibm.com/docs/ide/configuration/mcp/mcp-in-bob)
📚 **Mentions URL Bob** : [Context mentions — URL mentions](https://bob.ibm.com/docs/ide/features/context-mentions#url-mentions)
📚 **Tavily MCP (officiel)** : [github.com/tavily-ai/tavily-mcp](https://github.com/tavily-ai/tavily-mcp)
📚 **Crédits Tavily** : [docs.tavily.com/documentation/api-credits](https://docs.tavily.com/documentation/api-credits)

---

## 1. Quand utiliser l'URL directe ou Tavily

Bob peut lire une page web dont tu connais l'adresse — sans Tavily, sans installation. Tavily sert à **trouver des pages** quand tu n'as pas l'URL.

| Besoin | Ce qu'il faut utiliser |
|---|---|
| Lire une page dont tu connais l'URL | `@https://url-exacte.com` dans le chat Bob |
| Trouver des pages sur un sujet (pas d'URL connue) | Recherche Tavily via Bob |
| Interroger une API métier | Appel direct avec ses paramètres et autorisations |

> 📚 La syntaxe `@url` est documentée : [Context mentions — URL mentions](https://bob.ibm.com/docs/ide/features/context-mentions#url-mentions)

### Exemples pour ce hackathon

| Besoin | Méthode |
|---|---|
| Lire la page EPPO dont tu as déjà l'URL | `@https://gd.eppo.int/...` dans Bob |
| « Quelles bases publiques existent pour les pesticides en Europe ? » | Tavily via Bob |
| Lire la doc de l'API SNCF Open Data (URL connue) | Google → URL → `@https://...` dans Bob |
| « Quels formats de justificatifs les mutuelles acceptent-elles ? » | Tavily via Bob |

---

## 2. Connecter le serveur Tavily distant

Tavily fournit un **serveur MCP distant** (Streamable HTTP) : aucune installation locale n'est nécessaire.

> ⚠️ **À tester dans Bob avant le hackathon** : la compatibilité du transport Streamable HTTP avec ta version de Bob doit être vérifiée une fois en conditions réelles.

Créer ou éditer `.bob/mcp.json` à la racine du projet :

```json
{
  "mcpServers": {
    "tavily": {
      "type": "http",
      "url": "https://mcp.tavily.com/mcp/",
      "headers": {
        "Authorization": "Bearer ${TAVILY_API_KEY}"
      }
    }
  }
}
```

> 📚 Source transport : [github.com/tavily-ai/tavily-mcp](https://github.com/tavily-ai/tavily-mcp)

---

## 3. Configurer son authentification

### Créer un compte Tavily

1. Aller sur [app.tavily.com](https://app.tavily.com)
2. S'inscrire (email ou GitHub)
3. Copier la clé API : format `tvly-xxxxxxxxxxxxxxxx`

### Définir la variable d'environnement localement

La valeur `${TAVILY_API_KEY}` dans `mcp.json` est une substitution — Bob lit la variable d'environnement au démarrage. **Ne jamais inscrire la clé en dur dans le fichier.**

**macOS / Linux** — ajouter dans `~/.zshrc` ou `~/.bashrc` :
```bash
export TAVILY_API_KEY="tvly-VOTRE-CLE-ICI"
```
Puis relancer le terminal. **Note** : si Bob est lancé depuis le Finder (pas depuis un terminal), la variable peut ne pas être disponible. Dans ce cas, ouvrir Bob depuis un terminal avec `bob .` après avoir sourcé `.zshrc`.

**Windows** (PowerShell) :
```powershell
[System.Environment]::SetEnvironmentVariable("TAVILY_API_KEY","tvly-VOTRE-CLE-ICI","User")
```
Puis redémarrer Bob.

### Ce qui va dans Git — sans la clé

Commiter `.bob/mcp.json` uniquement avec `${TAVILY_API_KEY}`, jamais avec la clé réelle. Ajouter au `.gitignore` si tu préfères ne pas partager la config du tout :

```
.bob/mcp.json
```

> 📚 Voir aussi : [Understanding MCP — identifiants](https://bob.ibm.com/docs/ide/configuration/mcp/understanding-mcp)

### Partage en équipe

Chaque membre crée son propre compte Tavily (plan gratuit : 1 000 crédits/mois). Si l'équipe préfère une clé unique partagée, désigner un responsable qui gère le quota et partager la clé en message privé — jamais dans le dépôt ni dans le chat.

---

## 4. Effectuer un test observable

Un test fiable doit vérifier deux choses séparément :

**Étape 1 — Le serveur est connecté**
Aller dans **Settings → MCP** : le serveur `tavily` doit afficher un statut vert et lister ses outils (ex. `tavily_search`).

**Étape 2 — L'outil est réellement appelé**
Dans le chat Bob :

```
Utilise l'outil Tavily pour chercher : quels formats de documents 
accepte la MSA pour les remboursements de soins en France ?
Indique le titre exact des pages trouvées, leur URL officielle, 
les conditions d'accès (libre / inscription / payant) 
et ce que la recherche n'a pas permis de confirmer.
```

Un test réussi montre :
- un appel à l'outil `tavily_search` visible dans la conversation ;
- des résultats avec titres et URLs ;
- une mention explicite de ce qui reste incertain.

> Une réponse avec un lien ne prouve pas que Tavily a été utilisé — c'est l'appel d'outil visible qui le confirme.

---

## 5. Comprendre les deux compteurs et limiter les recherches

### Les deux compteurs

| Compteur | Ce qu'il mesure | Où le voir |
|---|---|---|
| **BobCoin** | Traitement Bob (tokens en entrée et sortie) | Fiche 01 |
| **Crédits Tavily** | Appels aux services Tavily | [app.tavily.com](https://app.tavily.com) |

Ces deux compteurs sont **indépendants**. Lire le résultat d'une recherche Tavily consomme aussi des tokens Bob (le texte retourné entre dans la fenêtre de contexte).

### Tarification Tavily (plan gratuit)

- **1 000 crédits/mois** offerts
- Recherche `basic` : **1 crédit**
- Recherche `advanced` : **2 crédits**

> 📚 Source : [docs.tavily.com/documentation/api-credits](https://docs.tavily.com/documentation/api-credits)

### Prompts économiques

Demander une URL ou un titre plutôt qu'une synthèse réduit le nombre de recherches.

❌ Coûteux :
```
Recherche web sur tout ce qui existe sur les APIs de transport en France
```

✅ Économique :
```
Recherche Tavily : URL de la documentation officielle de l'API SNCF 
open data pour les horaires TER — titre exact et lien direct
```

### Exemples de prompts pour le hackathon

**Défi Lallemand — Veille réglementaire :**
```
Recherche Tavily : bases de données officielles d'homologation de produits 
phytosanitaires accessibles par API ou téléchargement pour le Canada 
(Santé Canada), les États-Unis (EPA) et l'Europe (EPPO).
Pour chaque source : titre officiel, URL, conditions d'accès, 
et ce que la recherche n'a pas pu confirmer.
```

**Défi SNCF — Données horaires :**
```
Recherche Tavily : documentation développeur de l'API open data SNCF 
pour horaires TER Occitanie — URL officielle et conditions d'accès.
```

**Défi iMSA — Formats documents :**
```
Recherche Tavily : spécifications techniques des feuilles de soins 
et justificatifs de remboursement MSA en France — source officielle et URL.
```

---

## Checklist avant le hackathon

- [ ] Compte Tavily créé sur [app.tavily.com](https://app.tavily.com)
- [ ] Clé API `tvly-…` copiée
- [ ] Variable d'environnement `TAVILY_API_KEY` définie (et Bob ouvert depuis un terminal)
- [ ] `.bob/mcp.json` créé avec la config du serveur distant
- [ ] Bob redémarré — serveur `tavily` vert dans Settings → MCP, outils visibles
- [ ] Test d'appel d'outil réussi (appel `tavily_search` visible dans la conversation)
- [ ] `.bob/mcp.json` commité **sans la clé** (valeur `${TAVILY_API_KEY}`)

---

*Voir aussi : `01_bob_bobcoin.md` — gérer son budget · `02_bob_projet_equipe.md` — configuration partagée*
