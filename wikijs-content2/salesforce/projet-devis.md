---
title: Projet Devis
---

# Projet Devis

### **1. Contexte et Objectifs**

**Contexte** :

Codexa utilise actuellement un tableur Excel ("outil devis.xlsx") pour calculer des devis clients. Ce processus manuel est chronophage, sujet aux erreurs, et difficile à maintenir. L’objectif est d’automatiser ce processus dans Salesforce pour :

- Centraliser les données.
- Automatiser les calculs complexes.
- Améliorer la traçabilité et la collaboration.

**Objectifs** :

- Reproduire les fonctionnalités de l’Excel dans Salesforce.
- Créer un objet "Devis" avec des champs personnalisés et des flux automatisés.
- Garantir la cohérence des calculs (tarifs, budgets, remises).
- Faciliter la génération de devis PDF directement dans Salesforce avec pdf Butler.

### **2. Périmètre du projet**

**Fonctionnalités incluses** :

- Création/mise à jour de devis avec saisie des paramètres (client, type de prestation, durée, etc.).
- Calcul automatique des tarifs horaires (HT/TTC), budgets, et remises.
- Gestion des données de référence (tarifs, lieux, seuils) via des champs dédiés.
- Génération de devis au format PDF.

**Hors périmètre** :

- Gestion des signatures électroniques déjà en place avec DocuSign.

### **3. Acteurs et rôles**

| **Acteur** | **Rôle** |
| --- | --- |
| Equipe commerciale | Saisie des devis, consultation des budgets. |
| **Administrateur Salesforce** | Configuration des flows et maintenance. |

### **4. Spécifications techniques**

Mapping Excel > Salesforce

