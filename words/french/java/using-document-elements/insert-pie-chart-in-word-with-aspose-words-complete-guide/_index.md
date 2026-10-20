---
category: general
date: 2026-07-26
description: Insérez un diagramme circulaire dans un document Word à l'aide d'Aspose.Words.
  Apprenez à ajouter un graphique, à éclater une tranche et à afficher les pourcentages
  en quelques étapes seulement.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to add chart
- how to explode slice
- add chart to word
- how to show percentages
language: fr
lastmod: 2026-07-26
og_description: Insérez un diagramme circulaire dans un fichier Word avec Aspose.Words.
  Suivez ce guide pour apprendre à ajouter un diagramme, à éclater une part et à afficher
  rapidement les pourcentages.
og_image_alt: Screenshot illustrating insert pie chart in a Word document
og_title: Insérer un diagramme circulaire dans Word – Tutoriel Aspose.Words étape
  par étape
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert pie chart into a Word document using Aspose.Words. Learn how
    to add chart, explode slice, and show percentages in just a few steps.
  headline: Insert Pie Chart in Word with Aspose.Words – Complete Guide
  type: TechArticle
- questions:
  - answer: Just add additional `ChartSeries` objects to `chart.Series`. Each series
      can have its own data set, colors, and explode settings.
    question: What if I need more than one series?
  - answer: Yes. Each `ChartPoint` has a `Format.Fill.ForeColor` property you can
      set to any `System.Drawing.Color`.
    question: Can I change the chart’s colors?
  - answer: The `ChartType` enum includes bar, line, doughnut, and many more. Swap
      `ChartType.Pie` for whichever visual you need.
    question: What about different chart types?
  - answer: Absolutely. Word treats the chart as a native Office chart, so users can
      double‑click it to open the built‑in chart editor.
    question: Is the chart editable in Word after insertion?
  type: FAQPage
tags:
- Aspose.Words
- Chart Automation
- .NET Development
title: Insérer un diagramme circulaire dans Word avec Aspose.Words – Guide complet
url: /fr/java/using-document-elements/insert-pie-chart-in-word-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insérer un diagramme circulaire dans Word avec Aspose.Words – Guide complet

Vous avez déjà eu besoin de **insérer un diagramme circulaire** dans un rapport Word sans savoir par où commencer ? Vous n'êtes pas seul. Dans de nombreuses applications métier, l'impact visuel d'un diagramme circulaire rend les données immédiatement digestes, et Aspose.Words le rend possible en quelques lignes de code seulement.

Dans ce tutoriel, nous parcourrons les étapes exactes pour **ajouter un diagramme à Word**, éclater une tranche pour la mettre en avant, et afficher les pourcentages sur les libellés de données. À la fin, vous disposerez d’un exemple prêt à l’emploi que vous pourrez intégrer à n’importe quel projet .NET.

---

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

- .NET 6.0 ou version ultérieure (le code fonctionne aussi bien avec .NET Core qu’avec .NET Framework)
- Le package NuGet Aspose.Words for .NET installé  
  ```bash
  dotnet add package Aspose.Words
  ```
- Une compréhension de base de la syntaxe C# — rien de compliqué requis
- Un IDE de votre choix (Visual Studio, Rider ou VS Code)

C’est tout. Passons à la pratique.

---

## Insérer un diagramme circulaire dans un document Word

La première chose dont nous avons besoin est un nouvel objet `Document` et un `DocumentBuilder`. Pensez au builder comme à un stylo qui écrit directement sur la toile Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
using Aspose.Words.Charts;

// Step 1: Create a new document and a builder to work with it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Pourquoi c’est important :** Le `Document` représente l’ensemble du fichier .docx, tandis que le `DocumentBuilder` nous offre une API pratique pour insérer des éléments tels que des diagrammes, des tableaux et du texte. C’est la base de chaque opération **how to add chart**.

---

## How to Add Chart to Word

Maintenant que nous disposons d’un builder, nous pouvons réellement **insérer un diagramme circulaire**. La méthode `insertChart` prend le type de diagramme et les dimensions souhaitées en points (1 point = 1/72 pouce).

```csharp
// Step 2: Insert a pie chart of size 400x300 points
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

> **Astuce :** Si vous avez besoin d’une taille différente, modifiez simplement les valeurs de largeur et de hauteur. Le diagramme sera automatiquement redimensionné pour s’adapter aux marges de la page.

---

## How to Explode Slice for Emphasis

Un ajustement visuel courant consiste à « exploser » une tranche afin qu’elle sorte du cercle. Cela attire l’œil du lecteur vers le segment le plus important.

```csharp
// Step 3: Access the first series (the data set)
ChartSeries series = chart.Series[0];

