# Étape 0 — Pré-hackathon
> Fiche 04 · Hackathon IA for Impact 2026 · Avant vendredi 9 octobre, 17h

📚 **Programme et timing** : [`methodologie_hackathon_ia_for_impact.md`](../Méthodologie/methodologie_hackathon_ia_for_impact.md) · [`Hackathon IA for Impact _ 30h de challenge IA.pdf`](../Organisation/Hackathon%20IA%20for%20Impact%20_%2030h%20de%20challenge%20IA.pdf)

## 1. Objectif

Arriver au lancement avec un environnement fonctionnel et des questions utiles. Le temps de hackathon commence vendredi 9 octobre à 17h ; la configuration technique doit donc être faite avant ce créneau. 📚 [`Hackathon IA for Impact _ 30h de challenge IA.pdf`](../Organisation/Hackathon%20IA%20for%20Impact%20_%2030h%20de%20challenge%20IA.pdf)

## 2. Livrables attendus avant 17h

- Bob ouvert et testé sur sa machine.
- MCP web configuré si l'équipe en a besoin.
- Stack de développement vérifiée.
- Trois questions préparées pour chacun des défis.
- Outil de wireframe choisi.
- Budget BobCoin connu et stratégie Ask → Plan → Agent comprise. 📚 [`00_bob_intro.md`](00_bob_intro.md) · [`01_bob_bobcoin.md`](01_bob_bobcoin.md) · [`03_bob_mcp_web.md`](03_bob_mcp_web.md)

## 3. Actions participant, dans l'ordre

1. Ouvrir le projet de travail dans Bob.
2. Tester le mode Ask avec une question courte.
3. Vérifier `uvx --version` et le MCP web si une recherche externe est nécessaire.
4. Lire les fiches défis disponibles sans choisir trop tôt une solution.
5. Pour chaque défi, noter : utilisateur, problème, données disponibles, contraintes et question à poser au sponsor.
6. Vérifier la stack réellement maîtrisée par l'équipe.
7. Choisir Excalidraw, Figma ou papier pour les esquisses rapides.

## 4. Usage de Bob

Utiliser **Ask** pour analyser les documents locaux. Les supports du défi doivent déjà être placés dans le dossier `Défis/` du workspace ouvert dans Bob.

### Prompt générique d'analyse

```
[Ask] Analyse les documents disponibles dans le dossier Défis.

Pour le défi choisi, réponds uniquement aux points suivants :
1. Quel est l'utilisateur principal ?
2. Quel problème doit être résolu ?
3. Quelles données sont nécessaires ?
4. Quelles sont les contraintes explicites ?
5. Quelles sont les trois questions prioritaires à poser au sponsor ?

Ne propose pas encore de solution.
Distingue les informations présentes dans les documents,
les informations absentes et les hypothèses à valider.
```

### Illustration — Lallemand

Avec le support Lallemand placé dans `Défis/`, le prompt doit produire une analyse de ce type :

1. **Utilisateur principal** : Regulatory Affairs ; Marketing et Sales sont également des parties prenantes.
2. **Problème** : les homologations de produits de protection des plantes sont dispersées dans des bases nationales hétérogènes, ce qui rend les comparaisons manuelles longues.
3. **Données nécessaires** : sources officielles, homologations, usages, doses, restrictions, pays ou régions, valeur originale, valeur normalisée, source et date de collecte.
4. **Contraintes explicites** : chaque information doit être reliée à sa source ; aucune donnée ne doit être inventée ; les correspondances incertaines restent des hypothèses à confirmer ; le prototype doit être relançable depuis le dépôt remis.
5. **Questions prioritaires au sponsor** : quelles sources officielles et quelles régions faut-il couvrir pour la démonstration ? quels champs doivent être comparables entre produits et pays ? comment le statut d'une correspondance ou d'une donnée doit-il être validé par LPC ?

📚 [`Fiche défi Lallemand`](../Défis/Lallemand%20Plant%20Care%20-%20FICHE%20DEFI%20Hackathon%20IA%20FOR%20IMPACT%202026.pptx)

## 5. Points de vigilance

- Ne pas inventer une API, une donnée ou une contrainte absente du brief.
- Distinguer une information confirmée d'une hypothèse à valider.
- Ne pas consommer le budget sur des explorations inutiles : cibler les questions et ouvrir une nouvelle conversation lorsqu'on change de sujet. 📚 [`01_bob_bobcoin.md`](01_bob_bobcoin.md)
- Garder les clés API hors du dépôt et utiliser une variable d'environnement pour le MCP Tavily. 📚 [`03_bob_mcp_web.md`](03_bob_mcp_web.md)

## 6. Checklist de sortie

- [ ] Bob répond dans le mode Ask.
- [ ] Le MCP web est testé ou explicitement écarté.
- [ ] La stack de chaque membre est connue.
- [ ] Trois questions sont prêtes par défi.
- [ ] Un outil de wireframe est choisi.
- [ ] Aucun secret n'est placé dans Git.
- [ ] Le solde BobCoin et la réserve sont vérifiés.
