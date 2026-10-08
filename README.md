# MiniTâches

> Mes tâches, simplement.

## Présentation du produit

MiniTâches est une application mobile destinée aux étudiants.
Elle permet de noter leurs tâches et de suivre leur avancement
dans une liste simple.

Le MVP permet de :

- consulter les tâches ;
- ajouter une tâche ;
- marquer une tâche comme terminée ou à faire ;
- supprimer une tâche.

## Identité du produit

Consulter la [fiche complète de l’identité du produit](docs/01_Idee_et_identite_du_produit.md).

## 1. L’idée et l’identité de l’application

**Nom : MiniTâches**  
**Signature : « Mes tâches, simplement. »**  
**Public : un étudiant qui veut conserver une courte liste de choses à faire.**

L’utilisateur ouvre l’application, consulte sa liste, ajoute une tâche, change son état terminé et supprime une tâche devenue inutile. L’interface montre une seule page principale, un petit formulaire d’ajout et une confirmation de suppression.

> « Nous voulons aider un étudiant à garder une liste claire de ce qu’il a à faire. L’application doit être rapide à comprendre et les tâches doivent rester disponibles quand il la ferme puis la rouvre. »

**Objectif de produit :** permettre à un étudiant de gérer une liste persistante depuis son téléphone, avec les quatre opérations essentielles de consultation, ajout, changement d’état et suppression.

### Une architecture proche de DA2M

| Élément           | Responsabilité                                                       |
| ----------------- | -------------------------------------------------------------------- |
| Flutter / Dart    | Afficher les écrans, valider la saisie et envoyer les requêtes HTTP  |
| TaskService       | Centraliser les appels à l’API et transformer le JSON en objets Dart |
| Node.js / Express | Recevoir les requêtes, appliquer les règles et répondre en JSON      |
| MongoDB           | Conserver les tâches côté serveur                                    |

Flutter communique avec Express; Express communique avec MongoDB. La chaîne de connexion MongoDB reste dans la configuration du serveur.

Le modèle public d’une tâche contient `id` (chaîne), `title` (texte) et `done` (booléen). Le titre contient de 1 à 80 caractères après suppression des espaces au début et à la fin.
