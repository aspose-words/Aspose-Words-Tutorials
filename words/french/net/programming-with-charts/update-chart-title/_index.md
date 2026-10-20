---
title: Mettre à jour le titre du graphique et basculer la visibilité de la légende dans Word avec Aspose.Words for .NET
weight: 810
limit:
description: Apprenez à modifier le titre d'un graphique et à contrôler la visibilité de la légende dans un document Word avec Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, update chart title, toggle legend visibility, word chart manipulation, c# chart title, aspose words chart legend]
url: /net/programming-with-charts/update-chart-title/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Apprenez à modifier le titre d'un graphique et à contrôler la visibilité
    de la légende dans un document Word avec Aspose.Words for .NET.
  headline: Mettre à jour le titre du graphique et basculer la visibilité de la légende
    dans Word avec Aspose.Words for .NET
  type: TechArticle
- description: Apprenez à modifier le titre d'un graphique et à contrôler la visibilité
    de la légende dans un document Word avec Aspose.Words for .NET.
  name: Mettre à jour le titre du graphique et basculer la visibilité de la légende
    dans Word avec Aspose.Words for .NET
  steps:
  - name: Définissez le titre du graphique fourni par l'utilisateur et indiquez si
      la légende doit être affichée.
    text: Définissez le titre du graphique fourni par l'utilisateur et indiquez si
      la légende doit être affichée.
  - name: Créez un nouveau document Word et un DocumentBuilder pour ajouter du contenu.
    text: Créez un nouveau document Word et un DocumentBuilder pour ajouter du contenu.
  - name: Insérez un graphique en colonnes de 432 × 252 pt dans le document et vérifiez
      que la forme contient réellement un graphique.
    text: Insérez un graphique en colonnes de 432 × 252 pt dans le document et vérifiez
      que la forme contient réellement un graphique.
  - name: Récupérez l'objet Chart, définissez le texte de son titre avec la valeur
      fournie par l'utilisateur et assurez-vous que le titre est affiché.
    text: Récupérez l'objet Chart, définissez le texte de son titre avec la valeur
      fournie par l'utilisateur et assurez-vous que le titre est affiché.
  - name: 'Configurez la légende : affichez‑la à droite si demandé, sinon masquez‑la,
      et autorisez‑la à chevaucher la zone du tracé.'
    text: 'Configurez la légende : affichez‑la à droite si demandé, sinon masquez‑la,
      et autorisez‑la à chevaucher la zone du tracé.'
  - name: Enregistrez le document modifié sur le disque sous le nom CustomChart.docx.
    text: Enregistrez le document modifié sur le disque sous le nom CustomChart.docx.
  type: HowTo
- questions:
  - answer: Lorsque `displayLegend` est `true`, le code définit `chartLegend.Position`
      sur `LegendPosition.Right`, rendant la légende visible du côté droit de la zone
      du tracé ; la propriété `Overlay` reste à `true`, ce qui permet à la légende
      de chevaucher le graphique pour gagner de l'espace.
    question: Que change le fait de définir `displayLegend` à `true` dans le graphique
      généré ?
  - answer: Définissez `chartTitle.Show = false` (ou omettez simplement de définir
      `Show` à `true`) après avoir assigné `chartTitle.Text` ; le titre ne sera pas
      rendu dans le document Word.
    question: Comment puis‑je masquer le titre du graphique si l'utilisateur n'en
      fournit pas ?
  - answer: Oui — `InsertChart` renvoie un `Shape` qui devrait contenir un graphique,
      mais vérifier `HasChart` garantit que la forme contient réellement un objet
      `Chart` ; sinon le code lève une `InvalidOperationException`.
    question: Est‑il nécessaire de vérifier `chartContainer.HasChart` après avoir
      appelé `InsertChart` ?
  - answer: Absolument ; assignez n'importe quelle valeur de l'énumération `LegendPosition`
      (par ex. `LegendPosition.Top`, `LegendPosition.Bottom`, `LegendPosition.Left`)
      à `chartLegend.Position` pour repositionner la légende selon vos besoins.
    question: Puis‑je placer la légende ailleurs que du côté droit ?
  type: FAQPage
images:
- /net/programming-with-charts/update-chart-title/og-image.png
og_title: Modifier le titre du graphique et la légende dans Word
og_description: Apprenez à définir un titre de graphique personnalisé et à contrôler l'affichage de la légende dans un document Word avec Aspose.Words for .NET.
og_image_alt: Guide présentant le code qui met à jour le titre d'un graphique et bascule la légende dans un document Word en utilisant Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Mettre à jour le titre du graphique et basculer la visibilité de la légende dans Word avec Aspose.Words
Ce tutoriel montre comment modifier programmétiquement un graphique dans un document Word avec Aspose.Words for .NET. Vous apprendrez à insérer un graphique en colonnes, à remplacer son titre par le texte fourni par l'utilisateur et à contrôler la visibilité et le chevauchement de la légende selon les préférences de l'utilisateur. Ces étapes vous permettent d'adapter dynamiquement la présentation du graphique sans modification manuelle.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/update-chart-title" >}}


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

**Q: Que change le fait de définir `displayLegend` à `true` dans le graphique généré ?**  
A: Lorsque `displayLegend` est `true`, le code définit `chartLegend.Position` sur `LegendPosition.Right`, rendant la légende visible du côté droit de la zone du tracé ; la propriété `Overlay` reste à `true`, ce qui permet à la légende de chevaucher le graphique pour gagner de l'espace.

**Q: Comment puis‑je masquer le titre du graphique si l'utilisateur n'en fournit pas ?**  
A: Définissez `chartTitle.Show = false` (ou omettez simplement de définir `Show` à `true`) après avoir assigné `chartTitle.Text` ; le titre ne sera pas rendu dans le document Word.

**Q: Est‑il nécessaire de vérifier `chartContainer.HasChart` après avoir appelé `InsertChart` ?**  
A: Oui — `InsertChart` renvoie un `Shape` qui devrait contenir un graphique, mais vérifier `HasChart` garantit que la forme contient réellement un objet `Chart` ; sinon le code lève une `InvalidOperationException`.

**Q: Puis‑je placer la légende ailleurs que du côté droit ?**  
A: Absolument ; assignez n'importe quelle valeur de l'énumération `LegendPosition` (par ex. `LegendPosition.Top`, `LegendPosition.Bottom`, `LegendPosition.Left`) à `chartLegend.Position` pour repositionner la légende selon vos besoins.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}