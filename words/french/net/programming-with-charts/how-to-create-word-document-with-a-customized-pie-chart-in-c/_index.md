---
category: general
date: 2026-10-07
description: Apprenez à créer un document Word et à insérer un diagramme circulaire
  à l'aide d'Aspose.Words en C#. Le guide montre également comment générer un fichier
  Word avec des libellés de graphique personnalisés.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- generate word file
- customize pie chart
- how to add pie chart
language: fr
lastmod: 2026-10-07
og_description: Créez un document Word et insérez un diagramme circulaire en C#. Suivez
  ce guide étape par étape pour générer un fichier Word avec des libellés de graphique
  entièrement personnalisés.
og_image_alt: Screenshot of a Word document that contains a customized pie chart created
  with C#
og_title: Créer un document Word avec un graphique circulaire personnalisé en C#
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to create word document and insert pie chart using Aspose.Words
    in C#. The guide also shows how to generate word file with custom chart labels.
  headline: How to create word document with a customized pie chart in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- Chart
title: Comment créer un document Word avec un graphique circulaire personnalisé en
  C#
url: /fr/net/programming-with-charts/how-to-create-word-document-with-a-customized-pie-chart-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer un document Word avec un graphique circulaire personnalisé en C#

Si vous devez **créer un document Word** de façon programmatique, ce tutoriel vous montre comment **insérer un graphique circulaire** et personnaliser ses étiquettes de données à l’aide d’Aspose.Words pour .NET. Vous apprendrez également à **générer un fichier Word** contenant un graphique entièrement stylisé, depuis la configuration du projet jusqu’à l’enregistrement du document final.

Le guide parcourt chaque étape nécessaire pour ajouter un graphique, ajuster la position des étiquettes, activer les lignes de repère, puis enregistrer le résultat sous forme de fichier `.docx`. Aucun outil externe n’est requis en dehors de la bibliothèque Aspose.Words, et le code source complet est fourni afin que vous puissiez le copier, le coller et l’exécuter immédiatement.

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

* SDK .NET 6.0 ou version ultérieure installé  
* Une licence valide d’Aspose.Words pour .NET (ou une clé d’évaluation gratuite)  
* Un IDE tel que Visual Studio 2022 ou Visual Studio Code  

Vous devrez également ajouter les packages NuGet suivants à votre projet :

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.Drawing.Charts
```

Ces packages exposent les classes `Document`, `DocumentBuilder` et les classes liées aux graphiques utilisées dans les exemples ci‑dessous.

## Créer un document Word et ajouter un graphique

La première étape consiste à **créer un document Word** et à obtenir un `DocumentBuilder` qui vous permet d’insérer du contenu. Le builder fonctionne comme un curseur positionné à l’intérieur du document.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

L’objet `Document` représente l’ensemble du fichier Word, tandis que le `DocumentBuilder` propose des méthodes telles que `InsertChart` qui placent des objets directement dans le flux du document.

## Insérer un graphique circulaire dans le document

Une fois le builder prêt, vous pouvez **insérer un graphique circulaire** avec une taille spécifique. Le graphique est ajouté à la position actuelle du builder.

```csharp
        // Step 3: Insert a pie chart with the desired size (400x300 points)
        Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

        // Populate the chart with sample data
        pieChart.Series.Clear();
        ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                                new[] { 25.0, 35.0, 20.0, 20.0 });
```

`InsertChart` renvoie un objet `Chart` que vous pouvez manipuler davantage. Les données d’exemple créent quatre parts représentant les ventes trimestrielles.

## Personnaliser les étiquettes de données du graphique circulaire

Pour rendre le graphique plus lisible, il est souvent nécessaire de **personnaliser les étiquettes du graphique circulaire** : les positionner à l’extérieur des parts et afficher des lignes de repère. C’est ici que la `ChartDataLabelCollection` entre en jeu.

```csharp
        // Step 4: Get the data label collection of the first series
        ChartDataLabelCollection dataLabels = pieChart.Series[0].DataLabels;

        // Step 5: Position the data labels outside each slice
        dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Step 6: Enable leader lines for clearer label connections
        dataLabels.ShowLeaderLines = true;

        // Optional: Show the actual value and percentage
        dataLabels.ShowValue = true;
        dataLabels.ShowPercentage = true;
