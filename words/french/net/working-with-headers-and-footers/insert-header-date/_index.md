---
title: Insérer une date d’en-tête dynamique dans un document Word à l’aide d’Aspose.Words pour .NET
weight: 110
limit:
description: Apprenez comment ajouter un champ DATE dynamique à l’en-tête principal d’un document Word avec Aspose.Words pour .NET.
keywords: [Aspose.Words for .NET, insert header date, dynamic DATE field, DocumentBuilder header, Word document header automation]
url: /net/working-with-headers-and-footers/insert-header-date/
date: '2026-09-22'
lastmod: '2026-09-22'
schemas:
- author: Aspose
  dateModified: '2026-09-22'
  description: Apprenez comment ajouter un champ DATE dynamique à l’en-tête principal
    d’un document Word avec Aspose.Words pour .NET.
  headline: Insérer une date d’en-tête dynamique dans un document Word à l’aide d’Aspose.Words
    pour .NET
  type: TechArticle
- description: Apprenez comment ajouter un champ DATE dynamique à l’en-tête principal
    d’un document Word avec Aspose.Words pour .NET.
  name: Insérer une date d’en-tête dynamique dans un document Word à l’aide d’Aspose.Words
    pour .NET
  steps:
  - name: Créez un nouveau Document et un DocumentBuilder pour le modifier.
    text: Créez un nouveau Document et un DocumentBuilder pour le modifier.
  - name: Déplacez le curseur du builder vers l’en-tête principal afin que les insertions
      suivantes affectent l’en-tête.
    text: Déplacez le curseur du builder vers l’en-tête principal afin que les insertions
      suivantes affectent l’en-tête.
  - name: Écrivez l’étiquette statique et insérez un champ DATE formaté comme « MMMM
      d, yyyy » dans l’en-tête, créant ainsi une date dynamique.
    text: Écrivez l’étiquette statique et insérez un champ DATE formaté comme « MMMM
      d, yyyy » dans l’en-tête, créant ainsi une date dynamique.
  - name: Revenez au corps principal et ajoutez un paragraphe d’exemple, démontrant
      le contenu normal du document à côté de l’en-tête.
    text: Revenez au corps principal et ajoutez un paragraphe d’exemple, démontrant
      le contenu normal du document à côté de l’en-tête.
  - name: Enregistrez le document dans un fichier .docx.
    text: Enregistrez le document dans un fichier .docx.
  type: HowTo
- questions:
  - answer: L’appel `MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` place le
      builder sur l’en-tête principal existant, et `Write`/`InsertField` se contentent
      d’ajouter du texte à ce qui s’y trouve déjà ; ils ne suppriment pas le contenu
      existant.
    question: Que se passe-t-il si le document possède déjà un en-tête principal –
      mon code l’écrasera-t-il ?
  - answer: Yes – modify the switch format in the field code passed to `InsertField`,
      e.g. `builder.InsertField(\"DATE \\\\@ \"yyyy-MM-dd\"")` will produce a date
      like 2026-09-22.
    question: Puis-je modifier le format de date utilisé par le champ DATE, et comment ?
  - answer: Remplacez `HeaderFooterType.HeaderPrimary` par `HeaderFooterType.HeaderFirst`
      lors de l’appel à `MoveToHeaderFooter` ; le reste du code fonctionne de la même
      manière.
    question: Si je veux le champ de date dans l’en-tête de la première page au lieu
      de l’en-tête principal, que dois‑je faire ?
  - answer: Le champ est inséré uniquement avec le commutateur `\\@`, qui indique
      à Word d’afficher la date actuelle chaque fois que le champ est actualisé (par
      ex., à l’ouverture du fichier ou lorsque vous appuyez sur Ctrl+Alt+F9).
    question: Le champ DATE se met‑il à jour automatiquement lorsque le document est
      ouvert ultérieurement ?
  type: FAQPage
images:
- /net/working-with-headers-and-footers/insert-header-date/og-image.png
og_title: Ajouter une date dynamique à un en-tête Word
og_description: Guide étape par étape pour intégrer un champ de date dynamique dans votre en-tête Word avec Aspose.Words.
og_image_alt: Capture d’écran montrant comment insérer un champ DATE dynamique dans l’en-tête d’un document Word à l’aide d’Aspose.Words pour .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Insérer une date d’en-tête dynamique dans un document Word à l’aide d’Aspose.Words pour .NET
Ce tutoriel montre comment utiliser les classes Document et DocumentBuilder d’Aspose.Words pour .NET afin d’insérer un champ DATE dynamique dans l’en-tête principal d’un document Word. Le champ ajouté se met automatiquement à jour avec la date actuelle chaque fois que le document est ouvert, garantissant que votre en-tête reflète toujours la date la plus récente. Suivez le code pas à pas pour ajouter le champ et enregistrer le fichier mis à jour.

---

{{< tutorial-widget sourcePath="words/net/working-with-headers-and-footers/insert-header-date" >}}


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

**Q: Que se passe-t-il si le document possède déjà un en-tête principal – mon code l’écrasera-t-il ?**  
A: L’appel `MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` place le builder sur l’en-tête principal existant, et `Write`/`InsertField` se contentent d’ajouter du texte à ce qui s’y trouve déjà ; ils ne suppriment pas le contenu existant.

**Q: Puis-je modifier le format de date utilisé par le champ DATE, et comment ?**  
A: Yes – modify the switch format in the field code passed to `InsertField`, e.g. `builder.InsertField(\"DATE \\\\@ \"yyyy-MM-dd\"")` will produce a date like 2026-09-22.

**Q: Si je veux le champ de date dans l’en-tête de la première page au lieu de l’en-tête principal, que dois‑je faire ?**  
A: Remplacez `HeaderFooterType.HeaderPrimary` par `HeaderFooterType.HeaderFirst` lors de l’appel à `MoveToHeaderFooter` ; le reste du code fonctionne de la même manière.

**Q: Le champ DATE se met‑il à jour automatiquement lorsque le document est ouvert ultérieurement ?**  
A: Le champ est inséré uniquement avec le commutateur `\\@`, qui indique à Word d’afficher la date actuelle chaque fois que le champ est actualisé (par ex., à l’ouverture du fichier ou lorsque vous appuyez sur Ctrl+Alt+F9).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}