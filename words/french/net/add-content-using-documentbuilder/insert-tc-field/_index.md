---
title: Insérer un champ TC dans un document Word avec Aspose.Words for .NET
weight: 110
limit:
description: Apprenez à insérer un champ TC avec un texte personnalisé dans un document Word en utilisant Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, insert TC field, TC field Word, DocumentBuilder TC field, Word document index, table of contents field]
url: /net/add-content-using-documentbuilder/insert-tc-field/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Insérer un champ TC dans un document Word avec Aspose.Words
Ce tutoriel montre comment utiliser Aspose.Words for .NET pour insérer un champ TC (Table des matières) dans un document Word nouvellement créé. En utilisant DocumentBuilder, vous pouvez ajouter un champ TC avec un texte d’entrée personnalisé, ce qui est utile pour créer un index consultable pour une table des matières. L’exemple montre également comment enregistrer le document sur le disque.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-tc-field" >}}


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

**Q: Que signifie le commutateur "\f t" dans le code du champ TC ?**
A: Le commutateur "\f t" indique à Word de traiter l’entrée comme une entrée de tableau, ce qui la fait apparaître dans une table des matières générée avec le commutateur \f.

**Q: Comment puis‑je modifier le texte qui apparaît dans le champ TC ?**
A: Remplacez "Entry Text" dans l’appel InsertField par n’importe quelle chaîne que vous souhaitez, par ex., builder.InsertField("TC \"Chapter 1\" \f t");

**Q: Puis‑je insérer plusieurs champs TC dans le même document ?**
A: Oui ; il suffit d’appeler builder.InsertField avec différents textes d’entrée aux emplacements souhaités avant d’enregistrer le document.

**Q: Ce code fonctionne‑t‑il pour des formats autres que .docx, comme le .pdf ?**
A: Dans l’exemple, le document est enregistré au format .docx, mais Aspose.Words peut enregistrer dans d’autres formats (par ex., .pdf) en modifiant l’extension du fichier dans doc.Save et en s’assurant que le format de sortie correspondant est pris en charge.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}