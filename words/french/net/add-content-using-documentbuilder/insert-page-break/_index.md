---
title: Insérer un saut de page dans un document Word avec Aspose.Words for .NET
weight: 110
limit:
description: Apprenez à ajouter des sauts de page à un fichier Word avec Aspose.Words for .NET en utilisant Document et DocumentBuilder.
keywords: [Aspose.Words for .NET, insert page break, documentbuilder page break, c# add page break, word document pagination]
url: /net/add-content-using-documentbuilder/insert-page-break/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Insérer un saut de page dans un document Word avec Aspose.Words
Dans ce tutoriel interactif, vous apprendrez comment ajouter programmétiquement des sauts de page à un document Word en utilisant Aspose.Words for .NET. En créant un objet Document et en utilisant DocumentBuilder, vous pouvez contrôler où les nouvelles pages commencent, ce qui est essentiel pour le formatage des rapports, factures ou tout document à sections multiples. Suivez l'exemple étape par étape pour voir le code en action et prévisualiser le fichier résultant.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-page-break" >}}


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

**Q: Puis-je utiliser InsertBreak pour ajouter un saut de ligne ou un saut de section au lieu d'un saut de page ?**
A: Oui, InsertBreak accepte n'importe quelle valeur de l'énumération BreakType, comme BreakType.LineBreak ou BreakType.SectionBreakContinuous, pour insérer le saut correspondant.

**Q: Do I need to call InsertBreak before or after writing the text for the new page?**
A: InsertBreak doit être appelé après le contenu que vous souhaitez placer sur la page actuelle ; le prochain Writeln commencera alors sur la nouvelle page créée par le saut.

**Q: Que se passe-t-il si le chemin dataDir ne se termine pas par un séparateur de répertoire ?**
A: Si dataDir n'a pas de slash final, le nom du fichier sera concaténé directement (par ex., "C:\DocsAddContentUsingDocumentBuilder.InsertBreak.docx"), ce qui peut entraîner un chemin invalide ; assurez‑vous que le chemin se termine par "\\" ou utilisez Path.Combine.

**Q: Puis-je réutiliser la même instance de DocumentBuilder pour insérer plusieurs sauts dans le document ?**
A: Oui, la même instance de DocumentBuilder peut être utilisée de façon répétée ; chaque appel à InsertBreak insère un saut à la position actuelle du curseur du builder.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}