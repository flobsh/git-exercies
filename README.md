# Introduction à Git

Ce dépôt a pour objectif de vous familiariser avec Git au travers de petits exercices.

## Récupération

Récupérez ce dépôt avec la commande `git clone `

## Commits

Essayez de modifier le fichier `main.py`, par exemple en changeant le texte `Hello World` de la fonction `main`.

Tapez la commande `git status`. Qu'observez-vous ?

Tapez maintenant la commande `git add main.py`, puis à nouveau `git status`. Qu'est-ce qui a changé ?

Vous êtes maintenant prêt à faire un commit. Tapez `git commit -m "modification main.py"`.
Tapez `git log` pour observer l'historique des commmits.

## Branches

Créez une branche `modifications` :

```bash
git switch -c modifications
```

Vous êtes maintenant sur la branche `modifications` et tous les nouveaux commits appartiendront à cette branche.
Modifiez à nouveau le fichier `main.py`, par exemple en ajoutant `print(2 + 2)` dans la fonction `main`.

Faites un commit pour enregistrer cette modification.

### Observer les différences entre les branches

Basculez sur la branche `main` :

```bash
git switch main
```

Ouvrez le fichier `main.py`. Qu'observez-vous ?

Affichez les différences entre la branche `main` et la branche `modifications` avec la commande suivante :

```bash
git diff modifications
```

### Fusionner les modifications

Fusionnez les modification de la branche `modifications` dans la branche `main` :

```bash
# Assurez-vous que vous êtes bien dans la branche `main`
git switch main
# Fusionnez les modifications
git merge modifications
```

Ouvrez le fichier `main.py`. Qu'observez-vous ?

### Rebase

Il y a dans ce dépôt une branche `math`. Basculez dessus avec la commande `git switch`

Cette branche `math` a été créée avant les modifications que vous avez effectué dans `main.py`.
Utilisez la commande `git rebase` pour mettre à jour la branche `math` avec les modifications de la branche `main`.

## Conflits

Il se peut que lors de la fusion (*merge*) ou du rebase, il y ait des confilts entre plusieurs modifications.
Cela arrive si, par exemple, deux personnes ont modifier la même ligne de code dans deux branches différentes.

Lors du **merge** ou du **rebase**, Git va détecter ces conflits et vous proposer de les solutionner en conservant la version qui vous convient.

Placez-vous dans la branche `main` et fusionnez la branche `conflict`. Git devrait vous ouvrir un éditeur pour vous inviter à résoudre le conflit
concernant la ligne 2 du fichier `main.py`. Conservez la ligne que vous souhaitez (ou les deux), puis enregistrez et fermez le fichier.
