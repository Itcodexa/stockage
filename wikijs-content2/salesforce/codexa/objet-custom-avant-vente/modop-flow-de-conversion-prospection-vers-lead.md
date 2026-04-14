---
title: Modop Flow De Conversion Prospection Vers Lead
---

# MODOP - Flow de conversion Prospection vers Lead

## Objectif :

Permettre la création automatique d’un Lead à partir d’un enregistrement `Prospection__c`, tout en mettant à jour ce dernier (conversion marquée, date, lien avec le Lead créé).

## Prérequis :

- L’objet `Prospection__c` est déjà créé avec ses champs.
- Les profils utilisateurs ont accès à cet objet et au Lead.
- Un bouton ou une action rapide « Convertir en Lead » a été (ou sera) ajouté à la page.

## Création du Flow

### Étape 1 — Créer un nouveau Flow

1. Aller dans **Setup** > **Flow** > **New Flow**
2. Choisir **Record-Triggered Flow**
3. Object déclencheur : `Prospection__c`
4. Condition de déclenchement :
    - `Est converti en Lead ? = False`
    - Et (éventuellement) une condition manuelle comme un champ "Prêt à convertir"
5. Déclenchement : **A la mise à jour du record**
6. Cocher « Optimisé pour : Actions rapides et boutons »

### Étape 2 — Ajouter une action « Create Records »

**Nom :** `Créer Lead`

1. Type : `Create Records`
2. Objet : `Lead`
3. Mapping des champs :
    
    
    | Champ Lead | Valeur (depuis Prospection__c) |
    | --- | --- |
    | FirstName | `Prospection__c.FirstName__c` |
    | LastName | `Prospection__c.LastName__c` |
    | Company | `Prospection__c.Company__c` |
    | Email | `Prospection__c.Email__c` |
    | Phone | `Prospection__c.Phone__c` |
    | Website | `Prospection__c.Website__c` |
    | LeadSource | `Prospection__c.Source__c` |
    | Description | `Prospection__c.Comments__c` |
4. Stocker l’ID du Lead créé dans une variable `var_LeadId`

## Étape 3 — Ajouter un élément « Update Record »

**Nom :** `Marquer comme converti`

1. Type : `Update Records`
2. Choisir le record de départ : `Prospection__c`
3. Mettre à jour les champs :
    - `Est converti en Lead ? = TRUE`
    - `Date de conversion = TODAY()`
    - `Lead associé = var_LeadId`

## Étape 4 — Sauvegarder et activer

1. Donner un nom clair au Flow : 
2. Enregistrer
3. **Activer le Flow**

## Étape 5 — Tester

1. Créer une fiche `Prospection__c` avec tous les champs requis
2. Mettre à jour un champ déclencheur ou cliquer sur le bouton « Convertir en Lead »
3. Vérifier que :
    - Un Lead a été créé
    - La fiche Prospection a bien été mise à jour (checkbox + date + lien)
    - Le lien fonctionne entre les deux



