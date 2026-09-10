---
title: Insérer du HTML aligné dans un document Word à l'aide d'Aspose.Words pour .NET
weight: 210
limit:
description: Apprenez à insérer du HTML brut avec un alignement gauche, centre ou droite dans un document Word en utilisant Aspose.Words pour .NET.
keywords: [Aspose.Words for .NET, insert html word document, html alignment, documentbuilder html, c# insert html, aligned html in word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Insérer du HTML aligné dans un document Word à l'aide d'Aspose.Words pour .NET
Ce tutoriel interactif montre comment intégrer du HTML brut dans un document Word tout en contrôlant son alignement — gauche, centre ou droite — à l'aide d'Aspose.Words pour .NET. En exploitant Document et DocumentBuilder, vous pouvez insérer une chaîne HTML et appliquer l'alignement de paragraphe souhaité en quelques lignes de code seulement. L'exemple est idéal lorsque vous devez préserver le formatage HTML et placer le contenu précisément dans votre document.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-aligned-html" >}}


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

**Q: Que se passe-t-il si la chaîne HTML passée à DocumentBuilder.InsertHtml contient des balises que Aspose.Words ne prend pas en charge, comme <script> ou <iframe> ?**
A: Les balises non prises en charge sont ignorées ; Aspose.Words analyse uniquement le sous‑ensemble de HTML qu'il peut rendre, de sorte que <script>, <iframe> et les éléments similaires sont supprimés tandis que le reste du contenu est inséré.

**Q: Les styles CSS en ligne (par ex., <span style=\"color:red;\">) seront-ils conservés lors de l'utilisation de InsertHtml ?**
A: Oui, InsertHtml respecte de nombreuses propriétés CSS en ligne comme la couleur, la taille de police et l'arrière‑plan, en les convertissant en formatage Word correspondant.

**Q: InsertHtml crée‑t‑il automatiquement un nouveau paragraphe pour les éléments de niveau bloc comme <div> ou <h1> ?**
A: Les éléments de niveau bloc sont mappés aux paragraphes Word, ainsi chaque <div>, <p>, <h1>, etc., devient un paragraphe distinct dans le document.

**Q: Comment insérer du HTML à un emplacement précis dans un document existant au lieu du début ?**
A: Déplacez le curseur du DocumentBuilder vers le nœud souhaité (par ex., builder.MoveToDocumentEnd() ou builder.MoveToParagraph(index)) avant d’appeler InsertHtml ; le HTML sera inséré à la position actuelle du curseur.

**Q: Si le document contient déjà du texte, l’appel à InsertHtml écrasera‑t‑il le contenu existant ?**
A: Non, InsertHtml insère le HTML analysé à la position actuelle du builder sans supprimer les nœuds existants, sauf si vous déplacez explicitement le curseur dans ces nœuds ou les supprimez au préalable.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}