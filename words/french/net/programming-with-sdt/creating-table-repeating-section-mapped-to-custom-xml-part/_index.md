---
title: Création d'une section répétitive de tableau mappée sur une partie XML personnalisée
linktitle: Création d'une section répétitive de tableau mappée sur une partie XML personnalisée
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment créer un tableau avec une section répétitive mappée à un CustomXmlPart dans un document Word à l'aide d'Aspose.Words pour .NET.
weight: 10
url: /fr/net/programming-with-sdt/creating-table-repeating-section-mapped-to-custom-xml-part/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Création d'une section répétitive de tableau mappée sur une partie XML personnalisée

## Introduction

Dans ce didacticiel, nous allons parcourir le processus de création d'un tableau avec une section répétitive mappée à une partie XML personnalisée à l'aide d'Aspose.Words pour .NET. Cela est particulièrement utile pour générer dynamiquement des documents basés sur des données structurées.

## Prérequis

Avant de commencer, assurez-vous de disposer des éléments suivants :
1.  Bibliothèque Aspose.Words pour .NET installée. Vous pouvez la télécharger à partir du[Site Web d'Aspose](https://releases.aspose.com/words/net/).
2. Une compréhension de base de C# et XML.

## Importer des espaces de noms

Assurez-vous d'inclure les espaces de noms nécessaires dans votre projet :

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
using Aspose.Words.Tables;
```

## Étape 1 : Initialiser le document et DocumentBuilder

 Tout d’abord, créez un nouveau document et initialisez un`DocumentBuilder`:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Étape 2 : Ajouter une partie XML personnalisée

Ajoutez une partie XML personnalisée au document. Ce XML contient les données que nous souhaitons mapper à notre table :

```csharp
CustomXmlPart xmlPart = doc.CustomXmlParts.Add("Books",
    "<books><book><title>Everyday Italian</title><author>Giada De Laurentiis</author></book>" +
    "<book><title>Harry Potter</title><author>J K. Rowling</author></book>" +
    "<book><title>Learning XML</title><author>Erik T. Ray</author></book></books>");
```

## Étape 3 : Créer la structure du tableau

 Ensuite, utilisez le`DocumentBuilder` pour créer l'en-tête du tableau :

```csharp
Table table = builder.StartTable();
builder.InsertCell();
builder.Write("Title");
builder.InsertCell();
builder.Write("Author");
builder.EndRow();
builder.EndTable();
```

## Étape 4 : Créer une section répétitive

 Créer un`StructuredDocumentTag` (SDT) pour la section répétitive et la mapper aux données XML :

```csharp
StructuredDocumentTag repeatingSectionSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSection, MarkupLevel.Row);
repeatingSectionSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book", "");
table.AppendChild(repeatingSectionSdt);
```

## Étape 5 : Créer un élément de section répétitif

Créez un SDT pour l'élément de section répétitive et ajoutez-le à la section répétitive :

```csharp
StructuredDocumentTag repeatingSectionItemSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSectionItem, MarkupLevel.Row);
repeatingSectionSdt.AppendChild(repeatingSectionItemSdt);
Row row = new Row(doc);
repeatingSectionItemSdt.AppendChild(row);
```

## Étape 6 : mapper les données XML aux cellules du tableau

Créez des SDT pour le titre et l'auteur, mappez-les aux données XML et ajoutez-les à la ligne :

```csharp
StructuredDocumentTag titleSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
titleSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/title[1]", "");
row.AppendChild(titleSdt);

StructuredDocumentTag authorSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
authorSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/author[1]", "");
row.AppendChild(authorSdt);
```

## Étape 7 : Enregistrer le document

Enfin, enregistrez le document dans le répertoire spécifié :

```csharp
doc.Save(dataDir + "WorkingWithSdt.CreatingTableRepeatingSectionMappedToCustomXmlPart.docx");
```

## Conclusion

En suivant ces étapes, vous avez réussi à créer un tableau avec une section répétitive mappée sur une partie XML personnalisée à l'aide d'Aspose.Words pour .NET. Cela permet de générer du contenu dynamique basé sur des données structurées, ce qui rend la création de documents plus flexible et plus puissante.

## FAQ

### Qu'est-ce qu'un StructuredDocumentTag (SDT) ?
Un SDT, également connu sous le nom de contrôle de contenu, est une région délimitée dans un document utilisée pour contenir des données structurées.

### Puis-je utiliser d’autres types de données dans la partie XML personnalisée ?
Oui, vous pouvez structurer votre partie XML personnalisée avec n’importe quel type de données et les mapper en conséquence.

### Comment ajouter des lignes supplémentaires à la section répétitive ?
La section répétitive réplique automatiquement la structure de ligne pour chaque élément du chemin XML mappé.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
