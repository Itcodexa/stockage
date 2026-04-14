---
title: Cahier De Recette Génération De Devis Automatisé A
---

# Cahier de recette : génération de devis automatisé avec PDF Butler

Ce document a pour objectif de définir l'ensemble des tests à réaliser pour valider la correcte implémentation de la génération de devis automatisée dans Salesforce via l'application PDF Butler. Le cahier de recette couvre les aspects fonctionnels, la validation des données, la gestion des conditions d'affichage et le processus utilisateur.

## Environnement et prérequis

- Environnement de test : l'environnement de recette (UAT) de Salesforce.
- Utilisateur de test : un profil utilisateur ayant les droits nécessaires pour créer et modifier des devis, et accéder à PDF Butler.
- Configuration : on s'assure que la recette fonctionnelle a été entièrement implémentée dans l'environnement de test.

## Scénarios de test

**CT-01 : cas nominal - validation complète**

|  |  |
| --- | --- |
| Objectif | On valide la génération d'un devis standard avec tous les champs principaux renseignés. |
| Prérequis | On doit disposer d'un compte, d'un contact et d'une opportunité actifs dans Salesforce. |
| Jeu de données | - Compte : CODEXA SARL
- Contact : Julien Cubier Test
- Opportunité : CODEXA SARL 2 options Autre
- Devis :
- Type d'intervention: Prise de notes & rédaction ou Rédaction sur la base de vos audios
- Nature des réunion(s): CSE
- Format choisi 1: Flash infos
- Format choisi 2: Compte rendu intégral
- Langue: Français
- Durée moyenne des réunions: 2 heures
- Délai de livraison: 1,5 jours ouvrés par heure de réunion
- Lignes de devis :
1. Compte rendu intégral - Audio (Quantité: 2, Prix: 180,00 €)  
 2. Compte rendu intégral - PDN (Quantité: 2, Prix: 400,00 €) |
| Étapes de test | 1. On crée un devis avec le jeu de données ci-dessus.
2. On accède à la page du devis.  
3. Dans le composant "PDF Butler Document Previewer", on clique sur le bouton de prévisualisation.  
4. On vérifie la prévisualisation.  
5. On clique sur le bouton pour générer le PDF final. |
| Résultats attendus | - Le devis est généré sans erreur.
- Toutes les informations du jeu de données sont correctement affichées dans les placeholders correspondants ([[!CLIENT!]], [[!AFFAIRE!]], etc.).
- Les deux lignes de produits apparaissent correctement dans le tableau "Budget".  
- Les totaux (Subtotal, Total) sont calculés et affichés correctement.  
- Les paragraphes conditionnels pour "Flash infos" ([[!PREST_SYNF!]]) et "Compte rendu intégral" ([[!PREST_CRI!]]) sont visibles.
- Les autres paragraphes de prestation sont masqués. |
| Statut | X OK / ☐ KO (captures d’écran à fournir par mail) |

**CT-02 : validation des blocs conditionnels de prestation**

|  |  |
| --- | --- |
| Objectif | On vérifie que seuls les paragraphes correspondant aux formats de documents choisis sont affichés. |
| Prérequis | On doit disposer d'un devis de base. |
| Jeu de données | On crée 7 devis distincts. Pour chaque devis, on renseigne le champ Format choisi 1 avec une des valeurs suivantes, en laissant Format choisi 2 vide :
1. Mot à mot  
2. Compte rendu optimisé  
3. Compte rendu simplifié  
4. Synthèse (4 ou 6 pages/heure)  
5. Synthèse courte  
6. Flash  
7. Compte rendu intégral |
| Étapes de test | Pour chaque devis créé :
1. On génère la prévisualisation du document.  
2. On vérifie la section "Notre solution recommandée". |
| Résultats attendus | Pour chaque test, seul le paragraphe correspondant au format choisi doit être visible. Par exemple, pour le devis avec "Mot à mot", seul le bloc [[!PREST_MOT!]] doit s'afficher. Tous les autres blocs de prestation doivent être masqués. |
| Statut | X OK / ☐ KO (captures d’écran à fournir par mail) |

