---
category: general
date: 2026-07-29
description: Comment modifier un graphique dans un document Word — apprenez à changer
  la position des étiquettes du graphique, ajuster les étiquettes d’un graphique à
  barres, modifier les étiquettes de données du graphique et changer la police des
  étiquettes du graphique.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit chart
- change chart label position
- adjust bar chart labels
- modify chart data labels
- change chart label font
language: fr
lastmod: 2026-07-29
og_description: Comment modifier rapidement un graphique dans Word. Maîtrisez le changement
  de la position des étiquettes de graphique, l’ajustement des étiquettes de diagramme
  à barres, la modification des étiquettes de données du graphique et le changement
  de la police des étiquettes.
og_image_alt: Screenshot of a Word bar chart with custom label positions and larger
  font size
og_title: Comment modifier un graphique dans Word – Modifier les étiquettes et la
  police
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: How to edit chart in a Word document—learn to change chart label position,
    adjust bar chart labels, modify chart data labels, and change chart label font.
  headline: 'How to Edit Chart in Word: Change Label Position, Font & More'
  type: TechArticle
- description: How to edit chart in a Word document—learn to change chart label position,
    adjust bar chart labels, modify chart data labels, and change chart label font.
  name: 'How to Edit Chart in Word: Change Label Position, Font & More'
  steps:
  - name: What if the document contains multiple charts?
    text: 'The code above grabs the *first* chart (`GetChild(NodeType.Shape, 0, true)`).
      To edit all charts, replace the single retrieval with a loop:'
  - name: How to **change chart label font** for a specific series only?
    text: 'Each `ChartSeries` has its own `DataLabelCollection`. Target a series by
      index:'
  - name: Does this work with pie or line charts?
    text: Yes—`ChartDataLabelPosition` supports values like `InsideEnd`, `OutsideEnd`,
      and `BestFit`. For a pie chart you might prefer `OutsideEnd` to keep labels
      readable.
  - name: What about localization (e.g., different decimal separators)?
    text: Aspose.Words respects the document’s locale settings. If you need to enforce
      a specific format, adjust `label.NumberFormat` before saving.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
title: 'Comment modifier un graphique dans Word : changer la position des étiquettes,
  la police et plus'
url: /fr/net/working-with-charts/how-to-edit-chart-in-word-change-label-position-font-more/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment modifier un Chart dans Word : changer la position du libellé, la police et plus

Modifier un chart dans un document Word est un besoin fréquent lorsque vous souhaitez que vos rapports aient un aspect soigné. Vous êtes déjà tombé sur la difficulté de **change chart label position** ou de rendre les libellés lisibles sans fouiller dans d’innombrables menus ? Vous n’êtes pas seul — la plupart des développeurs rencontrent ce problème lorsqu’ils automatisent la génération de rapports. Dans ce guide, nous parcourrons un exemple complet et exécutable qui montre exactement comment **adjust bar chart labels**, **modify chart data labels**, et **change chart label font** en utilisant C# et la bibliothèque Aspose.Words.

## Ce que vous allez apprendre

- Charger un fichier .docx contenant déjà un bar chart.  
- Récupérer la première forme de chart et accéder à sa collection de data‑label.  
- **Change chart label position** pour rendre les barres plus épurées.  
- **Adjust bar chart labels** taille de police pour une meilleure lisibilité.  
- Enregistrer le document modifié sur le disque.  

Aucun outil externe, aucune étape manuelle dans l’interface — uniquement du code pur que vous pouvez intégrer à n’importe quel projet .NET. À la fin, vous disposerez d’une solution autonome réutilisable sur des dizaines de documents.

> **Prerequisites**  
> - .NET 6.0 ou version ultérieure (le code fonctionne également avec .NET Framework 4.7+).  
> - Aspose.Words for .NET (disponible via NuGet).  
> - Un fichier Word (`BarChart.docx`) contenant déjà un bar chart.  

Si l’un de ces éléments vous manque, téléchargez dès maintenant le dernier package Aspose.Words :

```bash
dotnet add package Aspose.Words
```

---

## How to Edit Chart : Retrieve the Chart from the Word Document

La première étape pour **how to edit chart** consiste à charger le document et à localiser la forme de chart. Aspose.Words traite les charts comme des nœuds `Shape`, nous pouvons donc utiliser `GetChild` avec `NodeType.Shape` pour récupérer le premier chart rencontré.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the Word document that contains a chart
Document document = new Document(@"C:\Temp\BarChart.docx");

