---
title: Ajouter une série de données nommée à un graphique histogramme dans Word en utilisant Aspose.Words for .NET
weight: 610
limit:
description: Apprenez à intégrer un graphique histogramme dans un document Word et à ajouter une série de données nommée avec Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, add named series chart, histogram chart in Word, ChartSeriesCollection Add overload, DocumentBuilder chart example, named data series Word]
url: /net/programming-with-charts/add-named-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Apprenez à intégrer un graphique histogramme dans un document Word
    et à ajouter une série de données nommée avec Aspose.Words for .NET.
  headline: Ajouter une série de données nommée à un graphique histogramme dans Word
    en utilisant Aspose.Words for .NET
  type: TechArticle
- description: Apprenez à intégrer un graphique histogramme dans un document Word
    et à ajouter une série de données nommée avec Aspose.Words for .NET.
  name: Ajouter une série de données nommée à un graphique histogramme dans Word en
    utilisant Aspose.Words for .NET
  steps:
  - name: Créez un nouveau document Word vide ainsi qu’un DocumentBuilder pour le
      modifier.
    text: Créez un nouveau document Word vide ainsi qu’un DocumentBuilder pour le
      modifier.
  - name: Insérez une forme de graphique histogramme de taille 500×300 dans le document
      et récupérez son objet Chart.
    text: Insérez une forme de graphique histogramme de taille 500×300 dans le document
      et récupérez son objet Chart.
  - name: Supprimez la série de remplissage par défaut qu’Aspose.Words ajoute aux
      nouveaux graphiques.
    text: Supprimez la série de remplissage par défaut qu’Aspose.Words ajoute aux
      nouveaux graphiques.
  - name: Ajoutez une série nommée « Demo Series » avec les points de données spécifiés
      au graphique histogramme.
    text: Ajoutez une série nommée « Demo Series » avec les points de données spécifiés
      au graphique histogramme.
  - name: Enregistrez le document dans un fichier .docx contenant la série de graphique
      étiquetée.
    text: Enregistrez le document dans un fichier .docx contenant la série de graphique
      étiquetée.
  type: HowTo
- questions:
  - answer: '`InsertChart` crée une série de remplissage par défaut ; la nettoyer
      supprime cette série vide afin que le graphique n’affiche que les données que
      vous ajoutez avec `Series.Add`.'
    question: Pourquoi dois‑je appeler `histogramChart.Series.Clear()` avant d’ajouter
      ma propre série ?
  - answer: Oui, appelez `histogramChart.Series.Add` plusieurs fois, chaque appel
      avec un nom distinct et des valeurs `double[] `; chaque série sera répertoriée
      dans la légende du graphique avec le nom fourni.
    question: Puis‑je ajouter plusieurs séries en utilisant la même surcharge, et
      chaque série apparaîtra‑t‑elle avec son propre libellé ?
  - answer: La surcharge attend un `double[]` ; si vous avez un `int[]` ou d’autres
      tableaux numériques, convertissez‑les ou cast‑les en `double[]` avant de les
      passer.
    question: L’argument `double[]` est‑il le seul type accepté pour les points de
      données ?
  - answer: La chaîne passée en premier argument (par ex., "Demo Series") est utilisée
      comme titre de la série et est affichée dans la légende du graphique par défaut.
    question: Le nom de série que je fournis apparaîtra‑t‑il automatiquement dans
      le graphique ?
  type: FAQPage
images:
- /net/programming-with-charts/add-named-series/og-image.png
og_title: Ajouter une série nommée à un graphique histogramme Word
og_description: Étiquetez rapidement une série de graphique dans Word avec Aspose.Words et voyez-la rendue instantanément.
og_image_alt: Capture d’écran montrant un document Word avec un graphique histogramme incluant une série de données étiquetée créée avec Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ajouter une série de données nommée à un graphique histogramme dans Word en utilisant Aspose.Words
Ce tutoriel montre comment créer un document Word avec Aspose.Words for .NET, insérer un graphique histogramme et ajouter une série de données étiquetée en utilisant la surcharge ChartSeriesCollection.Add qui accepte un nom et des valeurs. En nommant la série, vous pouvez identifier clairement chaque jeu de données dans le graphique, ce qui rend la sortie visuelle plus facile à lire et à interpréter.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/add-named-series" >}}


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

**Q: Pourquoi dois‑je appeler `histogramChart.Series.Clear()` avant d’ajouter ma propre série ?**  
A: `InsertChart` crée une série de remplissage par défaut ; la nettoyer supprime cette série vide afin que le graphique n’affiche que les données que vous ajoutez avec `Series.Add`.

**Q: Puis‑je ajouter plusieurs séries en utilisant la même surcharge, et chaque série apparaîtra‑t‑elle avec son propre libellé ?**  
A: Oui, appelez `histogramChart.Series.Add` plusieurs fois, chaque appel avec un nom distinct et des valeurs `double[] `; chaque série sera répertoriée dans la légende du graphique avec le nom fourni.

**Q: L’argument `double[]` est‑il le seul type accepté pour les points de données ?**  
A: La surcharge attend un `double[]` ; si vous avez un `int[]` ou d’autres tableaux numériques, convertissez‑les ou cast‑les en `double[]` avant de les passer.

**Q: Le nom de série que je fournis apparaîtra‑t‑il automatiquement dans le graphique ?**  
A: La chaîne passée en premier argument (par ex., "Demo Series") est utilisée comme titre de la série et est affichée dans la légende du graphique par défaut.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}