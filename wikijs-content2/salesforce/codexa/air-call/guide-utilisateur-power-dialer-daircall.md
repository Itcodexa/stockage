---
title: Guide Utilisateur Power Dialer Daircall
---

# Guide utilisateur -  Power Dialer d'Aircall

# Comment l’utiliser depuis l’intégration Salesforce ?

Rendre les appels sortants efficaces n'est pas une tâche facile. Power Dialer est la solution Aircall pour rationaliser les flux d'appels sortants.

## Quels sont les objectifs ?

Gagner du temps et maximiser la couverture des numéros par session, tout en minimisant les tâches manuelles. 

### Le process en pratique

Plus besoin de basculer entre les outils et de copier-coller des numéros de téléphone entre les appels. L’utilisateur peut importer des numéros en un clic dans sa liste de numérotation et commencer à appeler sans interruption. Le temps de travail après l'appel garantit une conservation précise des enregistrements - plus de notes ou d'étiquettes manquantes à la fin de chaque numérotation.

Chaque liste de numérotation est facilement accessible depuis la vue À faire et peut être mise à jour ou lancée à tout moment.

## Comment accéder au Power Dialer ?

La fonctionnalité Power Dialer est actuellement disponible sur le CTI d'Aircall avec l’intégration Salesforce.

⚠️ Les appareils mobiles utilisant l'application Aircall ne pourront pas utiliser le Power Dialer.

Accéder à la vue To-do pour importer et composer facilement des listes. Pour l'utiliser avec l'extension Chrome, assurez-vous d'avoir installé la dernière version à partir du [Chrome Web Store](https://chrome.google.com/webstore/category/extensions) .

