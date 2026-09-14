# Étape 4 — Finalisation & code freeze
> Fiche 08 · Samedi 10 octobre, 7h → 13h

📚 **Programme** : [`Hackathon IA for Impact _ 30h de challenge IA.pdf`](../Organisation/Hackathon%20IA%20for%20Impact _%2030h%20de%20challenge%20IA.pdf) · **Méthode** : [`methodologie_hackathon_ia_for_impact.md`](../Méthodologie/methodologie_hackathon_ia_for_impact.md)

## 1. Objectif

Transformer le prototype nocturne en démonstration fiable et reproductible. Le code freeze est fixé à 13h dans la méthodologie de travail : après cette heure, aucune nouvelle fonctionnalité. 📚 [`methodologie_hackathon_ia_for_impact.md`](../Méthodologie/methodologie_hackathon_ia_for_impact.md)

Le programme officiel indique que la matinée du samedi est dédiée à la finalisation technique et à la préparation des pitchs. 📚 [`Hackathon IA for Impact _ 30h de challenge IA.pdf`](../Organisation/Hackathon%20IA%20for%20Impact _%2030h%20de%20challenge%20IA.pdf)

## 2. Livrables attendus à 13h

- Démo de bout en bout.
- Scénario de démo de trois à cinq étapes.
- Données de secours prêtes si une dépendance échoue.
- Test sur l'appareil réellement utilisé pour présenter.
- README permettant de comprendre et relancer le dépôt.
- Version gelée, identifiée par un commit ou un tag.

## 3. Actions participant, dans l'ordre

1. Stabiliser le parcours principal ; arrêter l'ajout de fonctionnalités secondaires.
2. Intégrer front, back, IA et données.
3. Écrire l'histoire d'un utilisateur fictif et le scénario de démo.
4. Préparer les mocks et les chemins de secours.
5. Tester le parcours complet sur le device de présentation.
6. Corriger uniquement les bugs bloquants ou les défauts qui empêchent la compréhension.
7. Mettre à jour le README, commiter et geler le code à 13h.

## 4. Usage de Bob

Utiliser **Agent** sur des fichiers ciblés pour corriger, produire les mocks et rédiger la documentation. 📚 [`00_bob_intro.md`](00_bob_intro.md)

### Prompt générique de revue de démo

```
[Agent] Code freeze à 13h — il reste [HEURES RESTANTES] avant la limite.

Analyse uniquement le parcours de démonstration suivant.
Ne crée aucune nouvelle fonctionnalité.
Corrige seulement ce qui empêche le parcours de fonctionner ou d'être compris.
Si une étape est trop risquée à corriger dans le temps restant, signale-le
et propose une alternative plus simple qui tient dans le délai.

Parcours minimum (obligatoire — doit fonctionner avant 13h) :
[ÉTAPES DU PARCOURS MINIMUM — issues du scénario défini à l'étape 1]

Parcours enrichi (bonus uniquement si déjà intégré et stable) :
[ÉTAPES BONUS — uniquement si développées en étape 3]

Vérifie uniquement les fichiers suivants : [FICHIERS CONCERNÉS PAR LE PARCOURS]
Exécute les vérifications ciblées et résume les fichiers modifiés.
```

### Prompt générique de README

```
[Agent] Rédige ou mets à jour README.md pour qu'une personne externe puisse :
1. comprendre le problème et le MVP ;
2. installer le projet ;
3. configurer les variables d'environnement sans exposer de secret ;
4. lancer la démo ;
5. distinguer les données réelles, les données mock et les limites connues.
N'invente aucune commande : vérifie les scripts présents dans le dépôt.
```

### Gabarit de validation — ce que la sortie doit permettre

> La démo est prête pour le pitch si tous les points suivants sont vrais.

**Parcours minimum :**
- [ ] Exécutable de bout en bout sans intervention manuelle
- [ ] Données mock visibles et identifiables comme fictives
- [ ] Aucune erreur bloquante pendant le parcours
- [ ] Testé sur le device de présentation, pas seulement sur le poste de développement

**Parcours enrichi (bonus) :**
- [ ] Fonctionne de façon fiable sur au moins trois essais consécutifs
- [ ] Si instable : retiré du scénario de démo — ne pas le montrer au jury

**README :**
- [ ] Commandes de lancement vérifiées dans le dépôt
- [ ] Distinction données réelles / mock explicite
- [ ] Limites du prototype écrites sans les minimiser

**Ce qui bloque le passage au pitch :**
- Parcours minimum non reproductible
- Démo testée uniquement sur le poste de développement
- README avec des commandes inventées ou non vérifiées

> **Note** : la sortie réelle de Bob dépend de votre codebase. Vérifiez le parcours vous-même après chaque correction avant de déclarer la démo stable.

📚 [`Fiche défi Lallemand`](../Défis/Lallemand%20Plant%20Care%20-%20FICHE%20DEFI%20Hackathon%20IA%20FOR%20IMPACT%202026.pptx)

## 5. Points de vigilance

- Tester sur le matériel de présentation, pas uniquement sur l'ordinateur de développement. 📚 [`methodologie_hackathon_ia_for_impact.md`](../Méthodologie/methodologie_hackathon_ia_for_impact.md)
- Ne jamais remplacer une source indisponible par une donnée non signalée.
- À partir du code freeze, corriger la stabilité et la présentation, pas élargir le périmètre.
- Les critères officiels d'évaluation incluent impact, faisabilité, viabilité et niveau de réalisation du prototype. 📚 [`Hackathon IA for Impact _ 30h de challenge IA.pdf`](../Organisation/Hackathon%20IA%20for%20Impact _%2030h%20de%20challenge%20IA.pdf)

## 6. Checklist de sortie

- [ ] Démo complète exécutée sans intervention imprévue.
- [ ] Scénario utilisateur écrit.
- [ ] Données de secours disponibles et identifiées.
- [ ] Test effectué sur le device final.
- [ ] README relu par une personne qui n'a pas codé la fonctionnalité.
- [ ] Commit de code freeze créé à 13h.
- [ ] Aucun nouveau développement prévu après le freeze.
