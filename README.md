# Hackathon IA for Impact 2026 — Fiches IBM Bob

> **Ressources pratiques pour utiliser IBM Bob efficacement pendant les 30 heures de hackathon**  
> La Mêlée Numérique · Toulouse · 9–10 octobre 2026

---

## Présentation

Ce dépôt contient **10 fiches de référence** pour utiliser [IBM Bob](https://bob.ibm.com) — l'assistant IA de développement d'IBM — lors du **Hackathon IA for Impact 2026**.

Chaque fiche est conçue pour être opérationnelle immédiatement : prompts prêts à l'emploi, checklists de sortie, gabarits de validation. Elles sont organisées pour une équipe de **4–5 personnes** disposant d'un budget de **~50 BobCoins par personne** sur les 30 heures.

**Structure du hackathon couverte :**

```
Avant Ven 17h  →  Étape 0 : Pré-hackathon (fiches 00–04)
Ven 17h–22h    →  Étape 1 : Cadrage (fiche 05)
Ven 22h–Sam 2h →  Étape 2 : Architecture & setup (fiche 06)
Sam 2h–7h      →  Étape 3 : Production nocturne (fiche 07)
Sam 7h–13h     →  Étape 4 : Finalisation & code freeze (fiche 08)
Sam 13h–17h    →  Étape 5 : Pitch & démo (fiche 09)
```

---

## Les 10 fiches

| # | Fiche | Sujet | Timing |
|---|-------|-------|--------|
| 00 | [C'est quoi Bob ?](00_bob_intro.md) | Introduction, les 3 modes, les outils natifs, `/init` | Avant le hackathon |
| 01 | [Les BobCoin](01_bob_bobcoin.md) | Budget, stratégie Ask→Plan→Agent, les 5 erreurs à éviter | Tout le hackathon |
| 02 | [Bob en équipe](02_bob_projet_equipe.md) | `/init`, `AGENTS.md`, `.bob/rules/`, configuration partagée Git | Ven 22h (setup) |
| 03 | [MCP Tavily — recherche web](03_bob_mcp_web.md) | Ajouter la recherche web à Bob via MCP Tavily | Avant le hackathon |
| 04 | [Étape 0 — Pré-hackathon](04_hack_etape0_prephackathon.md) | Préparer l'environnement, analyser les défis, préparer les questions sponsors | Avant Ven 17h |
| 05 | [Étape 1 — Cadrage](05_hack_etape1_cadrage.md) | Comprendre le défi, formuler le MVP, répartir les rôles | Ven 17h → 22h |
| 06 | [Étape 2 — Architecture & setup](06_hack_etape2_setup.md) | Architecture, dépôt, squelette de projet, tâches attribuées | Ven 22h → Sam 2h |
| 07 | [Étape 3 — Production nocturne](07_hack_etape3_production.md) | Développement par briques, mocks, déblocage ciblé | Sam 2h → 7h |
| 08 | [Étape 4 — Finalisation](08_hack_etape4_finalisation.md) | Code freeze à 13h, démo stable, README, test sur device final | Sam 7h → 13h |
| 09 | [Étape 5 — Pitch](09_hack_etape5_pitch.md) | Script oral, questions jury, répétitions, plan de secours | Sam 13h → 17h |

---

## Résumé de chaque fiche

### [Fiche 00 — C'est quoi Bob ?](00_bob_intro.md)

IBM Bob est un **agent IA de développement** qui agit directement dans votre projet : il lit vos fichiers, écrit du code, exécute des commandes et peut utiliser des outils externes via MCP — le tout depuis une interface de chat.

**Points clés :**
- **3 modes** : `Ask` (questions, 0 fichier modifié), `Plan` (réflexion/architecture, 0 fichier modifié), `Agent` (écriture et exécution réelle)
- **Différence clé** vs Copilot/Claude : Bob lit, modifie et exécute *nativement*, sans plugin IDE
- **`/init`** : commande gratuite (0 BobCoin) à lancer en premier sur tout nouveau projet — génère `AGENTS.md` et `.bob/`
- **Règle d'or** : Ask → Plan → Agent. Ne passer en Agent que quand on sait exactement ce que l'on veut

---

### [Fiche 01 — Les BobCoin](01_bob_bobcoin.md)

Les BobCoins sont la métrique de consommation transparente de Bob. Chaque token (mots en entrée + contexte + réponse) se convertit en BobCoins.

**Points clés :**
- 🔴 **Élevé** : mode Agent sur un gros fichier, conversations longues, prompts vagues
- 🟡 **Moyen** : mode Plan, mode Agent ciblé
- 🟢 **Faible** : mode Ask avec question courte
- ⚪ **Gratuit** : `/init`, `.bob/rules/`, `AGENTS.md`, ouvrir une nouvelle conversation (`+`)
- **Budget recommandé** : 43–50 coins/personne sur 30h (+ 5–12 de réserve non négociable)
- **Les 5 erreurs à éviter** : conversation fleuve, demander à Bob de lire tout le projet, prompt vague, Agent pour une question, ne pas partager les réponses utiles

---

### [Fiche 02 — Bob en équipe](02_bob_projet_equipe.md)

Sans configuration partagée, chaque membre de l'équipe reçoit des réponses différentes et doit réexpliquer le contexte à chaque conversation. La solution : un dossier `.bob/` versionné dans Git.

**Points clés :**
- **`/init`** génère automatiquement `AGENTS.md` + fichiers de contexte dans `.bob/`
- **`.bob/rules/`** : fichiers Markdown lus automatiquement à chaque conversation (0 BobCoin)
  - `01_stack.md` — conventions de code et stack technique
  - `02_langue.md` — langue de réponse, ton, format
  - `03_equipe.md` — rôles, périmètres, conventions Git
- **`.bob/mcp.json`** : configuration des MCPs partagée avec toute l'équipe
- Règles projet > règles personnelles (`~/.bob/rules/`)
- **Checklist** avant de démarrer le hacking : `/init` fait, rules créées, MCP configuré, tout commité et pushé, chaque membre a cloné

---

### [Fiche 03 — MCP Tavily — recherche web](03_bob_mcp_web.md)

Bob n'a aucun accès réseau par défaut. Le MCP Tavily connecte Bob à un moteur de recherche web optimisé pour les agents IA.

**Points clés :**
- **Option A (recommandée)** : compte Tavily gratuit sur [app.tavily.com](https://app.tavily.com) → 1 000 crédits/mois
- **Configuration** : `uvx` (via `uv`) + fichier `.bob/mcp.json` avec `${TAVILY_API_KEY}` (jamais en dur)
- **Règle d'or** : si tu connais déjà l'URL, utilise `@https://...` dans le chat plutôt que Tavily (moins coûteux)
- **Ne jamais commiter la clé API** : utiliser une variable d'environnement locale
- **Vérification** : serveur `tavily-mcp` vert dans Settings → MCP de Bob

---

### [Fiche 04 — Étape 0 : Pré-hackathon](04_hack_etape0_prephackathon.md)

*Timing : avant vendredi 9 octobre 17h*

Arriver au lancement avec un environnement fonctionnel et des questions utiles préparées pour les sponsors.

**Points clés :**
- Bob ouvert, testé en mode Ask, MCP web opérationnel
- Pour chaque défi : identifier utilisateur, problème, données disponibles, contraintes, 3 questions au sponsor
- **Prompt générique** d'analyse des documents de défi inclus (mode Ask)
- **Ne pas choisir de solution trop tôt** — analyser d'abord, décider à l'étape 1
- Checklist de sortie : 7 points (Bob testé, MCP vérifié, stack connue, questions prêtes, wireframe choisi, aucun secret dans Git, solde BobCoin vérifié)

---

### [Fiche 05 — Étape 1 : Cadrage](05_hack_etape1_cadrage.md)

*Timing : vendredi 17h → 22h*

Comprendre le besoin avec le sponsor, choisir un défi et formuler un MVP démontrable en 20 heures.

**Points clés :**
- **Format MVP** : *"Pour [utilisateur], qui rencontre [problème], nous construisons [fonction unique] afin de [résultat observable], démontrée sur [cas de démonstration]."*
- **Modes** : Ask pour clarifier le brief, Plan pour comparer les options
- **Prompt générique** de cadrage inclus : 3 MVP comparés, chacun évalué sur faisabilité en 20h
- **Gabarit de validation** : liste de contrôle avant de passer à l'architecture (MVP retenu, scénario de démo, chemin de secours avec données fictives)
- Ne pas commencer l'implémentation avant que l'équipe sache répondre à « quoi, pour qui, comment le démontrer »

---

### [Fiche 06 — Étape 2 : Architecture & setup](06_hack_etape2_setup.md)

*Timing : vendredi 22h → samedi 2h*

Obtenir un dépôt qui démarre, une architecture décidée, des écrans esquissés et des tâches distribuées. Objectif : que ça *démarre* — pas que ça soit fonctionnel.

**Points clés :**
- Décision d'architecture limitée à **30 minutes**
- Lancer `/init` dans Bob dès le dépôt créé
- **Prompt d'architecture** (mode Plan) + **prompt d'implémentation** (mode Agent) inclus
- **Squelette uniquement** : les collecteurs de données réels et fonctionnalités avancées sont pour l'étape 3
- Prévoir un chemin de démo sans données réelles (JSON local ou mock statique)
- **Critère de succès** : le projet démarre avec une commande et affiche quelque chose

---

### [Fiche 07 — Étape 3 : Production nocturne](07_hack_etape3_production.md)

*Timing : samedi 2h → 7h*

Obtenir un prototype qui fonctionne sur le parcours principal, même incomplet.

**Points clés :**
- Coder par **briques indépendantes et testables**, intégrer tôt
- **Checkpoint** de 10 minutes toutes les 2 heures
- **Priorité absolue** : générer les données mock *avant* tout autre développement — elles garantissent une démo stable même si les collecteurs réels ne fonctionnent pas à 13h
- **Prompt de mock** inclus (3 cas : nominal, champ manquant, décision humaine requise)
- **Prompt de déblocage** ciblé : donner fichier + erreur exacte + résultat attendu
- Gérer la fatigue : une personne bloquée depuis longtemps passe le relais plutôt que de dégrader le prototype

---

### [Fiche 08 — Étape 4 : Finalisation & code freeze](08_hack_etape4_finalisation.md)

*Timing : samedi 7h → 13h · Code freeze à 13h*

Transformer le prototype nocturne en démonstration fiable et reproductible. Après 13h : **aucune nouvelle fonctionnalité**.

**Points clés :**
- Stabiliser le parcours principal, arrêter les fonctionnalités secondaires
- **Prompt de revue de démo** ciblé inclus : corrige uniquement ce qui empêche le parcours de fonctionner
- **Prompt de README** inclus : installe + configure + lance + distingue données réelles/mock/limites
- Tester sur le **device de présentation**, pas seulement sur le poste de développement
- **Commit de code freeze** à 13h — tag ou commit identifiable
- Critères jury officiels : impact, faisabilité, viabilité, niveau de réalisation du prototype

---

### [Fiche 09 — Étape 5 : Pitch](09_hack_etape5_pitch.md)

*Timing : samedi 13h → 17h · Time to Pitch à 17h*

Présenter une solution compréhensible, crédible et démontrable devant le jury en 4 heures de préparation.

**Points clés :**
- **Structure recommandée** : Problème → Solution → Démo → Impact & viabilité → Équipe
- **Prompt de script oral** inclus (mode Ask) : factuel, séparant résultats démontrés / hypothèses / à faire
- **Prompt de questions jury** inclus : 10 questions difficiles sur impact, faisabilité, données, limites, sécurité
- Répéter **au moins 3 fois** avec le même appareil et les mêmes données
- Ne jamais présenter une projection comme un résultat obtenu
- Préparer un **plan de secours** (vidéo ou scénario alternatif)

---

## Comment utiliser ces fiches

### Ordre recommandé

1. **Avant le hackathon** : lire les fiches 00, 01, 02, 03 et 04
2. **Vendredi 17h** : ouvrir la fiche 05 (cadrage)
3. **Vendredi 22h** : ouvrir la fiche 06 (setup) — avoir déjà fait `/init`
4. **Samedi 2h** : ouvrir la fiche 07 (production) — avoir les mocks en priorité
5. **Samedi 7h** : ouvrir la fiche 08 (finalisation) — viser le code freeze à 13h
6. **Samedi 13h** : ouvrir la fiche 09 (pitch)

### Principe d'utilisation

Chaque fiche contient :
- Un **objectif** et des **livrables attendus** à l'heure de sortie
- Des **prompts prêts à copier-coller** dans Bob
- Un **gabarit de validation** pour vérifier que la sortie de Bob est exploitable
- Une **checklist de sortie** avant de passer à l'étape suivante

> **Règle des modes** : Ask pour comprendre, Plan pour décider, Agent pour faire. Dans cet ordre. Voir fiche 01 pour le budget.

---

## Ressources

- [IBM Bob — Documentation officielle](https://bob.ibm.com/docs/ide)
- [BobCoins — Comprendre le budget](https://bob.ibm.com/docs/ide/account/bobcoins)
- [MCP dans Bob](https://bob.ibm.com/docs/ide/features/mcp/using-mcp-in-bob)
- [Démarrer un projet avec /init](https://bob.ibm.com/docs/ide/getting-started/tutorials/start-a-project)
- [Tavily — Recherche web pour agents IA](https://tavily.com)

---

*Hackathon IA for Impact 2026 · La Mêlée Numérique · Toulouse · 9–10 octobre 2026*
