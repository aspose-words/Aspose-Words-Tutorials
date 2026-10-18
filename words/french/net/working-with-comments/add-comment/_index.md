---
title: Insérez un Comment sur un paragraphe spécifique dans un document Word en utilisant Aspose.Words for .NET
weight: 210
limit:
description: Guide étape par étape pour ajouter un commentaire d'auteur à un paragraphe choisi dans un document Word et l'enregistrer au format DOCX en utilisant Aspose.Words for .NET.
keywords: [add comment Aspose.Words for .NET, insert comment Word document, comment author Aspose.Words, c# add comment to Word, save DOCX with comment]
url: /net/working-with-comments/add-comment/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Guide étape par étape pour ajouter un commentaire d'auteur à un paragraphe
    choisi dans un document Word et l'enregistrer au format DOCX en utilisant Aspose.Words
    for .NET.
  headline: Insérez un Comment sur un paragraphe spécifique dans un document Word
    en utilisant Aspose.Words for .NET
  type: TechArticle
- description: Guide étape par étape pour ajouter un commentaire d'auteur à un paragraphe
    choisi dans un document Word et l'enregistrer au format DOCX en utilisant Aspose.Words
    for .NET.
  name: Insérez un Comment sur un paragraphe spécifique dans un document Word en utilisant
    Aspose.Words for .NET
  steps:
  - name: Instanciez un nouveau Document et un DocumentBuilder pour commencer à construire
      le fichier Word.
    text: Instanciez un nouveau Document et un DocumentBuilder pour commencer à construire
      le fichier Word.
  - name: Utilisez DocumentBuilder.Writeln pour ajouter trois paragraphes distincts
      de texte au document.
    text: Utilisez DocumentBuilder.Writeln pour ajouter trois paragraphes distincts
      de texte au document.
  - name: Récupérez le deuxième paragraphe en toute sécurité, en revenant au premier
      si le document contient moins de deux paragraphes.
    text: Récupérez le deuxième paragraphe en toute sécurité, en revenant au premier
      si le document contient moins de deux paragraphes.
  - name: Créez un Comment avec les détails de l'auteur, définissez son texte, et
      attachez-le au paragraphe sélectionné.
    text: Créez un Comment avec les détails de l'auteur, définissez son texte, et
      attachez-le au paragraphe sélectionné.
  - name: Enregistrez le document modifié sous forme de fichier DOCX nommé 'sample.docx'
      dans le dossier actuel.
    text: Enregistrez le document modifié sous forme de fichier DOCX nommé 'sample.docx'
      dans le dossier actuel.
  type: HowTo
- questions:
  - answer: Le bloc `if` revient au premier paragraphe (`paraList[0]`) lorsque `paraList.Count`
      est inférieur à 2, de sorte que le commentaire sera attaché à ce seul paragraphe
      au lieu du deuxième manquant.
    question: Que fait le code si le document ne contient qu'un seul paragraphe ?
  - answer: Ils sont passés au constructeur `Comment` en tant que deuxième et troisième
      arguments – `new Comment(wordDoc, \"Jordan\", \"JH\", DateTime.Now)` – où "Jordan"
      est le nom de l'auteur et "JH" sont les initiales.
    question: Comment le nom de l'auteur du commentaire et les initiales sont-ils
      définis dans cet exemple ?
  - answer: Dans cet extrait, le commentaire est lié à l'ensemble du `Paragraph` via
      `AppendChild`, mais pour commenter une plage de texte, vous devez créer un `CommentRangeStart`
      et un `CommentRangeEnd` autour des nœuds `Run` souhaités, puis ajouter le nœud
      `Comment` entre eux.
    question: Puis-je attacher un commentaire à un morceau de texte spécifique plutôt
      qu'à tout le paragraphe ?
  - answer: '`AppendChild` ajoute le nœud `Comment` à la collection des enfants du
      paragraphe, et Aspose.Words génère automatiquement les marqueurs de début/fin
      de commentaire requis lors de l''enregistrement du document.'
    question: Dois-je insérer manuellement les marqueurs de commentaire, ou `AppendChild`
      s'en charge-t-il ?
  type: FAQPage
images:
- /net/working-with-comments/add-comment/og-image.png
og_title: Insérer un commentaire dans un paragraphe Word
og_description: Ajoutez un commentaire d'auteur à un paragraphe spécifique et exportez le fichier au format DOCX avec Aspose.Words.
og_image_alt: Guide montrant comment ajouter un commentaire à un paragraphe dans un document Word en utilisant Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Insérez un Comment sur un paragraphe spécifique dans un document Word en utilisant Aspose.Words
Avec Aspose.Words for .NET, vous pouvez ajouter des commentaires aux fichiers Word de manière programmatique. Ce tutoriel décrit la création d'un nouveau document, l'insertion de trois paragraphes, la localisation du deuxième paragraphe, et l'attachement d'un commentaire incluant les informations d'auteur et de date. Enfin, le document est enregistré sous forme de fichier DOCX en conservant le commentaire.

---

{{< tutorial-widget sourcePath="words/net/working-with-comments/add-comment" >}}


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

**Q: Que fait le code si le document ne contient qu'un seul paragraphe ?**  
A: Le bloc `if` revient au premier paragraphe (`paraList[0]`) lorsque `paraList.Count` est inférieur à 2, de sorte que le commentaire sera attaché à ce seul paragraphe au lieu du deuxième manquant.

**Q: Comment le nom de l'auteur du commentaire et les initiales sont-ils définis dans cet exemple ?**  
A: Ils sont passés au constructeur `Comment` en tant que deuxième et troisième arguments – `new Comment(wordDoc, \"Jordan\", \"JH\", DateTime.Now)` – où "Jordan" est le nom de l'auteur et "JH" sont les initiales.

**Q: Puis-je attacher un commentaire à un morceau de texte spécifique plutôt qu'à tout le paragraphe ?**  
A: Dans cet extrait, le commentaire est lié à l'ensemble du `Paragraph` via `AppendChild`, mais pour commenter une plage de texte, vous devez créer un `CommentRangeStart` et un `CommentRangeEnd` autour des nœuds `Run` souhaités, puis ajouter le nœud `Comment` entre eux.

**Q: Dois-je insérer manuellement les marqueurs de commentaire, ou `AppendChild` s'en charge-t-il ?**  
A: `AppendChild` ajoute le nœud `Comment` à la collection des enfants du paragraphe, et Aspose.Words génère automatiquement les marqueurs de début/fin de commentaire requis lors de l'enregistrement du document.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}