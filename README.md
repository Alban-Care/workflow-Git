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
