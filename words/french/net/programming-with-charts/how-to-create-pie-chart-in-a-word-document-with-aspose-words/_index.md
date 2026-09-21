---
category: general
date: 2026-09-21
description: Apprenez à créer un graphique circulaire et à l’insérer dans Word avec
  Aspose.Words, à ajouter des étiquettes de données au graphique circulaire et à afficher
  les pourcentages sur le graphique circulaire en quelques étapes seulement.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- insert chart into word
- add data labels to pie chart
- show percentages on pie chart
- how to display percentages in chart
language: fr
lastmod: 2026-09-21
og_description: Créer un diagramme circulaire dans Word avec Aspose.Words, insérer
  le diagramme dans Word, ajouter des étiquettes de données au diagramme circulaire
  et afficher les pourcentages sur le diagramme circulaire — le tout avec des exemples
  de code clairs.
og_image_alt: Screenshot of a Word document containing a pie chart with percentage
  data labels displayed outside each slice
og_title: Créer un diagramme circulaire dans Word avec Aspose.Words – guide étape
  par étape
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
- description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  name: How to create pie chart in a Word document with Aspose.Words
  steps:
  - name: Expected output
    text: 'When you open the generated document, you should see:'
  - name: Adding a title to the chart
    text: '```csharp chart.Title.Text = "Sales Distribution Q1"; chart.Title.Show
      = true; ```'
  - name: Changing slice colors
    text: '```csharp series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
      series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen; ```'
  - name: Handling an empty series
    text: 'If your data source might be empty, guard against `IndexOutOfRangeException`:'
  - name: Exporting to PDF instead of Word
    text: '```csharp doc.Save("PieChart.pdf", SaveFormat.Pdf); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- charting
- Word automation
title: Comment créer un diagramme circulaire dans un document Word avec Aspose.Words
url: /fr/net/programming-with-charts/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer un diagramme circulaire dans un document Word avec Aspose.Words

Si vous devez **créer un diagramme circulaire** de manière programmatique, Aspose.Words le rend simple. Dans ce tutoriel, vous verrez comment **insérer un graphique dans Word**, configurer les séries, **ajouter des étiquettes de données au diagramme circulaire**, et enfin **afficher les pourcentages sur le diagramme circulaire** afin que le visuel transmette les valeurs exactes. À la fin, vous disposerez d’un exemple complet et exécutable que vous pourrez intégrer à n’importe quel projet .NET.

Ce guide couvre tout ce que vous devez savoir : les packages NuGet requis, le code source complet en C#, les explications sur l’importance de chaque appel d’API, et des astuces pour personnaliser le graphique. Aucune documentation externe n’est nécessaire — il suffit de copier, exécuter et adapter.

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

* Le SDK .NET 6.0 ou une version ultérieure installé.  
* Visual Studio 2022 (ou tout IDE supportant .NET).  
* Une licence Aspose.Words for .NET (l’essai gratuit suffit pour les tests).  
* Une connaissance de base du C# et de la structure des documents Word.

Si vous avez déjà tout cela, vous pouvez passer directement au code.

## Étape 1 : Configurer le projet et importer Aspose.Words

Créez un nouveau projet console et ajoutez le package NuGet Aspose.Words :

```bash
dotnet new console -n PieChartDemo
cd PieChartDemo
dotnet add package Aspose.Words
```

Le package inclut l’espace de noms `Aspose.Words.Drawing.Charts`, qui contient les classes `Chart` et `ChartSeries` que nous utiliserons.

> **Astuce :** Placez votre fichier de licence (`Aspose.Words.lic`) à la racine du projet et chargez‑le au démarrage pour éviter les filigranes d’évaluation.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: Apply your license
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");
```

## Étape 2 : Créer un document vierge et un DocumentBuilder

Un `Document` représente le fichier Word, tandis que `DocumentBuilder` fournit une API fluide pour insérer du contenu.

```csharp
        // Create a new blank document
        Document doc = new Document();

        // DocumentBuilder will let us add a chart
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Pourquoi c’est important :** Le `DocumentBuilder` maintient le point d’insertion actuel, garantissant que le graphique apparaît exactement à l’endroit souhaité dans le flux du document.

## Étape 3 : Insérer un diagramme circulaire dans le document Word

Nous **insérons maintenant le graphique dans Word**. La méthode `InsertChart` prend le type de graphique, la largeur et la hauteur (en points).

```csharp
        // Insert a pie chart of size 400x300 points
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

À ce stade, le graphique contient une série de données par défaut avec des valeurs factices (25, 25, 25, 25). Vous pourrez les remplacer plus tard si besoin.

## Étape 4 : Accéder à la première série et personnaliser les étiquettes de données

Un diagramme circulaire possède généralement une seule série. Pour **ajouter des étiquettes de données au diagramme circulaire**, nous la récupérons et activons l’affichage du pourcentage.

```csharp
        // Access the first (and only) series of the chart
        ChartSeries series = chart.Series[0];

        // Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // Position the labels outside the slices for readability
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

