---
category: general
date: 2026-10-13
description: Comment formater un graphique dans Word avec C# en appliquant un format
  numérique personnalisé, tel que le format monétaire, aux axes du graphique. Exemple
  de code étape par étape inclus.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format chart
- apply custom number format
- custom number format word
- how to set chart
- change chart axis format
language: fr
lastmod: 2026-10-13
og_description: Comment formater un graphique dans Word avec C# vous permet d’appliquer
  un format numérique personnalisé aux axes du graphique, garantissant que les valeurs
  apparaissent en tant que monnaie, pourcentages ou tout autre modèle dont vous avez
  besoin. Suivez le guide étape par étape.
og_image_alt: Word chart showing axis values formatted as currency after applying
  custom number format
og_title: Comment formater un graphique dans Word avec C# – formats de nombres personnalisés
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: How to format chart in Word with C# by applying a custom number format,
    such as currency, to chart axes. Step‑by‑step code example included.
  headline: How to format chart in Word with C# and custom number formats
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart formatting
title: Comment formater un graphique dans Word avec C# et des formats numériques personnalisés
url: /fr/net/programming-with-charts/how-to-format-chart-in-word-with-c-and-custom-number-formats/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment formater un graphique dans Word avec C# et des formats numériques personnalisés

Formater un graphique dans Word avec C# est une exigence courante lorsque vous devez présenter des données de manière professionnelle. Ce guide vous montre comment appliquer un format numérique personnalisé à l'axe d'un graphique en utilisant **Aspose.Words for .NET**, afin que les valeurs apparaissent exactement comme vous le souhaitez.

Vous apprendrez à charger un fichier DOCX, à localiser le premier graphique, à lire le format actuel, puis à définir un nouveau modèle tel que la monnaie avec deux décimales. Le tutoriel couvre également comment modifier le format de l'axe du graphique pour des séries supplémentaires et comment réinitialiser le format si nécessaire.

## Prérequis

* .NET 6.0 ou version ultérieure installé  
* Un projet Visual Studio 2022 (ou tout IDE supportant .NET)  
* Le package NuGet **Aspose.Words for .NET** (`Aspose.Words`)  
* Un document Word (`input.docx`) contenant au moins un graphique

Vous pouvez ajouter le package avec la commande suivante :

```bash
dotnet add package Aspose.Words
```

## Comment formater un graphique dans Word en utilisant Aspose.Words

