---
category: general
date: 2026-10-20
description: Créer un diagramme circulaire dans un document Word avec Aspose.Words
  – guide étape par étape montrant comment définir la couleur, éclater une tranche
  et enregistrer le document Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save word document
- how to create chart
- how to explode slice
- how to set color
language: fr
lastmod: 2026-10-20
og_description: Créer un diagramme circulaire dans un document Word avec Aspose.Words.
  Apprenez comment définir la couleur, faire exploser une part et enregistrer le document
  Word dans un exemple unique et exécutable.
og_image_alt: Screenshot of a Word document containing a customized pie chart with
  an exploded red slice
og_title: Créer un diagramme circulaire dans un document Word – guide complet C#
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create pie chart in a Word document using Aspose.Words – step‑by‑step
    guide that shows how to set color, explode slice, and save Word document.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart automation
title: Comment créer un diagramme circulaire dans un document Word avec Aspose.Words
url: /fr/java/images-shapes/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer un diagramme circulaire dans un document Word avec Aspose.Words

Si vous devez **créer un diagramme circulaire** dans un fichier Word, ce guide vous montre exactement comment le faire. Vous verrez comment définir une couleur personnalisée, « exploser » une tranche pour la mettre en évidence, et enfin **enregistrer le document Word** avec le diagramme intégré.

Générer des diagrammes par programme supprime les étapes manuelles d’ouverture de Word, d’insertion d’un diagramme et de réglage de son apparence. À la fin de ce tutoriel, vous disposerez d’une application console C# complète et exécutable qui crée un diagramme circulaire, le personnalise et écrit le résultat sur le disque.

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

* le SDK .NET 6.0 ou une version ultérieure installé  
* une licence valide d’Aspose.Words for .NET (ou une clé d’évaluation gratuite)  
* un IDE tel que Visual Studio 2022 ou VS Code  

Aucun package NuGet supplémentaire n’est requis au‑delà de `Aspose.Words`.

## Comment créer un diagramme circulaire dans un document Word

La première étape consiste à instancier un `Document` et un `DocumentBuilder`. Le builder vous donne accès aux fonctionnalités de haut niveau de Word, y compris l’insertion de diagrammes.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a blank document and a builder.
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Step 2: Insert a 400x300‑point pie chart.
            Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data.
            // Series 0, Category 0‑2 correspond to three slices.
            pieChart.Series[0].DataPoints.Clear();
            pieChart.Series[0].DataPoints.Add(30); // Slice A
            pieChart.Series[0].DataPoints.Add(45); // Slice B
            pieChart.Series[0].DataPoints.Add(25); // Slice C

            // The chart is now part of the document; further customization follows.
```

À ce stade, le document contient déjà un diagramme circulaire de base. Les sections suivantes expliquent **comment exploser une tranche**, **comment définir une couleur**, et **comment enregistrer le document Word**.

## Comment exploser une tranche pour la mettre en évidence

« Exploser » une tranche la sépare du reste du diagramme, attirant ainsi le regard du lecteur. L’API Aspose.Words vous permet de spécifier une distance d’explosion en points.

```csharp
            // Step 3: Explode the first slice (index 0) by 20 points.
            // This moves the slice outward while keeping the rest of the chart intact.
            pieChart.Series[0].SetExplosion(0, 20);
```

Pourquoi exploser la tranche ? Dans les rapports qui mettent en avant une catégorie particulière — par exemple « Produit le plus vendu » — la séparation visuelle rend le point de données immédiatement reconnaissable.

## Comment définir une couleur sur une tranche du diagramme

Les couleurs personnalisées améliorent la cohérence de la marque et la lisibilité. Vous pouvez attribuer n’importe quel `System.Drawing.Color` à un point de données spécifique.

```csharp
            // Step 4: Apply a red fill to the same slice we just exploded.
            // The Fill property controls the interior color of the slice.
            pieChart.Series[0].DataPoints[0].Fill.ForeColor = Color.Red;
```

Vous n’êtes pas limité aux couleurs prédéfinies ; vous pouvez créer une valeur `Color.FromArgb` pour des nuances précises.

## Comment enregistrer le document Word avec le diagramme

Une fois le diagramme à votre goût, persister le fichier est simple. La méthode `Document.Save` écrit le document dans le format que vous spécifiez — ici nous utilisons le `.docx` par défaut.

```csharp
            // Step 5: Save the document to the desired location.
            string outputPath = @"C:\Temp\PieChart.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

