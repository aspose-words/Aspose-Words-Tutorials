---
title: Mappage XML de démarrage de la plage de balises de document structuré
linktitle: Mappage XML de démarrage de la plage de balises de document structuré
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment lier dynamiquement des données XML à des balises de document structurées dans Word à l'aide d'Aspose.Words pour .NET. Suivez notre guide étape par étape.
weight: 10
url: /fr/net/programming-with-sdt/structured-document-tag-range-start-xml-mapping/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mappage XML de démarrage de la plage de balises de document structuré

## Introduction

Avez-vous déjà souhaité insérer dynamiquement des données XML dans un document Word ? Eh bien, vous avez de la chance ! Aspose.Words pour .NET simplifie cette tâche. Dans ce didacticiel, nous nous penchons en profondeur sur le mappage XML de début de plage de balises de document structuré. Cette fonctionnalité vous permet de lier des parties XML personnalisées à des contrôles de contenu, garantissant ainsi que le contenu de votre document se met à jour de manière transparente avec vos données XML. Vous êtes prêt à transformer vos documents en chefs-d'œuvre dynamiques.

## Prérequis

Avant de passer à la partie codage, assurons-nous que vous disposez de tout ce dont vous avez besoin :

1.  Bibliothèque Aspose.Words pour .NET : assurez-vous d'avoir la dernière version. Vous pouvez la télécharger[ici](https://releases.aspose.com/words/net/).
2. Environnement de développement : Visual Studio ou tout autre IDE prenant en charge C#.
3. Connaissances de base de C# : La familiarité avec la programmation C# est indispensable.
4. Document Word : un exemple de document Word avec lequel travailler.

## Importer des espaces de noms

Tout d'abord, importons les espaces de noms nécessaires. Cela nous permettra d'avoir accès à toutes les classes et méthodes requises dans Aspose.Words pour .NET.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
using System.Text;
```

## Étape 1 : Configurez votre répertoire de documents

Chaque projet a besoin d'une fondation, n'est-ce pas ? Ici, nous définissons le chemin d'accès vers votre répertoire de documents.

```csharp
// Chemin vers votre répertoire de documents
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Étape 2 : Charger le document Word

Ensuite, nous chargeons le document Word. C'est dans ce document que nous allons insérer nos données XML.

```csharp
Document doc = new Document(dataDir + "Multi-section structured document tags.docx");
```

## Étape 3 : Ajouter une partie XML personnalisée

Nous devons construire une partie XML contenant les données que nous souhaitons insérer et l'ajouter à la collection CustomXmlPart du document. Cette partie XML personnalisée servira de source de données pour nos balises de document structurées.

### Créer une partie XML

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

Une balise de document structurée (SDT) est un contrôle de contenu qui peut se lier à une partie XML. Ici, nous créons une balise de document structurée qui affichera le contenu de notre partie XML personnalisée.

Tout d’abord, localisez le début de la plage SDT dans le document.

```csharp
StructuredDocumentTagRangeStart sdtRangeStart = (StructuredDocumentTagRangeStart)doc.GetChild(NodeType.StructuredDocumentTagRangeStart, 0, true);
```

## Étape 5 : définir le mappage XML pour le SDT

Il est maintenant temps de lier notre partie XML au SDT. En définissant un mappage XML, nous spécifions quelle partie des données XML doit être affichée dans le SDT.

 Le XPath pointe vers l'élément spécifique de la partie XML que nous voulons afficher. Ici, nous pointons vers le deuxième`<text>` élément dans le`<root>` élément.

```csharp
// Définir un mappage pour notre StructuredDocumentTag
sdtRangeStart.XmlMapping.SetMapping(xmlPart, "/root[1]/text[2]", null);
```

## Étape 6 : Enregistrer le document

Enfin, enregistrez le document pour voir les modifications en action. Le SDT dans le document Word affichera désormais le contenu XML spécifié.

```csharp
doc.Save(dataDir + "WorkingWithSdt.StructuredDocumentTagRangeStartXmlMapping.docx");
```

## Conclusion

Et voilà ! Vous avez réussi à mapper une partie XML à une balise de document structurée dans un document Word à l'aide d'Aspose.Words pour .NET. Cette fonctionnalité puissante vous permet de créer sans effort des documents dynamiques et axés sur les données. Que vous génériez des rapports, des factures ou tout autre type de document, le mappage XML peut considérablement rationaliser votre flux de travail.

## FAQ

### Qu'est-ce qu'une balise de document structuré dans Word ?
Les balises de document structurées, également appelées contrôles de contenu, sont des conteneurs pour des types de contenu spécifiques dans les documents Word. Elles peuvent être utilisées pour lier des données, restreindre la modification ou guider les utilisateurs dans la création de documents.

### Comment puis-je mettre à jour le contenu de la partie XML de manière dynamique ?
 Vous pouvez mettre à jour le contenu de la partie XML en modifiant le`xmlPartContent` chaîne avant de l'ajouter au document. Mettez simplement à jour la chaîne avec les nouvelles données et ajoutez-la au`CustomXmlParts` collection.

### Puis-je lier plusieurs parties XML à différents SDT dans le même document ?
Oui, vous pouvez lier plusieurs parties XML à différents SDT dans le même document. Chaque SDT peut avoir sa propre partie XML et son propre mappage XPath.

### Est-il possible de mapper des structures XML complexes sur des SDT ?
Absolument ! Vous pouvez mapper des structures XML complexes à des SDT en utilisant des expressions XPath détaillées qui pointent avec précision vers les éléments souhaités dans la partie XML.

### Comment puis-je supprimer une partie XML d’un document ?
 Vous pouvez supprimer une partie XML en appelant la fonction`Remove` méthode sur le`CustomXmlParts` collection, en passant le`xmlPartId` de la partie XML que vous souhaitez supprimer.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
