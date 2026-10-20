---
title: Supprimer une série de graphique d’un document Word avec Aspose.Words for .NET
weight: 510
limit:
description: Apprenez à supprimer une série de données spécifique d’un graphique en colonnes dans un document Word avec Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, remove chart series, ChartSeriesCollection.RemoveAt, column chart manipulation, Word document chart editing, C# chart series removal]
url: /net/programming-with-charts/remove-chart-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Apprenez à supprimer une série de données spécifique d’un graphique
    en colonnes dans un document Word avec Aspose.Words for .NET.
  headline: Supprimer une série de graphique d’un document Word avec Aspose.Words
    for .NET
  type: TechArticle
- description: Apprenez à supprimer une série de données spécifique d’un graphique
    en colonnes dans un document Word avec Aspose.Words for .NET.
  name: Supprimer une série de graphique d’un document Word avec Aspose.Words for
    .NET
  steps:
  - name: Créez un nouveau Document Word et un DocumentBuilder qui y est lié.
    text: Créez un nouveau Document Word et un DocumentBuilder qui y est lié.
  - name: Insérez un graphique en colonnes de taille 432 × 252 points et récupérez
      l’objet Chart pour une manipulation ultérieure.
    text: Insérez un graphique en colonnes de taille 432 × 252 points et récupérez
      l’objet Chart pour une manipulation ultérieure.
  - name: Définissez l’indice basé sur zéro de la série qui doit être supprimée (la
      deuxième série).
    text: Définissez l’indice basé sur zéro de la série qui doit être supprimée (la
      deuxième série).
  - name: Si l’indice est valide, appelez RemoveAt sur la collection Series du graphique
      pour supprimer cette série.
    text: Si l’indice est valide, appelez RemoveAt sur la collection Series du graphique
      pour supprimer cette série.
  - name: Enregistrez le document mis à jour dans un fichier .docx.
    text: Enregistrez le document mis à jour dans un fichier .docx.
  type: HowTo
- questions:
  - answer: La condition `if` (`targetSeriesIdx < columnChart.Series.Count`) échouera,
      donc `RemoveAt` ne sera jamais appelé et le graphique restera inchangé.
    question: Que se passe-t-il si je passe un indice égal au nombre de séries du
      graphique ?
  - answer: Oui, après `columnChart.Series.RemoveAt`, la légende est régénérée pour
      refléter les séries restantes, de sorte que l’entrée supprimée disparaît de
      la légende.
    question: La suppression d’une série met‑elle automatiquement à jour la légende
      du graphique ?
  - answer: Le code fonctionne pour tout type de graphique qui prend en charge une
      collection `Series` ; il suffit de remplacer `ChartType.Column` par le type
      souhaité lors de l’insertion du graphique.
    question: Puis‑je utiliser le même code pour supprimer une série d’un graphique
      en courbes ou en secteurs ?
  - answer: Un graphique sans série reste un `Shape` valide et sera enregistré, mais
      il apparaîtra vide dans le document résultant.
    question: Si je supprime la seule série d’un graphique, le graphique sera‑t‑il
      toujours enregistré correctement ?
  type: FAQPage
images:
- /net/programming-with-charts/remove-chart-series/og-image.png
og_title: Supprimer une série de graphique dans un document Word
og_description: Guide étape par étape pour retirer une série de données d’un graphique Word en utilisant Aspose.Words for .NET.
og_image_alt: Guide montrant comment supprimer une série de données spécifique d’un graphique en colonnes dans un document Word en utilisant Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Supprimer une série de graphique d’un document Word avec Aspose.Words
Ce tutoriel montre comment créer un document Word, ajouter un graphique en colonnes avec DocumentBuilder, puis supprimer une série de données spécifique de ce graphique en utilisant la méthode ChartSeriesCollection.RemoveAt. À la fin, vous disposerez d’un document enregistré avec la série indésirable supprimée, vous offrant un contrôle précis du contenu du graphique directement depuis le code .NET.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/remove-chart-series" >}}


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

**Q: Que se passe-t-il si je passe un indice égal au nombre de séries du graphique ?**  
A: La condition `if` (`targetSeriesIdx < columnChart.Series.Count`) échouera, donc `RemoveAt` ne sera jamais appelé et le graphique restera inchangé.

**Q: La suppression d’une série met‑elle automatiquement à jour la légende du graphique ?**  
A: Oui, après `columnChart.Series.RemoveAt`, la légende est régénérée pour refléter les séries restantes, de sorte que l’entrée supprimée disparaît de la légende.

**Q: Puis‑je utiliser le même code pour supprimer une série d’un graphique en courbes ou en secteurs ?**  
A: Le code fonctionne pour tout type de graphique qui prend en charge une collection `Series` ; il suffit de remplacer `ChartType.Column` par le type souhaité lors de l’insertion du graphique.

**Q: Si je supprime la seule série d’un graphique, le graphique sera‑t‑il toujours enregistré correctement ?**  
A: Un graphique sans série reste un `Shape` valide et sera enregistré, mais il apparaîtra vide dans le document résultant.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}