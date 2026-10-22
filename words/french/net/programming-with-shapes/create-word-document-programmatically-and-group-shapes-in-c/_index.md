---
category: general
date: 2026-08-10
description: Créer un document Word de façon programmatique avec Aspose.Words, apprendre
  à regrouper plusieurs formes Word, ajouter un rectangle à Word et créer une forme
  groupée en C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- group multiple shapes word
- add rectangle to word
- how to create group shape
language: fr
lastmod: 2026-08-10
og_description: Créez un document Word de manière programmatique avec Aspose.Words.
  Ce guide vous montre comment regrouper plusieurs formes dans Word, ajouter un rectangle
  dans Word et intégrer un contrôle de contenu texte brut, le tout en C#.
og_image_alt: Screenshot of a Word file showing a grouped rectangle and ellipse with
  a plain‑text content control
og_title: Créer un document Word par programmation – regrouper les formes en C#
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  headline: Create word document programmatically and group shapes in C#
  type: TechArticle
- description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  name: Create word document programmatically and group shapes in C#
  steps:
  - name: – Initialize the document and builder
    text: The `Document` object represents the entire DOCX file, while `DocumentBuilder`
      provides a convenient API to add content. Initializing them is the first requirement
      whenever you **create word document programmatically**.
  - name: – Create a group shape container
    text: A `Shape` with `ShapeType.Group` acts as a canvas that can hold other shapes.
      Setting `Width` and `Height` defines the bounding box for the group. This is
      the core of **how to create group shape** in Aspose.Words.
  - name: – Add a rectangle to word
    text: A rectangle is created with `ShapeType.Rectangle`. Its `Left` and `Top`
      properties position it relative to the group’s origin. This step demonstrates
      **add rectangle to word** and shows how you can control exact placement.
  - name: – Add an ellipse (circle) to the group
    text: An ellipse is added the same way as the rectangle, but with `ShapeType.Ellipse`.
      The `Left = 210` moves it to the right of the rectangle, creating a visually
      distinct pair of shapes inside the same group.
  - name: – Insert the completed group shape into the document
    text: '`builder.InsertNode(groupShape)` places the whole group at the current
      cursor location. Because the group already contains its children, you do not
      need additional insert calls for the rectangle or ellipse.'
  - name: – Create a plain‑text StructuredDocumentTag (SDT)
    text: A StructuredDocumentTag is a content control that end users can fill in
      when the document is opened in Word. Setting `Title = "CustomerName"` gives
      the control a meaningful identifier, which is useful for later data extraction.
  - name: – Save the document
    text: '`doc.Save("GroupAndSDT.docx")` writes the file to disk. The resulting DOCX
      contains the grouped shapes and the SDT. Opening the file in Microsoft Word
      will show a rectangle next to a circle, both selectable as a single object,
      followed by a placeholder “Enter name here …”.'
  - name: Using different shape types
    text: You can replace `ShapeType.Rectangle` or `ShapeType.Ellipse` with any other
      `ShapeType` (e.g., `ShapeType.Polygon`, `ShapeType.Line`). The grouping logic
      remains identical.
  - name: Setting fill color and borders
    text: '```csharp rectangleShape.FillColor = System.Drawing.Color.LightBlue; rectangleShape.StrokeColor
      = System.Drawing.Color.DarkBlue; ellipseShape.FillColor = System.Drawing.Color.LightCoral;
      ``` Adding fill and stroke improves visual distinction, especially when the
      document is shared with non‑technical'
  - name: Rotating the entire group
    text: '```csharp groupShape.Rotation = 45; // rotates both shapes together ```
      Rotating the group is more efficient than rotating each child individually.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Créer un document Word par programmation et regrouper les formes en C#
url: /fr/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un document Word programmatique et regrouper des formes en C#

