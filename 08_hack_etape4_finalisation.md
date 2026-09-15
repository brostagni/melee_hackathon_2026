# Étape 4 — Finalisation & code freeze
> Fiche 08 · Samedi 10 octobre, 7h → 13h

## 1. Objectif

Transformer le prototype nocturne en démonstration fiable et reproductible. Le code freeze est fixé à 13h dans la méthodologie de travail : après cette heure, aucune nouvelle fonctionnalité.

Le programme officiel indique que la matinée du samedi est dédiée à la finalisation technique et à la préparation des pitchs. *(Source : programme Hackathon IA for Impact 2026 — à confirmer dans le document officiel.)*

## 2. Livrables attendus à 13h

- Démo de bout en bout.
- Scénario de démo : trois étapes métier principales (éventuellement plusieurs manipulations pour les illustrer).
- Solutions de secours vérifiées pour chaque dépendance critique (source externe, appel IA, application elle-même).
- Test dans les conditions réelles de présentation.
- README permettant de comprendre et relancer le dépôt.
- Version de démonstration identifiée, testée et partagée au plus tard à 13h.

## 3. Actions participant, dans l'ordre

> **Point de départ à 7h :** si le parcours principal ne fonctionne pas encore, appliquer d'abord l'arbitrage de l'étape 3 — réduire le périmètre ou activer la solution de secours. La finalisation n'est pas une nouvelle phase de développement.

1. Stabiliser le parcours principal ; arrêter l'ajout de fonctionnalités secondaires.
2. Vérifier l'intégration existante et corriger les défauts du parcours retenu.
3. Finaliser le scénario utilisateur défini au cadrage.
4. Vérifier et compléter les solutions de secours préparées aux étapes précédentes.
5. Tester le parcours complet sur l'appareil de présentation.
6. Corriger uniquement les bugs bloquants ou les défauts qui empêchent la compréhension.
7. Mettre à jour le README, commiter et geler le code à 13h.

## 4. Usage de Bob

Utiliser **Agent** sur des fichiers ciblés pour corriger, produire les mocks et rédiger la documentation.

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

Commence par les fichiers suivants : [FICHIERS CONCERNÉS PAR LE PARCOURS]
Si une cause est située dans un composant appelé ou une configuration hors de ce périmètre,
étends l'analyse et justifie toute modification hors périmètre.

En sortie, indique pour chaque vérification :
- commandes exécutées ;
- résultats constatés ;
- vérifications non réalisées ;
- défauts restant connus.
```

### Prompt générique de README

```
[Agent] Rédige ou mets à jour README.md pour qu'une personne externe puisse :
1. comprendre le problème et le MVP ;
2. installer le projet ;
3. configurer les variables d'environnement sans exposer de secret ;
4. lancer la démo ;
5. distinguer les données réelles, les données simulées et les limites connues.
N'invente aucune commande : vérifie les scripts présents dans le dépôt.
```

### Gabarit de validation — ce que la sortie doit permettre

> La démo est prête pour le pitch si tous les points suivants sont vrais.

**Parcours minimum :**
- [ ] Exécutable de bout en bout sans manipulation technique imprévue
- [ ] Reproductible sur au moins deux essais consécutifs dans les conditions de présentation
- [ ] Scénario remis à zéro entre deux passages : aucun résultat résiduel du premier essai
- [ ] Données simulées visibles et identifiables comme telles lorsqu'elles sont utilisées
- [ ] Aucune erreur bloquante pendant le parcours
- [ ] Testé dans les conditions réelles de présentation

**Parcours enrichi (bonus) :**
- [ ] Fonctionne de façon fiable sur au moins trois essais consécutifs
- [ ] Si instable : retiré du scénario de démo — ne pas le montrer au jury

**Solutions de secours :**
- [ ] Source externe indisponible → échantillon local ou réponse enregistrée, identifié comme tel
- [ ] Appel IA indisponible → résultat préparé, en précisant que le traitement n'est pas exécuté en direct
- [ ] Application impossible à présenter → captures ou courte vidéo, annoncées comme démonstration enregistrée
- [ ] Chaque solution de secours a été testée — sa seule présence dans un dossier ne suffit pas

**README :**
- [ ] Commandes de lancement vérifiées dans le dépôt
- [ ] Un autre membre peut relancer le projet en suivant le README, sans étapes implicites
- [ ] Distinction données réelles / simulées explicite
- [ ] Limites du prototype écrites sans les minimiser

**Ce qui bloque le passage au pitch :**
- Parcours minimum non reproductible
- Démo non testée dans les conditions de présentation
- README avec des commandes inventées ou non vérifiées
- Solution de secours non testée

> **Note** : la sortie réelle de Bob dépend de votre codebase. Vérifiez le parcours vous-même après chaque correction avant de déclarer la démo stable.

## 5. Points de vigilance

- Tester dans les conditions de présentation, pas uniquement sur l'ordinateur de développement.
- Ne jamais remplacer une source indisponible par une donnée non signalée.
- À partir du code freeze, trois niveaux s'appliquent :
  - **Gel des fonctionnalités** : aucun ajout de périmètre.
  - **Version de démonstration validée** : un commit précis, testé et conservé.
  - **Correction exceptionnelle** : uniquement pour un défaut bloquant, avec nouvelle vérification et identification du nouveau commit. Les ajustements de slides peuvent continuer ; les modifications de l'application doivent rester maîtrisées.
- Les critères officiels d'évaluation incluent impact, faisabilité, viabilité et niveau de réalisation du prototype. *(Source : programme Hackathon IA for Impact 2026 — à confirmer dans le document officiel.)*

## 6. Checklist de sortie

- [ ] Le parcours principal a été rejoué dans les conditions de présentation.
- [ ] La solution de secours a été testée.
- [ ] Les données et traitements simulés sont clairement annoncés.
- [ ] Un autre membre peut relancer le projet avec le README.
- [ ] La version de démonstration est identifiée, partagée et conservée (commit ou tag).

La préparation du pitch peut avancer **en parallèle** de ces vérifications : un défaut technique ne doit pas bloquer tout le travail de narration.
