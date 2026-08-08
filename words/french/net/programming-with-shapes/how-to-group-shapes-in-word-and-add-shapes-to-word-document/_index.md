---
category: general
date: 2026-08-07
description: Comment regrouper des formes dans Word avec Aspose.Words et ajouter des
  formes à un document Word en utilisant C#. Suivez ce guide étape par étape pour
  un code propre et réutilisable.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes in word
- add shapes to word document
language: fr
lastmod: 2026-08-07
og_description: Comment regrouper des formes dans Word à l'aide d'Aspose.Words pour
  .NET. Ce tutoriel vous montre comment ajouter des formes à un document Word, les
  regrouper et enregistrer le fichier avec du code C# clair.
og_image_alt: Screenshot of a rectangle and ellipse grouped in a Word document created
  with Aspose.Words
og_title: Comment regrouper des formes dans Word – guide C# rapide
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to group shapes in Word with Aspose.Words and add shapes to Word
    document using C#. Follow this step‑by‑step guide for clean, reusable code.
  headline: How to group shapes in Word and add shapes to Word document
  type: TechArticle
- description: How to group shapes in Word with Aspose.Words and add shapes to Word
    document using C#. Follow this step‑by‑step guide for clean, reusable code.
  name: How to group shapes in Word and add shapes to Word document
  steps:
  - name: Create a document and a builder
    text: A `Document` object represents the entire DOCX file. `DocumentBuilder` provides
      a convenient API for editing the document.
  - name: Add the rectangle shape
    text: A rectangle is created by specifying `ShapeType.Rectangle`. Width, height,
      and location are set in points (1 pt ≈ 1/72 in).
  - name: Add the ellipse shape
    text: The ellipse uses `ShapeType.Ellipse`. Its size and position are independent
      of the rectangle, which allows you to control the final layout of the group.
  - name: Group the two shapes
    text: '`GroupShape` acts as a container that treats its children as a single object.
      This is the essential operation for **how to group shapes in Word**.'
  - name: Insert the grouped shape into the document
    text: '`DocumentBuilder.InsertNode` places the `GroupShape` at the current cursor
      location. Because we have not moved the builder, the group appears at the start
      of the first page.'
  - name: Save the document
    text: Finally, write the DOCX file to disk. Use a full path that your application
      can write to.
  - name: Expected output
    text: Open `GroupShape.docx`. You will see a single visual object that contains
      a blue rectangle on the left and a green ellipse on the right. Selecting the
      object in Word highlights both shapes simultaneously—proof that **how to group
      shapes in Word** succeeded.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Comment regrouper des formes dans Word et ajouter des formes à un document
  Word
url: /fr/net/programming-with-shapes/how-to-group-shapes-in-word-and-add-shapes-to-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment regrouper des formes dans Word et ajouter des formes à un document Word

If you need to **how to group shapes in Word**, this guide walks you through the complete process using Aspose.Words for .NET. You will also learn **add shapes to Word document** with a few lines of C# code, so the result is ready for any reporting or templating scenario.

The tutorial covers everything you need: required NuGet packages, a full source file, and an explanation of why each step matters. By the end you can generate a DOCX that contains a rectangle and an ellipse combined into a single group shape.

## Prérequis

Before you start, make sure you have:

* .NET 6.0 SDK or later installed  
* Visual Studio 2022 (or any IDE that supports .NET)  
* Aspose.Words for .NET NuGet package (`Aspose.Words`) – the free trial works for testing, but a license removes evaluation watermarks  

These items are the only external dependencies for **add shapes to Word document**.

## Comment regrouper des formes dans Word

The core of the solution is creating individual shapes, placing them on the page, and then wrapping them in a `GroupShape`. The following steps mirror the logical order of the code.

### Étape 1 : Créer un document et un constructeur

A `Document` object represents the entire DOCX file. `DocumentBuilder` provides a convenient API for editing the document.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create an empty Word document
Document doc = new Document();

// DocumentBuilder lets you insert nodes, text, and shapes
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Pourquoi c’est important* : The `Document` is the container for all Word elements. The `DocumentBuilder` keeps track of the current cursor position, which is required when you later insert the grouped shape.

### Étape 2 : Ajouter la forme rectangle

A rectangle is created by specifying `ShapeType.Rectangle`. Width, height, and location are set in points (1 pt ≈ 1/72 in).

```csharp
Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
rectangleShape.Width = 100;               // 100 pt wide
rectangleShape.Height = 50;               // 50 pt tall
rectangleShape.Left = 0;                  // X‑coordinate
rectangleShape.Top = 0;                   // Y‑coordinate
rectangleShape.StrokeColor = Color.Blue; // Outline color
```

