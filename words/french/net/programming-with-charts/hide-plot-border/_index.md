---
title: Masquer la bordure de la zone de tracé dans un graphique en colonnes avec Aspose.Words for .NET
weight: 410
limit:
description: Apprenez à masquer la bordure de la zone de tracé d’un graphique tout en conservant les lignes d'axes visibles dans un graphique en colonnes Word avec Aspose.Words for .NET.
keywords: [aspose.words for .net, hide plot border, column chart, chart formatting, word document chart, plot area border removal]
url: /net/programming-with-charts/hide-plot-border/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Apprenez à masquer la bordure de la zone de tracé d’un graphique tout
    en conservant les lignes d'axes visibles dans un graphique en colonnes Word avec
    Aspose.Words for .NET.
  headline: Masquer la bordure de la zone de tracé dans un graphique en colonnes avec
    Aspose.Words for .NET
  type: TechArticle
- description: Apprenez à masquer la bordure de la zone de tracé d’un graphique tout
    en conservant les lignes d'axes visibles dans un graphique en colonnes Word avec
    Aspose.Words for .NET.
  name: Masquer la bordure de la zone de tracé dans un graphique en colonnes avec
    Aspose.Words for .NET
  steps:
  - name: Créez un nouveau document Word vide ainsi qu'un DocumentBuilder pour le
      modifier.
    text: Créez un nouveau document Word vide ainsi qu'un DocumentBuilder pour le
      modifier.
  - name: Insérez un graphique en colonnes de 432×252 dans le document et récupérez
      son objet Chart.
    text: Insérez un graphique en colonnes de 432×252 dans le document et récupérez
      son objet Chart.
  - name: Effacez les séries existantes, définissez trois libellés de catégorie et
      ajoutez une série avec des valeurs d'exemple au graphique.
    text: Effacez les séries existantes, définissez trois libellés de catégorie et
      ajoutez une série avec des valeurs d'exemple au graphique.
  - name: Définissez le poids du trait de la zone de tracé à zéro, supprimant ainsi
      sa bordure tout en laissant les lignes d'axes visibles.
    text: Définissez le poids du trait de la zone de tracé à zéro, supprimant ainsi
      sa bordure tout en laissant les lignes d'axes visibles.
  - name: Enregistrez le document modifié dans un fichier .docx.
    text: Enregistrez le document modifié dans un fichier .docx.
  type: HowTo
- questions:
  - answer: La propriété `Stroke` appartient au format global de l’objet `Chart`,
      qui trace la bordure rectangulaire autour de la zone de tracé ; les lignes d'axes
      sont des objets `Axis` distincts et ne sont pas affectées par les paramètres
      `Stroke` du graphique.
    question: Pourquoi le réglage `columnChart.Format.Stroke.Weight = 0` supprime-t-il
      la bordure de la zone de tracé tout en laissant les lignes d'axes visibles ?
  - answer: Non, la propriété `Stroke` contrôle l’ensemble de la bordure de la zone
      de tracé comme un seul rectangle, de sorte que les bordures partielles ne peuvent
      pas être masquées via Aspose.Words ; il faudrait superposer des formes personnalisées
      ou modifier le graphique manuellement.
    question: Puis-je masquer uniquement un côté de la bordure de la zone de tracé
      (par exemple le côté gauche) tout en conservant les trois autres côtés ?
  - answer: Oui, la propriété `Stroke` est indépendante du `ChartType`, ainsi le fait
      de régler son `Weight` à 0 supprime la bordure de la zone de tracé pour les
      graphiques en ligne, en secteur ou tout autre type de graphique pris en charge.
    question: Si je change le type de graphique en ligne ou en secteur, `columnChart.Format.Stroke.Weight
      = 0` masquera-t-il toujours la bordure de la zone de tracé ?
  - answer: Aucun rafraîchissement supplémentaire n’est nécessaire ; la suppression
      des séries et l’ajout d’une nouvelle mettent à jour le graphique en interne,
      et `wordDoc.Save(...)` écrit l’état actuel dans le fichier .docx.
    question: Après avoir appelé `columnChart.Series.Clear()`, dois‑je rafraîchir
      le graphique avant d’enregistrer le document ?
  type: FAQPage
images:
- /net/programming-with-charts/hide-plot-border/og-image.png
og_title: Masquer la bordure de la zone de tracé dans un graphique en colonnes Word
og_description: Supprimez la bordure de la zone de tracé tout en conservant les lignes d'axes visibles dans un graphique en colonnes Word avec Aspose.Words for .NET.
og_image_alt: Guide montrant un document Word contenant un graphique en colonnes où la bordure de la zone de tracé est masquée mais les lignes d'axes restent visibles grâce à Aspose.Words for .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Masquer la bordure de la zone de tracé dans un graphique en colonnes avec Aspose.Words
Dans ce tutoriel, vous apprendrez à générer un document Word, insérer un graphique en colonnes, le remplir avec des données d'exemple, puis masquer la bordure de la zone de tracé du graphique tout en conservant les lignes d'axes visibles. Le code pas à pas montre chaque opération et se termine par l’enregistrement du document, afin que vous puissiez voir le résultat immédiatement.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/hide-plot-border" >}}


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

**Q: Pourquoi le réglage `columnChart.Format.Stroke.Weight = 0` supprime-t-il la bordure de la zone de tracé tout en laissant les lignes d'axes visibles ?**  
A: La propriété `Stroke` appartient au format global de l’objet `Chart`, qui trace la bordure rectangulaire autour de la zone de tracé ; les lignes d'axes sont des objets `Axis` distincts et ne sont pas affectées par les paramètres `Stroke` du graphique.

**Q: Puis-je masquer uniquement un côté de la bordure de la zone de tracé (par exemple le côté gauche) tout en conservant les trois autres côtés ?**  
A: Non, la propriété `Stroke` contrôle l’ensemble de la bordure de la zone de tracé comme un seul rectangle, de sorte que les bordures partielles ne peuvent pas être masquées via Aspose.Words ; il faudrait superposer des formes personnalisées ou modifier le graphique manuellement.

**Q: Si je change le type de graphique en ligne ou en secteur, `columnChart.Format.Stroke.Weight = 0` masquera-t-il toujours la bordure de la zone de tracé ?**  
A: Oui, la propriété `Stroke` est indépendante du `ChartType`, ainsi le fait de régler son `Weight` à 0 supprime la bordure de la zone de tracé pour les graphiques en ligne, en secteur ou tout autre type de graphique pris en charge.

**Q: Après avoir appelé `columnChart.Series.Clear()`, dois‑je rafraîchir le graphique avant d’enregistrer le document ?**  
A: Aucun rafraîchissement supplémentaire n’est nécessaire ; la suppression des séries et l’ajout d’une nouvelle mettent à jour le graphique en interne, et `wordDoc.Save(...)` écrit l’état actuel dans le fichier .docx.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}