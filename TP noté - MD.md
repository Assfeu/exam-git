---
title: Examen Git™ pour l'administrateur système
author: Tom Avenel
date: 2022-2023
footer: © 2023 Tom Avenel under CC BY-SA 4.0
keywords:
- git
- ci
- devops
---

\newpage{}

# Consignes globales

- Sauf mention explicite, chaque question nécessite l'exécution d'une ou plusieurs commandes `git` pour atteindre le résultat attendu. **Toutes** ces lignes de commandes devront être documentées dans le rapport du TP (et uniquement celles répondant à la question).
- L'utilisation d'un client graphique pour visualiser l'état du dépôt est cependant autorisé mais tous les changements dans le dépôt devront être réalisés par la ligne de commandes `git`.
- Lorsque des _Pull Request_ ou _Merge Request_ sont nécessaires, celles-ci seront approuvées par vous-même depuis l'interface `Github` avant intégration des changements dans la branche de destination.
- Ne supprimez aucune branche de travail, même après les avoir fusionnées (merge), sauf éventuellement celles ne répondant pas aux questions.
- **Pour tous les dépôts de code sur Github, ajouter le formateur comme collaborateur du dépôt : `@avenelt-esgi`**.
- Aucune modification future n'est autoriśee dans les dépôts Github créés pendant l'examen après l'heure de fin de l'examen, et jusqu'à notification du formateur.
- Déposer le document de réponses **en ayant renseigné votre NOM et PRÉNOM** dans la branche principale du dépôt Git.

# Infrastructure-as-Code : un dépôt de code Ansible versionné et testé

NOM : TORELLI

Prénom : Gaëtan

## Création du dépôt de code (2 pts)

- Créer un nouveau dépôt de code `git` hébergé en ligne sur `Github` nommé `exam-git` (aucune réponse attendue à cette étape).
- Ajouter le formateur comme contributeur du dépôt (compte **avenelt-esgi**).
- Cloner ce dépôt sur votre machine personnelle. Quelle est la différence entre ce dépôt de code et le dépot distant sur `Github` ?
La différence et que le dépôt local et différent du dépôt en ligne qui est héberger sur un serveur et donc les modification se feront d'abord en local puis il faudra envoyer les modification au dépôt en ligne.
- Quelle est la branche courante ? Comment avoir cette information ?
La branche courante et main et pour avoir cette information il faut entrer la commande suivante 'git branch'.

## Ajout d'un fichier dans l'historique (2 pts)

- Copier ce fichier avec les réponses de la première partie à la racine du dépôt de code (aucune réponse attendue à cette étape).
- Ajouter une première version de ce fichier dans le dépôt local.
- Vérifer que ce fichier a été correctement ajouté au dépôt (par la ligne de commandes git).
- Synchroniser le dépôt distant pour y intégrer les changements du dépôt local.

## Branche `ansible` (2 pts)

- Créer une branche `ansible` et y copier le contenu des 2 fichiers du tp Ansible dans un répertoire `ansible` (fichier `mes_hosts` et `mon_playbook`).
- Mettre à jour les 2 fichiers avec la description de votre environnement (utiliser des valeurs factices si vous n'avez pas d'environnement compatible pour une exécution d'un playbook Ansible) et intégrer les changements dans la branche.

## Préparation d'un hook de pre-push (3 pts)

Nous allons préparer un git hook à exécuter juste avant l'opération de push. Dans cette partie, on créera uniquement le script sans l'activer pour l'instant.

Ce script servira à afficher à l'écran un résumé des 5 derniers commits réalisés (une ligne par commit). Pour rappel, un hook pré-push est un shell script **exécutable** nommé : `.git/hooks/pre-push`. Afin de faciliter le versionning de ce script, nous allons commencer par créer un fichier `pre-push` dans un répertoire `scripts` à la racine du projet.

- Créer une branche `hook` pour versionner le script ;
- Créer le script `scripts/pre-push` dans la branche : on pourra notamment utiliser l'option `--oneline` de la commande qui nous intéresse ici.

On pourra donc utiliser un script de la forme :

```sh
#!/bin/sh

echo "Liste des derniers commits :"
echo "$(git .........)"
```

## Action GitHub (6 pts)

Créer 2 actions dans GitHub pour implémenter des vérifications sur les fichiers du dépôt (aucune réponse attendue à cette étape) :

- Une action qui vérifie les fichiers Ansible dans la branche `ansible` par le biais d'un linter ;
- Une action qui vérifie la grammaire du script de pre-push : `scripts/pre-push` depuis la branche `hooks` (on pourra utiliser l'action <https://github.com/marketplace/actions/shell-linter> ).

## Activation du hook (2 pts)

Une fois la vérification du script de pre-push correcte :

- copier le script `scripts/pre-push` à l'emplacement : `.git/hooks/pre-push` (à réaliser sans commande git - aucune réponse attentud à cette étape).
- créer un nouveau commit et vérifier que l'opération de `push` affiche bien la liste des commits ;
- fusionner la branche `hooks` dans la branche principale.

## Pull-request (3 pts)

- Effectuer une pull-request des changements réalisés dans la branche `ansible` et l'approuver soi-même (aucune réponse attendue à cette étape).
- Intégrer les changements de la branche `ansible` dans la branche principale du projet.

## Dépôt des réponses

**Ajouter la dernière version de ce document contenant les réponses aux différentes questions dans la branche principale du dépôt Git, à la fin de l'examen.**

