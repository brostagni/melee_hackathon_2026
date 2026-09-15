# Hackathon IA for Impact 2026 — Guide pratique avec IBM Bob

> La Mêlée Numérique · Toulouse · 9–10 octobre 2026
> Dix fiches pour préparer son environnement, construire un MVP en équipe et présenter une démonstration crédible.

## 1. À quoi sert ce dépôt ?

Ce dépôt rassemble des fiches pratiques pour accompagner les participants au Hackathon IA for Impact 2026 avec [IBM Bob](https://bob.ibm.com).

Vous y trouverez des explications, des prompts à adapter, des procédures de travail en équipe et des critères pour vérifier votre progression.

Le parcours vise un résultat concret : **un MVP — produit minimum viable — centré sur un utilisateur, fonctionnel sur un cas représentatif et démontrable avec des limites clairement annoncées**.

Les exemples sont adaptés à une équipe de quatre à cinq personnes. Ajustez les rôles, les technologies et le budget à votre situation.

## 2. Par où commencer ?

1. **Découvrez Bob** avec la [fiche 00](00_bob_intro.md).
2. **Préparez votre poste et vos questions** avec la [fiche 04](04_hack_etape0_prephackathon.md).
3. Consultez la [fiche 01](01_bob_bobcoin.md) pour suivre votre consommation et la [fiche 02](02_bob_projet_equipe.md) pour organiser le travail en équipe.
4. Si vous avez besoin de recherche web, consultez la [fiche 03](03_bob_mcp_web.md).
5. Pendant le hackathon, suivez les étapes des **fiches 05 à 09**.

Les fiches sont consultables directement sur GitHub. Pour les ouvrir dans Bob, téléchargez le dépôt ou clonez-le sur votre machine.

### Récupérer les fiches localement

**macOS / Linux :**

```bash
mkdir -p ~/Documents/BobIA
cd ~/Documents/BobIA
git clone https://github.com/brostagni/melee_hackathon_2026.git
cd melee_hackathon_2026
```

**Windows PowerShell :**

```powershell
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\Documents\BobIA"
Set-Location "$env:USERPROFILE\Documents\BobIA"
git clone https://github.com/brostagni/melee_hackathon_2026.git
Set-Location melee_hackathon_2026
```

Dans Bob, sélectionnez **File → Open Folder**, puis ouvrez le dossier `melee_hackathon_2026`.

**Ce dépôt contient les supports de préparation.** Le code du MVP sera développé dans un dépôt d'équipe distinct, créé pendant le cadrage. Utilisez alors l'URL communiquée par votre Lead Dev.

Si vous avez déjà cloné les fiches, réutilisez votre copie existante.

## 3. Les dix fiches

### Comprendre et configurer Bob

| Fiche                                                | Ce qu'elle vous aide à faire                                                     |
| ---------------------------------------------------- | -------------------------------------------------------------------------------- |
| [00 — C'est quoi Bob ?](00_bob_intro.md)             | Comprendre les modes, les outils et le vocabulaire.                              |
| [01 — Gérer ses Bobcoins](01_bob_bobcoin.md)         | Suivre la consommation, maîtriser le contexte et préserver une réserve.          |
| [02 — Travailler en équipe](02_bob_projet_equipe.md) | Configurer le projet, partager les consignes et organiser les contributions.     |
| [03 — Recherche web avec Tavily](03_bob_mcp_web.md)  | Distinguer lecture d'une URL et recherche web, puis configurer et tester le MCP. |

### Avancer du brief à la démonstration

| Fiche                                                    | Résultat recherché                                                                         |
| -------------------------------------------------------- | ------------------------------------------------------------------------------------------ |
| [04 — Pré-hackathon](04_hack_etape0_prephackathon.md)    | Un environnement prêt et des questions utiles pour les sponsors.                           |
| [05 — Découverte et cadrage](05_hack_etape1_cadrage.md)  | Un utilisateur, un problème, un MVP et un scénario de démonstration retenus.               |
| [06 — Architecture et setup](06_hack_etape2_setup.md)    | Un premier parcours connecté, un squelette partagé et le principal risque technique testé. |
| [07 — Production nocturne](07_hack_etape3_production.md) | La fonction centrale du MVP réalisée et intégrée dans la version commune.                  |
| [08 — Finalisation](08_hack_etape4_finalisation.md)      | Une démonstration reproductible, une solution de secours et une version identifiée.        |
| [09 — Pitch et démo](09_hack_etape5_pitch.md)            | Une présentation répétée, factuelle et adaptée au temps de passage.                        |

## 4. Les jalons de travail

Les créneaux ci-dessous constituent le parcours de travail proposé dans les fiches. Les consignes de l'organisation prévalent pour les horaires, les livrables et le passage devant le jury.

| Créneau                      | Priorité   | Résultat attendu                                                                    |
| ---------------------------- | ---------- | ----------------------------------------------------------------------------------- |
| **Avant vendredi 17 h**      | Préparer   | Bob opérationnel, accès vérifiés, briefs lus et questions préparées.                |
| **Vendredi 17 h–22 h**       | Cadrer     | Un seul MVP retenu, un hors périmètre explicite et des rôles répartis.              |
| **Vendredi 22 h–samedi 2 h** | Connecter  | Un parcours minimal exécutable et le risque technique principal testé.              |
| **Samedi 2 h–7 h**           | Réaliser   | La fonction centrale fonctionne sur un cas représentatif dans la version partagée.  |
| **Samedi 7 h–13 h**          | Stabiliser | Démonstration et secours testés, README utilisable, version de référence conservée. |
| **Samedi 13 h–17 h**         | Répéter    | Présentation chronométrée, transitions maîtrisées et réponses au jury préparées.    |

**Repère de planification : vendredi 22 h → samedi 13 h représente 15 heures écoulées**, pauses, intégration et tests compris.

Le jalon de **13 h** correspond à l'objectif de gel des fonctionnalités retenu dans cette méthode. Une correction exceptionnelle d'un défaut bloquant impose une nouvelle vérification de la version de démonstration.

La préparation du pitch commence en parallèle du développement. Une équipe prête peut avancer sans attendre le créneau suivant.

## 5. Bien utiliser Bob pendant le hackathon

### Choisir le mode selon le besoin

* **Ask** : comprendre un document, explorer le projet ou clarifier une question.
* **Plan** : préparer une réalisation et comparer les options lorsqu'un arbitrage est nécessaire.
* **Agent** : implémenter, modifier des fichiers, exécuter des commandes et vérifier les résultats.

Ask → Plan → Agent est un parcours utile pour une tâche incertaine. Une correction simple peut commencer directement en Agent.

### Donner une tâche vérifiable

Adaptez les prompts des fiches en indiquant :

* le résultat attendu ;
* les fichiers ou composants concernés ;
* les contraintes et interfaces à respecter ;
* un exemple d'entrée et de sortie lorsque cela aide ;
* les critères de réussite.

Vérifiez les résultats obtenus et les commandes réellement exécutées. Une réponse convaincante ne suffit pas à valider une fonctionnalité.

### Suivre le budget réel

Vérifiez votre solde au démarrage et aux principaux jalons. Les allocations dépendent des comptes utilisés ; les montants donnés en exemple ne constituent pas une garantie.

Les instructions projet et les contenus chargés contribuent au contexte traité par Bob. Gardez-les utiles et concis.

Si vous utilisez Tavily, distinguez **la consommation Bob** et **les crédits du service de recherche**.

## 6. Travailler sur une version commune

* Le Lead Dev prépare le squelette et annonce quand il est disponible.
* Chaque membre clone le dépôt d'équipe une seule fois et prépare son environnement local.
* Les contributions suivent la procédure de branches et de pull requests définie par l'équipe.
* Après intégration, le parcours principal est vérifié sur la version partagée.
* Les découvertes utiles sont partagées dans le chat d'équipe. Une personne désignée consigne les décisions validées dans `docs/bob-notes.md`.

Les fichiers de configuration partagés fournissent des consignes communes. Les identifiants et les prérequis locaux restent à configurer sur chaque poste.

## 7. Ce que la démonstration doit prouver

La démonstration doit montrer le bénéfice central du MVP sur un cas représentatif.

Distinguez explicitement :

* les données réelles et les données synthétiques ;
* les traitements exécutés en direct et les résultats préparés ;
* les résultats constatés, les hypothèses et les perspectives.

Une simulation peut permettre de présenter un parcours, mais elle ne prouve pas que le traitement remplacé fonctionne.

Avant le pitch, conservez une version identifiée, rejouez le scénario dans les conditions de présentation et testez la bascule vers la solution de secours.

## 8. Documents complémentaires et références

Ce dépôt contient les dix fiches et ce README. Les briefs sponsors, le programme officiel et la méthodologie cités dans certaines fiches ne sont pas inclus dans cette version du dépôt.

Les liens vers `../Défis/`, `../Organisation/` et `../Méthodologie/` supposent que ces documents sont disponibles dans l'arborescence locale correspondante. Récupérez-les auprès de l'organisation et vérifiez les consignes applicables à votre défi.

### Documentation des outils

* [IBM Bob — Documentation](https://bob.ibm.com/docs/ide)
* [IBM Bob — Modes](https://bob.ibm.com/docs/ide/features/modes)
* [IBM Bob — Bobcoins](https://bob.ibm.com/docs/ide/account/bobcoins)
* [IBM Bob — Initialiser un projet](https://bob.ibm.com/docs/ide/tutorials/start-a-project)
* [IBM Bob — Configuration MCP](https://bob.ibm.com/docs/ide/configuration/mcp/mcp-in-bob)
* [Tavily — Serveur MCP officiel](https://github.com/tavily-ai/tavily-mcp)

---

*Hackathon IA for Impact 2026 · La Mêlée Numérique · Toulouse · 9–10 octobre 2026*
