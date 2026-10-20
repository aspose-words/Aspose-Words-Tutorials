---
category: general
date: 2026-07-29
description: Créez un document Word vierge et apprenez à masquer une forme, créer
  un objet caché et créer une forme d’ellipse en utilisant Aspose.Words en C#. Code
  étape par étape inclus.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- blank word document
- how to hide shape
- create hidden object
- create ellipse shape
language: fr
lastmod: 2026-07-29
og_description: Créez un document Word vierge et masquez la forme instantanément.
  Apprenez à créer un objet caché et à dessiner une forme d’ellipse en utilisant Aspose.Words
  en C#.
og_image_alt: Hidden ellipse shape inserted into a blank Word document
og_title: Créer un document Word vierge avec une forme d'ellipse cachée – Tutoriel
  C#
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Create a blank word document and learn how to hide shape, create hidden
    object, and create ellipse shape using Aspose.Words in C#. Step‑by‑step code included.
  headline: Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide
  type: TechArticle
- description: Create a blank word document and learn how to hide shape, create hidden
    object, and create ellipse shape using Aspose.Words in C#. Step‑by‑step code included.
  name: Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide
  steps:
  - name: What if the target Word version doesn’t support hidden shapes?
    text: The `Hidden` flag is part of the Office Open XML spec and is respected by
      Word 2007+ and LibreOffice. Older formats (e.g., `.doc`) ignore the flag, so
      always save as `.docx` when you need reliable hiding.
  - name: Can I hide other types of objects (pictures, tables)?
    text: Yes. Any node derived from `Shape`—including pictures, text boxes, and even
      SmartArt—exposes the `Hidden` property. Just set it to `true` before insertion.
  - name: Does hiding a shape affect document performance?
    text: Negligibly. The shape is stored as XML markup, and Word skips rendering
      hidden objects during layout. If you embed many hidden objects, the file size
      grows, but rendering stays fast.
  - name: How does this differ from using a bookmark or comment as a marker?
    text: Bookmarks are invisible by design, but they’re meant for navigation, not
      visual placeholders. Comments appear in the margin. A hidden shape gives you
      a visual object (size, position) that you can later reveal or manipulate, which
      is handy for templating scenarios.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
- Shapes
title: Créer un document Word vierge avec une forme d'ellipse cachée – Guide complet
  C#
url: /fr/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un document Word vierge avec une forme d'ellipse masquée – Guide complet C#  

Vous avez déjà eu besoin de créer un **document Word vierge** puis de masquer une forme à l'intérieur ? Peut‑être générez‑vous un modèle où certains marqueurs doivent rester invisibles jusqu'à une étape ultérieure. Dans ce tutoriel, nous allons expliquer exactement **comment masquer une forme**, comment **créer un objet masqué**, et même comment **créer une forme d'ellipse** en utilisant Aspose.Words pour .NET. À la fin, vous disposerez d’un extrait C# prêt à l’exécution qui produit un fichier DOCX contenant une ellipse invisible.

## Ce que vous allez apprendre

- Initialiser un nouveau document Word vierge avec Aspose.Words.  
- Créer une forme d'ellipse, définir ses dimensions et la positionner sur la page.  
- Marquer la forme comme masquée afin qu'elle n'apparaisse jamais à l'écran ni à l'impression.  
- Enregistrer le résultat sur le disque et vérifier que l'objet masqué est réellement invisible.  

Aucune bibliothèque externe en plus d'Aspose.Words n'est requise, et le code fonctionne avec la version 24.10 ou supérieure (la propriété `Hidden` a été introduite dans cette version). Commençons.