[](https://support.aircall.io/hc/article_attachments/24517489384221)

⚠️ Pour masquer le Power Dialer, cliquer simplement sur la flèche à côté de celui-ci. Le Power Dialer restera dans un état réduit jusqu'à ce qu'un utilisateur le développe à nouveau manuellement.

## Comment ajouter des numéros à la liste ?

Le Power Dialer fonctionne sur la base de la liste importée. Il existe plusieurs façons d'intégrer des numéros de téléphone à votre liste Power Dialer : importer un fichier CSV, copier-coller des numéros ou ajouter des numéros via l'extension de navigateur Chrome d'Aircall.

### **1. Importer des numéros via un fichier CSV**

Pour préparer un fichier CSV à importer, voici quelques conseils rapides :

- La taille du fichier est limitée à 1 Mo ou 1 000 contacts
- Les numéros doivent être au format Excel pour Aircal (33)
- La première colonne contenant les nombres doit avoir un « titre »

⚠️ Remarque : l'importateur ne reconnaît que la colonne A d'une feuille de calcul et toutes les autres sont ignorées. 

[](https://support.aircall.io/hc/article_attachments/24517500354077)

Pour importer des numéros via .CSV dans Power Dialer :

- Cliquer sur « Créer une liste » dans le menu Power Dialer de la vue À faire
- Glisser et déposer le fichier CSV avec le format de numéro attendu
- La liste est importée avec succès

[](https://support.aircall.io/hc/article_attachments/24517489385245)

[](https://support.aircall.io/hc/article_attachments/24517500355101)

### **2. Copier-coller des numéros**

Les bonnes pratiques pour créer une liste manuellement : 

- Les listes sont limitées à 1 000 contacts
- Les numéros doivent être au format Aircall (+33)
- Le séparateur entre les valeurs doit être une virgule ou un point-virgule

Les étapes à suivre :

- Cliquer sur « Créer une liste » dans le menu Power Dialer
- Puis sur le bouton « Saisir manuellement »
- Copier les numéros au format attendu ou les saisir manuellement
- Cliquer sur « Ajouter des numéros »
- La liste a été ajoutée avec succès !

[](https://support.aircall.io/hc/article_attachments/24517500355485)

### **Gérer la liste**

Dans la vue dédiée, chaque utilisateur voit la « liste de numérotation » avec le nombre de numéros importés et le bouton « Démarrer la session ». Vous pouvez accéder à la liste **à tout moment** en cliquant sur « Ma liste de numérotation », la liste détaillée des numéros s'affichera.

Si les numéros sont déjà connus dans le système, vous verrez quelques détails de contact, tels que le prénom et le nom, le nom de l'entreprise et quelques lignes des notes de contact. Sinon, seul le numéro sera affiché.

À partir de cette vue, vous pouvez modifier la liste, si nécessaire. Supprimez les numéros un par un ou supprimez la liste avec le bouton « Archiver la liste ». Ajoutez d'autres numéros en important le nouveau fichier CSV ou en saisissant les numéros manuellement. Les numéros ajoutés à partir des pages Web avec l'extension Chrome seront également intégrés à cette liste (pour plus de détails, consultez [cet article](https://support.aircall.io/hc/en-gb/articles/10375354868893) ).

[](https://support.aircall.io/hc/article_attachments/24517489386141)

### **Erreurs et doublons**

En cas de problème de format ou de taille de fichier, vous serez averti comme suit :

- « L'importation a échoué - aucun numéro ajouté. Veuillez vous assurer que votre fichier est au format .CSV et réessayer »
- « L'importation a échoué - aucun numéro ajouté. Veuillez vous assurer que votre fichier contient un maximum de 1 000 enregistrements et réessayez »

Le format de numéro non valide et les doublons sont automatiquement rejetés. Si un tel problème survient, vous obtiendrez un résumé pertinent et pourrez télécharger les erreurs :

- Les numéros XX/XX sont importés avec succès
- X erreurs et X doublons sont détectés.

Si aucune de ces erreurs ne semble pertinente, vous pouvez ignorer cette étape et passer à la numérotation « Ignorer et passer à la numérotation » ou aller « Retour à l'importation » pour ajouter d'autres numéros.

[](https://support.aircall.io/hc/article_attachments/24517489386653)

[](https://support.aircall.io/hc/article_attachments/24517500356509)

## Gérer la session de numérotation

Cliquez sur « Démarrer la session » dans la vue Tâches ou dans les détails de la liste pour commencer la numérotation. Sélectionnez la ligne téléphonique que vous souhaitez utiliser pour cette session d'appel sortant. Ce paramètre sera appliqué à tous les numéros et ne pourra pas être modifié au cours d'une session.

[](https://support.aircall.io/hc/article_attachments/24517500357533)

Une fois la session démarrée, les appels vous seront automatiquement présentés en respectant l'ordre de la liste.

Pendant la session, vous pouvez gérer un appel spécifique :

- « Passer au suivant » et passer au numéro suivant dans la file d'attente
- Afficher les informations liées à votre CRM dans la vue d'appel
- Étiqueter ou commenter dans l'appel

Ou gérer toute la session :

- Supprimer un ou plusieurs numéros de la séquence à l'exception de l'appel en cours
- Supprimer toute la séquence en archivant la liste
- Mettre la session en pause dans le coin supérieur droit pour arrêter temporairement la séquence d'appel
- Ajouter à la liste de suivi un contact spécifique

[](https://support.aircall.io/hc/article_attachments/24517489390749)

## Temps de clôture

Lorsque vous utilisez le Power Dialer, vous bénéficiez du temps de clôture dédié, s'il est configuré, après chaque appel pour ajouter des balises, des notes ou pour effectuer tout travail nécessaire après l'appel. Une fois le temps de clôture expiré, le Power Dialer commencera automatiquement à composer le numéro suivant de la liste.

Si le balisage obligatoire est activé pour votre numéro, il apparaîtra également après l'appel comme d'habitude. Sinon, la vue Appel terminé s'affichera lorsque le temps de clôture commencera.

[Apprenez-en plus sur la configuration du délai de clôture ici.](https://support.aircall.io/hc/en-gb/articles/10375354632477)



