---
title: Avant Installation Du Connecteur Pardot
---

# Avant installation du connecteur Pardot

Pour pouvoir afficher la version du connecteur, vous aurez besoin d’une autorisation utilisateur du rôle d’administrateur Pardot.

1. Ouvrez la page Paramètres du compte.
2. Dans Pardot, cliquez sur  et sélectionnez **Paramètres**.
3. Dans l’application Lightning, sélectionnez **Paramètres Pardot**.
4. Votre numéro de version s’affichera dans la ligne Version du connecteur.

![Untitled](/avant-installation-du-connecteur-pardot-untitled.png)

Vous devez examiner plusieurs éléments avant de réactiver votre connecteur Salesforce-Pardot. Pour vous faciliter l’installation, nous avons décrit les éléments à prendre en compte, tels que la synchronisation des champs et des prospects, le mappage des utilisateurs et d’autres tâches de configuration. Prenez quelques minutes pour examiner ces éléments avant de passer à la configuration de votre connecteur Salesforce-Pardot.

## Considérations générales avant la configuration

- Vous ne pouvez configurer qu’un seul connecteur Salesforce dans Pardot.
- Pardot peut s’intégrer aux types d’enregistrements de compte personnel Salesforce.
- L’importation de prospects dans Pardot synchronise ces derniers avec Salesforce. Les prospects non attribués sont synchronisés avec Salesforce, mais les enregistrements ne sont pas créés si aucune adresse e-mail n’est renseignée.
- Pardot recherche fréquemment les modifications dans Salesforce et Pardot, toutes les 2 minutes environ.

**Considérations relatives à la version 2 du connecteur**

- Lorsque votre compte Pardot est fourni, le connecteur est créé, avec un statut « en pause ».
- Les enregistrements de prospect ne se synchronisent pas automatiquement tant que le connecteur n’est pas activé. Les campagnes des utilisateurs et les métadonnées continuent de se synchroniser et les enregistrements de prospects peuvent être synchronisés annuellement quand le connecteur est en pause.
- Avant de le réactiver, assurez-vous de revoir les paramètres et de configurer le partage de données marketing si vous souhaitez l’utiliser. Nous vous recommandons fortement de faire appel à un partenaire pour cette partie de l’installation.
- Un prospect peut être synchronisé manuellement de deux manières : Synchroniser avec CRM sur un enregistrement de prospect ou Envoyer à Pardot sur un enregistrement de prospect ou de piste.
- L’utilisateur d’intégration a accès à tous les enregistrements pouvant être synchronisés entre Salesforce et Pardot. Si vous prévoyez de lier plusieurs comptes Pardot à un compte Salesforce, vous ne pouvez pas utiliser l’utilisateur d’intégration à moins que vous ne prévoyiez également d’utiliser le partage de données marketing.

**Comptes autorisant la présence de plusieurs prospects disposant de la même adresse e-mail**

Dans la synchronisation Salesforce, l’aspect le plus important consiste à créer une relation unique entre un prospect Pardot et une piste, un contact ou un compte personnel Salesforce. Le connecteur Salesforce-Pardot utilise l’ID CRM comme critère de correspondance pour synchroniser dans les deux sens les comptes qui autorisent les prospects multiples avec une même adresse e-mail.

Cela signifie que lorsque Salesforce crée un compte de piste, de contact ou personnel avec une adresse e-mail spécifique, un prospect est créé dans Pardot avec un ID CRM correspondant. Les données de chaque enregistrement sont synchronisées en fonction du comportement de synchronisation défini pour chaque champ. L’[article d’aide](https://help.salesforce.com/articleView?id=sf.pardot_sf_connector_considerations_for_ampsea.htm&type=5) est une excellente ressource pour en savoir plus sur les comptes autorisant la présence de plusieurs prospects disposant de la même adresse e-mail.

**Utilisateur d’intégration Pardot**

L’utilisateur d’intégration Pardot est un utilisateur provisionné automatiquement qui se connecte à Salesforce pour synchroniser les données. Pardot est la seule application qui peut se connecter à Salesforce via l’utilisateur d’intégration, et ce, uniquement après qu’elle a été configurée par un administrateur Salesforce.

L’application connectée Pardot utilise une méthode d’authentification sécurisée qui permet aux serveurs de l’application Pardot de s’authentifier auprès de Salesforce. L’application connectée contient la moitié publique d’une paire de clés sécurisées provisionnée sur Pardot. Si vous avez d’autres questions ou si vous avez besoin d’aide, consultez le lien dans la section Ressources.

**Choix de la méthode de synchronisation**

Lorsque l’utilisateur d’intégration est défini comme utilisateur du connecteur, le connecteur Salesforce-Pardot synchronise tous les enregistrements des objets synchronisés entre Pardot et Salesforce. Si vous souhaitez synchroniser un sous-ensemble d’enregistrements, utilisez le partage de données marketing pour sélectionner les enregistrements à synchroniser. Utilisez l’utilisateur d’intégration inclus ou configurez votre propre utilisateur du connecteur.

Lorsque vous utilisez le partage de données marketing, nous vous recommandons d’utiliser l’utilisateur d’intégration plutôt que de configurer votre propre utilisateur du connecteur. L’utilisateur d’intégration est préconfiguré avec les autorisations nécessaires et ne nécessite pas de licence Sales Cloud.



