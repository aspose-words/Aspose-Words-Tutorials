---
category: general
date: 2026-10-13
description: Apprenez à ajuster programmatique les étiquettes de graphique dans un
  document Word en utilisant C#. Ce guide couvre la manipulation des graphiques avec
  Aspose.Words et l'alignement des étiquettes.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically adjust chart labels
- Aspose.Words chart manipulation
- C# chart data label
- Word document chart example
- modify chart label position
- set data label alignment
language: fr
lastmod: 2026-10-13
og_description: Ajustez programmétiquement les étiquettes de graphique dans un document
  Word en utilisant C#. Suivez ce tutoriel complet pour modifier le placement des
  étiquettes, l’alignement et bien plus encore.
og_image_alt: Screenshot showing programmatically adjust chart labels in a Word document
og_title: Modifier les étiquettes de graphique dans Word par programmation – Guide
  pas à pas en C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to programmatically adjust chart labels in a Word document
    using C#. This guide covers Aspose.Words chart manipulation and label alignment.
  headline: Programmatically adjust chart labels in a Word document with C#
  type: TechArticle
tags:
- chart labels
- C#
- Aspose.Words
title: Ajuster les libellés du graphique de façon programmatique dans un document
  Word avec C#
url: /fr/net/programming-with-charts/programmatically-adjust-chart-labels-in-a-word-document-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ajuster les étiquettes de graphique de manière programmatique dans un document Word avec C#

Si vous devez **ajuster les étiquettes de graphique de manière programmatique** dans un document Word, ce guide vous montre exactement comment le faire avec C#. Que vous génériez des rapports, automatisiez des tableaux de bord ou personnalisiez des modèles, vous verrez un exemple complet et exécutable qui modifie le placement et l’alignement des étiquettes d’un graphique à l’intérieur d’un fichier .docx.

Vous apprendrez également à utiliser les techniques de **manipulation de graphiques Aspose.Words**, à gérer plusieurs séries et à éviter les pièges courants lors de la manipulation d’objets **C# chart data label**.

## Prérequis

