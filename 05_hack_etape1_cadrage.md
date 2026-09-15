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
6. Répartir les rôles (voir gabarit ci-dessous) et privilégier les technologies maîtrisées — limiter les nouveautés aux cas où elles sont indispensables.
7. Faire valider la phrase de MVP par toute l'équipe avant de coder.

### Gabarit de répartition des rôles

> À remplir en équipe pendant l'étape 1. Ce gabarit est une base — adaptez-le à votre équipe réelle.

| Rôle | Responsabilité principale | Périmètre Git |
|---|---|---|
| **Lead Dev** | Crée le dépôt GitHub, lance `/init`, configure `.bob/`, orchestre les branches | Racine du projet, `AGENTS.md`, `.bob/` |
| **Dev Backend** | API, logique métier, accès aux données | `/backend`, `/api`, `/data` |
| **Dev Frontend / IA** | Interface utilisateur, intégration des appels IA | `/frontend`, `/src`, intégration API IA |
| **PM / Pitcher** | Scénario de démo, slides, coordination avec le sponsor, pitch | `/docs`, `/pitch` |

> Un membre peut cumuler deux rôles si l'équipe est petite (ex : Lead Dev + Backend). La responsabilité principale du PM/Pitcher est la narration et la coordination — il prépare le pitch pendant que les devs codent.

### Format de phrase MVP

> Pour **[utilisateur]**, qui rencontre **[problème]**, nous construisons **[fonction unique]** afin de **[résultat observable]**, démontrée sur **[cas de démonstration]**.

## 4. Usage de Bob