// Retrieve the first chart shape from the document
Chart chart = (Chart)document.GetChild(NodeType.Shape, 0, true);
```

> **Why this matters:**  
> En accédant directement à l’objet `Chart`, vous évitez le surcoût d’ouverture du fichier dans Word et de l’ajustement manuel de chaque libellé. C’est la pierre angulaire de toute automatisation **modify chart data labels**.

## Adjust Bar Chart Labels : Change Chart Label Position

Maintenant que nous disposons de l’instance `Chart`, parcourons sa `DataLabelCollection`. L’objectif est de **change chart label position** afin que chaque libellé se place proprement à la base de sa barre, plutôt que de flotter maladroitement au-dessus.

```csharp
// Loop through each data label in the chart
foreach (ChartDataLabel dataLabel in chart.DataLabelCollection)
{
    // Place label inside the base of the bar
    dataLabel.Position = ChartDataLabelPosition.InsideBase;
}
```

> **Pro tip:**  
> `InsideBase` fonctionne bien pour les bar charts verticaux. Si vous travaillez avec un bar chart horizontal, essayez `InsideEnd` à la place. Expérimenter les positions est peu coûteux — il suffit de relancer le code et d’ouvrir le document enregistré.

## Change Chart Label Font : Adjust Font Size for Readability

Une police trop petite est le tueur silencieux de la clarté des rapports. Pour **change chart label font**, il suffit de définir la propriété `Font.Size` sur chaque `ChartDataLabel`. Nous la porterons à 9 pt, un compromis idéal pour la plupart des rapports imprimés.

```csharp
foreach (ChartDataLabel dataLabel in chart.DataLabelCollection)
{
    // Set a readable font size (9 points)
    dataLabel.Font.Size = 9;
}
```

> **Why we do this:**  
> Ajuster la taille de la police fait partie des bonnes pratiques **modify chart data labels**. Des polices plus grandes améliorent l’accessibilité et réduisent le besoin de post‑traitement manuel.

## Save the Updated Document

Après avoir ajusté les positions et les polices, la dernière étape de **how to edit chart** consiste à persister les modifications. Aspose.Words le fait en une seule ligne.

```csharp
// Save the modified document with new label settings
document.Save(@"C:\Temp\BarChartCustomLabels.docx");
```

Ouvrez `BarChartCustomLabels.docx` dans Word et vous verrez les libellés bien ajustés à l’intérieur des barres, affichés avec une police claire de 9 pt. Fini le besoin de plisser les yeux sur de minuscules chiffres.

---

## Full Working Example (All Steps in One File)

Voici un programme console complet, prêt à être exécuté, qui montre l’ensemble du flux — du chargement du document à l’enregistrement de la version mise à jour. Copiez‑collez‑le dans un nouveau projet console .NET et appuyez sur **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelEditor
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source document (must contain a bar chart)
            string sourcePath = @"C:\Temp\BarChart.docx";

            // Path where the edited document will be saved
            string destPath = @"C:\Temp\BarChartCustomLabels.docx";

            // Load the Word document
            Document doc = new Document(sourcePath);

            // Retrieve the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Iterate over each data label
            foreach (ChartDataLabel label in chart.DataLabelCollection)
            {
                // Change chart label position
                label.Position = ChartDataLabelPosition.InsideBase;

                // Change chart label font size
                label.Font.Size = 9;
            }

            // Save the updated document
            doc.Save(destPath);
            Console.WriteLine($"Chart labels updated and saved to: {destPath}");
        }
    }
}
```

**Expected output** when you run the program:

```
Chart labels updated and saved to: C:\Temp\BarChartCustomLabels.docx
```

Ouvrez le fichier résultant et vous constaterez que les **adjust bar chart labels** sont positionnés à l’intérieur des barres avec une taille de police confortable.

---

## Common Questions & Edge Cases

### What if the document contains multiple charts?

Le code ci‑dessus récupère le *premier* chart (`GetChild(NodeType.Shape, 0, true)`). Pour modifier tous les charts, remplacez la récupération unique par une boucle :

```csharp
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape shape in shapes)
{
    if (shape.HasChart)
    {
        Chart chart = shape.GetChart();
        // Apply label changes as shown earlier
    }
}
```

### How to **change chart label font** for a specific series only?

Chaque `ChartSeries` possède sa propre `DataLabelCollection`. Ciblez une série par son indice :

```csharp
ChartSeries series = chart.Series[1]; // second series (zero‑based)
foreach (ChartDataLabel label in series.DataLabelCollection)
{
    label.Font.Size = 10; // larger for this series only
}
```

### Does this work with pie or line charts?

Oui—`ChartDataLabelPosition` prend en charge des valeurs comme `InsideEnd`, `OutsideEnd` et `BestFit`. Pour un pie chart, vous préférerez probablement `OutsideEnd` afin de garder les libellés lisibles.

### What about localization (e.g., different decimal separators)?

Aspose.Words respecte les paramètres de locale du document. Si vous devez imposer un format spécifique, ajustez `label.NumberFormat` avant l’enregistrement.

---

## Recap & Next Steps

Nous avons couvert **how to edit chart** dans un document Word de A à Z : chargement du fichier, récupération du chart, **changing chart label position**, **adjusting bar chart labels**, **modifying chart data labels**, et enfin **changing chart label font** avant d’enregistrer. L’exemple complet est prêt pour la production et peut être intégré à n’importe quel pipeline d’automatisation.

Prêt à passer au niveau supérieur ? Voici quelques idées de suivi :

- **Ajouter des couleurs aux data labels** (`dataLabel.Font.Color = Color.Blue;`).  
- **Afficher les valeurs en pourcentage** (`dataLabel.NumberFormat = "0%";`).  
- **Créer des charts programmatically** au lieu de charger des charts existants.  

Toutes ces extensions utilisent la même surface d’API que nous avons explorée aujourd’hui, vous vous sentirez donc immédiatement à l’aise.

Si vous avez rencontré des difficultés, laissez un commentaire ci‑dessous ou consultez la documentation Aspose.Words pour des options de personnalisation de chart plus avancées. Bon codage, et profitez de ces graphiques magnifiquement libellés !

## What Should You Learn Next?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et explorer des approches alternatives dans vos propres projets.

- [Personnaliser les libellés de données du graphique](/words/english/net/programming-with-charts/chart-data-label/)
- [Formater le nombre de libellés de données dans un graphique](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Libellé de données du graphique](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}