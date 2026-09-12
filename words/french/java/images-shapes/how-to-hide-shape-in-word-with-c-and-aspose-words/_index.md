---
category: general
date: 2026-09-11
description: Apprenez comment masquer une forme dans Word en utilisant C#. Ce guide
  montre également comment insérer une forme rectangulaire et insérer une forme dans
  un document Word avec Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape in word
- insert rectangle shape
- insert shape into word document
language: fr
lastmod: 2026-09-11
og_description: Comment masquer une forme dans Word en utilisant C# et Aspose.Words.
  Suivez le tutoriel étape par étape pour insérer une forme rectangulaire et gérer
  les formes dans un document Word.
og_image_alt: Screenshot showing how to hide shape in Word document using C#
og_title: Comment masquer une forme dans Word – guide complet C#
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  headline: How to hide shape in Word with C# and Aspose.Words
  type: TechArticle
- description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  name: How to hide shape in Word with C# and Aspose.Words
  steps:
  - name: Explanation of each step
    text: 1. **Create a new document** – `Document` represents the Word file in memory.
      `DocumentBuilder` provides a fluent API for inserting content. 2. **Insert rectangle
      shape** – `InsertShape` creates a drawing object of type `Rectangle`. The dimensions
      are expressed in points (1 pt ≈ 1/72 in). This satis
  - name: Expected result
    text: 'Open `output.docx` in Microsoft Word:'
  - name: Manually adding the hidden attribute (fallback)
    text: '```csharp // Fallback for Aspose.Words versions prior to 24.10 Shape shape
      = builder.InsertShape(ShapeType.Rectangle, 100, 50); shape.FillColor = System.Drawing.Color.LightGray;'
  type: HowTo
- questions:
  - answer: No. Hidden shapes are ignored by the layout engine, so they do not consume
      space. This is useful for placeholder content that should not affect page breaks.
    question: Does hiding a shape affect pagination?
  - answer: Yes. The same `Hidden` property works on shapes located anywhere in the
      document tree, including headers, footers, and even inside tables.
    question: Can I hide a shape that is part of a header or footer?
  - answer: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` for each target shape. ```csharp foreach (Shape s in
      doc.GetChildNodes(NodeType.Shape, true)) { if (s.ShapeType == ShapeType.Rectangle)
      s.Hidden = true; } ```
    question: What if I need to hide multiple shapes at once?
  - answer: 'When converting to PDF, hidden shapes are omitted by default, matching
      Word’s rendering behavior. If you need them in the PDF, you must unhide them
      before conversion. ## Tips and pitfalls * **Pro tip:** Set `shape.WrapType =
      WrapType.None` before hiding if you later plan to unhide the shape without '
    question: Is the hidden attribute preserved when converting to PDF?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Word automation
title: Comment masquer une forme dans Word avec C# et Aspose.Words
url: /fr/java/images-shapes/how-to-hide-shape-in-word-with-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment masquer une forme dans Word avec C# et Aspose.Words

Si vous devez masquer une forme dans Word tout en conservant la forme dans la structure du document, ce tutoriel vous montre exactement comment faire. En utilisant Aspose.Words pour .NET, vous pouvez insérer une forme rectangulaire, la masquer, et garder sa position pour un traitement ultérieur.

L’automatisation de Word nécessite souvent un contrôle fin des formes — que vous génériez des modèles, prépariez des rapports ou construisiez un service d’édition de documents. À la fin de ce guide, vous serez capable de :

* Insérer une forme rectangulaire dans un document Word (`insert rectangle shape`).
* Masquer n’importe quelle forme sans la supprimer (`how to hide shape in word`).
* Enregistrer le résultat et vérifier que la forme masquée n’apparaît pas dans la vue rendue (`insert shape into word document`).

L’exemple fonctionne avec Aspose.Words 24.10 ou supérieur et cible .NET 6.0+, mais les concepts s’appliquent également aux versions antérieures.

## Prérequis

* **Aspose.Words for .NET** ≥ 24.10. Vous pouvez obtenir une licence temporaire gratuite sur le site d’Aspose.
* **.NET SDK** 6.0 ou plus récent installé sur votre machine.
* Un environnement de développement tel que Visual Studio 2022, VS Code ou Rider.
* Une connaissance de base du C# et du concept Word Open XML (optionnel mais utile).

## Comment masquer une forme dans Word avec Aspose.Words

Voici un programme complet et exécutable qui démontre l’ensemble du flux de travail — de la création d’un document à l’insertion d’une forme rectangulaire, puis à son masquage.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HideShapeDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a rectangle shape (100 × 50 points) at the current cursor position.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        // Optional: give the shape a visible fill so you can see it before hiding.
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Hide the shape without removing it from the document.
        // The Hidden property is available starting with Aspose.Words 24.10.
        rectangle.Hidden = true;

        // Step 4: Save the document to disk.
        string outputPath = "output.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}. The rectangle shape is hidden.");
    }
}
```