L’exécution du programme crée `PieChart.docx`. L’ouverture du fichier dans Microsoft Word affiche un diagramme circulaire où la première tranche est explosée et colorée en rouge, exactement comme le code le spécifie.

### Résultat attendu

* Un fichier Word nommé **PieChart.docx** dans `C:\Temp`.  
* Le document contient un seul diagramme circulaire, de taille 400 × 300 points.  
* La tranche 0 est décalée de 20 points et remplie en rouge, tandis que les autres tranches conservent la couleur par défaut.  

Vous pouvez vérifier l’explosion et la couleur en sélectionnant le diagramme dans Word et en inspectant les propriétés de la tranche.

## Astuces professionnelles et pièges courants

* **Astuce pro :** Si vous devez modifier le titre du diagramme ou la légende, utilisez les propriétés `pieChart.Title.Text` et `pieChart.Legend` avant d’enregistrer.  
* **Attention à :** Oublier de vider les points de données par défaut peut entraîner des tranches supplémentaires indésirables. Appelez toujours `Series[0].DataPoints.Clear()` avant d’ajouter vos propres données.  
* **Conseil de performance :** Pour les gros documents, réutilisez une seule instance de `DocumentBuilder` au lieu de créer de nombreux builders ; cela réduit la consommation de mémoire.

## Comment créer un diagramme avec Aspose.Words (contexte supplémentaire)

La méthode `InsertChart` prend en charge de nombreux types de diagrammes en plus des diagrammes circulaires, tels que les diagrammes en colonnes, en lignes et en aires. Pour passer à un autre type, remplacez `ChartType.Pie` par la valeur d’énumération souhaitée, par exemple `ChartType.Column`. Le reste des étapes de personnalisation (explosion des tranches, définition des couleurs) suit le même schéma, bien que tous les types de diagrammes n’exposent pas une propriété « explosion ».

## Comment exploser une tranche dans d’autres types de diagrammes

Seuls les diagrammes de type circulaire exposent la méthode `SetExplosion`. Si vous essayez de l’appeler sur un diagramme à barres, l’API lève une `ArgumentException`. Dans ces cas, envisagez d’utiliser des étiquettes de données ou des bulles d’appel pour mettre en évidence une barre particulière.

## Comment définir une couleur sur une série plutôt que sur une seule tranche

Si vous voulez que chaque tranche d’une série partage la même couleur, parcourez les points de données :

```csharp
foreach (ChartDataPoint point in pieChart.Series[0].DataPoints)
{
    point.Fill.ForeColor = Color.Blue;
}
```

Cette approche est pratique lorsque vous avez besoin d’un schéma de couleurs uniforme sur plusieurs diagrammes.

## Comment enregistrer le document Word dans d’autres formats

Aspose.Words peut exporter vers PDF, HTML et de nombreux autres formats. Changez l’extension du fichier dans `Save` et, éventuellement, passez un objet `SaveOptions` :

```csharp
document.Save(@"C:\Temp\PieChart.pdf", SaveFormat.Pdf);
```

Le moteur de rendu du diagramme convertit automatiquement le diagramme vers le format cible, en conservant les couleurs et les réglages d’explosion.

## Conclusion

Vous savez maintenant comment **créer un diagramme circulaire** dans un document Word, personnaliser son apparence en **explosant une tranche** et en **définissant une couleur**, puis **enregistrer le document Word** avec le diagramme intégré. Cet exemple de bout en bout vous fournit une base solide pour automatiser la génération de rapports, de tableaux de bord ou tout autre scénario où des données visuelles doivent être insérées par programme.

### Prochaines étapes

* Explorez d’autres types de diagrammes (`ChartType.Column`, `ChartType.Line`) pour élargir votre boîte à outils de reporting.  
* Combinez plusieurs diagrammes dans un même document afin de créer des tableaux de bord complets.  
* Expérimentez avec `ChartDataLabel` pour afficher les pourcentages ou les valeurs directement sur les tranches.  

N’hésitez pas à adapter le code à vos propres sources de données — que vous extrayiez les valeurs d’une base de données, d’une API ou d’un fichier CSV, le même flux de travail Aspose.Words s’applique. Bon diagrammage !


## Que devez‑vous apprendre ensuite ?


Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications pas à pas pour vous aider à maîtriser des fonctionnalités supplémentaires de l’API et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Explode Pie Chart Slice in C# with Aspose.Words – Full Guide](/words/english/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/)
- [Insert Custom Column Chart in Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/insert-custom-chart/)
- [Update Chart Series Data in a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}