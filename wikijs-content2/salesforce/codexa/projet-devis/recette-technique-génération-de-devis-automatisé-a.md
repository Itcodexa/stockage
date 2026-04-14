---
title: Recette Technique Génération De Devis Automatisé A
---

# Recette technique : génération de devis automatisé avec PDF Butler

Ce document détaille la recette technique Salesforce pour l'implémentation de la génération automatisée de devis au format PDF dans Salesforce, en utilisant l'extension PDF Butler. L'objectif est de produire un document dynamique et conditionnel basé sur les informations d'un enregistrement de devis (Quote) et de ses objets liés.

## Prérequis

Avant de commencer la configuration, on s'assure que les éléments suivants sont en place :

- Salesforce org : un environnement Salesforce avec les objets standard Quote, Opportunity, Account, Contact, User et QuoteLineItem configurés.
- PDF Butler : l'application PDF Butler doit être installée et configurée dans l'organisation Salesforce.
- Champs personnalisés : tous les champs personnalisés mentionnés dans le fichier de mapping doivent être créés sur les objets correspondants dans Salesforce.

## Configuration des sources de données (DataSources)

Pour extraire les informations nécessaires de Salesforce, on configure deux sources de données principales dans PDF Butler.

**DataSource principal (SINGLE)**

Cette source de données récupère les informations de l'enregistrement de devis principal et des objets parents liés.

- Nom de la dataSource : Quote_DS
- Type : SINGLE
- Objet principal : Quote
- Champs à inclure : on utilisera le SOQL builder de PDF Butler pour sélectionner les champs requis du devis, ainsi que les champs des objets liés via des relations de recherche (lookup) :
- Quote: Id, QuoteNumber, Name, Status, Date_du_devis__c, ExpirationDate, Version__c, Type_prestation__c, Nature_reunions__c, Type_d_intervention__c, Format_choisi_1__c, Format_choisi_2__c, Enregistrement__c, Duree_moyenne_des_reunions__c, Delai_de_livraison__c, Delai_de_livraison_minimum__c, Delai_de_livraison_maximum__c, Langue_d_intervention_et_de_r_daction__c, BillingName, BillingAddress.
- Opportunity: Opportunity.Name, Opportunity.Id
- Contact: Contact.FirstName, Contact.LastName
- Account: Account.Name
- User: Owner.Name, Owner.Phone, Owner.Mobile, Owner.Email

**DataSource des lignes de devis (LIST)**

Cette source de données récupère la liste des produits (lignes de devis) associés au devis.

- Nom de la dataSource : QuoteLineItems_DS
- Type : LIST
- Objet principal : QuoteLineItem
- Relation : lié au Quote via le champ QuoteId.
- Champs à inclure :
- Product2.Name
- UnitPrice
- Prix_TTC__c (champ personnalisé)
- Duree_reunion__c (champ personnalisé)
- Budget_HT__c (champ personnalisé)
- Budget_TTC__c (champ personnalisé)

## Structure du template word et placeholders

Le document est généré à partir d'un template Microsoft Word (Template_nouveau_devis_V4.docx). Ce template contient des placeholders (champs de fusion) qui sont remplacés par les données de Salesforce lors de la génération. Les placeholders sont formatés comme suit : [[!NOM_DU_CHAMP!]].

Le template est structuré en plusieurs sections, dont certaines sont conditionnelles. Par exemple, les sections décrivant le type de prestation ([[!PREST_MOT!]], [[!PREST_CRI!]], etc.) ne s'affichent que si le format correspondant est sélectionné dans le devis.

## Configuration du document (Doc Config)

La configuration du document dans PDF Butler (Doc Config) fait le lien entre les dataSources, le template word et la logique d'affichage.

| Type de config | Placeholder(s) cible(s) | DataSource | Logique et description |
| --- | --- | --- | --- |
| SINGLE | Tous les [[!FIELD!]] hors tableaux et conditions complexes | Quote_DS | Mappage direct des champs de la dataSource Quote_DS vers les placeholders correspondants dans le template. |
| TABLE_ROW | [[!DOCUMENT!]], [[!PRIX_HT!]], [[!PRIX_TTC!]], [[!NB_HEURE!]], [[!BDGT_HT!]], [[!BDGT_TTC!]] | QuoteLineItems_DS | On itère sur chaque enregistrement de la dataSource QuoteLineItems_DS pour créer une ligne dans le tableau du budget. |
| PARAGRAPH avec Criteria | [[!I_DELAIAUTRE!]] | Quote_DS | Le paragraphe contenant ce placeholder ne s'affiche que si le champ Autre_delai_de_livraison__c n'est pas vide. Critère : Autre_delai_de_livraison__c != null |
| PARAGRAPH avec Criteria | [[!I_DELAIMINI!]] | Quote_DS | Le paragraphe ne s'affiche que si Delai_de_livraison_minimum__c n'est pas vide. Critère : Delai_de_livraison_minimum__c != null |
| PARAGRAPH avec Criteria | [[!I_DELAIMAX!]] | Quote_DS | Le paragraphe ne s'affiche que si Delai_de_livraison_maximum__c n'est pas vide. Critère : Delai_de_livraison_maximum__c != null |
| PARAGRAPH avec Criteria | [[!PREST_MOT!]] | Quote_DS | Le paragraphe s'affiche si Format_choisi_1__c ou Format_choisi_2__c est 'Mot à mot'. **Critère : `(Format_choisi_1__c = 'Mot à mot' |
| PARAGRAPH avec Criteria | [[!PREST_CRI!]] | Quote_DS | Le paragraphe s'affiche si Format_choisi_1__c ou Format_choisi_2__c est 'Compte rendu intégral'. **Critère : `(Format_choisi_1__c = 'Compte rendu intégral' |
| PARAGRAPH avec Criteria | ... | Quote_DS | On répète la logique ci-dessus pour tous les autres types de prestations ([[!PREST_CRO!]], [[!PREST_CRS!]], etc.) en adaptant la valeur du critère. |

