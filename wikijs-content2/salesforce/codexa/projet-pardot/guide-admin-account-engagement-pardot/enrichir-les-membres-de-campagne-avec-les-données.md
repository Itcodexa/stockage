---
title: Enrichir Les Membres De Campagne Avec Les Données
---

# Enrichir les membres de campagne avec les données account engagement

Ce guide a pour objectif de fournir à l'administrateur salesforce une documentation complète et centralisée pour améliorer la visibilité des données d'engagement des prospects. En suivant ces étapes, on ajoutera trois indicateurs clés de l'outil account engagement (pardot) directement sur les enregistrements des membres de campagne (campaign members) :

1. Le score du prospect (prospect score) : pour évaluer rapidement le niveau d'intérêt.
2. La dernière campagne significative : pour identifier la dernière interaction majeure (reflétant l'ajout à une liste).
3. Le dernier email marketing reçu : pour connaître la communication la plus récente.

L'implémentation de ces solutions se base principalement sur des outils déclaratifs (champs formules, salesforce flow) pour une maintenance simplifiée, conformément aux meilleures pratiques.

## Prérequis généraux

Avant de commencer, il est essentiel de s'assurer que l'environnement salesforce est correctement configuré :

- Intégration salesforce - account engagement : le connecteur doit être actif et fonctionnel.
- Campagnes connectées (connected campaigns) : la fonctionnalité doit être activée pour synchroniser les campagnes entre les deux systèmes.
- Historique d'engagement (engagement history) : cette fonctionnalité doit être configurée pour synchroniser les activités marketing (envois d'emails, etc.) en tant que tâches dans salesforce.
- Permissions : des droits d'administrateur sont nécessaires pour créer des champs, des flux (flows) et modifier les présentations de page.

## Partie 1 : afficher le score du prospect

Cette section explique comment créer un champ formule qui affiche le score du prospect (pi__score__c) directement sur l'enregistrement du membre de campagne.

**Étape 1 : création du champ formule**

1. Accéder à l'object manager et sélectionner l'objet campaign member.
2. Aller dans fields & relationships et cliquer sur new.
3. Choisir le type de champ formula.
4. Configurer les détails du champ :
    - Field label : score du prospect ae
    - Formula return type : number
    - Decimal places : 0

Saisir la formule suivante dans l'éditeur :

max(0, if(isblank(contactid), blankvalue(lead.pi__score__c, 0), blankvalue(contact.pi__score__c, 0)))

Cliquer sur check syntax, puis suivre les étapes pour enregistrer le champ en le rendant visible pour les profils concernés.

**Explication de la formule**

| Partie de la formule | Description |
| --- | --- |
| if(isblank(contactid), ...) | Vérifie si le membre de campagne est un lead (contactid est vide) ou un contact. |
| blankvalue(lead.pi__score__c, 0) | Si c'est un lead, cette fonction récupère le score. Si le champ est vide, elle retourne 0 pour éviter les erreurs. |
| blankvalue(contact.pi__score__c, 0) | Fait la même chose pour l'objet contact. |
| max(0, ...) | Assure que la valeur affichée ne sera jamais négative. |

## Partie 2 : afficher la dernière campagne significative

L'objectif ici est de connaître la dernière interaction majeure d'un prospect. Puisqu'il n'existe pas de champ "dernière liste", la meilleure pratique consiste à utiliser les campagnes salesforce comme un miroir des listes de prospects account engagement. Ce guide implémente une solution pour capturer la dernière campagne à laquelle un prospect a été ajouté.

**Étape 1 : création des champs de stockage sur lead et contact**

1.Sur l'objet lead, créer un nouveau champ de type text :

- Field label : dernière campagne ae
- Length : 255
- Field name : last_ae_campaign

2.Répéter l'opération à l'identique pour l'objet contact.

**Étape 2 : création du salesforce flow**

Ce flow se déclenchera à chaque ajout d'un membre à une campagne pour stocker le nom de cette campagne.

