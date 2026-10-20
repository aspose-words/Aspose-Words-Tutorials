---
category: general
date: 2026-07-19
description: Exploser une tranche de diagramme circulaire avec Aspose.Words pour C#.
  Apprenez à exploser une tranche de camembert, ajuster la taille du trou du donut
  et modifier rapidement les points de données du graphique.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- explode pie chart slice
- how to explode pie slice
- adjust doughnut hole size
- change chart data points
language: fr
lastmod: 2026-07-19
og_description: Faire exploser une part de diagramme circulaire avec Aspose.Words
  pour C#. Ce guide vous montre comment faire exploser une part de camembert, ajuster
  la taille du trou du donut et modifier efficacement les points de données du graphique.
og_image_alt: Screenshot showing an exploded pie chart slice created with Aspose.Words
  in C#
og_title: Faire exploser la part du graphique circulaire en C# – Tutoriel Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Explode pie chart slice using Aspose.Words for C#. Learn how to explode
    pie slice, adjust doughnut hole size, and change chart data points quickly.
  headline: Explode Pie Chart Slice in C# with Aspose.Words – Full Guide
  type: TechArticle
- description: Explode pie chart slice using Aspose.Words for C#. Learn how to explode
    pie slice, adjust doughnut hole size, and change chart data points quickly.
  name: Explode Pie Chart Slice in C# with Aspose.Words – Full Guide
  steps:
  - name: Install and Reference Aspose.Words
    text: 'First things first, add the Aspose.Words package to your project. In the
      Package Manager Console:'
  - name: Load the Word Document Containing the Chart
    text: We need a `Document` object that points at the `.docx` with the chart you
      want to modify.
  - name: Retrieve the First Chart Node
    text: Most examples assume a single chart, so we’ll grab the first one. If you
      have multiple charts, adjust the index accordingly.
  - name: Explode the First Slice of a Pie Chart
    text: Now the star of the show—**how to explode pie slice**. We’ll set the `Exploded`
      property of the first data point.
  - name: Adjust Doughnut Hole Size (If It’s a Doughnut Chart)
    text: If your chart happens to be a doughnut, you might want to **adjust doughnut
      hole size**. The hole size is a percentage of the chart’s radius.
  - name: Change Chart Data Points (Optional)
    text: Sometimes you need to **change chart data points**—maybe you’ve updated
      the underlying numbers and want the visual to reflect that.
  - name: Save the Modified Document
    text: Finally, write the changes back to disk. You can overwrite the original
      or create a new file—up to you.
  - name: What’s Next?
    text: '- **Style the exploded slice** (change fill color, border, or add a data
      label). Search for “Aspose.Words chart formatting”. - **Automate batch processing**
      of multiple documents—loop through a folder, explode slices, and save new versions.
      - **Combine with Aspose.Slides** if you need the same chart'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: Exploser une tranche de diagramme circulaire en C# avec Aspose.Words – Guide
  complet
url: /fr/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Exploser une tranche de diagramme circulaire en C# avec Aspose.Words – Guide complet

Vous vous êtes déjà demandé comment **exploser une tranche de diagramme circulaire** dans un document Word en utilisant C# ? Vous n'êtes pas le seul. Que vous prépariez une présentation commerciale ou que vous visualisiez les résultats d’une enquête, une tranche éclatée attire immédiatement l’attention là où vous le souhaitez. Dans ce tutoriel, nous parcourrons l’ensemble du processus : charger un document, récupérer le graphique, exploser la première tranche, ajuster le trou du donut, et même modifier les points de données du graphique.

Nous aborderons également les concepts secondaires que vous pourriez rechercher : **comment exploser une tranche de diagramme**, **ajuster la taille du trou du donut**, et **modifier les points de données du graphique**. Pas de blabla, juste une solution complète, prête à copier‑coller.

---

## Ce dont vous avez besoin

Avant de commencer, assurez‑vous d’avoir :

- **Aspose.Words for .NET** (la dernière version au 19‑07‑2026). Vous pouvez l’obtenir via NuGet avec `Install-Package Aspose.Words`.
- Un projet **.NET 6+** (ou .NET Framework 4.7.2+ si vous êtes encore sur l’ancien framework).
- Un fichier Word (`Chart.docx`) contenant déjà un graphique circulaire ou en forme de donut. Si vous n’en avez pas, créez rapidement un graphique dans Word et enregistrez‑le.

