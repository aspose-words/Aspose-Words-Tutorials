---
category: general
date: 2026-09-14
description: Insérer un graphique radar dans Word avec C#. Apprenez à définir le titre
  du graphique, à ajouter plusieurs séries et à créer le graphique programmatiquement
  en quelques lignes seulement.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert radar chart
- set chart title
- create radar chart word
- multiple series radar chart
- create chart programmatically
language: fr
lastmod: 2026-09-14
og_description: Insérer un graphique radar dans Word avec C#. Ce tutoriel montre comment
  définir le titre du graphique, ajouter plusieurs séries et créer le graphique de
  manière programmatique.
og_image_alt: Screenshot of a Word document displaying a radar chart with sales data
og_title: Insérer un graphique radar dans Word avec C# – guide de programmation rapide
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Insert radar chart in Word with C#. Learn how to set chart title, add
    multiple series, and create the chart programmatically in just a few lines.
  headline: Insert radar chart in Word using C# – step‑by‑step guide
  type: TechArticle
tags:
- radar chart
- C#
- Aspose.Words
title: Insérer un graphique radar dans Word avec C# – guide étape par étape
url: /fr/net/programming-with-charts/insert-radar-chart-in-word-using-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insérer un graphique radar dans Word avec C# – guide étape par étape

Si vous devez **insérer un graphique radar** dans un document Word, ce guide vous montre comment le faire de manière programmatique avec C#. Vous apprendrez également à **définir le titre du graphique**, ajouter un **graphique radar à séries multiples**, et enregistrer le fichier sans quitter votre IDE.

Le tutoriel couvre tout, de la configuration du projet à l’appel final `doc.Save`, afin que vous puissiez copier‑coller l’exemple complet et l’exécuter immédiatement. Aucune recherche dans une documentation externe n’est nécessaire.

## Prérequis

* .NET 6 (ou version ultérieure) installé.
* Une licence valide d’Aspose.Words for .NET (ou une clé d’évaluation temporaire).
* Visual Studio 2022 ou tout IDE C# de votre choix.

> **Astuce :** Si vous utilisez la version d’essai gratuite, pensez à définir la licence avant la première création de `Document` afin d’éviter le filigrane d’évaluation.

## Étape 1 : Insérer un graphique radar dans un document Word

La première opération consiste à créer un nouveau `Document` et un `DocumentBuilder`. Le builder vous donne accès au contenu du document et vous permet de placer un **graphique radar** exactement où vous le souhaitez.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Create a new blank Word document.
Document doc = new Document();

// DocumentBuilder provides methods to insert content.
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a radar (radial) chart at the current cursor position.
Chart chart = builder.InsertChart(ChartType.Radar);
```

*Pourquoi cette étape est importante :* `InsertChart` crée un objet graphique que vous pouvez configurer entièrement avant d’enregistrer le document. Utiliser `ChartType.Radar` indique à Word de rendre un graphique radial au lieu d’un graphique à colonnes ou en lignes.

## Étape 2 : Définir le titre du graphique et les graduations des axes

Un graphique sans titre peut prêter à confusion. Ici, nous **définissons le titre du graphique** à « Sales Radar » et activons les graduations sur les deux axes (disponibles à partir d’Aspose.Words 24.9).

```csharp
// Give the chart a meaningful title.
chart.Title.Text = "Sales Radar";

// Enable graduations (grid lines) on both X and Y axes.
chart.AxisX.HasGraduations = true;
chart.AxisY.HasGraduations = true;
```

*Pourquoi cette étape est importante :* Le titre fournit un contexte aux lecteurs, et les graduations améliorent la lisibilité en montrant où chaque point de données se situe sur l’échelle.

## Étape 3 : Créer plusieurs séries pour le graphique radar

Un **graphique radar à séries multiples** vous permet de comparer différentes périodes côte à côte. Ci‑dessus, nous ajoutons deux séries — Q1 et Q2—chacune avec trois points de données.

```csharp
// Series 1: Q1 data.
chart.Series.Add(
    "Q1",                                 // Series name
    new[] { "Jan", "Feb", "Mar" },        // Category labels
    new[] { 10, 20, 30 }                  // Values
);

