---
title: Configuration De Salesforce Et Pardot Pour Le Conn
---

# Configuration de Salesforce et Pardot pour le connecteur (1)

## Objectifs de formation

Une fois cette unité terminée, vous pourrez :

- Répertorier les étapes de configuration de Salesforce pour le connecteur Salesforce-Pardot
- Décrire l’importance de la configuration de Salesforce pour le connecteur Salesforce-Pardot
- Répertorier les étapes de configuration de Pardot pour le connecteur Salesforce-Pardot

# Configuration de Salesforce pour le connecteur

Une fois que connecteur configuré, Pardot génère une nouvelle piste dans Salesforce dès qu’un prospect est créé et qu’il n’existe n’a pas d’enregistrement de piste correspondant dans Salesforce. Pour Codexa, il est peu probable que cela arrive. 
De plus, lorsque Pardot convertit cette piste en contact dans Salesforce, il se peut que l’enregistrement de contact n’extrait pas toutes les données de l’enregistrement de piste. Pour limiter les pertes, il suffit de réaliser un mappage.

### Mappage des champs de piste personnalisés Pardot aux champs de contact dans Salesforce

En mappant vos pistes avec des champs de contact dans Salesforce, vous obtenez la garantie que Salesforce transmet correctement les données à l’enregistrement de contact.

1. Dans Salesforce, dans Configuration, cliquez sur **Gestionnaire d’objet** dans le menu.
2. Cliquez sur **Piste**.
3. Cliquez sur **Champs et relations**.
4. Cliquez sur **Mapper les champs de piste**.
5. Cliquez sur l’onglet **Contact**.
6. Cliquez sur **Enregistrer** lorsque vous avez terminé de mapper tous les champs de piste souhaités.

### Affichage des informations Pardot sur les présentations de page de piste et de contact

Lorsque vous installez l’application Pardot AppExchange, les champs Pardot et les pages Visualforce sont ajoutés mais ne s’affichent pas. Pas d’inquiétude ! 

Quelques étapes à suivre et vous pourrez les afficher. Pour afficher les champs Pardot et les pages Visualforce dans Salesforce, ajoutez-les à vos présentations de page de piste et de contact Salesforce.

### Étape 3 : Ajout de boutons Pardot personnalisés aux présentations de page Salesforce

Le bouton Envoyer à Pardot permet d’ajouter facilement des pistes ou des contacts Salesforce à Pardot. S’il existe un enregistrement correspondant, le bouton synchronise les enregistrements au lieu de créer un prospect.

1. Dans Salesforce, dans Configuration, cliquez sur **Gestionnaire d’objet** dans le menu.
2. Cliquez sur **Piste**.
3. Cliquez sur **Page de présentation** puis **Lead Layout**
4. Sélectionnez **Boutons** puis ajouter **Send to Account Engagement** et **Send Account Engagement Email** dans les boutons personnalisés.

![Untitled](/configuration-de-salesforce-et-pardot-pour-le-conn-untitled.png)

### Étape 4 : Ajout d’actions standard Pardot à Salesforce

Ajoutez des boutons et des actions Pardot à Salesforce en tant qu’actions standard dans les vues de liste et sur certaines pages d’enregistrement. Ajoutez des actions à des pages d’enregistrement dans Salesforce dans la présentation de page d’objets standards tel que l’objet Piste ou Contact.

1. Dans Salesforce, dans Configuration, cliquez sur **Gestionnaire d’objet** dans le menu.
2. Cliquez sur **Piste**.
3. Cliquez sur **Page de présentation** puis **Lead Layout**
4. Sélectionnez **Mobiles & Lightning Actions** puis ajouter **Send to Account Engagement** et **Send Account Engagement Email** dans **Actions de Salesforce mobile et de Lightning Experience**.

### Étape 5 : Accès aux données Pardot dans Salesforce accordé aux utilisateurs

Appliquez l’ensemble d’autorisations Pardot inclus avec le package AppExchange à tout utilisateur qui accède ou utilise les données Pardot dans Salesforce.

1. Dans Configuration marketing, saisissez `Ensembles d’autorisations` dans la case Recherche rapide, puis sélectionnez **Ensembles d’autorisations**.
2. Cliquez sur **Pardot**.
3. Cliquez sur **Gérer les attributions**.
4. Cliquez sur **Ajouter des attributions**.
5. Sélectionnez les utilisateurs auxquels vous souhaitez attribuer l’ensemble d’autorisations.
6. Cliquez sur **Attribuer**.

## Configuration de Pardot pour le connecteur

Cette étape a été traitée automatiquement lors de l’installation de Pardot, il n’est pas nécessaire de revenir dessus pour le moment.



