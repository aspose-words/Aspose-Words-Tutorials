---
category: general
date: 2026-09-21
description: Comment formater les séries dans un graphique en courbes Word avec C#.
  Apprenez à créer un document Word, insérer un graphique en courbes et appliquer
  un format numérique personnalisé.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format series
- create word document
- insert line chart
- add chart to word
- apply custom number format
language: fr
lastmod: 2026-09-21
og_description: Comment formater les séries dans un graphique en courbes Word en utilisant
  C#. Ce tutoriel vous montre comment créer un document Word, insérer un graphique
  en courbes et appliquer un format numérique personnalisé.
og_image_alt: Screenshot of a Word document showing a line chart with percentage‑formatted
  Y‑axis values
og_title: Comment formater les séries dans un graphique en courbes Word avec C# –
  guide étape par étape
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: How to format series in a Word line chart using C#. Learn to create
    a Word document, insert a line chart, and apply a custom number format.
  headline: How to format series in a Word line chart with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart
- Word automation
title: Comment formater les séries d’un graphique en courbes Word avec C#
url: /fr/net/programming-with-charts/how-to-format-series-in-a-word-line-chart-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment formater des séries dans un graphique en courbes Word avec C#

Si vous avez besoin de **formater des séries** dans un graphique en courbes Word, ce guide vous fournit une solution complète, prête à l’emploi. Vous verrez comment **créer un document Word**, **insérer un graphique en courbes**, et **appliquer un format numérique personnalisé** aux valeurs Y — le tout avec Aspose.Words for .NET.

L’automatisation Word devient simple une fois que vous comprenez le modèle d’objet du graphique. À la fin de ce tutoriel, vous disposerez d’un fichier Word contenant un graphique en courbes dont les séries de données sont affichées en pourcentages avec deux décimales.

## Ce que vous allez réaliser

* Générer un fichier `.docx` vierge par programme.  
* Ajouter un graphique en courbes de taille 400 × 300 points.  
* Accéder à la première série de données du graphique.  
* Appliquer le code de format `#,##0.00%` afin que les valeurs Y apparaissent en pourcentage.  

Aucun outil externe n’est requis en dehors du package NuGet Aspose.Words.

## Prérequis

