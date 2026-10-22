---
category: general
date: 2026-10-13
description: Exemple de graphique radial Aspose.Words montrant comment activer les
  graduations sur un graphique radial en utilisant C# et Aspose.Words 24.9+.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose.words radial chart example
- Aspose.Words chart API
- C# radial chart
- graduations visibility
- Aspose.Words version 24.9
- chart manipulation in .NET
language: fr
lastmod: 2026-10-13
og_description: Exemple de graphique radial Aspose.Words démontrant l’activation des
  graduations sur un graphique radial avec C# et la dernière bibliothèque 24.9+.
og_image_alt: Aspose.Words radial chart example displaying graduations
og_title: Exemple de graphique radial Aspose.Words – activer les graduations en C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  headline: 'Aspose.Words radial chart example: enable graduations in C#'
  type: TechArticle
- description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  name: 'Aspose.Words radial chart example: enable graduations in C#'
  steps:
  - name: Load the document that contains a radial chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: Retrieve the first chart shape from the document
    text: '```csharp // NodeType.Shape selects shapes; the third argument (true) searches
      the whole tree. Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
      if (chart == null) { throw new InvalidOperationException("No chart shape found
      in the document."); } ```'
  - name: Enable graduations on the radial chart
    text: '```csharp // This property is available starting with Aspose.Words 24.9.
      chart.RadialChart.IsGraduationsVisible = true; ```'
  - name: Save the modified document
    text: '```csharp string outputPath = Path.Combine(Environment.CurrentDirectory,
      "RadialChart_Graduations.docx"); doc.Save(outputPath); Console.WriteLine($"Document
      saved to {outputPath}"); ```'
  - name: Expected output
    text: When you open `RadialChart_Graduations.docx` in Word, the radial chart will
      display tick marks (graduations) around the circular axis, similar to the screenshot
      shown earlier. The rest of the chart (data series, legend, title) remains unchanged.
  type: HowTo
tags:
- Aspose.Words
- C#
- Charts
title: 'Exemple de graphique radial Aspose.Words : activer les graduations en C#'
url: /fr/net/programming-with-charts/aspose-words-radial-chart-example-enable-graduations-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Exemple de graphique radial Aspose.Words : activer les graduations en C#

Si vous recherchez un **exemple de graphique radial Aspose.Words**, vous êtes au bon endroit. Ce tutoriel vous guide pas à pas pour activer les graduations d’un graphique radial à l’aide de l’API Aspose.Words for .NET.

Les graphiques radiaux sont utiles pour visualiser des données cycliques telles que les métriques d’heure de la journée ou les tendances saisonnières. Par défaut, les graduations (les marques de graduation autour de l’axe circulaire) sont masquées, ce qui peut rendre le graphique plus difficile à lire. Les activer ne nécessite qu’une seule ligne de code, mais il faut connaître le modèle d’objet correct et la version qui prend en charge cette fonctionnalité.

Dans ce guide, vous apprendrez à :

* Charger un document Word contenant déjà un graphique radial.  
* Accéder à la forme du graphique via l’API Aspose.Words chart.  
* Activer la **visibilité des graduations** (disponible à partir de **Aspose.Words version 24.9**).  
* Enregistrer le document modifié et vérifier le résultat.

Le code complet, exécutable, est fourni, vous pouvez le copier‑coller dans un nouveau projet console et voir l’effet immédiatement.

![Exemple de graphique radial Aspose.Words avec graduations](https://example.com/images/radial-chart-graduations.png "Exemple de graphique radial Aspose.Words montrant les graduations activées")

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

| Prérequis | Pourquoi c’est important |
|-------------|----------------|
| .NET 6.0 ou ultérieur | Aspose.Words for .NET 24.9+ cible .NET Standard 2.0 et fonctionne sur .NET 6+. |
| Aspose.Words for .NET **24.9** ou plus récent | La propriété `IsGraduationsVisible` a été introduite dans la version 24.9. Les versions antérieures lanceront une `MissingMemberException`. |
| Un document Word (`RadialChart.docx`) contenant un graphique radial | L’exemple manipule un graphique existant ; créer un graphique à partir de zéro est un sujet distinct. |
| Un IDE C# (Visual Studio, Rider, VS Code) | Tout IDE capable de compiler des projets .NET fonctionnera. |
| Package NuGet `Aspose.Words` | Installez‑le via `dotnet add package Aspose.Words --version 24.9.0` (ou version ultérieure). |

> **Astuce pro :** Si vous ne pouvez pas passer à la version 24.9, vous pouvez toujours modifier d’autres propriétés du graphique, mais les graduations resteront masquées car l’API n’expose pas ce drapeau.

## Exemple de graphique radial Aspose.Words – guide étape par étape

Les sections suivantes décomposent le processus en étapes distinctes et faciles à suivre. Chaque étape inclut le code exact dont vous avez besoin ainsi qu’une courte explication du *pourquoi* de l’étape.

### Étape 1 : Charger le document qui contient un graphique radial

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// The file path can be absolute or relative to the executable directory.
string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");

// Load the Word document. Aspose.Words parses the entire file into a DOM tree.
Document doc = new Document(sourcePath);
```

**Pourquoi c’est important :**  
`Document` est le point d’entrée de l’**API Aspose.Words chart**. Il charge le fichier DOCX en mémoire, vous donnant accès à chaque nœud — paragraphes, tableaux et formes de graphiques. Si le fichier est introuvable, `Document` lève une `FileNotFoundException`, qu’il faut gérer dans le code de production.

### Étape 2 : Récupérer la première forme de graphique du document

```csharp
// NodeType.Shape selects shapes; the third argument (true) searches the whole tree.
Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
if (chart == null)
{
    throw new InvalidOperationException("No chart shape found in the document.");
}
```

**Pourquoi c’est important :**  
Les graphiques sont stockés sous forme de nœuds `Shape`. La méthode `GetChild` avec `NodeType.Shape` parcourt le DOM et renvoie la première forme correspondante. Le cast en `Chart` vous donne accès aux propriétés spécifiques du graphique telles que `RadialChart`. La vérification de null garantit une erreur claire si le document ne contient aucun graphique, ce qui est un cas limite fréquent lors de la réutilisation de modèles.

### Étape 3 : Activer les graduations sur le graphique radial

```csharp
// This property is available starting with Aspose.Words 24.9.
chart.RadialChart.IsGraduationsVisible = true;
```

**Pourquoi c’est important :**  
`IsGraduationsVisible` contrôle les marques de graduation autour de l’axe circulaire. Lorsqu’elle est définie sur `true`, le graphique affiche les graduations, améliorant la lisibilité pour les utilisateurs qui doivent évaluer les valeurs avec précision. La propriété se trouve sous `RadialChart`, qui est un sous‑type de `Chart`. Si vous essayez cela sur un graphique non radial (par ex. un diagramme à barres), la propriété `RadialChart` sera `null`, il faut donc vérifier le type de graphique d’abord dans des scénarios plus complexes.

#### Gestion des graphiques non radiaux (optionnel)

```csharp
if (chart.ChartType == ChartType.Radial)
{
    chart.RadialChart.IsGraduationsVisible = true;
}
else
{
    Console.WriteLine("The chart is not radial; graduations are not applicable.");
}
```

Cette garde rend le code robuste lorsque le document source peut contenir différents types de graphiques.

### Étape 4 : Enregistrer le document modifié

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

**Pourquoi c’est important :**  
Appeler `Save` écrit le DOM en mémoire dans un fichier .docx, persistant la modification apportée au graphique. Le fichier de sortie peut être ouvert dans Microsoft Word, LibreOffice ou tout autre visualiseur supportant le format DOCX. Vous verrez le graphique radial avec les graduations visibles.

## Exemple complet, exécutable

Voici le programme complet que vous pouvez coller dans `Program.cs` d’un projet console .NET.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // 1. Load the source document that contains a radial chart.
        // -----------------------------------------------------------------
        string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");
        Document doc = new Document(sourcePath);

        // -----------------------------------------------------------------
        // 2. Locate the first chart shape in the document.
        // -----------------------------------------------------------------
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // -----------------------------------------------------------------
        // 3. Enable graduations (tick marks) on the radial chart.
        // -----------------------------------------------------------------
        // Ensure the chart is radial before accessing RadialChart.
        if (chart.ChartType == ChartType.Radial && chart.RadialChart != null)
        {
            chart.RadialChart.IsGraduationsVisible = true;
        }
        else
        {
            Console.WriteLine("The chart is not a radial chart; cannot set graduations.");
            return;
        }

        // -----------------------------------------------------------------
        // 4. Save the updated document.
        // -----------------------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Radial chart with graduations saved to: {outputPath}");
    }
}
```

### Résultat attendu

Lorsque vous ouvrirez `RadialChart_Graduations.docx` dans Word, le graphique radial affichera des marques de graduation autour de l’axe circulaire, comme sur la capture d’écran présentée plus haut. Le reste du graphique (séries de données, légende, titre) reste inchangé.

## Variations courantes et cas limites

| Situation | Solution |
|-----------|----------|
| **Version Aspose.Words ancienne (< 24.9)** | Mettre à jour vers le dernier package NuGet. La propriété `IsGraduationsVisible` n’existe pas dans les versions antérieures. |
| **Plusieurs graphiques dans le même document** | Utiliser `doc.GetChild(NodeType.Shape, index, true)` avec l’`index` approprié ou itérer sur `doc.GetChildNodes(NodeType.Shape, true)` et filtrer par `ChartType.Radial`. |
| **Graphique créé programmatique** | Utiliser `DocumentBuilder` pour insérer un graphique, puis définir `RadialChart.IsGraduationsVisible` on the |

## Que devez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets avec des explications étape par étape pour vous aider à maîtriser d’autres fonctionnalités de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Update Chart Series Data in a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)
- [Remove a Chart Series from a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/remove-chart-series/)
- [Hide Plot Area Border in a Column Chart with Aspose.Words for .NET](/words/english/net/programming-with-charts/hide-plot-border/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}