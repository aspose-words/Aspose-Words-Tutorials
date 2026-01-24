---
date: 2026-01-24
description: Apprenez à fusionner des données XML avec Aspose.Words pour Java, à automatiser
  la génération de documents Java et à utiliser la syntaxe Mustache pour des documents
  dynamiques.
linktitle: Using XML Data
second_title: Aspose.Words Java Document Processing API
title: Comment fusionner XML dans Aspose.Words pour Java
url: /fr/java/document-manipulation/using-xml-data/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Comment fusionner du XML dans Aspose.Words pour Java

Dans ce guide complet, vous découvrirez **comment fusionner du XML** à l'aide d'Aspose.Words pour Java. Nous parcourrons les scénarios de publipostage de base et imbriqués, vous montrerons comment **utiliser la syntaxe Mustache**, et expliquerons comment **automatiser la génération de documents** de style Java. À la fin, vous serez capable de générer des documents Word personnalisés directement à partir de sources XML en quelques lignes de code.

## Réponses rapides
- **Quelle est la classe principale pour le publipostage ?** `Document` et sa propriété `MailMerge`.  
- **Puis-je fusionner des tables XML imbriquées ?** Oui – utilisez `executeWithRegions` pour les données hiérarchiques.  
- **La syntaxe Mustache est‑elle prise en charge ?** Activez‑la avec `setUseNonMergeFields(true)`.  
- **Ai‑je besoin d’une licence pour la production ?** Une licence commerciale d’Aspose.Words est requise.  
- **Quelle version de Java est compatible ?** Java 8+ et les versions ultérieures sont entièrement prises en charge.

## Qu’est‑ce que le publipostage XML dans Aspose.Words ?
Le publipostage XML vous permet de lier des ensembles de données basés sur XML à des espaces réservés dans un modèle Word. Le moteur remplace chaque espace réservé par la valeur du nœud XML correspondant, produisant un document final sans édition manuelle.

## Pourquoi utiliser Aspose.Words pour la génération de documents basés sur XML ?
- **Automatisez la génération de documents Java** sans aucune dépendance à Microsoft Office.  
- **Prise en charge des hiérarchies complexes** répétitives et contenu conditionnel.  
-, pour un templating avancé.  
- **Multi‑plateforme** – fonctionne sous Windows, Linux et macOS.

## Prérequis

Avant de commencer, assurez‑vous de disposer de ce qui suit :

