# Étape 2 — Architecture & setup
> Fiche 06 · Vendredi 9 octobre, 22h → samedi 10 octobre, 2h (enveloppe maximale)

📚 **Programme** : [`Hackathon IA for Impact _ 30h de challenge IA.pdf`](../Organisation/Hackathon%20IA%20for%20Impact%20_%2030h%20de%20challenge%20IA.pdf) · **Méthode** : [`methodologie_hackathon_ia_for_impact.md`](../Méthodologie/methodologie_hackathon_ia_for_impact.md)

## 1. Objectif

Sur les 15 h disponibles entre vendredi 22h et samedi 13h, cette étape en utilise 4. Elle doit donc permettre de **vérifier que le MVP peut être construit et intégré** : architecture décidée, squelette partagé qui démarre, premier parcours connecté fonctionnel (même avec des simulations), risque technique principal testé, tâches attribuées avec leurs interfaces.

« Afficher quelque chose » ne suffit pas. L'objectif est de prouver que la structure choisie permet de réaliser le parcours.

## 2. Livrables attendus à 2h

- Architecture minimale retenue et documentée.
- Squelette partagé, reproductible sur une seconde machine.
- Un parcours connecté minimal fonctionnel — les simulations sont acceptées, mais elles doivent être clairement identifiées.
- Risque technique principal testé ; solution de secours définie si nécessaire.
- Tâches attribuées avec leurs interfaces et critères de validation.

Ce que « parcours connecté minimal » signifie selon le type de projet :

| Type de projet                        | Résultat attendu                                                                                       |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| Application avec interface et backend | Une action utilisateur appelle le backend et affiche une réponse structurée, éventuellement simulée.  |
| Traitement documentaire               | Un fichier d'exemple traverse les principales étapes et produit une sortie minimale.                  |
| Comparaison de données                | Un petit échantillon local est chargé et présenté dans le format attendu.                             |

## 3. Déroulé indicatif

| Créneau          | Priorité                                                                                        |
| ---------------- | ----------------------------------------------------------------------------------------------- |
| **22h–22h30**    | Confirmer l'architecture minimale, les interfaces entre composants et les responsabilités.      |
| **22h30–23h30**  | Créer et partager le squelette ; tester en parallèle la dépendance la plus risquée.             |
| **23h30–1h**     | Faire fonctionner un premier parcours connecté avec des données préparées.                      |
| **1h–2h**        | Vérifier sur une seconde machine, intégrer les premiers éléments, préparer les tâches suivantes.|

Les 4h sont une enveloppe maximale. Une équipe prête plus tôt commence les fonctionnalités sans attendre 2h.

La préparation des données, les maquettes et le scénario de démonstration n'ont pas à attendre qu'un problème local d'installation soit résolu.

## 4. Actions — qui fait quoi