## Table de mapping détaillée

Le tableau suivant résume le mapping complet entre les champs Salesforce, les placeholders du template et les objets concernés.

| Placeholder | Champ Salesforce | Objet Salesforce | Type de mapping |
| --- | --- | --- | --- |
| [[!AFFAIRE!]] | N_d_Affaire__c | Opportunité | SINGLE |
| [[!DATE!]] | Date_du_devis__c | Devis | SINGLE |
| [[!CLIENT!]] | Account.Name | Opportunité | SINGLE |
| [[!CLIENT_P!]] | FirstName | Contact | SINGLE |
| [[!CLIENT_N!]] | LastName | Contact | SINGLE |
| [[!COMMERCIAL!]] | Owner.Name | User | SINGLE |
| [[!PHONE!]] | Owner.Phone | User | SINGLE |
| [[!MOBILE!]] | Owner.Mobile | User | SINGLE |
| [[!EMAIL!]] | Owner.Email | User | SINGLE |
| [[!REUNION!]] | TypeReunion__c | Opportunité | SINGLE |
| [[!LANGUE!]] | Langue_d_intervention_et_de_r_daction__c | Devis | SINGLE |
| [[!DUREE!]] | Duree_moyenne_des_reunions__c | Devis | SINGLE |
| [[!NOMBRE!]] | NombreReunions__c | Opportunité | SINGLE |
| [[!PRESTATION!]] | Prestation__c | Opportunité | SINGLE |
| [[!DELAI!]] | Delai_de_livraison__c | Devis | SINGLE |
| [[!I_DELAIAUTRE!]] | - | Devis | CONDITIONNAL |
| [[!AUTRE_DELAI!]] | Autre_delai_de_livraison__c | Devis | SINGLE |
| [[!I_DELAIMINI!]] | - | Devis | CONDITIONNAL |
| [[!DELAIMINI!]] | Delai_de_livraison_minimum__c | Devis | SINGLE |
| [[!I_DELAIMAX!]] | - | Devis | CONDITIONNAL |
| [[!DELAIMAXI!]] | Delai_de_livraison_maximum__c | Devis | SINGLE |
| [[!PREST_MOT!]] | - | Devis | CONDITIONNAL |
| [[!PREST_CRI!]] | - | Devis | CONDITIONNAL |
| [[!PREST_CRO!]] | - | Devis | CONDITIONNAL |
| [[!PREST_CRS!]] | - | Devis | CONDITIONNAL |
| [[!PREST_SYN!]] | - | Devis | CONDITIONNAL |
| [[!PREST_SYNC!]] | - | Devis | CONDITIONNAL |
| [[!PREST_SYNF!]] | - | Devis | CONDITIONNAL |
| [[!DOCUMENT!]] | Product2.Name | Produit | LIST |
| [[!PRIX_HT!]] | UnitPrice | Produit | LIST |
| [[!PRIX_TTC!]] | Prix_TTC__c | Produit | LIST |
| [[!NB_HEURE!]] | Duree_reunion__c | Produit | LIST |
| [[!BDGT_HT!]] | Budget_HT__c | Produit | LIST |
| [[!BDGT_TTC!]] | Budget_TTC__c | Produit | LIST |

## Processus de génération

La génération du devis sera initiée depuis la page de l'enregistrement Quote dans Salesforce. La capture d'écran fournie montre un composant lightning "PDF Butler Document Previewer" sur la droite de la page. C'est via ce composant que l'on pourra :

1.Prévisualiser le document : on clique sur un bouton pour générer une prévisualisation du devis avec les données de l'enregistrement courant.

2.Générer le PDF final : une fois la prévisualisation validée, on pourra générer le fichier PDF final, qui pourra ensuite être sauvegardé dans les fichiers du devis (Quote PDFs) et envoyé au client.

La configuration se fera sans code Apex, en utilisant uniquement les outils déclaritifs de PDF Butler (dataSources, doc config, etc.), conformément aux préférences de l'utilisateur.

## 8. Références

- [1] PDF Butler academy. (2024). PDF Butler documentation. Récupéré de [https://www.pdfbutler.com/academy/pdf-butler-academy/](https://www.pdfbutler.com/academy/pdf-butler-academy/)



