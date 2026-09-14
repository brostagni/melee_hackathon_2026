# Étape 1 — Découverte & cadrage
> Fiche 05 · Vendredi 9 octobre, 17h → 22h

📚 **Programme** : [`Hackathon IA for Impact _ 30h de challenge IA.pdf`](../Organisation/Hackathon%20IA%20for%20Impact%20_%2030h%20de%20challenge%20IA.pdf) · **Méthode** : [`methodologie_hackathon_ia_for_impact.md`](../Méthodologie/methodologie_hackathon_ia_for_impact.md)

## 1. Objectif

Comprendre le besoin avec le sponsor, choisir un défi et formuler un MVP démontrable. Le programme prévoit l'accueil, la présentation des challenges, la constitution des équipes, les échanges avec les sponsors et des temps d'aide à l'idéation jusqu'au Pizza Time. 📚 [`Hackathon IA for Impact _ 30h de challenge IA.pdf`](../Organisation/Hackathon%20IA%20for%20Impact%20_%2030h%20de%20challenge%20IA.pdf)

## 2. Livrables attendus à 22h

- Défi choisi et problème reformulé.
- Utilisateur principal identifié.
- Une phrase de MVP.
- Un scénario de démonstration envisagé.
- Contraintes et hypothèses séparées.
- Rôles répartis et première stack retenue.

## 3. Actions participant, dans l'ordre

1. Écouter la présentation du défi.
2. Poser les questions préparées et noter les réponses exactes.
3. Reformuler le problème avec l'utilisateur, la situation et le résultat attendu.
4. Comparer deux ou trois angles de MVP ; choisir le plus faisable à démontrer.
5. Écrire ce qui est explicitement hors périmètre.
6. Répartir les rôles et choisir uniquement des technologies déjà maîtrisées.
7. Faire valider la phrase de MVP par toute l'équipe avant de coder.

### Format de phrase MVP

> Pour **[utilisateur]**, qui rencontre **[problème]**, nous construisons **[fonction unique]** afin de **[résultat observable]**, démontrée sur **[cas de démonstration]**.

## 4. Usage de Bob

Utiliser **Ask**, puis **Plan**. Ask sert à clarifier le brief ; Plan sert à comparer les options sans modifier le projet. 📚 [`00_bob_intro.md`](00_bob_intro.md)

### Prompt générique de cadrage

```
[Plan] Voici l'analyse du défi (sortie de l'étape 0) et les réponses du sponsor.

Contrainte absolue : la démo doit fonctionner de bout en bout avant 13h samedi,
soit environ 20h de prototypage disponibles (Ven 22h → Sam 13h), avec une équipe
de 4 à 5 personnes partant de zéro.

Propose trois MVP en tenant compte de ce délai.
Pour chacun : utilisateur, promesse, parcours de démo en 3 étapes max,
données nécessaires, risques liés au temps et ce qui est explicitement hors périmètre.
Évalue chaque MVP sur : démontrable en 20h ? démo stable sans données réelles ? jury comprend en 2 min ?
Indique lequel est réalisable et lequel dépasse le délai disponible.
Ne génère aucun code.

[ANALYSE DU DÉFI — sortie de l'étape 0]
[RÉPONSES DU SPONSOR]
```

### Gabarit de validation — ce que la sortie doit contenir

> La sortie de Bob est utilisable pour passer à l'étape 2 si et seulement si elle contient tous les éléments suivants. Si un élément manque, reposez la question avant de continuer.

**Pour chaque MVP proposé :**
- [ ] Un utilisateur nommé
- [ ] Une promesse en une phrase sans jargon
- [ ] Un parcours de démo en 3 étapes max
- [ ] Les données nécessaires identifiées
- [ ] Les risques liés au temps explicités
- [ ] Ce qui est hors périmètre listé

**Pour la comparaison :**
- [ ] Une indication explicite pour chaque MVP : réalisable en 20h ou non
- [ ] Une justification du MVP recommandé liée au délai, pas seulement à l'impact
- [ ] Un seul MVP retenu, avec un parcours de démo qui peut fonctionner sur données mock si les sources réelles sont indisponibles

**Ce qui bloque le passage à l'étape 2 :**
- MVP retenu non démontrable sans accès à une API externe non testée
- Aucun chemin de secours avec données fictives identifié
- Plusieurs MVP retenus sans choix tranché

> **Note** : la sortie réelle de Bob dépend de votre conversation et peut différer de ce gabarit. Vérifiez que votre sortie couvre chaque point avant de passer à l'architecture.

📚 [`Fiche défi Lallemand`](../Défis/Lallemand%20Plant%20Care%20-%20FICHE%20DEFI%20Hackathon%20IA%20FOR%20IMPACT%202026.pptx)

## 5. Points de vigilance

- Ne pas commencer l'implémentation tant que l'équipe ne sait pas répondre à « quoi, pour qui, comment le démontrer ? ». 📚 [`methodologie_hackathon_ia_for_impact.md`](../Méthodologie/methodologie_hackathon_ia_for_impact.md)
- Une idée ambitieuse n'est pas un MVP si son parcours ne peut pas être démontré.
- Pour Lallemand, une donnée extraite ne doit pas être présentée comme validée et toute information doit conserver sa source. 📚 [`Fiche défi Lallemand`](../Défis/Lallemand%20Plant%20Care%20-%20FICHE%20DEFI%20Hackathon%20IA%20FOR%20IMPACT%202026.pptx)
- Pour iMSA, l'orientation humaine doit rester visible lorsque l'écart nécessite une vérification. 📚 [`iMSA.txt`](../Défis/iMSA.txt)

## 6. Checklist de sortie

- [ ] Défi et utilisateur principal choisis.
- [ ] Phrase MVP validée par toute l'équipe.
- [ ] Scénario de démo écrit en quelques étapes.
- [ ] Hors périmètre explicite.
- [ ] Rôles répartis.
- [ ] Risques et hypothèses notés.
- [ ] Budget BobCoin de l'étape respecté et réserve conservée. 📚 [`01_bob_bobcoin.md`](01_bob_bobcoin.md)