Si vous devez **créer un document Word programmatique**, ce tutoriel vous montre comment construire un fichier DOCX avec Aspose.Words et **regrouper plusieurs formes Word** ensemble. Nous aborderons également **ajouter un rectangle à Word** et **comment créer une forme groupée** contenant à la fois un rectangle et une ellipse, plus un StructuredDocumentTag en texte brut pour la saisie utilisateur.

Vous terminerez avec un fichier Word prêt à l’emploi contenant une forme groupée rectangle‑ellipse et un contrôle de contenu où l’utilisateur peut saisir un nom. Aucun éditage manuel dans Word n’est requis après l’exécution du code.

## Ce dont vous aurez besoin

- .NET 6.0 ou version ultérieure (l’exemple cible .NET 6, mais toute version récente de .NET fonctionne)
- Une licence Aspose.Words for .NET (l’essai gratuit suffit pour les tests)
- Visual Studio 2022 ou tout IDE C# de votre choix
- Une connaissance de base de la syntaxe C#

## Créer un document Word programmatique – flux de travail global

Le processus se compose de trois phases logiques :

1. **Initialiser** un `Document` et un `DocumentBuilder` – la base de tout fichier Word que vous générez.
2. **Construire une forme groupée** qui contient un rectangle et une ellipse – illustre **regrouper plusieurs formes Word** et **comment créer une forme groupée**.
3. **Insérer un StructuredDocumentTag (SDT)** – un contrôle de contenu en texte brut qui permet aux utilisateurs finaux de remplir des données, illustrant **ajouter un rectangle à Word** dans le cadre de la mise en page globale du document.

