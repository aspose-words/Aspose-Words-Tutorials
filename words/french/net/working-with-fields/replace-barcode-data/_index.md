---
title: Remplacer les données du code‑barres dans les documents Word avec Aspose.Words pour .NET
weight: 110
limit:
description: Apprenez à insérer un champ DISPLAYBARCODE et à remplacer sa chaîne de données avec Aspose.Words pour .NET.
keywords: [Aspose.Words for .NET, barcode field, replace barcode data, Document.Range.Replace, DISPLAYBARCODE, Word barcode update]
url: /net/working-with-fields/replace-barcode-data/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Apprenez à insérer un champ DISPLAYBARCODE et à remplacer sa chaîne
    de données avec Aspose.Words pour .NET.
  headline: Remplacer les données du code‑barres dans les documents Word avec Aspose.Words
    pour .NET
  type: TechArticle
- description: Apprenez à insérer un champ DISPLAYBARCODE et à remplacer sa chaîne
    de données avec Aspose.Words pour .NET.
  name: Remplacer les données du code‑barres dans les documents Word avec Aspose.Words
    pour .NET
  steps:
  - name: Créez un nouvel objet Document et un DocumentBuilder pour construire son
      contenu.
    text: Créez un nouvel objet Document et un DocumentBuilder pour construire son
      contenu.
  - name: Insérez un champ DISPLAYBARCODE et définissez son type, sa valeur initiale
      et les caractères de début/fin, puis ajoutez un saut de ligne.
    text: Insérez un champ DISPLAYBARCODE et définissez son type, sa valeur initiale
      et les caractères de début/fin, puis ajoutez un saut de ligne.
  - name: Appelez UpdateFields pour rendre le champ code‑barres nouvellement inséré.
    text: Appelez UpdateFields pour rendre le champ code‑barres nouvellement inséré.
  - name: Utilisez le moteur de recherche/remplacement pour changer la chaîne de données
      du code‑barres de INIT123 à NEWVAL.
    text: Utilisez le moteur de recherche/remplacement pour changer la chaîne de données
      du code‑barres de INIT123 à NEWVAL.
  - name: Mettez à jour les champs à nouveau afin que le DISPLAYBARCODE reflète la
      nouvelle chaîne de données.
    text: Mettez à jour les champs à nouveau afin que le DISPLAYBARCODE reflète la
      nouvelle chaîne de données.
  - name: Enregistrez le document au format .docx.
    text: Enregistrez le document au format .docx.
  type: HowTo
- questions:
  - answer: '`Range.Replace` ne modifie que le texte sous‑jacent ; le résultat visuel
      du champ DISPLAYBARCODE n’est régénéré que lorsque `UpdateFields()` est appelé,
      de sorte que le nouveau code‑barres apparaît dans le document enregistré.'
    question: Pourquoi dois‑je appeler `myDocument.UpdateFields()` après avoir exécuté
      `Range.Replace` ?
  - answer: Oui, `Document.Range.Replace` agit sur l’ensemble de la plage du document,
      donc tout texte correspondant ailleurs sera remplacé à moins que vous ne limitiez
      la recherche avec `FindReplaceOptions` (par ex., en définissant une `Range`
      spécifique ou en utilisant `.MatchWholeWord`).
    question: L’appel `Replace(\"INIT123\", \"NEWVAL\", ...)` affectera‑t‑il d’autres
      occurrences de \"INIT123\" en dehors du champ code‑barres ?
  - answer: Vous pouvez assigner une nouvelle valeur à `displayBarcode.BarcodeType`
      à tout moment, mais vous devez appeler `myDocument.UpdateFields()` ensuite pour
      que la modification soit reflétée dans le code‑barres rendu.
    question: Puis‑je changer le type de code‑barres (par ex., de CODE39 à QR) après
      l’insertion du champ ?
  - answer: Lorsque `AddStartStopChar` est vrai, Aspose.Words ajoute automatiquement
      les caractères de début/fin requis (`*`) autour de la valeur du code‑barres,
      ce qui est nécessaire pour CODE39 ; réglez‑le sur false si votre symbologie
      n’en a pas besoin.
    question: Que fait la propriété `AddStartStopChar = true` pour les codes‑barres
      CODE39 ?
  - answer: Aucun paramètre spécial n’est requis pour une correspondance exacte simple,
      mais vous pouvez activer `.MatchCase` ou `.MatchWholeWord` dans `FindReplaceOptions`
      afin d’éviter des remplacements partiels accidentels.
    question: Dois‑je configurer des options spéciales dans `FindReplaceOptions` pour
      remplacer la valeur du code‑barres en toute sécurité ?
  type: FAQPage