Le programme complet suivant montre chaque étape nécessaire pour **formater** les valeurs d'axe du graphique. Enregistrez le fichier sous le nom `Program.cs` et exécutez-le depuis la ligne de commande ou votre IDE.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Load the Word document that contains the chart
        Document doc = new Document("input.docx");

        // Step 2: Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Step 3: Access the X‑value collection of the first data series
        ChartXValueCollection xValues = chart.ChartData.Series[0].XValues;

        // Optional: Show the current number format code
        Console.WriteLine($"Current format code: {xValues.FormatCode}");

        // Step 4: Apply a custom number format (currency with two decimals)
        // The format string follows Excel/Word conventions.
        xValues.FormatCode = "\"$\"#,##0.00";

        // Step 5: Save the modified document
        doc.Save("output_formatted.docx");
        Console.WriteLine("Chart axis format applied and document saved as output_formatted.docx");
    }
}
```

### Explication de chaque étape

| Étape | Pourquoi c'est important | Code clé |
|------|--------------------------|----------|
| **Charger le document** | Vous avez besoin d'un objet `Document` pour travailler avec le fichier Word. | `new Document("input.docx")` |
| **Récupérer le graphique** | Les objets `Chart` sont stockés en tant que nœuds `Shape` ; le cast vous permet d'utiliser les API spécifiques aux graphiques. | `(Chart)doc.GetChild(NodeType.Shape, 0, true)` |
| **Accéder aux valeurs X** | Le formatage de l'axe s'applique à la collection de valeurs d'une série de données. | `chart.ChartData.Series[0].XValues` |
| **Lire le format actuel** | Connaître le `FormatCode` existant vous aide à décider s'il faut le remplacer ou le compléter. | `xValues.FormatCode` |
| **Définir un format personnalisé** | La propriété `FormatCode` accepte tout modèle compatible Excel, permettant les monnaies, pourcentages, dates, etc. | `xValues.FormatCode = "\"$\"#,##0.00"` |
| **Enregistrer le document** | La persistance des modifications écrit le nouveau format d'axe dans le fichier DOCX. | `doc.Save("output_formatted.docx")` |

L'exécution du programme génère `output_formatted.docx`. Ouvrez-le dans Word et vous verrez les valeurs de l'axe X du graphique affichées comme **$1,234.00**, **$2,345.00**, … au lieu de simples nombres.

## Appliquer un format numérique personnalisé à l'axe du graphique

Si vous devez **appliquer un format numérique personnalisé** à l'axe Y ou à des séries supplémentaires, le processus est identique — il suffit de cibler une collection différente :

```csharp
// Apply format to Y‑values of the second series
ChartYValueCollection yValues = chart.ChartData.Series[1].YValues;
yValues.FormatCode = "0%"; // percentage format
```

> **Astuce :** Utilisez des guillemets doubles à l'intérieur de la chaîne de format pour intégrer des caractères littéraux (par ex., `"$"` pour la monnaie). Échappez les guillemets comme indiqué ci‑dessus.

## Format numérique personnalisé – gestion de la langue du document Word

Word respecte la langue du document lors de l'interprétation des formats numériques. Si le document utilise une langue autre que l'anglais (US), vous devrez peut‑être ajuster la chaîne de format :

```csharp
// German locale – uses comma as decimal separator
xValues.FormatCode = "\"€\" #.##0,00";
```

Tester le format sur un document avec les paramètres de langue allemande confirme que les valeurs apparaissent comme **€ 1.234,00**.

## Comment définir les propriétés du graphique par programme

Au‑delà du formatage des axes, vous voulez souvent **définir** les titres du graphique, les légendes ou les étiquettes de données. Voici un extrait rapide qui montre comment définir le titre d'un graphique après avoir formaté l'axe :

```csharp
chart.Title.Text = "Sales by Quarter";
chart.Title.IsVisible = true;
```

Combiner cela avec le format numérique personnalisé vous donne un graphique entièrement soigné, prêt pour le reporting.

## Modifier dynamiquement le format de l'axe du graphique en fonction de l'entrée utilisateur

Dans des applications réelles, vous pouvez laisser les utilisateurs choisir un format à l'exécution. La méthode suivante encapsule la logique de formatage :

```csharp
static void SetAxisFormat(Chart chart, int seriesIndex, string formatCode)
{
    var xVals = chart.ChartData.Series[seriesIndex].XValues;
    xVals.FormatCode = formatCode;
}
```

Vous pouvez appeler `SetAxisFormat(chart, 0, "\"$\"#,##0.00")` pour la monnaie ou `SetAxisFormat(chart, 0, "0%")` pour les pourcentages. Cette approche garde votre code principal propre et supporte les extensions futures.

## Cas limites et pièges courants

| Situation | Points d'attention | Solution suggérée |
|-----------|--------------------|-------------------|
| Le document ne contient **aucun graphique** | `GetChild` renvoie `null`, provoquant une exception de cast. | Vérifier `null` avant le cast (voir l'exemple). |
| Plusieurs graphiques dans le même document | Le code récupère toujours le premier graphique (`index 0`). | Parcourir `doc.GetChildNodes(NodeType.Shape, true)` et filtrer par `ShapeType.Chart`. |
| Série **sans valeurs X** (par ex., graphiques circulaires) | Accéder à `XValues` peut lever `ArgumentOutOfRangeException`. | Vérifier que `Series[i].XValues` n'est pas vide avant le formatage. |
| Incohérence de langue | Le symbole monétaire peut apparaître incorrectement. | Définir explicitement `xValues.FormatCode` avec les symboles de la langue appropriée. |

## Résultat attendu

Après avoir exécuté le programme d'exemple, ouvrez **output_formatted.docx**. L'axe X du graphique doit afficher les nombres dans le format personnalisé choisi. Pour l'exemple de monnaie, les libellés d'axe ressemblent à :

```
$1,000.00
$2,000.00
$3,000.00
```

Si vous avez appliqué le format pourcentage aux valeurs Y, les libellés de l'axe Y apparaissent comme :

```
10%
20%
30%
```

## Conclusion

Ce tutoriel vous a montré **comment formater un graphique** dans Word avec C# en **appliquant un format numérique personnalisé** aux valeurs d'axe. Vous disposez désormais d'un modèle réutilisable pour définir la monnaie, les pourcentages ou tout autre modèle numérique, ainsi que de conseils pour gérer les langues, les séries multiples et les entrées utilisateur dynamiques.

Ensuite, vous pourriez explorer **comment définir les titres du graphique**, les étiquettes de données, ou même exporter le graphique en image en utilisant `ChartRenderer`. Ces sujets s'appuient directement sur les concepts abordés ici et vous aideront à créer des solutions de reporting entièrement automatisées.

---

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Format de nombre pour l'axe d'un graphique](/words/english/net/programming-with-charts/number-format-for-axis/)
- [Formater le nombre d'étiquettes de données dans un graphique](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Formater l'axe X secondaire et définir les unités d'affichage en milliers dans les graphiques en ligne Word en utilisant Aspose.Words for .NET](/words/english/net/programming-with-charts/format-secondary-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}