Utiliser **Ask**, puis **Plan**. Ask sert à clarifier le brief ; Plan prépare et compare les options — ici, on lui demande explicitement de ne pas générer de code. 📚 [`00_bob_intro.md`](00_bob_intro.md) · [Modes Bob](https://bob.ibm.com/docs/ide/features/modes)

### Prompt générique de cadrage

```
[Plan] Voici l'analyse du défi (sortie de l'étape 0) et les réponses du sponsor.

Contrainte absolue : la démo doit fonctionner de bout en bout avant 13h samedi.
Le temps disponible est de 15h écoulées (Ven 22h → Sam 13h), pauses, intégration
et tests inclus — ce n'est pas 15h de développement effectif par personne.
L'équipe est de 4 à 5 personnes partant de zéro.

Propose trois MVP en tenant compte de ce délai.
Pour chacun : utilisateur, promesse, parcours de démo en 3 étapes max,
données nécessaires, risques liés au temps et ce qui est explicitement hors périmètre.
Pour chaque MVP, indique :
- faisabilité estimée : favorable, incertaine ou défavorable ;
- hypothèses nécessaires pour atteindre ce résultat ;
- principal point à tester rapidement pour lever le risque principal ;
- réduction de périmètre possible si le délai se révèle trop court ;
- quelle partie de la promesse dépend réellement de l'IA ;
- quel résultat observable montrera que le MVP apporte quelque chose (comparaison exploitable, anomalie repérée, tâche simplifiée…).
Pour chaque MVP, indique aussi si la démo peut fonctionner sans accès aux sources en direct, et si oui, sous quelle forme (réponse enregistrée, échantillon réel préparé, données synthétiques signalées).
Le jury doit comprendre en 2 min.
Le choix final appartient à l'équipe, à partir de ces propositions et des vérifications effectuées.
Ne génère aucun code.

[ANALYSE DU DÉFI — sortie de l'étape 0]
[RÉPONSES DU SPONSOR]
```

### Gabarit de validation — ce que la sortie doit contenir

> Cinq éléments suffisent pour passer à l'étape 2. Vérifiez-les sur le MVP **retenu** — les options abandonnées n'ont pas besoin d'être documentées exhaustivement.

**Sur le MVP retenu :**
- [ ] Un utilisateur et un problème précis
- [ ] Une phrase MVP (voir format § 3)
- [ ] Un parcours de démonstration en 3 étapes max
- [ ] Une solution de secours définie pour les données, avec ses limites clairement annoncées — quelle qu'en soit la forme (réponse enregistrée, échantillon réel préparé avec ses sources, données synthétiques explicitement signalées)
- [ ] Le principal risque identifié et la manière de le vérifier rapidement

**Sur la comparaison des trois options :**
- [ ] Pour chaque MVP : faisabilité estimée (favorable / incertaine / défavorable), hypothèses nécessaires et réduction de périmètre possible
- [ ] Un seul MVP retenu, avec une justification liée au délai de 15h, pas seulement à l'impact

**Ce qui bloque le passage à l'étape 2 :**
- MVP retenu non démontrable sans accès à une source externe non testée *et* aucune solution de secours définie
- Plusieurs MVP retenus sans choix tranché

> **Note** : la sortie réelle de Bob dépend de votre conversation. Le choix final appartient à l'équipe, à partir des propositions de Bob et des vérifications effectuées.

📚 [`Fiche défi Lallemand`](../Défis/Lallemand%20Plant%20Care%20-%20FICHE%20DEFI%20Hackathon%20IA%20FOR%20IMPACT%202026.pptx)

## 5. Fin d'étape 1 — préparer le terrain technique (vers 21h30)

Avant de passer à l'implémentation (étape 2, 22h), le Lead Dev crée le dépôt GitHub pendant que les autres membres préparent leurs machines.

**Lead Dev :**

1. Aller sur [github.com](https://github.com) → **New repository**.
2. Nom du projet (ex : `hackathon-2026-equipe`), visibilité **Private**, cocher **Add a README file** → **Create repository**.
3. Copier l'URL HTTPS affichée (bouton **Code** → **HTTPS**), par exemple : `https://github.com/equipe/hackathon-2026-equipe.git`.
4. Inviter les membres : **Settings → Collaborators → Add people** → saisir leur nom d'utilisateur GitHub.
5. Ouvrir un terminal, se placer dans le dossier de travail, cloner le repo en local, puis l'ouvrir dans Bob :
   ```bash
   cd ~/Documents/BobIA          # Mac/Linux
   # cd "$env:USERPROFILE\Documents\BobIA"   # Windows PowerShell

   git clone https://github.com/equipe/hackathon-2026-equipe.git
   cd hackathon-2026-equipe
   # → File → Open Folder dans Bob : sélectionner ce dossier
   ```
6. Partager l'URL dans le chat d'équipe (WhatsApp, Discord…) pour que les membres puissent vérifier leur accès.
7. Une fois le squelette pushé (début étape 2), annoncer séparément dans le chat : « squelette en ligne, vous pouvez cloner ».

**Membres (dès réception de l'URL) :**

1. Accepter l'invitation GitHub reçue par email.
2. Vérifier l'accès : ouvrir l'URL dans un navigateur, le dépôt doit être visible.
3. Attendre l'annonce du Lead Dev (« squelette en ligne ») avant de cloner — le squelette applicatif n'est pas encore disponible jusqu'au début de l'étape 2.

> La séquence complète `git clone` + ouverture dans Bob est dans la fiche [`02_bob_projet_equipe.md`](02_bob_projet_equipe.md) § 11.

## 6. Points de vigilance

- Ne pas commencer l'implémentation tant que l'équipe ne sait pas répondre à « quoi, pour qui, comment le démontrer ? ». 📚 [`methodologie_hackathon_ia_for_impact.md`](../Méthodologie/methodologie_hackathon_ia_for_impact.md)
- Une idée ambitieuse n'est pas un MVP si son parcours ne peut pas être démontré.
- Pour Lallemand, une donnée extraite ne doit pas être présentée comme validée et toute information doit conserver sa source. 📚 [`Fiche défi Lallemand`](../Défis/Lallemand%20Plant%20Care%20-%20FICHE%20DEFI%20Hackathon%20IA%20FOR%20IMPACT%202026.pptx)
- Pour iMSA, l'orientation humaine doit rester visible lorsque l'écart nécessite une vérification. 📚 [`iMSA.txt`](../Défis/iMSA.txt)

## 7. Checklist de sortie

- [ ] Défi et utilisateur principal choisis.
- [ ] Phrase MVP validée par toute l'équipe.
- [ ] Scénario de démo écrit en quelques étapes.
- [ ] Hors périmètre explicite.
- [ ] Rôles répartis selon le gabarit (Lead Dev, Backend, Frontend/IA, PM/Pitcher).
- [ ] Risques et hypothèses notés.
- [ ] Dépôt GitHub créé par le Lead Dev, URL partagée, accès vérifié par au moins un autre membre.
- [ ] Budget BobCoin de l'étape respecté et réserve conservée. 📚 [`01_bob_bobcoin.md`](01_bob_bobcoin.md)
