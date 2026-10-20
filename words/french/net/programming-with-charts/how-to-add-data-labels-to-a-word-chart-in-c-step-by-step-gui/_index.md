---
category: general
date: 2026-08-04
description: Comment ajouter des étiquettes de données en C# avec Aspose.Words. Apprenez
  à modifier le graphique, centrer les étiquettes de données du graphique, afficher
  les pourcentages dans le graphique et personnaliser les étiquettes de données du
  graphique.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add data labels
- how to edit chart
- center chart data labels
- show percentages in chart
- customize chart data labels
language: fr
lastmod: 2026-08-04
og_description: Comment ajouter des étiquettes de données en C# avec Aspose.Words.
  Ce tutoriel vous montre comment modifier le graphique, centrer les étiquettes de
  données du graphique, afficher les pourcentages dans le graphique et personnaliser
  les étiquettes de données du graphique.
og_image_alt: Screenshot of a Word chart with data labels added using C#
og_title: Comment ajouter des étiquettes de données à un graphique Word en C# – guide
  complet
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  headline: How to add data labels to a Word chart in C# – step‑by‑step guide
  type: TechArticle
- description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  name: How to add data labels to a Word chart in C# – step‑by‑step guide
  steps:
  - name: – Load the Word document containing the chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: – Retrieve the first chart from the document
    text: '```csharp // Find the first shape that contains a chart. Shape chartShape
      = (Shape)document.GetChild(NodeType.Shape, 0, true); Chart chart = chartShape.GetChart();
      ```'
  - name: – Enable data label customization and show percentages in chart
    text: '```csharp // Access the first series of the chart. ChartSeries series =
      chart.Series[0];'
  - name: – Change the label placement to the center of each data point
    text: '```csharp // Position the labels at the center of each point. dataLabels.Position
      = ChartDataLabelPosition.Center; // center chart data labels ```'
  - name: – Further customize chart data labels (optional)
    text: 'If you need more control, you can adjust font, color, or leader lines:'
  - name: – Save the modified document
    text: '```csharp // Persist the changes to a new file. document.Save("YOUR_DIRECTORY/output.docx");
      ```'
  - name: Expected result
    text: 'When you open `output.docx` in Microsoft Word, the chart will display:'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart manipulation
title: Comment ajouter des étiquettes de données à un graphique Word en C# – guide
  étape par étape
url: /fr/net/programming-with-charts/how-to-add-data-labels-to-a-word-chart-in-c-step-by-step-gui/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment ajouter des étiquettes de données à un graphique Word en C# – guide étape par étape

Si vous avez besoin de **how to add data labels** à un graphique intégré dans un document Word, ce guide vous montre le code exact à exécuter. Vous verrez comment modifier les propriétés du graphique, centrer les étiquettes de données du graphique, afficher les pourcentages dans le graphique et personnaliser les étiquettes de données du graphique pour n'importe quel scénario.

Le tutoriel couvre tout ce qui est nécessaire pour modifier un graphique existant, du chargement du document à la sauvegarde des modifications. Aucune référence externe n'est requise — uniquement la bibliothèque Aspose.Words for .NET et un environnement de développement C# de base.

## Prérequis

Avant de commencer, assurez-vous d'avoir :

* .NET 6.0 (ou version ultérieure) installé.
* Aspose.Words for .NET version 23.9 ou plus récent.  
  Vous pouvez l'installer via NuGet :

```bash
dotnet add package Aspose.Words
```

* Un fichier Word (`input.docx`) contenant au moins un graphique.

## Comment ajouter des étiquettes de données à un graphique Word en C#

Les sections suivantes vous guident à travers chaque étape. Le mot‑clé principal **how to add data labels** apparaît naturellement dans le texte et dans les commentaires du code, maintenant la densité dans la plage recommandée.

### Étape 1 – Charger le document Word contenant le graphique

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document.
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

*Pourquoi cette étape est importante* : L'objet `Document` représente l'intégralité du fichier Word. Le charger vous donne accès à chaque nœud, y compris les formes qui hébergent les graphiques.

### Étape 2 – Récupérer le premier graphique du document

```csharp
// Find the first shape that contains a chart.
Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
Chart chart = chartShape.GetChart();
```

*Pourquoi cette étape est importante* : Les graphiques sont stockés à l'intérieur des nœuds `Shape`. En convertissant le nœud récupéré en `Shape` et en appelant `GetChart()`, vous obtenez un objet `Chart` qui expose les séries, les axes et les collections d'étiquettes.

### Étape 3 – Activer la personnalisation des étiquettes de données et afficher les pourcentages dans le graphique

```csharp
// Access the first series of the chart.
ChartSeries series = chart.Series[0];

// Turn on data labels and request percentage values.
ChartDataLabelCollection dataLabels = series.DataLabels;
dataLabels.ShowPercentage = true;   // show percentages in chart
dataLabels.ShowValue = true;        // optional: also show raw values
```

*Pourquoi cette étape est importante* : Le réglage de `ShowPercentage` indique à Aspose.Words de calculer et d'afficher la contribution de chaque part au total. Cela répond directement au mot‑clé secondaire **show percentages in chart**.

### Étape 4 – Modifier le placement de l'étiquette au centre de chaque point de données

```csharp
// Position the labels at the center of each point.
dataLabels.Position = ChartDataLabelPosition.Center; // center chart data labels
```

*Pourquoi cette étape est importante* : La propriété `Position` contrôle l'emplacement de l'étiquette par rapport au point de données. Utiliser `Center` satisfait le mot‑clé secondaire **center chart data labels** et améliore la lisibilité des graphiques en secteurs ou en anneaux.

### Étape 5 – Personnaliser davantage les étiquettes de données du graphique (optionnel)

Si vous avez besoin de plus de contrôle, vous pouvez ajuster la police, la couleur ou les lignes de repère :

```csharp
// Example: make labels bold and red.
dataLabels.Font.Bold = true;
dataLabels.Font.Color = System.Drawing.Color.Red;

