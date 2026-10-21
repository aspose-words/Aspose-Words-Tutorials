---
title: Appliquer un style personnalisé au texte des commentaires dans les documents Word avec Aspose.Words for .NET
weight: 310
limit:
description: Apprenez à ajouter des commentaires et à appliquer un style de paragraphe personnalisé à tout le texte des commentaires dans un document Word avec Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, style comment text, custom comment style, Word document comments, apply paragraph style, document branding]
url: /net/working-with-comments/style-comment-text/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Apprenez à ajouter des commentaires et à appliquer un style de paragraphe
    personnalisé à tout le texte des commentaires dans un document Word avec Aspose.Words
    for .NET.
  headline: Appliquer un style personnalisé au texte des commentaires dans les documents
    Word avec Aspose.Words for .NET
  type: TechArticle
- description: Apprenez à ajouter des commentaires et à appliquer un style de paragraphe
    personnalisé à tout le texte des commentaires dans un document Word avec Aspose.Words
    for .NET.
  name: Appliquer un style personnalisé au texte des commentaires dans les documents
    Word avec Aspose.Words for .NET
  steps:
  - name: Créez un nouveau Document vide et un DocumentBuilder pour le modifier.
    text: Créez un nouveau Document vide et un DocumentBuilder pour le modifier.
  - name: Insérez deux phrases d'exemple dans le document.
    text: Insérez deux phrases d'exemple dans le document.
  - name: Créez un commentaire de Carol, définissez son texte, déplacez‑vous au début
      du document et attachez le commentaire au premier paragraphe.
    text: Créez un commentaire de Carol, définissez son texte, déplacez‑vous au début
      du document et attachez le commentaire au premier paragraphe.
  - name: Créez un commentaire de Dave, définissez son texte, déplacez‑vous à la fin
      du document et attachez le commentaire au dernier paragraphe.
    text: Créez un commentaire de Dave, définissez son texte, déplacez‑vous à la fin
      du document et attachez le commentaire au dernier paragraphe.
  - name: Définissez un style de paragraphe personnalisé nommé "BrandComment" avec
      la police Arial, 10 pt, couleur bleu foncé, en gras, pour correspondre à la
      marque de l'entreprise.
    text: Définissez un style de paragraphe personnalisé nommé "BrandComment" avec
      la police Arial, 10 pt, couleur bleu foncé, en gras, pour correspondre à la
      marque de l'entreprise.
  - name: Collectez tous les nœuds Comment du document dans une liste.
    text: Collectez tous les nœuds Comment du document dans une liste.
  - name: Parcourez chaque commentaire et appliquez le style BrandComment à chaque
      paragraphe à l'intérieur du commentaire.
    text: Parcourez chaque commentaire et appliquez le style BrandComment à chaque
      paragraphe à l'intérieur du commentaire.
  - name: Créez un dossier Results si nécessaire et enregistrez le document modifié
      sous le nom StyledCommentsDocument.docx.
    text: Créez un dossier Results si nécessaire et enregistrez le document modifié
      sous le nom StyledCommentsDocument.docx.
  type: HowTo