### Explication de chaque étape

1. **Créer un nouveau document** – `Document` représente le fichier Word en mémoire. `DocumentBuilder` fournit une API fluide pour insérer du contenu.
2. **Insérer une forme rectangulaire** – `InsertShape` crée un objet de dessin de type `Rectangle`. Les dimensions sont exprimées en points (1 pt ≈ 1/72 in). Cela satisfait le besoin `insert rectangle shape`.
3. **Masquer la forme** – En définissant `Shape.Hidden = true`, la forme est marquée comme masquée dans le balisage Word (`<w:hidden/>`). La forme reste partie de l’arbre du document, vous pouvez donc la réafficher ou y accéder programmatiquement plus tard. C’est le cœur de `how to hide shape in word`.
4. **Enregistrer le fichier** – Le document est écrit dans `output.docx`. Lorsqu’il est ouvert dans Microsoft Word, le rectangle ne sera pas visible, mais il existe toujours dans le XML et peut être inspecté avec un visualiseur ZIP ou l’Open XML SDK.

### Résultat attendu

Ouvrez `output.docx` dans Microsoft Word :

* Le document apparaît vide — aucune forme visible.
* Si vous inspectez le XML sous‑jacent (`word/document.xml`), vous trouverez un élément `<w:pict>` avec un attribut `<w:hidden/>`, confirmant que la forme est présente mais masquée.

```xml
<w:pict>
  <v:shape id="Shape0" style="position:absolute; ...">
    <v:fillcolor>#ADD8E6</v:fillcolor>
    <w:hidden/>
  </v:shape>
</w:pict>
```

La forme masquée peut être rendue visible à nouveau en définissant `Hidden = false` puis en ré‑enregistrant le document.

## Insérer une forme rectangulaire dans un document Word

Bien que l’objectif principal soit de masquer une forme, de nombreux scénarios commencent par insérer d’abord une forme. La méthode `InsertShape` prend en charge de nombreuses valeurs `ShapeType`, dont `Rectangle`, `Ellipse`, `Line` et des images personnalisées.

```csharp
// Example: Insert an ellipse shape and keep it visible.
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
ellipse.FillColor = System.Drawing.Color.Pink;
```

**Pourquoi utiliser un rectangle ?**  
Un rectangle fournit un conteneur propre, aligné sur les axes, qui peut contenir du texte, des images ou d’autres formes imbriquées. Il est souvent utilisé comme espace réservé pour du contenu dynamique tel que des tableaux ou des graphiques. En insérant d’abord le rectangle, vous préservez la cohérence de la mise en page même après l’avoir masqué.

## Insérer une forme dans un document Word – bonnes pratiques

Lorsque vous `insert shape into word document`, considérez les points suivants :

* **Définir des dimensions explicites** – Évitez de compter sur le redimensionnement automatique ; spécifiez la largeur et la hauteur en points pour garantir une mise en page cohérente sur toutes les plateformes.
* **Définir le positionnement** – Par défaut, la forme est ancrée au paragraphe courant. Utilisez `builder.MoveTo` ou `builder.StartBookmark` pour la placer avec précision.
* **Appliquer le style tôt** – La couleur de remplissage, le style de ligne et le texte d’habillage influencent l’apparence finale. Même les formes masquées bénéficient d’un style correct car le balisage reste inchangé.
* **Compatibilité de version** – La propriété `Hidden` n’est disponible qu’à partir d’Aspose.Words 24.10. Si vous ciblez une version antérieure, vous pouvez ajouter manuellement l’attribut `<w:hidden/>` à l’aide de l’API `Node`.

