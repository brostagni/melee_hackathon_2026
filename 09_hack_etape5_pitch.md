# Étape 5 — Pitch & démo
> Fiche 09 · Samedi 10 octobre, 13h → 17h · Time to Pitch à 17h

📚 **Programme officiel** : [`Hackathon IA for Impact _ 30h de challenge IA.pdf`](../Organisation/Hackathon%20IA%20for%20Impact%20_%2030h%20de%20challenge%20IA.pdf) · **Méthode de pitch** : [`methodologie_hackathon_ia_for_impact.md`](../Méthodologie/methodologie_hackathon_ia_for_impact.md)

## 1. Objectif

Présenter une solution compréhensible, crédible et démontrable devant le jury. Le Time to Pitch commence samedi à 17h ; les quatre heures précédentes servent principalement aux répétitions, au chronométrage et à la préparation des réponses aux questions du jury — pas à recommencer le travail de cadrage. 📚 [`Hackathon IA for Impact _ 30h de challenge IA.pdf`](../Organisation/Hackathon%20IA%20for%20Impact%20_%2030h%20de%20challenge%20IA.pdf)

Le jury évalue notamment l'impact, la faisabilité, la viabilité et le niveau de réalisation du prototype. 📚 [`Hackathon IA for Impact _ 30h de challenge IA.pdf`](../Organisation/Hackathon%20IA%20for%20Impact%20_%2030h%20de%20challenge%20IA.pdf)

## 2. Livrables attendus à 17h

- Plan de présentation validé.
- Démo répétée dans les conditions réelles.
- Script partagé et réparti entre les intervenants.
- Réponses préparées aux questions probables.
- Vidéo ou scénario de secours si le règlement et le matériel le permettent.
- Durée ajustée à la consigne communiquée par l'organisation ou le jury.

## 3. Structure du pitch

La méthode recommande cette progression :

1. **Problème** : une douleur réelle et un utilisateur.
2. **Solution** : une phrase sans jargon.
3. **Démo** : montrer les trois étapes métier principales.
4. **Impact** : quel bénéfice concret pour l'utilisateur ; ce qui a été observé et ce qui reste à mesurer.
5. **Viabilité** : quelles conditions permettraient un usage réel (accès aux données, coûts, intégration, responsable métier).
6. **Reprise** : comment relancer le prototype et poursuivre le travail après le hackathon.
7. **Équipe** : rôles et complémentarité. 📚 [`methodologie_hackathon_ia_for_impact.md`](../Méthodologie/methodologie_hackathon_ia_for_impact.md)

> Impact, viabilité et reprise répondent à des questions distinctes. Quelques phrases suffisent pour chacune ; il n'est pas nécessaire d'inventer un modèle économique ni un gain chiffré.

### Actions, dans l'ordre

1. Reprendre l'histoire utilisateur choisie au cadrage — ne pas en inventer une nouvelle.
2. Mettre à jour le script avec les résultats réellement obtenus depuis le cadrage.
3. Limiter les slides à une idée par slide.
4. Écrire les phrases de transition et répartir les rôles.
5. Répéter au moins trois fois avec le même appareil et les mêmes données, en remettant le scénario à son état initial entre deux passages.
6. Mesurer la durée de la présentation complète (parole, manipulations et transitions) et supprimer ce qui n'aide pas à comprendre.
7. Répéter une fois la bascule vers le plan de secours.
8. Préparer les questions sur données, limites, reprise et impact.

## 4. Usage de Bob

Utiliser **Ask** pour challenger le message, puis **Agent** pour rédiger ou modifier les fichiers de pitch. 📚 [`00_bob_intro.md`](00_bob_intro.md)

### Prompt générique de script

```
[Ask] À partir du MVP, du scénario de démo et des preuves disponibles,
propose un script oral structuré en : problème, solution, démo (3 étapes métier principales),
impact, viabilité, reprise, équipe.

Contrainte : 4h de préparation disponibles (Sam 13h → 17h), pitch à 17h.
Durée maximale de la présentation complète (parole + manipulations + transitions) :
[DURÉE COMMUNIQUÉE PAR L'ORGANISATION].
Reste factuel : sépare les résultats démontrés, les hypothèses et ce qui reste à faire.
N'invente aucun chiffre. Ne présente comme réalisée aucune fonctionnalité non vérifiée ;
annonce explicitement les perspectives comme des travaux futurs.

[MVP RETENU — sortie de l'étape 1]
[SCÉNARIO DE DÉMO — parcours minimum validé en étape 4]
[PREUVES DISPONIBLES — ce qui fonctionne réellement : tests, observations, sources, échanges sponsor]
[COMMIT DE RÉFÉRENCE — version de démo validée identifiée par son commit]
```

### Prompt générique de questions jury