*Pourquoi c’est important* : Setting `StrokeColor` makes the shape visible when the document is opened. You could also fill the shape with `FillColor` if a solid interior is required.

### Étape 3 : Ajouter la forme ellipse

The ellipse uses `ShapeType.Ellipse`. Its size and position are independent of the rectangle, which allows you to control the final layout of the group.

```csharp
Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
ellipseShape.Width = 80;
ellipseShape.Height = 80;
ellipseShape.Left = 120;                  // Placed to the right of the rectangle
ellipseShape.Top = 0;
ellipseShape.StrokeColor = Color.Green;
```

*Pourquoi c’est important* : By positioning the ellipse at `Left = 120`, it does not overlap the rectangle, making the group visually distinct.

### Étape 4 : Regrouper les deux formes

`GroupShape` acts as a container that treats its children as a single object. This is the essential operation for **how to group shapes in Word**.

```csharp
GroupShape groupShape = new GroupShape(doc);
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);
```

*Pourquoi c’est important* : Grouping enables you to move, resize, or rotate both shapes together. Any transformation applied to `groupShape` propagates to its children.

### Étape 5 : Insérer la forme groupée dans le document

`DocumentBuilder.InsertNode` places the `GroupShape` at the current cursor location. Because we have not moved the builder, the group appears at the start of the first page.

```csharp
builder.InsertNode(groupShape);
```

*Pourquoi c’est important* : Inserting the node directly avoids the need for a separate paragraph or table cell. The group becomes part of the document flow.

### Étape 6 : Enregistrer le document

Finally, write the DOCX file to disk. Use a full path that your application can write to.

```csharp
doc.Save(@"C:\Temp\GroupShape.docx");
```

*Pourquoi c’est important* : `doc.Save` finalizes all changes. The resulting file can be opened in Microsoft Word, LibreOffice, or any viewer that supports DOCX.

## Fichier source complet

Copy the code below into a new console project (`dotnet new console`) and run it. The program creates a file named `GroupShape.docx` containing a grouped rectangle and ellipse.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordShapeGrouping
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new document and a builder to edit it
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Define a rectangle shape
            Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
            rectangleShape.Width = 100;
            rectangleShape.Height = 50;
            rectangleShape.Left = 0;
            rectangleShape.Top = 0;
            rectangleShape.StrokeColor = Color.Blue;

            // Step 3: Define an ellipse shape
            Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
            ellipseShape.Width = 80;
            ellipseShape.Height = 80;
            ellipseShape.Left = 120;
            ellipseShape.Top = 0;
            ellipseShape.StrokeColor = Color.Green;

            // Step 4: Group the two shapes together
            GroupShape groupShape = new GroupShape(doc);
            groupShape.AppendChild(rectangleShape);
            groupShape.AppendChild(ellipseShape);

            // Step 5: Insert the grouped shape into the document
            builder.InsertNode(groupShape);

            // Step 6: Save the document
            doc.Save(@"C:\Temp\GroupShape.docx");
        }
    }
}
```

### Résultat attendu

Open `GroupShape.docx`. You will see a single visual object that contains a blue rectangle on the left and a green ellipse on the right. Selecting the object in Word highlights both shapes simultaneously—proof that **how to group shapes in Word** succeeded.

## Questions fréquentes et cas particuliers

* **Puis-je ajouter plus de deux formes ?**  
  Yes. Call `groupShape.AppendChild` for each additional `Shape` before inserting the group.

* **Et si je dois faire pivoter le groupe ?**  
  Set `groupShape.RotationAngle = 45;` (angle in degrees) after the group is built.

* **Dois‑je appeler `doc.UpdatePageLayout()` ?**  
  Not for this scenario. The layout updates automatically when the document is saved.

* **Comment la licence affecte‑t‑elle le code ?**  
  With a valid Aspose.Words license (`License license = new License(); license.SetLicense("Aspose.Words.lic");`) the generated document contains no evaluation watermark.

## Conclusion

You now know **how to group shapes in Word** and **add shapes to Word document** using Aspose.Words for .NET. The tutorial covered creating a document, defining individual shapes, grouping them, inserting the group, and saving the file.  

From here you can experiment with:

* Adding text boxes or pictures to the group  
* Changing fill colors, line styles, or shadow effects  
* Grouping shapes inside tables or headers  

These extensions let you build sophisticated Word templates programmatically while keeping the code clean and maintainable. Happy coding!

## Que devriez‑vous apprendre ensuite ?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Word Document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}