---
title: Créer un tableau à texte pivoté dans un document Word en utilisant Aspose.Words pour .NET
weight: 110
limit:
description: Apprenez à créer un tableau Word avec des largeurs de colonne fixes, du texte pivoté, des hauteurs de ligne précises et des cellules remplies en utilisant Aspose.Words pour .NET.
keywords: [Aspose.Words for .NET, rotated text table, fixed column widths, vertical alignment Aspose.Words, set row height Word, populate table cells .NET]
url: /net/add-content-using-documentbuilder/create-rotated-text-table/
date: '2026-09-16'
lastmod: '2026-09-16'
schemas:
- author: Aspose
  dateModified: '2026-09-16'
  description: Apprenez à créer un tableau Word avec des largeurs de colonne fixes,
    du texte pivoté, des hauteurs de ligne précises et des cellules remplies en utilisant
    Aspose.Words pour .NET.
  headline: Créer un tableau à texte pivoté dans un document Word en utilisant Aspose.Words
    pour .NET
  type: TechArticle
- description: Apprenez à créer un tableau Word avec des largeurs de colonne fixes,
    du texte pivoté, des hauteurs de ligne précises et des cellules remplies en utilisant
    Aspose.Words pour .NET.
  name: Créer un tableau à texte pivoté dans un document Word en utilisant Aspose.Words
    pour .NET
  steps:
  - name: Instanciez un nouveau Document et un DocumentBuilder qui seront utilisés
      pour construire le tableau.
    text: Instanciez un nouveau Document et un DocumentBuilder qui seront utilisés
      pour construire le tableau.
  - name: Démarrez un nouveau tableau, insérez la première cellule et fixez les largeurs
      de colonne afin qu'elles ne s'ajustent pas automatiquement.
    text: Démarrez un nouveau tableau, insérez la première cellule et fixez les largeurs
      de colonne afin qu'elles ne s'ajustent pas automatiquement.
  - name: Alignez le contenu verticalement au centre dans la cellule actuelle et écrivez
      le texte de la première cellule de la première ligne.
    text: Alignez le contenu verticalement au centre dans la cellule actuelle et écrivez
      le texte de la première cellule de la première ligne.
  - name: Insérez la deuxième cellule de la première ligne et écrivez son texte.
    text: Insérez la deuxième cellule de la première ligne et écrivez son texte.
  - name: Fermez la première ligne, finalisant sa mise en page.
    text: Fermez la première ligne, finalisant sa mise en page.
  - name: Démarrez la première cellule de la deuxième ligne, définissez la hauteur
      de la ligne à exactement 100 points, faites pivoter le texte vers le haut et
      écrivez le texte de la cellule.
    text: Démarrez la première cellule de la deuxième ligne, définissez la hauteur
      de la ligne à exactement 100 points, faites pivoter le texte vers le haut et
      écrivez le texte de la cellule.
  - name: Insérez la deuxième cellule de la deuxième ligne, faites pivoter son texte
      vers le bas et écrivez le texte de la cellule.
    text: Insérez la deuxième cellule de la deuxième ligne, faites pivoter son texte
      vers le bas et écrivez le texte de la cellule.
  - name: Fermez la deuxième ligne, complétant la seconde rangée du tableau.
    text: Fermez la deuxième ligne, complétant la seconde rangée du tableau.
  - name: Terminez la construction du tableau, scellant la structure du tableau.
    text: Terminez la construction du tableau, scellant la structure du tableau.
  - name: Enregistrez le document complet dans un fichier .docx.
    text: Enregistrez le document complet dans un fichier .docx.
  type: HowTo
- questions:
  - answer: Après avoir fixé les largeurs de colonne, attribuez une largeur à chaque
      cellule en utilisant `builder.CellFormat.Width = <valueInPoints>;` avant d'insérer
      la cellule suivante ; le tableau conservera ces largeurs exactes.
    question: Comment puis‑je définir des largeurs de colonne spécifiques après avoir
      appelé `table.AutoFit(AutoFitBehavior.FixedColumnWidths)` ?
  - answer: '`builder.CellFormat.VerticalAlignment` est un paramètre au niveau de
      la cellule, vous devez donc le définir à nouveau pour les cellules de la deuxième
      ligne (par ex., `builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;`)
      avant d''écrire leur contenu.'
    question: Pourquoi l'alignement vertical n'affecte-t-il que la première ligne
      et pas la deuxième ?
  - answer: Oui — définissez `builder.RowFormat.Height` et `builder.RowFormat.HeightRule
      = HeightRule.Exactly` avant chaque appel à `builder.EndRow();` ; la ligne suivante
      peut avoir une valeur de hauteur différente.
    question: Puis‑je attribuer à chaque ligne une hauteur exacte différente, et si
      oui, comment ?
  - answer: Réinitialisez l'orientation en assignant `builder.CellFormat.Orientation
      = TextOrientation.Horizontal;` avant d'écrire dans la cellule suivante.
    question: Comment rétablir l'orientation du texte par défaut après avoir utilisé
      `TextOrientation.Upward` ou `Downward` ?
  type: FAQPage
images:
- /net/add-content-using-documentbuilder/create-rotated-text-table/og-image.png
og_title: Créer un tableau à texte pivoté dans Word avec Aspose.Words
og_description: Code étape par étape pour créer un tableau à largeur fixe avec du texte verticalement pivoté et des hauteurs de ligne exactes.
og_image_alt: Capture d'écran montrant un document Word avec un tableau qui a des largeurs de colonne fixes, du texte pivoté dans les cellules et des hauteurs de ligne définies, créé en utilisant Aspose.Words pour .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Créer un tableau à texte pivoté dans un document Word en utilisant Aspose.Words pour .NET
Ce tutoriel montre comment générer un document Word et ajouter un tableau dont les colonnes ont des largeurs fixes, les lignes des hauteurs exactes, et le texte des cellules est pivoté verticalement. Vous apprendrez à définir l'alignement vertical, appliquer l'orientation du texte, remplir chaque cellule avec du contenu, puis enregistrer le document — le tout avec Aspose.Words pour .NET.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/create-rotated-text-table" >}}


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
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Comment puis‑je définir des largeurs de colonne spécifiques après avoir appelé `table.AutoFit(AutoFitBehavior.FixedColumnWidths)` ?**  
A: Après avoir fixé les largeurs de colonne, attribuez une largeur à chaque cellule en utilisant `builder.CellFormat.Width = <valueInPoints>;` avant d'insérer la cellule suivante ; le tableau conservera ces largeurs exactes.

**Q: Pourquoi l'alignement vertical n'affecte-t-il que la première ligne et pas la deuxième ?**  
A: `builder.CellFormat.VerticalAlignment` est un paramètre au niveau de la cellule, vous devez donc le définir à nouveau pour les cellules de la deuxième ligne (par ex., `builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;`) avant d'écrire leur contenu.

**Q: Puis‑je attribuer à chaque ligne une hauteur exacte différente, et si oui, comment ?**  
A: Oui — définissez `builder.RowFormat.Height` et `builder.RowFormat.HeightRule = HeightRule.Exactly` avant chaque appel à `builder.EndRow();` ; la ligne suivante peut avoir une valeur de hauteur différente.

**Q: Comment rétablir l'orientation du texte par défaut après avoir utilisé `TextOrientation.Upward` ou `Downward` ?**  
A: Réinitialisez l'orientation en assignant `builder.CellFormat.Orientation = TextOrientation.Horizontal;` avant d'écrire dans la cellule suivante.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}