```
[Ask] À partir du contexte du projet ci-dessous, liste les dix questions
difficiles que le jury pourrait poser sur impact, faisabilité, viabilité,
données, limites, sécurité et reprise du prototype.
Inclure obligatoirement : « Qu'apporte précisément l'IA dans votre solution ? »
Pour chaque question, donne une réponse courte fondée uniquement sur ce
qui est réellement construit, et indique ce qui reste à valider.
Une réponse peut exposer une hypothèse ou une piste, à condition de ne pas
la présenter comme acquise.

[CONTEXTE DU PROJET — version de démonstration validée, identifiée par son commit,
et preuves disponibles : tests, observations, sources et échanges avec le sponsor]
```

### Gabarit de validation — ce que le script doit contenir

> Le script est utilisable pour le pitch si tous les points suivants sont vrais.

**Structure du pitch :**
- [ ] Problème en une phrase — une douleur réelle, un utilisateur nommé
- [ ] Solution en une phrase — sans jargon, sans acronyme non expliqué
- [ ] Démo en 3 étapes métier principales — uniquement le parcours minimum validé
- [ ] Impact : bénéfice concret observé, ce qui reste à mesurer
- [ ] Viabilité : conditions d'un usage réel (données, coûts, intégration, responsable métier)
- [ ] Reprise : comment relancer et poursuivre après le hackathon
- [ ] Équipe : rôles en 15 secondes

**Factualité :**
- [ ] Aucun résultat projeté présenté comme obtenu
- [ ] Aucune fonctionnalité non vérifiée présentée comme réalisée
- [ ] Perspectives annoncées explicitement comme travaux futurs
- [ ] Limites du prototype nommées explicitement (données mock, sources couvertes)
- [ ] Hypothèses distinguées des faits confirmés

**Durée :**
- [ ] Présentation complète chronométrée (parole, manipulations et transitions)
- [ ] Respecte la durée maximale avec une marge pour les imprévus
- [ ] Vérifier séparément si les questions du jury sont incluses dans le créneau

**Questions jury :**
- [ ] Réponse préparée à « Qu'apporte précisément l'IA dans votre solution ? »
- [ ] Réponses fondées sur la version de démonstration validée (commit de référence) et les preuves disponibles
- [ ] Ce qui reste à valider est dit explicitement — pas minimisé

**Plan de secours :**
- [ ] Qui pilote la démonstration
- [ ] Qui poursuit l'explication en cas de problème
- [ ] Critère clair pour basculer vers le secours
- [ ] Phrase indiquant qu'il s'agit d'un résultat enregistré ou simulé
- [ ] Bascule répétée au moins une fois — pas seulement le parcours idéal

**Ce qui bloque un passage convaincant :**
- Script qui présente des fonctionnalités non démontrables comme réalisées
- Durée de la présentation complète non testée dans les conditions réelles
- Absence de répétition de la bascule vers le plan de secours
- Réponses aux questions jury qui inventent des chiffres ou des certitudes

> **Note** : la sortie réelle de Bob dépend de votre MVP et de votre scénario. Vérifiez que le script correspond à ce que vous pouvez réellement montrer, et que la version de référence est bien le commit validé en étape 4 — pas simplement ce qui est présent dans le dépôt.

## 5. Points de vigilance

- Ne pas transformer une projection en résultat obtenu.
- Ne pas noyer la démo dans l'architecture : le jury doit comprendre le bénéfice et voir le prototype fonctionner.
- Répondre aux limites sans les cacher ; elles renforcent la crédibilité si le périmètre est maîtrisé.
- Éviter toute séance de dépannage en direct devant le jury ; basculer vers le secours selon le critère défini.
- Vérifier la durée et les consignes exactes de passage auprès de l'organisation : le document officiel fixe l'horaire du Time to Pitch, mais ne précise pas ici une durée individuelle de présentation. 📚 [`Hackathon IA for Impact _ 30h de challenge IA.pdf`](../Organisation/Hackathon%20IA%20for%20Impact%20_%2030h%20de%20challenge%20IA.pdf)

## 6. Checklist de sortie

- [ ] Problème, utilisateur et impact sont compris en moins d'une minute.
- [ ] Le MVP est formulé sans jargon.
- [ ] La démo suit l'histoire utilisateur choisie au cadrage.
- [ ] Les sources, limites et hypothèses sont explicables.
- [ ] Les perspectives sont annoncées comme travaux futurs, pas comme réalisations.
- [ ] La présentation complète respecte la durée maximale avec une marge pour les imprévus.
- [ ] La démo a été répétée au moins trois fois, avec remise à zéro du scénario entre chaque passage.
- [ ] Chaque membre connaît son rôle ; les intervenants maîtrisent leurs transitions.
- [ ] Un plan de secours est prêt et a été répété.
