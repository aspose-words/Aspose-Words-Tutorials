---
title: Ajouter des numéros de page au pied de page d'un document Word avec Aspose.Words pour .NET
weight: 210
limit:
description: Ajoutez des numéros de page qui se mettent à jour automatiquement au pied de page principal d'un document Word en utilisant Aspose.Words pour .NET.
keywords: [Aspose.Words for .NET, add page numbers, word document footer, documentbuilder page numbers, automatic page numbering, c# aspose.words]
url: /net/working-with-headers-and-footers/add-page-numbers/
date: '2026-09-22'
lastmod: '2026-09-22'
schemas:
- author: Aspose
  dateModified: '2026-09-22'
  description: Ajoutez des numéros de page qui se mettent à jour automatiquement au
    pied de page principal d'un document Word en utilisant Aspose.Words pour .NET.
  headline: Ajouter des numéros de page au pied de page d'un document Word avec Aspose.Words
    pour .NET
  type: TechArticle
- description: Ajoutez des numéros de page qui se mettent à jour automatiquement au
    pied de page principal d'un document Word en utilisant Aspose.Words pour .NET.
  name: Ajouter des numéros de page au pied de page d'un document Word avec Aspose.Words
    pour .NET
  steps:
  - name: Créez un nouvel objet Document et un DocumentBuilder qui y est lié.
    text: Créez un nouvel objet Document et un DocumentBuilder qui y est lié.
  - name: Déplacez le curseur du builder vers le pied de page principal de la première
      section.
    text: Déplacez le curseur du builder vers le pied de page principal de la première
      section.
  - name: Définissez l'alignement du paragraphe sur centré afin que le texte du pied
      de page soit centré.
    text: Définissez l'alignement du paragraphe sur centré afin que le texte du pied
      de page soit centré.
  - name: Écrivez le libellé "Page " et insérez un champ PAGE qui affiche le numéro
      de page actuel.
    text: Écrivez le libellé "Page " et insérez un champ PAGE qui affiche le numéro
      de page actuel.
  - name: Écrivez " de " et insérez un champ NUMPAGES qui indique le nombre total
      de pages.
    text: Écrivez " de " et insérez un champ NUMPAGES qui indique le nombre total
      de pages.
  - name: Enregistrez le document dans un fichier .docx.
    text: Enregistrez le document dans un fichier .docx.
  type: HowTo
- questions:
  - answer: Non. `MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` déplace le builder
      uniquement vers le pied de page principal de la *première* section, de sorte
      que les champs y sont insérés uniquement.
    question: Si le document comporte plus d'une section, ce code ajoutera-t-il des
      numéros de page au pied de page de chaque section ?
  - answer: Définissez `builder.ParagraphFormat.Alignment` sur une autre valeur `ParagraphAlignment`
      (par ex., `ParagraphAlignment.Right`) avant d'écrire les champs.
    question: Comment puis‑je modifier l'alignement du paragraphe du numéro de page
      dans le pied de page ?
  - answer: '`InsertField` prend le code du champ et un résultat de champ optionnel ;
      passer `null` indique à Aspose.Words de laisser Word calculer le résultat à
      l''exécution.'
    question: Que représente l'argument `null` dans `InsertField("PAGE", null)` ?
  - answer: Oui — remplacez `HeaderFooterType.FooterPrimary` par `HeaderFooterType.HeaderPrimary`
      (ou un autre type d'en-tête) avant d'insérer les champs.
    question: Puis‑je placer les mêmes champs "Page X de Y" dans l'en-tête au lieu
      du pied de page ?
  type: FAQPage
images:
- /net/working-with-headers-and-footers/add-page-numbers/og-image.png
og_title: Insérer des numéros de page automatiques dans le pied de page Word
og_description: Code étape par étape pour ajouter des numéros de page dynamiques à un pied de page Word avec Aspose.Words pour .NET.
og_image_alt: Guide montrant comment ajouter des numéros de page automatiques au pied de page d'un document Word avec Aspose.Words pour .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ajouter des numéros de page au pied de page d'un document Word avec Aspose.Words pour .NET
Ce tutoriel montre comment utiliser Aspose.Words Document et DocumentBuilder pour insérer des numéros de page qui se mettent à jour automatiquement dans le pied de page principal d'un document Word. En ajoutant les numéros de page par programme, vous garantissez une pagination cohérente dans tout le fichier sans modification manuelle. Le code d'exemple est prêt à être exécuté dans un environnement .NET.

---

{{< tutorial-widget sourcePath="words/net/working-with-headers-and-footers/add-page-numbers" >}}


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
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Si le document comporte plus d'une section, ce code ajoutera-t-il des numéros de page au pied de page de chaque section ?**  
A: Non. `MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` déplace le builder uniquement vers le pied de page principal de la *première* section, de sorte que les champs y sont insérés uniquement.

**Q: Comment puis‑je modifier l'alignement du paragraphe du numéro de page dans le pied de page ?**  
A: Définissez `builder.ParagraphFormat.Alignment` sur une autre valeur `ParagraphAlignment` (par ex., `ParagraphAlignment.Right`) avant d'écrire les champs.

**Q: Que représente l'argument `null` dans `InsertField("PAGE", null)` ?**  
A: `InsertField` prend le code du champ et un résultat de champ optionnel ; passer `null` indique à Aspose.Words de laisser Word calculer le résultat à l'exécution.

**Q: Puis‑je placer les mêmes champs "Page X de Y" dans l'en-tête au lieu du pied de page ?**  
A: Oui — remplacez `HeaderFooterType.FooterPrimary` par `HeaderFooterType.HeaderPrimary` (ou un autre type d'en-tête) avant d'insérer les champs.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}