C’est tout — aucune bibliothèque supplémentaire, aucune interopérabilité COM, uniquement du code géré pur.

---

## Exploser une tranche de diagramme circulaire – Implémentation pas à pas

Ci‑dessous, nous décomposons la tâche en étapes faciles. Chaque section possède un titre clair, un extrait de code et une courte explication du *pourquoi* de chaque action.

### Étape 1 : Installer et référencer Aspose.Words

Première chose, ajoutez le package Aspose.Words à votre projet. Dans la console du gestionnaire de packages :

```powershell
Install-Package Aspose.Words
```

> **Astuce :** Si vous utilisez l’interface NuGet intégrée à Visual Studio, recherchez « Aspose.Words » et cliquez sur Installer. Cela vous garantit les dernières corrections de bugs et la prise en charge des graphiques dès le départ.

### Étape 2 : Charger le document Word contenant le graphique

Nous avons besoin d’un objet `Document` qui pointe vers le fichier `.docx` contenant le graphique que vous souhaitez modifier.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document
Document doc = new Document(@"C:\Charts\Chart.docx");

// Verify that the document actually contains a chart
if (doc.GetChildNodes(NodeType.Chart, true).Count == 0)
{
    throw new InvalidOperationException("No chart found in the specified document.");
}
```

> **Pourquoi c’est important :** `Document` est le point d’entrée de chaque opération dans Aspose.Words. En vérifiant la présence de graphiques dès le départ, on évite les références nulles plus tard lorsqu’on essaie d’exploser une tranche.

### Étape 3 : Récupérer le premier nœud de graphique

La plupart des exemples supposent un seul graphique, nous allons donc récupérer le premier. Si vous avez plusieurs graphiques, ajustez l’indice en conséquence.

```csharp
// Grab the first chart in the document (index 0)
Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
```

> **Remarque :** Le cast vers `Chart` est sûr après avoir confirmé qu’un graphique existe. Cet objet nous donne accès aux séries, aux points de données et aux paramètres spécifiques au type de graphique.

### Étape 4 : Exploser la première tranche d’un graphique circulaire

Voici le cœur du sujet—**comment exploser une tranche de diagramme**. Nous allons définir la propriété `Exploded` du premier point de données.

```csharp
// Ensure the chart is a Pie (or Pie3D) before exploding
if (chart.ChartType == ChartType.Pie || chart.ChartType == ChartType.Pie3D)
{
    // Explode the first slice (index 0)
    chart.PieChartData.Series[0].DataPoints[0].Exploded = true;
}
else
{
    Console.WriteLine("The chart is not a pie chart; skipping explode operation.");
}
```

> **Pourquoi cela fonctionne :** `Exploded` indique à Word de détacher cette tranche du centre, créant l’effet classique du « pie chart explosé ». La propriété est booléenne, donc la mettre à `true` suffit.

### Étape 5 : Ajuster la taille du trou du donut (si c’est un graphique donut)

Si votre graphique est un donut, vous pouvez vouloir **ajuster la taille du trou du donut**. La taille du trou est un pourcentage du rayon du graphique.

```csharp
// Check for Doughnut chart type and modify the hole size
if (chart.ChartType == ChartType.Doughnut)
{
    // Set the hole size to 30% (range: 0–100)
    chart.DoughnutChartData.HoleSize = 30;
}
```

> **Ce que signifie le nombre :** Une valeur de `30` indique que le cercle intérieur occupera 30 % du rayon total, laissant un anneau extérieur plus épais.

### Étape 6 : Modifier les points de données du graphique (optionnel)

Parfois, vous devez **modifier les points de données du graphique**—peut‑être avez‑vous mis à jour les chiffres sous‑jacent et vous voulez que le visuel reflète ces changements.

```csharp
// Example: Update the second data point's value to 75
if (chart.PieChartData?.Series?.Count > 0 && chart.PieChartData.Series[0].DataPoints.Count > 1)
{
    chart.PieChartData.Series[0].DataPoints[1].Value = 75;
}
```

> **Pourquoi le faire :** Modifier la valeur d’un point de données recalcule automatiquement les pourcentages des tranches, maintenant le graphique à jour sans édition manuelle dans Word.

### Étape 7 : Enregistrer le document modifié

Enfin, écrivez les changements sur le disque. Vous pouvez écraser le fichier original ou créer un nouveau fichier—c’est à vous de décider.

```csharp
// Save the document with the exploded slice and adjusted doughnut hole
doc.Save(@"C:\Charts\FormattedChart.docx");

