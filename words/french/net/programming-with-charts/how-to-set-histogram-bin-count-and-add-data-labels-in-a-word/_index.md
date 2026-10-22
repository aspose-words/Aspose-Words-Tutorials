---
category: general
date: 2026-10-13
description: Définissez le nombre de classes de l'histogramme dans un graphique Word
  avec C# et ajoutez des étiquettes de données pour améliorer la lisibilité. Apprenez
  comment charger un document Word en C# et mettre à jour le graphique.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set histogram bin count
- add data labels histogram
- how to update word chart
- enable chart data labels
- load word document c#
language: fr
lastmod: 2026-10-13
og_description: Définissez le nombre de classes de l'histogramme dans un graphique
  Word en utilisant C# et activez les étiquettes de données pour une visualisation
  plus claire. Suivez ce tutoriel complet pour charger un document Word en C# et mettre
  à jour le graphique.
og_image_alt: Screenshot of a Word histogram chart after setting bin count and enabling
  data labels
og_title: Définir le nombre de classes d'histogramme dans un graphique Word avec C#
  – guide étape par étape
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Set histogram bin count in a Word chart with C# and add data labels
    to improve readability. Learn how to load a Word document C# and update the chart.
  headline: How to set histogram bin count and add data labels in a Word chart using
    C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- Chart manipulation
title: Comment définir le nombre de classes d’un histogramme et ajouter des étiquettes
  de données dans un graphique Word en C#
url: /fr/net/programming-with-charts/how-to-set-histogram-bin-count-and-add-data-labels-in-a-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment définir le nombre de classes d'histogramme et ajouter des étiquettes de données dans un graphique Word avec C#

Si vous devez **définir le nombre de classes d'histogramme** dans un graphique Word, ce guide vous montre comment le faire avec C#. Vous apprendrez également comment **ajouter des étiquettes de données à l'histogramme** afin que chaque classe affiche sa valeur, rendant le graphique plus lisible. La solution fonctionne avec n'importe quel fichier `.docx` contenant un graphique d'histogramme, et elle utilise la bibliothèque Aspose.Words for .NET.

Mettre à jour un graphique est une tâche courante lorsque vous générez des rapports automatiquement. À la fin de ce tutoriel, vous serez capable de **charger un document Word C#**, modifier le nombre de classes de l'histogramme, activer les étiquettes de données, et enregistrer le résultat sans édition manuelle.

## Ce que vous apprendrez

* Comment charger un document Word en C# (`load word document c#`).
* Comment localiser le premier graphique d'histogramme dans le document (`how to update word chart`).
* Les étapes exactes pour **définir le nombre de classes d'histogramme** et **activer les étiquettes de données du graphique**.
* Conseils pour gérer plusieurs graphiques, différents types de graphiques et les pièges courants.

## Prérequis

