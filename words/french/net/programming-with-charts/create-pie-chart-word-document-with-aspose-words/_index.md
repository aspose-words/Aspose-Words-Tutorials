---
category: general
date: 2026-08-10
description: Créer un document Word avec un diagramme circulaire à l’aide d’Aspose.Words.
  Apprenez à insérer un diagramme, à personnaliser les couleurs du diagramme circulaire
  et à modifier la couleur d’une tranche du diagramme en C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- customize pie chart colors
- how to style pie
- how to insert chart
- change pie slice color
language: fr
lastmod: 2026-08-10
og_description: Créer un document Word avec un graphique circulaire à l'aide d'Aspose.Words.
  Ce guide explique comment insérer un graphique, personnaliser les couleurs du graphique
  circulaire et modifier la couleur d'une tranche du graphique dans une application
  C#.
og_image_alt: Screenshot of a Word document containing a styled pie chart generated
  by Aspose.Words
og_title: Créer un document Word avec un diagramme circulaire – Guide Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create pie chart Word document using Aspose.Words. Learn how to insert
    chart, customize pie chart colors, and change pie slice color in C#.
  headline: Create pie chart Word document with Aspose.Words
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for .NET is compatible with .NET Core, .NET 5, .NET
      6, and later. Just reference the same NuGet package.
    question: Does this work with .NET Core?
  - answer: Replace `ChartType.Pie` with `ChartType.Doughnut`. The same styling APIs
      (`Explosion`, `ForeColor`) apply.
    question: What if I need a donut chart instead of a pie?
  - answer: Open the existing file with `new Document("Existing.docx")`, create a
      `DocumentBuilder` for that document, and call `InsertChart` at the desired cursor
      position.
    question: Can I insert the chart into an existing document?
  - answer: 'Pie charts are best for a limited number of categories (typically < 10).
      For many categories, consider a bar or column chart instead. ## Full source
      code recap Below is the complete program in one block for easy copy‑paste: ```csharp
      using System; using System.Drawing; using Aspose.Words; using Aspo'
    question: How do I handle large datasets?
  type: FAQPage
tags:
- Aspose.Words
- C#
- pie chart
title: Créer un diagramme circulaire dans un document Word avec Aspose.Words
url: /fr/net/programming-with-charts/create-pie-chart-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un document Word avec un diagramme circulaire avec Aspose.Words

Si vous devez **créer un document Word avec un diagramme circulaire** de manière programmatique, ce tutoriel vous montre exactement comment faire. Nous parcourrons l'insertion d'un graphique, la **personnalisation des couleurs du diagramme circulaire**, et le **changement de couleur d'une tranche du diagramme circulaire** en utilisant Aspose.Words pour .NET.

Vous verrez un exemple complet et exécutable que vous pouvez copier dans Visual Studio, exécuter, et ouvrir immédiatement le *.docx* généré pour vérifier le diagramme circulaire stylisé. Aucune documentation externe n'est requise — tout ce dont vous avez besoin se trouve dans ce guide.

## Prérequis

Avant de commencer, assurez-vous d'avoir :

* .NET 6.0 SDK ou version ultérieure installé  
* Une licence valide d'Aspose.Words pour .NET (ou une clé d'évaluation temporaire)  
* Visual Studio 2022 (ou tout IDE C#)  

Le code utilise uniquement les espaces de noms `Aspose.Words` et `Aspose.Words.Drawing.Charts`, donc aucun package NuGet supplémentaire n'est requis au-delà de la bibliothèque Aspose.Words.

## Créer un document Word avec un diagramme circulaire – exemple complet

Le programme C# suivant crée un nouveau document Word, insère un diagramme circulaire, stylise les deux premières tranches et enregistre le fichier. Chaque étape est expliquée en détail.

```csharp
using System;
using System.Drawing;                // For Color
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Initialize a blank document and a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Insert a pie chart of size 400x300 points.
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            // Step 3: Populate the chart with sample data (optional but makes the chart visible).
            // Aspose.Words creates an empty series by default; we add a series with three values.
            chart.Series.Clear(); // Remove the default empty series.
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30); // Slice 1
            series.DataPoints.Add(45); // Slice 2
            series.DataPoints.Add(25); // Slice 3

            // Step 4: Explode the first slice to emphasize it.
            series.Points[0].Explosion = 20; // 20% explosion makes the slice pop out.

            // Step 5: **Customize pie chart colors** – set the first two slices.
            series.Points[0].Format.Fill.ForeColor = Color.Orange; // Slice 1 color
            series.Points[1].Format.Fill.ForeColor = Color.Green;  // Slice 2 color

            // Step 6: **Change pie slice color** for any additional slices if needed.
            // Example: set the third slice to a custom blue.
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            // Step 7: Save the document containing the styled pie chart.
            string outputPath = @"PieChartStyled.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Explication de chaque étape

