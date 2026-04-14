---
title: Mise À Jour Icu Locale Formats
---

# Mise à jour ICU Locale Formats

Réalisé le 18/02/2025

**Date limite d’activation forcée : juin 2025.** 

Salesforce remplace son ancien système de gestion des formats de dates, nombres et devises par le standard international **ICU (International Components for Unicode)**. Ce changement peut sembler technique, mais il a des **conséquences concrètes sur vos données affichées et traitées au quotidien**.

En effet, un tel décalage peut **fausser vos rapports, altérer vos filtres** ou provoquer des erreurs dans vos automatisations.

**⚙️ Quels modules sont concernés ?**

- **Pardot (Marketing Cloud Account Engagement)** : Problèmes d’envois programmés ou de segmentation.
- **Automatisations (Flows, Triggers)** : Exécution sur des dates incorrectes.
- **Rapports & Tableaux de bord** : Mauvaise lecture des données temporelles.
- **Applications tierces intégrées** : Incompatibilités dues aux changements de formats.

## **🛠️ Comment mesurer l’étendue du problème dans votre organisation Salesforce ?**

### **🔎 Les requêtes à lancer dans votre org Salesforce**

*📂 Classes Apex concernées :*

*SELECT Name, ApiVersion, NamespacePrefix*

FROM ApexClass

WHERE ApiVersion < 45.0

ORDER BY NamespacePrefix, Name

*🔄 Triggers Apex concernés :*

*SELECT Name, ApiVersion, NamespacePrefix*

FROM ApexTrigger

WHERE ApiVersion < 45.0

ORDER BY NamespacePrefix, Name

*🖥️ Pages Visualforce concernées :*

*SELECT Name, ApiVersion, NamespacePrefix*

FROM ApexPage

WHERE ApiVersion < 45.0

ORDER BY NamespacePrefix, Name

**📝 Analyse des résultats**
**NamespacePrefix ≠ NULL** : Ces composants sont liés à des packages tiers. Leur gestion demande des actions spécifiques.

pi = Pardot

**Le package est géré directement par Salesforce** :

- Ouvrez un ticket auprès du support Salesforce via votre interface d’assistance.



