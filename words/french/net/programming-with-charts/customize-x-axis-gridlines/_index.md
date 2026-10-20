---
title: Personnalisez les lignes de grille de l'axe X dans un graphique en colonnes avec Aspose.Words for .NET
weight: 610
limit:
description: Apprenez à ajouter et à personnaliser la couleur des lignes de grille majeures de l'axe X dans un graphique en colonnes Word avec Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, column chart, customize x axis gridlines, word chart gridlines, primary x axis gridlines, chart formatting .NET]
url: /net/programming-with-charts/customize-x-axis-gridlines/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Apprenez à ajouter et à personnaliser la couleur des lignes de grille
    majeures de l'axe X dans un graphique en colonnes Word avec Aspose.Words for .NET.
  headline: Personnalisez les lignes de grille de l'axe X dans un graphique en colonnes
    avec Aspose.Words for .NET
  type: TechArticle
- description: Apprenez à ajouter et à personnaliser la couleur des lignes de grille
    majeures de l'axe X dans un graphique en colonnes Word avec Aspose.Words for .NET.
  name: Personnalisez les lignes de grille de l'axe X dans un graphique en colonnes
    avec Aspose.Words for .NET
  steps:
  - name: Créez un nouveau document Word et un DocumentBuilder pour le modifier.
    text: Créez un nouveau document Word et un DocumentBuilder pour le modifier.
  - name: Insérez un graphique en colonnes de 432×252 dans le document et obtenez
      son objet Chart.
    text: Insérez un graphique en colonnes de 432×252 dans le document et obtenez
      son objet Chart.
  - name: Supprimez la série par défaut et ajoutez une série personnalisée avec trois
      groupes et valeurs.
    text: Supprimez la série par défaut et ajoutez une série personnalisée avec trois
      groupes et valeurs.
  - name: Obtenez une référence à l'axe horizontal (X) principal du graphique.
    text: Obtenez une référence à l'axe horizontal (X) principal du graphique.
  - name: Activez l'affichage des lignes de grille majeures sur l'axe X principal.
    text: Activez l'affichage des lignes de grille majeures sur l'axe X principal.
  - name: Définissez la couleur des lignes de grille en bleu et leur épaisseur à 2
      points.
    text: Définissez la couleur des lignes de grille en bleu et leur épaisseur à 2
      points.
  - name: Enregistrez le document dans un fichier .docx.
    text: Enregistrez le document dans un fichier .docx.
  type: HowTo
- questions:
  - answer: 'Définissez la même propriété d''axe sur false : `horizontalAxis.HasMajorGridlines
      = false;` bascule la visibilité des lignes de grille majeures de l''axe X.'
    question: Comment masquer à nouveau les lignes de grille majeures après les avoir
      activées ?
  - answer: Non, les paramètres `Format.Stroke` s'appliquent uniquement à l'axe que
      vous modifiez ; pour styliser les lignes de grille de l'axe Y, vous devez ajuster
      séparément `chart.AxisY.Format.Stroke`.
    question: Le fait de modifier `horizontalAxis.Format.Stroke.Color` affectera-t-il
      également les lignes de grille de l'axe Y ?
  - answer: Utilisez `horizontalAxis.Format.Stroke.Weight` et attribuez une valeur
      double (par ex., `0.5`) pour rendre les lignes de grille plus fines.
    question: Quelle propriété contrôle l'épaisseur des lignes de grille majeures
      de l'axe X ?
  - answer: Oui, définissez `horizontalAxis.Format.Stroke.DashStyle` sur une valeur
      d'énumération `DashStyle` telle que `DashStyle.Dash` ou `DashStyle.Dot`.
    question: Puis-je modifier le motif de tirets des lignes de grille majeures de
      l'axe X ?
  type: FAQPage
images:
- /net/programming-with-charts/customize-x-axis-gridlines/og-image.png
og_title: Stylisez les lignes de grille de l'axe X dans un graphique en colonnes Word
og_description: Activez et personnalisez la couleur des lignes de grille de l'axe X principal d'un graphique Word avec Aspose.Words for .NET.
og_image_alt: Guide montrant un document Word avec un graphique en colonnes où les lignes de grille majeures de l'axe X principal sont mises en évidence avec une couleur personnalisée à l'aide d'Aspose.Words for .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Personnalisez les lignes de grille de l'axe X dans un graphique en colonnes avec Aspose.Words
Dans ce tutoriel, vous apprendrez comment créer un document Word, insérer un graphique en colonnes, remplacer ses données par défaut, puis activer les lignes de grille majeures sur l'axe X principal. Vous verrez également comment modifier la couleur des lignes de grille pour qu’elle corresponde à votre conception. Suivez le code étape par étape pour obtenir un contrôle précis sur la visibilité et le style des lignes de grille de l'axe X.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/customize-x-axis-gridlines" >}}


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

**Q: Comment masquer à nouveau les lignes de grille majeures après les avoir activées ?**  
A: Définissez la même propriété d'axe sur false : `horizontalAxis.HasMajorGridlines = false;` bascule la visibilité des lignes de grille majeures de l'axe X.

**Q: Le fait de modifier `horizontalAxis.Format.Stroke.Color` affectera-t-il également les lignes de grille de l'axe Y ?**  
A: Non, les paramètres `Format.Stroke` s'appliquent uniquement à l'axe que vous modifiez ; pour styliser les lignes de grille de l'axe Y, vous devez ajuster séparément `chart.AxisY.Format.Stroke`.

**Q: Quelle propriété contrôle l'épaisseur des lignes de grille majeures de l'axe X ?**  
A: Utilisez `horizontalAxis.Format.Stroke.Weight` et attribuez une valeur double (par ex., `0.5`) pour rendre les lignes de grille plus fines.

**Q: Puis-je modifier le motif de tirets des lignes de grille majeures de l'axe X ?**  
A: Oui, définissez `horizontalAxis.Format.Stroke.DashStyle` sur une valeur d'énumération `DashStyle` telle que `DashStyle.Dash` ou `DashStyle.Dot`.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}