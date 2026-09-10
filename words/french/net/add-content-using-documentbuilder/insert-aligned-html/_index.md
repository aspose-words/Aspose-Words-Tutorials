---
title: Insérer du HTML aligné dans un document Word avec Aspose.Words for .NET
weight: 210
limit:
description: Apprenez à insérer du HTML avec un alignement spécifique dans un document Word en utilisant Aspose.Words for .NET.
keywords: [insert aligned html, Aspose.Words for .NET, documentbuilder html insertion, html alignment in word, c# insert html word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Insérer du HTML aligné dans un document Word avec Aspose.Words
Ce tutoriel montre comment utiliser DocumentBuilder d'Aspose.Words for .NET pour intégrer du balisage HTML dans un document Word et contrôler son alignement. Vous verrez comment insérer le HTML, définir l'alignement du paragraphe (gauche, centre ou droite), puis enregistrer le document résultant. L'exemple est idéal pour les développeurs qui doivent conserver le formatage de type web tout en générant des fichiers Word de manière programmatique.

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

**Q: InsertHtml peut‑il être utilisé pour ajouter du HTML dans un document Word existant plutôt que dans un nouveau ?**
A: Oui. Créez un Document à partir du fichier existant, positionnez le curseur du DocumentBuilder à l’endroit où vous souhaitez insérer le HTML (par ex., en utilisant builder.MoveToDocumentEnd()), puis appelez builder.InsertHtml avec votre balisage.

**Q: Quels attributs HTML sont pris en compte par InsertHtml pour l’alignement ?**
A: InsertHtml respecte l’attribut "align" sur les éléments de niveau bloc tels que <p>, <div> et les balises de titre, en appliquant l’alignement de paragraphe correspondant dans le document Word résultant.

**Q: Que se passe‑t‑il si la chaîne HTML contient des balises ou du CSS non pris en charge ?**
A: Les balises non prises en charge sont ignorées et leur texte interne est inséré en texte brut ; les styles CSS en ligne que Aspose.Words ne reconnaît pas sont également ignorés, de sorte que seul le sous‑ensemble d’HTML supporté est rendu.

**Q: Do I need to close the DocumentBuilder before saving the document?**
A: Non, aucune fermeture explicite n’est requise ; après l’insertion du HTML, vous pouvez appeler directement doc.Save avec le nom de fichier et le format souhaités, et les ressources du builder sont libérées automatiquement.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}