---
title: Attribuer Les Droits Sur Les Campagnes Salesforce
---

# Attribuer les droits sur les campagnes Salesforce

Comment donner un accès complet aux campagnes Salesforce à des utilisateurs ? Ce livrable couvre les permissions nécessaires et la méthode recommandée pour les attribuer de manière efficace et sécurisée.

## 1. Comprendre les niveaux d'accès aux campagnes

Dans Salesforce, l'accès aux campagnes est contrôlé par une combinaison de deux éléments principaux :

- La case "Utilisateur marketing" (Marketing User) : une case à cocher sur la fiche de l'utilisateur qui débloque des fonctionnalités spécifiques à la gestion des campagnes.
- Les permissions d'objet : elles définissent les actions de base qu'un utilisateur peut effectuer sur les enregistrements de l'objet campagne (créer, lire, modifier, supprimer - CRUD).

Pour un accès complet, ces deux éléments doivent être correctement configurés.

## 2. Méthode recommandée : utiliser un ensemble de permissions (Permission Set)

Plutôt que de modifier directement les profils, il est recommandé d'utiliser un ensemble de permissions. Cette approche est plus flexible, réutilisable et s'aligne avec les meilleures pratiques de Salesforce pour la gestion des permissions .

Ce guide se concentrera sur la création d'un ensemble de permissions dédié qui pourra être assigné à n'importe quel utilisateur nécessitant un accès complet aux campagnes.

## 3. Étapes de configuration

Voici les étapes détaillées pour donner un accès complet aux campagnes.

**Étape 1 : Activer la case "Utilisateur marketing"**

Cette case est un prérequis indispensable pour la création et l'édition des campagnes .

1.On accède à la configuration (Setup) en cliquant sur l'icône d'engrenage.

2.Dans la barre de recherche rapide, on tape "Utilisateurs" (Users) et on le sélectionne.

3.On clique sur le nom de l'utilisateur que l'on souhaite modifier.

4.On clique sur Modifier (Edit).

5.On coche la case Utilisateur marketing (Marketing User).

6.On clique sur Enregistrer (Save).

Note importante : si la case "Utilisateur marketing" est grisée, cela signifie probablement que la licence de l'utilisateur (par exemple, Salesforce Platform) ne le permet pas. Il faudra passer à une licence "Salesforce" complète pour activer cette option .

**Étape 2 : Créer et configurer l'ensemble de permissions**

Cet ensemble de permissions contiendra toutes les autorisations nécessaires pour un accès complet aux campagnes.

1.Dans la configuration (Setup), on tape "Ensembles de permissions" (Permission Sets) dans la recherche rapide et on le sélectionne.

2.On clique sur Nouveau (New).

3.On donne un nom à l'ensemble de permissions, par exemple Accès complet aux campagnes, et on clique sur Enregistrer (Save).

4.Dans la page de l'ensemble de permissions, on trouve la section Paramètres d'objet (Object Settings).

5.On clique sur Campagnes (Campaigns).

6.On clique sur Modifier (Edit).

7.On coche les cases suivantes pour accorder des droits complets (CRUD)  :

Pour un accès administratif total, on peut également cocher Modifier tout (Modify All), ce qui permet de modifier tous les enregistrements de campagne, quel que soit le propriétaire.

- Lire (Read)
- Créer (Create)
- Modifier (Edit)
- Supprimer (Delete)

8.On clique sur Enregistrer (Save).

**Étape 3 : Assigner l'ensemble de permissions aux utilisateurs**

1.Toujours dans la page de l'ensemble de permissions, on clique sur Gérer les attributions (Manage Assignments).

2.On clique sur Ajouter des attributions (Add Assignments).

3.On coche la case à côté des utilisateurs auxquels on souhaite donner ces droits.

4.On clique sur Attribuer (Assign), puis sur Terminé (Done).

Une fois ces étapes terminées, il est conseillé de demander aux utilisateurs de se déconnecter et de se reconnecter à Salesforce pour que les changements prennent effet.

## 4. Impact des paramètres de partage à l'échelle de l'organisation (OWD)

Les paramètres de partage par défaut (OWD) définissent le niveau d'accès de base aux enregistrements pour les utilisateurs qui n'en sont pas propriétaires .

- Si l'OWD pour l'objet campagne est défini sur privé (Private), les utilisateurs ne verront par défaut que les campagnes qu'ils possèdent, même avec l'ensemble de permissions ci-dessus.
- Pour que les utilisateurs puissent voir toutes les campagnes, l'OWD doit être défini sur lecture publique seule (Public Read Only) ou lecture/écriture publique (Public Read/Write).

Pour vérifier et modifier l'OWD :

1.Dans la configuration (Setup), on recherche "Paramètres de partage" (Sharing Settings).

2.On clique sur Modifier (Edit) dans la section des paramètres par défaut de l'organisation.

3.On trouve l'objet Campagne et on ajuste l'accès par défaut selon les besoins.

## 5. Tableau récapitulatif des permissions

| Permission | Case "Utilisateur marketing" | Ensemble de permissions (CRUD) | Effet |
| --- | --- | --- | --- |
| Lecture seule | Non requise | Lecture | L'utilisateur peut voir les campagnes (selon l'OWD). |
| Création/édition | Requise | Créer, Lire, Modifier | L'utilisateur peut créer et modifier des campagnes. |
| Accès complet | Requise | Créer, Lire, Modifier, Supprimer | L'utilisateur a un contrôle total sur les campagnes qu'il peut voir. |



