---
"description": "Découvrez comment lier dynamiquement des données XML à des balises de documents structurés dans Word avec Aspose.Words pour .NET. Suivez notre guide étape par étape."
"linktitle": "Mappage XML de démarrage de plage de balises de document structuré"
"second_title": "API de traitement de documents Aspose.Words"
"title": "Mappage XML de démarrage de plage de balises de document structuré"
"url": "/fr/net/programming-with-sdt/structured-document-tag-range-start-xml-mapping/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Mappage XML de démarrage de plage de balises de document structuré

## Introduction

Avez-vous déjà souhaité insérer dynamiquement des données XML dans un document Word ? Ça tombe bien ! Aspose.Words pour .NET simplifie cette tâche. Dans ce tutoriel, nous explorons en profondeur le mappage XML de début de plage de balises de documents structurés. Cette fonctionnalité vous permet de lier des parties XML personnalisées à des contrôles de contenu, garantissant ainsi une mise à jour fluide du contenu de votre document avec vos données XML. Prêt à transformer vos documents en chefs-d'œuvre dynamiques ?

## Prérequis

Avant de passer à la partie codage, assurons-nous que vous disposez de tout ce dont vous avez besoin :

1. Bibliothèque Aspose.Words pour .NET : Assurez-vous d'avoir la dernière version. Vous pouvez la télécharger. [ici](https://releases.aspose.com/words/net/).
2. Environnement de développement : Visual Studio ou tout autre IDE prenant en charge C#.
3. Connaissances de base de C# : La familiarité avec la programmation C# est indispensable.
4. Document Word : un exemple de document Word avec lequel travailler.

## Importer des espaces de noms

Commençons par importer les espaces de noms nécessaires. Cela nous permettra d'accéder à toutes les classes et méthodes requises dans Aspose.Words pour .NET.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
using System.Text;
```

## Étape 1 : Configurez votre répertoire de documents

Tout projet a besoin d'une base, n'est-ce pas ? Ici, nous définissons le chemin d'accès à votre répertoire de documents.

```csharp
// Chemin d'accès à votre répertoire de documents 
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Étape 2 : Charger le document Word

Ensuite, nous chargeons le document Word. C'est dans ce document que nous allons insérer nos données XML.

```csharp
Document doc = new Document(dataDir + "Multi-section structured document tags.docx");
```

## Étape 3 : Ajouter une partie XML personnalisée

Nous devons créer une partie XML contenant les données à insérer et l'ajouter à la collection CustomXmlPart du document. Cette partie XML personnalisée servira de source de données pour les balises structurées de notre document.

### Création d'une partie XML

Tout d’abord, générez un identifiant unique pour la partie XML et définissez son contenu.

```csharp
// Construisez une partie XML contenant des données et ajoutez-la à la collection CustomXmlPart du document.
string xmlPartId = Guid.NewGuid().ToString("B");
string xmlPartContent = "<root><text>Text element #1</text><text>Text element #2</text></root>";
CustomXmlPart xmlPart = doc.CustomXmlParts.Add(xmlPartId, xmlPartContent);
```

### Vérifier le contenu de la partie XML

Pour garantir que la partie XML est correctement ajoutée, nous imprimons son contenu.

```csharp
Console.WriteLine(Encoding.UTF8.GetString(xmlPart.Data));
```

## Étape 4 : Créer une balise de document structurée

Une balise de document structurée (SDT) est un contrôle de contenu pouvant être lié à une partie XML. Ici, nous créons une SDT qui affichera le contenu de notre partie XML personnalisée.

Tout d’abord, localisez le début de la plage SDT dans le document.

```csharp
StructuredDocumentTagRangeStart sdtRangeStart = (StructuredDocumentTagRangeStart)doc.GetChild(NodeType.StructuredDocumentTagRangeStart, 0, true);
```

## Étape 5 : Définir le mappage XML pour le SDT

Il est maintenant temps de lier notre partie XML au SDT. En définissant un mappage XML, nous spécifions quelle partie des données XML doit être affichée dans le SDT.

Le XPath pointe vers l'élément spécifique de la partie XML que nous souhaitons afficher. Ici, nous pointons vers le deuxième élément. `<text>` élément dans le `<root>` élément.

```csharp
// Définir un mappage pour notre StructuredDocumentTag
sdtRangeStart.XmlMapping.SetMapping(xmlPart, "/root[1]/text[2]", null);
```

## Étape 6 : Enregistrer le document

Enfin, enregistrez le document pour visualiser les modifications. Le SDT du document Word affichera désormais le contenu XML spécifié.

```csharp
doc.Save(dataDir + "WorkingWithSdt.StructuredDocumentTagRangeStartXmlMapping.docx");
```

## Conclusion

Et voilà ! Vous avez réussi à mapper une partie XML à une balise de document structurée dans un document Word grâce à Aspose.Words pour .NET. Cette fonctionnalité puissante vous permet de créer facilement des documents dynamiques et axés sur les données. Que vous génériez des rapports, des factures ou tout autre type de document, le mappage XML peut considérablement optimiser votre flux de travail.

## FAQ

### Qu'est-ce qu'une balise de document structuré dans Word ?
Les balises de document structurées, également appelées contrôles de contenu, sont des conteneurs pour des types de contenu spécifiques dans les documents Word. Elles peuvent être utilisées pour lier des données, restreindre les modifications ou guider les utilisateurs dans la création de documents.

### Comment puis-je mettre à jour le contenu de la partie XML de manière dynamique ?
Vous pouvez mettre à jour le contenu de la partie XML en modifiant le `xmlPartContent` chaîne avant de l'ajouter au document. Il suffit de mettre à jour la chaîne avec les nouvelles données et de l'ajouter au `CustomXmlParts` collection.

### Puis-je lier plusieurs parties XML à différents SDT dans le même document ?
Oui, vous pouvez lier plusieurs parties XML à différents SDT dans un même document. Chaque SDT peut avoir sa propre partie XML et son propre mappage XPath.

### Est-il possible de mapper des structures XML complexes vers des SDT ?
Absolument ! Vous pouvez mapper des structures XML complexes à des SDT en utilisant des expressions XPath détaillées qui pointent précisément vers les éléments souhaités dans la partie XML.

### Comment puis-je supprimer une partie XML d’un document ?
Vous pouvez supprimer une partie XML en appelant la `Remove` méthode sur le `CustomXmlParts` collection, en passant le `xmlPartId` de la partie XML que vous souhaitez supprimer.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}