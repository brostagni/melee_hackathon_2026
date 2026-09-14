# Les BobCoin — Gérer son budget sur 30h
> Fiche 01 · Hackathon IA for Impact 2026

📚 **Doc officielle** : [BobCoins — IBM Bob](https://bob.ibm.com/docs/ide/account/bobcoins)

---

## C'est quoi un BobCoin ?

> *"Bobcoins are the consumption-based billing metric used for Bob plans. They provide a transparent, predictable way to measure and bill for your Bob usage."*
> — [Documentation IBM Bob](https://bob.ibm.com/docs/ide/account/bobcoins)

Sous le capot, Bob utilise des **tokens** — les unités de traitement des modèles de langage. Chaque mot que vous écrivez, chaque fichier que Bob lit, chaque réponse qu'il génère consomme des tokens. Les BobCoin sont la conversion de ces tokens en unité de budget compréhensible.

```
Votre prompt         →  tokens en entrée  ┐
Contexte (fichiers,  →  tokens en entrée  ├─→  BobCoin consommés
  historique, rules) →  tokens en entrée  │
Réponse de Bob       →  tokens en sortie  ┘
```

> 📚 Doc : [Bobcoins vs tokens](https://bob.ibm.com/docs/ide/account/bobcoins#understanding-bobcoins)

---

## Ce qui consomme des BobCoin

### 🔴 Consommation élevée
- **Mode Agent sur un gros fichier** : Bob lit tout le fichier avant de modifier
- **Conversations longues** : l'historique entier est relu à chaque message
- **Prompts vagues qui nécessitent plusieurs allers-retours** : chaque échange coûte
- **Demander à Bob de lire toute la codebase** sans cibler un fichier précis

### 🟡 Consommation moyenne
- **Mode Plan** : réflexion sans écriture de fichiers, mais la réponse peut être longue
- **Mode Agent sur un fichier ciblé** : Bob ne lit que ce qu'il faut
- **Correction de bug avec contexte précis** : efficace si le bug est bien décrit

### 🟢 Consommation faible
- **Mode Ask avec question courte** : réponse directe, peu de contexte
- **Demande de génération de texte simple** (ex : rédiger un README)

### ⚪ Ne coûte PAS de BobCoin
- La commande **`/init`** — génération de AGENTS.md
- Les fichiers **`.bob/rules/`** — lus automatiquement comme instructions système
- **`AGENTS.md`** — contexte projet permanent
- Ouvrir une **nouvelle conversation** (bouton `+`)

> 📚 Doc contexte : [Context window management](https://bob.ibm.com/docs/ide/core-concepts/context-window-management)

---

## La règle d'or : Ask → Plan → Agent

C'est **l'ordre qui économise le plus de BobCoin** et produit les meilleurs résultats.

```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│   💬 ASK          🗺️ PLAN          🤖 AGENT                │
│   "Est-ce que  →  "Voilà le    →  "Fais exactement         │
│   cette archi     plan précis"    ce plan"                  │
│   tient ?"                                                  │
│                                                             │
│   Peu de coins    Coins moyens     Coins élevés             │
│   Aucun fichier   Aucun fichier    Modifie les fichiers     │
│   modifié         modifié                                   │
└─────────────────────────────────────────────────────────────┘
```

### Pourquoi cet ordre ?

**Sans Plan, Agent part dans la mauvaise direction.** Corriger une mauvaise implémentation coûte 3× plus cher que de l'avoir planifiée correctement. Un aller-retour en Agent (implémenter → constater que c'est faux → réimplémenter) peut consumer 15–20 coins là où un Plan de 3 coins aurait évité l'erreur.

### Exemple concret

❌ **Mauvaise approche** (gaspillage) :
```
[Agent] "Crée-moi une API FastAPI avec authentification, 
         base de données PostgreSQL, gestion des rôles et 
         envoi d'emails"
→ Bob génère quelque chose, vous réalisez que l'archi ne convient pas
→ Vous redemandez, Bob régénère
→ 3 allers-retours = ~30 coins pour un résultat insatisfaisant
```

✅ **Bonne approche** (économique) :
```
[Ask]   "Quels sont les trade-offs entre JWT et sessions 
         pour notre API hackathon ?" → 2 coins
[Plan]  "Conçois l'architecture de l'API : endpoints, 
         modèles, auth — priorité simplicité démo" → 4 coins
[Agent] "Implémente exactement ce plan dans /backend/api.py" → 8 coins
         Total : 14 coins, résultat aligné dès le premier essai
```

---

## Budget recommandé sur les 30h

*Pour une équipe de 4–5 personnes, 50 coins/personne = 200–250 coins au total.*

| Étape | Timing | Coins/personne | Mode principal | Ce qu'on fait avec Bob |
|---|---|---|---|---|
| **0 — Pré-hackathon** | Avant Ven 17h | 2–3 | Ask | Lire les défis, préparer les questions |
| **1 — Cadrage** | Ven 17h–22h | 5–8 | Ask → Plan | Analyser le défi, définir le MVP, choisir l'archi |
| **2 — Setup** | Ven 22h–Sam 2h | 8–10 | Plan → Agent | Générer la structure du projet, config de base |
| **3 — Production** | Sam 2h–7h | 10–12 | Agent | Composants, pipeline IA, corrections de bugs |
| **4 — Finalisation** | Sam 7h–13h | 8–10 | Agent | Mock data, intégration, README |
| **5 — Pitch** | Sam 13h–17h | 5–7 | Ask → Agent | Plan slides, script pitch, réponses jury |
| **Réserve** | — | 5–12 | — | Imprévus, bugs bloquants |
| **Total** | | **43–50** | | |

> La réserve de 5–12 coins est **non négociable**. Les imprévus dans un hackathon ne sont pas optionnels.

---

## Stratégie d'équipe : qui dépense quoi

### Principe : un coin dépensé profite à toute l'équipe

Évitez que 4 personnes posent la même question à Bob en parallèle. Désignez **une personne par sujet** :

| Rôle | Utilisation de Bob | Budget estimé |
|---|---|---|
| **Lead Dev** | Architecture, intégration, bugs bloquants | 40–50 coins |
| **Dev IA/Data** | Pipeline IA, prompts, parsing données | 40–50 coins |
| **UI/UX** | Génération de composants front, wireframes → code | 30–40 coins |
| **PM/Pitcher** | Analyse défi, plan slides, script pitch | 20–30 coins |
| **Généraliste** | Renfort où ça bloque, documentation | 20–30 coins |

### Règle de mutualisation
> Si deux personnes ont la même question → **une seule pose la question**, partage la réponse dans le chat d'équipe.

---

## Les 5 erreurs qui ruinent un budget en 2h

### ❌ Erreur 1 — Conversation fleuve
Garder la même conversation pendant 6h. L'historique grossit, chaque message coûte de plus en plus cher.
**Fix** : ouvrir une nouvelle conversation (`+`) dès qu'on change de sujet ou de tâche.

> 📚 Doc : [Create a new context window](https://bob.ibm.com/docs/ide/getting-started/tutorials/context-window)

### ❌ Erreur 2 — Demander à Bob de lire tout le projet
`"Regarde tout mon code et dis-moi ce qui ne va pas"` — Bob lit tout, ça coûte énorme.
**Fix** : cibler le fichier ou la fonction précise. `"Dans /backend/api.py ligne 45, pourquoi cette erreur ?"`.

### ❌ Erreur 3 — Prompt vague → réponse ratée → recommencer
Un prompt imprécis génère une réponse inexacte, vous recorrigez, Bob régénère. Chaque aller-retour coûte.
**Fix** : passer 2 minutes à formuler un prompt précis économise 10 minutes et 15 coins de corrections.

### ❌ Erreur 4 — Utiliser Agent pour une question
`"[Agent] Explique-moi comment fonctionne OAuth"` — Agent charge tout le contexte projet pour répondre à une question qui n'en a pas besoin.
**Fix** : Ask pour les questions, Agent pour les actions.

### ❌ Erreur 5 — Ne pas partager les réponses utiles
Bob répond brillamment à une question d'architecture → la réponse reste dans le chat d'une seule personne.
**Fix** : copier les réponses importantes dans un fichier `docs/bob-notes.md` commité. Toute l'équipe en profite, personne ne repose la même question.

---

## Vérifier son solde

Votre solde BobCoin est visible dans les **Settings** de Bob. Consultez-le à chaque début d'étape pour ajuster votre stratégie si vous avez pris du retard sur le budget.

> 📚 Doc : [Increasing your Bobcoin budget](https://bob.ibm.com/docs/ide/account/bobcoins#increasing-your-bobcoin-budget)

---

*Voir aussi : `00_bob_intro.md` — c'est quoi Bob · `02_bob_projet_equipe.md` — configuration partagée*
