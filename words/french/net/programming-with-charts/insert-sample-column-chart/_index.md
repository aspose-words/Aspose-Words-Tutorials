---
title: Insérer un graphique à colonnes d'exemple dans un document Word avec Aspose.Words for .NET
weight: 410
limit:
description: Guide étape par étape pour créer un fichier Word, insérer un graphique à colonnes par défaut avec DocumentBuilder.InsertChart, accéder à l'objet Chart et enregistrer au format .docx.
keywords: [Aspose.Words for .NET, insert column chart, documentbuilder inserchart, create word document with chart, save chart to docx, chart object Aspose.Words]
url: /net/programming-with-charts/insert-sample-column-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Guide étape par étape pour créer un fichier Word, insérer un graphique
    à colonnes par défaut avec DocumentBuilder.InsertChart, accéder à l'objet Chart
    et enregistrer au format .docx.
  headline: Insérer un graphique à colonnes d'exemple dans un document Word avec Aspose.Words
    for .NET
  type: TechArticle
- description: Guide étape par étape pour créer un fichier Word, insérer un graphique
    à colonnes par défaut avec DocumentBuilder.InsertChart, accéder à l'objet Chart
    et enregistrer au format .docx.
  name: Insérer un graphique à colonnes d'exemple dans un document Word avec Aspose.Words
    for .NET
  steps:
  - name: Créez un document Word vide et un DocumentBuilder pour le modifier.
    text: Créez un document Word vide et un DocumentBuilder pour le modifier.
  - name: Insérez un graphique à colonnes de taille 432 × 252 points dans le document.
    text: Insérez un graphique à colonnes de taille 432 × 252 points dans le document.
  - name: Récupérez l'objet Chart à partir de la forme insérée pour une personnalisation
      supplémentaire si nécessaire.
    text: Récupérez l'objet Chart à partir de la forme insérée pour une personnalisation
      supplémentaire si nécessaire.
  - name: Enregistrez le document, qui contient maintenant le graphique à colonnes
      inséré, au format .docx.
    text: Enregistrez le document, qui contient maintenant le graphique à colonnes
      inséré, au format .docx.
  type: HowTo
- questions:
  - answer: Les dimensions sont spécifiées en points (1 point = 1/72 pouce), donc
      432 pt ≈ 6 po et 252 pt ≈ 3,5 po.
    question: Quelles unités sont utilisées pour les paramètres de largeur et de hauteur
      (432, 252) dans InsertChart ?
  - answer: Oui — après l'insertion, vous disposez de l'objet Chart via `chartContainer.Chart` ;
      vous pouvez modifier son SeriesCollection, ses Categories et ses Values pour
      remplacer les données d'exemple.
    question: Puis-je modifier les données du graphique après avoir appelé InsertChart
      avec le jeu de données par défaut ?
  - answer: Il suffit de remplacer `ChartType.Column` par une autre valeur d'énumération
      comme `ChartType.Line` dans l'appel `InsertChart`.
    question: Est-il possible d'insérer un type de graphique différent (par ex., un
      graphique en courbes) en utilisant le même code ?
  - answer: Non—`docBuilder.InsertChart` intègre automatiquement le graphique dans
      une `Shape` ; appeler `wordDoc.Save` écrit le graphique avec le document.
    question: Do I need to call any additional method to embed the chart before saving
      the document?
  type: FAQPage
images:
- /net/programming-with-charts/insert-sample-column-chart/og-image.png
og_title: Insérer un graphique à colonnes d'exemple dans un document Word
og_description: Ajoutez un graphique à colonnes prêt à l'emploi à un document Word avec Aspose.Words for .NET en quelques minutes.
og_image_alt: Capture d'écran montrant un document Word avec un graphique à colonnes d'exemple inséré à l'aide d'Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Insérer un graphique à colonnes d'exemple dans un document Word avec Aspose.Words
Ce tutoriel vous guide dans la création d'un nouveau document Word et l'insertion d'un graphique à colonnes par défaut avec DocumentBuilder.InsertChart. Vous verrez également comment récupérer l'objet Chart intégré pour une manipulation supplémentaire. Enfin, le guide montre comment enregistrer le document au format .docx.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/insert-sample-column-chart" >}}


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

**Q: Quelles unités sont utilisées pour les paramètres de largeur et de hauteur (432, 252) dans InsertChart ?**  
A: Les dimensions sont spécifiées en points (1 point = 1/72 pouce), donc 432 pt ≈ 6 po et 252 pt ≈ 3,5 po.

**Q: Puis-je modifier les données du graphique après avoir appelé InsertChart avec le jeu de données par défaut ?**  
A: Oui — après l'insertion, vous disposez de l'objet Chart via `chartContainer.Chart` ; vous pouvez modifier son SeriesCollection, ses Categories et ses Values pour remplacer les données d'exemple.

**Q: Est-il possible d'insérer un type de graphique différent (par ex., un graphique en courbes) en utilisant le même code ?**  
A: Il suffit de remplacer `ChartType.Column` par une autre valeur d'énumération comme `ChartType.Line` dans l'appel `InsertChart`.

**Q: Do I need to call any additional method to embed the chart before saving the document?**  
A: Non—`docBuilder.InsertChart` intègre automatiquement le graphique dans une `Shape` ; appeler `wordDoc.Save` écrit le graphique avec le document.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}