| Champ Salesforce | Condition | Champ dynamique | Objet | Type | Valeur(s) |
| --- | --- | --- | --- | --- | --- |
| N_d_Affaire__c | / | [[!AFFAIREE!]] | Opportunité | SINGLE | POTXXXX |
| Date_du_devis__c | / | [[!DATE!]] | Devis | SINGLE | XX/XX/XX |
| Account.Name | / | [[!CLIENT!]] | Opportunité | SINGLE | TEXTE |
| FirstName | / | [[!CLIENT_P!]] | Contact | SINGLE | TEXTE |
| LastName | / | [[!CLIENT_N!]] | Contact | SINGLE | TEXTE |
| Owner.Name | / | [[!COMMERCIAL!]] | User | SINGLE | TEXTE |
| Owner.Phone | / | [[!PHONE!]] | User | SINGLE | NUMERO DE TELEPHONE |
| Owner.Mobile | / | [[!MOBILE!]] | User | SINGLE | NUMERO DE MOBILE |
| Owner.Email | / | [[!EMAIL!]] | User | SINGLE | EMAIL |
| TypeReunion__c | / | [[!REUNION!]] | Opportunité | SINGLE | Autre, CA, Commission et comité, CSE, CSSCT et Groupe et conférence |
| Langue_d_intervention_et_de_r_daction__c | / | [[!LANGUE!]] | Devis | SINGLE | A valider : Français, Anglais |
| Duree_moyenne_des_reunions__c | / | [[!DUREE!]] | Devis | SINGLE | XX |
| NombreReunions__c | / | [[!NOMBRE!]] | Opportunité | SINGLE | XX |
| Prestation__c | / | [[!PRESTATION!]] | Opportunité | SINGLE | Prise de notes & rédaction
Visio & rédaction
Rédaction sur la base de vos audios
Rédaction sans enregistrement
Prise de notes ou visio & rédaction
Prise de notes & rédaction ou Rédaction sur la base de vos audios
Prise de notes & rédaction ou Rédaction sans enregistrement
Visio & rédaction ou Rédaction sur la base de vos audios
Visio & rédaction ou Rédaction sans enregistrement
Prise de notes ou visio & rédaction ou Rédaction sur la base de vos audios |
| Delai_de_livraison__c | / | [[!DELAI!]] | Devis | SINGLE | XX |
| / | Autre_delai_de_livraison__c n'est pas vide | [[!I_DELAIAUTRE!]] | Devis | CONDITIONNAL |  |
| Autre_delai_de_livraison__c | / | [[!AUTRE_DELAI!]] | Devis | SINGLE | TEXTE |
| / | Delai_de_livraison_minimum__c n'est pas vide | [[!I_DELAIMINI!]] | Devis | CONDITIONNAL |  |
| Delai_de_livraison_minimum__c | / | [[!DELAIMINI!]] | Devis | SINGLE | TEXTE |
| / | Delai_de_livraison_maximum__c n'est pas vide | [[!I_DELAIMAX!]] | Devis | CONDITIONNAL |  |
| Delai_de_livraison_maximum__c | / | [[!DELAIMAXI!]] | Devis | SINGLE | TEXTE |
| / | Type_de_document__c ou Type_de_document2__c = Mot à mot | [[!PREST_MOT!]] | Devis | CONDITIONNAL | A valider : Mot à mot, Compte rendu intégral, Compte rendu révisé, Compte rendu optimisé, Compte rendu simplifié, Synthèse 6 p/h, Synthèse 4 p/h, Synthèse courte, Flash infos, Relevé de décisions |
| / | Type_de_document__c ou Type_de_document2__c = Compte rendu intégral | [[!PREST_CRI!]] | Devis | CONDITIONNAL |  |
| / | Type_de_document__c ou Type_de_document2__c = Compte rendu optimisé | [[!PREST_CRO!]] | Devis | CONDITIONNAL |  |
| / | Type_de_document__c ou Type_de_document2__c = Compte rendu simplifié | [[!PREST_CRS!]] | Devis | CONDITIONNAL |  |
| / | Type_de_document__c ou Type_de_document2__c = Synthèse 4 p/h ou Synthèse 6 p/h | [[!PREST_SYN!]] | Devis | CONDITIONNAL |  |
| / | Type_de_document__c ou Type_de_document2__c = Synthèse courte | [[!PREST_SYNC!]] | Devis | CONDITIONNAL |  |
| / | Type_de_document__c ou Type_de_document2__c = Flash infos | [[!PREST_SYNF!]] | Devis | CONDITIONNAL |  |
| Product2.Name | / | [[!DOCUMENT!]] | Produit | SINGLE | A valider : Compte rendu intégral - PDN, Relevé de décisions - PDN, Relevé de décisions - Audio, Relevé de décisions - Visio, Flash infos - Visio, Flash infos - Audio, Flash infos - PDN, Synthèse courte - PDN, Synthèse courte - Audio, Synthèse courte - Visio, Synthèse standard (4P/H) - PDN, Synthèse standard (4P/H) - Audio, Synthèse standard (4P/H) - Visio, Synthèse standard (6P/H) - Visio, Synthèse standard (6P/H) - Audio, Synthèse standard (6P/H) - PDN, Compte rendu simplifié - PDN, Compte rendu simplifié - Audio, Compte rendu simplifié - Visio, Compte rendu révisé - Visio, Compte rendu révisé - Audio, Compte rendu révisé - PDN, Compte rendu optimisé - Visio, Compte rendu optimisé - PDN, Compte rendu optimisé - Audio, Compte rendu intégral - Audio, Mot à Mot - Visio, Mot à Mot - PDN, Compte rendu intégral - Visio, Mot à Mot - Audio |
| UnitPrice | / | [[!PRIX_HT!]] | Produit | SINGLE | XXXX€ |
| Prix_TTC__c | / | [[!PRIX_TTC!]] | Produit | SINGLE | XXXX€ |
| Duree_reunion__c | / | [[!NB_HEURE!]] | Produit | SINGLE | XX |
| Budget_HT__c | / | [[!BDGT_HT!]] | Produit | SINGLE | XXXX€ |
| Budget_TTC__c | / | [[!BDGT_TTC!]] | Produit | SINGLE | XXXX€ |

[Ajout de nouveaux produits](/salesforce/codexa/projet-devis/ajout-de-nouveaux-produits)

[Spécifications techniques](/salesforce/codexa/projet-devis/spécifications-techniques)

[Recette technique : génération de devis automatisé avec PDF Butler](/salesforce/codexa/projet-devis/recette-technique-génération-de-devis-automatisé-a)

[Cahier de recette : génération de devis automatisé avec PDF Butler](/salesforce/codexa/projet-devis/cahier-de-recette-génération-de-devis-automatisé-a)

[Ajout des utilisateurs](/salesforce/codexa/projet-devis/ajout-des-utilisateurs)



