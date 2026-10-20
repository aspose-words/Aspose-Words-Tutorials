---
title: Redimensionner le diagramme proportionnellement lors du changement de taille de page dans Word avec Aspose.Words for .NET
weight: 210
limit:
description: Apprenez à redimensionner automatiquement un diagramme en colonnes Word lors du passage du document à A4 avec Aspose.Words for .NET.
keywords: [chart resizing, Aspose.Words for .NET, Word column chart, automatic chart scaling, A4 page size, resize chart in Word]
url: /net/programming-with-charts/resize-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Apprenez à redimensionner automatiquement un diagramme en colonnes
    Word lors du passage du document à A4 avec Aspose.Words for .NET.
  headline: Redimensionner le diagramme proportionnellement lors du changement de
    taille de page dans Word avec Aspose.Words for .NET
  type: TechArticle
- description: Apprenez à redimensionner automatiquement un diagramme en colonnes
    Word lors du passage du document à A4 avec Aspose.Words for .NET.
  name: Redimensionner le diagramme proportionnellement lors du changement de taille
    de page dans Word avec Aspose.Words for .NET
  steps:
  - name: Créez un nouvel objet Document et un DocumentBuilder pour le modifier.
    text: Créez un nouvel objet Document et un DocumentBuilder pour le modifier.
  - name: Insérez un diagramme en colonnes de taille 432×252 points et récupérez son
      objet Chart.
    text: Insérez un diagramme en colonnes de taille 432×252 points et récupérez son
      objet Chart.
  - name: Définissez le texte du titre du diagramme sur "Quarterly Revenue" et rendez-le
      visible.
    text: Définissez le texte du titre du diagramme sur "Quarterly Revenue" et rendez-le
      visible.
  - name: Enregistrez le document dans un fichier affichant la taille originale du
      diagramme.
    text: Enregistrez le document dans un fichier affichant la taille originale du
      diagramme.
  - name: Modifiez la taille du papier du document en A4 et rafraîchissez la mise
      en page.
    text: Modifiez la taille du papier du document en A4 et rafraîchissez la mise
      en page.
  - name: Calculez une nouvelle largeur de diagramme égale à 80 % de la largeur de
      la page tout en préservant le ratio d'aspect original.
    text: Calculez une nouvelle largeur de diagramme égale à 80 % de la largeur de
      la page tout en préservant le ratio d'aspect original.
  - name: Si la forme contient un diagramme, appliquez la largeur et la hauteur calculées
      pour le redimensionner.
    text: Si la forme contient un diagramme, appliquez la largeur et la hauteur calculées
      pour le redimensionner.
  - name: Enregistrez le document après que le diagramme ait été redimensionné pour
      refléter la nouvelle taille de page.
    text: Enregistrez le document après que le diagramme ait été redimensionné pour
      refléter la nouvelle taille de page.
  type: HowTo
- questions:
  - answer: Oui. Modifier `docBuilder.PageSetup.PaperSize` n'ajuste pas automatiquement
      les formes existantes, vous devez donc recalculer et attribuer vous-même `chartContainer.Width`
      et `Height` comme indiqué.
    question: Dois‑je redimensionner manuellement le diagramme après avoir changé
      la taille du papier du document ?
  - answer: Il stocke `originalAspectRatio = chartContainer.Height / chartContainer.Width`
      puis calcule `newChartHeight = newChartWidth * originalAspectRatio` après avoir
      déterminé la nouvelle largeur.
    question: Comment le code conserve‑t‑il le ratio largeur‑hauteur original du diagramme
      lors du redimensionnement ?
  - answer: '`UpdatePageLayout()` force le moteur de mise en page à réévaluer les
      dimensions de la page, garantissant que `docBuilder.PageSetup.PageWidth` reflète
      la nouvelle largeur A4 avant que la taille du diagramme ne soit recalculée.'
    question: Pourquoi `myDoc.UpdatePageLayout()` est‑il appelé après avoir défini
      la taille du papier à A4 ?
  - answer: La condition `if (chartContainer.HasChart)` empêche le code d'assigner
      `Width` et `Height` lorsqu'aucun diagramme n'est présent, évitant ainsi une
      exception d'exécution.
    question: Que se passe‑t‑il si la forme insérée ne contient pas réellement de
      diagramme ?
  - answer: Absolument — remplacez le multiplicateur `0.8` par n'importe quelle proportion
      que vous préférez ; le reste de la logique de redimensionnement préservera toujours
      le ratio d'aspect original.
    question: Puis‑je modifier le facteur d'échelle de 80 % à une autre valeur ?
  type: FAQPage
images:
- /net/programming-with-charts/resize-chart/og-image.png
og_title: Redimensionner un diagramme Word lors du passage à A4
og_description: Gardez votre diagramme proportionnel en le redimensionnant automatiquement après avoir changé le document en A4.
og_image_alt: Capture d'écran montrant un diagramme en colonnes redimensionné automatiquement pour s'adapter à un document Word au format A4 avec Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Redimensionner le diagramme proportionnellement lors du changement de taille de page dans Word avec Aspose.Words
Ce tutoriel montre comment insérer un diagramme en colonnes dans un document Word, passer la taille de page du document à A4 et faire en sorte que le diagramme se redimensionne automatiquement afin de rester proportionnel à la nouvelle largeur de page. En suivant les étapes, vous verrez le diagramme ajuster ses dimensions sans mise à l'échelle manuelle, garantissant une mise en page cohérente sur différents formats de page.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/resize-chart" >}}


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

**Q: Dois‑je redimensionner manuellement le diagramme après avoir changé la taille du papier du document ?**  
A: Oui. Modifier `docBuilder.PageSetup.PaperSize` n'ajuste pas automatiquement les formes existantes, vous devez donc recalculer et attribuer vous-même `chartContainer.Width` et `Height` comme indiqué.

**Q: Comment le code conserve‑t‑il le ratio largeur‑hauteur original du diagramme lors du redimensionnement ?**  
A: Il stocke `originalAspectRatio = chartContainer.Height / chartContainer.Width` puis calcule `newChartHeight = newChartWidth * originalAspectRatio` après avoir déterminé la nouvelle largeur.

**Q: Pourquoi `myDoc.UpdatePageLayout()` est‑il appelé après avoir défini la taille du papier à A4 ?**  
A: `UpdatePageLayout()` force le moteur de mise en page à réévaluer les dimensions de la page, garantissant que `docBuilder.PageSetup.PageWidth` reflète la nouvelle largeur A4 avant que la taille du diagramme ne soit recalculée.

**Q: Que se passe‑t‑il si la forme insérée ne contient pas réellement de diagramme ?**  
A: La condition `if (chartContainer.HasChart)` empêche le code d'assigner `Width` et `Height` lorsqu'aucun diagramme n'est présent, évitant ainsi une exception d'exécution.

**Q: Puis‑je modifier le facteur d'échelle de 80 % à une autre valeur ?**  
A: Absolument — remplacez le multiplicateur `0.8` par n'importe quelle proportion que vous préférez ; le reste de la logique de redimensionnement préservera toujours le ratio d'aspect original.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}