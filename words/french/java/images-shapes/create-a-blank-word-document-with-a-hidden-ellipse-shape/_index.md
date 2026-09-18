---
category: general
date: 2026-09-18
description: Créez un document Word vierge et masquez une forme d'ellipse à l'aide
  d'Aspose.Words. Apprenez comment masquer une forme dans Word, comment insérer une
  ellipse et créer rapidement une forme masquée.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to hide shape
- how to insert ellipse
- hide shape in word
- create hidden shape
language: fr
lastmod: 2026-09-18
og_description: Créez un document Word vierge et masquez une forme d’ellipse dans
  Word. Ce guide vous montre, étape par étape, comment insérer une ellipse, masquer
  la forme dans Word et créer une forme cachée avec Aspose.Words.
og_image_alt: Screenshot of a blank Word document containing a hidden ellipse shape
  created with Aspose.Words
og_title: Créer un document Word vierge avec une forme d'ellipse cachée
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create a blank Word document and hide an ellipse shape using Aspose.Words.
    Learn how to hide shape in Word, how to insert ellipse, and create hidden shape
    quickly.
  headline: Create a blank Word document with a hidden ellipse shape
  type: TechArticle
- description: Create a blank Word document and hide an ellipse shape using Aspose.Words.
    Learn how to hide shape in Word, how to insert ellipse, and create hidden shape
    quickly.
  name: Create a blank Word document with a hidden ellipse shape
  steps:
  - name: Pro tip
    text: If you later need to make the shape visible again, simply set `ellipse.Hidden
      = false;` and save the document.
  - name: What if the shape still appears?
    text: '* Ensure you are using Aspose.Words 23.9 or later – older versions had
      a bug where `Hidden` was ignored for some shape types. * Verify that you are
      not applying any additional formatting (e.g., `WrapType`) that forces the shape
      to occupy layout space.'
  - name: Can I hide other shape types?
    text: Yes. The same `Hidden` property works for `ShapeType.Rectangle`, `ShapeType.Picture`,
      etc. Just replace `ShapeType.Ellipse` with the desired type.
  - name: How to list hidden shapes later?
    text: '```csharp foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
      { if (shape.Hidden) Console.WriteLine($"Hidden shape: {shape.ShapeType}"); }
      ```'
  - name: Next steps
    text: '* Explore **how to hide shape** conditionally based on document content.
      * Learn **how to unhide shape** when generating a final version of the document.
      * Combine hidden shapes with **custom document properties** to embed machine‑readable
      data.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Créer un document Word vierge avec une forme d'ellipse cachée
url: /fr/java/images-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un document Word vierge avec une forme d'ellipse masquée

Si vous devez **créer un document Word vierge** contenant une forme que vous ne voulez pas voir apparaître dans la mise en page, ce guide vous montre exactement comment procéder. En utilisant Aspose.Words pour .NET, vous pouvez insérer programmétiquement une ellipse puis masquer la forme afin que le document reste visuellement vide tout en conservant les données de la forme.

Dans ce tutoriel, vous apprendrez :

* comment **créer un document Word vierge**,
* comment **insérer une ellipse** à l'aide de `DocumentBuilder`,
* comment **masquer la forme dans Word** afin qu'elle n'affecte pas la page,
* comment **créer une forme masquée** pour un traitement ultérieur.

Les étapes fonctionnent avec .NET 6+ et la dernière version d'Aspose.Words (23.9 au moment de la rédaction). Aucune installation supplémentaire d'Office n'est requise.

## Prérequis

* Visual Studio 2022 (ou tout IDE C#)
* SDK .NET 6 ou ultérieur
* Package NuGet Aspose.Words for .NET  
  ```bash
  dotnet add package Aspose.Words
  ```
* Connaissances de base en C# et concepts de documents Word

## Étape 1 : Créer un document Word vierge

La première chose à faire est d'instancier un objet `Document`. Cet objet représente un fichier `.docx` vide et constitue la base de toutes les opérations ultérieures.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document
Document doc = new Document();   // <-- creates a blank Word document in memory
```

Créer un **document Word vierge** vous offre une toile propre – aucun paragraphe, aucune section, seulement la structure de paquet sous-jacente. C’est le point de départ idéal lorsque vous avez uniquement besoin d’une forme masquée et rien d’autre.

## Étape 2 : Initialiser un DocumentBuilder

`DocumentBuilder` fournit une API pratique pour ajouter du contenu à un `Document`. Il fonctionne comme un curseur que vous déplacez à travers le document.

