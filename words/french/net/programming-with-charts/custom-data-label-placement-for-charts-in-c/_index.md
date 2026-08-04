---
category: general
date: 2026-08-04
description: Le placement personnalisé des étiquettes de données pour les graphiques
  en C# vous permet de centrer les étiquettes sur les tranches du graphique. Suivez
  ce guide étape par étape en utilisant l'API de graphiques Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- Custom Data‑Label Placement for Charts
- chart data label positioning
- Aspose.Words chart API
- C# chart manipulation
- Word document chart automation
language: fr
lastmod: 2026-08-04
og_description: Placement personnalisé des étiquettes de données pour les graphiques
  en C# vous montre comment centrer toutes les étiquettes de données sur chaque tranche
  d’un graphique Word. Maîtrisez le positionnement des étiquettes de données de graphique
  avec Aspose.Words.
og_image_alt: Screenshot of a Word chart with centered data labels after applying
  C# code
og_title: Placement personnalisé des étiquettes de données pour les graphiques en
  C# – guide étape par étape
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Custom Data‑Label Placement for Charts in C# lets you center labels
    on chart slices. Follow this step‑by‑step guide using Aspose.Words chart API.
  headline: Custom Data‑Label Placement for Charts in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart
- Data Labels
title: Placement personnalisé des étiquettes de données pour les graphiques en C#
url: /fr/net/programming-with-charts/custom-data-label-placement-for-charts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Placement personnalisé des étiquettes de données pour les graphiques en C#

**Placement personnalisé des étiquettes de données pour les graphiques** vous permet de contrôler exactement où chaque étiquette apparaît sur un graphique dans un document Word. Dans ce tutoriel, vous apprendrez à centrer toutes les étiquettes de données sur chaque tranche à l’aide de C# et de l’API de graphiques Aspose.Words.

Vous obtiendrez un exemple complet et exécutable qui charge un fichier `.docx`, accède à la première forme de graphique, change la `Position` de chaque étiquette en `Center`, puis enregistre le document mis à jour. Aucune référence externe n’est requise – seulement la bibliothèque Aspose.Words for .NET et un environnement de développement C# de base.

**Ce que vous allez apprendre**

* Comment charger un document Word contenant un graphique.  
* Comment localiser la forme de graphique avec l’API de graphiques Aspose.Words.  
* Comment appliquer le **positionnement des étiquettes de données du graphique** à chaque série du graphique.  
* Comment enregistrer le document afin que les étiquettes centrées apparaissent dans Word.  

**Prérequis**

