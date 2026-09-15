# Étape 0 — Pré-hackathon
> Fiche 04 · Hackathon IA for Impact 2026 · Avant vendredi 9 octobre, 17h

📚 **Programme et timing** : [`methodologie_hackathon_ia_for_impact.md`](../Méthodologie/methodologie_hackathon_ia_for_impact.md) · [`Hackathon IA for Impact _ 30h de challenge IA.pdf`](../Organisation/Hackathon%20IA%20for%20Impact%20_%2030h%20de%20challenge%20IA.pdf)

## 1. Objectif

Arriver au lancement avec un environnement fonctionnel et des questions utiles. Le temps de hackathon commence vendredi 9 octobre à 17h. Ce qui doit être prêt avant ce créneau : Bob fonctionnel, Git installé, accès GitHub testé, documents disponibles, questions préparées. Les dépendances du projet, les accès aux données et les outils spécifiques seront organisés après le choix du défi. 📚 [`Hackathon IA for Impact _ 30h de challenge IA.pdf`](../Organisation/Hackathon%20IA%20for%20Impact%20_%2030h%20de%20challenge%20IA.pdf)

## 2. Livrables attendus avant 17h

### Chacun sur sa machine (avant le vendredi)

- Bob installé et connexion avec IBMid testée. 📚 [`02_bob_projet_equipe.md`](02_bob_projet_equipe.md)
- Compte GitHub créé, `git` installé (`git --version` dans un terminal) et authentification GitHub testée.
- Connexion au MCP web testée si retenue, selon la fiche 03. 📚 [`03_bob_mcp_web.md`](03_bob_mcp_web.md)
- Trois questions préparées pour chacun des défis.
- Outil de wireframe choisi (Excalidraw, Figma ou papier).
- Budget BobCoin connu et savoir choisir Ask, Plan ou Agent selon la tâche. 📚 [`00_bob_intro.md`](00_bob_intro.md) · [`01_bob_bobcoin.md`](01_bob_bobcoin.md)

### Après le choix du défi (étape 1, 17h→22h)

- Stack commune choisie parmi les technologies maîtrisées par les personnes qui vont l'implémenter et l'intégrer.
- Rôles répartis (Lead Dev, Backend, Frontend/IA, PM/Pitcher).
- Décision sur les accès nécessaires (données, APIs, outils) et qui les prépare.

## 3. Actions par personne, dans l'ordre

### Avant le vendredi — sur sa machine