1.Créer un nouveau record-triggered flow.

2.Configurer le déclencheur :

- Object : campaign member
- Trigger the flow when : a record is created
- Optimize the flow for : actions and related records

3.Ajouter une décision pour différencier lead et contact ($record.whoid commence par 00q pour un lead).

4.Configurer les branches de mise à jour :

- Branche lead : ajouter un élément update records pour mettre à jour le champ last_ae_campaign__c du lead ($record.whoid) avec la valeur {!$record.campaign.name}.
- Branche contact : faire de même pour l'objet contact.

5.Sauvegarder et activer le flow.

**Étape 3 : création du champ formule sur campaign member**

1.Sur l'objet campaign member, créer un nouveau champ formula.

2.Field label : dernière campagne ae

3.Formula return type : text

4.Formule : if(isblank(contactid), lead.last_ae_campaign__c, contact.last_ae_campaign__c)

5.Enregistrer le champ.

## Partie 3 : afficher le dernier email reçu

Cette solution avancée permet de capturer le nom et la date du dernier email marketing envoyé, tout en filtrant les communications non pertinentes.

**Étape 1 : création des champs de stockage sur lead et contact**

1.Sur l'objet lead, créer les deux champs suivants :

- Champ 1 (texte) : dernier email ae (nom) (api name: last_ae_email_name__c)
- Champ 2 (date/time) : dernier email ae (date) (api name: last_ae_email_date__c)

2.Répéter l'opération pour l'objet contact.

**Étape 2 : création du salesforce flow de capture d'email**

1.Créer un nouveau record-triggered flow sur l'objet task.

2.Configurer le déclencheur :

- Trigger the flow when : a record is created
- Set entry conditions :
- subject starts with list email sent:
- whoid is null false
- subject does not start with pardot misc email:

3.Créer une ressource de type formule pour nettoyer le sujet de l'email :

- Api name : cleanedemailsubject
- Data type : text
- Formule :

Plain Text

trim(substitute(substitute({!$record.subject}, "list email sent:", ""), "email sent:", ""))

4.Ajouter une décision pour différencier lead et contact (basée sur $record.whoid).

5.Configurer les branches de mise à jour :

- Branche lead : mettre à jour l'enregistrement lead correspondant.
- last_ae_email_name__c = {!cleanedemailsubject}
- last_ae_email_date__c = {!$record.createddate}
- Branche contact : faire de même pour l'objet contact.

6.Sauvegarder et activer le flow.

**Étape 3 : création des champs formule sur campaign member**

1.Sur l'objet campaign member, créer deux champs formula.

2.Champ 1 : nom de l'email

- Field label : dernier email ae (nom)
- Formula return type : text
- Formule : if(isblank(contactid), lead.last_ae_email_name__c, contact.last_ae_email_name__c)

3.Champ 2 : date de l'email

- Field label : dernier email ae (date)
- Formula return type : date/time
- Formule : if(isblank(contactid), lead.last_ae_email_date__c, contact.last_ae_email_date__c)

4.Enregistrer les deux champs.

## Partie 4 : déploiement et vérification

Pour finaliser l'implémentation, il est crucial de rendre ces nouveaux champs visibles pour les utilisateurs.

1.Accéder à l'object manager et sélectionner l'objet campaign.

2.Aller dans page layouts et choisir la présentation de page appropriée.

3.Faire défiler jusqu'à la section related lists et trouver la liste campaign members.

4.Cliquer sur l'icône en forme de clé à molette pour modifier les propriétés.

5.Ajouter les nouveaux champs créés (score du prospect ae, dernière campagne ae, dernier email ae (nom), dernier email ae (date)) à la liste des champs sélectionnés.

6.Organiser l'ordre des colonnes et enregistrer.

Après avoir sauvegardé, naviguer vers une campagne existante pour vérifier que les nouvelles colonnes apparaissent et affichent les données correctement. Ces champs seront également disponibles pour la création de rapports sur les campagnes et leurs membres.



