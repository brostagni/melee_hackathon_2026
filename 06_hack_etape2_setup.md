# Étape 2 — Architecture & setup
> Fiche 06 · Vendredi 9 octobre, 22h → samedi 10 octobre, 2h

📚 **Programme** : [`Hackathon IA for Impact _ 30h de challenge IA.pdf`](../Organisation/Hackathon%20IA%20for%20Impact%20_%2030h%20de%20challenge%20IA.pdf) · **Méthode** : [`methodologie_hackathon_ia_for_impact.md`](../Méthodologie/methodologie_hackathon_ia_for_impact.md)

## 1. Objectif

Obtenir un dépôt qui démarre, une architecture décidée, des écrans esquissés et des tâches distribuées. Le programme appelle cette période « prototypage et challenge » à partir de 22h. 📚 [`Hackathon IA for Impact _ 30h de challenge IA.pdf`](../Organisation/Hackathon%20IA%20for%20Impact _ 30h%20de%20challenge%20IA.pdf)

## 2. Livrables attendus à 2h

- Dépôt initialisé et première version committée.
- Architecture minimale documentée.
- Trois à cinq écrans clés esquissés si une interface est nécessaire.
- Variables d'environnement définies sans secret commité.
- Tâches découpées et attribuées.
- Parcours principal identifiable, même avec des données fictives.

## 3. Actions participant, dans l'ordre

1. Limiter la décision d'architecture à 30 minutes.
2. Créer le dépôt et lancer `/init` dans Bob pour générer le contexte projet.
3. Relire `AGENTS.md` et créer les règles d'équipe utiles.
4. Créer le squelette minimal du projet et vérifier qu'il démarre.
5. Dessiner les écrans du parcours principal.
6. Découper les tâches en briques intégrables.
7. Configurer les variables d'environnement sur chaque machine.
8. Commit, partage et vérification par au moins une autre personne.

📚 `/init`, `AGENTS.md`, les rules et le partage de configuration sont décrits dans [`02_bob_projet_equipe.md`](02_bob_projet_equipe.md).

## 4. Usage de Bob

Utiliser **Plan** pour l'architecture, puis **Agent** pour créer le squelette et les fichiers de configuration. 📚 [`00_bob_intro.md`](00_bob_intro.md)

### Prompt générique d'architecture

```
[Plan] À partir du MVP retenu à l'étape 1 et de la stack maîtrisée par l'équipe,
propose deux architectures minimales pour un hackathon de 30h.

Contrainte absolue : sur 4h de setup disponibles (Ven 22h → Sam 2h),
l'objectif est uniquement que le projet démarre — pas qu'il soit fonctionnel.
Les collecteurs de données réels et les fonctionnalités avancées se codent
en étape 3 (Sam 2h → 7h). Ne les inclure dans le squelette que comme fichiers vides.

Pour chaque architecture : dossiers, flux de données, interfaces entre briques,
risques liés au temps, capacité de reprise. Recommande l'option la plus rapide
à faire démarrer, pas la plus élégante.
N'ajoute aucune fonctionnalité hors MVP.

[MVP RETENU — sortie de l'étape 1]
[STACK MAÎTRISÉE PAR L'ÉQUIPE]
```

### Prompt générique d'implémentation

```
[Agent] Implémente uniquement le squelette validé ci-dessous.
Critère de succès : le projet démarre avec une commande et affiche quelque chose.
Crée les fichiers minimaux, respecte la stack existante, ajoute une commande
pour démarrer et vérifie son fonctionnement. Ne crée pas de fonctionnalité métier.
Liste les commandes de validation à exécuter.

[ARCHITECTURE VALIDÉE — sortie du prompt d'architecture]
```

### Gabarit de validation — ce que la sortie d'architecture doit contenir

> La sortie est utilisable pour lancer l'implémentation si elle contient tous les éléments suivants.

**Pour chaque architecture proposée :**
- [ ] Liste des dossiers et fichiers à créer
- [ ] Distinction claire entre ce qui est dans le squelette et ce qui est reporté en étape 3
- [ ] Chemin de démo sans données réelles identifié (JSON local ou mock statique)
- [ ] Risques liés au délai de 4h explicités
- [ ] Commandes pour démarrer le projet

**Pour la recommandation :**
- [ ] Une seule architecture retenue
- [ ] Justification liée au temps disponible et à la stack de l'équipe, pas à la beauté du code
- [ ] Aucune fonctionnalité hors MVP dans le squelette

**Ce qui bloque le passage à l'implémentation :**
- Squelette qui suppose une base de données configurée dès le setup
- Collecteurs de données réels requis avant que le projet démarre
- Architecture recommandée hors stack maîtrisée par l'équipe

**Pour la sortie de l'implémentation :**
- [ ] Le projet démarre avec une commande (ex : `uvicorn main:app`, `npm start`)
- [ ] L'interface affiche quelque chose, même vide
- [ ] Aucune erreur au démarrage

> **Note** : la sortie réelle de Bob dépend de votre conversation et de votre stack. Vérifiez que votre squelette démarre avant de distribuer les tâches.

📚 [`Fiche défi Lallemand`](../Défis/Lallemand%20Plant%20Care%20-%20FICHE%20DEFI%20Hackathon%20IA%20FOR%20IMPACT%202026.pptx)

## 5. Points de vigilance

- Ne pas choisir un framework que personne ne maîtrise ; la méthode recommande la simplicité et le temps limité. 📚 [`methodologie_hackathon_ia_for_impact.md`](../Méthodologie/methodologie_hackathon_ia_for_impact.md)
- Ne pas placer de clé API dans Git. 📚 [`03_bob_mcp_web.md`](03_bob_mcp_web.md)
- Ne pas confondre architecture de démonstration et architecture de production.
- Prévoir un chemin de secours avec des données fictives explicitement marquées lorsque l'accès à une source est indisponible ; cette possibilité est explicitement prévue pour Lallemand. 📚 [`Fiche défi Lallemand`](../Défis/Lallemand%20Plant%20Care%20-%20FICHE%20DEFI%20Hackathon%20IA%20FOR%20IMPACT%202026.pptx)

## 6. Checklist de sortie

- [ ] Le projet démarre sur une machine de l'équipe.
- [ ] `/init` est fait et `AGENTS.md` est relu.
- [ ] Les rules d'équipe sont commitées si nécessaires.
- [ ] L'architecture est documentée.
- [ ] Les écrans clés sont esquissés.
- [ ] Les tâches sont attribuées.
- [ ] Les variables d'environnement sont configurées localement.
- [ ] Un commit de référence existe.