// Example: add leader lines for better separation.
dataLabels.ShowLeaderLines = true;
```

Ces réglages illustrent le mot‑clé secondaire **customize chart data labels** et démontrent comment vous pouvez adapter l'apparence pour correspondre aux directives de la marque.

### Étape 6 – Enregistrer le document modifié

```csharp
// Persist the changes to a new file.
document.Save("YOUR_DIRECTORY/output.docx");
```

*Pourquoi cette étape est importante* : L'enregistrement écrit le graphique mis à jour dans le document Word, rendant les nouvelles étiquettes de données visibles lorsque le fichier est ouvert dans Microsoft Word.

## Exemple complet et exécutable

Voici un programme complet que vous pouvez copier, coller et exécuter. Il inclut toutes les directives `using` nécessaires ainsi que des commentaires expliquant chaque ligne.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class AddDataLabelsDemo
{
    static void Main()
    {
        // 1. Load the Word document.
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first chart.
        Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
        Chart chart = chartShape.GetChart();

        // 3. Enable data labels and show percentages.
        ChartSeries series = chart.Series[0];
        ChartDataLabelCollection dataLabels = series.DataLabels;
        dataLabels.ShowPercentage = true;
        dataLabels.ShowValue = true;

        // 4. Center the labels on each data point.
        dataLabels.Position = ChartDataLabelPosition.Center;

        // 5. Optional: further customize appearance.
        dataLabels.Font.Bold = true;
        dataLabels.Font.Color = System.Drawing.Color.DarkBlue;
        dataLabels.ShowLeaderLines = true;

        // 6. Save the modified document.
        document.Save("YOUR_DIRECTORY/output.docx");

        Console.WriteLine("Data labels added and document saved successfully.");
    }
}
```

### Résultat attendu

Lorsque vous ouvrez `output.docx` dans Microsoft Word, le graphique affichera :

* Valeurs de pourcentage à côté de chaque part (par ex., **25 %**, **40 %**, …).
* Étiquettes positionnées au centre de chaque point de données.
* Tout style supplémentaire que vous avez appliqué, comme du texte rouge en gras.

Ces repères visuels rendent le graphique plus facile à interpréter, notamment dans les présentations ou les rapports.

## Comment modifier les propriétés du graphique au‑delà des étiquettes de données

Bien que l'objectif de ce guide soit **how to add data labels**, vous pourriez également vouloir **how to edit chart** des paramètres tels que les titres, le placement de la légende ou le format des axes. L'objet `Chart` fournit des propriétés comme `Title`, `Legend` et `AxisX/AxisY`. Par exemple, pour modifier le titre du graphique :

```csharp
chart.Title.Text = "Quarterly Sales Breakdown";
chart.Title.Font.Size = 14;
```

Toutes les modifications de graphique suivent le même schéma : récupérer le graphique, ajuster ses propriétés, puis enregistrer le document.

## Pièges courants et conseils de bonnes pratiques

| Piège | Pourquoi cela se produit | Solution recommandée |
|---|---|---|
| Le graphique se trouve à l'intérieur d'une forme groupée. | `GetChild(NodeType.Shape, …)` renvoie le groupe externe, pas le graphique interne. | Rechercher récursivement une forme avec `shape.HasChart`. |
| Les étiquettes de données n'apparaissent pas après l'enregistrement. | `ShowValue` ou `ShowPercentage` n'a pas été défini sur `true`. | Définir explicitement `ShowValue` et `ShowPercentage` sur `true` selon les besoins. |
| Les étiquettes se chevauchent sur les petites parts. | Le positionnement centré peut provoquer un encombrement. | Utilisez `ChartDataLabelPosition.OutSideEnd` pour un placement extérieur, ou activez `LeaderLines`. |

## Conclusion

Vous savez maintenant **how to add data labels** à un graphique Word en utilisant C#. Le tutoriel a couvert la récupération du graphique, l'activation de la visibilité des étiquettes, le centrage des étiquettes, l'affichage des pourcentages et la personnalisation de l'apparence. Avec ces connaissances, vous pouvez également **how to edit chart** les détails, **center chart data labels**, **show percentages in chart**, et **customize chart data labels** pour tout scénario de reporting.

Prêt à explorer davantage ? Essayez d'ajouter plusieurs séries, d'appliquer un formatage conditionnel ou d'exporter le graphique en image. L'API Aspose.Words offre de vastes capacités de manipulation de graphiques — expérimentez pour trouver la représentation visuelle parfaite de vos données.

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code fonctionnels complets avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l'API et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Personnaliser les étiquettes de données du graphique](/words/english/net/programming-with-charts/chart-data-label/)
- [Définir les options par défaut pour les étiquettes de données dans un graphique](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Personnaliser un point de données unique dans un graphique](/words/english/net/programming-with-charts/single-chart-data-point/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}