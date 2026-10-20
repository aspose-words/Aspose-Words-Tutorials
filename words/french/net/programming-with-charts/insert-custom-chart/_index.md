---
title: Insérer un graphique en colonnes personnalisé dans un document Word avec Aspose.Words for .NET
weight: 310
limit:
description: Créez un fichier Word, insérez un graphique en colonnes, remplacez ses données par un tableau personnalisé, ajoutez un titre et enregistrez — le tout avec Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, custom chart, column chart, Word document chart, populate chart from array, insert chart Aspose.Words]
url: /net/programming-with-charts/insert-custom-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Créez un fichier Word, insérez un graphique en colonnes, remplacez
    ses données par un tableau personnalisé, ajoutez un titre et enregistrez — le
    tout avec Aspose.Words for .NET.
  headline: Insérer un graphique en colonnes personnalisé dans un document Word avec
    Aspose.Words for .NET
  type: TechArticle
- description: Créez un fichier Word, insérez un graphique en colonnes, remplacez
    ses données par un tableau personnalisé, ajoutez un titre et enregistrez — le
    tout avec Aspose.Words for .NET.
  name: Insérer un graphique en colonnes personnalisé dans un document Word avec Aspose.Words
    for .NET
  steps:
  - name: Créez un nouveau Document et un DocumentBuilder qui y est attaché.
    text: Créez un nouveau Document et un DocumentBuilder qui y est attaché.
  - name: Insérez un graphique en colonnes de taille 432 x 252 points dans le document
      et récupérez son objet Chart.
    text: Insérez un graphique en colonnes de taille 432 x 252 points dans le document
      et récupérez son objet Chart.
  - name: Supprimez la série d'exemple générée automatiquement du graphique.
    text: Supprimez la série d'exemple générée automatiquement du graphique.
  - name: Définissez les libellés de catégorie de l'axe X et les entrées de légende
      pour chaque série.
    text: Définissez les libellés de catégorie de l'axe X et les entrées de légende
      pour chaque série.
  - name: Créez un tableau à deux dimensions où chaque ligne contient les valeurs
      d'une série.
    text: Créez un tableau à deux dimensions où chaque ligne contient les valeurs
      d'une série.
  - name: Parcourez chaque série, extrayez ses valeurs de ligne depuis la matrice,
      puis ajoutez la série au graphique avec l'entrée de légende correspondante et
      les libellés de l'axe X.
    text: Parcourez chaque série, extrayez ses valeurs de ligne depuis la matrice,
      puis ajoutez la série au graphique avec l'entrée de légende correspondante et
      les libellés de l'axe X.
  - name: Définissez le texte du titre du graphique sur « Half‑Yearly Revenue » et
      rendez-le visible.
    text: Définissez le texte du titre du graphique sur « Half‑Yearly Revenue » et
      rendez-le visible.
  - name: Enregistrez le document contenant le graphique personnalisé dans un fichier
      .docx.
    text: Enregistrez le document contenant le graphique personnalisé dans un fichier
      .docx.
  type: HowTo
- questions:
  - answer: '`Chart.Series.Add` attend que la longueur du tableau de valeurs soit
      égale au nombre de libellés de l''axe X, et vous devez ajouter exactement une
      série par entrée de légende ; une incompatibilité déclenchera une `ArgumentException`
      à l''exécution.'
    question: Que se passe-t-il si les lignes ou colonnes de `dataMatrix` ne correspondent
      pas aux longueurs de `legendEntries` ou `xLabels` ?
  - answer: Oui — remplacez `ChartType.Column` dans `docBuilder.InsertChart` par tout
      autre `ChartType` (par ex., `ChartType.Line`) et les appels ultérieurs à `Series.Add`
      rempliront le nouveau graphique de la même manière.
    question: Puis-je utiliser un type de graphique différent, comme un graphique
      en courbes, avec la même logique de remplissage des données ?
  - answer: Ajustez les propriétés `Width` et `Height` de l'objet `Shape` renvoyé
      par `InsertChart` (par ex., `chartContainer.Width = 500; chartContainer.Height
      = 300;`).
    question: Comment modifier la taille du graphique après son insertion ?
  - answer: Définissez `chartObj.Series[i].HasDataLabel = true;` pour chaque série
      après l'avoir ajoutée, ou parcourez `chartObj.Series` et activez `HasDataLabel`
      afin d'afficher les valeurs sur le graphique.
    question: Existe-t-il un moyen rapide d'afficher les étiquettes de données sur
      chaque colonne du graphique ?
  type: FAQPage
images:
- /net/programming-with-charts/insert-custom-chart/og-image.png
og_title: Ajouter un graphique en colonnes personnalisé à un document Word
og_description: Remplacez les données par défaut d'un graphique par votre propre tableau et définissez un titre en quelques secondes.
og_image_alt: Capture d'écran montrant un document Word avec un graphique en colonnes personnalisé créé avec Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Insérer un graphique en colonnes personnalisé dans un document Word avec Aspose.Words
Ce tutoriel vous guide dans la création d'un document Word, l'insertion d'un graphique en colonnes, la suppression de ses données par défaut et le remplissage du graphique avec des valeurs personnalisées provenant d'un tableau à deux dimensions — en associant chaque ligne à une série et chaque colonne à une catégorie. Vous verrez également comment ajouter un titre au graphique avant d'enregistrer le fichier. Suivez les étapes pour obtenir un graphique entièrement personnalisé directement dans votre fichier Word.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/insert-custom-chart" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Que se passe-t-il si les lignes ou colonnes de `dataMatrix` ne correspondent pas aux longueurs de `legendEntries` ou `xLabels` ?**  
A: `Chart.Series.Add` attend que la longueur du tableau de valeurs soit égale au nombre de libellés de l'axe X, et vous devez ajouter exactement une série par entrée de légende ; une incompatibilité déclenchera une `ArgumentException` à l'exécution.

**Q: Puis-je utiliser un type de graphique différent, comme un graphique en courbes, avec la même logique de remplissage des données ?**  
A: Oui — remplacez `ChartType.Column` dans `docBuilder.InsertChart` par tout autre `ChartType` (par ex., `ChartType.Line`) et les appels ultérieurs à `Series.Add` rempliront le nouveau graphique de la même manière.

**Q: Comment modifier la taille du graphique après son insertion ?**  
A: Ajustez les propriétés `Width` et `Height` de l'objet `Shape` renvoyé par `InsertChart` (par ex., `chartContainer.Width = 500; chartContainer.Height = 300;`).

**Q: Existe-t-il un moyen rapide d'afficher les étiquettes de données sur chaque colonne du graphique ?**  
A: Définissez `chartObj.Series[i].HasDataLabel = true;` pour chaque série après l'avoir ajoutée, ou parcourez `chartObj.Series` et activez `HasDataLabel` afin d'afficher les valeurs sur le graphique.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}