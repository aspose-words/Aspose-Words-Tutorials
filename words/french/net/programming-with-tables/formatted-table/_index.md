---
title: Tableau formaté
linktitle: Tableau formaté
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment créer et formater des tableaux dans des documents Word à l'aide d'Aspose.Words pour .NET avec ce guide détaillé étape par étape.
weight: 10
url: /fr/net/programming-with-tables/formatted-table/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tableau formaté

## Introduction

Créer et formater des tableaux dans des documents Word par programmation peut sembler une tâche ardue, mais avec Aspose.Words pour .NET, cela devient simple et gérable. Dans ce didacticiel, nous vous expliquerons comment créer un tableau formaté dans un document Word à l'aide d'Aspose.Words pour .NET. Nous aborderons tout, de la configuration de votre environnement à l'enregistrement de votre document avec un tableau magnifiquement formaté.

## Prérequis

Avant de plonger dans le code, assurons-nous que vous avez tout ce dont vous avez besoin :

1. Bibliothèque Aspose.Words pour .NET : téléchargez-la depuis[ici](https://releases.aspose.com/words/net/).
2. Environnement de développement : un IDE comme Visual Studio.
3. .NET Framework : assurez-vous que .NET Framework est installé sur votre ordinateur.

## Importer des espaces de noms

Avant d'écrire le code réel, vous devez importer les espaces de noms nécessaires :

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

## Étape 1 : Configurez votre répertoire de documents

Tout d’abord, vous devez définir le chemin où votre document sera enregistré.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Remplacer`"YOUR DOCUMENT DIRECTORY"` avec le chemin réel où vous souhaitez enregistrer le document.

## Étape 2 : Initialiser le document et DocumentBuilder

Maintenant, initialisez un nouveau document et un objet DocumentBuilder.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Le`DocumentBuilder` est une classe d'aide qui simplifie le processus de création de documents.

## Étape 3 : Commencez la table

 Ensuite, commencez à créer la table en utilisant le`StartTable` méthode.

```csharp
Table table = builder.StartTable();
builder.InsertCell();
```

L'insertion d'une cellule est nécessaire pour commencer le tableau.

## Étape 4 : Appliquer la mise en forme à l'échelle du tableau

Vous pouvez appliquer une mise en forme qui affecte l'ensemble du tableau. Par exemple, définir le retrait à gauche :

```csharp
table.LeftIndent = 20.0;
```

## Étape 5 : formater la ligne d’en-tête

Définissez la hauteur, l’alignement et d’autres propriétés de la ligne d’en-tête.

```csharp
builder.RowFormat.Height = 40.0;
builder.RowFormat.HeightRule = HeightRule.AtLeast;
builder.CellFormat.Shading.BackgroundPatternColor = Color.FromArgb(198, 217, 241);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Font.Size = 16;
builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.CellFormat.Width = 100.0;
builder.Write("Header Row,\n Cell 1");
```

Dans cette étape, nous faisons ressortir la ligne d’en-tête en définissant une couleur d’arrière-plan, une taille de police et un alignement.

## Étape 6 : insérer des cellules d'en-tête supplémentaires

Insérer plus de cellules pour la ligne d’en-tête :

```csharp
builder.InsertCell();
builder.Write("Header Row,\n Cell 2");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Header Row,\n Cell 3");
builder.EndRow();
```

## Étape 7 : formater les lignes du corps

Après avoir configuré l'en-tête, formatez le corps du tableau :

```csharp
builder.CellFormat.Shading.BackgroundPatternColor = Color.White;
builder.CellFormat.Width = 100.0;
builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;
builder.RowFormat.Height = 30.0;
builder.RowFormat.HeightRule = HeightRule.Auto;
```

## Étape 8 : Insérer les lignes du corps

Insérer les lignes du corps avec le contenu :

```csharp
builder.InsertCell();
builder.Font.Size = 12;
builder.Font.Bold = false;
builder.Write("Row 1, Cell 1 Content");
builder.InsertCell();
builder.Write("Row 1, Cell 2 Content");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Row 1, Cell 3 Content");
builder.EndRow();
```

Répétez pour les lignes supplémentaires :

```csharp
builder.InsertCell();
builder.CellFormat.Width = 100.0;
builder.Write("Row 2, Cell 1 Content");
builder.InsertCell();
builder.Write("Row 2, Cell 2 Content");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Row 2, Cell 3 Content.");
builder.EndRow();
builder.EndTable();
```

## Étape 9 : Enregistrer le document

Enfin, enregistrez le document dans le répertoire spécifié :

```csharp
doc.Save(dataDir + "WorkingWithTables.FormattedTable.docx");
```

Cela créera et enregistrera un document Word avec le tableau formaté.

## Conclusion

Et voilà ! En suivant ces étapes, vous pouvez créer un tableau bien formaté dans un document Word à l'aide d'Aspose.Words pour .NET. Cette puissante bibliothèque facilite la manipulation programmatique des documents Word, vous faisant ainsi gagner du temps et des efforts.

## FAQ

### Qu'est-ce que Aspose.Words pour .NET ?
Aspose.Words pour .NET est une bibliothèque puissante permettant de créer, d'éditer et de convertir des documents Word par programmation.

### Puis-je utiliser différentes couleurs pour différentes rangées ?
Oui, vous pouvez appliquer différentes mises en forme, y compris des couleurs, à différentes lignes ou cellules.

### Aspose.Words pour .NET est-il gratuit ?
 Aspose.Words pour .NET est une bibliothèque payante, mais vous pouvez obtenir un[essai gratuit](https://releases.aspose.com/).

### Comment obtenir de l'assistance pour Aspose.Words pour .NET ?
 Vous pouvez obtenir de l'aide auprès de[Forums communautaires Aspose](https://forum.aspose.com/c/words/8).

### Puis-je créer d’autres types de documents avec Aspose.Words pour .NET ?
Oui, Aspose.Words pour .NET prend en charge divers formats de documents, notamment PDF, HTML et TXT.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