- [Aspose.Words for Java](https://products.aspose.com/words/java/) installé (la dernière version).  
- Fichiers XML d'exemple pour les clients, les commandes et les fournisseurs (le tutoriel utilise `Mail merge data - Customers.xml`, `Orders.xml` et `Vendors.xml`).  
- Documents modèles Word contenant des champs de publipostage (par ex., `Registration complete.docx`, `Invoice.docx`, `Vendor.docx`).  

## Comment fusionner du XML – Publipostage de base

Un publipostage de base récupère une table XML unique dans un modèle Word. Suivez ces étapes :

1. Chargez le fichier XML dans un `DataSet`.  
2. Ouvrez le document Word de destination.  
3. Exécutez le publipostage en utilisant le nom de la table.  
4. Enregistrez le document fusionné.

```java
DataSet customersDs = new DataSet();
customersDs.readXml("Your Directory Path" + "Mail merge data - Customers.xml");
Document doc = new Document("Your Directory Path" + "Mail merge destinations - Registration complete.docx");
doc.getMailMerge().execute(customersDs.getTables().get("Customer"));
doc.save("Your Directory Path" + "BasicMailMerge.docx");
```

**Astuce :** Gardez votre structure XML plate pour les fusions simples – chaque table doit correspondre directement à un ensemble de champs de publipostage.

## Comment fusionner du XML – Publip votre XML contient des relations parent‑enfant (par ex., des commandes avec des lignes d'articles), vous avez besoin d'un publipostage imbriqué. La méthode `executeWithRegions` traite chaque région de manière récursive.

1. Chargez le XML hiérarchique dans un `DataSet`.  
2. Désactivez la suppression des espaces blancs si vous avez besoin d'un formatage exact.  
3. Appelez `executeWithRegions` pour gérer toutes les tables imbriquées.  
4. Enregistrez le résultat.

```java
DataSet pizzaDs = new DataSet();
pizzaDs.readXml("Your Directory Path" + "Mail merge data - Orders.xml");
Document doc = new Document("Your Directory Path" + "Mail merge destinations - Invoice.docx");
doc.getMailMerge().setTrimWhitespaces(false);
doc.getMailMerge().executeWithRegions(pizzaDs);
doc.save("Your Directory Path" + "NestedMailMerge.docx");
```

**Erreur courante :** Oublier de définir `setTrimWhitespaces(false)` peut entraîner des espaces indésirables dans le document final, notamment pour les champs monétaires ou numériques.

## Comment utiliser la syntaxe Mustache avec un DataSet

La syntaxe Mustache vous permet d'insérer des espaces réservés non liés aux champs de publipostage (par ex., `{{CustomerName}}`) dans votre modèle. Activez‑la et exécutez un publipostage basé sur les régions.

1. Chargez le XML du fournisseur.  
2. Activez la prise en charge de Mustache avec `setUseNonMergeFields(true)`.  
3. Exécutez le publipostage avec les régions.  
4. Enregistrez la sortie.

```java
DataSet ds = new DataSet();
ds.readXml("Your Directory Path" + "Mail merge data - Vendors.xml");
Document doc = new Document("Your Directory Path" + "Mail merge destinations - Vendor.docx");
doc.getMailMerge().setUseNonMergeFields(true);
doc.getMailMerge().executeWithRegions(ds);
doc.save("Your Directory Path" + "MustacheSyntaxUsingDataSet.docx");
```

**Pourquoi utiliser Mustache ?** Elle offre une façon claire et indépendante du langage de référencer les données, rendant vos modèles plus faciles à lire et à maintenir, surtout lors de **la génération de documents** pilotés par XML.

## Problèmes courants et solutions

| Problème | Solution |
|----------|----------|
| Nœuds XML ne correspondant pas aux champs de publipostage | Vérifiez que les noms des éléments XML correspondent exactement aux noms des champs de publipostage (sensible à la casse). |
| Des espaces blancs apparaissent autour des valeurs fusionnées | Utilisez `doc.getMailMerge().setTrimWhitespaces(false)` pour préserver l'espacement original. |
| Les tables imbriquées sont ignorées | Assurez‑vous que la région de la table parent est définie dans le modèle (par ex., `{{#Orders}} … {{/Orders}}`). |
| Les espaces réservés Mustache ne sont pas remplacés | Appelez `setUseNonMergeFields(true)` avant d'exécuter le publipostage. |

## FAQ

### Comment préparer mes données XML pour le publipostage ?
Assurez‑vous que votre XML suit une structure tabulaire où chaque élément `<TableName>` contient des lignes (`<Row>`) et des colonnes correspondant aux champs de publipostage de votre modèle Word.

### Puis‑je personnaliser le comportement de suppression des espaces pour les valeurs du publipostage ?
Oui. Utilisez `doc.getMailMerge().setTrimWhitespaces(false)` pour conserver les espaces de début/fin exactement tels qu'ils apparaissent dans le XML.

### Qu’est‑ce que la syntaxe Mustache, et quand l’utiliser ?
La syntaxe Mustache (`{{FieldName}}`) permet des espaces réservés flexibles qui ne sont pas limités aux champs de publipostage traditionnels. Activez‑la avec `setUseNonMergeFields(true)` lorsque vous avez besoin d’un modèle plus propre ou souhaitez séparer la logique des données du code des champs Word.

### Comment automatiser la génération de documents dans les projets Java avec cette approche ?
Intégrez les extraits de code ci‑dessus dans votre couche de service, lisez le XML depuis des bases de données ou des API, et invoquez la routine de publipostage chaque fois qu’un nouveau document est requis (par ex., génération de factures, création de contrats).

### Une licence commerciale est‑elle requise pour une utilisation en production ?
Oui, Aspose.Words nécessite une licence valide pour les déploiements en production. Une licence temporaire gratuite est disponible pour l’évaluation.

---

**Dernière mise à jour :** 2026-01-24  
**Testé avec :** Aspose.Words for Java (dernière version)  
**Auteur :** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}