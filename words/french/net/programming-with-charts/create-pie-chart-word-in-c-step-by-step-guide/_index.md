---
category: general
date: 2026-08-07
description: Créer rapidement un diagramme circulaire dans Word avec C#. Apprenez
  à insérer un diagramme circulaire, ajouter des étiquettes de données, afficher le
  pourcentage du diagramme et personnaliser les étiquettes de données du diagramme.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- show percentage chart
- add data labels pie
- insert pie chart
- customize chart data labels
language: fr
lastmod: 2026-08-07
og_description: Créer un diagramme circulaire Word en C# avec Aspose.Words. Ce tutoriel
  montre comment insérer un diagramme circulaire, ajouter des étiquettes de données,
  et afficher les pourcentages tout en personnalisant les étiquettes du graphique.
og_image_alt: Word document displaying a pie chart with percentage labels outside
  each slice
og_title: Créer un diagramme circulaire en C# – tutoriel complet
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  headline: Create pie chart word in C# – step‑by‑step guide
  type: TechArticle
- description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  name: Create pie chart word in C# – step‑by‑step guide
  steps:
  - name: Call `chart.Series.Add()` for each additional series.
    text: Call `chart.Series.Add()` for each additional series.
  - name: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
    text: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
  - name: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
    text: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
  type: HowTo
tags:
- pie chart
- C#
- Aspose.Words
- chart customization
title: Créer un graphique circulaire Word en C# – guide étape par étape
url: /fr/net/programming-with-charts/create-pie-chart-word-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un pie chart word en C# – guide étape par étape

Si vous avez besoin de **create pie chart word** documents en C#, ce guide fournit une solution complète, prête à l'exécution. Vous verrez comment **insert pie chart**, **add data labels pie**, et **show percentage chart** tout en **customize chart data labels** pour un rendu soigné.

Générer des graphiques de manière programmatique vous évite la modification manuelle, surtout lorsque des rapports ou tableaux de bord doivent être produits automatiquement. Dans les sections ci‑dessous, vous apprendrez tout ce qui est nécessaire pour intégrer un diagramme circulaire entièrement étiqueté dans un fichier Word en utilisant Aspose.Words pour .NET.

## Prérequis et configuration

