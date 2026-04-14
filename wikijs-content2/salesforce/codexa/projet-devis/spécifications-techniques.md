---
title: Spécifications Techniques
---

# Spécifications techniques

Ce document fournit les spécifications techniques détaillées pour la configuration de PDF Butler. On y décrit la structure des sources de données (data sources) et la logique de chaque type de configuration (config type) nécessaire pour générer le devis automatisé.

## Sources de données (data sources)

La configuration s'appuie sur deux sources de données pour collecter toutes les informations requises depuis Salesforce.

**2.1. Data source principale : Quote**

Cette source de données récupère les informations de l'enregistrement du devis et de ses objets parents directs.

- Nom : Quote
- Type : SINGLE
- Objet principal : Quote (Devis)
- Logique d'extraction : on utilise une requête SOQL pour extraire les champs du devis ainsi que les champs des objets liés (opportunité, contact, compte, propriétaire). La requête doit inclure les champs listés dans la recette fonctionnelle, tels que Quote.Name, Opportunity.Name, Contact.FirstName, Account.Name, Owner.Email, etc.

![image.png](/spécifications-techniques-image.png)

**2.2. Data source des lignes de devis : Quote Products**

Cette source de données récupère la liste de tous les produits (lignes de devis) associés au devis principal.

- Nom : Quote Products
- Type : List
- Objet principal : QuoteLineItem (Élément de ligne de devis)
- Relation : la liaison se fait via le champ QuoteId, qui établit la relation parent-enfant entre le devis et ses lignes.
- Logique d'extraction : la requête SOQL doit extraire les champs de chaque ligne de produit, comme Product2.Name, UnitPrice, Quantity, et les champs de budget personnalisés (Budget_HT__c, Budget_TTC__c).

Objet : Quote Products (Items)

## Types de configuration (config types)

Les "config types" définissent comment les données extraites sont mappées et affichées dans le template word. Chaque entrée de la liste correspond à un placeholder ou à une logique conditionnelle dans le document.

Le tableau ci-dessous détaille la configuration de chaque type, en se basant sur la liste fournie dans la capture d'écran.

| Nom du config type | Type de configuration | Data source | Champ source / logique de critère |
| --- | --- | --- | --- |
| Mappage de champs simples |  |  |  |
| SINGLE - AFFAIRE | SINGLE | Quote | Opportunity.N_d_Affaire__c |
| SINGLE - DATE | SINGLE | Quote | Date_du_devis__c |
| SINGLE - CLIENT | SINGLE | Quote | Account.Name |
| SINGLE - CLIENT_P | SINGLE | Quote | Contact.FirstName |
| SINGLE - CLIENT_N | SINGLE | Quote | Contact.LastName |
| SINGLE - COMMERCIAL | SINGLE | Quote | Owner.Name |
| SINGLE - PHONE | SINGLE | Quote | Owner.Phone |
| SINGLE - MOBILE | SINGLE | Quote | Owner.Mobile |
| SINGLE - EMAIL | SINGLE | Quote | Owner.Email |
| SINGLE - REUNION | SINGLE | Quote | TypeReunion__c |
| SINGLE - LANGUE | SINGLE | Quote | Langue_d_intervention_et_de_r_daction__c |
| SINGLE - DUREE | SINGLE | Quote | Duree_moyenne_des_reunions__c |
| SINGLE - NOMBRE | SINGLE | Quote | NombreReunions__c |
| TITLE - DEVIS | TITLE | Quote | QuoteNumber |
| TITLE - VERSION | TITLE | Quote | Version__c |
| SINGLE - PRESTATION | SINGLE | Quote | Prestation__c |
| SINGLE - DELAI | SINGLE | Quote | Delai_de_livraison__c |
| SINGLE - AUTRE_DELAI | SINGLE | Quote | Autre_delai_de_livraison__c |
| Sections conditionnelles (délais) |  |  |  |
| CONDITIONAL_SECTION - I_DELAIMINI | CONDITIONAL_SECTION | Quote | Delai_de_livraison_minimum__c != null |
| CONDITIONAL_SECTION - I_DELAIMAX | CONDITIONAL_SECTION | Quote | Delai_de_livraison_maximum__c != null |
| CONDITIONAL_SECTION - I_DELAIAUTRE | CONDITIONAL_SECTION | Quote | Autre_delai_de_livraison__c != null |
| Tableau des lignes de produits |  |  |  |
| TABLE_ROW - DOCUMENT | TABLE_ROW | Quote Products | Itération sur la liste Quote Products |
| SINGLE - PRIX_HT | SINGLE | Quote Products | UnitPrice |
| SINGLE - PRIX_TTC | SINGLE | Quote Products | Prix_TTC__c |
| SINGLE - BDGT_HT | SINGLE | Quote Products | Budget_HT__c |
| SINGLE - BDGT_TTC | SINGLE | Quote Products | Budget_TTC__c |
| SINGLE - NB_HEURE | SINGLE | Quote Products | Duree_reunion__c |
| Sections conditionnelles (prestations) |  |  |  |
| CONDITIONAL_SECTION - PREST_MOT | CONDITIONAL_SECTION | Quote | (Format_choisi_1__c = 'Mot à mot' || Format_choisi_2__c = 'Mot à mot') |
| CONDITIONAL_SECTION - PREST_CRI | CONDITIONAL_SECTION | Quote | (Format_choisi_1__c = 'Compte rendu intégral' || Format_choisi_2__c = 'Compte rendu intégral') |
| CONDITIONAL_SECTION - PREST_CRO | CONDITIONAL_SECTION | Quote | (Format_choisi_1__c = 'Compte rendu optimisé' || Format_choisi_2__c = 'Compte rendu optimisé') |
| CONDITIONAL_SECTION - PREST_CRS | CONDITIONAL_SECTION | Quote | (Format_choisi_1__c = 'Compte rendu simplifié' || Format_choisi_2__c = 'Compte rendu simplifié') |
| CONDITIONAL_SECTION - PREST_SYN | CONDITIONAL_SECTION | Quote | (Format_choisi_1__c = 'Synthèse' || Format_choisi_2__c = 'Synthèse') |
| CONDITIONAL_SECTION - PREST_SYNC | CONDITIONAL_SECTION | Quote | (Format_choisi_1__c = 'Synthèse courte' || Format_choisi_2__c = 'Synthèse courte') |
| CONDITIONAL_SECTION - PREST_SYNF | CONDITIONAL_SECTION | Quote | (Format_choisi_1__c = 'Flash infos' || Format_choisi_2__c = 'Flash infos') |