> Le dépôt GitHub existe déjà (créé en fin d'étape 1 par le Lead Dev). L'URL a été partagée dans le chat d'équipe. Le Lead Dev reprend le dossier déjà cloné à l'étape 1 — pas besoin de recloner.

### Lead Dev — dès 22h

```bash
# 1. Reprendre le dossier cloné à l'étape 1
cd hackathon-2026-equipe

# 2. Créer le squelette minimal (avec Bob en mode Agent — voir § 5)
#    Critère : le projet démarre avec une commande et un premier échange
#    entre composants produit une sortie structurée

# 3. Vérifier le démarrage, puis lancer /init (mode Agent)
#    → Bob génère AGENTS.md et .bob/ en s'appuyant sur le squelette existant
#    → Relire AGENTS.md — corriger la stack si Bob a mal interprété
#    → Créer .bob/rules/01_stack.md, 02_langue.md, 03_equipe.md
#    → Créer .bob/mcp.json si utilisation du MCP web
#      (ajouter .bob/mcp.json au .gitignore si clé API présente)

# 4. Premier commit et push
git add .
git commit -m "feat: squelette initial + configuration Bob"
git push
```

**→ Prévenir l'équipe dès que le push est visible.**

📚 Séquence complète Lead Dev → membres : [`02_bob_projet_equipe.md`](02_bob_projet_equipe.md) § 11.

---

### En parallèle — tester le risque principal

Pendant que le Lead Dev finalise le squelette, **une personne vérifie la dépendance la plus risquée** pour le MVP. Selon le défi, cela peut être :

- un premier appel à une API externe (clé valide, format de réponse) ;
- la lecture d'un document représentatif (champs présents, encodage) ;
- un premier appel au modèle d'IA (latence, format de sortie).

Résultat attendu : **accès confirmé, limite identifiée ou solution de secours activée.**

---

### Point de synchronisation — avant de distribuer les tâches

> - Le squelette démarre sur la machine du Lead Dev **et** sur une seconde machine.
> - Les interfaces entre composants sont comprises par tous les contributeurs concernés.
> - Chaque tâche a un responsable, un résultat attendu et un critère de validation.
>
> Si le squelette ne démarre pas sur une seconde machine, résoudre avant de distribuer.
> La langue de réponse de Bob n'est pas un critère bloquant : les tâches peuvent démarrer dès que les interfaces sont claires.

---

### Membres — dès que le Lead Dev a pushé

**Se placer dans le dossier de travail :**

```bash
cd ~/Documents/BobIA          # Mac/Linux
```

```powershell
cd "$env:USERPROFILE\Documents\BobIA"   # Windows PowerShell
```

**Puis cloner avec l'URL réelle communiquée par le Lead Dev dans le chat d'équipe :**

```bash
git clone https://github.com/equipe/hackathon-2026-equipe.git
cd hackathon-2026-equipe
```

> Si vous avez déjà cloné le dépôt, ouvrez votre copie existante et récupérez les mises à jour (`git pull`) ; ne le clonez pas une seconde fois.

**Ouvrir ce dossier précis dans Bob : File → Open Folder → `BobIA/hackathon-2026-equipe`**

```bash
# 1. (effectué ci-dessus — vous êtes dans hackathon-2026-equipe/)

# 2. Ouvrir ce dossier dans Bob (File → Open Folder → BobIA/hackathon-2026-equipe)
#    → "Do you trust the authors ?" → Yes, I trust the authors

# 3. Vérifier que .bob/ et AGENTS.md sont présents dans l'explorateur

# 4. Vérifier que le projet démarre avec la commande fournie par le Lead Dev

# 5. Configurer les variables d'environnement locales si nécessaire
#    (clé API Tavily, etc. — ne jamais les committer)
```

---

### Suite — tous ensemble

1. Distribuer les tâches par branche : `git checkout -b feat/nom-feature`.
2. Les contributeurs dont la machine n'est pas encore prête peuvent avancer sur la préparation des données, les maquettes et le scénario de démonstration.

## 5. Usage de Bob

Utiliser **Plan** pour l'architecture, puis **Agent** pour créer le squelette et les fichiers de configuration. 📚 [`00_bob_intro.md`](00_bob_intro.md)

### Prompt générique d'architecture

```
[Plan] À partir du MVP retenu à l'étape 1 et de la stack maîtrisée par l'équipe,
propose une architecture minimale pour un hackathon de 30h.

Contrainte absolue : sur 4h de setup disponibles (Ven 22h → Sam 2h),
l'objectif est qu'un premier parcours connecté fonctionne — une action utilisateur
appelle le backend et produit une réponse structurée, ou un fichier d'exemple
traverse les principales étapes et produit une sortie minimale.
Les simulations sont acceptées, mais doivent être explicitement identifiées.
Les fonctionnalités complètes se codent en étape 3 (Sam 2h → 7h).

Si un arbitrage architectural reste ouvert après le cadrage, présente deux options
et recommande celle qui permet de réaliser et d'intégrer le MVP dans le délai
restant — pas seulement de démarrer rapidement.

Pour l'architecture : dossiers, flux de données, interfaces entre composants,
risque technique principal et comment le tester rapidement.
N'ajoute aucune fonctionnalité hors MVP.

[MVP RETENU — sortie de l'étape 1]
[STACK MAÎTRISÉE PAR L'ÉQUIPE]
[RISQUE PRINCIPAL IDENTIFIÉ EN ÉTAPE 1]
```

### Prompt générique d'implémentation

```
[Agent] Implémente uniquement le squelette validé ci-dessous.
Critère de succès : le projet démarre avec une commande et un premier échange
entre composants produit une sortie structurée (simulation acceptée).
Crée les fichiers minimaux, respecte la stack existante, ajoute une commande
pour démarrer et vérifie son fonctionnement.
Les fonctions simulées doivent avoir des entrées et sorties définies et être
clairement marquées comme simulations.
Ne crée pas de fonctionnalité métier.
Liste les commandes de validation à exécuter.

[ARCHITECTURE VALIDÉE — sortie du prompt d'architecture]
```

### Gabarit de validation — ce que la sortie d'architecture doit contenir

> La sortie est utilisable pour lancer l'implémentation si elle contient tous les éléments suivants.

**Pour l'architecture proposée :**
- [ ] Liste des dossiers et fichiers à créer
- [ ] Distinction claire entre ce qui est dans le squelette et ce qui est reporté en étape 3
- [ ] Parcours connecté minimal décrit (même avec simulations)
- [ ] Simulations clairement identifiées avec leurs interfaces (entrées / sorties)
- [ ] Risque technique principal et comment le tester en parallèle du setup
- [ ] Commandes pour démarrer le projet

**Pour la recommandation :**
- [ ] Justification liée au temps disponible et à la stack de l'équipe
- [ ] Option retenue = la plus simple pour réaliser **et intégrer** le MVP dans le délai restant
- [ ] Aucune fonctionnalité hors MVP dans le squelette

**Ce qui bloque le passage à l'implémentation :**
- Dépendance non maîtrisée qui compromet le démarrage (base de données externe non provisionnée, service tiers inaccessible…)
- Architecture recommandée hors stack maîtrisée par l'équipe
- Collecteurs de données réels requis avant que le parcours minimal fonctionne, sans solution de secours définie

**Pour la sortie de l'implémentation :**
- [ ] Le projet démarre avec une commande
- [ ] Un premier échange entre composants produit une sortie structurée
- [ ] Les simulations sont identifiées dans le code
- [ ] Aucune erreur au démarrage

## 6. Points de vigilance

- Ne pas choisir un framework que personne ne maîtrise. 📚 [`methodologie_hackathon_ia_for_impact.md`](../Méthodologie/methodologie_hackathon_ia_for_impact.md)
- Ne pas placer de clé API dans Git. 📚 [`03_bob_mcp_web.md`](03_bob_mcp_web.md)
- Ne pas confondre architecture de démonstration et architecture de production.
- Prévoir un chemin de secours avec des données fictives explicitement marquées lorsque l'accès à une source est indisponible. Vérifier dans la fiche du défi si cette possibilité est autorisée. 📚 [`Défis/`](../Défis/)
- Un démarrage rapide peut cacher une intégration difficile : retenir l'option la plus simple pour **réaliser et intégrer** le MVP, pas seulement pour démarrer.
- Esquisser uniquement les écrans nécessaires au parcours retenu ; un seul peut suffire.

## 7. Checklist de sortie

- [ ] Architecture minimale retenue et documentée.
- [ ] Squelette partagé et reproductible sur une seconde machine.
- [ ] Premier parcours connecté fonctionnel — simulations clairement identifiées.
- [ ] Risque technique principal testé ; solution de secours définie si nécessaire.
- [ ] Tâches attribuées avec leurs interfaces et critères de validation.
