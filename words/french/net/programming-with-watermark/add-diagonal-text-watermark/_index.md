---
title: Créer un filigrane texte diagonal avec police personnalisée dans un document Word à l'aide d'Aspose.Words pour .NET
weight: 210
limit:
description: Code étape par étape pour ajouter un filigrane texte diagonal avec police personnalisée à un .docx Word en utilisant Aspose.Words pour .NET.
keywords: [Aspose.Words for .NET, diagonal text watermark, custom font watermark, Word document watermark, Document.Watermark.SetText, C# watermark API]
url: /net/programming-with-watermark/add-diagonal-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Code étape par étape pour ajouter un filigrane texte diagonal avec
    police personnalisée à un .docx Word en utilisant Aspose.Words pour .NET.
  headline: Créer un filigrane texte diagonal avec police personnalisée dans un document
    Word à l'aide d'Aspose.Words pour .NET
  type: TechArticle
- description: Code étape par étape pour ajouter un filigrane texte diagonal avec
    police personnalisée à un .docx Word en utilisant Aspose.Words pour .NET.
  name: Créer un filigrane texte diagonal avec police personnalisée dans un document
    Word à l'aide d'Aspose.Words pour .NET
  steps:
  - name: Créez une nouvelle instance vide de document Word nommée `document`.
    text: Créez une nouvelle instance vide de document Word nommée `document`.
  - name: Configurez `watermarkSettings` avec la police Arial 48 pt gris, une disposition
      diagonale et un rendu opaque.
    text: Configurez `watermarkSettings` avec la police Arial 48 pt gris, une disposition
      diagonale et un rendu opaque.
  - name: Appliquez le filigrane texte « Private » à `document` en utilisant les paramètres
      définis précédemment.
    text: Appliquez le filigrane texte « Private » à `document` en utilisant les paramètres
      définis précédemment.
  - name: Définissez le chemin du fichier où le document filigrané sera enregistré.
    text: Définissez le chemin du fichier où le document filigrané sera enregistré.
  - name: Enregistrez le `document` modifié à l'emplacement spécifié sous forme de
      fichier .docx.
    text: Enregistrez le `document` modifié à l'emplacement spécifié sous forme de
      fichier .docx.
  type: HowTo
- questions:
  - answer: '`IsSemitrasparent` détermine si le filigrane est rendu avec une opacité
      partielle ; le régler sur `false` rend le filigrane totalement opaque, tandis
      que `true` applique un effet semi‑transparent par défaut.'
    question: Que contrôle le drapeau **IsSemitrasparent** dans `TextWatermarkOptions` ?
  - answer: Oui — définissez la propriété `Layout` sur `WatermarkLayout.Horizontal`
      (ou une autre valeur d’énumération) avant d’appeler `document.Watermark.SetText`.
    question: Puis-je changer l’orientation du filigrane en horizontal au lieu de
      diagonal ?
  - answer: Word reviendra à sa police par défaut pour le filigrane, de sorte que
      le texte apparaît toujours mais peut différer du style prévu.
    question: Que se passe-t-il si la `FontFamily` spécifiée (par ex., « Arial »)
      n’est pas installée sur la machine cible ?
  - answer: Chargez le fichier existant avec `Document document = new Document(\"Existing.docx\");`,
      puis configurez `TextWatermarkOptions` et appelez `document.Watermark.SetText`
      comme indiqué.
    question: Est‑il possible d’ajouter un filigrane à un fichier `.docx` existant
      au lieu d’en créer un nouveau ?
  type: FAQPage
images:
- /net/programming-with-watermark/add-diagonal-text-watermark/og-image.png
og_title: Ajouter un filigrane texte diagonal avec police personnalisée
og_description: Apprenez à intégrer un filigrane texte incliné avec votre propre police dans un fichier Word en quelques minutes.
og_image_alt: Guide montrant comment ajouter un filigrane texte diagonal avec police personnalisée à un document Word en utilisant Aspose.Words pour .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Créer un filigrane texte diagonal avec police personnalisée dans un document Word à l'aide d'Aspose.Words pour .NET
Ce tutoriel vous guide dans la création d’un nouveau document Word, la configuration d’un filigrane texte diagonal avec les paramètres de police de votre choix, son application via l’API Document.Watermark.SetText et l’enregistrement du résultat sous forme de fichier .docx. À la fin, vous disposerez d’un document filigrané professionnel qui met en avant votre image de marque ou votre propriété. Le code étape par étape est prêt à être copié dans n’importe quel projet .NET.

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-diagonal-text-watermark" >}}


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

**Q: Que contrôle le drapeau **IsSemitrasparent** dans `TextWatermarkOptions` ?**  
A: `IsSemitrasparent` détermine si le filigrane est rendu avec une opacité partielle ; le régler sur `false` rend le filigrane totalement opaque, tandis que `true` applique un effet semi‑transparent par défaut.

**Q: Puis-je changer l’orientation du filigrane en horizontal au lieu de diagonal ?**  
A: Oui — définissez la propriété `Layout` sur `WatermarkLayout.Horizontal` (ou une autre valeur d’énumération) avant d’appeler `document.Watermark.SetText`.

**Q: Que se passe-t-il si la `FontFamily` spécifiée (par ex., « Arial ») n’est pas installée sur la machine cible ?**  
A: Word reviendra à sa police par défaut pour le filigrane, de sorte que le texte apparaît toujours mais peut différer du style prévu.

**Q: Est‑il possible d’ajouter un filigrane à un fichier `.docx` existant au lieu d’en créer un nouveau ?**  
A: Chargez le fichier existant avec `Document document = new Document(\"Existing.docx\");`, puis configurez `TextWatermarkOptions` et appelez `document.Watermark.SetText` comme indiqué.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}