**CT-03 : validation des conditions de délais de livraison**

|  |  |
| --- | --- |
| Objectif | On valide l'affichage conditionnel des champs de délais de livraison spécifiques. |
| Prérequis | On doit disposer d'un devis de base. |
| Jeu de données | Scénario 1 (sans délais spécifiques) :
- Delai_de_livraison_minimum__c: vide
- Delai_de_livraison_maximum__c: vide
- Autre_delai_de_livraison__c: vide

Scénario 2 (avec délais spécifiques) :
- Delai_de_livraison_minimum__c: 3 jours ouvrés
- Delai_de_livraison_maximum__c: 10 jours ouvrés
- Autre_delai_de_livraison__c: Livraison spéciale sous 48h |
| Étapes de test | 1. On crée un devis pour chaque scénario.
2. On génère la prévisualisation pour chaque devis.  
3. On observe la section "Votre besoin" dans le document généré. |
| Résultats attendus | - Scénario 1 : les lignes "Délai mini de :", "Délai max. de livraison :" et "Délai de livraison spécifique :" ne doivent PAS apparaître.
- Scénario 2 : les trois lignes de délais spécifiques doivent apparaître avec les valeurs correspondantes. |
| Statut | X OK / ☐ KO (captures d’écran à fournir par mail) |

**CT-04 : validation des lignes de devis multiples**

|  |  |
| --- | --- |
| Objectif | On s'assure que le tableau du budget affiche correctement un nombre variable de produits. |
| Prérequis | On doit disposer d'un devis de base. |
| Jeu de données | On crée un devis et on y ajoute 5 QuoteLineItem différents, avec des quantités et des prix variés. |
| Étapes de test | 1. On génère la prévisualisation du document.
2. On examine le tableau "Budget". |
| Résultats attendus | - Le tableau "Budget" doit contenir exactement 5 lignes, une pour chaque produit.
- Les informations de chaque ligne (nom, prix, quantité, total) doivent être correctes.  
- Le total général du devis doit correspondre à la somme des 5 lignes. |
| Statut | X OK / ☐ KO (captures d’écran à fournir par mail) |

**CT-05 : validation de la gestion des champs vides**

|  |  |
| --- | --- |
| Objectif | On vérifie que le document est généré correctement même si des champs non obligatoires sont laissés vides. |
| Prérequis | On doit disposer d'un devis de base. |
| Jeu de données | On crée un devis en ne renseignant que les champs strictement obligatoires. On laisse les champs suivants vides :
- Format choisi 2
- Delai_de_livraison_minimum__c
- Delai_de_livraison_maximum__c
- Autre_delai_de_livraison__c
- Owner.Mobile |
| Étapes de test | 1. On génère la prévisualisation du document.
2. On examine le document généré. |
| Résultats attendus | - Le document est généré sans erreur.
- Les placeholders correspondant à des champs vides ne doivent pas afficher "null" ou un texte d'erreur. Ils doivent être vides.  
- Les blocs conditionnels liés à ces champs vides ne doivent pas s'afficher. |
| Statut | X OK / ☐ KO (captures d’écran à fournir par mail) |

**CT-06 : validation du processus utilisateur**

|  |  |
| --- | --- |
| Objectif | On valide le bon fonctionnement des actions utilisateur dans le composant PDF Butler. |
| Prérequis | On doit disposer d'un devis valide (on utilise le jeu de données de CT-01). |
| Jeu de données | N/A |
| Étapes de test | 1. Sur la page du devis, on clique sur le bouton de prévisualisation.
2. On ferme la prévisualisation.  
3. On clique sur le bouton de génération finale du PDF.  
4. On vérifie la section "Quote PDFs (0)" sur la page du devis. |
| Résultats attendus | - La prévisualisation s'affiche correctement.
- Le PDF final est généré et automatiquement attaché à l'enregistrement du devis.  
- La section "Quote PDFs" doit maintenant indiquer "Quote PDFs (1)" et contenir le document généré. |
| Statut | X OK / ☐ KO (captures d’écran à fournir par mail) |



