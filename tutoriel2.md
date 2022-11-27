---
title: Tutoriel Git / GitHub (3)
author: Pierre Poulain
license: Creative Commons Attribution-ShareAlike (CC BY-SA 4.0)
---

# Partie 3 : Un peu de spéléo

*Remarque : cette section est l'occasion d'explorer l'historique d'un dépôt git et d'aborder une nouvelle commande, `git show`.*

J'ai développé il y a quelques années le logiciel [autoclasswrapper](https://github.com/pierrepo/autoclasswrapper), un wrapper Python pour le programme de classification bayesienne [AutoClass C](https://ti.arc.nasa.gov/tech/rse/synthesis-projects-applications/autoclass/autoclass-c/). Ce travail a été publié dans *The Journal of Open Source Software* en [2019](https://joss.theoj.org/papers/10.21105/joss.01390).

Vous allez télécharger l'intégralité du dépôt git de ce projet, explorer son historique et observer comment j'ai développé ce programme. Vous aurez la possibilité de modifier localement (sur adenine) ce projet mais vous ne pourrez pas envoyer vos modifications sur le dépôt initial (avec la commande `git push`) car vous n'en avez pas les droits.

Depuis un terminal sur adenine, déplacez-vous dans le répertoire de base de votre environnement `meg_m1_geno_bioinfo` :
```bash
$ cd $HOME/meg_m1_geno_bioinfo
```

🔔 Rappels :

- Ne tapez pas le caractère `$` en début de ligne et faites attention aux majuscules et aux minuscules.
- Copiez / collez les commandes pour aller plus vite et faire moins d'erreur. Ne copiez / collez pas non plus n'importe quoi, lisez les consignes avec attention **avec d'exécuter une commande**.

Vérifiez avec la commande `pwd` que vous obtenez quelque chose du type :
```
$ pwd
/srv/home/ppoulain/meg_m1_geno_bioinfo
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

### De quand date le dernier *commit* et quel est son *hash* ?

Astuce : combinez les commandes `git log` et `head`.


### Quand a été créé le tout premier *commit* ?

Astuce : combinez les commandes `git log` et `tail`.


### Combien de *commits* ont été enregistrés jusqu'à présent ?

Astuce : combinez les commandes `git log`, `grep -c` et un mot-clé pertinent.

Vérifiez cette valeur sur le site du dépôt : <https://github.com/pierrepo/autoclasswrapper>

### Trouvez dans quel *commit* j'ai ajouté la possibilité de construire un dendrogramme

Astuces : 

- Combinez les commandes `git log`, `grep -B4` et un mot-clé pertinent.
- Pour trouver le bon mot-clé (en anglais), jetez un oeil à la page [dendrogramme](https://en.wikipedia.org/wiki/Dendrogram) sur Wikipédia.


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
