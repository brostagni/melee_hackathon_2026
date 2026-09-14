# Étape 3 — Production nocturne
> Fiche 07 · Samedi 10 octobre, 2h → 7h

📚 **Programme** : [`Hackathon IA for Impact _ 30h de challenge IA.pdf`](../Organisation/Hackathon%20IA%20for%20Impact%20_%2030h%20de%20challenge%20IA.pdf) · **Méthode** : [`methodologie_hackathon_ia_for_impact.md`](../Méthodologie/methodologie_hackathon_ia_for_impact.md)

## 1. Objectif

Obtenir un prototype qui fonctionne sur le parcours principal, même incomplet. Le programme prévoit le prototypage nocturne avec l'appui des mentors. 📚 [`Hackathon IA for Impact _ 30h de challenge IA.pdf`](../Organisation/Hackathon%20IA%20for%20Impact _%2030h%20de%20challenge%20IA.pdf)

## 2. Livrables attendus à 7h

- Parcours MVP exécutable de bout en bout.
- Briques intégrées au moins une fois.
- Données réalistes ou mocks identifiés comme tels.
- Commits réguliers et état récupérable.
- Liste courte des blocages restant à traiter.

## 3. Actions participant, dans l'ordre

1. Coder par briques indépendantes et testables.
2. Intégrer tôt, même avec des données fictives.
3. Faire un checkpoint de dix minutes environ toutes les deux heures.
4. Corriger d'abord les blocages du parcours de démo.
5. Commiter régulièrement et partager les décisions importantes.
6. Gérer la fatigue : une personne bloquée depuis longtemps peut passer le relais ou dormir plutôt que dégrader le prototype. 📚 [`methodologie_hackathon_ia_for_impact.md`](../Méthodologie/methodologie_hackathon_ia_for_impact.md)

## 4. Usage de Bob

Utiliser **Agent** pour des changements ciblés : composants répétitifs, parsing, appels API, mocks et correction d'erreurs. Donner à Bob le fichier, l'erreur et le résultat attendu ; ne pas lui demander de relire toute la codebase. 📚 [`00_bob_intro.md`](00_bob_intro.md) · [`01_bob_bobcoin.md`](01_bob_bobcoin.md)

### Prompt générique de mock — priorité absolue

```
[Agent] Le squelette du projet issu de l'étape 2 est en place.

Priorité : générer les données de démonstration avant tout autre développement.
Les données mock garantissent une démo fonctionnelle même si aucun collecteur
réel n'est opérationnel à 13h samedi (code freeze).

À partir du MVP retenu et des champs définis dans l'architecture, génère
un fichier de données fictives qui couvre :
1. un cas nominal complet ;
2. un cas avec un champ manquant ;
3. un cas nécessitant une décision humaine ou signalé comme hypothèse.
Marque chaque entrée comme mock de façon lisible dans les données.
Ajoute uniquement le fichier dans le dossier prévu.

[MVP RETENU — sortie de l'étape 1]
[CHAMPS DÉFINIS DANS L'ARCHITECTURE — sortie de l'étape 2]
[DOSSIER CIBLE]
```

### Prompt générique de déblocage — bonus si le temps le permet

```
[Agent] Dans [FICHIER], la commande [COMMANDE] produit cette erreur :
[ERREUR EXACTE]

Résultat attendu : [RÉSULTAT].
Analyse uniquement la cause liée à ce fichier, propose le changement minimal,
applique-le, puis exécute la commande ciblée pour vérifier.
Ne touche pas aux autres fichiers du projet.
```

### Gabarit de validation — ce que la sortie de mock doit contenir

> La sortie est utilisable pour passer à l'étape 4 si elle contient tous les éléments suivants.

**Pour le fichier de mock :**
- [ ] Trois entrées minimum couvrant les trois cas demandés
- [ ] Chaque entrée explicitement marquée comme fictive
- [ ] Tous les champs de l'architecture présents (ou null si absent — c'est le cas 2)
- [ ] Le cas hypothèse ou décision humaine clairement distingué du cas confirmé
- [ ] Le fichier est dans le dossier prévu par l'architecture

**Ce qui bloque le passage à l'étape 4 :**
- Données mock sans marquage fictif — risque de les présenter comme réelles devant le jury
- Champs absents du mock alors que l'interface les attend — la démo plante
- Aucun cas limite ou hypothèse — la démo ne montre pas la rigueur du projet

**Pour le déblocage d'un collecteur réel :**
- [ ] L'erreur est reproduite et identifiée avant d'appeler Bob
- [ ] La correction ne touche qu'au fichier concerné
- [ ] Le collecteur fonctionne après correction — valider avant de commiter

> **Note** : la sortie réelle de Bob dépend de votre conversation et de vos champs. Vérifiez que la démo affiche les trois cas avant de continuer.

📚 [`Fiche défi Lallemand`](../Défis/Lallemand%20Plant%20Care%20-%20FICHE%20DEFI%20Hackathon%20IA%20FOR%20IMPACT%202026.pptx)

## 5. Points de vigilance

- Une démo stable vaut mieux qu'une fonctionnalité supplémentaire non intégrée.
- Tout mock doit être identifiable comme mock ; ne pas le présenter comme une donnée réelle.
- Ne pas dépenser des coins pour une réponse générale quand une question ciblée suffit. 📚 [`01_bob_bobcoin.md`](01_bob_bobcoin.md)
- Partager les décisions utiles dans un fichier commité ou dans la documentation d'équipe. 📚 [`01_bob_bobcoin.md`](01_bob_bobcoin.md)

## 6. Checklist de sortie

- [ ] Le parcours MVP peut être lancé.
- [ ] Les briques principales ont été intégrées.
- [ ] Les mocks sont signalés.
- [ ] Un cas nominal et un cas limite sont testés.
- [ ] Les erreurs bloquantes restantes sont listées.
- [ ] Les changements sont commitées régulièrement.
- [ ] La réserve BobCoin n'est pas consommée sans arbitrage.
