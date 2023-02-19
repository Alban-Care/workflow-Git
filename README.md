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

