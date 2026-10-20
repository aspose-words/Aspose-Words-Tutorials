---
title: Définir des étiquettes de données uniformes dans un graphique en colonnes avec Aspose.Words pour .NET
weight: 110
limit:
description: Apprenez à créer un graphique en colonnes Word et à appliquer une taille et une couleur de police uniformes aux étiquettes de données de toutes les séries avec Aspose.Words pour .NET.
keywords: [Aspose.Words for .NET, uniform data labels, chart data label formatting, column chart Word SDK, default data label style, Word document chart customization]
url: /net/programming-with-charts/uniform-data-labels/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Apprenez à créer un graphique en colonnes Word et à appliquer une taille
    et une couleur de police uniformes aux étiquettes de données de toutes les séries
    avec Aspose.Words pour .NET.
  headline: Définir des étiquettes de données uniformes dans un graphique en colonnes
    avec Aspose.Words pour .NET
  type: TechArticle
- description: Apprenez à créer un graphique en colonnes Word et à appliquer une taille
    et une couleur de police uniformes aux étiquettes de données de toutes les séries
    avec Aspose.Words pour .NET.
  name: Définir des étiquettes de données uniformes dans un graphique en colonnes
    avec Aspose.Words pour .NET
  steps:
  - name: Créez un nouveau document Word vide et un DocumentBuilder pour le modifier.
    text: Créez un nouveau document Word vide et un DocumentBuilder pour le modifier.
  - name: Insérez un graphique en colonnes de 500×300 dans le document et récupérez
      son objet Chart.
    text: Insérez un graphique en colonnes de 500×300 dans le document et récupérez
      son objet Chart.
  - name: Supprimez la série d'exemple par défaut qu'Aspose.Words ajoute à un nouveau
      graphique.
    text: Supprimez la série d'exemple par défaut qu'Aspose.Words ajoute à un nouveau
      graphique.
  - name: Définissez les libellés de catégorie et ajoutez deux séries de données (Item
      Alpha et Item Beta) avec leurs valeurs au graphique.
    text: Définissez les libellés de catégorie et ajoutez deux séries de données (Item
      Alpha et Item Beta) avec leurs valeurs au graphique.
  - name: Définissez la taille et la couleur de police de base qui seront appliquées
      à toutes les étiquettes de données.
    text: Définissez la taille et la couleur de police de base qui seront appliquées
      à toutes les étiquettes de données.
  - name: Activez les étiquettes de données pour chaque série, affichez la valeur
      numérique et appliquez la taille et la couleur de police prédéfinies.
    text: Activez les étiquettes de données pour chaque série, affichez la valeur
      numérique et appliquez la taille et la couleur de police prédéfinies.
  - name: Enregistrez le document dans un fichier .docx.
    text: Enregistrez le document dans un fichier .docx.
  type: HowTo
- questions:
  - answer: '`InsertChart` crée un graphique avec une série d’exemple par défaut ;
      la supprimer supprime cet espace réservé afin que le graphique n’affiche que
      les séries que vous ajoutez (`Item Alpha` et `Item Beta`).'
    question: Pourquoi dois‑je appeler `chart.Series.Clear()` avant d’ajouter mes
      propres séries ?
  - answer: Remplacez `Color.White` par n’importe quelle valeur `System.Drawing.Color`,
      par exemple `Color.Black` ou `Color.FromArgb(255, 30, 144, 255)` ; la nouvelle
      couleur est appliquée via `series.DataLabels.Font.Color` dans la boucle.
    question: Comment puis‑je changer la couleur de l’étiquette de données pour une
      couleur autre que le blanc ?
  - answer: Les étiquettes de données seront masquées, de sorte que les paramètres
      de police que vous avez appliqués deviennent invisibles ; vous devez laisser
      `HasDataLabels` à `true` pour que les étiquettes (et leur style) apparaissent.
    question: Que se passe‑t‑il si je définis `series.HasDataLabels = false` après
      avoir configuré la taille et la couleur de la police ?
  - answer: Oui — chaque `ChartSeries` possède son propre objet `DataLabels`, ainsi
      toute série ajoutée après la boucle initiale doit également avoir `HasDataLabels`,
      `ShowValue` et les propriétés de police définies, soit en parcourant à nouveau
      la boucle, soit en extrayant le style dans une méthode d’assistance.
    question: Dois‑je parcourir à nouveau les séries si j’ajoute une autre série plus
      tard dans le code ?
  type: FAQPage
images:
- /net/programming-with-charts/uniform-data-labels/og-image.png
og_title: Appliquer des étiquettes de données uniformes à un graphique Word
og_description: Attribuez rapidement à chaque étiquette de graphique la même taille de police et la même couleur avec Aspose.Words pour .NET.
og_image_alt: Guide présentant un document Word contenant un graphique en colonnes où toutes les étiquettes de données partagent la même taille de police et la même couleur, créé avec Aspose.Words pour .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Définir des étiquettes de données uniformes dans un graphique en colonnes avec Aspose.Words pour .NET
Ce tutoriel montre comment générer un document Word, insérer un graphique en colonnes et ajouter des séries de données personnalisées avec Aspose.Words pour .NET. Il montre ensuite comment définir la taille et la couleur de police par défaut des étiquettes de données afin que chaque série du graphique affiche des libellés identiques. En appliquant un style unique, vous assurez une apparence visuelle cohérente sur l’ensemble du graphique.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/uniform-data-labels" >}}


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

**Q: Pourquoi dois‑je appeler `chart.Series.Clear()` avant d’ajouter mes propres séries ?**  
A: `InsertChart` crée un graphique avec une série d’exemple par défaut ; la supprimer supprime cet espace réservé afin que le graphique n’affiche que les séries que vous ajoutez (`Item Alpha` et `Item Beta`).

**Q: Comment puis‑je changer la couleur de l’étiquette de données pour une couleur autre que le blanc ?**  
A: Remplacez `Color.White` par n’importe quelle valeur `System.Drawing.Color`, par exemple `Color.Black` ou `Color.FromArgb(255, 30, 144, 255)` ; la nouvelle couleur est appliquée via `series.DataLabels.Font.Color` dans la boucle.

**Q: Que se passe‑t‑il si je définis `series.HasDataLabels = false` après avoir configuré la taille et la couleur de la police ?**  
A: Les étiquettes de données seront masquées, de sorte que les paramètres de police que vous avez appliqués deviennent invisibles ; vous devez laisser `HasDataLabels` à `true` pour que les étiquettes (et leur style) apparaissent.

**Q: Dois‑je parcourir à nouveau les séries si j’ajoute une autre série plus tard dans le code ?**  
A: Oui — chaque `ChartSeries` possède son propre objet `DataLabels`, ainsi toute série ajoutée après la boucle initiale doit également avoir `HasDataLabels`, `ShowValue` et les propriétés de police définies, soit en parcourant à nouveau la boucle, soit en extrayant le style dans une méthode d’assistance.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}