// Quick confirmation
Console.WriteLine("Document saved successfully with exploded pie chart slice.");
```

> **Conseil :** Utilisez `SaveFormat.Docx` si vous devez être explicite, mais `Save(string)` détecte automatiquement le format à partir de l’extension du fichier.

---

## Résultat attendu

Lorsque vous ouvrirez `FormattedChart.docx` dans Microsoft Word, vous devriez voir :

- La première tranche d’un graphique circulaire **explosée** vers l’extérieur.
- Si le graphique est un donut, le trou central occupe maintenant **30 %** du rayon.
- Tous les points de données modifiés reflètent les nouvelles valeurs que vous avez définies.

Voici une maquette de ce à quoi ressemble la tranche explosée (image à titre d’illustration uniquement).

![Exploded pie chart slice created with Aspose.Words in C#](exploded-pie-slice.png)

*Texte alternatif :* **tranche de diagramme circulaire éclatée** montrant un segment détaché dans un document Word.

---

## Questions fréquentes et cas particuliers

**Et si le graphique n’est pas un circulaire ou un donut ?**  
Le code vérifie `ChartType` avant d’appliquer `Exploded` ou `HoleSize`. Pour les graphiques à barres, en lignes ou en aires, ces propriétés n’existent tout simplement pas, donc la logique les ignore en toute sécurité.

**Puis‑je exploser plusieurs tranches ?**  
Absolument. Parcourez `chart.PieChartData.Series[0].DataPoints` et définissez `Exploded = true` sur chaque indice que vous désirez.

**Dois‑je me soucier des formats numériques spécifiques à la culture ?**  
Aspose.Words stocke les valeurs numériques en tant que doubles, indépendamment de la locale, vous êtes donc à l’abri des problèmes de virgules vs points.

**Qu’en est‑il des graphiques intégrés dans les en‑têtes/pieds de page ?**  
Utilisez `doc.GetChildNodes(NodeType.Chart, true)` pour récupérer tous les graphiques, puis inspectez `ParentNode` de chaque nœud pour savoir où il se trouve. La même logique d’explosion s’applique.

---

## Conclusion

Vous disposez maintenant d’une solution solide, prête à copier‑coller, pour **exploser une tranche de diagramme circulaire** avec Aspose.Words en C#. Nous avons couvert tout le flux : chargement du document, récupération du graphique, explosion de la tranche, **ajustement de la taille du trou du donut**, **modification des points de données**, puis sauvegarde du fichier.

N’hésitez pas à expérimenter : essayez d’exploser une autre tranche, modifiez la taille du trou à 45 %, ou mettez à jour plusieurs points de données en même temps. L’API Aspose.Words rend ces ajustements simples, et les changements apparaissent immédiatement à l’ouverture du fichier Word.

---

### Et après ?

- **Styliser la tranche explosée** (modifier la couleur de remplissage, la bordure ou ajouter une étiquette de données). Recherchez « Aspose.Words chart formatting ».
- **Automatiser le traitement par lots** de plusieurs documents : parcourez un dossier, explosez les tranches, et enregistrez de nouvelles versions.
- **Combiner avec Aspose.Slides** si vous avez besoin du même graphique dans une présentation PowerPoint.

Vous avez d’autres questions sur la manipulation des graphiques, ou vous souhaitez approfondir d’autres types de graphiques ? Laissez un commentaire ci‑dessous, et bon codage !

## Que devez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques présentées dans ce guide. Chaque ressource inclut des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et explorer des approches d’implémentation alternatives dans vos projets.

- [Insérer un graphique à colonnes dans Word avec Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insérer un graphique à colonnes simple dans Word avec Aspose.Words for .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Insérer un graphique en aires dans un document Word | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}