// Step 4: Explode the first slice to emphasize it
series.Points[0].Exploded = true;
```

> **Pourquoi exploser une tranche ?** Lorsque vous souhaitez mettre en avant une catégorie particulière — par exemple, « revenus T1 » dans un rapport financier — exploser la tranche la rend immédiatement visible sans texte supplémentaire.

---

## How to Show Percentages on Data Labels

La plupart des diagrammes circulaires sont plus lisibles lorsque chaque tranche affiche son pourcentage. Aspose.Words nous permet d’activer cela avec une seule propriété.

```csharp
// Step 5: Show percentages on the data labels of the first series
series.DataLabelFormat.ShowPercentage = true;
```

> **Note rapide :** Le drapeau `ShowPercentage` s’applique à tous les points de la série, vous n’avez donc pas besoin de le définir tranche par tranche.

---

## Save the Document Containing the Chart

Enfin, nous enregistrons le document sur le disque. Choisissez le dossier qui vous convient ; assurez‑vous simplement que le chemin existe.

```csharp
// Step 6: Save the document containing the chart
doc.Save(@"C:\Temp\PieChart.docx");
```

Lorsque vous ouvrirez `PieChart.docx` dans Microsoft Word, vous verrez un diagramme circulaire parfaitement rendu avec la première tranche éclatée et les pourcentages affichés — exactement ce à quoi on s’attend d’un rapport professionnel soigné.

---

## Full Working Example

Voici le programme complet, prêt à être copié‑collé. Exécutez‑le en tant qu’application console et vérifiez le fichier de sortie.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a new document and a builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a pie chart (400x300 points)
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data
            ChartSeries series = chart.Series[0];
            series.Name = "Sales Q1";
            series.Add(30); // Product A
            series.Add(45); // Product B
            series.Add(25); // Product C

            // Explode the first slice (Product A)
            series.Points[0].Exploded = true;

            // Show percentages on data labels
            series.DataLabelFormat.ShowPercentage = true;

            // Save the document
            string outputPath = @"C:\Temp\PieChart.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Résultat attendu :** Ouvrez le `PieChart.docx` généré. Vous verrez un diagramme circulaire à trois tranches intitulé « Sales Q1 », avec la première tranche retirée et chaque tranche libellée « 30 % », « 45 % » et « 25 % ». Le rendu correspond aux données que nous avons fournies.

---

## Common Questions & Edge Cases

- **Et si j’ai besoin de plus d’une série ?**  
  Ajoutez simplement des objets `ChartSeries` supplémentaires à `chart.Series`. Chaque série peut disposer de son propre jeu de données, de ses couleurs et de ses réglages d’explosion.

- **Puis‑je modifier les couleurs du diagramme ?**  
  Oui. Chaque `ChartPoint` possède une propriété `Format.Fill.ForeColor` que vous pouvez définir sur n’importe quelle `System.Drawing.Color`.

- **Qu’en est‑il des autres types de diagrammes ?**  
  L’énumération `ChartType` comprend bar, line, doughnut et bien d’autres. Remplacez `ChartType.Pie` par le type visuel dont vous avez besoin.

- **Le diagramme est‑il modifiable dans Word après l’insertion ?**  
  Absolument. Word traite le diagramme comme un diagramme Office natif, les utilisateurs peuvent donc double‑cliquer dessus pour ouvrir l’éditeur de diagrammes intégré.

---

## Conclusion

Vous savez maintenant exactement comment **insérer un diagramme circulaire** dans un document Word avec Aspose.Words, **comment ajouter un diagramme à Word**, **comment exploser une tranche**, et **comment afficher les pourcentages** sur les libellés de données. L’exemple complet ci‑dessus est prêt à être exécuté, et vous pouvez l’étendre avec des données personnalisées, du style ou des séries supplémentaires.

Prêt pour l’étape suivante ? Essayez de remplacer le diagramme circulaire par un diagramme en anneau, ou générez un lot de rapports avec différents jeux de données automatiquement. Si vous êtes curieux d’autres visualisations, consultez nos guides sur **how to add chart** pour les diagrammes à barres et en lignes, ou explorez la référence API **add chart to word** pour des personnalisations plus poussées.

Bon codage, et que vos documents soient toujours aussi clairs qu’une part de tarte parfaitement découpée !


## What Should You Learn Next?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}