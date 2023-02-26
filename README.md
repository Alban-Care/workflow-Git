La branche `main` stocke l'historique officiel et abrégé des versions de l'application et ne subit aucune modification durant les phases de développement.

## Branche de développement

La branche `develop` sert de branche d'intégration pour les fonctionnalités, elle contiendra l'historique complet du projet.

### Création de la branch `develop`

```bash
# créer une branche dévelop
git branch develop
# pousser la branch develop
git push -u origin develop
```

## Branches de fonctionnalité

Il convient de créer une branche pour chaque fonctionnalité.

### Création d'une branche de fonctionnalité

Il est important d'être positionné sur la branch develop avant de créer la branche de fonctionnalité.

```bash
# se positionner sur la branche dévelop
git switch develop
# se positionner automatiquement après l'avoir crée sur la branche feature_branch (en la prefixant par "feature/")
git checkout -b feature/feature_branch
```

### Pusher une branche de fonctionnalité (sauvegarde/collaboration)

```bash
# pousser la branch feature
git push
```

### Terminer une branche de fonctionnalité

Losque le travail de développement est terminé sur la fonctionnalité, l'étape suivante consiste à merger la branche `feature` dans la branche `develop`.

```bash
# Se positionner sur la branch develop
git switch develop
# Merger la branch feature sur la branch develop
git merge feature/feature_branch
```

## Branches de livraison

Une fois que `develop` a acquis suffisament de fonctionnalités en vue d'une livraision, on creer une branche `release`. Plus aucune fonctionnalité ne sera ajoutée à cette branche elle sera uniquement dédiée aux corrections de bugs, à la génération de documentation et autres tâches de livraison.

```bash
# Se positionner sur la branch develop
git switch develop
# Se positionner automatiquement après l'avoir crée sur la branche de release 0.1.0 (en la prefixant par "release/")
git checkout -b release/0.1.0
```

### Merger une branche de livraison

```bash
# Se positionner sur la branch main
git switch main
# Merger la branche release sur main pour la mise en production
git merge release/0.1.0
# Se positionner sur la branch develop
git switch develop
# Merger la branche release sur develop pour mettre à jour la branche qui a pu évoluer entre la création de la branche release et la livraison
git merge release/0.1.0
```

## Ma chronologie quotidienne pour bien démarrer ma journée de code (et vivre amoureusement avec git)
Attention, le but ici est de vous décrire ma façon de faire (dans des cas biens particuliers). Ce n'est pas LA façon de faire ! 
Cette description contient une partie ou je propose un `rebase`. Il faut garder à l'esprit que le rebase n'est pas une opération anodine, s'il vous plaît lisé attentivement cet article : [rebase](https://www.atlassian.com/fr/git/tutorials/rewriting-history/git-rebase)

Prêt ? GO ! GO ! GO !

- Je me prépare un café/thé (ça va être utile pour la suite)
- Je vérifie que je n'ai aucun fichier en attente de `commit` sur ma branche de travail (en cas de manque d'inspiration WIP est mon ami !)
- Si ma branche est sauvegardée sur le dépôt distant, je met à jour mon dépôt distant `git push`. Si non... euh je ne fais pas :) !
- Je switch sur la branch develop `git switch develop`
- Je met à jour mon dépôt local avec le dépôt distant `git pull` (il peut arriver qu'un collègue ait eu une insomnie et merger son travail dans la nuit)

__Cas n°1 : mon dépôt local est à jour avec mon dépôt local__

  ```bash
  Already up to date.
  ```
  
- Je retroune sur ma branche de travail, café/thé et... Code, commit, répéte !

__Cas n°2 : mon dépôt locla se met à jour avec le dépôt distant__

- Je bois une gorgée de café/thé (j'avais prévenu de le faire avant !) tout en faisant le point sur les fichiers qui ont été modifiés pendant que je m'enivrais avec Nótt !

__Cas n°1 : Je n'utilise pas et n'utiliserais pas les fichiers modifiés__

- Je retroune sur ma branche de travail, café/thé et... Code, commit, répéte ! (Attention de garder à l'esprit les fichiers qui ont été mis à jour)

__Cas n°2 : Ouch ! Certains fichiers modifiés dans la nuit risques d'affecter mon code sur ma branche de travail !__

- Je rebois une belle gorgée de café/thé et j'attaque une lecture des commits à la recherche de changement(s) impactant(s) ma branche de travail...

__Cas n°1 : Pas de souci à première vue__

- Je retroune sur ma branche de travail, café/thé et... Code, commit, répéte, tout gardant à l'esprit les fichiers qui ont été mis à jour !

__Cas n°2 : Une partie du code va impacter mon travail__

- J'imagine que je contacterai mon collègue pour m'entretenir avec lui sur ces changements et trouver un bon compromis ! Paix, amour et code !

- Je retourne sur ma branche de travail (les mains moites !)
- Je [rebase](https://www.atlassian.com/fr/git/tutorials/rewriting-history/git-rebase) ma branche avec la "nouvelle" branche `develop` (je tire les changements de `develop`pour pouvoir les utiliser dans ma branche de travail `git rebase develop`)
- Je corrige les conflits de fusion s'il y en a... 
- Je commit (et pousse sur ma branche distante si elle extiste) tous ces changements et café !
- Cool, je peux enfin reprendre mes activités sur ma branche qui sont...  Code, commit, répéte !

Voilà MON fonctionnement, s'il vous plaît, en toute circonstance adaptez ces quelques lignes !