* .NET 6.0 SDK ou version ultérieure.  
* Visual Studio 2022 (ou tout IDE C#).  
* Aspose.Words for .NET 23.10 ou plus récent – installez via `dotnet add package Aspose.Words`.  

Le code fonctionne sous Windows, Linux et macOS car Aspose.Words est indépendant de la plateforme.

## Créer un document Word avec Aspose.Words

La première étape consiste à instancier un objet `Document`. Cet objet représente l’ensemble du fichier Word en mémoire.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document.
        Document doc = new Document();

        // The document currently has no content.
        // We will add a chart in the next step.
```

*Pourquoi c’est important* : `Document` est le point d’entrée pour toutes les opérations de traitement Word. Sans lui, vous ne pouvez pas ajouter de paragraphes, de tableaux ou de graphiques.

## Insérer un graphique en courbes dans le document

Un `DocumentBuilder` écrit du contenu dans le `Document`. L’appel à `InsertChart` crée une forme de graphique sur la page courante.

```csharp
        // Step 2: Initialize a DocumentBuilder to construct the document content.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a line chart with the desired size (400 × 300 points).
        Chart chart = builder.InsertChart(ChartType.Line, 400, 300);
```

*Pourquoi c’est important* : `InsertChart` renvoie un objet `Chart` qui vous donne un contrôle total sur les séries, les axes et le formatage. Les paramètres de taille sont exprimés en points (1 point = 1/72 pouce).

## Accéder à la première série de données

Chaque graphique contient une ou plusieurs `ChartSeries`. La première série se trouve à l’index 0.

```csharp
        // Step 4: Access the first data series of the chart.
        ChartSeries series = chart.Series[0];
```

*Pourquoi c’est important* : L’objet `ChartSeries` contient les valeurs Y, les valeurs X et les options de formatage pour une seule ligne d’un graphique en courbes. Modifier cet objet change la représentation visuelle des données.

## Appliquer un format numérique personnalisé à la série

La propriété `FormatCode` contrôle la façon dont les valeurs numériques sont affichées. La définir sur `#,##0.00%` indique à Word de traiter les valeurs comme des pourcentages avec deux décimales.

```csharp
        // Step 5: Apply a custom number format to the Y‑values.
        // This displays the numbers as percentages with two decimals.
        series.YValues.FormatCode = "#,##0.00%";

        // Optional: Populate the series with sample data.
        series.YValues.Add(0.15);
        series.YValues.Add(0.30);
        series.YValues.Add(0.45);
        series.YValues.Add(0.60);
```

*Pourquoi c’est important* : Sans format personnalisé, Word affiche les nombres décimaux bruts (par ex., `0.15`). Le code de format les convertit en `15.00%`, ce qui est souvent ce que les rapports d’entreprise exigent.

## Enregistrer le document et vérifier le résultat

```csharp
        // Save the document to the file system.
        string outputPath = "FormattedSeriesLineChart.docx";
        doc.Save(outputPath);
        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Lorsque vous ouvrez `FormattedSeriesLineChart.docx` dans Microsoft Word, vous verrez un graphique en courbes où les libellés de l’axe Y affichent `15.00%`, `30.00%`, `45.00%` et `60.00%`. La taille du graphique correspond aux dimensions fournies dans `InsertChart`.

### Capture d’écran du résultat attendu

> *Image : Une page de document Word affichant un graphique en courbes avec des valeurs d’axe Y formatées en pourcentage.*  
> *(Texte alternatif : Capture d’écran d’un document Word montrant un graphique en courbes avec des valeurs d’axe Y formatées en pourcentage)*

## Variations courantes et cas limites

| Situation | Ajustement |
|-----------|------------|
| **Séries multiples** | Boucler sur `chart.Series` et définir `FormatCode` pour chaque série. |
| **Type de graphique différent** | Remplacer `ChartType.Line` par `ChartType.Column`, `ChartType.Pie`, etc. |
| **Séparateurs spécifiques à la locale** | Utiliser des chaînes de format sensibles à `CultureInfo`, par ex., `"# ##0,00 %"` pour les paramètres régionaux français. |
| **Source de données dynamique** | Remplir `series.YValues` à partir d’une base de données ou d’un fichier CSV avant d’appliquer le format. |

**Astuce :** Appliquez toujours le format **après** avoir ajouté les valeurs Y. Modifier le format d’abord puis ajouter les valeurs fonctionne également, mais le faire plus tard garantit que le format est appliqué à l’ensemble final de données.

## Récapitulatif

Vous savez maintenant **comment formater des séries** dans un graphique en courbes Word avec C#. Le tutoriel a couvert :

* Créer un document Word (`create word document`).  
* Insérer un graphique en courbes (`insert line chart`, `add chart to word`).  
* Accéder à la première série du graphique.  
* Appliquer un format numérique personnalisé (`apply custom number format`) pour afficher des pourcentages.

## Étapes suivantes

* Expérimentez avec différentes valeurs de `ChartType` pour voir comment se comportent les autres visualisations.  
* Ajoutez des titres, des libellés d’axes et des légendes en utilisant `chart.Title`, `chart.AxisX.Title` et `chart.AxisY.Title`.  
* Exportez le graphique en tant qu’image (`chart.Save` avec `SaveFormat.Png`) pour une utilisation dans des rapports web.

N’hésitez pas à adapter ce modèle pour générer des tableaux de bord, des rapports financiers ou tout document nécessitant un graphique programmatique. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Créer un graphique en courbes dans Word avec Aspose.Words for .NET](/words/english/net/working-with-charts/create-chart-using-shape/)
- [Insérer un graphique en colonnes dans un document Word](/words/english/net/programming-with-charts/insert-column-chart/)
- [Insérer un graphique en aires dans un document Word | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}