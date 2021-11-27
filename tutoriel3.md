---
title: Tutoriel Git / GitHub (4)
author: Pierre Poulain
license: Creative Commons Attribution-ShareAlike (CC BY-SA 4.0)
---

# Partie 4 : Branches

## 4.1 Création de branche

Revisionez la vidéo « [Débuter avec Git et Github en 30 min](https://youtu.be/hPfgekYUKgk?t=634) » à partir de 10'34 sur les branches.

Depuis un terminal sur adenine, revenez dans le répertoire `meg-test` :
```bash
$ cd $HOME/meg_m1_gb_r/meg-test
```

🔔 Rappels :

- Ne tapez pas le caractère `$` en début de ligne et faites attention aux majuscules et aux minuscules.
- Copiez / collez les commandes pour aller plus vite et faire moins d'erreur. Ne copiez / collez pas non plus n'importe quoi, lisez les consignes avec attention avec d'exécuter une commande.

Vérifiez que votre dépôt est « propre », c'est-à-dire qu'il ne contient pas de fichier modifié non commité.

```bash
$ git status
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean
```

Créez une nouvelle branche, par exemple *nouveau-fichier* :

```bash
$ git branch nouveau-fichier
```

Vérifiez que cette branche existe bien :

```bash
$ git branch
* master
  nouveau-fichier
```

Le symbole `*` à gauche de *master* indique que la branche courante est *master*.

Basculez maintenant sur la branche que vous venez de créer :

```bash
$ git checkout nouveau-fichier
```

Vérifiez que vous êtes désormais sur la bonne branche :

```bash
$ git branch
  master
* nouveau-fichier
```

Le symbole `*` à gauche de *nouveau-fichier* indique que la branche courante est *nouveau-fichier*.

Créez un nouveau fichier `test2.txt` avec le texte qui vous convient :

```bash
$ echo "Nouveau fichier pour tester une branche" > test2.txt
```

Demandez ensuite à git de prendre en compte votre nouveau fichier :

```bash
$ git add test2.txt
```

Puis réalisez un premier *commit* :

```bash
$ git commit -m "Création d'un nouveau fichier"
```

Réalisez plusieurs *commits* en modifiant à chaque fois le fichier `test2.txt`, par exemple :

```bash
$ echo "Une ligne supplémentaire" >> test2.txt
$ git add test2.txt
$ git commit -m "Ajout d'une ligne"
$ echo "Et encore une !" >> test2.txt
$ git add test2.txt
$ git commit -m "Ajout d'une dernière ligne"
```

## 4.2 Fusion

Revenez sur la branche *master* et vérifiez que le fichier `test2.txt` n'est **pas** présent dans votre répertoire :

```bash
$ git checkout master
$ ls
```

Les branches fonctionnent comme des sortes de « réalités parallèles ». Il est donc normal que le fichier que vous avez créé dans la branche *nouveau-fichier* n'apparaisse pas dans la branche *master*.

Fusionnez maintenant sur la branche actuelle (*master*) la branche *nouveau-fichier* :

```bash
$ git merge nouveau-fichier
```

Vérifiez que le fichier `test2.txt` est présent et contient vos modifications :

```bash
$ ls
$ cat test2.txt
```

La branche *nouveau-fichier* ne sert plus à rien car les modifications qu'elle contenait ont été fusionnées dans la branche *master*.
Vous pouvez donc supprimer la branche *nouveau-fichier* :

```bash
$ git branch -d nouveau-fichier
```

Puis vérifiez qu'elle a bien été détruite :

```bash
$ git branch
* master
```

Enfin, envoyez toutes vos modifications sur GitHub :

```bash
$ git push
```

Vérifiez que le dépôt sur GitHub a bien été mis à jour.


# Partie 6 : Collaboration avec GitHub

Revisionez la vidéo « [Débuter avec Git et Github en 30 min](https://youtu.be/hPfgekYUKgk?t=1058) » à partir de 17'38 sur le dépôt distant et GitHub.

Explorez le travail collaboratif avec une ou plusieurs autres personnes. 

Remarque : Comme votre dépôt est déjà sur GitHub, vous n'aurez pas besoin d'exécuter la commande `git remote add...`