### Ajout manuel de l’attribut hidden (solution de secours)

```csharp
// Fallback for Aspose.Words versions prior to 24.10
Shape shape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
shape.FillColor = System.Drawing.Color.LightGray;

// Access the underlying OpenXml node.
var shapeNode = shape.GetChildNodes(NodeType.Any, true)[0];
shapeNode.GetAttributes().Add("w:hidden", "true");
```

## Exemple complet de bout en bout

En réunissant tous les éléments, voici un programme unique qui :

1. Insère une forme rectangulaire.
2. Masque la forme.
3. Insère une ellipse visible pour le contraste.
4. Enregistre le document.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class FullDemo
{
    static void Main()
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert and hide a rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 120, 60);
        rect.FillColor = System.Drawing.Color.LightGreen;
        rect.Hidden = true; // core of how to hide shape in word

        // Insert a visible ellipse to show the difference.
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.FillColor = System.Drawing.Color.Coral;

        // Save the output.
        string filePath = "demo_output.docx";
        doc.Save(filePath);
        Console.WriteLine($"Demo document saved to {filePath}");
    }
}
```

L’exécution du programme produit `demo_output.docx`. Lorsqu’il est ouvert, vous ne verrez que l’ellipse corail ; le rectangle vert est présent dans le XML mais masqué à l’affichage.

## Questions fréquentes et cas particuliers

**Q : Le masquage d’une forme affecte‑t‑il la pagination ?**  
R : Non. Les formes masquées sont ignorées par le moteur de mise en page, elles ne consomment donc pas d’espace. Cela est utile pour du contenu de substitution qui ne doit pas influencer les sauts de page.

**Q : Puis‑je masquer une forme qui fait partie d’un en‑tête ou d’un pied de page ?**  
R : Oui. La même propriété `Hidden` fonctionne sur les formes situées n’importe où dans l’arbre du document, y compris les en‑têtes, pieds de page et même à l’intérieur de tableaux.

**Q : Que faire si je dois masquer plusieurs formes en même temps ?**  
R : Parcourez la collection `Document.GetChildNodes(NodeType.Shape, true)` et définissez `Hidden = true` pour chaque forme ciblée.

```csharp
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.ShapeType == ShapeType.Rectangle)
        s.Hidden = true;
}
```

**Q : L’attribut hidden est‑il conservé lors de la conversion en PDF ?**  
R : Lors de la conversion en PDF, les formes masquées sont omises par défaut, reproduisant le comportement de rendu de Word. Si vous avez besoin qu’elles apparaissent dans le PDF, vous devez les rendre visibles avant la conversion.

## Astuces et pièges

* **Astuce pro :** Définissez `shape.WrapType = WrapType.None` avant de masquer si vous prévoyez de réafficher la forme sans perturber le texte environnant.
* **Attention aux versions plus anciennes d’Aspose.Words** : La propriété `Hidden` lève une `NotSupportedException` avant la version 24.10. Utilisez alors l’approche XML manuelle.
* **Tests :** Ouvrez toujours le `.docx` généré dans Word et utilisez « Show XML markup » (onglet Développeur) pour vérifier que l’attribut `<w:hidden/>` est présent.

## Conclusion

Vous savez maintenant comment masquer une forme dans Word en utilisant C# et Aspose.Words, ainsi que comment insérer une forme rectangulaire et insérer une forme dans un document Word avec un contrôle total de la visibilité. En exploitant la propriété `Hidden`, vous pouvez conserver les formes dans le modèle du document pour un traitement ultérieur tout en présentant une vue épurée aux utilisateurs finaux.

Ensuite, explorez des sujets connexes tels que **la mise à jour des propriétés de forme à l’exécution**, **la conversion des formes masquées en images**, ou **l’utilisation de l’Open XML SDK pour manipuler directement les éléments masqués**. Ces extensions approfondiront vos compétences.

## What Should You Learn Next?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}