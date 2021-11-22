---
title: Tutoriel Git / GitHub (2)
author: Pierre Poulain
license: Creative Commons Attribution-ShareAlike (CC BY-SA 4.0)
---



# Partie 3 : Un peu de spéléo

*Remarque : cette section est l'occasion d'explorer l'historique d'un dépôt git et d'aborder une nouvelle commande, `git show`.*

J'ai développé il y a quelques années [autoclasswrapper](https://github.com/pierrepo/autoclasswrapper), un wrapper Python pour le programme de classification bayesienne  [AutoClass C](https://ti.arc.nasa.gov/tech/rse/synthesis-projects-applications/autoclass/autoclass-c/). Ce travail a été publié dans *The Journal of Open Source Software* en [2019](https://joss.theoj.org/papers/10.21105/joss.01390).

Vous allez télécharger l'intégralité du dépôt git de ce projet, explorer son historique et observer comment j'ai développé ce projet. Vous aurez la possibilité de modifier localement (sur adenine) ce projet mais vous ne pourrez pas envoyer vos modifications sur le dépôt initial (avec la commande `git push`) car vous n'en avez pas les droits.

Depuis votre terminal sur adenine, déplacez-vous dans le répertoire de base de votre environnement `meg_m1_gb_r` :
```bash
$ cd $HOME/meg_m1_gb_r
```

Vérifiez avec la commande `pwd` que vous obtenez quelque chose du type :
```
$ pwd
/srv/home/ppoulain/meg_m1_gb_r
```
avec `ppoulain` qui est remplacé par votre *login* sur adenine.


Téléchargez l'intégralité du projet *autoclasswrapper* avec la commande :
```bash
$ git clone https://github.com/pierrepo/autoclasswrapper.git
```

puis déplacez-vous dans le répertoire du projet :
```bash
$ cd autoclasswrapper
```

Utilisez maintenant différentes commandes git pour explorer le projet 
et répondre aux questions suivantes.
### De quand date le dernier *commit* ?

Astuce : combinez les commandes `git log` et `head`.


### Quand a été créé le tout premier *commit* ?

Astuce : combinez les commandes `git log` et `tail`.


### Combien de *commits* ont été enregistrés jusqu'à présent ?

Astuce : combinez les commandes `git log`, `grep -c` et un mot-clé pertinent.

Vérifiez cette valeur sur le site du dépôt : <https://github.com/pierrepo/autoclasswrapper>

### Trouvez dans quel *commit* j'ai ajouté la possibilité de construire un dendrogramme

Astuces : 

- Combinez les commandes `git log`, `grep -B4` et un mot-clé pertinent.
- Jetez un oeil à la page [dendrogramme](https://en.wikipedia.org/wiki/Dendrogram) sur Wikipédia.


### Combien de fichiers ont été modifiés dans le *commit* correspondant ?

Utilisez pour cela la commande :

```
$ git show --name-only <identifiant-du-commit>
```

avec `<identifiant-du-commit>` l'identifiant du *commit* intéressant. 

Aide : il commence par `2d1c` 😉

Notez la différence avec la commande :
```
$ git show <identifiant-du-commit>
```
Pressez la touche <kbd>q</kbd> pour quitter.


# Partie 4 : Branches

## 4.1 Création de branche

Revisionez la vidéo « [Débuter avec Git et Github en 30 min](https://youtu.be/hPfgekYUKgk?t=634) » à partir de 10'34 sur les branches.

Depuis votre terminal sur adenine, revenez dans le répertoire `meg-test` :
```bash
$ cd $HOME/meg_m1_gb_r/meg-test
```

Vérifiez que votre dépôt est « propre », c'est-à-dire sans fichier modifié mais non commité.
```
$ git status
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

Réalisez plusieurs *commits* en modifiant à chaque fois le fichier `test2.txt`, par exemple :

```bash
$ git add test2.txt
$ git commit -m "Création d'un nouveau fichier"
$ echo "Une ligne supplémentaire" >> test2.txt
$ git add test2.txt
$ git commit -m "Ajout d'une ligne"
```

## 4.2 Fusion

Revenez sur la branche *master* et vérifiez que le fichier `test2.txt` n'est **pas** présent :

```bash
$ git checkout master
$ ls
```

Fusionnez maintenant sur *master* la branche *nouveau-fichier* :

```bash
$ git merge nouveau-fichier
```

Vérifiez que le fichier `test2.txt` est présent et contient vos modifications :

```bash
$ ls
$ cat test2.txt
```

Supprimez l'ancienne branche *nouveau-fichier* :

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

