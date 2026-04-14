---
title: Ajout De Nouveaux Produits
---

# Ajout de nouveaux produits

Ce guide explique comment on ajoute de nouveaux produits dans l'objet Products de Salesforce. Pour garantir la cohérence des données et le bon fonctionnement des automatisations, il est impératif de suivre les conventions de nommage et de structuration établies.

## 2. Accès à l'objet produits

Pour commencer, on accède à l'objet "Products" (Produits) depuis le lanceur d'applications de Salesforce. On peut utiliser la barre de recherche pour le trouver rapidement.

![image.png](/ajout-de-nouveaux-produits-image.png)

## 3. Procédure de création d'un nouveau produit

![image.png](/ajout-de-nouveaux-produits-image-1.png)

La création d'un produit se fait en plusieurs étapes simples :

- Dans l'onglet "Products", on clique sur le bouton New (Nouveau) en haut à droite.
- On remplit les champs du nouveau produit en suivant scrupuleusement les conventions détaillées dans la section suivante.
- On s'assure que la case Active est cochée pour que le produit soit utilisable dans les devis.
- On clique sur Save (Enregistrer).

## 4. Conventions de remplissage des champs

Chaque produit est défini par trois champs principaux qui doivent respecter une structure précise.

**Product Name (nom du produit)**

Le nom du produit suit toujours le format : [Type de document] - [Mode de prestation].

- [Type de document] : correspond au type de livrable (ex: "Mot à Mot", "Flash infos", "Synthèse courte").
- [Mode de prestation] : correspond à la famille du produit (ex: "Audio", "PDN", "Visio").

Exemple : Synthèse courte - PDN

**Product Family (famille de produits)**

Ce champ définit le mode de prestation. On choisit l'une des trois valeurs existantes dans la liste de sélection :

- Audio
- PDN
- Visio

**Product Code (code produit)**

Le code produit est un identifiant unique qui suit une structure stricte : COD[numéro][lettre].

- COD : préfixe fixe.
- [numéro] : un numéro séquentiel à deux chiffres qui identifie le type de document. On utilise le tableau ci-dessous pour trouver le bon numéro ou en assigner un nouveau.
- [lettre] : un suffixe d'une lettre qui correspond à la Product Family :
- A pour Audio
- P pour PDN
- V pour Visio

**Tableau de référence des codes produits**

On utilise ce tableau pour s'assurer de la cohérence des codes. Si on introduit un nouveau type de document, on lui assigne le prochain numéro disponible dans la séquence.

| Type de document | Numéro de code |
| --- | --- |
| Mot à Mot | 01 |
| Relevé de décisions | 02 |
| Flash infos | 03 |
| Synthèse courte | 04 |
| Synthèse standard (4P/H) | 05 |
| Synthèse standard (6P/H) | 06 |
| Nouveau type à définir | 07, 08, etc. |

## 5. Exemple : ajout d'un nouveau type de document

On souhaite ajouter le type de document "Compte rendu intégral", qui n'existe pas encore. Ce nouveau type doit être décliné pour les trois familles de produits (Audio, PDN, Visio).

1.Assignation du code : d'après le tableau de référence, le prochain numéro disponible est 07.

2.Création des 3 produits : on va créer trois enregistrements de produit distincts.

Produit 1 : version Audio

Produit 2 : version PDN

Produit 3 : version Visio

- Product Name : Compte rendu intégral - Audio
- Product Code : COD07A
- Product Family : Audio
- Active : coché
- Product Name : Compte rendu intégral - PDN
- Product Code : COD07P
- Product Family : PDN
- Active : coché
- Product Name : Compte rendu intégral - Visio
- Product Code : COD07V
- Product Family : Visio
- Active : coché

## 6. Ajout du pricebook et du prix

Une fois un produit créé et activé, on ne doit pas oublier de l'ajouter à un catalogue de prix (Price Book) pour qu'il puisse être sélectionné dans un devis.

![image.png](/ajout-de-nouveaux-produits-image-2.png)

Sur la page du produit nouvellement créé, on accède à la liste associée (Related).

Comme on utilise un catalogue de prix, il faut cliquer sur Add to Price Book (Ajouter au catalogue de prix) pour définir des prix spécifiques.

Si le produit n’a jamais été associé au Price Book, il faut réaliser l’opération dans Standard Price Book puis **Price Book Entries.**

![image.png](/ajout-de-nouveaux-produits-image-3.png)

Si le produit existe et qu’il a déjà été associé au Price Book, il suffit de cliquer sur le chevron tout à droite pour le mettre à jour (Edit)

![image.png](/ajout-de-nouveaux-produits-image-4.png)



