---
title: Installation Du Connecteur Et Activation De Pardot
---

# Installation du connecteur et activation de Pardot (1)

# Objectifs de formation

- Configurer l’utilisateur de connecteur
- Installer l’application Pardot AppExchange
- Activer Pardot dans Salesforce
- Configurer et réactiver le connecteur Salesforce-Pardot dans Pardot

### Configuration de l’utilisateur de connecteur

Avant de configurer l’utilisateur de connecteur, assurez-vous qu’il dispose des autorisations suivantes.

- API activée
- Gestion des profils et ensembles d’autorisations
- Afficher tous les utilisateurs
- Afficher la configuration

## Installation de l’application Pardot AppExchange

Seul un administrateur Salesforce sur la plate-forme Salesforce peut installer et activer Pardot. Pour effectuer la configuration, l’administrateur Salesforce nomme un administrateur Pardot qui peut configurer le côté Pardot du compte. La bonne nouvelle, c’est qu’un administrateur Pardot n’a pas besoin d’être un administrateur Salesforce.

Commençons dès maintenant à télécharger, à installer et à configurer les ensembles d’autorisations appropriés.

1. Cliquez sur le [lien d’installation](http://www2.pardot.com/notes/pardot-appexchange-package-download-and-release-notes/) pour vous assurer que votre compte Salesforce est mis à jour avec une application personnalisée, un onglet personnalisé et des champs personnalisés sous les pistes et les contacts. Vous devrez peut-être modifier votre vue pour que les champs s’affichent.
2. Passez en revue toutes les actions et cliquez sur **Installer**.
3. Dans l’assistant d’installation, sélectionnez **Accorder l’accès uniquement aux administrateurs**.

Avant d’activer Pardot, accordez à l’utilisateur attribué en tant qu’administrateur Pardot l’accès à l’application Pardot Lightning. Voici les étapes de base à suivre pour configurer l’application Pardot Lightning.

1. Accordez aux utilisateurs l’accès à l’application connectée Pardot.
2. Attribuez l’ensemble d’autorisations Utilisateur de Sales Cloud ou Utilisateur CRM.
3. Mettez l’application à la disposition des utilisateurs.

Maintenant qu’elle est activée, l’application apparaît dans le lanceur d’application pour tous les utilisateurs dotés de l’ensemble d’autorisations Utilisateur de Sales Cloud, auxquels l’autorisation d’application a été attribuée.

# Activation de Pardot

Un administrateur Salesforce doit activer les nouvelles unités commerciales Pardot et nommer un administrateur Pardot. Si vous avez plusieurs unités commerciales Pardot, assurez-vous d’affecter un administrateur Pardot à chacune d’entre elles.

Notez que le recours à un partenaire pour aider à activer Pardot est fortement recommandé. Pour plus d’informations, reportez-vous au guide de configuration du connecteur Salesforce dans la section Ressources.

# Configuration et réactivation du connecteur Salesforce-Pardot dans Pardot

À sa création, l’état du connecteur Salesforce-Pardot est en pause. Un administrateur Pardot doit configurer le connecteur et le réactiver pour commencer la synchronisation des données. Le connecteur Salesforce-Pardot utilise l’utilisateur d’intégration pour la synchronisation. Si vous souhaitez synchroniser les enregistrements de manière sélective, remplacez l’utilisateur du connecteur par un utilisateur disposant des autorisations appropriées ou configurez le partage de données marketing avant de reprendre la synchronisation.

Les pistes et les contacts de Salesforce qui n’existent pas dans Pardot ne sont pas automatiquement synchronisés avec Pardot. Vous devez importer ces enregistrements pour établir une synchronisation.

Dans l’unité suivante, nous allons apprendre à configurer Salesforce pour le connecteur Salesforce-Pardot.

# Ressources

- [*Site Pardot* : Guide de configuration du connecteur Salesforce](https://www.pardot.com/training/salesforce-connector-setup-guide/)
    
    [Aide Salesforce : Installation de l’application Pardot AppExchange](https://help.salesforce.com/articleView?id=pardot_sf_connector_setup_install_package.htm&type=5)
    
- [*Aide Salesforce :* Test du connecteur Salesforce-Pardot](https://help.salesforce.com/articleView?id=pardot_sf_connector_setup_test_connector.htm&type=5)
- [*Aide Salesforce :* Configuration de l’utilisateur de connecteur](https://help.salesforce.com/articleView?id=pardot_sf_connector_setup_connector_user_parent.htm&type=5)
- [*Aide Salesforce :* Partage de données marketing](https://help.salesforce.com/apex/HTViewHelpDoc?id=pardot_sf_connector_setup_selective_sync_config.htm)
- [*Site Pardot :* Guide de configuration du connecteur Salesforce](https://www.pardot.com/training/salesforce-connector-setup-guide/) [Site Pardot : Implémentation de la synchronisation sélective](https://pardot.hubs.vidyard.com/watch/p1hzfmynjXnUB79qH9NKZ3)