| Exigence | Pourquoi c'est important |
|-------------|----------------|
| .NET 6.0 ou ultérieur | Fournit le runtime pour Aspose.Words. |
| Aspose.Words for .NET (v23.9 ou plus récent) | Propose l'API `Chart` utilisée pour modifier les graphiques Word. |
| Un fichier Word (`input.docx`) contenant un graphique d'histogramme | Le code fonctionne sur un histogramme existant ; vous pouvez en créer un manuellement dans Word pour les tests. |
| Visual Studio 2022 (ou tout IDE C#) | Facilite la compilation et l'exécution de l'exemple. |

Installez le package NuGet avec la commande suivante :

```bash
dotnet add package Aspose.Words
```

> **Astuce :** Si vous prévoyez de traiter de nombreux documents, activez la licence Aspose.Words pour supprimer les filigranes d'évaluation.

## Étape 1 : Charger le document Word (load word document c#)

La première opération consiste à ouvrir le fichier `.docx` contenant l'histogramme. L'utilisation de `Document.Load` garantit que toutes les parties du document, y compris les graphiques, sont disponibles en mémoire.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Path to the source document
string inputPath = @"C:\Docs\input.docx";

// Load the Word document
Document doc = new Document(inputPath);
```

> **Pourquoi cette étape est importante :** Charger le document est la base de toute modification. Si le fichier ne peut pas être ouvert, les étapes suivantes échoueront avec une `FileNotFoundException`.

## Étape 2 : Localiser le graphique d'histogramme (how to update word chart)

Word stocke les graphiques sous forme de nœuds `Shape`. Nous devons trouver la première forme et la convertir en `Chart`. Si votre document contient plusieurs graphiques, vous pouvez parcourir toutes les formes et inspecter `chart.ChartType`.

```csharp
// Retrieve the first shape in the document (depth‑first search)
Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

// Ensure the shape really is a chart
if (shape?.Chart == null)
{
    throw new InvalidOperationException("The first shape is not a chart.");
}

// Cast the shape to a Chart object
Chart histogramChart = shape.Chart;
```

> **Cas particulier :** Si le document ne contient pas de graphique, `GetChild` renvoie `null`. La vérification ci‑dessus empêche une `NullReferenceException`.

## Étape 3 : Définir le nombre de classes d'histogramme (set histogram bin count)

La granularité visuelle d'un histogramme est contrôlée par la propriété `BinCount`. L'augmenter crée plus de barres, ce qui peut révéler une distribution de données plus fine.

```csharp
// Verify that the chart is a histogram
if (histogramChart.ChartType != ChartType.Histogram)
{
    throw new InvalidOperationException("The selected chart is not a histogram.");
}

// Set the desired number of bins (e.g., 15)
histogramChart.HistogramChart.BinCount = 15;
```

> **Pourquoi c'est nécessaire :** Ajuster le nombre de classes vous permet d'adapter le graphique à votre public. Un petit nombre de classes simplifie la vue, tandis qu'un nombre plus élevé fournit plus de détails.

## Étape 4 : Activer les étiquettes de données du graphique (add data labels histogram / enable chart data labels)

Les étiquettes de données rendent la valeur de chaque classe visible directement sur le graphique. Cela est particulièrement utile lorsque l'histogramme est imprimé ou exporté en PDF.

```csharp
// Turn on data labels for each bin
histogramChart.HistogramChart.ShowLabels = true;

// Optional: customize label format (e.g., show percentage)
histogramChart.HistogramChart.Labels.NumberFormat = "#,##0";
```

> **Conseil pratique :** Si vous préférez les pourcentages plutôt que les comptes bruts, définissez `NumberFormat = "0%"` et activez `ShowPercentage = true`.

## Étape 5 : Enregistrer le document modifié

Après les modifications, écrivez le document sur le disque. Vous pouvez écraser le fichier original ou en créer un nouveau.

```csharp
// Path to the output document
string outputPath = @"C:\Docs\output.docx";

// Save the updated document
doc.Save(outputPath);
```

L'ouverture de `output.docx` dans Microsoft Word affiche maintenant un histogramme avec 15 classes et des étiquettes de données visibles.

## Étape 6 : Vérifier le résultat (expected output)

Pour vous assurer que l'opération a réussi sans inspection visuelle, vous pouvez lire les propriétés de façon programmatique :

```csharp
// Reload the saved file for verification
Document verifyDoc = new Document(outputPath);
Chart verifyChart = ((Shape)verifyDoc.GetChild(NodeType.Shape, 0, true)).Chart;

Console.WriteLine($"BinCount: {verifyChart.HistogramChart.BinCount}");
Console.WriteLine($"ShowLabels: {verifyChart.HistogramChart.ShowLabels}");
```

La console devrait afficher :

```
BinCount: 15
ShowLabels: True
```

Si les valeurs correspondent, l'histogramme a été correctement mis à jour.

## Exemple complet exécutable

En réunissant tous les éléments, voici un programme autonome que vous pouvez copier, coller et exécuter :

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // ---------- Step 1: Load the Word document ----------
        string inputPath = @"C:\Docs\input.docx";
        Document doc = new Document(inputPath);

        // ---------- Step 2: Locate the histogram chart ----------
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape?.Chart == null)
            throw new InvalidOperationException("No chart found in the document.");

        Chart histogramChart = shape.Chart;

        // ---------- Step 3: Set histogram bin count ----------
        if (histogramChart.ChartType != ChartType.Histogram)
            throw new InvalidOperationException("The chart is not a histogram.");

        histogramChart.HistogramChart.BinCount = 15;

        // ---------- Step 4: Enable chart data labels ----------
        histogramChart.HistogramChart.ShowLabels = true;
        histogramChart.HistogramChart.Labels.NumberFormat = "#,##0";

        // ---------- Step 5: Save the modified document ----------
        string outputPath = @"C:\Docs\output.docx";
        doc.Save(outputPath);

        // ---------- Step 6: Verify the changes ----------
        Document verifyDoc = new Document(outputPath);
        Chart verifyChart = ((Shape)verifyDoc.GetChild(NodeType.Shape, 0, true)).Chart;

        Console.WriteLine($"BinCount: {verifyChart.HistogramChart.BinCount}");
        Console.WriteLine($"ShowLabels: {verifyChart.HistogramChart.ShowLabels}");
    }
}
```

Exécutez le programme, puis ouvrez `output.docx` pour voir l'histogramme mis à jour.

## Questions fréquentes et cas particuliers

| Question | Réponse |
|----------|--------|
| **Et si le document contient plus d'un graphique ?** | Utilisez `doc.GetChildNodes(NodeType.Shape, true)` pour récupérer une collection, puis parcourez‑la et vérifiez chaque `Chart.ChartType`. |
| **Puis‑je changer la largeur de classe au lieu du nombre ?** | Oui. Utilisez `histogramChart.HistogramChart.BinWidth` pour spécifier une largeur fixe ; le réglage de `BinCount` sera ignoré. |
| **L'API est‑elle compatible avec .NET Core ?** | Aspose.Words for .NET prend en charge .NET Core, .NET 5+ et .NET Framework. Le même code fonctionne sur tous les runtimes supportés. |
| **Comment masquer la légende après avoir ajouté les étiquettes ?** | Définissez `histogramChart.Legend.Visible = false;`. Cela garde le graphique épuré lorsque les étiquettes transmettent déjà les données. |

## Conclusion

Vous savez maintenant comment **définir le nombre de classes d'histogramme** et **ajouter des étiquettes de données** à un graphique Word avec C#. En chargeant le document, en localisant l'histogramme, en ajustant `BinCount`, en activant `ShowLabels`, et en enregistrant le fichier, vous pouvez automatiser les mises à jour de graphiques dans n'importe quel pipeline de reporting.  

À partir d'ici, vous pourriez explorer :

* **how to update word chart** couleurs et styles,
* **enable chart data labels** pour d'autres types de graphiques (camembert, barre, ligne),
* Générer des graphiques à partir de données brutes avec Aspose.Words ou Aspose.Cells,
* Intégrer le document mis à jour dans un PDF avec Aspose.PDF.

Expérimentez différents nombres de classes et formats d'étiquettes pour trouver l'équilibre visuel qui sert le mieux votre public. Bon codage !  

![Histogramme Word après

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l'API et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Update Chart Series Data in a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)
- [Set Uniform Data Labels in a Column Chart Using Aspose.Words for .NET](/words/english/net/programming-with-charts/uniform-data-labels/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}