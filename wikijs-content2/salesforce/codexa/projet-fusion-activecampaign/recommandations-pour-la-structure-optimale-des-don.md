---
title: Recommandations Pour La Structure Optimale Des Don
---

# Recommandations pour la structure optimale des données

## Objet Lead (piste)

### Champs à créer

| Nom du champ | API Name | Type de données | Valeurs | Required |
| --- | --- | --- | --- | --- |
| Type de contact | Type_de_contact__c | Picklist | Contact | x |

Valeur par défaut : Contact

### Mapping champs

Lead.Type de contact to Contact.Type de contact

## Objet Compte

Connecter les rédacteurs, en tant que Contact, au compte Codexa.
Pas de création de champs.
Owner : Julien

## Objet Contact

### Champs à créer

| Nom du champ | Valeurs |  |
| --- | --- | --- |
| Prise de poste	 | AAAA |  |
| Actif | Oui
Non |  |
| Rôle | RS
RI |  |
| Équipe | Rédacteur
Production
Commerce
Direction |  |
| Non relu | Oui
Non |  |
| Propositions auto | Oui
Non |  |
| Prise de notes | Oui
Non |  |
| Type de collaboration	 | Actif
À former
Mission1OK
Fin de collaboration
Indisponible |  |
| Type de contact | Contact
Rédac |  |
| Non relu | Oui
Non |  |

### Champs existants

| Nom du champ | Type de données | Required |
| --- | --- | --- |
| Prénom | Texte |  |
| Nom | Texte | x |
| Email | Email | x |
| Téléphone | Phone |  |
| Contact Owner | OwnerId | x |

### Visibilité des champs

Visible pour tous les profils, mais en lecture seule sauf pour les administrateur.

### Méthodologie détaillée

- Ajout de la segmentation type de contact sur l'objet contact
- Modification de l'ensemble des contacts existants
    - Ajout du statut Contact
    - Mise à jour des flux d'automation
    - Réalisation de tests manuels
    - Création d'un rapport dynamique
- Modification du Lightning Record Pages : Contact_Record_Page
    - Ajout d’une section rédacteur avec affichage conditionnel (Type de contact = Rédac)
    - Ajout d’un affichage conditionnel sur section Préférences de communication

### Spécifications techniques

| Nom du champ | API Name |
| --- | --- |
| Prise de poste | Prise_de_poste__c |
| Actif | Actif__c |
| Rôle | Role__c |
| Équipe | Equipe__c |
| Non relu | Non_relu__c |
| Propositions auto | Propositions_auto__c |
| Type de collaboration | Type_de_collaboration__c |
| Type de contact | Type_de_contact__c |

### Spécifications fonctionnelles

| Nom du champ | Type de données | Required | Validation rules° |
| --- | --- | --- | --- |
| Prise de poste | Number(4, 0) |  |  |
| Actif | Picklist |  | x |
| Rôle | Picklist |  | x |
| Equipe | Picklist |  | x |
| Non relu | Picklist |  | x |
| Propositions auto | Picklist |  | x |
| Type de collaboration | Picklist |  | x |
| Type de contact | Picklist | x |  |

* le champ ne peut pas être vide si le Type de contact = Rédac

### Validation rules créées

Nom : Actif_Obligatoire_Si_Type_Redac



