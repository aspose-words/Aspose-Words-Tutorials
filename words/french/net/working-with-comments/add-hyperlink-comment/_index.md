---
title: Ajouter un commentaire hyperlien et exporter en tant qu’annotation PDF avec Aspose.Words for .NET
weight: 110
limit:
description: Apprenez à ajouter un commentaire hyperlien dans un fichier Word et à l’exporter en tant qu’annotation PDF avec Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, add hyperlink comment, PDF annotation, export Word to PDF, comment with hyperlink, verify PDF output]
url: /net/working-with-comments/add-hyperlink-comment/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Apprenez à ajouter un commentaire hyperlien dans un fichier Word et
    à l’exporter en tant qu’annotation PDF avec Aspose.Words for .NET.
  headline: Ajouter un commentaire hyperlien et exporter en tant qu’annotation PDF
    avec Aspose.Words for .NET
  type: TechArticle
- description: Apprenez à ajouter un commentaire hyperlien dans un fichier Word et
    à l’exporter en tant qu’annotation PDF avec Aspose.Words for .NET.
  name: Ajouter un commentaire hyperlien et exporter en tant qu’annotation PDF avec
    Aspose.Words for .NET
  steps:
  - name: Créez un nouvel objet Document vide et un DocumentBuilder pour travailler
      avec celui‑ci.
    text: Créez un nouvel objet Document vide et un DocumentBuilder pour travailler
      avec celui‑ci.
  - name: Écrivez une ligne de texte visible qui accueillera le commentaire à venir.
    text: Écrivez une ligne de texte visible qui accueillera le commentaire à venir.
  - name: Créez un Comment rédigé par Jane Doe et attachez‑le au premier paragraphe
      du document.
    text: Créez un Comment rédigé par Jane Doe et attachez‑le au premier paragraphe
      du document.
  - name: À l’intérieur du commentaire, ajoutez un paragraphe et insérez un hyperlien
      bleu souligné vers le site Web de la bibliothèque Aspose.Words.
    text: À l’intérieur du commentaire, ajoutez un paragraphe et insérez un hyperlien
      bleu souligné vers le site Web de la bibliothèque Aspose.Words.
  - name: Configurez le document pour rendre les commentaires sous forme d’annotations
      PDF et rafraîchissez la mise en page.
    text: Configurez le document pour rendre les commentaires sous forme d’annotations
      PDF et rafraîchissez la mise en page.
  - name: Créez un dossier "Output" dans le répertoire actuel pour stocker le PDF
      généré.
    text: Créez un dossier "Output" dans le répertoire actuel pour stocker le PDF
      généré.
  - name: Enregistrez le document préparé en tant que fichier PDF en utilisant PdfSaveOptions.
    text: Enregistrez le document préparé en tant que fichier PDF en utilisant PdfSaveOptions.
  - name: Vérifiez que le fichier PDF existe et contient des données, puis affichez
      le résultat dans la console.
    text: Vérifiez que le fichier PDF existe et contient des données, puis affichez
      le résultat dans la console.
  type: HowTo
- questions:
  - answer: Le troisième paramètre de `InsertHyperlink` indique si le lien doit être
      traité comme un champ ; le définir à `false` insère un hyperlien simple qui
      fonctionne dans l’annotation PDF sans nécessiter de code de champ.
    question: Que contrôle le troisième argument (`false`) dans `InsertHyperlink` ?
  - answer: Définissez `myDocument.LayoutOptions.CommentDisplayMode` sur `CommentDisplayMode.ShowInBalloons`
      avant d’appeler `Save` ; le PDF contiendra alors le commentaire comme un commentaire
      Word standard plutôt que comme une annotation.
    question: Comment faire apparaître le commentaire sous forme de bulle dans le
      document Word au lieu d’une annotation PDF ?
  - answer: Oui — chaque `Comment` que vous ajoutez à un paragraphe peut contenir
      son propre appel `InsertHyperlink`, et tous les hyperliens seront conservés
      comme des annotations PDF distinctes lorsque le document sera enregistré.
    question: Si j’ajoute plusieurs commentaires, chaque hyperlien fonctionnera‑t‑il
      dans le PDF exporté ?
  - answer: Ouvrez le PDF généré, localisez l’annotation de commentaire (généralement
      affichée sous forme d’icône de note), cliquez dessus pour révéler le texte du
      commentaire, puis cliquez sur le lien bleu souligné ; il devrait ouvrir l’URL
      cible dans un navigateur Web.
    question: Comment vérifier que l’hyperlien à l’intérieur du commentaire fonctionne
      réellement après la génération du PDF ?
  type: FAQPage
images:
- /net/working-with-comments/add-hyperlink-comment/og-image.png
og_title: Insérer un commentaire hyperlien & exporter en PDF
og_description: Apprenez à intégrer un lien cliquable dans un commentaire Word et à le transformer en annotation PDF.
og_image_alt: Guide montrant comment ajouter un commentaire avec un hyperlien cliquable à un document Word et l’exporter en tant qu’annotation PDF en utilisant Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ajouter un commentaire hyperlien et exporter en tant qu’annotation PDF avec Aspose.Words
Dans ce tutoriel, vous verrez comment créer un document Word, insérer un commentaire contenant un hyperlien cliquable vers un site Web externe, configurer ce commentaire pour qu’il apparaisse comme une annotation PDF, exporter le document au format PDF et vérifier le fichier PDF résultant. Le code étape par étape vous permet d’ajouter des commentaires riches et activés par des liens et de les conserver lors de la conversion en PDF, ce qui facilite le partage de notes interactives avec les lecteurs.

---

{{< tutorial-widget sourcePath="words/net/working-with-comments/add-hyperlink-comment" >}}


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

**Q: Que contrôle le troisième argument (`false`) dans `InsertHyperlink` ?**  
A: Le troisième paramètre de `InsertHyperlink` indique si le lien doit être traité comme un champ ; le définir à `false` insère un hyperlien simple qui fonctionne dans l’annotation PDF sans nécessiter de code de champ.

**Q: Comment faire apparaître le commentaire sous forme de bulle dans le document Word au lieu d’une annotation PDF ?**  
A: Définissez `myDocument.LayoutOptions.CommentDisplayMode` sur `CommentDisplayMode.ShowInBalloons` avant d’appeler `Save` ; le PDF contiendra alors le commentaire comme un commentaire Word standard plutôt que comme une annotation.

**Q: Si j’ajoute plusieurs commentaires, chaque hyperlien fonctionnera‑t‑il dans le PDF exporté ?**  
A: Oui — chaque `Comment` que vous ajoutez à un paragraphe peut contenir son propre appel `InsertHyperlink`, et tous les hyperliens seront conservés comme des annotations PDF distinctes lorsque le document sera enregistré.

**Q: Comment vérifier que l’hyperlien à l’intérieur du commentaire fonctionne réellement après la génération du PDF ?**  
A: Ouvrez le PDF généré, localisez l’annotation de commentaire (généralement affichée sous forme d’icône de note), cliquez dessus pour révéler le texte du commentaire, puis cliquez sur le lien bleu souligné ; il devrait ouvrir l’URL cible dans un navigateur Web.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}