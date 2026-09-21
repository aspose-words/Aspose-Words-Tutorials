---
category: general
date: 2026-09-21
description: Apprenez à créer un document Word en C# et à insérer un graphique en
  colonnes, à définir la position des étiquettes et à afficher les valeurs à l’aide
  d’Aspose.Words dans un guide étape par étape.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- how to insert chart
- how to set label
- how to display values
- insert column chart word
language: fr
lastmod: 2026-09-21
og_description: Créer un document Word C# avec Aspose.Words. Ce tutoriel montre comment
  insérer un graphique en colonnes, définir la position des étiquettes et afficher
  les valeurs.
og_image_alt: Screenshot of a Word document created with C# that contains a column
  chart and data labels
og_title: Créer un document Word en C# – insérer un graphique en colonnes, définir
  le libellé, afficher les valeurs
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create Word document C# and insert a column chart, set
    label position, and display values using Aspose.Words in a step‑by‑step guide.
  headline: How to create Word document C# with a column chart and formatted labels
  type: TechArticle
- description: Learn how to create Word document C# and insert a column chart, set
    label position, and display values using Aspose.Words in a step‑by‑step guide.
  name: How to create Word document C# with a column chart and formatted labels
  steps:
  - name: Expected result
    text: When you open `output.docx`, you should see a single column chart similar
      to the image below. Each column has a numeric label at its top, inside the column,
      displaying the series value.
  - name: Adding custom data to the chart
    text: 'If you need to replace the placeholder data, you can modify the chart’s
      `Series` collection:'
  - name: Changing label font and color
    text: 'You can further customize the label appearance:'
  - name: Inserting multiple charts
    text: The `DocumentBuilder` can insert as many charts as you need. Just call `InsertChart`
      again after moving the cursor with `builder.Writeln()` or `builder.InsertParagraph()`.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Charts
title: Comment créer un document Word en C# avec un diagramme en colonnes et des étiquettes
  formatées
url: /fr/net/programming-with-charts/how-to-create-word-document-c-with-a-column-chart-and-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer un document Word C# avec un diagramme en colonnes et des libellés formatés

Si vous devez **créer un document Word C#** qui inclut un diagramme, ce guide vous montre exactement comment le faire. Vous apprendrez à insérer un diagramme en colonnes, à positionner son libellé de données et à afficher les valeurs du libellé — le tout avec Aspose.Words for .NET.

La génération d’un fichier Word contenant un diagramme nécessitait auparavant un travail manuel dans Microsoft Word. Avec les étapes **how to insert chart** décrites ici, vous pouvez automatiser l’ensemble du processus depuis le code, rendant la génération de rapports rapide et reproductible. Le tutoriel couvre également **how to set label** et **how to display values** afin que le diagramme soit prêt pour les utilisateurs finaux.

À la fin de cet article, vous disposerez d’un programme C# complet et exécutable qui crée un fichier `.docx` contenant un diagramme en colonnes dont les libellés de données apparaissent à l’intérieur de chaque colonne et affichent leurs valeurs numériques.

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

* Le SDK .NET 6.0 ou une version ultérieure installé  
* Une copie sous licence de **Aspose.Words for .NET** (l’essai gratuit suffit pour les tests)  
* Un IDE tel que Visual Studio 2022 ou Visual Studio Code  

Aucun package NuGet supplémentaire n’est requis au‑delà de `Aspose.Words`.

## Étape 1 : Configurer le projet et ajouter Aspose.Words

Créez un nouveau projet console et ajoutez le package Aspose.Words :

```bash
dotnet new console -n WordChartDemo
cd WordChartDemo
dotnet add package Aspose.Words
```

La commande `dotnet add package` récupère la dernière version stable de **Aspose.Words**, qui inclut l’API de diagrammes utilisée dans l’exemple **insert column chart word**.

## Étape 2 : Créer un nouveau document Word vierge

Le premier extrait de code crée un document vide et un `DocumentBuilder` qui vous permet d’insérer du contenu. C’est la base pour **create word document C#**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 2: Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` représente l’ensemble du fichier `.docx`, tandis que `DocumentBuilder` fournit des méthodes telles que `InsertParagraph`, `InsertImage` et, de façon cruciale pour ce tutoriel, `InsertChart`.

## Étape 3 : Insérer un diagramme en colonnes (how to insert chart)

Nous insérons maintenant un **column chart**. La méthode `InsertChart` prend le type de diagramme, la largeur et la hauteur en points.

