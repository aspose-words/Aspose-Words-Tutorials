---
title: Insérer une forme de règle horizontale dans un document Word avec Aspose.Words for .NET
weight: 110
limit:
description: Apprenez à ajouter une forme de règle horizontale à un document Word avec Aspose.Words for .NET en utilisant DocumentBuilder.
keywords: [Aspose.Words for .NET, insert horizontal rule shape, documentbuilder horizontal line, create Word document .NET, horizontal rule shape tutorial]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Insérer une forme de règle horizontale dans un document Word avec Aspose.Words
Dans ce tutoriel, vous apprendrez comment insérer programmétiquement une forme de règle horizontale dans un document Word avec Aspose.Words for .NET. En utilisant les classes Document et DocumentBuilder, nous créons un nouveau document, ajoutons un paragraphe de texte, puis plaçons une forme de ligne horizontale à l'emplacement souhaité. La règle horizontale fournit un séparateur visuel qui peut être utile pour les sauts de section ou pour mettre en évidence visuellement.

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

**Q: Où exactement `builder.InsertHorizontalRule()` place-t-il la ligne dans le document ?**  
A: `InsertHorizontalRule` insère une forme de règle horizontale à la position actuelle du curseur du `DocumentBuilder` ; si vous souhaitez qu'elle soit sur une ligne séparée, appelez `builder.Writeln()` avant l'insertion.

**Q: Puis-je modifier l'épaisseur, la couleur ou la largeur de la règle horizontale insérée ?**  
A: `InsertHorizontalRule` ajoute une règle au style par défaut et n'expose pas d'options de formatage ; pour personnaliser ces propriétés, vous devez insérer manuellement un `Shape` (par ex., `builder.InsertShape(ShapeType.HorizontalLine)`) puis définir ses propriétés `LineFormat`.

**Q: Est-il possible d'ajouter plusieurs règles horizontales dans le même document ?**  
A: Oui — appelez simplement `builder.InsertHorizontalRule()` chaque fois que vous avez besoin d'une nouvelle règle ; chaque appel crée une forme distincte à la position actuelle du builder.

**Q: La règle horizontale sera-t-elle visible lorsque le .docx enregistré sera ouvert dans Microsoft Word ?**  
A: Absolument ; la règle est enregistrée comme une forme à l'intérieur du fichier .docx, donc Word l'affiche exactement comme elle apparaît dans le document généré.

**Q: Que se passe-t-il si le dossier `dataDir` n'existe pas avant d'appeler `doc.Save(...)` ?**  
A: `doc.Save` lèvera une `DirectoryNotFoundException` ; assurez‑vous que le répertoire cible existe ou créez‑le programmatique­ment avant l'enregistrement.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}