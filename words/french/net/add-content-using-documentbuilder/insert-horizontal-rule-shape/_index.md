---
title: Insérer une forme de règle horizontale dans un document Word à l'aide d'Aspose.Words pour .NET
weight: 110
limit:
description: Guide étape par étape pour insérer une forme de règle horizontale dans un document Word avec Aspose.Words pour .NET.
keywords: [Aspose.Words for .NET, insert horizontal rule shape, horizontal rule shape .NET, DocumentBuilder horizontal rule, add horizontal line Word, create Word document Aspose]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Insérer une forme de règle horizontale dans un document Word à l'aide d'Aspose.Words pour .NET
Apprenez à utiliser Aspose.Words pour .NET afin d'insérer une forme de règle horizontale dans un document Word. Ce tutoriel vous guide à travers la création d'un nouveau document, l'ajout d'une ligne de texte, le placement d'une forme de règle horizontale avec DocumentBuilder, et l'enregistrement du fichier. La règle horizontale fournit un séparateur visuel simple pour votre contenu.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-horizontal-rule-shape" >}}


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

**Q: Puis-je modifier l'apparence (couleur, épaisseur) de la règle horizontale insérée avec DocumentBuilder.InsertHorizontalRule() ?**
A: InsertHorizontalRule crée une forme de ligne horizontale intégrée avec un formatage par défaut ; pour modifier son apparence, vous devez récupérer l'objet Shape inséré (builder.CurrentParagraph.LastChild) et ajuster ses propriétés LineFormat.

**Q: Que se passe-t-il si j'appelle InsertHorizontalRule() après un paragraphe qui se termine déjà par un saut de ligne ?**
A: La méthode insère la règle comme un paragraphe séparé, de sorte que tout saut de ligne précédent crée simplement un paragraphe vide avant la règle ; la règle apparaîtra toujours sur sa propre ligne.

**Q: Est-il possible d'insérer plusieurs règles horizontales dans le même document en utilisant DocumentBuilder ?**
A: Oui, chaque appel à builder.InsertHorizontalRule() ajoute une nouvelle forme de règle horizontale à la position actuelle du curseur, permettant plusieurs règles dans tout le document.

**Q: InsertHorizontalRule() fonctionne-t-il lors de l'enregistrement du document dans des formats autres que DOCX, comme le PDF ?**
A: La règle horizontale est stockée comme une forme dans le modèle du document, de sorte que lors de l'enregistrement en PDF, XPS ou autres formats pris en charge, la règle est rendue correctement dans le résultat.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}