| Étape | Ce qu'elle fait | Pourquoi c'est important |
|------|----------------|--------------------------|
| **1** | Crée un nouveau `Document` et un `DocumentBuilder`. | Le `DocumentBuilder` fournit des méthodes fluides pour insérer du contenu, comme des graphiques, dans le fichier Word. |
| **2** | Appelle `InsertChart` avec `ChartType.Pie` et une taille fixe. | `InsertChart` est la méthode **comment insérer un graphique** ; spécifier la largeur/hauteur garantit que le graphique s'adapte correctement à la page. |
| **3** | Ajoute une série de données avec trois catégories et des valeurs numériques. | Un diagramme circulaire sans données est invisible ; le remplir montre les étapes de style. |
| **4** | Définit `Explosion` sur le premier point. | Faire exploser une tranche attire l'attention sur un segment particulier—utile pour mettre en évidence des données clés. |
| **5** | Définit `ForeColor` pour les deux premiers points. | C'est le cœur de la **personnalisation des couleurs du diagramme circulaire** ; vous pouvez utiliser n'importe quel `System.Drawing.Color`. |
| **6** | Montre comment **changer la couleur d'une tranche du diagramme circulaire** pour des tranches supplémentaires. | Démontre que le style n'est pas limité aux deux premières tranches ; vous pouvez colorer chaque tranche individuellement. |
| **7** | Enregistre le document sous `PieChartStyled.docx`. | Le résultat final peut être ouvert dans Microsoft Word, Google Docs ou tout visualiseur compatible. |

#### Résultat attendu

L'ouverture de `PieChartStyled.docx` affiche une page unique avec un diagramme circulaire de 400 × 300 pt :

* Tranche 1 (orange) est éclatée vers l'extérieur.  
* Tranche 2 (vert) apparaît adjacente à la tranche éclatée.  
* Tranche 3 (bleu acier) remplit le segment restant.

Le graphique reflète les valeurs de données (30, 45, 25) et les couleurs personnalisées que vous avez définies.

## Comment styliser le diagramme circulaire – conseils supplémentaires

* **Utiliser les couleurs du thème** – au lieu de coder en dur `Color.Orange`, vous pouvez récupérer les couleurs du thème du document :  
  ```csharp
  chart.Series[0].Points[0].Format.Fill.ForeColor = doc.Theme.ColorScheme.Accent1;
  ```
* **Ajouter des étiquettes de données** – si vous souhaitez afficher les pourcentages sur le graphique :  
  ```csharp
  chart.HasDataLabel = true;
  chart.DataLabel.NumberFormat = "#%";
  ```
* **Redimensionner dynamiquement** – calculer la taille du graphique en fonction des marges de la page :  
  ```csharp
  double width = doc.PageSetup.PageWidth - doc.PageSetup.LeftMargin - doc.PageSetup.RightMargin;
  double height = width * 0.75; // 4:3 aspect ratio
  builder.InsertChart(ChartType.Pie, width, height);
  ```

Ces variantes démontrent la flexibilité de **comment styliser le diagramme circulaire** au-delà de l'exemple de base.

## Questions fréquentes

**Q : Cette fonctionnalité fonctionne-t-elle avec .NET Core ?**  
**R : Oui. Aspose.Words pour .NET est compatible avec .NET Core, .NET 5, .NET 6 et les versions ultérieures. Il suffit de référencer le même package NuGet.**

**Q : Et si j'ai besoin d'un graphique en anneau au lieu d'un diagramme circulaire ?**  
**R : Remplacez `ChartType.Pie` par `ChartType.Doughnut`. Les mêmes API de style (`Explosion`, `ForeColor`) s'appliquent.**

**Q : Puis-je insérer le graphique dans un document existant ?**  
**R : Ouvrez le fichier existant avec `new Document("Existing.docx")`, créez un `DocumentBuilder` pour ce document, et appelez `InsertChart` à la position du curseur souhaitée.**

**Q : Comment gérer de grands ensembles de données ?**  
**R : Les diagrammes circulaires conviennent mieux à un nombre limité de catégories (généralement < 10). Pour de nombreuses catégories, envisagez plutôt un graphique à barres ou à colonnes.**

## Récapitulatif du code source complet

Voici le programme complet en un seul bloc pour un copier‑coller facile :

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            chart.Series.Clear();
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30);
            series.DataPoints.Add(45);
            series.DataPoints.Add(25);

            series.Points[0].Explosion = 20;
            series.Points[0].Format.Fill.ForeColor = Color.Orange;
            series.Points[1].Format.Fill.ForeColor = Color.Green;
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            doc.Save("PieChartStyled.docx");
            Console.WriteLine("Document saved as PieChartStyled.docx");
        }
    }
}
```

L'exécution de ce code produit le document Word contenant le diagramme circulaire stylisé décrit précédemment.

## Conclusion

Vous savez maintenant comment **créer des documents Word avec un diagramme circulaire** en utilisant Aspose.Words, **personnaliser les couleurs du diagramme circulaire**, et **changer la couleur d'une tranche du diagramme circulaire** de façon programmatique. Le guide a couvert l'insertion du graphique, le remplissage des données, l'explosion d'une tranche, l'application de couleurs personnalisées, et l'enregistrement du résultat.  

À partir de là, vous pouvez explorer des sujets connexes tels que **comment insérer un graphique** d'un type autre que le diagramme circulaire, ajouter des légendes, ou générer des rapports multi‑pages avec plusieurs graphiques. Expérimentez avec différents schémas de couleurs et ensembles de données pour répondre à vos besoins de reporting.

Bon codage!

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code fonctionnels complets avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Insérer un graphique à colonnes dans Word en utilisant Aspose.Words pour .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insérer un graphique en aires dans un document Word | Aspose.Words pour .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Créer un graphique de dispersion Word en utilisant Aspose.Words pour .NET](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}