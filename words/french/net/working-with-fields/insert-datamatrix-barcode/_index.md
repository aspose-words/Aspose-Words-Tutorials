---
title: Insérer un code-barres DataMatrix dans un document Word à l'aide d'Aspose.Words for .NET
weight: 210
limit:
description: Ajoutez un code-barres DataMatrix à un document Word de façon programmatique avec Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, datamatrix barcode, displaybarcode field, documentbuilder barcode, word document barcode, insert barcode .net]
url: /net/working-with-fields/insert-datamatrix-barcode/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Ajoutez un code-barres DataMatrix à un document Word de façon programmatique
    avec Aspose.Words for .NET.
  headline: Insérer un code-barres DataMatrix dans un document Word à l'aide d'Aspose.Words
    for .NET
  type: TechArticle
- description: Ajoutez un code-barres DataMatrix à un document Word de façon programmatique
    avec Aspose.Words for .NET.
  name: Insérer un code-barres DataMatrix dans un document Word à l'aide d'Aspose.Words
    for .NET
  steps:
  - name: Créez un nouveau document Word vide et un DocumentBuilder pour le modifier.
    text: Créez un nouveau document Word vide et un DocumentBuilder pour le modifier.
  - name: Insérez un champ DISPLAYBARCODE à la position actuelle du curseur, ce qui
      ajoute un espace réservé de champ au document.
    text: Insérez un champ DISPLAYBARCODE à la position actuelle du curseur, ce qui
      ajoute un espace réservé de champ au document.
  - name: Définissez le BarcodeType du champ sur DataMatrix et fournissez la chaîne
      de données à encoder.
    text: Définissez le BarcodeType du champ sur DataMatrix et fournissez la chaîne
      de données à encoder.
  - name: Définissez éventuellement les couleurs d'arrière-plan et de premier plan
      du code-barres.
    text: Définissez éventuellement les couleurs d'arrière-plan et de premier plan
      du code-barres.
  - name: Appelez UpdateFields sur le document pour rendre l'image du code-barres
      à l'intérieur du champ.
    text: Appelez UpdateFields sur le document pour rendre l'image du code-barres
      à l'intérieur du champ.
  - name: Enregistrez le document dans un fichier .docx.
    text: Enregistrez le document dans un fichier .docx.
  type: HowTo
- questions:
  - answer: Le champ sera inséré, mais `document.UpdateFields()` laissera le code-barres
      vide et Aspose.Words lèvera une `FieldException` indiquant un type de code-barres
      invalide.
    question: Que se passe-t-il si j'attribue une valeur non prise en charge à `displayBarcodeField.BarcodeType` ?
  - answer: '`UpdateFields()` rend les images du code-barres, vous pouvez donc insérer
      plusieurs objets `FieldDisplayBarcode` et appeler `document.UpdateFields()`
      une seule fois à la fin pour les rendre tous.'
    question: Dois-je appeler `document.UpdateFields()` après chaque insertion de
      code-barres, ou puis-je l'appeler une seule fois après avoir ajouté tous les
      champs ?
  - answer: Les deux propriétés attendent une chaîne hexadécimale RGB préfixée par
      `0x` (par ex., `0xFF0000` pour le rouge) ; tout autre format sera ignoré et
      les couleurs par défaut seront utilisées.
    question: Quel format les chaînes de couleur doivent-elles avoir pour `BackgroundColor`
      et `ForegroundColor` ?
  - answer: Oui — il suffit de définir `displayBarcodeField.BarcodeValue` sur une
      nouvelle chaîne et d'appeler à nouveau `document.UpdateFields()` pour actualiser
      l'image rendue.
    question: Puis-je modifier la charge utile du code-barres après l'insertion du
      champ ?
  type: FAQPage
images:
- /net/working-with-fields/insert-datamatrix-barcode/og-image.png
og_title: Insérer un code-barres DataMatrix avec Aspose.Words
og_description: Apprenez comment ajouter un code-barres DataMatrix à un fichier Word en quelques lignes de code .NET.
og_image_alt: Guide montrant comment insérer et rendre un code-barres DataMatrix dans un document Word en utilisant Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Insérer un code-barres DataMatrix dans un document Word à l'aide d'Aspose.Words
Avec Aspose.Words for .NET, vous pouvez ajouter programmétiquement un code-barres DataMatrix à un document Word. Ce tutoriel montre comment créer un nouveau document, insérer un champ DISPLAYBARCODE, définir son type sur DataMatrix et rendre l'image du code-barres en utilisant les classes Document et DocumentBuilder. Suivez les étapes pour générer un code-barres imprimable directement dans votre fichier .docx.

---

{{< tutorial-widget sourcePath="words/net/working-with-fields/insert-datamatrix-barcode" >}}


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

**Q: Que se passe-t-il si j'attribue une valeur non prise en charge à `displayBarcodeField.BarcodeType` ?**  
A: Le champ sera inséré, mais `document.UpdateFields()` laissera le code-barres vide et Aspose.Words lèvera une `FieldException` indiquant un type de code-barres invalide.

**Q: Dois-je appeler `document.UpdateFields()` après chaque insertion de code-barres, ou puis-je l'appeler une seule fois après avoir ajouté tous les champs ?**  
A: `UpdateFields()` rend les images du code-barres, vous pouvez donc insérer plusieurs objets `FieldDisplayBarcode` et appeler `document.UpdateFields()` une seule fois à la fin pour les rendre tous.

**Q: Quel format les chaînes de couleur doivent-elles avoir pour `BackgroundColor` et `ForegroundColor` ?**  
A: Les deux propriétés attendent une chaîne hexadécimale RGB préfixée par `0x` (par ex., `0xFF0000` pour le rouge) ; tout autre format sera ignoré et les couleurs par défaut seront utilisées.

**Q: Puis-je modifier la charge utile du code-barres après l'insertion du champ ?**  
A: Oui — il suffit de définir `displayBarcodeField.BarcodeValue` sur une nouvelle chaîne et d'appeler à nouveau `document.UpdateFields()` pour actualiser l'image rendue.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}