---
title: Mettre à jour les données des séries de graphique dans un document Word avec Aspose.Words for .NET
weight: 610
limit:
description: Apprenez à modifier les points de données des séries de graphique dans un document Word et à actualiser le graphique à l’aide d’Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, modify chart series, update chart data points, Word chart manipulation, C# chart editing, column chart in Word]
url: /net/programming-with-charts/modify-chart-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Apprenez à modifier les points de données des séries de graphique dans
    un document Word et à actualiser le graphique à l’aide d’Aspose.Words for .NET.
  headline: Mettre à jour les données des séries de graphique dans un document Word
    avec Aspose.Words for .NET
  type: TechArticle
- description: Apprenez à modifier les points de données des séries de graphique dans
    un document Word et à actualiser le graphique à l’aide d’Aspose.Words for .NET.
  name: Mettre à jour les données des séries de graphique dans un document Word avec
    Aspose.Words for .NET
  steps:
  - name: Créez un nouveau Document, insérez un graphique en colonnes avec un DocumentBuilder,
      puis enregistrez-le comme fichier initial.
    text: Créez un nouveau Document, insérez un graphique en colonnes avec un DocumentBuilder,
      puis enregistrez-le comme fichier initial.
  - name: Ouvrez le fichier enregistré et localisez la forme du graphique pour obtenir
      l'objet Chart existant.
    text: Ouvrez le fichier enregistré et localisez la forme du graphique pour obtenir
      l'objet Chart existant.
  - name: Effacez les valeurs de la première série et ajoutez de nouveaux points,
      puis ajustez la deuxième série en supprimant son premier point et en en ajoutant
      un nouveau.
    text: Effacez les valeurs de la première série et ajoutez de nouveaux points,
      puis ajustez la deuxième série en supprimant son premier point et en en ajoutant
      un nouveau.
  - name: Enregistrez le document modifié dans un nouveau fichier contenant le graphique
      mis à jour.
    text: Enregistrez le document modifié dans un nouveau fichier contenant le graphique
      mis à jour.
  type: HowTo
- questions:
  - answer: Utilisez `document.GetChildNodes(NodeType.Shape, true)` pour obtenir toutes
      les formes, puis filtrez avec `s.HasChart` et choisissez la première (ou celle
      dont vous avez besoin) – cela évite de sélectionner des images ou des zones
      de texte non liées.
    question: Comment puis‑je localiser de manière fiable la forme du graphique dans
      un document qui peut contenir d’autres formes ?
  - answer: '`ClearValues()` supprime les points de données existants ; sans cela,
      les nouveaux points sont ajoutés aux anciens, ce qui peut entraîner des catégories
      en double ou des totaux incorrects.'
    question: Pourquoi dois‑je appeler `ClearValues()` avant d’ajouter de nouveaux
      points à une série ?
  - answer: Utilisez `FromString` lorsque les catégories de l’axe X du graphique sont
      textuelles (par ex., "Group A"), et `FromDouble` lorsque l’axe attend des valeurs
      numériques comme des dates ou des mesures.
    question: Quand faut‑il utiliser `ChartXValue.FromString` plutôt que `ChartXValue.FromDouble`
      pour les valeurs de l’axe X ?
  - answer: Tenter d’accéder à une série inexistante génère une `ArgumentOutOfRangeException` ;
      vérifiez toujours `existingChart.Series.Count` avant de référencer un indice
      spécifique.
    question: Que se passe‑t‑il si le graphique n’a qu’une seule série et que j’essaie
      d’accéder à `existingChart.Series[1]` ?
  - answer: Enregistrer `openedDoc` suffit car c’est l’instance du document qui contient
      le graphique modifié ; le `document` original n’a servi qu’à créer le fichier
      initial.
    question: Dois‑je réenregistrer le `document` original après avoir modifié le
      graphique, ou l’enregistrement de `openedDoc` suffit‑il ?
  type: FAQPage
images:
- /net/programming-with-charts/modify-chart-series/og-image.png
og_title: Modifier les données des séries de graphique dans Word
og_description: Guide étape par étape pour modifier les valeurs des séries d’un graphique dans un fichier Word avec Aspose.Words for .NET.
og_image_alt: Guide montrant un document Word avec un graphique en colonnes avant et après la mise à jour de ses données de séries à l’aide d’Aspose.Words for .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Mettre à jour les données des séries de graphique dans un document Word avec Aspose.Words
Ce tutoriel montre comment créer un document Word contenant un graphique en colonnes, puis rouvrir le fichier, récupérer les séries de graphique existantes, modifier leurs points de données et enregistrer le document afin que le graphique affiche les nouvelles valeurs. Suivez le code étape par étape pour voir à quel point il est simple d’ajuster programmétiquement les données du graphique avec Aspose.Words for .NET.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/modify-chart-series" >}}


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

**Q: Comment puis‑je localiser de manière fiable la forme du graphique dans un document qui peut contenir d’autres formes ?**  
A: Utilisez `document.GetChildNodes(NodeType.Shape, true)` pour obtenir toutes les formes, puis filtrez avec `s.HasChart` et choisissez la première (ou celle dont vous avez besoin) – cela évite de sélectionner des images ou des zones de texte non liées.

**Q: Pourquoi dois‑je appeler `ClearValues()` avant d’ajouter de nouveaux points à une série ?**  
A: `ClearValues()` supprime les points de données existants ; sans cela, les nouveaux points sont ajoutés aux anciens, ce qui peut entraîner des catégories en double ou des totaux incorrects.

**Q: Quand faut‑il utiliser `ChartXValue.FromString` plutôt que `ChartXValue.FromDouble` pour les valeurs de l’axe X ?**  
A: Utilisez `FromString` lorsque les catégories de l’axe X du graphique sont textuelles (par ex., "Group A"), et `FromDouble` lorsque l’axe attend des valeurs numériques comme des dates ou des mesures.

**Q: Que se passe‑t‑il si le graphique n’a qu’une seule série et que j’essaie d’accéder à `existingChart.Series[1]` ?**  
A: Tenter d’accéder à une série inexistante génère une `ArgumentOutOfRangeException` ; vérifiez toujours `existingChart.Series.Count` avant de référencer un indice spécifique.

**Q: Dois‑je réenregistrer le `document` original après avoir modifié le graphique, ou l’enregistrement de `openedDoc` suffit‑il ?**  
A: Enregistrer `openedDoc` suffit car c’est l’instance du document qui contient le graphique modifié ; le `document` original n’a servi qu’à créer le fichier initial.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}