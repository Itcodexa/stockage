---
title: Objet Custom Avant Vente
---

# Objet custom - Avant-vente

## ✨ Objectif de l'objet `Prospection__c`

L'objet personnalisé `Prospection__c` a pour but de permettre aux équipes avant-vente de saisir, suivre et qualifier des contacts commerciaux pré-matures sans polluer le pipeline commercial officiel (Leads / Opportunités). Il permet de structurer la phase de prospection et de n'envoyer vers les équipes commerciales que les prospects jugés matures.

## Fiche technique de l'objet

**Nom API** : `Prospection__c`

**Type** : Objet personnalisé standard

**Activités activées** : Oui

**Historique activé** : Recommandé

**Disposition Lightning** : Oui

## Champs principaux

[Fiche_Champs_Prospection](Objet%20custom%20-%20Avant-vente/Fiche_Champs_Prospection%20215fa3aa503c80909c70d827c91aa911.csv)

### Catégories de champs :

- Informations de contact (Prénom, Nom, Email, Société, etc.)
- Données de qualification (Source, Canal, Score marketing...)
- Suivi interne (Responsable avant-vente, Dates, Conversion...)

## Mise en page recommandée (Layout)

**Sections suggérées :**

1. Informations de contact
2. Données marketing / source
3. État de qualification
4. Historique de conversion
5. Activités et commentaires

**Actions visibles :**

- Modifier / Supprimer
- Convertir en Lead (voir bouton personnalisé)

## Processus de conversion en Lead

### Objectif :

Permettre aux équipes avant-vente de transformer une fiche Prospection validée en un Lead standard Salesforce.

### Mécanique :

- Action rapide ou bouton "Convertir en Lead"
- Flow Salesforce qui :
    - Crée un enregistrement Lead
    - Récupère les champs clés depuis la fiche Prospection
    - Met à jour `IsConverted__c` à TRUE + `ConversionDate__c`
    - Lie le Lead à la fiche d'origine (`AssociatedLead__c`)

## ⚖️ Mapping des champs vers Lead

| Prospection__c | Lead |
| --- | --- |
| FirstName__c | FirstName |
| LastName__c | LastName |
| Email__c | Email |
| Phone__c | Phone |
| Company__c | Company |
| Website__c | Website |
| Source__c | LeadSource |
| Comments__c | Description |

## 📊 Suivi et reporting

Rapports recommandés :

- Prospections créées par mois
- Prospections par étape de qualification
- Taux de conversion vers Lead
- Délai moyen de conversion

## Mise en œuvre technique

**Profils et accès :**

- Créer un nouvel ensemble de permissions si besoin
- Ajouter l'objet à l'application Lightning concernée

**Règles de partage :**

- Lecture/Écriture pour les avant-vente
- Lecture seule pour les commerciaux

**Automatisations possibles :**

- Notification quand une fiche est convertie
- Rappel de relance si pas de contact depuis X jours

[MODOP - Flow de conversion `Prospection` vers `Lead`](/salesforce/codexa/objet-custom-avant-vente/modop-flow-de-conversion-prospection-vers-lead)



