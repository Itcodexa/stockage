---
title: Fl017 Rec Account Updatecontacts Aftersave
---

# FL017_REC_Account_UpdateContacts_AfterSave

Ce flux est un **flux déclenché par un enregistrement**. Il s'exécute automatiquement lorsqu'un enregistrement de l'objet **Compte** est créé ou mis à jour, et il est optimisé pour les **Actions et enregistrements associés**.

Voici le déroulement détaillé du processus :

1. **Déclencheur :** Le flux démarre lorsqu'un enregistrement de l'objet **Compte** est modifié.
2. **Exécution immédiate :** Les actions suivantes sont exécutées sans délai.
3. **Obtenir les contacts associés (Get All related contacts) :** Le système recherche et collecte tous les enregistrements de **Contact** qui sont liés au **Compte** qui a déclenché le flux.
4. **Boucle sur les contacts (Iterate all the contacts) :** Le flux entre dans une boucle pour traiter chaque enregistrement de **Contact** trouvé, un par un.
    - **Pour chaque contact dans la boucle :**
        - **Attribuer l'enregistrement (Assign each record) :** Une ou plusieurs valeurs sont assignées ou modifiées sur l'enregistrement de contact en cours de traitement dans la boucle.
        - **Collecter les contacts mis à jour (Get all the contacts updated records) :** L'enregistrement de contact modifié est ajouté à une collection (une liste) de contacts à mettre à jour.
5. **Après le dernier contact :** Une fois que la boucle a traité tous les contacts, l'action suivante est exécutée.
6. **Mettre à jour les enregistrements de contact (Update Contact record) :** Le système effectue une seule opération de mise à jour en bloc pour tous les contacts qui ont été collectés dans la liste à l'étape précédente. Cette méthode est efficace car elle minimise le nombre d'opérations DML (Data Manipulation Language).
7. **Fin :** Le flux termine son exécution.

En résumé, ce flux est conçu pour **mettre à jour automatiquement tous les contacts liés à un compte lorsque ce dernier est modifié**.