```csharp
// Step 2: Initialise a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

Le constructeur crée automatiquement une première section et un paragraphe par défaut, vous permettant de commencer à insérer des formes sans ajouter manuellement des sections.

## Étape 3 : Insérer une forme d'ellipse

Nous **insérons une ellipse** maintenant à l'aide de la méthode `InsertShape`. Cette méthode prend une énumération `ShapeType`, la largeur et la hauteur (en points).

```csharp
// Step 3: Insert an ellipse shape with a width of 100 points and a height of 50 points
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
```

Pourquoi une ellipse ? Une ellipse est une forme vectorielle qui peut être masquée sans affecter le flux du texte environnant. La largeur de 100 pt et la hauteur de 50 pt sont arbitraires ; vous pouvez les ajuster selon vos besoins de traitement ultérieur.

## Étape 4 : Masquer la forme afin qu’elle n’apparaisse pas dans la mise en page

Pour **masquer la forme dans Word**, définissez la propriété `Hidden` de l'objet `Shape` sur `true`. Lorsque le document est ouvert dans Microsoft Word, la forme sera invisible et n’occupera pas d’espace dans la mise en page.

```csharp
// Step 4: Hide the shape so it does not appear in the layout
ellipse.Hidden = true;   // <-- this hides the shape in Word
```

Le drapeau `Hidden` est stocké dans le XML de la forme (`<w:hidden/>`). Word respecte cet attribut lors du rendu, ce qui explique pourquoi le document apparaît complètement vide bien que la forme existe.

### Astuce

Si vous devez plus tard rendre la forme visible à nouveau, il suffit de définir `ellipse.Hidden = false;` puis d’enregistrer le document.

## Étape 5 : Enregistrer le document avec la forme masquée

Enfin, persistez le document sur le disque. Le fichier sera un `.docx` standard que tout traitement de texte peut ouvrir.

```csharp
// Step 5: Save the document with the hidden shape
doc.Save(@"C:\Temp\HiddenEllipse.docx");
```

Le fichier enregistré, `HiddenEllipse.docx`, est un **document Word vierge** qui contient une ellipse masquée. L’ouvrir dans Microsoft Word affiche une page vide, mais la forme est toujours présente dans la structure Open XML.

## Exemple complet fonctionnel

Ci-dessous se trouve le programme complet et autonome que vous pouvez copier, coller et exécuter.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace HiddenShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a blank Word document
            Document doc = new Document();

            // 2️⃣ Initialise DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert an ellipse shape (width: 100pt, height: 50pt)
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

            // 4️⃣ Hide the shape so it does not affect layout
            ellipse.Hidden = true;

            // 5️⃣ Save the result
            string outputPath = @"C:\Temp\HiddenEllipse.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Sortie attendue**

* Un fichier nommé `HiddenEllipse.docx` apparaît dans `C:\Temp`.
* L’ouverture du fichier dans Microsoft Word affiche une page complètement vide.
* Si vous inspectez le document avec l’Open XML SDK ou un visualiseur zip, vous trouverez l’élément `<w:shape>` contenant `<w:hidden/>` dans la partie du document.

## Questions fréquentes et cas particuliers

### Que faire si la forme apparaît encore ?

* Assurez‑vous d’utiliser Aspose.Words 23.9 ou une version ultérieure – les versions antérieures comportaient un bug où `Hidden` était ignoré pour certains types de formes.
* Vérifiez que vous n’appliquez aucun formatage supplémentaire (par ex., `WrapType`) qui forcerait la forme à occuper de l’espace dans la mise en page.

### Puis‑je masquer d’autres types de formes ?

Oui. La même propriété `Hidden` fonctionne pour `ShapeType.Rectangle`, `ShapeType.Picture`, etc. Il suffit de remplacer `ShapeType.Ellipse` par le type souhaité.

### Comment lister les formes masquées ultérieurement ?

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.Hidden)
        Console.WriteLine($"Hidden shape: {shape.ShapeType}");
}
```

Cet extrait parcourt toutes les formes et affiche celles qui sont masquées, ce qui est utile pour les flux de travail **de création de formes masquées** où vous devez plus tard les traiter ou les rendre visibles.

## Conclusion

Vous savez maintenant comment **créer un document Word vierge**, **insérer une ellipse**, et **masquer une forme dans Word** afin de produire une **forme masquée** qui reste invisible pour le lecteur. Cette technique est pratique pour stocker des métadonnées, des signets ou du XML personnalisé dans un document sans en modifier l’apparence visuelle.

### Prochaines étapes

* Explorer **comment masquer une forme** conditionnellement en fonction du contenu du document.
* Apprendre **comment rendre une forme visible** lors de la génération d’une version finale du document.
* Combiner les formes masquées avec **des propriétés de document personnalisées** pour intégrer des données lisibles par machine.

N’hésitez pas à expérimenter différents types de formes, tailles et logiques d’état masqué pour adapter votre scénario d’automatisation. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l’API et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Créer un document Word vierge avec une forme rectangulaire ombrée – Guide étape par étape](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Créer une forme rectangulaire dans Word avec Aspose.Words – Guide étape par étape](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Créer une forme groupée dans un document Word en utilisant Aspose.Words pour .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}