# Étape 3 — Production nocturne
> Fiche 07 · Samedi 10 octobre, 2h → 7h

📚 **Programme** : [`Hackathon IA for Impact _ 30h de challenge IA.pdf`](../Organisation/Hackathon%20IA%20for%20Impact%20_%2030h%20de%20challenge%20IA.pdf) · **Méthode** : [`methodologie_hackathon_ia_for_impact.md`](../Méthodologie/methodologie_hackathon_ia_for_impact.md)

## 1. Objectif

Réaliser et intégrer la fonction centrale du MVP sur un cas représentatif. À 7h, le parcours principal doit être exécutable sur la version partagée du projet — pas seulement sur les machines individuelles.

| Échéance | Résultat attendu |
| -------- | ---------------- |
| **2h — fin du setup** | Un parcours minimal connecté, éventuellement simulé ; les interfaces sont définies et le principal risque technique a été testé. |
| **7h — fin de la production** | La fonction centrale du MVP fonctionne sur un cas représentatif ; les composants sont intégrés et les limites connues. |
| **13h — objectif de gel du code de l'équipe** | Une démonstration reproductible, avec une solution de secours préparée. |

Cette étape ne repart pas sur la préparation des mocks : le squelette et les premières données ont été posés à l'étape 2. Il s'agit maintenant de coder, d'intégrer et de vérifier.

## 2. Livrables attendus à 7h

- La fonction centrale du MVP fonctionne sur un cas représentatif.
- Le parcours est exécutable sur la version partagée du projet.
- Un cas nominal et un cas limite pertinent ont été vérifiés.
- Les données ou traitements simulés sont explicitement identifiés et marqués de façon visible.
- Une version fonctionnelle est conservée et peut être relancée.
- Les limites et travaux restants sont classés par priorité.

## 3. Actions participant, dans l'ordre

1. Reprendre les tâches attribuées à 2h, les interfaces définies et les données préparées.
2. Implémenter la fonction centrale, en faisant tourner un premier cas de bout en bout avant d'élargir.
3. Faire un point court toutes les deux heures — voir § 5 pour les questions.
4. Corriger en priorité les blocages du parcours principal — un bug qui empêche le parcours passe avant toute fonctionnalité secondaire.
5. Intégrer : les changements terminés passent par la procédure de branche et de PR commune ; après fusion, vérifier le parcours sur la version partagée.
6. Gérer la fatigue : une personne bloquée depuis longtemps peut passer le relais ou dormir plutôt que dégrader le prototype. 📚 [`methodologie_hackathon_ia_for_impact.md`](../Méthodologie/methodologie_hackathon_ia_for_impact.md)

## 4. Usage de Bob

Utiliser **Agent** pour des changements ciblés : composants répétitifs, parsing, appels API, correction d'erreurs. Donner à Bob la tâche, les interfaces concernées et le résultat attendu ; ne pas lui demander de relire toute la codebase. 📚 [`00_bob_intro.md`](00_bob_intro.md) · [`01_bob_bobcoin.md`](01_bob_bobcoin.md)

### Prompt principal — réaliser une fonctionnalité

```
[Agent] Tu travailles sur [NOM DU COMPOSANT / DE LA FONCTION].

Tâche : [décrire la fonctionnalité à implémenter]

Composants concernés et interfaces :
- [COMPOSANT A] reçoit [ENTRÉE] et produit [SORTIE]
- [COMPOSANT B] appelle [COMPOSANT A] avec [PARAMÈTRES]

Comportement attendu : [décrire le comportement précis]

Exemple d'entrée : [EXEMPLE]
Exemple de sortie attendue : [EXEMPLE]

Critère de réussite : [ce qui doit être vrai pour que la fonctionnalité soit considérée terminée]

Contraintes :
- Respecter les interfaces définies dans [FICHIER D'ARCHITECTURE / AGENTS.md]
- Préserver les comportements existants ; limiter les modifications à celles nécessaires à la tâche
- Exécuter les commandes de vérification après implémentation et rapporter les résultats ; signaler celles qui n'ont pas pu être exécutées
```

### Prompt complémentaire — données de test

À utiliser si les données préparées à l'étape 2 ne couvrent pas les cas nécessaires au test de la fonctionnalité.

> **Distinction importante** : des données fictives réellement traitées par la fonction démontrent une capacité d'extraction ou d'analyse. Un résultat préécrit injecté directement dans l'affichage ne démontre que le parcours d'affichage. Choisir le niveau de simulation en fonction de ce que l'on veut prouver.

