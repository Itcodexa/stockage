---
title: Import Export De Données
---

# Import & export de données

## **Export - Mode opératoire**

Pour exporter des données à l’aide de ce service, procéder comme suit :

1. Dans Setup (Configuration), saisir Data Export (Exporter les données) dans la zone Quick Find (Recherche rapide), puis sélectionner **Export Now (Exporter maintenant)** ou **Schedule Export (Planifier l’exportation)**.
    - L’option **Export Now (Exporter maintenant)** prépare les fichiers à une exportation immédiate. Cette option est disponible uniquement si suffisamment de temps s'est écoulé depuis la dernière exportation.
    - L’option **Schedule Export (Planifier l’exportation)** permet de programmer le processus d’exportation de sorte qu’il s’exécute à une fréquence mensuelle.
2. Sélectionner le codage souhaité pour votre fichier d'exportation (**généralement : ISO8859-1**)
3. Pour inclure des images, des documents et des pièces jointes dans vos données, activer la box “**Inclure des images, des documents et des pièces jointes**”
4. Sélectionner Replace carriage returns with spaces (Remplacer les retours à la ligne par des espaces) pour insérer des espaces à la place des retours à la ligne ou des sauts de ligne dans les fichiers d’exportation. Cette option est utile s’il est envisagé d'utiliser les fichiers d'exportation pour importer des données ou effectuer d'autres intégrations.
5. Si une exportation est planifiée, sélectionner la fréquence (disponible uniquement pour les organisations avec des exportations mensuelles), les dates de début et de fin ainsi que l'heure de lancement de l'exportation.
6. Sous Exported Data (Données exportées), sélectionner les types de données à inclure dans l’exportation. Il est recommandé de sélectionner **Include all data (Inclure toutes les données)** si la terminologie propre à certains types de données n’est pas maîtrisée.
7. Cliquer sur **Start Export (Démarrer l’exportation)** ou sur **Save (Enregistrer)**. Salesforce crée une archive zip de fichiers CSV et vous l'envoie par e-mail lorsqu'elle est prête. Les exportations seront terminées dès que possible. Cependant, il n’est pas possible de garantir la date et l’heure de fin de l’exportation. Les exportations volumineuses sont divisées en plusieurs fichiers. Il faut suivre le lien de l’e-mail ou cliquer sur **Data Export (Exportation de données)** pour télécharger le fichier zip. Les fichiers zip sont supprimés 48 heures après l'envoi de l'e-mail.

## **Import - Mode opératoire**

### Utilisation de l’assistant d’importation de données (moins de 50 000 enregistrements)

Lorsqu’un fichier d’exportation a été créé et que les données ont été mises à jour pour l’importation, il faut suivre la procédure ci-dessous pour importer les données à l’aide de l’assistant d’importation de données.

1. Démarrer l'assistant.
    1. Dans Setup (Configuration), saisir Data Import Wizard (Assistant d’importation de données) dans la zone Quick Find (Recherche rapide), puis sélectionner **Data Import Wizard (Assistant d’importation de données)**.
    2. Lire les informations indiquées sur la page d’accueil, puis cliquez sur **Launch Wizard! (Lancer l’assistant !)**
2. Choisir les données à importer.
    1. Pour importer des comptes, des contacts, des pistes, des solutions, des comptes personnels ou des membres de campagne, cliquer sur **Standard Objects (Objects standard)**. Pour importer des objets personnalisés, cliquer sur **Custom Objects (Objects personnalisés)**.
    2. Spécifier s’il faut ajouter de nouveaux enregistrements à Salesforce, mettre à jour des enregistrements existants ou ajouter et mettre à jour des enregistrements simultanément.
    3. Spécifier des critères de correspondance et d'autres critères si nécessaire. Pour plus d'informations sur chaque option, il suffit de survoler les points d'interrogation.
    4. Spécifier le fichier qui contient vos données. Il est possible de spécifier le fichier de données en faisant glisser le fichier CSV vers la zone de chargement de la page ou en cliquant sur la catégorie de fichier CSV utilisée, en accédant au fichier et en le sélectionnant.
    5. Choisir une méthode de codage de caractères pour votre fichier. La plupart des utilisateurs peuvent accepter le codage de caractères par défaut.
    6. Cliquer sur **Next (Suivant)**.
3. Mapper les champs de données avec des champs de données Salesforce. L’assistant d’importation de données essaie de mapper autant de champs de données que possible avec des champs de données Salesforce standard. Toutefois, si Salesforce ne peut pas mapper les champs automatiquement, Il est nécessaire de les mapper manuellement. Les champs non mappés ne sont pas importés dans Salesforce. Pour afficher la liste des champs de données Salesforce standard, dans Setup (Configuration) en haut de la page, cliquez sur **Object Manager (Gestionnaire d’objet)**. Cliquer sur les objets dont les champs vous intéressent, puis cliquer sur **Fields & Relationships (Champs et relations)**. Par exemple, pour afficher une liste de champs Salesforce standard relatifs aux pistes, cliquez sur **Object Manager (Gestionnaire d’objet)** | **Lead (Pistes)** | **Fields & Relationships (Champs et relations)**.
    1. Scanner la liste des champs de données mappés et localisez tous les champs non mappés.
    2. Cliquer sur **Map (Mapper)** à gauche de chaque champ non mappé.
    3. Dans la boîte de dialogue Map Your Field (Mapper votre champ), sélectionnez les champs Salesforce qui doit être mapper, puis cliquer sur **Map (Mapper)**. La boîte de dialogue Map Your Field (Mapper votre champ) permet également d’enregistrer, pour des comptes et des contacts, des données issues de champs non mappés dans un champ de note général. Pour cela, sélectionner Account Note (Note sur le compte) ou Contact Note (Note sur le contact) dans la liste déroulante Map To (Mapper avec), puis cliquer sur **Map (Mapper)**.
    4. Pour modifier des mappages ayant été mis en place automatiquement par Salesforce, cliquez sur **Change (Modifier)** à gauche du champ approprié, sélectionner les champs Salesforce avec lesquels vous souhaitez procéder à un mappage, puis cliquer sur **Map (Mapper)**.
    5. Cliquer sur **Next (Suivant)**.
4. Vérifier et lancer votre importation.
    1. Vérifier vos informations d'importation dans la page Révision. S’il reste des champs non mappés qui doivent être importés, cliquer sur **Previous (Précédent)** pour revenir à la page précédente et spécifier une nouvelle fois les mappages.
    2. Cliquer sur **Start Import (Démarrer l’importation)**.
5. Vérifier le statut d'importation. Dans Setup (Configuration), saisir « Bulk Data Load Jobs » (Tâches de chargement de données en masse) dans la zone Quick Find (Recherche rapide), puis sélectionner **Bulk Data Load Jobs (Tâches de chargement de données en masse)**. L’utilisateur qui a lancé l’importation des données reçoit un e-mail de statut une fois l’opération terminée.

[Universités](/salesforce/codexa/import-export-de-données/universités)