![Diagramme d'une ellipse masquée dans un document Word vierge](https://example.com/hidden-ellipse.png "Forme d'ellipse masquée insérée dans un document Word vierge")

## Créer un document Word vierge et insérer une forme d'ellipse masquée

La première étape consiste à créer un tout nouveau document. Considérez `Document` comme une toile vide ; `DocumentBuilder` est votre pinceau.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document and a DocumentBuilder to edit it.
Document document = new Document();               // This is your blank word document.
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Pourquoi commencer avec un document vierge ?**  
> Une page blanche garantit qu'aucun contenu préexistant n'interfère avec la forme masquée que vous allez ajouter. Cela rend également l'exemple plus facile à copier‑coller dans n'importe quel projet.

## Comment masquer une forme : définir la propriété Hidden

Aspose.Words 24.10 a introduit le drapeau `Hidden` sur `Shape`. Lorsqu'il est réglé sur `true`, Word traite la forme comme un commentaire — complètement invisible dans l'interface et à l'impression.

```csharp
// Step 2: Create an ellipse shape and set its size and position.
Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
ellipseShape.Width = 100;   // Width in points
ellipseShape.Height = 80;   // Height in points
ellipseShape.Left = 150;    // Horizontal offset from the left margin
ellipseShape.Top = 150;     // Vertical offset from the top margin

// Step 3: Hide the shape so it does not appear when the document is viewed or printed.
ellipseShape.Hidden = true;   // This is the key to "how to hide shape"
```

> **Astuce :** Si vous devez plus tard révéler la forme par programme, il suffit de basculer `ellipseShape.Hidden = false;` et de ré‑enregistrer le document.

## Créer un objet masqué : insérer la forme dans le document

Maintenant que l'ellipse est prête et masquée, nous l'insérons à l'emplacement actuel du curseur du builder. La position du builder par défaut est le début du premier paragraphe, ce qui est parfait pour un document vierge.

```csharp
// Step 4: Insert the hidden shape into the document at the current builder position.
builder.InsertNode(ellipseShape);
```

> **Et si vous avez besoin de la forme sur une page spécifique ?**  
> Déplacez d'abord le builder vers la page souhaitée (`builder.MoveToDocumentEnd();` ou `builder.MoveToPage(pageNumber);`) avant d'appeler `InsertNode`.

## Enregistrer le document contenant la forme masquée

Enfin, écrivez le fichier sur le disque. Le résultat sera un DOCX standard que n'importe quel traitement de texte peut ouvrir—sauf que l'ellipse restera invisible.

```csharp
// Step 5: Save the document containing the hidden shape.
document.Save("YOUR_DIRECTORY/HiddenShape.docx");
```

> **Résultat attendu :** Ouvrez `HiddenShape.docx` dans Microsoft Word. Vous ne verrez aucun graphique, mais la taille du fichier sera légèrement supérieure à celle d'un document réellement vide car l'ellipse masquée est stockée dans le XML.

## Vérifier l'ellipse masquée par programme (facultatif)

Si vous souhaitez revérifier que la forme est bien masquée, vous pouvez charger le fichier enregistré et inspecter la propriété `Hidden` de la forme :

```csharp
Document loaded = new Document("YOUR_DIRECTORY/HiddenShape.docx");
Shape loadedShape = (Shape)loaded.GetChild(NodeType.Shape, 0, true);
Console.WriteLine($"Is shape hidden? {loadedShape.Hidden}"); // Should print True
```

L'exécution de cet extrait affiche `True`, confirmant que l'objet masqué a survécu au cycle d'enregistrement‑chargement.

## Cas limites et questions fréquentes

### Que faire si la version cible de Word ne prend pas en charge les formes masquées ?

Le drapeau `Hidden` fait partie de la spécification Office Open XML et est respecté par Word 2007+ et LibreOffice. Les formats plus anciens (par ex., `.doc`) ignorent ce drapeau, il faut donc toujours enregistrer en `.docx` lorsque vous avez besoin d'un masquage fiable.

### Puis‑je masquer d'autres types d'objets (images, tableaux) ?

Oui. Tout nœud dérivé de `Shape`—y compris les images, les zones de texte et même les SmartArt—expose la propriété `Hidden`. Il suffit de la régler sur `true` avant l'insertion.

### Le masquage d'une forme affecte‑t‑il les performances du document ?

Négligeablement. La forme est stockée sous forme de balisage XML, et Word ignore le rendu des objets masqués pendant la mise en page. Si vous intégrez de nombreuses formes masquées, la taille du fichier augmente, mais le rendu reste rapide.

### En quoi cela diffère‑t‑il de l'utilisation d'un signet ou d'un commentaire comme marqueur ?

Les signets sont invisibles par conception, mais ils sont destinés à la navigation, pas aux espaces réservés visuels. Les commentaires apparaissent dans la marge. Une forme masquée vous fournit un objet visuel (taille, position) que vous pouvez révéler ou manipuler plus tard, ce qui est pratique pour les scénarios de templating.

## Exemple complet fonctionnel

Ci‑dessus se trouve le programme complet, prêt à copier‑coller. Il comprend toutes les directives `using`, la création de l'ellipse masquée et une étape de vérification.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HiddenEllipseDemo
{
    static void Main()
    {
        // 1️⃣ Create a blank word document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Build the ellipse shape.
        Shape ellipse = new Shape(doc, ShapeType.Ellipse)
        {
            Width = 100,
            Height = 80,
            Left = 150,
            Top = 150,
            Hidden = true               // ← how to hide shape
        };

        // 3️⃣ Insert the hidden shape.
        builder.InsertNode(ellipse);

        // 4️⃣ Save the file.
        string outPath = "HiddenEllipse.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");

        // 5️⃣ Optional: Verify that the shape is hidden.
        Document loaded = new Document(outPath);
        Shape loadedEllipse = (Shape)loaded.GetChild(NodeType.Shape, 0, true);
        Console.WriteLine($"Is the ellipse hidden? {loadedEllipse.Hidden}");
    }
}
```

L'exécution du programme crée `HiddenEllipse.docx` dans le dossier d'exécution. Ouvrez‑le — vous verrez une page vierge parfaitement normale, mais l'ellipse masquée vit discrètement à l'intérieur.

## Récapitulatif

Nous avons vu comment **créer un document Word vierge**, **masquer une forme**, **créer un objet masqué**, et **créer une forme d'ellipse**, le tout avec quelques lignes de C#. L'essentiel à retenir est la propriété `Hidden` sur `Shape`, qui transforme tout élément visuel en un marqueur invisible sans compromettre la compatibilité avec Word.

## Et après ?

- **Styliser la forme masquée** (couleur de remplissage, style de ligne) afin que lorsqu'elle sera révélée plus tard, elle apparaisse exactement comme prévu.  
- **Combiner les formes masquées avec des signets** pour créer des modèles dynamiques qui peuvent être activés ou désactivés.  
- **Explorer d'autres types de formes**—rectangles, flèches, ou même des chemins SVG personnalisés—en remplaçant `ShapeType.Ellipse`.  

N'hésitez pas à expérimenter : modifiez la taille, déplacez la position, ou insérez plusieurs ellipses masquées. Le même schéma fonctionne pour toute forme Aspose.Words que vous devez garder hors de vue.

Si vous rencontrez un problème ou avez des idées pour étendre ce schéma, laissez un commentaire ci‑dessous. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code fonctionnels complets avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l'API et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Créer un document Word vierge avec une forme de rectangle ombrée – Guide étape par étape](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Créer une forme groupée dans un document Word en utilisant Aspose.Words pour .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Créer une forme de rectangle dans Word avec Aspose.Words – Guide étape par étape](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}