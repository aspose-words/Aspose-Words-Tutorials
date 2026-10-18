---
title: Formater l’axe X secondaire et définir les unités d’affichage en milliers dans les graphiques en courbes Word avec Aspose.Words pour .NET
weight: 710
limit:
description: Créez un graphique en courbes Word, ajoutez un axe X secondaire, définissez son unité d’affichage en milliers et appliquez un format numérique personnalisé avec Aspose.Words pour .NET.
keywords: [secondary axis formatting, Aspose.Words for .NET, line chart axis units, display units thousands, custom numeric format axis, Word chart secondary X axis]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Créez un graphique en courbes Word, ajoutez un axe X secondaire, définissez
    son unité d’affichage en milliers et appliquez un format numérique personnalisé
    avec Aspose.Words pour .NET.
  headline: Formater l’axe X secondaire et définir les unités d’affichage en milliers
    dans les graphiques en courbes Word avec Aspose.Words pour .NET
  type: TechArticle
- description: Créez un graphique en courbes Word, ajoutez un axe X secondaire, définissez
    son unité d’affichage en milliers et appliquez un format numérique personnalisé
    avec Aspose.Words pour .NET.
  name: Formater l’axe X secondaire et définir les unités d’affichage en milliers
    dans les graphiques en courbes Word avec Aspose.Words pour .NET
  steps:
  - name: Créez un nouvel objet Document et un DocumentBuilder pour commencer à construire
      le fichier Word.
    text: Créez un nouvel objet Document et un DocumentBuilder pour commencer à construire
      le fichier Word.
  - name: Insérez un graphique en courbes de taille 500×300 dans le document et récupérez
      l’objet Chart.
    text: Insérez un graphique en courbes de taille 500×300 dans le document et récupérez
      l’objet Chart.
  - name: Supprimez la série de démonstration par défaut qu’Aspose.Words ajoute automatiquement.
    text: Supprimez la série de démonstration par défaut qu’Aspose.Words ajoute automatiquement.
  - name: Définissez un tableau d’étiquettes de catégorie qui seront utilisées pour
      l’axe X.
    text: Définissez un tableau d’étiquettes de catégorie qui seront utilisées pour
      l’axe X.
  - name: Ajoutez la série de données principale nommée "Main Data" en utilisant les
      étiquettes et les valeurs.
    text: Ajoutez la série de données principale nommée "Main Data" en utilisant les
      étiquettes et les valeurs.
  - name: Créez un groupe de séries secondaire de type Line et affectez-le au groupe
      d’axes secondaire.
    text: Créez un groupe de séries secondaire de type Line et affectez-le au groupe
      d’axes secondaire.
  - name: Définissez l’unité d’affichage de l’axe X secondaire sur des milliers afin
      que les valeurs soient affichées en K.
    text: Définissez l’unité d’affichage de l’axe X secondaire sur des milliers afin
      que les valeurs soient affichées en K.
  - name: Appliquez le format numérique personnalisé "#,##0.0" aux graduations de
      l’axe X secondaire.
    text: Appliquez le format numérique personnalisé "#,##0.0" aux graduations de
      l’axe X secondaire.
  - name: Ajoutez éventuellement une série de données auxiliaire au groupe secondaire.
    text: Ajoutez éventuellement une série de données auxiliaire au groupe secondaire.
  - name: Enregistrez le document dans un fichier .docx.
    text: Enregistrez le document dans un fichier .docx.
  type: HowTo
- questions:
  - answer: Non – les paramètres `AxisX` appartiennent au `ChartSeriesGroup`, vous
      pouvez donc définir `secondaryGroup.AxisX.DisplayUnit.Unit` et `secondaryGroup.AxisX.NumberFormat.FormatCode`
      avant ou après l’ajout des séries ; la configuration s’appliquera à l’axe du
      groupe dans les deux cas.
    question: Do I have to add the secondary series before setting the display unit
      and number format on the secondary X‑axis?
  - answer: Oui – affectez n’importe quelle valeur `AxisBuiltInUnit`, par exemple
      `secondaryGroup.AxisX.DisplayUnit.Unit = AxisBuiltInUnit.Millions;` pour afficher
      les valeurs de l’axe en millions au lieu de milliers.
    question: Puis-je utiliser une autre unité intégrée, comme les millions, pour
      l’axe X secondaire ?
  - answer: Non – le code de format est appliqué uniquement à l’axe que vous modifiez
      (`secondaryGroup.AxisX.NumberFormat.FormatCode`), ainsi l’axe X principal conserve
      son format par défaut.
    question: Le format personnalisé `"#,##0.0"` affectera-t-il les étiquettes de
      l’axe X principal ?
  - answer: Le graphique contiendra la série de démonstration par défaut en plus de
      celles que vous ajoutez, ce qui peut entraîner des lignes supplémentaires et
      des catégories incohérentes ; vider la collection garantit que seules les données
      prévues apparaissent.
    question: Que se passe-t-il si j’oublie de vider la série de démonstration avec
      `lineChart.Series.Clear();` ?
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: Formater l’axe X secondaire et définir les unités en milliers
og_description: Ajoutez un axe X secondaire à un graphique en courbes Word et formatez ses étiquettes en milliers avec un motif personnalisé.
og_image_alt: Guide montrant comment ajouter un axe X secondaire à un graphique en courbes Word et formater ses étiquettes pour afficher les unités en milliers en utilisant Aspose.Words pour .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Formater l’axe X secondaire et définir les unités d’affichage en milliers dans les graphiques en courbes Word avec Aspose.Words pour .NET
Ce tutoriel vous guide dans la création d’un document Word contenant un graphique en courbes, l’ajout d’un axe X secondaire et la configuration de cet axe pour afficher les valeurs en milliers. Vous apprendrez également à appliquer un format numérique personnalisé aux étiquettes de l’axe secondaire, ce qui vous donne un contrôle précis sur la présentation des données. Suivez les étapes pour améliorer la lisibilité des graphiques à axes multiples dans vos rapports Word.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/format-secondary-axis" >}}


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

**Q: Do I have to add the secondary series before setting the display unit and number format on the secondary X‑axis?**  
A: Non – les paramètres `AxisX` appartiennent au `ChartSeriesGroup`, vous pouvez donc définir `secondaryGroup.AxisX.DisplayUnit.Unit` et `secondaryGroup.AxisX.NumberFormat.FormatCode` avant ou après l’ajout des séries ; la configuration s’appliquera à l’axe du groupe dans les deux cas.

**Q: Puis-je utiliser une autre unité intégrée, comme les millions, pour l’axe X secondaire ?**  
A: Oui – affectez n’importe quelle valeur `AxisBuiltInUnit`, par exemple `secondaryGroup.AxisX.DisplayUnit.Unit = AxisBuiltInUnit.Millions;` pour afficher les valeurs de l’axe en millions au lieu de milliers.

**Q: Le format personnalisé `"#,##0.0"` affectera-t-il les étiquettes de l’axe X principal ?**  
A: Non – le code de format est appliqué uniquement à l’axe que vous modifiez (`secondaryGroup.AxisX.NumberFormat.FormatCode`), ainsi l’axe X principal conserve son format par défaut.

**Q: Que se passe-t-il si j’oublie de vider la série de démonstration avec `lineChart.Series.Clear();` ?**  
A: Le graphique contiendra la série de démonstration par défaut en plus de celles que vous ajoutez, ce qui peut entraîner des lignes supplémentaires et des catégories incohérentes ; vider la collection garantit que seules les données prévues apparaissent.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}