1. Ouvrir le **workspace de préparation** dans Bob : le dossier contenant ces fiches et les supports `Défis/`. C'est un dossier local sur votre ordinateur — pas encore le projet hackathon, qui sera créé à l'étape 2.
2. Tester le mode Ask avec une question courte sur l'un des défis.
3. Lire les fiches défis disponibles sans choisir trop tôt une solution.
4. Pour chaque défi, noter : utilisateur, problème, données disponibles, contraintes et question à poser au sponsor.
5. Vérifier sa stack personnelle : langages installés, runtimes, éditeurs.
6. Vérifier `git --version` dans un terminal. Si absent, installer [git-scm.com](https://git-scm.com).
7. Si le MCP web est envisagé, tester la connexion selon la fiche [`03_bob_mcp_web.md`](03_bob_mcp_web.md). Le mode d'installation dépend du serveur retenu ; le serveur distant peut ne pas nécessiter d'installation locale.

### Le vendredi en équipe (17h→22h — voir fiche 05)

8. Choisir la stack commune parmi les technologies maîtrisées par les personnes qui vont l'implémenter et l'intégrer.
9. Répartir les rôles (voir gabarit fiche [`05_hack_etape1_cadrage.md`](05_hack_etape1_cadrage.md)).
10. Identifier les accès nécessaires (données, APIs, outils) et décider qui les prépare.

## 4. Usage de Bob

Utiliser **Ask** pour analyser les documents locaux. Les supports du défi doivent déjà être placés dans le dossier `Défis/` du workspace ouvert dans Bob.

> **Workspace Bob** = un dossier ouvert dans l'application Bob. Le dossier ouvert fournit le contexte de travail du projet. Ouvrir ce workspace de préparation (avec `Défis/`) permet à Bob d'analyser les supports **sans recherche web** — Bob requiert une connexion internet active, mais il n'interroge pas le web si aucun MCP web n'est configuré.

### Prompt générique d'analyse

```
[Ask] Analyse uniquement le défi [NOM], à partir du document [FICHIER].

Pour ce défi, réponds uniquement aux points suivants :
1. Quel est l'utilisateur principal ?
2. Quel problème doit être résolu ?
3. Quelles données sont nécessaires ?
4. Quelles sont les contraintes explicites ?
5. Quelles sont les trois questions prioritaires à poser au sponsor ?

Pour chaque information confirmée, indique le fichier et la page
ou diapositive qui la justifie.

Ne propose pas encore de solution.
Distingue les informations présentes dans les documents,
les informations absentes et les hypothèses à valider.
```

### Illustration — Lallemand

Avec le support Lallemand placé dans `Défis/`, le prompt doit produire une analyse de ce type :

1. **Utilisateur principal** : Regulatory Affairs ; Marketing et Sales sont également des parties prenantes.
2. **Problème** : les homologations de produits de protection des plantes sont dispersées dans des bases nationales hétérogènes, ce qui rend les comparaisons manuelles longues.
3. **Données nécessaires** : sources officielles, homologations, usages, doses, restrictions, pays ou régions, source et date de collecte.
4. **Contraintes explicites** *(à confirmer sur le support Lallemand)* : chaque information doit être reliée à sa source ; aucune donnée ne doit être inventée ; les correspondances incertaines restent des hypothèses à confirmer.
5. **Questions prioritaires au sponsor** : quelles sources officielles et quelles régions faut-il couvrir pour la démonstration ? quels champs doivent être comparables entre produits et pays ? comment le statut d'une correspondance ou d'une donnée doit-il être validé par LPC ?

📚 [`Fiche défi Lallemand`](../Défis/Lallemand%20Plant%20Care%20-%20FICHE%20DEFI%20Hackathon%20IA%20FOR%20IMPACT%202026.pptx)

## 5. Points de vigilance

- Ne pas inventer une API, une donnée ou une contrainte absente du brief.
- Distinguer une information confirmée d'une hypothèse à valider.
- Ne pas consommer le budget sur des explorations inutiles : cibler les questions et ouvrir une nouvelle conversation lorsqu'on change de sujet. 📚 [`01_bob_bobcoin.md`](01_bob_bobcoin.md)
- Ne jamais copier une clé API dans un fichier texte, un chat d'équipe ou un email — utiliser une variable d'environnement. Le dépôt Git sera créé à l'étape 2 ; cette règle s'applique dès maintenant. 📚 [`03_bob_mcp_web.md`](03_bob_mcp_web.md)

## 6. Checklist de sortie

- [ ] IBMid créé (ou existant confirmé) et connexion à Bob testée. 📚 [`02_bob_projet_equipe.md`](02_bob_projet_equipe.md)
- [ ] Compte GitHub créé et `git --version` retourne une version dans le terminal.
- [ ] Bob répond en mode Ask sur le workspace de préparation.
- [ ] `uvx --version` testé ou MCP web explicitement écarté.
- [ ] Stack personnelle vérifiée (langages, runtimes).
- [ ] Trois questions sont prêtes par défi.
- [ ] Un outil de wireframe est choisi.
- [ ] Aucun secret n'est placé dans Git.
- [ ] Le solde BobCoin et la réserve sont vérifiés.

---

> **Note sur le dépôt Git** : dans la fiche 02, la création du dépôt est indiquée en fin d'étape 1. Dans le déroulé de la fiche 05, elle intervient à la transition entre cadrage et réalisation. Les deux sont cohérents — le dépôt est créé avant que le code commence.