```
[Agent] Le parcours MVP nécessite des données de test supplémentaires.
Les données préparées à l'étape 2 sont : [DÉCRIRE CE QUI EXISTE]

Compléter uniquement les cas manquants pour couvrir :
1. [CAS MANQUANT 1]
2. [CAS MANQUANT 2]

Respecter le contrat de données défini dans [FICHIER D'ARCHITECTURE] :
- Ne pas ajouter de champ hors schéma pour le marquage fictif ; utiliser un fichier de métadonnées séparé ou un indicateur visible dans la démo si le schéma l'interdit
- Un champ absent et un champ null ne sont pas équivalents — se conformer au schéma
- Ajouter les entrées dans le dossier prévu, sans écraser l'existant

[CONTRAT DE DONNÉES — champs, types, valeurs attendues]
[DOSSIER CIBLE]
```

### Prompt complémentaire — corriger un blocage du parcours principal

À utiliser dès qu'un bug empêche le parcours principal de fonctionner.

```
[Agent] Dans [FICHIER], la commande [COMMANDE] produit cette erreur :
[ERREUR EXACTE]

Résultat attendu : [RÉSULTAT].

Commencer par analyser la cause dans ce fichier. Si elle provient du schéma
de données, d'une configuration ou d'un composant appelé, étendre l'analyse
à ces éléments et justifier toute modification hors du fichier signalé.
Proposer le changement minimal, l'appliquer, puis exécuter la commande
ciblée pour vérifier. Le critère de qualité est la correction ciblée,
pas le nombre de fichiers touchés.
```

### Gabarit de validation — sortie de l'étape

> La sortie est utilisable pour passer à l'étape 4 si elle satisfait les critères suivants.

**Pour la fonctionnalité implémentée :**
- [ ] La fonction centrale fonctionne sur un cas représentatif
- [ ] Les entrées et sorties respectent les interfaces définies à l'étape 2
- [ ] Un cas nominal et un cas limite pertinent pour le défi ont été vérifiés
- [ ] Les simulations (données ou traitements) sont identifiées explicitement dans le code et visibles pendant la démonstration

**Pour l'intégration :**
- [ ] Les changements terminés ont été fusionnés via la procédure de branche et de PR commune
- [ ] Le parcours principal fonctionne sur la version partagée après fusion
- [ ] Les résultats du composant principal sont utilisables par le composant suivant dans le parcours

**Ce qui bloque le passage à l'étape 4 :**
- Le parcours principal ne s'exécute pas sur la version partagée
- Les simulations ne sont pas identifiées — risque de les présenter comme des résultats réels devant le jury
- Aucun cas limite vérifié — la démo ne montre pas que le projet gère l'incertitude

## 5. Points de synchronisation

Checkpoint toutes les deux heures environ, sur trois questions :

- Qu'est-ce qui fonctionne dans la version commune ?
- Qu'est-ce qui bloque le parcours ?
- Que faut-il simplifier ou abandonner ?

Les décisions sont partagées dans le chat d'équipe, validées collectivement et consignées dans `bob-notes.md` par la personne responsable. 📚 [`02_bob_projet_equipe.md`](02_bob_projet_equipe.md) § 8.

## 6. Points de vigilance

- La fonction centrale passe avant toute fonctionnalité secondaire.
- Une démo stable sur la version partagée vaut mieux qu'une fonctionnalité supplémentaire isolée sur une branche.
- Distinguer données simulées et traitement simulé : ce sont deux niveaux de démonstration différents.
- Tout mock doit être identifiable dans les données et visible pendant la démonstration.
- Ne pas dépenser des coins pour une réponse générale quand une question ciblée suffit. 📚 [`01_bob_bobcoin.md`](01_bob_bobcoin.md)

## 7. Checklist de sortie

- [ ] La fonction centrale du MVP fonctionne sur un cas représentatif.
- [ ] Le parcours est exécutable sur la version partagée du projet.
- [ ] Un cas nominal et un cas limite pertinent ont été vérifiés.
- [ ] Les données ou traitements simulés sont explicitement identifiés et marqués de façon visible dans la démo.
- [ ] Une version fonctionnelle est conservée et peut être relancée.
- [ ] Les limites et travaux restants sont classés par priorité.
- [ ] Les changements sont commités et fusionnés via la procédure commune.

> Si le parcours principal reste bloqué à 7h, décider d'une réduction de périmètre ou activer la solution de secours définie à l'étape 2 — inscrire le blocage dans une liste ne suffit pas.