* .NET 6.0 (ou version ultérieure) installé.  
* Visual Studio 2022 (ou tout IDE C#).  
* Une référence au package NuGet `Aspose.Words`.  
* Un fichier Word (`Chart.docx`) contenant au moins un graphique.

---

## Placement personnalisé des étiquettes de données pour les graphiques – étape 1 : charger le document

La première action consiste à ouvrir le fichier Word qui contient le graphique. `Document` est le point d’entrée pour toute manipulation avec Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the source Word document.
Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

// Verify that the document actually contains a chart.
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
if (shapes.Count == 0)
{
    throw new InvalidOperationException("The document does not contain any shapes.");
}
```

*Pourquoi cette étape est importante* : Sans charger le document, vous ne pouvez pas accéder à l’objet graphique. La validation vous renvoie une erreur claire si le fichier ne contient pas de graphique, évitant ainsi une référence nulle plus tard.

---

## Utiliser l’API de graphiques Aspose.Words pour accéder aux formes de graphique

Aspose.Words traite un graphique comme un objet `Chart` imbriqué dans une `Shape`. Vous le récupérez en castant le nœud enfant approprié.

```csharp
// Get the first shape that is a chart.
Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (!chartShape.HasChart)
{
    throw new InvalidOperationException("The first shape is not a chart.");
}

// Extract the Chart instance.
Chart chart = chartShape.GetChart();
```

*Pourquoi cette étape est importante* : Accéder directement à `Chart` vous donne le contrôle complet sur les séries, les points de données et les propriétés des étiquettes. Si la forme n’est pas un graphique, le code s’arrête rapidement avec un message informatif.

---

## Définir le positionnement des étiquettes de données du graphique en C#

Parcourez maintenant chaque série et chaque étiquette de données, en définissant la `Position` sur `Center`. C’est le cœur du **Placement personnalisé des étiquettes de données pour les graphiques**.

```csharp
// Center all data labels on each slice of the chart.
foreach (Series series in chart.Series)
{
    foreach (ChartDataLabel label in series.DataLabels)
    {
        // Position enum values: Center, InsideEnd, OutsideEnd, etc.
        label.Position = ChartDataLabelPosition.Center;
    }
}
```

**Astuce** : Si vous avez besoin d’un placement différent (par ex., `InsideEnd` pour un graphique en colonnes), modifiez la valeur de l’énumération en conséquence. L’énumération `ChartDataLabelPosition` couvre toutes les positions standard prises en charge par Word.

*Pourquoi cette étape est importante* : Modifier `label.Position` met à jour la représentation OOXML sous‑jacente, de sorte que l’étiquette apparaisse centrée lorsque le document est ouvert dans Microsoft Word.

---

## Enregistrer le document Word avec les étiquettes mises à jour

Après avoir modifié le graphique, persistez les changements dans un fichier. Vous pouvez écraser l’original ou créer une nouvelle copie.

```csharp
// Save the modified document with centered labels.
doc.Save(@"YOUR_DIRECTORY\ChartLabelsCentered.docx");
```

*Pourquoi cette étape est importante* : L’enregistrement écrit le OOXML mis à jour sur le disque. L’ouverture de `ChartLabelsCentered.docx` dans Word affichera chaque étiquette de tranche centrée, confirmant que le **Placement personnalisé des étiquettes de données pour les graphiques** a réussi.

---

## Cas particuliers et variantes

| Situation | Comment gérer |
|-----------|---------------|
| **Graphiques multiples** dans le même document | Parcourez `doc.GetChildNodes(NodeType.Shape, true)` et vérifiez `shape.HasChart` pour chaque forme. |
| **Types de graphiques différents** (pie, doughnut, bar) | `ChartDataLabelPosition.Center` fonctionne pour les graphiques de type camembert. Pour les graphiques à barres/colonnes, vous préférerez peut‑être `InsideEnd` ou `OutsideEnd`. |
| **Le texte de l’étiquette nécessite un formatage** | Accédez à `label.TextProperties` pour définir la taille de police, la couleur ou le gras. |
| **Exécution sur .NET Core** | Assurez‑vous de référencer la version .NET Standard d’Aspose.Words ; l’API est identique. |

---

## Exemple complet fonctionnel

Voici le programme complet que vous pouvez copier‑coller dans une application console. Il inclut toutes les directives `using` nécessaires ainsi que la gestion des erreurs.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Path to the source and destination files.
        const string sourcePath = @"YOUR_DIRECTORY\Chart.docx";
        const string destPath   = @"YOUR_DIRECTORY\ChartLabelsCentered.docx";

        // Load the document.
        Document doc = new Document(sourcePath);

        // Find the first chart shape.
        Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (chartShape == null || !chartShape.HasChart)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Get the Chart object.
        Chart chart = chartShape.GetChart();

        // Center all data labels.
        foreach (Series series in chart.Series)
        {
            foreach (ChartDataLabel label in series.DataLabels)
            {
                label.Position = ChartDataLabelPosition.Center;
            }
        }

        // Save the updated document.
        doc.Save(destPath);
        Console.WriteLine($"Document saved with centered labels to: {destPath}");
    }
}
```

**Résultat attendu** : Ouvrez `ChartLabelsCentered.docx` dans Microsoft Word. Chaque tranche du graphique affiche maintenant son étiquette de données directement au centre de la tranche, offrant un rendu visuel plus épuré.

---

## Conclusion

Vous disposez maintenant d’une solution complète de **Placement personnalisé des étiquettes de données pour les graphiques** en C#. En chargeant le document, en accédant au graphique via l’API de graphiques Aspose.Words, en définissant `ChartDataLabelPosition.Center` pour chaque étiquette, puis en enregistrant le fichier, vous pouvez automatiser le positionnement des étiquettes pour tout graphique basé sur Word.

Ensuite, explorez d’autres options de **positionnement des étiquettes de données du graphique** telles que `InsideEnd` ou `OutsideEnd`, ou expérimentez la **manipulation de graphiques C#** pour changer les couleurs, ajouter des légendes ou générer des graphiques à partir de zéro. Ces extensions s’appuient directement sur les techniques présentées ici et élargissent vos compétences en automatisation de graphiques dans les documents Word. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Personnaliser les étiquettes de données du graphique](/words/english/net/programming-with-charts/chart-data-label/)
- [Formater le nombre d’étiquettes de données dans un graphique](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Étiquette de données du graphique](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}