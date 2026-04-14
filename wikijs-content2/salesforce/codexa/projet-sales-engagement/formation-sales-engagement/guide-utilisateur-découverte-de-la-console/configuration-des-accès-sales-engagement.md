---
title: Configuration Des Accès Sales Engagement
---

# Configuration des accès Sales Engagement

**Sales Engagement** (anciennement appelé **High Velocity Sales**) est une fonctionnalité Salesforce conçue pour aider les équipes de vente à automatiser et optimiser leurs interactions avec les prospects et clients. Pour utiliser cette fonctionnalité, vous devez disposer d'une licence spécifique pour **Sales Engagement** et suivre quelques étapes pour l'activer et le configurer.

### Étapes pour activer **Sales Engagement** dans Salesforce :

### 1. **Vérifiez les licences disponibles**

Avant d'activer **Sales Engagement**, assurez-vous que votre organisation Salesforce dispose des licences nécessaires.

1. Allez dans **Paramètres** (Setup) en cliquant sur l'icône d'engrenage en haut à droite de l'écran.
2. Dans la barre de recherche rapide, tapez **Company Information** (Informations sur l'entreprise) et cliquez dessus.
3. Dans cette section, cherchez les **licences** pour **Sales Engagement** pour vérifier si elles sont disponibles dans votre organisation.
    - Si vous n'avez pas de licences **Sales Engagement**, vous devrez contacter Salesforce pour obtenir ces licences ou en parler avec votre administrateur Salesforce.

### 2. **Activer Sales Engagement**

Si vous disposez des licences, vous pouvez activer **Sales Engagement**.

1. Allez dans **Paramètres** (Setup).
2. Dans la barre de recherche rapide, tapez **Sales Engagement** et sélectionnez **Sales Engagement Settings** (Paramètres de Sales Engagement).
3. Sur l'écran des paramètres de **Sales Engagement**, activez la fonctionnalité en basculant l'interrupteur **Enable Sales Engagement** (Activer Sales Engagement).

### 3. **Attribuer les licences aux utilisateurs**

Après avoir activé **Sales Engagement**, vous devez attribuer des licences et permissions aux utilisateurs concernés.

1. Allez dans **Paramètres** (Setup).
2. Recherchez **Users** (Utilisateurs) dans la barre de recherche et sélectionnez **Users**.
3. Trouvez l'utilisateur ou le groupe d'utilisateurs à qui vous voulez attribuer la licence **Sales Engagement**.

lien court : [https://codexa.lightning.force.com/lightning/setup/PermSets/home](https://codexa.lightning.force.com/lightning/setup/PermSets/home)

| Connaissances des conversations Sales Engagement | Permet aux utilisateurs de Sales Engagement d'accéder aux Connaissances des conversations Einstein pour Sales. |
| --- | --- |

| Créateur de cadence Sales Engagement | Permet aux utilisateurs responsables commerciaux d'accéder à l'application Sales Engagement, et de créer et modifier des cadences. |
| --- | --- |

| Créateur de cadence rapide Sales Engagement | Permet aux commerciaux d'accéder à l'application Sales Engagement, et de créer et modifier des cadences rapides. |
| --- | --- |

| Utilisateur de Sales Engagement | Permet aux utilisateurs d'accéder à l'application Sales Engagement, d'ajouter des clients à des cadences et de les contacter via la File d'attente des travaux. |
| --- | --- |

| Utilisateur de Sales Engagement Basic | Accédez aux fonctionnalités de base de l'automatisation commerciale et de la productivité par e-mail, y compris à Cadences rapide, e-mail automatisé, suivi des e-mails et insertion de la disponibilité. |
| --- | --- |

1. Cliquez sur l'utilisateur et attribuez-lui la **licence High Velocity Sales / Sales Engagement** dans la section des licences de l'utilisateur.

### 4. **Configurer les ensembles d'autorisations pour Sales Engagement**

Pour que vos utilisateurs puissent accéder à toutes les fonctionnalités de **Sales Engagement**, vous devrez configurer les **ensembles d'autorisations** :

1. Allez dans **Paramètres** (Setup).
2. Dans la barre de recherche rapide, tapez **Permission Sets** (Ensembles d’autorisations) et cliquez dessus.
3. Recherchez ou créez un ensemble d'autorisations pour **Sales Engagement**.
4. Incluez des autorisations comme **Sales Cadence**, **Einstein Activity Capture**, et d'autres fonctionnalités clés de **Sales Engagement**.
5. Attribuez cet ensemble d'autorisations aux utilisateurs qui utiliseront **Sales Engagement**.

### 5. **Configurer les fonctionnalités principales de Sales Engagement**

Une fois activé, vous devrez configurer certaines fonctionnalités clés de **Sales Engagement** :

- **Sales Cadences** : Créez et gérez des séquences d'engagement de vente automatisées pour vos représentants commerciaux afin qu'ils puissent suivre un parcours standardisé avec leurs prospects.
- **Einstein Activity Capture** : Utilisez cette fonctionnalité pour capturer automatiquement les e-mails et événements dans Salesforce.
- **Work Queues** : Configurez les files de travail qui permettent aux commerciaux de prioriser leurs activités et engagements.

### 6. **Configurer l'accès à Sales Engagement dans le lanceur d'application**

Après avoir activé et configuré **Sales Engagement**, vous pouvez ajouter le raccourci **Sales Engagement** dans le **Lanceur d'application** (App Launcher) pour les utilisateurs concernés (comme expliqué précédemment).

Une fois tout configuré, il suffit de recharger une page web ouverte sur Salesforce afin de vérifier si le lanceur d’application contient l’icône Sales Engagement. Ensuite, il faudra effectuer des tests pour s’assurer que l’équipe commerciale dispose des autorisation pour accéder à **Sales Engagement,** créer des cadences de vente, utiliser les files de travail et capturer des activités.

Pour activer **Sales Engagement**, vous devez :

1. Vérifier que vous disposez des licences nécessaires.
2. Activer la fonctionnalité dans les paramètres.
3. Attribuer les licences et ensembles d'autorisations aux utilisateurs.
4. Configurer les principales fonctionnalités comme les **Sales Cadences** et **Work Queues**.



