---
category: general
date: 2026-09-08
description: Créez un document Word vierge et ajoutez un graphique à Word avec Aspose.Words.
  Apprenez comment insérer un graphique radar, activer les graduations et enregistrer
  le fichier.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add chart to word
- insert radar chart
- Aspose.Words chart
- C# Word automation
language: fr
lastmod: 2026-09-08
og_description: Créer un document Word vierge et ajouter un graphique à Word à l’aide
  d’Aspose.Words. Ce tutoriel montre comment insérer un graphique radar, configurer
  les axes et enregistrer le document.
og_image_alt: Radar chart inserted into a blank Word document created with C#
og_title: Créer un document Word vierge et ajouter un graphique radar – guide étape
  par étape
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: create blank Word document and add chart to Word with Aspose.Words.
    Learn how to insert radar chart, enable graduations, and save the file.
  headline: How to create blank Word document and add chart to Word
  type: TechArticle
tags:
- Word
- C#
- Aspose.Words
- Chart
title: Comment créer un document Word vierge et ajouter un graphique à Word
url: /fr/net/programming-with-charts/how-to-create-blank-word-document-and-add-chart-to-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer un document Word vierge et ajouter un graphique à Word

Si vous devez **créer un document Word vierge** pour un rapport, un modèle ou une fusion de courrier automatisée, ce guide vous accompagne pas à pas avec C# et Aspose.Words. Vous apprendrez également comment **ajouter un graphique à Word**, en particulier comment **insérer un graphique radar**, activer les graduations et enregistrer le résultat au format .docx.

Ce tutoriel couvre tout, de la configuration du projet à l’étape de vérification finale. À la fin, vous disposerez d’un extrait de code réutilisable que vous pourrez intégrer dans n’importe quelle application .NET. Aucune expérience préalable avec Aspose.Words n’est requise, mais vous devez connaître les bases de C# et disposer d’un SDK .NET récent installé.

## Prérequis

- SDK .NET 6.0 ou ultérieur  
- Aspose.Words for .NET (package NuGet `Aspose.Words`)  
- Un IDE tel que Visual Studio 2022 ou VS Code  
- Permission d’écriture dans le dossier où le document sera enregistré  

Vous pouvez installer la bibliothèque avec la commande suivante :

```bash
dotnet add package Aspose.Words
```

## Étape 1 : Créer un document Word vierge

La première étape consiste à **créer un document Word vierge** en mémoire. La classe `Document` représente le fichier complet, tandis que `DocumentBuilder` fournit une API fluide pour ajouter du contenu.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

public class RadarChartDemo
{
    public static void Main()
    {
        // Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` commence vide, vous avez donc une toile propre sur laquelle placer le graphique. Garder le document vierge à ce stade facilite la réutilisation du même code pour différents modèles.

## Étape 2 : Ajouter un graphique à Word

Ensuite, nous **ajoutons un graphique à Word** en appelant `InsertChart`. La méthode nécessite le type de graphique et les dimensions souhaitées en points (1 point = 1/72 pouce).

```csharp
        // Insert a radar (radial) chart with a defined size
        Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

`ChartType.Radar` indique à Aspose.Words de générer un graphique radial, idéal pour afficher des données multivariées dans une disposition circulaire. Les valeurs de taille (400 × 300) conviennent à la plupart des pages en portrait, mais vous pouvez les ajuster selon votre mise en page.

## Étape 3 : Insérer le graphique radar et configurer les graduations

Nous **insérons le graphique radar** et activons les graduations (ticks) sur les axes catégorie (X) et valeur (Y). Les graduations améliorent la lisibilité en affichant les positions exactes de chaque point de donnée.

```csharp
        // Turn on graduations for both axes
        radarChart.AxisX.HasGraduations = true;   // radial (category) axis
        radarChart.AxisY.HasGraduations = true;   // value axis

        // Optional: define a custom graduation step for the radial axis
        radarChart.AxisX.GraduationStep = 10;
```

Définir `HasGraduations` à `true` trace des marques de graduation sur les axes. L’option `GraduationStep` contrôle l’espacement entre les graduations sur l’axe radial ; un pas de 10 signifie une graduation tous les 10 degrés.

### Astuce
Si vous devez afficher des étiquettes de données, appelez `radarChart.Series[0].HasDataLabel = true;`. Cela ajoute la valeur numérique à côté de chaque point, ce qui est utile pour les présentations.

## Étape 4 : Remplir le graphique avec des données d’exemple (facultatif)

Un graphique radar sans données est invisible. Voici une façon rapide d’ajouter une série de valeurs d’exemple. Vous pouvez remplacer ce bloc par votre propre source de données.

```csharp
        // Add a series with sample data
        radarChart.Series.Clear(); // Remove any default series
        var series = radarChart.Series.Add("Performance", "Category");
        series.Add(30);
        series.Add(55);
        series.Add(70);
        series.Add(45);
        series.Add(90);
```

Chaque appel à `Add` insère un point dans la série. L’ordre des points correspond aux positions angulaires autour du cercle.

## Étape 5 : Enregistrer le document contenant le graphique

Enfin, stockez le document sur le disque. La méthode `Save` écrit automatiquement le fichier .docx, en conservant le graphique et toute la mise en forme.

```csharp
        // Save the document to a file
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadarChart.docx");
        document.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

L’exécution du programme crée un **document Word vierge** qui contient maintenant un graphique radar pleinement fonctionnel. Ouvrez le fichier dans Microsoft Word pour voir le résultat.

![Radar chart in Word document](radar_chart.png){alt="Graphique radar inséré dans un document Word vierge"}

## Variations courantes et cas limites

| Situation | Ce qu’il faut modifier |
|-----------|------------------------|
| **Taille de graphique différente** | Ajustez les paramètres de largeur/hauteur de `InsertChart`. |
| **Autres types de graphiques** | Remplacez `ChartType.Radar` par `ChartType.Column`, `ChartType.Pie`, etc., en conservant la même logique de graduation. |
| **Enregistrement dans un flux** | Utilisez `document.Save(Stream, SaveFormat.Docx)` |

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Insérer un graphique en aires dans un document Word | Aspose.Words pour .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Créer un graphique de dispersion Word en utilisant Aspose.Words pour .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Insérer un graphique en colonnes dans Word en utilisant Aspose.Words pour .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}