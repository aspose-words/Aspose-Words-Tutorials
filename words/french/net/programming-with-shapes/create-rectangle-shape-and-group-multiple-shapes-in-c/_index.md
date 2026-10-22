---
category: general
date: 2026-09-18
description: Créer une forme rectangulaire dans un document Word à l'aide de C#. Apprenez
  à ajouter plusieurs formes, à les regrouper et à insérer le groupe de formes avec
  Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add multiple shapes
- add shapes to group
- insert group shape
language: fr
lastmod: 2026-09-18
og_description: Créer une forme rectangulaire dans un fichier Word avec C#. Ce guide
  montre comment ajouter plusieurs formes, ajouter des formes à un groupe et insérer
  un groupe de formes à l'aide d'Aspose.Words.
og_image_alt: Grouped rectangle and ellipse shapes displayed in a Word document
og_title: Créer une forme rectangulaire et regrouper les formes en C#
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create rectangle shape in a Word document using C#. Learn how to add
    multiple shapes, add shapes to a group, and insert group shape with Aspose.Words.
  headline: Create rectangle shape and group multiple shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Shape
- GroupShape
title: Créer une forme rectangulaire et regrouper plusieurs formes en C#
url: /fr/net/programming-with-shapes/create-rectangle-shape-and-group-multiple-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer une forme rectangulaire et regrouper plusieurs formes en C#

Si vous devez **créer une forme rectangulaire** dans un document Word, ce tutoriel montre une solution complète. Vous verrez comment **ajouter plusieurs formes**, **ajouter des formes à un groupe** et **insérer une forme de groupe** en utilisant l’API Aspose.Words pour .NET.

Travailler avec des formes est une exigence courante lors de la génération de rapports, de contrats ou de documents marketing de façon programmatique. À la fin de ce guide, vous disposerez d’une application console C# exécutable qui produit un fichier `.docx` contenant un rectangle, une ellipse et un groupe qui regroupe les deux formes.

Les seules exigences préalables sont un SDK .NET récent (6.0 ou ultérieur) et une copie sous licence d’Aspose.Words pour .NET. Aucun outil supplémentaire n’est requis.

## Prérequis

- SDK .NET 6.0 ou plus récent  
- Aspose.Words pour .NET (package NuGet `Aspose.Words`)  
- Familiarité de base avec la syntaxe C#  

Vous pouvez installer le package avec la commande suivante :

```bash
dotnet add package Aspose.Words
```

## Étape 1 : Créer une forme rectangulaire avec Aspose.Words

La première étape consiste à créer un objet `Shape` de type `Rectangle`. Cet objet représente le rectangle visuel qui apparaîtra dans le document.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty document
Document doc = new Document();

// Initialize a DocumentBuilder for editing the document
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape: width = 100 points, height = 50 points
Shape rectangle = new Shape(doc, ShapeType.Rectangle);
rectangle.Width = 100;
rectangle.Height = 50;

// Optional: give the rectangle a fill color and a border
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.StrokeWeight = 1.0;

// Insert the rectangle at the current builder position
builder.InsertNode(rectangle);
```

**Pourquoi c’est important :** `ShapeType.Rectangle` indique à Aspose.Words de rendre un rectangle géométrique. La définition de `Width` et `Height` détermine sa taille en points (1 point = 1/72 pouce). L’ajout de couleurs de remplissage et de contour rend la forme visible sans besoin de style supplémentaire.

## Étape 2 : Ajouter plusieurs formes au document

Après le rectangle, vous pouvez créer un nombre quelconque de formes supplémentaires. Dans cet exemple, nous ajoutons une ellipse pour illustrer le fonctionnement de **ajouter plusieurs formes**.

```csharp
// Create an ellipse shape: width = 80 points, height = 80 points
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width = 80;
ellipse.Height = 80;

// Style the ellipse
ellipse.FillColor = System.Drawing.Color.LightCoral;
ellipse.StrokeColor = System.Drawing.Color.Maroon;
ellipse.StrokeWeight = 1.0;

// Insert the ellipse after the rectangle
builder.InsertNode(ellipse);
```

**Pourquoi c’est important :** Chaque appel à `new Shape` crée un objet de dessin indépendant. En les insérant séquentiellement, vous constituez une collection de formes qui pourra ensuite être groupée ou positionnée individuellement.

## Étape 3 : Ajouter des formes au groupe

Regrouper des formes simplifie la gestion de la mise en page car le groupe se comporte comme un nœud unique. Cette étape montre comment **ajouter des formes au groupe** à l’aide de `GroupShape`.

```csharp
// Create a GroupShape with a bounding box of 200x200 points
GroupShape group = new GroupShape(doc, 200, 200);

// Move the builder's cursor back to the start of the document
builder.MoveToDocumentStart();

// Insert the empty group into the document
builder.InsertNode(group);

