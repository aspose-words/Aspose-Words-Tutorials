---
category: general
date: 2026-09-08
description: Apprenez à regrouper des formes dans Word avec DocumentBuilder, créez
  un document Word vierge et insérez une forme rectangulaire en quelques lignes de
  code C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create blank word doc
- insert rectangle shape word
- how to use documentbuilder
language: fr
lastmod: 2026-09-08
og_description: Regroupez des formes dans Word à l'aide de DocumentBuilder. Ce tutoriel
  montre comment créer un document Word vierge, insérer une forme rectangulaire et
  combiner les formes en un GroupShape.
og_image_alt: Screenshot of a Word document showing grouped shapes – group shapes
  in Word example
og_title: Regrouper des formes dans Word avec DocumentBuilder – exemple complet en
  C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to group shapes in Word with a DocumentBuilder, create a
    blank Word doc, and insert a rectangle shape in just a few lines of C# code.
  headline: How to group shapes in Word using DocumentBuilder – step‑by‑step guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Comment regrouper des formes dans Word avec DocumentBuilder – guide étape par
  étape
url: /fr/net/programming-with-shapes/how-to-group-shapes-in-word-using-documentbuilder-step-by-st/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment regrouper des formes dans Word avec DocumentBuilder – guide étape par étape

Si vous devez **regrouper des formes dans Word** de manière programmatique, ce tutoriel présente une solution complète en C#. Vous verrez comment **créer un document Word vierge**, utiliser **DocumentBuilder**, et **insérer une forme rectangle** avant de la regrouper avec une ellipse. Le résultat est un seul `GroupShape` que vous pouvez déplacer, redimensionner ou styliser comme un seul objet.

Ce guide couvre tout ce que vous devez savoir pour générer un document Word avec des graphiques groupés en utilisant la bibliothèque Aspose.Words pour .NET. À la fin de l'article, vous disposerez d'un projet exécutable qui produit `GroupedShapes.docx` contenant un rectangle et une ellipse combinés en une seule forme.

## Prérequis

- .NET 6.0 ou supérieur (le code fonctionne également avec .NET Framework 4.7.2+)
- Package NuGet Aspose.Words for .NET (`Aspose.Words`) – version 23.12 ou plus récente
- Un IDE C# tel que Visual Studio 2022 ou Visual Studio Code
- Familiarité de base avec la syntaxe C# et la programmation orientée objet

> **Astuce :** Installez le package NuGet depuis la ligne de commande pour garder votre projet propre :  
> `dotnet add package Aspose.Words --version 23.12.0`

## Étape 1 : Créer un document Word vierge

La première opération consiste à instancier un objet `Document`, qui représente un fichier Word vide, et un `DocumentBuilder` qui vous permet d'ajouter du contenu.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Step 1: Create a blank Word document and a DocumentBuilder
        Document document = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Pourquoi c’est important :** `Document` fournit le conteneur de fichier, tandis que `DocumentBuilder` offre une API fluide pour insérer du texte, des images et des formes. Sans `DocumentBuilder`, vous devriez manipuler l'arbre de nœuds du document manuellement, ce qui est source d’erreurs.

## Étape 2 : Insérer une forme rectangle

Un rectangle est un élément de base courant pour les diagrammes. Utilisez `InsertShape` avec `ShapeType.Rectangle` et spécifiez la largeur et la hauteur en points (1 pt ≈ 1/72 in).

```csharp
        // Step 2: Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;   // distance from the left margin (points)
        rectangleShape.Top = 50;    // distance from the top margin (points)
```

**Pourquoi c’est important :** Définir `Left` et `Top` positionne le rectangle précisément sur la page, ce qui est essentiel lorsque vous le regroupez plus tard avec d’autres formes. La méthode `InsertShape` ajoute automatiquement la forme au paragraphe actuel.

## Étape 3 : Insérer une forme ellipse

Ensuite, ajoutez une ellipse qui se placera à côté du rectangle.

```csharp
        // Step 3: Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;
```

**Pourquoi c’est important :** Utiliser un `ShapeType` différent montre comment la même API `DocumentBuilder` peut créer des graphiques variés. Positionner l’ellipse de façon à ce qu’elle chevauche le rectangle rend l’effet de groupement évident.

## Étape 4 : Regrouper les deux formes

Un `GroupShape` agit comme un conteneur. En ajoutant le rectangle et l’ellipse comme enfants, ils se comportent comme un seul objet.

```csharp
        // Step 4: Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        // Define the bounding rectangle that encloses all child shapes
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Insert the group into the document body
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);
```

**Pourquoi c’est important :** La propriété `Bounds` indique à Word où le groupe se situe sur la page. En ajoutant les formes enfants, vous conservez leur formatage individuel tout en permettant des transformations collectives (déplacement, rotation, redimensionnement).

## Étape 5 : Enregistrer le document

Enfin, écrivez le document sur le disque. Vous pouvez modifier le chemin vers n’importe quel dossier de votre choix.

```csharp
        // Step 5: Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Lorsque vous ouvrez `GroupedShapes.docx` dans Microsoft Word, vous verrez un rectangle et une ellipse regroupés. Sélectionner le groupe mettra en surbrillance les deux formes, vous permettant de les faire glisser ou de les redimensionner comme une seule unité.

### Résultat attendu

- Un fichier Word nommé **GroupedShapes.docx**
- La première page contient un **rectangle** (100 pt × 50 pt) à la position (50, 50)
- Une **ellipse** (80 pt × 80 pt) à la position (200, 70)
- Les deux formes font partie d’un **GroupShape** avec une boîte englobante de 300 pt × 200 pt

## Variations courantes et cas limites

| Scénario | Ajustement |
|----------|------------|
| **Taille de page différente** | Définissez `document.Sections[0].PageSetup.PageWidth` et `PageHeight` avant d’insérer les formes. |
| **Plus de deux formes** | Créez des objets `Shape` supplémentaires et appelez `groupShape.AppendChild(newShape)` pour chacun. |
| **Appliquer une couleur de remplissage** | `rectangleShape.FillColor = System.Drawing.Color.LightBlue;` |
| **Faire pivoter le groupe** | `groupShape.Rotation = 45;` (degrees) |
| **Exporter en PDF** | Après avoir enregistré le DOCX, appelez `document.Save("GroupedShapes.pdf");` |

## Code source complet (prêt à l’exécution)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Create a blank Word document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;
        rectangleShape.Top = 50;

        // Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;

        // Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);

        // Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Copiez le code dans un nouveau projet console, restaurez le package NuGet Aspose.Words, puis exécutez-le. La console confirmera l’emplacement du fichier, et l’ouverture du fichier affichera les graphiques groupés.

## Conclusion

Vous savez maintenant **comment regrouper des formes dans Word** avec le `DocumentBuilder` d’Aspose.Words. Le tutoriel a parcouru la création d’un **document Word vierge**, **l’insertion d’une forme rectangle**, l’ajout d’une ellipse, et leur combinaison en un `GroupShape`. Avec cette base, vous pouvez créer des diagrammes plus riches, des organigrammes ou des graphiques personnalisés directement depuis C#.

### Et après ?

- Explorez **how to use DocumentBuilder** pour les tables, les en-têtes et les pieds de page.
- Combinez les techniques **insert rectangle shape Word** avec des zones de texte pour des diagrammes annotés.
- Utilisez **create blank word doc** comme modèle pour la génération automatisée de rapports.

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités d’API supplémentaires et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Créer un groupe de formes dans un document Word avec Aspose.Words pour .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insérer des formes dans des documents Word avec Aspose.Words pour .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Créer une forme rectangle dans Word avec C# – Guide étape par étape](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}