* .NET 6.0 SDK ou version ultérieure installé.  
* Une licence valide d'Aspose.Words pour .NET (ou une clé d'évaluation temporaire).  
* Visual Studio 2022 (ou tout IDE supportant C#).  

Ajoutez le package NuGet Aspose.Words à votre projet :

```bash
dotnet add package Aspose.Words
```

> **Astuce :** Si vous prévoyez de générer de nombreux graphiques, activez le mode **Free‑Form Drawing** (`DocumentBuilder.UseFreeFormDrawing = true`) pour de meilleures performances.

## Créer un pie chart word avec Aspose.Words

La première étape majeure consiste à créer un document Word vierge et un `DocumentBuilder`. Cet objet pilote toutes les insertions suivantes.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new blank document and a DocumentBuilder
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Pourquoi c’est important* : `Document` représente le fichier `.docx` complet, tandis que `DocumentBuilder` offre une API fluide pour ajouter des paragraphes, des tableaux et des graphiques. Commencer avec un document vierge garantit qu'aucun formatage caché n'interfère avec la mise en page du graphique.

## Insérer un pie chart dans le document

Nous plaçons maintenant un pie chart de la taille souhaitée. La méthode `InsertChart` renvoie un objet `Chart` que nous pouvons configurer davantage.

```csharp
// Step 2: Insert a pie chart of the desired size
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

*Pourquoi c’est important* : le drapeau `ChartType.Pie` indique à Aspose.Words de générer un graphique circulaire. La largeur (`400`) et la hauteur (`300`) sont exprimées en points, vous offrant un contrôle précis sur l'encombrement visuel.

## Remplir le graphique avec des données

Un pie chart nécessite au moins une série de valeurs numériques. Ici, nous ajoutons trois catégories : « Apples », « Bananas » et « Cherries ».

```csharp
// Populate the first series with sample data
chart.Series[0].AddCategory("Apples", 40);
chart.Series[0].AddCategory("Bananas", 35);
chart.Series[0].AddCategory("Cherries", 25);
```

*Pourquoi c’est important* : chaque appel `AddCategory` crée une tranche. La valeur numérique détermine la taille de la tranche, tandis que l’étiquette devient le nom de la catégorie affiché lorsque les étiquettes de données sont activées.

## Ajouter des étiquettes de données pie et afficher le pourcentage du graphique

Pour rendre le graphique informatif, nous activons les étiquettes de données, les positionnons à l'extérieur des tranches, et demandons à Aspose.Words d'afficher à la fois le nom de la catégorie et le pourcentage.

```csharp
// Step 3: Access the first series' data label collection
ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;

// Step 4: Position labels outside the slices and show useful information
labels.Position = ChartDataLabelPosition.OutsideEnd; // places label outside each slice
labels.ShowCategoryName = true;                     // displays "Apples", "Bananas", …
labels.ShowPercentage = true;                       // displays "40%" etc.
```

*Pourquoi c’est important* : définir `Position` à `OutsideEnd` améliore la lisibilité, surtout lorsque les tranches sont petites. Activer `ShowCategoryName` et `ShowPercentage` répond à l'exigence **show percentage chart** et satisfait l'objectif **add data labels pie**.

## Personnaliser davantage les étiquettes de données du graphique (optionnel)

Vous pouvez souhaiter changer la police, ajouter une ligne de repère, ou masquer la légende. L'extrait suivant montre des personnalisations courantes :

```csharp
// Optional: customize label font and leader lines
labels.Font.Size = 10;
labels.Font.Color = System.Drawing.Color.DarkBlue;
labels.ShowLeaderLines = true;

// Optional: hide the default legend because labels already contain the needed info
chart.HasLegend = false;
```

*Pourquoi c’est important* : personnaliser l'apparence des étiquettes garantit que le graphique correspond au guide de style de votre document. Supprimer la légende réduit l'encombrement visuel lorsque les étiquettes de données transmettent déjà la même information.

## Enregistrer le document avec le graphique personnalisé

Enfin, écrivez le document sur le disque. Choisissez un chemin auquel vous avez les droits d'écriture.

```csharp
// Step 5: Save the document with the customized chart
doc.Save("YOUR_DIRECTORY/ChartWithCustomLabels.docx");
```

Lorsque vous ouvrez `ChartWithCustomLabels.docx` dans Microsoft Word, vous verrez un pie chart où chaque tranche est étiquetée avec son nom de catégorie et son pourcentage, positionnée à l'extérieur de la tranche, et stylisée avec les paramètres de police personnalisés.

### Résultat attendu

| Tranche | Valeur | Pourcentage | Étiquette affichée dans Word |
|---------|--------|-------------|------------------------------|
| Apples  | 40    | 40 %       | Apples – 40 %       |
| Bananas | 35    | 35 %       | Bananas – 35 %      |
| Cherries| 25    | 25 %       | Cherries – 25 %     |

Le graphique devrait ressembler à l'illustration ci‑dessous :

![Document Word affichant un pie chart avec des étiquettes de pourcentage à l'extérieur de chaque tranche](pie-chart-word.png "Exemple de création de pie chart word")

*Le texte alternatif de l'image inclut le mot‑clé principal pour le SEO.*

## Gestion de plusieurs séries et cas limites

L'exemple de base utilise une seule série, ce qui est typique pour un pie chart. Si vous devez afficher plusieurs séries (par ex., comparer deux années), vous devez :

1. Appeler `chart.Series.Add()` pour chaque série supplémentaire.  
2. S'assurer que chaque série utilise les mêmes catégories ; sinon, Aspose.Words lèvera une `ArgumentException`.  
3. Optionnellement, définir `labels.ShowSeriesName = true` pour différencier les tranches.

```csharp
// Adding a second series (e.g., sales in 2025)
chart.Series.Add("2025");
chart.Series[1].AddCategory("Apples", 45);
chart.Series[1].AddCategory("Bananas", 30);
chart.Series[1].AddCategory("Cherries", 25);
```

Lorsque plusieurs séries existent, le graphique se rend automatiquement comme un **clustered pie** (également appelé « pie of pies »). Vérifiez la sortie pour vous assurer que les étiquettes restent lisibles.

## Problèmes courants et comment les éviter

| Problème | Cause | Solution |
|----------|-------|----------|
| Les étiquettes se chevauchent les tranches | Zone du graphique trop petite ou trop de catégories | Augmenter les dimensions du graphique (`InsertChart(width, height)`) ou changer `Position` en `InsideEnd`. |
| Les pourcentages ne totalisent pas 100 % | Erreurs d'arrondi dans les données | Utiliser `labels.ShowPercentage = true` (Aspose.Words normalise automatiquement). |
| Le graphique apparaît vide dans Word | Licence manquante ou expiration de la période d'évaluation | Vérifiez qu'une licence Aspose.Words valide est chargée avant de créer le document. |
| Les couleurs de police diffèrent du thème Word | Police personnalisée définie dans le code | Supprimer les paramètres de police personnalisés ou correspondre aux couleurs du thème Word (`System.Drawing.Color.Black`). |

## Code source complet (exécutable)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Load license (optional for evaluation)
        // License license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert a pie chart
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 3. Add data to the first series
        chart.Series[0].AddCategory("Apples", 40);
        chart.Series[0].AddCategory("Bananas", 35);
        chart.Series[0].AddCategory("Cherries", 25);

        // 4. Configure data labels
        ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;
        labels.Position = ChartDataLabelPosition.OutsideEnd;
        labels.ShowCategoryName = true;
        labels.ShowPercentage = true;

        // Optional: further customization
        labels.Font.Size = 10;
        labels.Font.Color = Color.DarkBlue;
        labels.ShowLeaderLines = true;
        chart.HasLegend = false;

        // 5. Save the document
        doc.Save("ChartWithCustomLabels.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

L'exécution du programme génère `ChartWithCustomLabels.docx`, qui contient un exemple **create pie chart word** répondant à toutes les exigences listées dans le tutoriel.

## Conclusion

Vous savez maintenant comment **create pie chart word** des documents en C# en utilisant Aspose.Words. Le guide a couvert l'insertion d'un pie chart, **add data labels pie**, **show percentage chart**, et **customize chart data labels** pour obtenir un fichier Word professionnel et axé sur les données.  

À partir de là, vous pouvez explorer des sujets connexes tels que **insert pie chart** dans des paragraphes existants, générer des graphiques **bar** ou **line**, ou automatiser la création en lot de rapports avec des jeux de données variables. Expérimentez différentes positions d'étiquettes, styles de police et configurations multi‑séries pour adapter la sortie à vos besoins spécifiques de reporting.

Bon graphique !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Personnaliser les étiquettes de données du graphique](/words/english/net/programming-with-charts/chart-data-label/)
- [Définir les options par défaut pour les étiquettes de données dans un graphique](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Insérer un graphique en colonnes dans un document Word](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}