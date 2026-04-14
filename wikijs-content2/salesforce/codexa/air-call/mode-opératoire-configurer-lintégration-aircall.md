---
title: Mode Opératoire Configurer Lintégration Aircall
---

# Mode opératoire - Configurer l’intégration Aircall dans Salesforce

Afin de profiter pleinement de l’intégration Aircall et Salesforce, s’assurer que l’organisation répond aux exigences minimales.

## **Vérifications - Exigences minimales**

- Utiliser soit le [**Forfait Salesforce Enterprise ou Unlimited**](https://www.salesforce.com/editions-pricing/sales-and-service-cloud/) (pas un forfait Groupe ou Essentials), ou un forfait Professionnel en contactant votre responsable de compte Salesforce pour acheter un accès API, si vous ne souhaitez pas utiliser la fonctionnalité Omni-Channel.
    - Salesforce Enterprise - Omni-Channel
    - Pour utiliser Omni-Channel, il faut migrer vers un forfait Entreprise ou Illimité.
    
- Utiliser un [**Forfait Professionnel ou Entreprise personnalisé avec Aircall**](https://aircall.io/pricing/)
    - Forfait professionel
- Disposer de privilèges d'administrateur Salesforce de niveau supérieur ou d'autorisations de sécurité complètes au niveau de l'objet et du champ complet.
- Disposer d’une  [**Licence Salesforce**](https://help.salesforce.com/articleView?id=users_license_types_available.htm&type=0&language=en_US)
    
    Conçu pour les utilisateurs qui ont besoin d'un accès complet aux applications CRM et AppExchange standard. Les utilisateurs disposant de cette licence utilisateur ont le droit d'accéder à n'importe quelle application standard ou personnalisée.
    
    Chaque licence offre plus de stockage pour les utilisateurs des éditions Enterprise, Unlimited et Performance.
    
- Utiliser la même adresse e-mail pour Aircall et Salesforce (sinon les appels seront attribués à l'administrateur du compte au lieu du bon utilisateur).
    - Confirmation du portage

## Renvoi

Récupération des RIO de chaque numéro

Orange business lounge pour le renvoi d’appel des mobiles vers fixe.

Accès au portail à vérifier pour paramétrage.

## Installation

**Sur Salesforce**

- Se connecter

**Sur Aircall**

- [Se connecter](https://dashboard.aircall.io/login) au **Dashboard** d'Aircall
- Accéder à **Intégrations & API** et sélectionner **Salesforce v3** dans la section **Découvrir les intégrations**
- Cliquer sur **Installer l'intégration**
- Cliquer sur **Autoriser**
- Sélectionner un numéro qui doit être lié à l’intégration, puis cliquer sur **Ajouter un numéro**
    - Numéro entrant = 1 seul numéro affecté et plusieurs numéros sortants
- Choisir l’environnement : **Sandbox** ou **Production,** puis cliquer sur **Se connecter à Salesforce**
- Installer **Aircall CTI dans Salesforce** pour l'environnement Sandbox ou Production en cliquant sur **Installer CTI**

📚 Plus d’infos plus sur la configuration du **CTI Aircall [ici pour Salesforce Lightning](http://help.aircall.io/en/articles/3819640-how-to-configure-your-aircall-cti-within-salesforce-lightning)** et [**ici pour Salesforce Classic**](http://help.aircall.io/en/articles/3819641-how-to-configure-your-aircall-cti-within-salesforce-classic)

- Une fois l'installation terminée, revenir au tableau de bord Aircall et cliquer sur **Configurer CTI** pour être dirigé vers plus d'instructions sur la configuration de votre CTI
- Cliquer sur **Étape suivante**
- Installer le **package Omni-Channel** en cliquant sur **Installer le package Omni-Channel** . *Cette étape est facultative et peut être effectuée ultérieurement.*

📚 Plus d’infos sur Omni-Channel : [**Utilisation d'Aircall avec la fonctionnalité Salesforce Omni-Channel**](https://help.aircall.io/en/articles/3819628-using-aircall-with-the-salesforce-omni-channel-feature) et [**Installation de Salesforce Omni-Channel pour Aircall**](https://help.aircall.io/en/articles/3819559-installing-salesforce-omni-channel-for-aircall)

- Après l'installation, cliquer sur **Étape suivante** pour accéder à des instructions supplémentaires sur la configuration d'Omni-Channel
- Cliquer à nouveau sur **Étape suivante**
- Cliquer sur **Ouvrir les paramètres Salesforce**
- Dans Salesforce, vérifier que les cases **Visible** sont cochées pour *tous* profils, puis cliquez sur **Enregistrer**

Une fois ces étapes réalisées, votre intégration est active ! 🎉