```

Définir `Position` sur `OutsideEnd` déplace chaque étiquette au‑delà du bord de la part, tandis que `ShowLeaderLines` trace une ligne reliant l’étiquette à sa part. Les indicateurs optionnels `ShowValue` et `ShowPercentage` offrent aux lecteurs à la fois les valeurs brutes et les pourcentages relatifs.

**Astuce :** Si vous devez formater la police de l’étiquette, utilisez `dataLabels.Font` pour définir la taille, la couleur et le style. Cela garantit que le graphique correspond à l’identité visuelle de votre entreprise.

## Enregistrer et générer le fichier Word

Une fois le graphique entièrement configuré, vous pouvez **générer un fichier Word** en enregistrant l’instance `Document` sur le disque. Choisissez le format `.docx` pour une compatibilité maximale avec les versions récentes de Word.

```csharp
        // Step 7: Save the document with the customized chart
        string outputPath = @"C:\Temp\CustomPieChart.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Lorsque vous ouvrez `CustomPieChart.docx`, vous verrez un graphique circulaire avec quatre parts, chaque étiquette placée à l’extérieur de la part, reliée par des lignes de repère et affichant à la fois la valeur et le pourcentage.

![Screenshot of a Word document that contains a customized pie chart created with C#](image-placeholder.png)

*L’image montre le résultat final du tutoriel **create word document**.*

## Variantes courantes et cas limites

| Scénario | Comment adapter le code |
|----------|--------------------------|
| **Séries multiples** | Ajoutez des objets `ChartSeries` supplémentaires à `pieChart.Series`. Chaque série peut disposer de sa propre collection `DataLabels` pour un style indépendant. |
| **Taille du graphique différente** | Modifiez les paramètres de largeur et de hauteur dans `InsertChart(width, height)`. Les valeurs sont en points (1 pt ≈ 1/72 in). |
| **Titre du graphique** | Utilisez `pieChart.Title.Text = "Quarterly Sales"` pour ajouter un titre descriptif. |
| **Exportation en PDF** | Appelez `document.Save("Report.pdf", SaveFormat.Pdf);` après la création du graphique. |
| **Gestion de la licence** | Placez votre fichier de licence (`Aspose.Words.lic`) dans le dossier de l’application et chargez‑le avec `new License().SetLicense("Aspose.Words.lic");` avant de créer le document. |

Ces variantes vous permettent de répondre à la question **how to add pie chart** dans de nombreux scénarios réels, des rapports simples aux tableaux de bord complexes.

## Conclusion

Vous savez maintenant comment **créer un document Word**, **insérer un graphique circulaire** et **personnaliser les étiquettes du graphique circulaire** à l’aide d’Aspose.Words pour .NET. L’exemple complet montre un flux de travail clair : initialiser le document, ajouter un graphique, ajuster la position des étiquettes de données, activer les lignes de repère, puis **générer un fichier Word** pouvant être partagé avec n’importe qui.

Essayez d’étendre ce tutoriel en expérimentant avec d’autres types de graphiques (`ChartType.Column`, `ChartType.Line`) ou en appliquant des palettes de couleurs personnalisées pour correspondre à votre marque. En cas de problème, consultez la documentation d’Aspose.Words ou explorez des sujets connexes tels que « how to add pie chart » avec plusieurs séries et des sources de données dynamiques.

Bon codage, et n’hésitez pas à partager vos résultats ou à poser des questions complémentaires dans les commentaires !

## Que devriez‑vous apprendre ensuite ?


Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)
- [Insert Area Chart Into A Word Document](/words/english/net/programming-with-charts/insert-area-chart/)
- [Insert Scatter Chart in Word Document](/words/english/net/programming-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}