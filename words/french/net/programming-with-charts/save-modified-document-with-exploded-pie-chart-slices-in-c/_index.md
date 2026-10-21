---
category: general
date: 2026-10-13
description: 'Enregistrer le document modifié après avoir personnalisé un diagramme
  circulaire : éclater les parts, modifier l’angle de la première part et afficher
  les libellés de pourcentage en C#.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save modified document
- show percentage labels
- explode pie chart slices
- display percentages pie
- change first slice
language: fr
lastmod: 2026-10-13
og_description: Sauvegardez le document modifié après avoir personnalisé un graphique
  circulaire en C#. Apprenez à faire exploser les tranches du graphique, à modifier
  l'angle de la première tranche et à afficher les libellés de pourcentage.
og_image_alt: Screenshot of a Word document where the pie chart slices are exploded
  and percentage labels are displayed after saving the modified document
og_title: Enregistrer le document modifié avec des tranches de diagramme circulaire
  éclatées – Guide C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: 'Save modified document after customizing a pie chart: explode slices,
    change first slice angle, and show percentage labels in C#.'
  headline: Save modified document with exploded pie chart slices in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word chart
- pie chart
- document manipulation
title: Enregistrer le document modifié avec des tranches de diagramme circulaire éclatées
  en C#
url: /fr/net/programming-with-charts/save-modified-document-with-exploded-pie-chart-slices-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Enregistrer le document modifié avec des tranches de diagramme circulaire éclatées en C#

Si vous devez **enregistrer le document modifié** après avoir ajusté un diagramme circulaire Word, ce guide vous montre exactement comment. Vous apprendrez à éclater les tranches du diagramme circulaire, à changer l'angle de la première tranche et à afficher les libellés de pourcentage — le tout en quelques lignes de code C#.

Personnaliser les graphiques est une exigence courante lors de la génération de rapports, factures ou tableaux de bord de manière programmatique. À la fin de ce tutoriel, vous serez capable de charger un fichier DOCX, de modifier l'apparence du graphique et d'**enregistrer le document modifié** prêt à être distribué.

## Prérequis

