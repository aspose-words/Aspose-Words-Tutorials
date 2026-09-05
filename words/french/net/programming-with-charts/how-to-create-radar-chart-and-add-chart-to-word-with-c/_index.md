---
category: general
date: 2026-09-05
description: Créer un graphique en radar dans Word avec C#. Apprenez à générer un
  document Word vierge, ajouter un graphique en radar, définir la taille du graphique
  et activer rapidement les marques de graduation.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radar chart
- add chart to word
- add radar chart
- generate blank word document
- set chart size word
language: fr
lastmod: 2026-09-05
og_description: Créer un graphique en radar dans Word avec C#. Ce guide vous montre
  comment générer un document Word vierge, ajouter un graphique en radar, définir
  la taille du graphique et activer les marques de graduation — le tout en quelques
  minutes.
og_image_alt: Screenshot of a Word document with a created radar chart
og_title: Créer un graphique radar dans Word – guide C# étape par étape
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create radar chart in Word using C#. Learn to generate a blank Word
    document, add a radar chart, set chart size, and enable tick marks quickly.
  headline: How to create radar chart and add chart to Word with C#
  type: TechArticle
tags:
- C#
- Aspose.Words
- Chart
- Word automation
title: Comment créer un graphique radar et ajouter le graphique à Word avec C#
url: /fr/net/programming-with-charts/how-to-create-radar-chart-and-add-chart-to-word-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer un radar chart et ajouter un chart à Word avec C#

Si vous devez **create radar chart** dans un fichier Word, ce guide vous accompagne tout au long du processus. Vous apprendrez comment **generate blank word document**, insérer un radar chart, **set chart size word**, et activer les graduations d'axe — le tout en quelques lignes de code C#.

Ajouter des données visuelles aux rapports est une exigence courante, et l'utilisation d'Aspose.Words simplifie la tâche. Dans les étapes ci‑dessous, nous couvrons également comment **add chart to word** des documents de façon programmatique, afin que vous puissiez automatiser des tableaux de bord, des résumés financiers ou tout contenu basé sur des données.

## Prérequis

