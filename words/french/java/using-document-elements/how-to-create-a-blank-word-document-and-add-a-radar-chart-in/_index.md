---
category: general
date: 2026-09-21
description: Créez un document Word vierge et apprenez comment insérer un graphique
  radar dans un fichier Word à l’aide de DocumentBuilder – guide étape par étape.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert radar chart
- insert chart word file
- generate word document chart
- add radial chart word
language: fr
lastmod: 2026-09-21
og_description: Créer un document Word vierge et insérer un graphique radar dans un
  fichier Word avec Aspose.Words. Suivez ce tutoriel pour générer rapidement un graphique
  dans un document Word.
og_image_alt: Screenshot showing a blank Word document with a radar chart inserted
og_title: Créer un document Word vierge et ajouter un graphique radar – guide complet
  C#
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create blank Word document and learn how to insert radar chart in a
    Word file using DocumentBuilder – step‑by‑step guide.
  headline: How to create a blank Word document and add a radar chart in C#
  type: TechArticle
- description: Create blank Word document and learn how to insert radar chart in a
    Word file using DocumentBuilder – step‑by‑step guide.
  name: How to create a blank Word document and add a radar chart in C#
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 or later (the code also works with .NET Framework 4.6+). * Aspose.Words
      for .NET (NuGet package `Aspose.Words` version 23.9 or newer). * Basic familiarity
      with C# and Visual Studio or your preferred IDE.'
  - name: Expected output
    text: '* A `RadialChartExample.docx` file on your desktop. * The first page contains
      a radar chart with five data points labeled “Series 1”. * No additional text
      appears because the document started blank.'
  - name: 1. Changing chart size after insertion
    text: 'If the initial dimensions don’t fit your layout, resize the chart like
      this:'
  - name: 2. Inserting the chart into a specific location
    text: You can move the builder’s cursor to a bookmark, table cell, or paragraph
      before calling `InsertChart`.
  - name: 3. Customizing chart appearance
    text: Aspose.Words exposes the full chart object model, allowing you to set titles,
      axis labels, and colors.
  - name: 4. Dealing with missing fonts
    text: 'If the target environment lacks a font used in the chart, Aspose.Words
      substitutes a default font. To guarantee consistency, embed the required fonts:'
  - name: 5. Exporting to other formats
    text: 'The same document can be saved as PDF, HTML, or PNG without extra code
      changes:'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart generation
title: Comment créer un document Word vierge et ajouter un graphique radar en C#
url: /fr/java/using-document-elements/how-to-create-a-blank-word-document-and-add-a-radar-chart-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer un document Word vierge et y ajouter un graphique radar en C#

Si vous devez **créer un document Word vierge** et y intégrer un graphique radar (radial), ce tutoriel vous fournit une solution prête à l’emploi. Vous verrez comment utiliser Aspose.Words .NET pour générer le fichier, insérer le graphique et enregistrer le résultat — le tout en quelques étapes concises.

Un document vierge offre une toile propre pour tout scénario de génération de rapports automatisés, et l’ajout d’un graphique radar vous permet de visualiser des données multidimensionnelles directement dans Word. À la fin de ce guide, vous serez capable de générer un document Word contenant un graphique sans aucune édition manuelle.

## Ce que vous allez apprendre

* Comment **créer un document Word vierge** programmatique avec C#.
* Le code exact pour **insérer un graphique radar** à l’aide de `DocumentBuilder`.
* Les différentes manières **d’insérer un graphique dans un fichier Word** et de personnaliser sa taille.
* Comment **générer un graphique dans un document Word** et vérifier le résultat.
* Astuces pour **ajouter des graphiques radiaux dans des fichiers Word**, y compris les pièges courants.

### Prérequis

* .NET 6.0 ou ultérieur (le code fonctionne également avec .NET Framework 4.6+).
* Aspose.Words for .NET (package NuGet `Aspose.Words` version 23.9 ou plus récent).
* Une connaissance de base du C# et de Visual Studio ou de votre IDE préféré.

## Créer un document Word vierge avec C#

La première étape consiste à instancier un objet `Document` vide. Cet objet représente un fichier `.docx` totalement vierge.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

// Step 1: Create a new blank document
Document doc = new Document();
```

`Document` crée la structure du fichier mais ne contient aucune section ni aucune page pour l’instant. Aspose.Words ajoute automatiquement une section par défaut lorsque vous commencez à ajouter du contenu, ce qui explique pourquoi l’étape suivante fonctionne sans configuration supplémentaire.

## Comment insérer un graphique radar dans le fichier Word

Un graphique radar (également appelé graphique radial) visualise des points de données sur des axes qui rayonnent à partir d’un point central. Aspose.Words fournit `DocumentBuilder.insertChart` à cet effet.

```csharp
// Step 2: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(doc);

// Step 3: Insert a radar (radial) chart with the desired size (width: 400pt, height: 300pt)
Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

`InsertChart` renvoie un objet `Chart` que vous pouvez configurer davantage. Le graphique apparaît sur la première page du document vierge parce que le builder est positionné au début du document par défaut.

## Insérer le graphique dans un fichier Word – ajout de séries de données

Un graphique sans données est invisible. Remplissez le graphique radar avec une ou plusieurs séries pour le rendre significatif.