// Series 2: Q2 data.
chart.Series.Add(
    "Q2",
    new[] { "Jan", "Feb", "Mar" },
    new[] { 15, 25, 35 }
);
```

*Pourquoi cette étape est importante :* Ajouter plusieurs séries montre comment comparer des ensembles de données sur le même radar, un besoin fréquent pour les ventes, la performance ou les résultats d’enquêtes.

## Étape 4 : Enregistrer le document Word de façon programmatique

Enfin, vous **créez le graphique de façon programmatique** et persistez le document sur le disque. La méthode `Save` écrit un fichier `.docx` qui peut être ouvert dans Microsoft Word.

```csharp
// Define the output path. Adjust the directory as needed.
string outputPath = Path.Combine(
    Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
    "RadialGraduations.docx"
);

// Save the document containing the radar chart.
doc.Save(outputPath);
```

Lorsque vous ouvrez `RadialGraduations.docx`, vous verrez un graphique radar intitulé « Sales Radar » avec deux séries (Q1 et Q2) tracées par rapport aux mois Jan‑Mar.

### Résultat attendu

![Radar chart in Word](https://example.com/radar-chart.png){: .align-center alt="Document Word affichant un graphique radar avec deux séries de données"}

La capture d’écran (ou le fichier réel) confirme que le graphique a été inséré, titré et rempli correctement.

## Exemple complet et exécutable

En rassemblant tous les éléments, voici un programme autonome que vous pouvez compiler et exécuter :

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1. Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert a radar chart.
        Chart chart = builder.InsertChart(ChartType.Radar);

        // 3. Set chart title and enable axis graduations.
        chart.Title.Text = "Sales Radar";
        chart.AxisX.HasGraduations = true;
        chart.AxisY.HasGraduations = true;

        // 4. Add two data series.
        chart.Series.Add("Q1", new[] { "Jan", "Feb", "Mar" }, new[] { 10, 20, 30 });
        chart.Series.Add("Q2", new[] { "Jan", "Feb", "Mar" }, new[] { 15, 25, 35 });

        // 5. Save the document.
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadialGraduations.docx"
        );
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Exécutez le programme, ouvrez le fichier généré, et vérifiez que l’opération **insérer un graphique radar** a réussi.

## Questions fréquentes & cas particuliers

| Question | Réponse |
|----------|--------|
| **Puis-je changer le type de graphique après l’insertion ?** | Oui. Après `InsertChart`, attribuez un nouveau `ChartType` à `chart.Type`. Cependant, créer le graphique avec le type correct dès le départ est plus efficace. |
| **Et si j’ai besoin de plus de deux séries ?** | Appelez `chart.Series.Add` pour chaque série supplémentaire. Le graphique ajustera automatiquement la légende et les couleurs. |
| **Comment personnaliser les couleurs ou les marqueurs ?** | Utilisez `chart.Series[i].Format.Fill.ForeColor` pour les couleurs de remplissage et `chart.Series[i].Marker` pour les styles de marqueur. |
| **L’API est‑elle compatible avec .NET Framework ?** | Le même code fonctionne avec .NET Framework 4.7+ ; il suffit de référencer le DLL Aspose.Words approprié. |
| **Et si j’utilise une version plus ancienne d’Aspose.Words ?** | Les graduations (`HasGraduations`) ont été introduites dans la version 24.9. Pour les versions antérieures, vous pouvez ajouter manuellement des lignes de grille en utilisant `chart.AxisX.MajorGridLines` et `chart.AxisY.MajorGridLines`. |

## Conclusion

Vous savez maintenant comment **insérer un graphique radar** dans un document Word avec C#, **définir le titre du graphique**, ajouter un **graphique radar à séries multiples**, et **créer le graphique de façon programmatique**. Cette solution de bout en bout vous permet d’automatiser les rapports, les tableaux de bord, ou tout scénario nécessitant une comparaison visuelle de catégories.

Ensuite, explorez des sujets connexes tels que **personnaliser les couleurs du graphique**, **exporter les graphiques en images**, ou **intégrer des graphiques dans des fichiers PDF**. Expérimentez avec différents ensembles de données pour voir comment la visualisation radar s’adapte.

Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Insérer un graphique en colonnes dans Word avec Aspose.Words pour .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insérer un graphique à bulles dans Word avec Aspose.Words pour .NET](/words/english/net/working-with-charts/insert-bubble-chart/)
- [Insérer un graphique en aires dans un document Word | Aspose.Words pour .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}