- questions:
  - answer: Le code appelle `commentNode.EnsureMinimum()` qui crée un paragraphe par
      défaut si le commentaire est vide, de sorte que l'attribution du style suivante
      dispose toujours d'un paragraphe sur lequel travailler.
    question: Que se passe-t-il si un nœud de commentaire n'a aucun paragraphe lorsque
      j'exécute la boucle d'application du style ?
  - answer: Seuls les paragraphes à l'intérieur de l'objet `Comment` sont stylisés ;
      le texte d'ancre dans le document principal conserve son formatage d'origine
      car le style est appliqué à `para.ParagraphFormat.Style` dans chaque commentaire.
    question: Le style personnalisé "BrandComment" affecte-t-il l'ancre du commentaire
      (le texte surligné dans le document principal) ou uniquement le texte du commentaire ?
  - answer: Oui, récupérez le style existant avec `document.Styles["ExistingStyleName"]`
      et assignez‑le à `para.ParagraphFormat.Style` dans la même boucle, en sautant
      l'étape `document.Styles.Add`.
    question: Puis-je appliquer un style de paragraphe existant au lieu d'en créer
      un nouveau pour les commentaires ?
  - answer: Il renvoie chaque nœud `Comment` dans l'arborescence du document, y compris
      les réponses imbriquées, car l'argument `true` rend la recherche récursive.
    question: '`document.GetChildNodes(NodeType.Comment, true)` renverra‑t‑il également
      les réponses aux commentaires (nœuds de commentaire imbriqués) ?'
  - answer: Non, `document.Styles.Add` crée un style uniquement si aucun style portant
      ce nom n'existe déjà ; les exécutions ultérieures réutiliseront le style "BrandComment"
      existant.
    question: Si j'exécute le code plusieurs fois sur le même document, des styles
      "BrandComment" en double seront‑ils créés ?
  type: FAQPage
images:
- /net/working-with-comments/style-comment-text/og-image.png
og_title: Styliser tout le texte des commentaires dans un document Word
og_description: Découvrez comment ajouter programmatiquement des commentaires et leur appliquer un style personnalisé avec Aspose.Words for .NET.
og_image_alt: Capture d'écran montrant un document Word avec du texte de commentaire stylisé créé à l'aide d'Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Appliquer un style personnalisé au texte des commentaires dans les documents Word avec Aspose.Words
Ce tutoriel montre comment utiliser Aspose.Words for .NET pour ajouter programmatiquement des commentaires à un fichier Word, puis appliquer un style de paragraphe personnalisé à chaque paragraphe de commentaire. En stylisant le texte des commentaires, vous pouvez garantir que toutes les remarques respectent la charte de votre entreprise sans mise en forme manuelle. L'exemple couvre la création de commentaires, la définition d'un style et l'attribution de ce style à chaque bloc de commentaire.

---

{{< tutorial-widget sourcePath="words/net/working-with-comments/style-comment-text" >}}


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

**Q: Que se passe-t-il si un nœud de commentaire n'a aucun paragraphe lorsque j'exécute la boucle d'application du style ?**  
A: Le code appelle `commentNode.EnsureMinimum()` qui crée un paragraphe par défaut si le commentaire est vide, de sorte que l'attribution du style suivante dispose toujours d'un paragraphe sur lequel travailler.

**Q: Le style personnalisé "BrandComment" affecte-t-il l'ancre du commentaire (le texte surligné dans le document principal) ou uniquement le texte du commentaire ?**  
A: Seuls les paragraphes à l'intérieur de l'objet `Comment` sont stylisés ; le texte d'ancre dans le document principal conserve son formatage d'origine car le style est appliqué à `para.ParagraphFormat.Style` dans chaque commentaire.

**Q: Puis-je appliquer un style de paragraphe existant au lieu d'en créer un nouveau pour les commentaires ?**  
A: Oui, récupérez le style existant avec `document.Styles["ExistingStyleName"]` et assignez‑le à `para.ParagraphFormat.Style` dans la même boucle, en sautant l'étape `document.Styles.Add`.

**Q: `document.GetChildNodes(NodeType.Comment, true)` renverra‑t‑il également les réponses aux commentaires (nœuds de commentaire imbriqués) ?**  
A: Il renvoie chaque nœud `Comment` dans l'arborescence du document, y compris les réponses imbriquées, car l'argument `true` rend la recherche récursive.

**Q: Si j'exécute le code plusieurs fois sur le même document, des styles "BrandComment" en double seront‑ils créés ?**  
A: Non, `document.Styles.Add` crée un style uniquement si aucun style portant ce nom n'existe déjà ; les exécutions ultérieures réutiliseront le style "BrandComment" existant.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}