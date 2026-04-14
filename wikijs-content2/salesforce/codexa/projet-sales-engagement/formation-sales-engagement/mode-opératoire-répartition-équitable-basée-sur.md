---
title: Mode Opératoire Répartition Équitable Basée Sur
---

# Mode opératoire - Répartition équitable basée sur l'ordre défini

## Objectifs

- Les leads seront assignés de manière équitable et tournante (Round Robin) aux membres de la file d'attente.
- La variable `LastAssignedUser` garantit que chaque commercial reçoit un lead à son tour.

### **Étape 1 : Créer une file d'attente (Queue)**

1. **Accédez à Setup** :
    - Cliquez sur l'icône en forme d'engrenage en haut à droite, puis sélectionnez **Setup**.
2. **Recherchez "Queues"** :
    - Dans la barre de recherche rapide (à gauche), tapez **"Queues"** et sélectionnez **Queues** sous la section **Manage Users**.
3. **Créez une nouvelle file d'attente** :
    - Cliquez sur **New**.
    - Remplissez les champs suivants :
        - **Label** : Donnez un nom à votre file d'attente (ex: "Leads - Équipe Commerciale").
        - **Queue Name** : Ce champ se remplit automatiquement.
        - **Supported Objects** : Sélectionnez **Lead** (cochez la case).
    - Cliquez sur **Save**.
4. **Ajoutez des membres à la file d'attente** :
    - Sur la page de détails de la file d'attente, cliquez sur **Add** dans la section **Queue Members**.
    - Sélectionnez les **utilisateurs** (commerciaux) que vous souhaitez ajouter à la file.
    - Cliquez sur **Save**.

### **Étape 2 : Configurer les règles d'assignation (Assignment Rules)**

1. **Accédez à Setup** :
    - Retournez dans **Setup**.
2. **Recherchez "Lead Assignment Rules"** :
    - Dans la barre de recherche rapide, tapez **"Lead Assignment Rules"** et sélectionnez **Lead Assignment Rules**.
3. **Créez une nouvelle règle d'assignation** :
    - Cliquez sur **New**.
    - Donnez un nom à votre règle (ex: "Assignation Équitable des Leads").
    - Cliquez sur **Save**.
4. **Ajoutez une entrée de règle** :
    - Cliquez sur **New** dans la section **Rule Entries**.
    - Remplissez les champs suivants :
        - **Order** : 1 (cela définit l'ordre d'exécution de la règle).
        - **Criteria** : Définissez les conditions pour déclencher cette règle. Par exemple, vous pouvez choisir "Tous les nouveaux leads" en laissant les critères vides.
        - **Assign to** : Sélectionnez la file d'attente que vous avez créée à l'étape 1.
    - Cliquez sur **Save**.
5. **Activez la règle d'assignation** :
    - Retournez à la page principale des **Lead Assignment Rules**.
    - Cochez la case **Active** à côté de votre nouvelle règle.



