---
title: Plan Daction
---

# Plan d’action

Présenté le : 02/05/2025

## Ressources nécessaires

- Consultante Salesforce
- Responsable innovation
- Support ponctuel de l'équipe technique et commerciale (côté client pour accès et validation)

### Temps de mise en oeuvre estimé : 5 jours
Documentation : 1 jour

### Légende

- Tâche terminée ✅
- Tâche en cours 📍

## 1. Audit Salesforce - 0,5 jour  ✅

### Objet contact

- Analyse de la structure actuelle des contacts dans Salesforce
- Identification des champs existants et leur utilisation

### Objet comptes

- Analyse de la structure des comptes dans Salesforce
- Cartographie de la relation entre comptes et contacts

**Livrable :** 

- Recommandations pour la structure optimale des données

## 2. Qualification à réaliser - 0,5 jour ✅

### Identification des données manquantes

- 94 comptes identifiés avec des informations manquantes
- Définition des informations prioritaires à obtenir

**Livrable :** 

- Export listing Excel des comptes identifié

## 3. Création des champs manquants - 0,75 jour ✅

### Analyse des écarts (Gap Analysis)

- Identification des champs présents dans ActiveCampaign mais absents dans Salesforce
- Évaluation des champs nécessaires pour Pardot mais non existants dans la configuration actuelle
- Cartographie des champs personnalisés à créer

### Conception et mise en œuvre

- Création des champs personnalisés dans Salesforce
- Création des règles de validation
- Création des champs personnalisés dans Pardot

## 4. Import de la base de données ActiveCampaign dans Salesforce - 0,5 jour ✅

### Préparation des données

- Export complet des données d'ActiveCampaign
- Nettoyage et normalisation des données (format, doublons, etc.)
- Enrichissement des données si nécessaire
- Mappings des champs entre ActiveCampaign et Salesforce/Pardot

### Exécution et validation

- Import des données
- Contrôle qualité après import
- Correction des anomalies détectées

**Livrable :** 

- Modèle Excel format csv à utiliser.

## 5. Segmentation Pardot - 0,75 jour ✅

### Analyse des besoins en segmentation

- Revue des segments existants dans ActiveCampaign
- Identification des critères de segmentation pertinents

### Configuration des segments dans Pardot

- Création des listes dynamiques
- Configuration des règles d'automatisation pour la maintenance des segments
- Configuration des suppressions et des préférences de communication

## 6. Conception des 3 automations - 1,5 jour 📍

### Analyse des automations existantes

- Audit des automations dans ActiveCampaign
- Documentation des règles, déclencheurs et actions

### Conception des 3 automations principales

- Accueil Rédacteurs_Attente première mission
    1. Templates : 
        - M1.1_TestRéussi_Pleine
        - M1.2_TestRéussi_Creuse
        - M2.1_Bienvenue
        - M2.2_Bienvenue
        - M3_AttenteMission
        - M4_AttenteMission
        - M5.1_Excuses_Pleine
        - M5.2_Excuses_Creuse
        
    
    **Nomage : S1**
    

- Accueil rédacteurs_Pendant première mission
    1. Templates : 
        - M1_PassageActif
        - M1_PassageActif_PDN
        - M2_Actif_PDN_RA
        - M2_Actif_RA
        - M3_Actif_Cooptation
        - M3_Actif_PropAuto
        - M4_Actif_Cooptation
        - M4_Actif_Témoignages
        - M5_Actif_RappelBonnesPratiques
        - M5_Actif_Témoignages
    
    Nomage : S2
    
- Accueil Rédacteurs_Fin des missions de test
    1. Templates :
        - M1_Mission1OK
        - M2_SéquenceEdito1_Philo
        - M3_SéquenceEdito2_Pratique
        - M4_SéquenceEdito3_Témoignages

Nomage : S3

### Plan de reprise des automations en cours

- Audit des automations en cours dans ActiveCampaign

## 7. Rapport de suivi - 0,5 jour

- Création de campagne de suivi
- Rapports d’activité (périodicité)
- KPi : à définir

## Risques et plan de mitigation

1. **Perte de données pendant la migration**
    - *Mitigation* : Sauvegardes complètes avant chaque étape, migration par phases, protocole de vérification
2. **Interruption des campagnes marketing en cours**
    - *Mitigation* : Planification détaillée de la transition, période de double exécution

## 8. Documentation - 1 jour



