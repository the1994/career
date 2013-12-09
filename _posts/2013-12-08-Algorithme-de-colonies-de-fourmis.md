---
layout: post
title: "Algorithme de colonies de fourmis"
description: "Algorithme de colonies de fourmis"
category: "Programming"
tags: ["Algorithm", "Java"]
---

# Préface

C'est mes reponses pour le cours Info-521:

![pic](http://media-cache-ec0.pinimg.com/736x/bf/af/f3/bfaff3316fe175034fa01da0d404f188.jpg)

# Algorithme

### Description générale

![pic](http://upload.wikimedia.org/wikipedia/commons/thumb/2/2a/Aco_TSP.svg/800px-Aco_TSP.svg.png)

L'algorithme "Système formique" optimisant le problème du voyageur de commerce:

1. une fourmi choisit un trajet, et trace une piste de phéromone.
2. l'ensemble des fourmis parcourt un certain nombre de trajets, chaque fourmis déposant une quantité de phéromone proportionnelle à la qualité du parcourts.
3. chaque arête du meilleur chemin est plus renforcée que les autres.
4. l'évaporation fait disparaître les mauvaises solutions.

### Description formelle

La régle de déplacement, appelée "règle aléatoire de transition proportionnelle", est écrite mathématiquement sous la forme suivante:

![pic](http://upload.wikimedia.org/math/0/7/c/07c690df6ac123d810621855ae3e01b2.png)

Une fois la tournée des villes éffectuée, une fourmi k dépose une quantité de phéromone sur chaque arête de son parcours:

![pic](http://upload.wikimedia.org/math/5/f/d/5fd80b97ad7e5517c636908754543a6a.png)

A la fin de chaque itération de l'algorithme, les phéromones déposées aux itérations précédentes par les fourmis s'évaporent de:

![pic](http://upload.wikimedia.org/math/b/7/5/b756d5ee105cb64b78fcaafec889177a.png)

Et à la fin de l'itération, on a la somme des phéromones qui ne se sont pas évaporées et de celles qui viennent d'être déposées:

![pic](http://upload.wikimedia.org/math/a/f/7/af7b60d7f88976977c04b25baef9c050.png)

# Code

The implementation of algorithme can be found here:

[ant](https://github.com/jesusjzp/python_training/tree/master/java/ant)