// Append the previously created rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

**Pourquoi c’est important :** `GroupShape` agit comme un conteneur. Lorsque vous déplacez, faites pivoter ou redimensionnez le groupe, toutes les formes enfants suivent automatiquement. La boîte englobante (200 × 200 points) définit l’espace de coordonnées pour les formes enfants.

## Étape 4 : Insérer la forme de groupe dans le document

Maintenant que le groupe contient le rectangle et l’ellipse, vous devez **insérer la forme de groupe** à l’emplacement souhaité. Le builder a déjà placé le groupe vide, mais vous pouvez également l’insérer ailleurs si besoin.

```csharp
// Position the group at a specific location (optional)
group.Left = 50;   // 50 points from the left margin
group.Top = 100;   // 100 points from the top margin

// Save the document with the grouped shapes
doc.Save("GroupShapeExample.docx");
```

**Pourquoi c’est important :** Modifier `Left` et `Top` déplace l’ensemble du groupe à l’intérieur de la page. En enregistrant le document, la hiérarchie des formes est écrite dans un fichier `.docx` qui peut être ouvert avec Microsoft Word, LibreOffice ou tout visualiseur compatible.

## Exemple complet exécutable

Voici le programme complet qui combine toutes les étapes. Copiez le code dans un nouveau projet console et exécutez‑le pour générer `GroupShapeExample.docx`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document
            Document doc = new Document();

            // Step 2: Initialize a DocumentBuilder for editing the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle);
            rectangle.Width = 100;
            rectangle.Height = 50;
            rectangle.FillColor = Color.LightBlue;
            rectangle.StrokeColor = Color.DarkBlue;
            rectangle.StrokeWeight = 1.0;

            // Step 4: Create an ellipse shape
            Shape ellipse = new Shape(doc, ShapeType.Ellipse);
            ellipse.Width = 80;
            ellipse.Height = 80;
            ellipse.FillColor = Color.LightCoral;
            ellipse.StrokeColor = Color.Maroon;
            ellipse.StrokeWeight = 1.0;

            // Step 5: Create a GroupShape that will hold both shapes
            GroupShape group = new GroupShape(doc, 200, 200);
            group.Left = 50;   // optional positioning
            group.Top = 100;   // optional positioning

            // Add the rectangle and ellipse to the group
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Insert the group into the document at the current builder position
            builder.InsertNode(group);

            // Step 6: Save the document containing the grouped shapes
            doc.Save("GroupShapeExample.docx");

            Console.WriteLine("Document saved successfully.");
        }
    }
}
```

**Résultat attendu :**  
L’ouverture de `GroupShapeExample.docx` affiche un seul groupe contenant un rectangle bleu‑clair et une ellipse corail‑clair, tous deux positionnés à l’intérieur d’un conteneur de 200 × 200 points. Le groupe peut être sélectionné comme un objet unique dans Word, confirmant que **ajouter des formes au groupe** a réussi.

## Variations courantes et cas limites

| Situation | Ajustement recommandé |
|-----------|------------------------|
| Types de formes différents (par ex., `ShapeType.Line`) | Créez la forme avec le `ShapeType` souhaité et définissez sa géométrie en conséquence. |
| Besoin de faire pivoter une forme | Utilisez `shape.Rotation = 45;` (degrés) avant de l’ajouter au groupe. |
| Documents volumineux avec de nombreux groupes | Réutilisez une seule instance de `DocumentBuilder` ; évitez de créer un nouveau builder pour chaque groupe afin de réduire la consommation mémoire. |
| Enregistrement au format PDF au lieu de DOCX | Appelez `doc.Save("output.pdf", SaveFormat.Pdf);` après l’insertion du groupe. |

**Astuce :** Définissez toujours des valeurs explicites pour `Left` et `Top` du groupe lorsque vous avez besoin d’un placement précis. Si vous les omettez, le groupe hérite de la position actuelle du curseur du builder, ce qui peut entraîner des résultats de mise en page inattendus.

## Conclusion

Vous savez maintenant comment **créer une forme rectangulaire**, **ajouter plusieurs formes**, **ajouter des formes à un groupe** et **insérer une forme de groupe** dans un document Word en utilisant C#. L’exemple complet illustre le flux de travail complet, de la création du document à l’enregistrement du fichier final.  

Ensuite, explorez des sujets connexes tels que **positionner les formes par rapport au texte**, **appliquer le texte d’habillage**, et **exporter les formes groupées en PDF**. Ces extensions vous permettent de créer des mises en page de documents sophistiquées et programmatiques avec Aspose.Words.

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques présentées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Créer une forme rectangulaire dans Word avec C# – Guide étape par étape](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Créer une forme de groupe dans un document Word en utilisant Aspose.Words pour .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Créer un document Word vierge avec une forme rectangulaire ombrée – Guide étape par étape](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}