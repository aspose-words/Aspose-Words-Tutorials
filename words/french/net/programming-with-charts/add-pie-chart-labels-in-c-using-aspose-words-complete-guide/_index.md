---
category: general
date: 2026-07-20
description: Ajoutez des libellés de diagramme circulaire avec Aspose.Words pour .NET.
  Découvrez comment modifier les libellés du diagramme circulaire, afficher les libellés
  de pourcentage et mettre à jour rapidement les libellés des séries du diagramme.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart labels
- change pie chart labels
- update chart series labels
- show percentage labels
- display pie chart percentages
language: fr
lastmod: 2026-07-20
og_description: Ajoutez des étiquettes de diagramme circulaire en C# avec Aspose.Words.
  Maîtrisez la modification des étiquettes de diagramme circulaire, l’affichage des
  pourcentages et la mise à jour des étiquettes de séries de diagramme en quelques
  étapes seulement.
og_image_alt: Word document screenshot displaying a pie chart with custom percentage
  labels
og_title: Ajouter des étiquettes de diagramme circulaire en C# – Tutoriel complet
  Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Add pie chart labels with Aspose.Words for .NET. Learn how to change
    pie chart labels, show percentage labels, and update chart series labels quickly.
  headline: Add pie chart labels in C# using Aspose.Words – Complete Guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: Ajouter des étiquettes de diagramme circulaire en C# avec Aspose.Words – Guide
  complet
url: /fr/net/programming-with-charts/add-pie-chart-labels-in-c-using-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ajouter des étiquettes de diagramme circulaire en C# avec Aspose.Words – Guide complet

Vous devez **ajouter des étiquettes de diagramme circulaire** à un document Word en C# ? Avec Aspose.Words, vous pouvez facilement **modifier les étiquettes de diagramme circulaire** et **afficher les pourcentages du diagramme circulaire** directement dans le fichier—sans aucun ajustement manuel dans Word.

Dans ce tutoriel, nous parcourrons les étapes exactes pour **afficher les étiquettes de pourcentage**, les repositionner, et même **mettre à jour les étiquettes de séries de graphique** pour des données dynamiques. À la fin, vous disposerez d’un extrait réutilisable que vous pourrez intégrer à n’importe quel projet .NET.

> **Aperçu rapide :** Après avoir suivi le guide, l’ouverture du fichier `.docx` enregistré révélera un diagramme circulaire où chaque part est étiquetée avec son pourcentage, positionnée à l’extérieur de la part pour une lisibilité maximale.

---

## Ce dont vous avez besoin

- **Aspose.Words for .NET** (la dernière version à partir de 2026). Vous pouvez l’obtenir via NuGet : `Install-Package Aspose.Words`.
- Un **document Word** contenant déjà un diagramme circulaire ou en anneau (nous l’appellerons `Chart.docx`).
- Une connaissance de base du **C#** et de Visual Studio (ou de votre IDE préféré).

C’est tout—pas de bibliothèques supplémentaires, pas d’interop COM, juste du code géré pur.

---

## Ajouter des étiquettes de diagramme circulaire – Implémentation complète