* .NET 6.0 (ou version ultérieure) installé  
* Visual Studio 2022 (ou tout IDE C#)  
* Le package NuGet **Aspose.Words for .NET** (`Install-Package Aspose.Words`)  
* Un document Word (`input.docx`) contenant au moins un graphique  

Ces éléments sont requis pour l'**exemple de graphique de document Word** que nous allons modifier.

## Étape 1 : Configurer le projet et importer les espaces de noms

Créez un nouveau projet console et ajoutez les directives `using` nécessaires. Cela prépare l’environnement pour **ajuster les étiquettes de graphique de manière programmatique**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source and destination files
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the document that contains a chart
            Document doc = new Document(inputPath);
```

*Pourquoi cette étape ?*  
Le chargement du document vous donne accès à l’arborescence interne de l'**exemple de graphique de document Word**, où les graphiques sont stockés sous forme de nœuds de forme.

## Étape 2 : Localiser la première forme de graphique

Les graphiques sont stockés sous forme de nœuds `Shape`. Le code suivant récupère le premier graphique du document, qui est la cible de nos ajustements d’étiquettes.

```csharp
            // Retrieve the first chart shape in the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }
```

*Pourquoi cette étape ?*  
La méthode `GetChild` recherche de façon récursive (`true`) et renvoie le premier nœud de type `Shape`. Le cast en `Chart` nous permet d’utiliser l’API spécifique aux graphiques.

## Étape 3 : Accéder à l’étiquette de données que vous souhaitez modifier

Chaque série d’un graphique possède une collection d’étiquettes de données. Pour un graphique simple, la première étiquette suffit souvent. Le code ci‑dessous montre comment y accéder.

```csharp
            // Access the first series' first data label
            ChartSeries series = chart.Series[0];
            ChartDataLabel dataLabel = series.DataLabelCollection[0];
```

*Pourquoi cette étape ?*  
`ChartSeries` représente une série de points. `DataLabelCollection` contient les étiquettes de cette série, permettant un contrôle précis du placement et de l’alignement.

## Étape 4 : Modifier le placement et l’alignement de l’étiquette

Nous **ajustons maintenant les étiquettes de graphique de manière programmatique** en définissant la position, l’alignement horizontal et l’alignement vertical. Ces propriétés correspondent aux options que vous voyez dans l’interface Word.

```csharp
            // Set the label's position relative to the data point
            dataLabel.Position = DataLabelPosition.OutsideEnd; // Options: OutsideEnd, InsideEnd, etc.

            // Align the label horizontally and vertically
            dataLabel.HorizontalAlignment = HorizontalAlignment.Center;
            dataLabel.VerticalAlignment = VerticalAlignment.Top;
```

*Pourquoi ces réglages ?*

* `OutsideEnd` place l’étiquette juste à l’extérieur de l’extrémité de chaque barre ou colonne, améliorant la lisibilité.  
* `HorizontalAlignment.Center` garde le texte centré sur le point, tandis que `VerticalAlignment.Top` aligne le bord supérieur de l’étiquette avec le point de données, évitant le chevauchement avec d’autres éléments.

### Astuce
Si un graphique possède plusieurs séries, parcourez `chart.Series` et appliquez les mêmes paramètres à chaque `DataLabelCollection`. Cela garantit une apparence cohérente sur l’ensemble du graphique.

```csharp
            // Example: adjust all series in the chart
            foreach (ChartSeries s in chart.Series)
            {
                foreach (ChartDataLabel lbl in s.DataLabelCollection)
                {
                    lbl.Position = DataLabelPosition.OutsideEnd;
                    lbl.HorizontalAlignment = HorizontalAlignment.Center;
                    lbl.VerticalAlignment = VerticalAlignment.Top;
                }
            }
```

## Étape 5 : Enregistrer le document modifié

Après avoir ajusté les étiquettes, enregistrez les modifications dans un nouveau fichier. Cela complète le processus de **modification de la position des étiquettes de graphique**.

```csharp
            // Save the updated document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Lorsque vous ouvrirez `output.docx`, vous verrez que chaque étiquette de graphique a été déplacée à l’extrémité extérieure de son point de données, centrée horizontalement et alignée verticalement en haut.

## Cas particuliers et variantes

| Situation | À surveiller | Approche recommandée |
|-----------|--------------|----------------------|
| **Multiple charts** in the same document | `GetChild` only returns the first chart. | Use `doc.GetChildNodes(NodeType.Shape, true)` to iterate over all chart shapes. |
| **Series without data labels** | `DataLabelCollection` may be empty. | Check `series.HasDataLabels` before accessing the collection. |
| **Different chart types** (pie, line, scatter) | Not all `DataLabelPosition` values are valid. | Use `DataLabelPosition.Auto` for charts that decide the best placement automatically. |
| **Localization** | Alignment constants are language‑agnostic, but the rendered text may need right‑to‑left support. | Set `dataLabel.TextDirection` if you need RTL languages. |

## Exemple complet et exécutable

Voici le programme complet que vous pouvez copier, coller et exécuter. Remplacez `YOUR_DIRECTORY` par le chemin réel d’un dossier.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the Word document that contains a chart
            Document doc = new Document(inputPath);

            // Retrieve the first chart shape from the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Loop through all series and adjust each data label
            foreach (ChartSeries series in chart.Series)
            {
                foreach (ChartDataLabel label in series.DataLabelCollection)
                {
                    label.Position = DataLabelPosition.OutsideEnd;
                    label.HorizontalAlignment = HorizontalAlignment.Center;
                    label.VerticalAlignment = VerticalAlignment.Top;
                }
            }

            // Save the modified document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Résultat attendu :** L’ouverture de `output.docx` montre chaque étiquette de graphique positionnée à l’extérieur du point de données, centrée horizontalement et alignée en haut — exactement l’effet de **ajustement programmatique des étiquettes de graphique** que vous avez scripté.

## Conclusion

Vous savez maintenant comment **ajuster les étiquettes de graphique de manière programmatique** dans un document Word en utilisant C#. Le tutoriel a couvert :

* Chargement d’un document avec **manipulation de graphiques Aspose.Words**  
* Accès à un **C# chart data label**  
* Modification de la **position des étiquettes de graphique** et de l’alignement  
* Enregistrement du fichier et gestion des cas particuliers courants  

À partir de là, vous pouvez explorer des scénarios plus avancés, comme la personnalisation des polices d’étiquette, l’ajout de mise en forme conditionnelle ou la mise à jour de plusieurs graphiques en traitement par lots. Expérimentez les différentes options `DataLabelPosition` pour trouver le style qui convient le mieux à vos rapports.

---

*Prêt à améliorer votre pipeline de génération de rapports automatisés ? Essayez d’ajouter des formats numériques personnalisés aux étiquettes ou d’exporter le graphique sous forme d’image à utiliser dans des PDF.*

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Définir des étiquettes de données uniformes dans un graphique à colonnes avec Aspose.Words pour .NET](/words/english/net/programming-with-charts/uniform-data-labels/)
- [Définir les options par défaut pour les étiquettes de données dans un graphique](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Mettre à jour les données de séries de graphique dans un document Word avec Aspose.Words pour .NET](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}