images:
- /net/working-with-fields/replace-barcode-data/og-image.png
og_title: Mettre à jour un champ de code‑barres dans Word avec Aspose.Words
og_description: Échangez la chaîne de données d’un code‑barres et actualisez‑la instantanément dans un fichier Word.
og_image_alt: Capture d’écran montrant un document Word avec un champ DISPLAYBARCODE avant et après le remplacement des données à l’aide d’Aspose.Words pour .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Remplacer les données du code‑barres dans les documents Word avec Aspose.Words pour .NET
Ce tutoriel démontre comment insérer un champ DISPLAYBARCODE dans un document Word puis utiliser la méthode Document.Range.Replace pour modifier la chaîne de données du code‑barres. Après le remplacement, le champ est actualisé afin que le code‑barres mis à jour apparaisse dans le fichier enregistré. Suivez les étapes pour voir la mise à jour du code‑barres instantanément sans recréer le champ.

---

{{< tutorial-widget sourcePath="words/net/working-with-fields/replace-barcode-data" >}}


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

**Q: Pourquoi dois‑je appeler `myDocument.UpdateFields()` après avoir exécuté `Range.Replace` ?**  
A: `Range.Replace` ne modifie que le texte sous‑jacent ; le résultat visuel du champ DISPLAYBARCODE n’est régénéré que lorsque `UpdateFields()` est appelé, de sorte que le nouveau code‑barres apparaît dans le document enregistré.

**Q: L’appel `Replace(\"INIT123\", \"NEWVAL\", ...)` affectera‑t‑il d’autres occurrences de \"INIT123\" en dehors du champ code‑barres ?**  
A: Oui, `Document.Range.Replace` agit sur l’ensemble de la plage du document, donc tout texte correspondant ailleurs sera remplacé à moins que vous ne limitiez la recherche avec `FindReplaceOptions` (par ex., en définissant une `Range` spécifique ou en utilisant `.MatchWholeWord`).

**Q: Puis‑je changer le type de code‑barres (par ex., de CODE39 à QR) après l’insertion du champ ?**  
A: Vous pouvez assigner une nouvelle valeur à `displayBarcode.BarcodeType` à tout moment, mais vous devez appeler `myDocument.UpdateFields()` ensuite pour que la modification soit reflétée dans le code‑barres rendu.

**Q: Que fait la propriété `AddStartStopChar = true` pour les codes‑barres CODE39 ?**  
A: Lorsque `AddStartStopChar` est vrai, Aspose.Words ajoute automatiquement les caractères de début/fin requis (`*`) autour de la valeur du code‑barres, ce qui est nécessaire pour CODE39 ; réglez‑le sur false si votre symbologie n’en a pas besoin.

**Q: Dois‑je configurer des options spéciales dans `FindReplaceOptions` pour remplacer la valeur du code‑barres en toute sécurité ?**  
A: Aucun paramètre spécial n’est requis pour une correspondance exacte simple, mais vous pouvez activer `.MatchCase` ou `.MatchWholeWord` dans `FindReplaceOptions` afin d’éviter des remplacements partiels accidentels.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}