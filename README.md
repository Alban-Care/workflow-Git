# workflow-Git

## Branche de développement

### Création de la branch `develop`

```bash
git branch develop
git push -u origin develop
```

### Basculer sur la branch `develop`

```bash
git switch develop
```

## Branches de fonctionnalité

### Création d'une branche de fonctionnalité

```bash
git switch develop
git checkout -b feature/feature_branch
```

### Pusher une branche de fonctionnalité (sauvegarde/collaboration)

```bash
git push
```

### Terminer une branche de fonctionnalité

Losque le travail de développement est terminé sur la fonctionnalité, l'étape suivante consiste à merger la branche `feature` dans la branche `develop`.

```bash
# Se positionner sur la branch develop
git checkout develop
# Merger la branch feature sur la branch develop
git merge feature/feature_branch
```

## Branches de livraison

Une fois que `develop` a acquis suffisament de fonctionnalités en vue d'une livraision, on creer une branche `release`. Plus aucune fonctionnalité ne sera ajoutée à cette branche elle sera uniquement dédiée aux corrections de bugs, à la génération de documentation et autres tâches de livraison.

```bash
# Se positionner sur la branch develop
git switch develop
# se positionner automatiquement après l'avoir crée sur la branche de release 0.1.0 (en la prefixant par "release/")
git checkout -b release/0.1.0
```

