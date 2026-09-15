# Les BobCoin — Gérer son budget sur 24h
> Fiche 01 · Hackathon IA for Impact 2026

📚 **Doc officielle** : [BobCoins — IBM Bob](https://bob.ibm.com/docs/ide/account/bobcoins)

---

## C'est quoi un BobCoin ?

> *"Bobcoins are the consumption-based billing metric used for Bob plans. They provide a transparent, predictable way to measure and bill for your Bob usage."*
> — [Documentation IBM Bob](https://bob.ibm.com/docs/ide/account/bobcoins)

Sous le capot, Bob utilise des **tokens** — les unités de traitement des modèles de langage. Chaque mot que vous écrivez, chaque fichier que Bob lit, chaque réponse qu'il génère consomme des tokens. Les BobCoin mesurent les ressources consommées, dont les tokens — avec des différences selon les modèles et les opérations.

```
Votre prompt         →  tokens en entrée  ┐
Contexte (fichiers,  →  tokens en entrée  ├─→  BobCoin consommés
  historique, rules) →  tokens en entrée  │
Réponse de Bob       →  tokens en sortie  ┘
```

> 📚 Doc : [Bobcoins — comprendre la consommation](https://bob.ibm.com/docs/ide/account/bobcoins#understanding-bobcoins)

---

## Ce qui consomme des BobCoin

### 🔴 Consommation élevée
- **Mode Agent sur un gros fichier** : Bob peut lire des fichiers entiers si le contexte l'exige
- **Conversations longues** : le contexte actif est renvoyé au modèle à chaque message, et grossit avec le temps
- **Prompts vagues qui nécessitent plusieurs allers-retours** : chaque échange coûte
- **Demander à Bob de lire toute la codebase** sans cibler un fichier précis

### 🟡 Consommation moyenne
- **Mode Plan** : réflexion et conception, la réponse peut être longue
- **Mode Agent sur un fichier ciblé** : Bob peut lire des plages de lignes et faire des recherches ciblées
- **Correction de bug avec contexte précis** : efficace si le bug est bien décrit

### 🟢 Consommation faible
- **Mode Ask avec question courte** : réponse directe — *attention, un prompt court accompagné d'un contexte déjà volumineux reste coûteux*
- **Demande de génération de texte simple** : le coût dépend du contexte chargé et de la longueur du résultat

### ⚪ Coûte peu, apporte beaucoup
- **`/init`** — génère l'`AGENTS.md` : un investissement de quelques coins qui structure toute la session
- **`.bob/rules/`** — instructions projet chargées automatiquement : à rédiger dense et court pour un coût minimal
- **`AGENTS.md`** — contexte projet permanent : bien rédigé une fois, réutilisé à chaque conversation
- **Ouvrir une nouvelle conversation** (`+`) — repart d'un contexte vide, sans l'historique accumulé

> 💡 Ces éléments ont un coût de contexte faible **si on les garde concis**. Un `AGENTS.md` de 500 lignes ou des `rules/` verbeux se retrouvent dans chaque requête et consomment à chaque échange.

> 📚 Doc contexte : [Context window management](https://bob.ibm.com/docs/ide/core-concepts/context-window-management)

---

## La règle d'or : Ask → Plan → Agent

Pour quelqu'un qui découvre l'outil, cet ordre est **le plus naturellement économique** — il évite de lancer des actions coûteuses avant d'avoir clarifié le besoin.

```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│   💬 ASK          🗺️ PLAN          🤖 AGENT                │
│   "Est-ce que  →  "Voilà le    →  "Fais exactement         │
│   cette archi     plan précis"    ce plan"                  │
│   tient ?"                                                  │
│                                                             │
│   Peu de coins    Coins moyens     Coins élevés             │
│   Aucun fichier   Modifications    Modifie les fichiers     │
│   modifié         limitées                                   │
└─────────────────────────────────────────────────────────────┘
```

### Pourquoi cet ordre ?

**Sans Plan, Agent part dans la mauvaise direction.** À titre d'exemple : corriger une mauvaise implémentation peut coûter 3× plus cher que de l'avoir planifiée correctement. Un aller-retour en Agent (implémenter → constater que c'est faux → réimplémenter) peut consommer 15–20 coins là où un Plan de ~3 coins aurait évité l'erreur.

> *Ces chiffres sont illustratifs — la consommation réelle dépend du contexte, du modèle et de la complexité de la tâche.*

En pratique, l'objectif est : **choisir le mode adapté, fournir le contexte pertinent et vérifier le résultat avant de poursuivre.**

> 📚 Doc : [Modes disponibles](https://bob.ibm.com/docs/ide/features/modes)

### Exemple concret

❌ **Approche sans plan** (risque de gaspillage) :
```
[Agent] "Crée-moi une API FastAPI avec authentification, 
         base de données PostgreSQL, gestion des rôles et 
         envoi d'emails"
→ Bob génère quelque chose, vous réalisez que l'archi ne convient pas
→ Vous redemandez, Bob régénère
→ Exemple : 3 allers-retours ≈ ~30 coins pour un résultat insatisfaisant
```

✅ **Approche planifiée** :
```
[Ask]   "Quels sont les trade-offs entre JWT et sessions 
         pour notre API hackathon ?" → ~2 coins
[Plan]  "Conçois l'architecture de l'API : endpoints, 
         modèles, auth — priorité simplicité démo" → ~4 coins
[Agent] "Implémente exactement ce plan dans /backend/api.py" → ~8 coins
         Exemple : total ~14 coins, résultat aligné dès le premier essai
```

> *Ces montants sont des exemples destinés à illustrer l'écart potentiel, pas des valeurs garanties.*

---

## Budget indicatif sur les 24h

*Si chaque membre dispose de 50 coins — **à vérifier sur votre compte hackathon**. Les enveloppes individuelles ne sont pas nécessairement transférables entre membres.*

| Étape | Timing | Coins/personne | Mode principal | Ce qu'on fait avec Bob |
|---|---|---|---|---|
| **0 — Pré-hackathon** | Avant Ven 17h | 2–3 | Ask | Lire les défis, préparer les questions |
| **1 — Cadrage** | Ven 17h–22h | 5–8 | Ask → Plan | Analyser le défi, définir le MVP, choisir l'archi |
| **2 — Setup** | Ven 22h–Sam 2h | 8–10 | Plan → Agent | Générer la structure du projet, config de base |
| **3 — Production** | Sam 2h–7h | 10–12 | Agent | Composants, pipeline IA, corrections de bugs |
| **4 — Finalisation** | Sam 7h–13h | 8–10 | Agent | Mock data, intégration, README |
| **5 — Pitch** | Sam 13h–17h | 5–7 | Ask → Agent | Plan slides, script pitch, réponses jury |
| **Réserve** | — | 5–12 | — | Imprévus, bugs bloquants |
| **Total** | | **43–62** | | |

> ⚠️ Le scénario haut (62 coins) peut dépasser une enveloppe individuelle de 50. Dans ce cas : réduire la réserve, mutualiser davantage les requêtes, ou ajuster les étapes les plus consommatrices.
>
> La réserve de 5–12 coins est **fortement recommandée**. Les imprévus dans un hackathon ne sont pas optionnels.

> *Ces fourchettes sont indicatives. Ajustez-les aux consommations réellement observées au fil de l'événement.*

---

## Stratégie d'équipe : qui dépense quoi

### Principe : un coin dépensé profite à toute l'équipe

Évitez que 4 personnes posent la même question à Bob en parallèle. Désignez **une personne par sujet** :

| Rôle | Utilisation de Bob | Budget indicatif |
|---|---|---|
| **Lead Dev** | Architecture, intégration, bugs bloquants | 40–50 coins |
| **Dev IA/Data** | Pipeline IA, prompts, parsing données | 40–50 coins |
| **UI/UX** | Génération de composants front, wireframes → code | 30–40 coins |
| **PM/Pitcher** | Analyse défi, plan slides, script pitch | 20–30 coins |
| **Généraliste** | Renfort où ça bloque, documentation | 20–30 coins |

> *Ces budgets par rôle sont des ordres de grandeur pour guider les priorités — pas des allocations fixes. L'allocation exacte dépend de votre offre hackathon.*

### Règle de mutualisation
> Si deux personnes ont la même question → **une seule pose la question**, partage la réponse dans le chat d'équipe.

---

## Les 5 erreurs qui augmentent inutilement la consommation

### ❌ Erreur 1 — Conversation fleuve
Garder la même conversation pendant 6h. Le contexte actif grossit, chaque message coûte de plus en plus cher.
**Fix** : ouvrir une nouvelle conversation (`+`) dès qu'on change de sujet ou de tâche. Avant de fermer, noter dans le chat d'équipe les décisions prises, les fichiers importants et ce qui reste à faire.

> 📚 Doc : [Create a new context window](https://bob.ibm.com/docs/ide/getting-started/tutorials/context-window)

### ❌ Erreur 2 — Demander à Bob de lire tout le projet
`"Regarde tout mon code et dis-moi ce qui ne va pas"` — Bob charge tout, ça coûte énorme.
**Fix** : cibler le fichier ou la fonction précise. `"Dans /backend/api.py ligne 45, pourquoi cette erreur ?"`.

### ❌ Erreur 3 — Prompt vague → réponse ratée → recommencer
Un prompt imprécis génère une réponse inexacte, vous recorrigez, Bob régénère. Chaque aller-retour coûte.
**Fix** : 2 minutes à formuler un prompt précis peuvent économiser plusieurs allers-retours et une bonne dizaine de coins — *à titre d'exemple*.

### ❌ Erreur 4 — Utiliser Agent pour une question
`"[Agent] Explique-moi comment fonctionne OAuth"` — Agent charge tout le contexte projet pour répondre à une question qui n'en a pas besoin.
**Fix** : Ask pour les questions, Agent pour les actions.

### ❌ Erreur 5 — Ne pas partager les réponses utiles
Bob répond brillamment à une question d'architecture → la réponse reste dans le chat d'une seule personne.
**Fix** : copier les **décisions validées** dans un fichier `docs/bob-notes.md` commité. Toute l'équipe en profite, personne ne repose la même question.

---

## Vérifier son solde

Votre solde BobCoin est visible dans **Settings → General**. D'autres indicateurs de consommation sont disponibles dans le panneau Bob et dans **Bobalytics**. Consultez-le à chaque début d'étape pour ajuster votre stratégie si vous avez pris du retard sur le budget.

> 📚 Doc : [Suivi de consommation](https://bob.ibm.com/docs/ide/account/bobcoins#monitoring-your-usage)

---

*Voir aussi : [`00_bob_intro.md`](00_bob_intro.md) — c'est quoi Bob · [`02_bob_projet_equipe.md`](02_bob_projet_equipe.md) — configuration partagée*