- .NET 6.0 ou ultérieur (le code fonctionne également avec .NET Framework 4.6+)
- Aspose.Words for .NET 23.10 ou plus récent (version d'essai gratuite ou copie sous licence)
- Un fichier Word (`input.docx`) contenant un seul diagramme circulaire
- Visual Studio 2022 ou tout IDE C#

> **Conseil :** Le package NuGet Aspose.Words est ajouté avec `dotnet add package Aspose.Words`.

## Étape 1 : Charger le document Word contenant le graphique

La première étape consiste à ouvrir le fichier DOCX source. La classe `Document` représente l'ensemble du fichier Word en mémoire.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
```

Le chargement du document vous donne un accès complet à chaque nœud, y compris les formes qui contiennent des graphiques.

## Étape 2 : Récupérer la première forme de graphique du document

Les graphiques sont stockés à l'intérieur des nœuds `Shape`. Vous pouvez localiser le premier graphique avec `GetChild`.

```csharp
        // Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
```

Si le document contient plusieurs graphiques, ajustez l'index (`0`) ou parcourez la collection. Cette ligne garantit que vous avez une référence à l'objet `Chart` que vous allez modifier.

## Étape 3 : Éclater les tranches du diagramme circulaire

Éclater une tranche la sépare du reste du diagramme, rendant le graphique plus lisible. La propriété `Explode` s'applique à toute la série.

```csharp
        // Enable slice explosion so each slice is separated from the pie
        chart.PieChart.Explode = true;
```

Définir `Explode` à `true` **éclate les tranches du diagramme circulaire** pour l'ensemble de la série, ce qui est utile lorsque vous souhaitez que chaque tranche se détache.

## Étape 4 : Modifier l'angle de la première tranche

Parfois, vous avez besoin que la première tranche commence à un angle personnalisé, par exemple pour s'aligner à une directive de conception.

```csharp
        // Set a custom start angle for the first slice (30 degrees)
        chart.PieChart.FirstSliceAngle = 30;
```

La propriété `FirstSliceAngle` **modifie l'orientation de la première tranche**, faisant pivoter l'ensemble du diagramme afin que la première tranche débute à 30 degrés.

## Étape 5 : Afficher les libellés de pourcentage sur les tranches du diagramme

Afficher la contribution numérique de chaque tranche est souvent requis dans les rapports. Le drapeau `DataLabel.ShowPercentage` active les valeurs en pourcentage.

```csharp
        // Display percentage values on the data labels of the pie slices
        chart.PieChart.DataLabel.ShowPercentage = true;
```

Cette étape **affiche les libellés de pourcentage** directement sur le graphique, ce qui satisfait également l'exigence **display percentages pie**.

## Étape 6 : Enregistrer le document modifié

Après que toutes les personnalisations aient été appliquées, persistez les modifications dans un nouveau fichier. La méthode `Save` écrit le DOCX mis à jour sur le disque.

```csharp
        // Save the modified document
        doc.Save(@"YOUR_DIRECTORY\output.docx");
    }
}
```

Vous avez maintenant un **enregistrer le document modifié** qui contient un diagramme circulaire éclaté, une première tranche pivotée et des libellés de pourcentage visibles.

![Enregistrer le document modifié montrant un diagramme circulaire éclaté](/images/pie-chart-exploded.png "Enregistrer le document modifié avec des tranches de diagramme circulaire éclatées et des libellés de pourcentage")

*La capture d'écran illustre le résultat final après l'enregistrement du document.*

## Exemple complet, exécutable

En assemblant les éléments, voici le programme complet que vous pouvez copier‑coller dans un projet console :

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace PieChartCustomizer
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source DOCX
            Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

            // 2️⃣ Get the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Explode all slices
            chart.PieChart.Explode = true;

            // 4️⃣ Rotate the first slice to 30°
            chart.PieChart.FirstSliceAngle = 30;

            // 5️⃣ Show percentages on each slice
            chart.PieChart.DataLabel.ShowPercentage = true;

            // 6️⃣ Persist the changes
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Résultat attendu

L'ouverture de `output.docx` affichera un diagramme circulaire où :

- Chaque tranche est légèrement séparée (**exploded pie chart slices**)
- La première tranche commence avec un décalage de 30 degrés (**change first slice**)
- Chaque tranche montre sa contribution en pourcentage (**show percentage labels**, **display percentages pie**)
- Le fichier a été **save modified document** sans altérer l'original.

## Questions fréquentes et cas particuliers

| Question | Réponse |
|----------|--------|
| **Et si le document n'a aucun graphique ?** | Le code vérifie `null` après `GetChild`. Si aucun graphique n'existe, vous pouvez soit en ajouter un programmatiquement, soit interrompre avec un message clair. |
| **Puis-je éclater une seule tranche ?** | Oui. Utilisez `chart.PieChart.Series[0].DataPoints[i].Explosion = true;` où `i` est l'index de la tranche. |
| **Comment changer le format du libellé (p. ex., afficher la valeur + % )?** | Définissez `chart.PieChart.DataLabel.ShowValue = true;` et éventuellement `chart.PieChart.DataLabel.ShowPercentage = true;` pour combiner les deux. |
| **Le style du graphique est-il conservé après l'enregistrement ?** | Aspose.Words conserve tous les styles, y compris les couleurs et les polices, lorsque vous **save modified document**. |
| **Puis-je traiter plusieurs graphiques dans le même fichier ?** | Parcourez tous les nœuds `Shape` avec `NodeType.Shape` et filtrez par `shape.HasChart`. Appliquez les mêmes étapes à chaque graphique. |

## Conclusion

Vous savez maintenant comment **save modified document** après avoir personnalisé programmaticalement un diagramme circulaire dans Word. Le guide a couvert l'éclatement des tranches du diagramme, la modification de l'angle de la première tranche et l'affichage des libellés de pourcentage — répondant aux exigences **show percentage labels**, **explode pie chart slices**, **display percentages pie**, et **change first slice**.

Ensuite, envisagez d'explorer :

- Ajouter des séries de données dynamiquement (`chart.Series.Add(...)`)  
- Personnaliser le placement de la légende et les titres du graphique  
- Convertir le DOCX en PDF tout en préservant le style du graphique  

N'hésitez pas à expérimenter différents angles, paramètres d'éclatement ou formats de libellés pour répondre à vos besoins de reporting. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Comment enregistrer un document modifié en C# avec Aspose.Words – Guide étape par étape](/words/english/net/programming-with-docsaveoptions/how-to-save-edited-document-in-c-with-aspose-words-step-by-s/)
- [Mettre à jour les données de série de graphique dans un document Word avec Aspose.Words pour .NET](/words/english/net/programming-with-charts/modify-chart-series/)
- [Insérer un graphique en colonnes dans un document Word](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}