**Pourquoi nous définissons `ShowPercentage` :** Ce drapeau indique à Aspose.Words de calculer la contribution de chaque part et de l’afficher sous forme de pourcentage. La propriété `Position` garantit que l’étiquette ne chevauche pas la part, ce qui améliore la lisibilité—surtout lorsque les parts sont petites.

## Étape 5 : (Facultatif) Remplacer les données factices

Si vous souhaitez des valeurs spécifiques, remplacez les points par défaut :

```csharp
        // Clear existing points
        series.Points.Clear();

        // Add custom data points
        series.Points.Add(new ChartPoint(40)); // 40%
        series.Points.Add(new ChartPoint(30)); // 30%
        series.Points.Add(new ChartPoint(20)); // 20%
        series.Points.Add(new ChartPoint(10)); // 10%
```

Les pourcentages affichés s’ajusteront automatiquement pour refléter les nouvelles valeurs.

## Étape 6 : Enregistrer le document

Enfin, écrivez le document sur le disque. L’extension détermine le format ; `.docx` crée un fichier Word moderne.

```csharp
        // Save the document containing the pie chart
        doc.Save("PieChart.docx");
    }
}
```

L’exécution du programme génère un fichier nommé **PieChart.docx** dans le répertoire de sortie. L’ouvrir avec Microsoft Word montre un diagramme circulaire avec chaque part étiquetée par son pourcentage, positionné à l’extérieur des parts.

### Résultat attendu

Lorsque vous ouvrez le document généré, vous devez voir :

* Un seul diagramme circulaire, de taille 400 × 300 pt.  
* Quatre parts (ou autant que de points que vous avez ajoutés).  
* Des étiquettes de pourcentage telles que « 40 % », « 30 % », etc., affichées à l’extérieur de chaque part.

Si les étiquettes apparaissent à l’intérieur des parts, vérifiez que `ChartDataLabelPosition.OutsideEnd` a bien été défini.

## Étape 7 : Variantes courantes et cas particuliers

### Ajouter un titre au graphique

```csharp
chart.Title.Text = "Sales Distribution Q1";
chart.Title.Show = true;
```

### Modifier les couleurs des parts

```csharp
series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen;
```

### Gérer une série vide

Si votre source de données peut être vide, protégez‑vous contre `IndexOutOfRangeException` :

```csharp
if (series.Points.Count == 0)
{
    // Provide a fallback to avoid runtime errors
    series.Points.Add(new ChartPoint(100));
}
```

### Exporter en PDF au lieu de Word

```csharp
doc.Save("PieChart.pdf", SaveFormat.Pdf);
```

La même logique de rendu du graphique s’applique ; Aspose.Words convertit automatiquement la mise en page Word en PDF.

## Listing complet du code source

Voici le programme complet, prêt à être exécuté. Copiez‑le dans `Program.cs` et lancez `dotnet run`.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: apply your license to remove evaluation watermarks
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Create a DocumentBuilder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a pie chart (400x300 points)
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 4. Access the first series
        ChartSeries series = chart.Series[0];

        // 5. Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // 6. Position data labels outside the slices
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Optional: replace placeholder data with custom values
        series.Points.Clear();
        series.Points.Add(new ChartPoint(40));
        series.Points.Add(new ChartPoint(30));
        series.Points.Add(new ChartPoint(20));
        series.Points.Add(new ChartPoint(10));

        // Optional: add a title
        chart.Title.Text = "Quarterly Sales Breakdown";
        chart.Title.Show = true;

        // 7. Save the document
        doc.Save("PieChart.docx"); // Change extension to .pdf for PDF output
    }
}
```

## Conclusion

Vous savez maintenant comment **créer un diagramme circulaire** dans un fichier Word avec Aspose.Words, **insérer un graphique dans Word**, **ajouter des étiquettes de données au diagramme circulaire**, et **afficher les pourcentages sur le diagramme circulaire**. L’exemple montre le flux complet—de la configuration du projet au document final—afin que vous puissiez l’adapter à des tableaux de bord, des rapports ou la génération automatisée de factures.

Ensuite, explorez des sujets connexes tels que **comment afficher les pourcentages dans les légendes de graphique**, la personnalisation des couleurs du graphique, ou la conversion du document Word en PDF pour la distribution. Expérimentez avec d’autres types de graphiques (Bar, Line) en utilisant la même méthode `InsertChart` pour élargir vos capacités d’automatisation.

Bon graphique !


## Que devez‑vous apprendre ensuite ?


Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets et fonctionnels avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}