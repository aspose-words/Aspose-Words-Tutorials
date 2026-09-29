---
title: Ajouter un filigrane texte rouge diagonal aux documents Word avec Aspose.Words for .NET
weight: 110
limit:
description: Appliquer automatiquement un filigrane texte rouge en diagonale à chaque fichier Word généré dans un lot en utilisant Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, text watermark, red diagonal watermark, batch document generation, DocumentBuilder watermark, automated report]
url: /net/programming-with-watermark/add-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Appliquer automatiquement un filigrane texte rouge en diagonale à chaque
    fichier Word généré dans un lot en utilisant Aspose.Words for .NET.
  headline: Ajouter un filigrane texte rouge diagonal aux documents Word avec Aspose.Words
    for .NET
  type: TechArticle
- description: Appliquer automatiquement un filigrane texte rouge en diagonale à chaque
    fichier Word généré dans un lot en utilisant Aspose.Words for .NET.
  name: Ajouter un filigrane texte rouge diagonal aux documents Word avec Aspose.Words
    for .NET
  steps:
  - name: Créez le dossier "GeneratedReports" où les fichiers de sortie seront enregistrés.
    text: Créez le dossier "GeneratedReports" où les fichiers de sortie seront enregistrés.
  - name: Démarrez une boucle qui générera trois documents distincts.
    text: Démarrez une boucle qui générera trois documents distincts.
  - name: Créez un nouvel objet document Word vide.
    text: Créez un nouvel objet document Word vide.
  - name: Utilisez DocumentBuilder pour écrire une ligne de titre et une description
      dans le document.
    text: Utilisez DocumentBuilder pour écrire une ligne de titre et une description
      dans le document.
  - name: Définissez l'apparence du filigrane, y compris la police, la taille, la
      couleur et la disposition diagonale.
    text: Définissez l'apparence du filigrane, y compris la police, la taille, la
      couleur et la disposition diagonale.
  - name: Appliquez le filigrane rouge diagonal configuré avec le texte "PROTECTED"
      au document.
    text: Appliquez le filigrane rouge diagonal configuré avec le texte "PROTECTED"
      au document.
  - name: Enregistrez le document filigrané dans le dossier "GeneratedReports" avec
      un nom de fichier unique.
    text: Enregistrez le document filigrané dans le dossier "GeneratedReports" avec
      un nom de fichier unique.
  - name: Fermez la boucle après le traitement du document actuel.
    text: Fermez la boucle après le traitement du document actuel.
  type: HowTo
- questions:
  - answer: IsSemitrasparent détermine si le filigrane est rendu avec une opacité
      partielle ; le régler sur **true** rend le texte semi‑transparent afin que le
      contenu sous-jacent reste plus lisible.
    question: Que contrôle l'option **IsSemitrasparent** et quel effet a le fait de
      la régler sur **true** ?
  - answer: Oui — définissez la propriété **Layout** sur **WatermarkLayout.Horizontal**
      dans **TextWatermarkOptions** avant d’appeler **document.Watermark.SetText**.
    question: Puis-je changer l'orientation du filigrane en horizontal au lieu de
      diagonal ?
  - answer: L’extrait crée une nouvelle instance de **Document**, mais vous pouvez
      ouvrir n’importe quel fichier existant (par ex., `new Document("Existing.docx")`)
      puis appeler **document.Watermark.SetText** pour appliquer le même filigrane.
    question: Ce code ajoutera-t-il un filigrane à un fichier Word existant ou uniquement
      aux documents nouvellement créés ?
  - answer: Attribuez une couleur personnalisée avec **Color.FromArgb(red, green,
      blue)** à la propriété **Color** de **TextWatermarkOptions**, par ex., `Color
      = Color.FromArgb(128, 0, 128)` pour du violet.
    question: Comment puis‑je utiliser une couleur RVB personnalisée pour le filigrane
      au lieu du **Color.Red** prédéfini ?
  type: FAQPage
images:
- /net/programming-with-watermark/add-text-watermark/og-image.png
og_title: Ajouter un filigrane texte rouge diagonal aux documents Word
og_description: Découvrez comment appliquer automatiquement un filigrane rouge diagonal à chaque document Word dans un lot avec Aspose.Words.
og_image_alt: Guide montrant comment ajouter un filigrane texte rouge diagonal aux documents Word en utilisant Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ajouter un filigrane texte rouge diagonal aux documents Word avec Aspose.Words
Ce tutoriel montre comment intégrer automatiquement un filigrane texte rouge en diagonale dans chaque document Word créé lors d'une génération de rapports par lots. En utilisant les classes Document et DocumentBuilder d'Aspose.Words for .NET, le filigrane est appliqué de façon programmatique au fur et à mesure que les fichiers sont produits, garantissant que chaque document porte la même marque ou mention de confidentialité sans effort manuel.

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-text-watermark" >}}


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

**Q: Que contrôle l'option **IsSemitrasparent** et quel effet a le fait de la régler sur **true** ?**  
A: IsSemitrasparent détermine si le filigrane est rendu avec une opacité partielle ; le régler sur **true** rend le texte semi‑transparent afin que le contenu sous-jacent reste plus lisible.

**Q: Puis-je changer l'orientation du filigrane en horizontal au lieu de diagonal ?**  
A: Oui — définissez la propriété **Layout** sur **WatermarkLayout.Horizontal** dans **TextWatermarkOptions** avant d’appeler **document.Watermark.SetText**.

**Q: Ce code ajoutera-t-il un filigrane à un fichier Word existant ou uniquement aux documents nouvellement créés ?**  
A: L’extrait crée une nouvelle instance de **Document**, mais vous pouvez ouvrir n’importe quel fichier existant (par ex., `new Document("Existing.docx")`) puis appeler **document.Watermark.SetText** pour appliquer le même filigrane.

**Q: Comment puis‑je utiliser une couleur RVB personnalisée pour le filigrane au lieu du **Color.Red** prédéfini ?**  
A: Attribuez une couleur personnalisée avec **Color.FromArgb(red, green, blue)** à la propriété **Color** de **TextWatermarkOptions**, par ex., `Color = Color.FromArgb(128, 0, 128)` pour du violet.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}