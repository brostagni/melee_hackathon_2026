# Étape 5 — Pitch & démo
> Fiche 09 · Samedi 10 octobre, 13h → 17h · Time to Pitch à 17h

📚 **Programme officiel** : [`Hackathon IA for Impact _ 30h de challenge IA.pdf`](../Organisation/Hackathon%20IA%20for%20Impact _%2030h%20de%20challenge%20IA.pdf) · **Méthode de pitch** : [`methodologie_hackathon_ia_for_impact.md`](../Méthodologie/methodologie_hackathon_ia_for_impact.md)

## 1. Objectif

Présenter une solution compréhensible, crédible et démontrable devant le jury. Le programme indique que le Time to Pitch commence samedi à 17h ; les quatre heures précédentes servent à préparer et répéter. 📚 [`Hackathon IA for Impact _ 30h de challenge IA.pdf`](../Organisation/Hackathon%20IA%20for%20Impact _%2030h%20de%20challenge%20IA.pdf)

Le jury évalue notamment l'impact, la faisabilité, la viabilité et le niveau de réalisation du prototype. 📚 [`Hackathon IA for Impact _ 30h de challenge IA.pdf`](../Organisation/Hackathon%20IA%20for%20Impact _%2030h%20de%20challenge%20IA.pdf)

## 2. Livrables attendus à 17h

- Plan de présentation validé.
- Démo répétée dans les conditions réelles.
- Script partagé et réparti entre les intervenants.
- Réponses préparées aux questions probables.
- Vidéo ou scénario de secours si le règlement et le matériel le permettent.
- Durée ajustée à la consigne communiquée par l'organisation ou le jury.

## 3. Structure participant

La méthode recommande cette progression :

1. **Problème** : une douleur réelle et un utilisateur.
2. **Solution** : une phrase sans jargon.
3. **Démo** : montrer le parcours principal.
4. **Impact et viabilité** : qui bénéficie de la solution et comment elle peut être reprise.
5. **Équipe** : rôles et complémentarité. 📚 [`methodologie_hackathon_ia_for_impact.md`](../Méthodologie/methodologie_hackathon_ia_for_impact.md)

### Actions, dans l'ordre

1. Choisir une seule histoire utilisateur.
2. Limiter les slides à une idée par slide.
3. Écrire les phrases de transition.
4. Répéter au moins trois fois avec le même appareil et les mêmes données.
5. Mesurer la durée et supprimer ce qui n'aide pas à comprendre.
6. Préparer les questions sur données, limites, reprise et impact.

## 4. Usage de Bob

Utiliser **Ask** pour challenger le message, puis **Agent** pour rédiger ou modifier les fichiers de pitch. 📚 [`00_bob_intro.md`](00_bob_intro.md)

### Prompt générique de script

```
[Ask] À partir du MVP, du scénario de démo et des preuves disponibles,
propose un script oral structuré en : problème, solution, démo, impact/viabilité, équipe.

Contrainte : 4h de préparation disponibles (Sam 13h → 17h), pitch à 17h.
Durée maximale du script : [DURÉE COMMUNIQUÉE PAR L'ORGANISATION].
Reste factuel : sépare les résultats démontrés, les hypothèses et ce qui reste à faire.
N'invente aucun chiffre. Si une fonctionnalité n'est pas dans la démo, ne la présente pas.

[MVP RETENU — sortie de l'étape 1]
[SCÉNARIO DE DÉMO — parcours minimum validé en étape 4]
[PREUVES DISPONIBLES — ce qui fonctionne réellement]
```

### Prompt générique de questions jury

```
[Ask] À partir du contexte du projet ci-dessous, liste les dix questions
difficiles que le jury pourrait poser sur impact, faisabilité, viabilité,
données, limites, sécurité et reprise du prototype.
Pour chaque question, donne une réponse courte fondée uniquement sur ce
qui est réellement construit, et indique ce qui reste à valider.

[CONTEXTE DU PROJET — ce qui est dans le dépôt à 13h]
```

### Gabarit de validation — ce que le script doit contenir

> Le script est utilisable pour le pitch si tous les points suivants sont vrais.

**Structure :**
- [ ] Problème en une phrase — une douleur réelle, un utilisateur nommé
- [ ] Solution en une phrase — sans jargon, sans acronyme non expliqué
- [ ] Démo en 3 étapes max — uniquement le parcours minimum validé
- [ ] Impact : qui bénéficie et comment le prototype peut être repris
- [ ] Équipe : rôles en 15 secondes

**Factualité :**
- [ ] Aucun résultat projeté présenté comme obtenu
- [ ] Limites du prototype nommées explicitement (données mock, sources couvertes)
- [ ] Hypothèses distinguées des faits confirmés

**Durée :**
- [ ] Script chronométré dans les conditions réelles
- [ ] Finit en dessous de la durée maximale, pas juste en dessous

**Questions jury :**
- [ ] Réponses fondées uniquement sur ce qui est dans le dépôt à 13h
- [ ] Ce qui reste à valider est dit explicitement — pas minimisé

**Ce qui bloque un passage convaincant :**
- Script qui présente des fonctionnalités non démontrables
- Durée non testée dans les conditions réelles
- Réponses aux questions jury qui inventent des chiffres ou des certitudes

> **Note** : la sortie réelle de Bob dépend de votre MVP et de votre scénario. Vérifiez que le script correspond à ce que vous pouvez réellement montrer.

📚 [`Fiche défi Lallemand`](../Défis/Lallemand%20Plant%20Care%20-%20FICHE%20DEFI%20Hackathon%20IA%20FOR%20IMPACT%202026.pptx)

## 5. Points de vigilance

- Ne pas transformer une projection en résultat obtenu.
- Ne pas noyer la démo dans l'architecture : le jury doit comprendre le bénéfice et voir le prototype fonctionner.
- Répondre aux limites sans les cacher ; elles renforcent la crédibilité si le périmètre est maîtrisé.
- Vérifier la durée et les consignes exactes de passage auprès de l'organisation : le document officiel fixe l'horaire du Time to Pitch, mais ne précise pas ici une durée individuelle de présentation. 📚 [`Hackathon IA for Impact _ 30h de challenge IA.pdf`](../Organisation/Hackathon%20IA%20for%20Impact _%2030h%20de%20challenge%20IA.pdf)

## 6. Checklist de sortie

- [ ] Problème, utilisateur et impact sont compris en moins d'une minute.
- [ ] Le MVP est formulé sans jargon.
- [ ] La démo suit une histoire unique.
- [ ] Les sources, limites et hypothèses sont explicables.
- [ ] La durée respecte la consigne de l'organisation.
- [ ] La démo a été répétée au moins trois fois.
- [ ] Chaque membre connaît sa phrase et son rôle.
- [ ] Un plan de secours est prêt.