Vous trouverez ci‑dessous le code complet et exécutable suivi d’une explication étape par étape.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1 – Initialize the document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2 – Create a group shape container
            Shape groupShape = new Shape(doc, ShapeType.Group)
            {
                Width = 400,
                Height = 200
            };

            // Step 3 – Add a rectangle to the group
            Shape rectangleShape = new Shape(doc, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100,
                Left = 0,
                Top = 0
            };
            groupShape.GroupShape.AddChild(rectangleShape);

            // Step 4 – Add an ellipse (circle) to the group
            Shape ellipseShape = new Shape(doc, ShapeType.Ellipse)
            {
                Width = 100,
                Height = 100,
                Left = 210, // Position next to the rectangle
                Top = 0
            };
            groupShape.GroupShape.AddChild(ellipseShape);

            // Step 5 – Insert the completed group shape into the document
            builder.InsertNode(groupShape);

            // Step 6 – Create a plain‑text StructuredDocumentTag for user input
            StructuredDocumentTag sdtTag = new StructuredDocumentTag(
                doc,
                SdtType.PlainText,
                MarkupLevel.Block)
            {
                Title = "CustomerName"
            };
            builder.InsertNode(sdtTag);
            builder.Writeln("Enter name here …");

            // Step 7 – Save the document
            doc.Save("GroupAndSDT.docx");
            Console.WriteLine("Document created successfully.");
        }
    }
}
```

### Étape 1 – Initialiser le document et le builder
L’objet `Document` représente l’ensemble du fichier DOCX, tandis que `DocumentBuilder` fournit une API pratique pour ajouter du contenu. Les initialiser constitue la première exigence chaque fois que vous **créez un document Word programmatique**.

> **Astuce :** Si vous prévoyez de réutiliser le même document dans plusieurs opérations, conservez une seule instance de `DocumentBuilder` afin d’éviter la création d’objets superflus.

### Étape 2 – Créer un conteneur de forme groupée
Une `Shape` avec `ShapeType.Group` agit comme une toile pouvant contenir d’autres formes. Le réglage de `Width` et `Height` définit la boîte englobante du groupe. C’est le cœur de **comment créer une forme groupée** dans Aspose.Words.

> **Cas limite :** Si la largeur du groupe est inférieure à la largeur combinée de ses enfants, ceux‑ci seront rognés. Assurez‑vous que le groupe soit suffisamment grand pour contenir chaque forme enfant.

### Étape 3 – Ajouter un rectangle à Word
Un rectangle est créé avec `ShapeType.Rectangle`. Ses propriétés `Left` et `Top` le positionnent par rapport à l’origine du groupe. Cette étape montre **ajouter un rectangle à Word** et explique comment contrôler le placement exact.

> **Erreur courante :** Oublier de définir `Left`/`Top` entraîne l’affichage du rectangle à l’origine par défaut du groupe (0,0), ce qui peut chevaucher d’autres enfants.

### Étape 4 – Ajouter une ellipse (cercle) au groupe
Une ellipse est ajoutée de la même façon que le rectangle, mais avec `ShapeType.Ellipse`. Le `Left = 210` la décale à droite du rectangle, créant une paire de formes visuellement distincte au sein du même groupe.

> **Pourquoi utiliser un groupe ?** Le groupement vous permet de déplacer, faire pivoter ou redimensionner les deux formes ensemble avec une seule opération ultérieure, tout en conservant leur disposition relative.

### Étape 5 – Insérer la forme groupée terminée dans le document
`builder.InsertNode(groupShape)` place l’ensemble du groupe à l’emplacement actuel du curseur. Comme le groupe contient déjà ses enfants, aucun appel d’insertion supplémentaire n’est nécessaire pour le rectangle ou l’ellipse.

### Étape 6 – Créer un StructuredDocumentTag (SDT) en texte brut
Un StructuredDocumentTag est un contrôle de contenu que les utilisateurs finaux peuvent remplir lorsque le document est ouvert dans Word. Définir `Title = "CustomerName"` donne au contrôle un identifiant significatif, utile pour l’extraction de données ultérieure.

> **Pourquoi un SDT en texte brut ?** Il restreint la saisie au texte simple, évitant les formats accidentels qui pourraient perturber le traitement en aval.

### Étape 7 – Enregistrer le document
`doc.Save("GroupAndSDT.docx")` écrit le fichier sur le disque. Le DOCX résultant contient les formes groupées et le SDT. L’ouverture du fichier dans Microsoft Word affichera un rectangle à côté d’un cercle, tous deux sélectionnables comme un seul objet, suivi d’un espace réservé « Enter name here … ».

#### Résultat attendu
- Un fichier nommé **GroupAndSDT.docx** dans le répertoire d’exécution.
- Dans Word : une forme groupée (rectangle + ellipse) que vous pouvez déplacer comme une unité.
- Directement sous le groupe, un contrôle de contenu grisâtre invitant l’utilisateur à saisir un nom.

## Variantes supplémentaires et bonnes pratiques

### Utiliser différents types de forme
Vous pouvez remplacer `ShapeType.Rectangle` ou `ShapeType.Ellipse` par tout autre `ShapeType` (par ex., `ShapeType.Polygon`, `ShapeType.Line`). La logique de groupement reste identique.

### Définir la couleur de remplissage et les bordures
```csharp
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```
Ajouter un remplissage et un contour améliore la distinction visuelle, surtout lorsque le document est partagé avec des parties prenantes non techniques.

### Faire pivoter l’ensemble du groupe
```csharp
groupShape.Rotation = 45; // rotates both shapes together
```
Faire pivoter le groupe est plus efficace que de faire pivoter chaque enfant individuellement.

### Exporter en PDF
Si vous avez besoin d’une version PDF, il suffit d’appeler :
```csharp
doc.Save("GroupAndSDT.pdf", SaveFormat.Pdf);
```
Toutes les formes groupées et le SDT (rendu comme un champ texte) apparaîtront dans le PDF.

## Pièges courants et comment les éviter

| Symptôme | Cause | Correction |
|----------|-------|------------|
|          |       |            |

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Créer une forme groupée dans un document Word avec Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Créer une forme rectangle dans Word avec C# – Guide étape par étape](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Créer un document Word vierge avec une forme rectangle ombrée – Guide étape par étape](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}