* .NET 6.0 ou version ultérieure installée  
* Une licence Aspose.Words pour .NET (ou un essai gratuit) – la bibliothèque fournit les API `Document`, `DocumentBuilder` et chart utilisées dans ce tutoriel  
* Visual Studio 2022 (ou tout IDE C#)  

> **Astuce :** Si vous testez, placez le DLL Aspose.Words dans le dossier `bin` de votre projet et référencez‑le via NuGet (`Install-Package Aspose.Words`).

## Comment créer un radar chart dans un document Word

La première étape consiste à **generate blank word document** qui hébergera le graphique. Cela vous fournit une toile vierge et vous permet de contrôler les métadonnées du document avant d’ajouter tout contenu.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// 1️⃣ Create an empty Word document
Document document = new Document();   // this is a blank .docx file
```

*Pourquoi c’est important :* Un objet `Document` vide garantit qu’aucun style ou section caché n’interfère avec la mise en page du graphique. Cela vous permet également de définir les propriétés du document (auteur, titre) ultérieurement si nécessaire.

## Comment ajouter un chart à Word en utilisant Aspose.Words

Ensuite, créez un `DocumentBuilder`. Le builder est le moteur qui vous permet d’insérer du texte, des images et des graphiques dans le document.

```csharp
// 2️⃣ Initialize a DocumentBuilder for the empty document
DocumentBuilder builder = new DocumentBuilder(document);
```

Vous pouvez maintenant **add radar chart** directement à l’endroit où le curseur est positionné. La méthode `InsertChart` accepte un enum `ChartType`, ainsi que la largeur et la hauteur en points.

```csharp
// 3️⃣ Insert a radar (radial) chart with a specific size
Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

*Pourquoi 400 × 300 ?* Ces dimensions offrent un graphique clair et lisible sur une page A4 standard. Vous pouvez ajuster la taille ultérieurement avec l’étape **set chart size word** si votre mise en page nécessite un rapport d’aspect différent.

## Définir la taille du graphique dans Word

Si vous devez affiner la taille après l’insertion, vous pouvez modifier les propriétés `Width` et `Height` du graphique. Cela est utile lorsque le texte environnant ou les marges de la page imposent un équilibre visuel différent.

```csharp
// 4️⃣ Adjust chart dimensions (optional)
// radarChart.Width = 500;   // width in points
// radarChart.Height = 350;  // height in points
```

> **Note :** La surcharge de `InsertChart` définit déjà la taille, donc le code ci‑dessus est optionnel et présenté pour plus de complétude.

## Activer les marques de graduation sur l’axe radial

Un radar chart est le plus utile lorsque l’axe radial affiche des graduations claires. Les paramètres suivants activent les marques de graduation et définissent l’intervalle à 30 degrés, ce qui correspond aux affichages radar de type boussole typiques.

```csharp
// 5️⃣ Turn on graduations (tick marks) and set interval
radarChart.AxisX.HasGraduations = true;      // show tick marks
radarChart.AxisX.GraduationInterval = 30;   // every 30 degrees
```

*Pourquoi c’est important :* Les graduations aident les lecteurs à évaluer les valeurs à chaque angle, améliorant la lisibilité pour les parties prenantes qui ne sont pas familières avec les données.

## Enregistrer le document contenant le graphique

Enfin, écrivez le document sur le disque. Vous pouvez choisir n’importe quel dossier ; assurez‑vous simplement que le chemin existe.

```csharp
// 6️⃣ Save the Word file
document.Save(@"C:\Temp\RadialChart.docx");
```

Lorsque vous ouvrez `RadialChart.docx` dans Microsoft Word, vous verrez un radar chart entièrement rendu, centré sur la page, de la taille spécifiée, avec des marques de graduation toutes les 30 degrés.

### Résultat attendu

* Un fichier `.docx` nommé **RadialChart.docx**  
* La première page contient un radar chart de taille 400 × 300 points  
* L’axe X (axe radial) affiche des marques de graduation à 0°, 30°, 60°, …, 330°  

Vous pouvez maintenant remplacer la série de données factice par vos propres valeurs en accédant à `radarChart.Series` – mais cela dépasse le cadre de ce tutoriel de base **add radar chart**.

## Variations courantes et cas limites

| Scénario | Ajustement |
|----------|------------|
| **Type de graphique différent** | Replace `ChartType.Radar` with `ChartType.Column`, `ChartType.Pie`, etc. |
| **Graphiques multiples** | Call `InsertChart` repeatedly; each call positions the new chart after the previous one. |
| **Ensembles de données volumineux** | Use `radarChart.Series[0].DataPoints.AddDataPointForBarSeries(value)` to populate many points. |
| **Enregistrement en PDF** | Call `document.Save("RadialChart.pdf", SaveFormat.Pdf);` after the chart is added. |
| **Exécution sur .NET Core** | Ensure you reference `Aspose.Words.NETCore` package; API usage is identical. |

## Exemple complet, exécutable

Ci‑dessus se trouve le programme complet que vous pouvez copier‑coller dans une application console. Il inclut toutes les étapes, les ajustements de taille optionnels, et des commentaires pour plus de clarté.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace RadarChartDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Generate a blank Word document
            Document document = new Document();

            // 2️⃣ Create a builder to work with the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // 3️⃣ Insert a radar chart (400 × 300 points)
            Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);

            // 4️⃣ (Optional) Change chart size if needed
            // radarChart.Width = 500;
            // radarChart.Height = 350;

            // 5️⃣ Enable tick marks on the radial axis
            radarChart.AxisX.HasGraduations = true;          // show tick marks
            radarChart.AxisX.GraduationInterval = 30;       // every 30 degrees

            // 6️⃣ Populate the chart with sample data (optional)
            radarChart.Series[0].DataPoints.Clear();
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(10);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(20);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(30);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(40);

            // 7️⃣ Save the document
            string outputPath = @"C:\Temp\RadialChart.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Exécutez le programme, ouvrez le fichier résultant, et vous verrez le radar chart exactement comme décrit.

## Conclusion

Vous savez maintenant comment **create radar chart** et **add chart to Word** des documents en utilisant C#. Le tutoriel a couvert la génération d’un **blank word document**, l’insertion d’un radar chart, **set chart size word**, et l’activation des graduations d’axe. Avec cette base, vous pouvez étendre la solution à plusieurs graphiques, des séries de données personnalisées, ou l’exportation en PDF.

### Prochaines étapes

* Explorez d’autres types de graphiques avec `ChartType` (par ex., `Bar`, `Line`) – consultez le mot‑clé **add radar chart** pour des exemples associés.

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Insert Scatter Chart in Word Document](/words/english/net/programming-with-charts/insert-scatter-chart/)
- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}