Voici un programme console C# **complet et exécutable** qui charge un document, modifie le premier diagramme circulaire et enregistre le résultat. Chaque ligne est commentée afin que vous compreniez **pourquoi** nous faisons ce que nous faisons, et pas seulement **quoi**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartLabelDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the Word document that already contains a pie chart.
            //    Change the path to where your Chart.docx lives.
            Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

            // 2️⃣ Retrieve the first chart node in the document.
            //    The GetChild method walks the document tree and returns the first Node of type Chart.
            Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Access the data label collection of the first series.
            //    In a pie chart each series represents the whole pie; the collection holds the labels for each slice.
            ChartDataLabelCollection dataLabels = chart.Series[0].DataLabelCollection;

            // 4️⃣ Position the data labels **outside** the slices.
            //    This is the most readable layout for pie/doughnut charts.
            dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

            // 5️⃣ Turn on the percentage display.
            //    ShowPercentage automatically calculates and shows each slice’s contribution.
            dataLabels.ShowPercentage = true;

            // 6️⃣ (Optional) If you also want the actual values, enable ShowValue.
            //    dataLabels.ShowValue = true; // uncomment to display raw numbers.

            // 7️⃣ Save the modified document.
            //    The new file will contain the pie chart with custom labels.
            doc.Save(@"YOUR_DIRECTORY\ChartWithCustomLabels.docx");

            Console.WriteLine("Pie chart labels added successfully!");
        }
    }
}
```

### Résultat attendu

Ouvrez `ChartWithCustomLabels.docx` dans Microsoft Word. Vous devriez voir le diagramme circulaire **avec des étiquettes de pourcentage positionnées à l’extérieur de chaque part**. Les étiquettes ressemblent à « 35 % », « 20 % », etc., rendant le graphique immédiatement compréhensible.

---

## Modifier les étiquettes de diagramme circulaire : positionnement et formatage

Si vous avez seulement besoin de **modifier les étiquettes de diagramme circulaire** sans afficher les pourcentages, vous pouvez ajuster la propriété `Position` à l’une des valeurs suivantes :

| Enum de position | Effet visuel |
|------------------|--------------|
| `InsideEnd`   | Les étiquettes se trouvent à l’intérieur de la part, juste au bord. |
| `Center`      | Les étiquettes apparaissent au centre de la part (utile pour les petits graphiques). |
| `OutsideEnd`  | Les étiquettes sont à l’extérieur de la part, reliées par une ligne de repère (notre valeur par défaut). |

```csharp
dataLabels.Position = ChartDataLabelPosition.Center; // example switch
```

**Astuce :** `OutsideEnd` fonctionne mieux lorsque le graphique comporte de nombreuses parts ; cela évite le chevauchement du texte.

---

## Afficher les étiquettes de pourcentage sur un diagramme circulaire

La propriété `ShowPercentage` est un **drapeau booléen**. La définir à `true` indique à Aspose.Words de calculer la contribution de chaque part à partir de la source de données sous‑jacente.

```csharp
dataLabels.ShowPercentage = true; // Turns on the % display
```

Vous pouvez également la combiner avec `ShowValue` si vous avez besoin à la fois des nombres bruts **et** des pourcentages :

```csharp
dataLabels.ShowValue = true; // Shows the actual cell value next to the %
```

Lorsque les deux drapeaux sont activés, l’étiquette ressemble à « 45 % (120) ».

---

## Mettre à jour les étiquettes de séries de graphique pour des données dynamiques

Souvent, vous générerez des graphiques à la volée—pensez aux ventes mensuelles ou aux résultats d’enquêtes. Pour **mettre à jour les étiquettes de séries de graphique** de façon programmatique, modifiez la collection `Series` avant d’intervenir sur les étiquettes de données :

```csharp
// Assume you have a second series you want to rename
chart.Series[1].Name = "Projected Growth";

// Refresh the data label collection after changes
ChartDataLabelCollection secondSeriesLabels = chart.Series[1].DataLabelCollection;
secondSeriesLabels.ShowPercentage = true;
secondSeriesLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

Cet extrait montre comment **mettre à jour les étiquettes de séries de graphique** pour n’importe quelle série, pas seulement la première. C’est pratique lorsque vous créez des rapports combinant des données réelles et prévisionnelles.

---

## Cas limites et pièges courants

| Situation | À surveiller | Solution |
|-----------|--------------|----------|
| **Le graphique n’est pas un diagramme circulaire/anneau** | `Position` peut n’avoir aucun effet visuel. | Vérifiez que `chart.Type` est `ChartType.Pie` ou `ChartType.Doughnut`. |
| **Aucun graphique trouvé** | `GetChild` renvoie `null`. | Ajoutez une clause de garde (voir le code) et consignez un message utile. |
| **Version Word plus ancienne** | Certaines fonctionnalités d’étiquettes sont ignorées. | Enregistrez au format `.docx` (le format moderne) pour garantir une prise en charge complète. |
| **Grand nombre de parts** | Les étiquettes peuvent se chevaucher même avec `OutsideEnd`. | Envisagez de réduire le nombre de parts ou d’augmenter la taille du graphique. |

---

## Exemple complet (copier‑coller)

Voici le **programme complet** que vous pouvez copier dans un nouveau projet console. Remplacez simplement `YOUR_DIRECTORY` par le dossier contenant `Chart.docx`.



## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser d’autres fonctionnalités de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Définir les options par défaut pour les étiquettes de données dans un graphique](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Personnaliser une série de graphique unique](/words/english/net/programming-with-charts/single-chart-series/)
- [Insérer un graphique en colonnes dans Word avec Aspose.Words pour .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}