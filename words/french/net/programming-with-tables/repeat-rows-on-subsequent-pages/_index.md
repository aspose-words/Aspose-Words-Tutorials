---
title: Répéter les lignes sur les pages suivantes
linktitle: Répéter les lignes sur les pages suivantes
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment créer des documents Word avec des lignes d'en-tête de tableau répétitives à l'aide d'Aspose.Words pour .NET. Suivez ce guide pour garantir des documents professionnels et soignés.
weight: 10
url: /fr/net/programming-with-tables/repeat-rows-on-subsequent-pages/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Répéter les lignes sur les pages suivantes

## Introduction

Créer un document Word par programmation peut être une tâche ardue, surtout lorsque vous devez conserver la mise en forme sur plusieurs pages. Avez-vous déjà essayé de créer un tableau dans Word, pour vous rendre compte que vos lignes d'en-tête ne se répètent pas sur les pages suivantes ? N'ayez crainte ! Avec Aspose.Words pour .NET, vous pouvez facilement vous assurer que vos en-têtes de tableau se répètent sur chaque page, offrant ainsi un aspect professionnel et soigné à vos documents. Dans ce didacticiel, nous vous guiderons à travers les étapes à suivre pour y parvenir à l'aide d'exemples de code simples et d'explications détaillées. Plongeons-nous dans le vif du sujet !

## Prérequis

Avant de commencer, assurez-vous de disposer des éléments suivants :

1.  Aspose.Words pour .NET : vous pouvez le télécharger[ici](https://releases.aspose.com/words/net/).
2. .NET Framework installé sur votre machine.
3. Visual Studio ou tout autre IDE prenant en charge le développement .NET.
4. Compréhension de base de la programmation C#.

Assurez-vous d’avoir installé Aspose.Words pour .NET et configuré votre environnement de développement avant de continuer.

## Importer des espaces de noms

Pour commencer, vous devez importer les espaces de noms nécessaires dans votre projet. Ajoutez les directives using suivantes en haut de votre fichier C# :

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Ces espaces de noms incluent les classes et les méthodes nécessaires pour manipuler les documents et les tableaux Word.

## Étape 1 : Initialiser le document

 Tout d’abord, créons un nouveau document Word et un`DocumentBuilder` pour construire notre table.

```csharp
// Chemin vers votre répertoire de documents
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Ce code initialise un nouveau document et un`DocumentBuilder` objet qui aide à construire la structure du document.

## Étape 2 : démarrer le tableau et définir les lignes d’en-tête

Ensuite, nous allons démarrer le tableau et définir les lignes d’en-tête que nous souhaitons répéter sur les pages suivantes.

```csharp
builder.StartTable();
builder.RowFormat.HeadingFormat = true;
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.CellFormat.Width = 100;

builder.InsertCell();
builder.Writeln("Heading row 1");
builder.EndRow();

builder.InsertCell();
builder.Writeln("Heading row 2");
builder.EndRow();
```

 Ici, nous commençons une nouvelle table, définissons les`HeadingFormat`propriété à`true` pour indiquer que les lignes sont des en-têtes et définir l'alignement et la largeur des cellules.

## Étape 3 : ajouter des lignes de données au tableau

Nous allons maintenant ajouter plusieurs lignes de données à notre tableau. Ces lignes ne se répéteront pas sur les pages suivantes.

```csharp
builder.CellFormat.Width = 50;
builder.ParagraphFormat.ClearFormatting();
for (int i = 0; i < 50; i++)
{
    builder.InsertCell();
    builder.RowFormat.HeadingFormat = false;
    builder.Write("Column 1 Text");
    
    builder.InsertCell();
    builder.Write("Column 2 Text");
    builder.EndRow();
}
```

 Cette boucle insère 50 lignes de données dans la table, avec deux colonnes dans chaque ligne.`HeadingFormat` est réglé sur`false` pour ces lignes, car ce ne sont pas des lignes d'en-tête.

## Étape 4 : Enregistrer le document

Enfin, nous enregistrons le document dans le répertoire spécifié.

```csharp
doc.Save(dataDir + "WorkingWithTables.RepeatRowsOnSubsequentPages.docx");
```

Cela enregistre le document avec le nom spécifié dans votre répertoire de documents.

## Conclusion

Et voilà ! Avec seulement quelques lignes de code, vous pouvez créer un document Word avec des tableaux comportant des lignes d'en-tête répétées sur les pages suivantes à l'aide d'Aspose.Words pour .NET. Cela améliore non seulement la lisibilité de vos documents, mais garantit également une apparence cohérente et professionnelle. Maintenant, allez-y et essayez ceci dans vos projets !

## FAQ

### Puis-je personnaliser davantage les lignes d’en-tête ?
 Oui, vous pouvez appliquer une mise en forme supplémentaire aux lignes d'en-tête en modifiant les propriétés de`ParagraphFormat`, `RowFormat` , et`CellFormat`.

### Est-il possible d'ajouter plus de colonnes au tableau ?
 Absolument ! Vous pouvez ajouter autant de colonnes que nécessaire en insérant plus de cellules dans le`InsertCell` méthode.

### Comment puis-je faire en sorte que d’autres lignes se répètent sur les pages suivantes ?
 Pour répéter une ligne, définissez le`RowFormat.HeadingFormat`propriété à`true` pour cette ligne spécifique.

### Puis-je utiliser cette méthode pour des tableaux existants dans un document ?
 Oui, vous pouvez modifier les tables existantes en y accédant via le`Document` objet et en appliquant un formatage similaire.

### Quelles autres options de formatage de tableau sont disponibles dans Aspose.Words pour .NET ?
 Aspose.Words pour .NET propose une large gamme d'options de mise en forme de tableau, notamment la fusion de cellules, les paramètres de bordure et l'alignement de tableau. Découvrez le[documentation](https://reference.aspose.com/words/net/) pour plus de détails.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