```csharp
        // Step 3: Insert a column chart with a width of 400 pt and height of 300 pt.
        Chart chart = builder.InsertChart(ChartType.Column, 400, 300);
```

À ce stade, le diagramme contient une série de données par défaut avec des valeurs factices. Vous pouvez remplacer les données de la série si vous avez besoin de nombres personnalisés, mais pour démontrer **how to set label** et **how to display values**, les données par défaut sont suffisantes.

## Étape 4 : Positionner le libellé de données à l’intérieur de chaque colonne (how to set label)

Les libellés de données sont le texte qui apparaît sur chaque colonne. Pour rendre le diagramme plus lisible, nous déplaçons le libellé à l’intérieur de la colonne et activons son affichage numérique.

```csharp
        // Step 4: Access the first data label of the first series.
        ChartDataLabel label = chart.DataLabels[0];

        // Position the label at the inside end of the column.
        label.Position = ChartDataLabelPosition.InsideEnd;

        // Show the numeric value of each data point.
        label.ShowValue = true;
```

`ChartDataLabelPosition.InsideEnd` place le libellé en haut de la colonne tout en restant à l’intérieur de la forme de la colonne, ce qui est un style visuel courant pour les rapports. Le fait de définir `ShowValue` à `true` répond à l’exigence **how to display values**.

## Étape 5 : Enregistrer le document

Enfin, écrivez le document sur le disque. Le fichier peut être ouvert avec Microsoft Word, LibreOffice ou tout visualiseur supportant le format Open XML.

```csharp
        // Step 5: Save the document to the output folder.
        string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

L’exécution du programme produit `output.docx` contenant un diagramme en colonnes avec les libellés de données positionnés à l’intérieur de chaque colonne et affichant leurs valeurs.

### Résultat attendu

Lorsque vous ouvrez `output.docx`, vous devez voir un diagramme en colonnes similaire à l’image ci‑dessous. Chaque colonne possède un libellé numérique en haut, à l’intérieur de la colonne, affichant la valeur de la série.

![Chart in a Word document created with C#](/images/word-chart-example.png "Chart in a Word document created with C# – create word document C#")

*Texte alternatif :* *Diagramme dans un document Word créé avec C# qui montre comment insérer un diagramme en colonnes word et afficher les valeurs.*

## Variantes courantes et cas limites

### Ajout de données personnalisées au diagramme

Si vous devez remplacer les données factices, vous pouvez modifier la collection `Series` du diagramme :

```csharp
// Replace the default series with custom values.
chart.Series.Clear();
ChartSeries series = chart.Series.Add(ChartType.Column);
series.Name = "Sales Q1";
series.AddCategory("Jan", 120);
series.AddCategory("Feb", 150);
series.AddCategory("Mar", 180);
```

### Modification de la police et de la couleur du libellé

Vous pouvez personnaliser davantage l’apparence du libellé :

```csharp
label.Font.Name = "Arial";
label.Font.Size = 10;
label.Font.Color = System.Drawing.Color.DarkBlue;
```

### Insertion de plusieurs diagrammes

Le `DocumentBuilder` peut insérer autant de diagrammes que nécessaire. Appelez simplement `InsertChart` à nouveau après avoir déplacé le curseur avec `builder.Writeln()` ou `builder.InsertParagraph()`.

## Astuces professionnelles

* **Astuce pro :** Définissez `chart.HasTitle = true` et attribuez `chart.Title.Text` pour donner au diagramme un titre descriptif. Cela améliore l’accessibilité pour les lecteurs d’écran.
* **Attention :** Lors de l’enregistrement sur un partage réseau, assurez‑vous que l’application possède les droits d’écriture ; sinon `doc.Save` lèvera une `UnauthorizedAccessException`.
* **Conseil de performance :** Réutilisez une seule instance de `DocumentBuilder` pour plusieurs insertions ; créer un nouveau builder à chaque opération ajoute une surcharge inutile.

## Conclusion

Vous savez maintenant comment **create word document C#** contenant un diagramme en colonnes, comment **insert chart**, **set label** et **display values** à l’intérieur de chaque colonne. L’exemple complet de code ci‑dessus est prêt à être exécuté, et vous pouvez l’étendre avec des données personnalisées, du style ou des diagrammes supplémentaires.

Ensuite, explorez des sujets connexes tels que **how to insert picture**, **how to generate tables** ou **how to apply document themes** pour rendre vos rapports automatisés encore plus riches. Bon codage !

## Que devez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert a Simple Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}