```csharp
// Step 4: Populate the chart with series data
ChartSeries series = radarChart.Series.Add("Series 1");

// Add data points (example values)
series.DataPoints.Add(4);
series.DataPoints.Add(7);
series.DataPoints.Add(3);
series.DataPoints.Add(6);
series.DataPoints.Add(5);
```

Vous pouvez ajouter autant de séries que nécessaire. Chaque série peut avoir un nom distinct, qui apparaît dans la légende du graphique. Les points de données correspondent aux axes radiaux ; l’ordre dans lequel vous les ajoutez définit leur position autour du cercle.

## Générer un graphique dans un document Word – sauvegarde du fichier

Après avoir construit le graphique, persistez le document sur le disque. Choisissez un emplacement où vous avez les droits d’écriture.

```csharp
// Step 5: Save the document containing the radar chart
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), 
                                 "RadialChartExample.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Lorsque vous ouvrez le fichier `.docx` résultant dans Microsoft Word, vous verrez une page vierge contenant un graphique radar de taille 400 × 300 points, rempli avec les données d’exemple.

### Résultat attendu

* Un fichier `RadialChartExample.docx` sur votre bureau.
* La première page contient un graphique radar avec cinq points de données libellés « Series 1 ».
* Aucun texte supplémentaire n’apparaît car le document a commencé vierge.

## Ajouter un graphique radial dans Word – gestion des cas limites courants

### 1. Modifier la taille du graphique après insertion

Si les dimensions initiales ne correspondent pas à votre mise en page, redimensionnez le graphique ainsi :

```csharp
radarChart.Width = 500;   // width in points
radarChart.Height = 350;  // height in points
```

### 2. Insérer le graphique à un emplacement spécifique

Vous pouvez déplacer le curseur du builder vers un signet, une cellule de tableau ou un paragraphe avant d’appeler `InsertChart`.

```csharp
builder.MoveToBookmark("ChartLocation");
Chart chartInTable = builder.InsertChart(ChartType.Radar, 350, 250);
```

### 3. Personnaliser l’apparence du graphique

Aspose.Words expose le modèle complet d’objets du graphique, vous permettant de définir les titres, les libellés d’axes et les couleurs.

```csharp
radarChart.Title.Text = "Sales Performance";
radarChart.Series[0].FillFormat.ForeColor = System.Drawing.Color.Blue;
radarChart.AxisX.Title.Text = "Quarter";
radarChart.AxisY.Title.Text = "Revenue (M)";
```

### 4. Gérer les polices manquantes

Si l’environnement cible ne possède pas une police utilisée dans le graphique, Aspose.Words substitue une police par défaut. Pour garantir la cohérence, intégrez les polices requises :

```csharp
doc.FontSettings.SubstitutionSettings.DefaultFontName = "Arial";
```

### 5. Exporter vers d’autres formats

Le même document peut être enregistré en PDF, HTML ou PNG sans modifications de code supplémentaires :

```csharp
doc.Save("RadialChartExample.pdf");
```

## Exemple complet, exécutable

Assembler toutes les pièces donne un programme unique que vous pouvez copier, coller et exécuter.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class RadarChartDemo
{
    static void Main()
    {
        // Create a new blank document
        Document doc = new Document();

        // Initialize DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a radar chart (400pt x 300pt)
        Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);

        // Add a data series with sample values
        ChartSeries series = radarChart.Series.Add("Quarterly Sales");
        series.DataPoints.Add(4);
        series.DataPoints.Add(7);
        series.DataPoints.Add(3);
        series.DataPoints.Add(6);
        series.DataPoints.Add(5);

        // Optional: customize appearance
        radarChart.Title.Text = "Quarterly Sales Radar";
        radarChart.AxisX.Title.Text = "Quarter";
        radarChart.AxisY.Title.Text = "Units Sold";

        // Save the document
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadialChartExample.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Exécutez ce programme, ouvrez le fichier généré, et vous verrez un graphique radar professionnel prêt à être distribué.

## Conclusion

Vous savez maintenant comment **créer un document Word vierge**, **insérer un graphique radar** et **générer un graphique dans un document Word** à l’aide d’Aspose.Words. En suivant les étapes ci‑dessus, vous pouvez également **ajouter des graphiques radiaux dans des fichiers Word** à tout pipeline de génération de rapports automatisé, personnaliser la taille, le style et exporter vers d’autres formats.

**Prochaines étapes**

* Explorez d’autres types de graphiques (`ChartType.Column`, `ChartType.Pie`) pour élargir votre boîte à outils de reporting.
* Combinez plusieurs graphiques sur une même page en appelant `InsertChart` à plusieurs reprises.
* Intégrez des données provenant d’une base de données ou d’un fichier CSV pour alimenter les séries dynamiquement.
* Consultez la documentation d’Aspose.Words pour des options de mise en forme avancées telles que les libellés de données conditionnels et les modèles de graphiques.

N’hésitez pas à expérimenter avec le code, à ajuster les dimensions ou à remplacer les données d’exemple par de véritables indicateurs métier. Bon codage !


## Que devriez‑vous apprendre ensuite ?


Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques présentées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications pas à pas pour vous aider à maîtriser des fonctionnalités supplémentaires de l’API et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Insert a Bubble Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}