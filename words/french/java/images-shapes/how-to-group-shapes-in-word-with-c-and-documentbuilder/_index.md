---
category: general
date: 2026-10-04
description: Apprenez à regrouper des formes dans Word avec C#. Ce guide montre comment
  insérer une forme rectangle, regrouper plusieurs formes et créer un fichier Word
  vierge par programmation.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- insert rectangle shape
- group multiple shapes
- append child to group
- create blank word file
language: fr
lastmod: 2026-10-04
og_description: Regroupez des formes dans Word avec C#. Suivez ce guide étape par
  étape pour insérer une forme rectangle, regrouper plusieurs formes et créer un fichier
  Word vierge avec DocumentBuilder.
og_image_alt: Screenshot of grouped rectangle and ellipse shapes inside a Word document
og_title: Regrouper des formes dans Word avec C# – tutoriel complet sur DocumentBuilder
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to group shapes in Word using C#. This guide shows how to
    insert rectangle shape, group multiple shapes, and create a blank Word file programmatically.
  headline: How to group shapes in Word with C# and DocumentBuilder
  type: TechArticle
- description: Learn how to group shapes in Word using C#. This guide shows how to
    insert rectangle shape, group multiple shapes, and create a blank Word file programmatically.
  name: How to group shapes in Word with C# and DocumentBuilder
  steps:
  - name: '**Create a blank Word file** – Starting with a clean document guarantees
      that no hidden formatting interferes with shape positioning.'
    text: '**Create a blank Word file** – Starting with a clean document guarantees
      that no hidden formatting interferes with shape positioning.'
  - name: '**Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level
      node manipulation, letting you focus on layout.'
    text: '**Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level
      node manipulation, letting you focus on layout.'
  - name: '**Insert individual shapes** – You first need separate objects (`insert
      rectangle shape` and an ellipse) before you can group them. Adjusting `Left`
      and `Top` ensures they appear side‑by‑side.'
    text: '**Insert individual shapes** – You first need separate objects (`insert
      rectangle shape` and an ellipse) before you can group them. Adjusting `Left`
      and `Top` ensures they appear side‑by‑side.'
  - name: '**Group multiple shapes** – By creating a `GroupShape` and using **append
      child to group**, you turn two independent drawings into a single logical unit.
      Moving or resizing the group will affect both children simultaneously.'
    text: '**Group multiple shapes** – By creating a `GroupShape` and using **append
      child to group**, you turn two independent drawings into a single logical unit.
      Moving or resizing the group will affect both children simultaneously.'
  - name: '**Save the document** – The final file, `GroupedShapes.docx`, can be opened
      in Microsoft Word to verify that the rectangle and ellipse are indeed grouped
      (select one, and both move together).'
    text: '**Save the document** – The final file, `GroupedShapes.docx`, can be opened
      in Microsoft Word to verify that the rectangle and ellipse are indeed grouped
      (select one, and both move together).'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shape handling
- DocumentBuilder
title: Comment regrouper des formes dans Word avec C# et DocumentBuilder
url: /fr/java/images-shapes/how-to-group-shapes-in-word-with-c-and-documentbuilder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment regrouper des formes dans Word avec C# et DocumentBuilder

Si vous devez **regrouper des formes dans Word** depuis une application C#, ce tutoriel vous montre exactement comment le faire. Vous verrez comment *insérer une forme rectangle*, combiner plusieurs dessins en un seul groupe, et enfin **créer un fichier Word vierge** contenant les objets groupés.

Travailler avec des formes est une exigence courante lors de la génération de rapports, factures ou modèles personnalisés de façon programmatique. À la fin de ce guide, vous disposerez d’un extrait de code réutilisable que vous pourrez intégrer dans n’importe quel projet .NET faisant référence à Aspose.Words.

## Ce que vous apprendrez

- Créer un document Word vierge à partir de zéro.  
- Insérer une forme rectangle et une ellipse à l’aide de `DocumentBuilder`.  
- **Regrouper plusieurs formes** dans un `GroupShape`.  
- Utiliser **append child to group** pour construire la hiérarchie.  
- Enregistrer le fichier sur le disque et vérifier le résultat.

Aucune expérience préalable avec Aspose.Words n’est requise, mais vous devez avoir une compréhension de base du développement C# et .NET.

## Prérequis

| Exigence | Raison |
|----------|--------|
| .NET 6.0 ou version ultérieure | Fournit le runtime pour le code C#. |
| Aspose.Words for .NET (latest version) | Fournit les classes `Document`, `DocumentBuilder` et les formes. |
| Un IDE tel que Visual Studio 2022 (ou VS Code) | Facilite la compilation et l’exécution de l’exemple. |
| Permission d’écriture sur un dossier de votre machine | Nécessaire pour l’appel `doc.save`. |

Installez Aspose.Words via NuGet :

```bash
dotnet add package Aspose.Words
```

---

## Regrouper des formes dans Word – guide étape par étape

Voici le programme complet et exécutable. Chaque section est expliquée en détail afin que vous compreniez **pourquoi** le code est écrit ainsi, et pas seulement **ce que** fait le code.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

namespace WordShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // -------------------------------------------------
            // Step 1: create a blank Word file
            // -------------------------------------------------
            // The Document constructor creates an empty .docx container.
            Document doc = new Document();

            // -------------------------------------------------
            // Step 2: initialize DocumentBuilder to add content
            // -------------------------------------------------
            // DocumentBuilder is the high‑level API for inserting text,
            // images, tables, and shapes into the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // -------------------------------------------------
            // Step 3: insert individual shapes
            // -------------------------------------------------
            // Insert a rectangle shape – this demonstrates the
            // "insert rectangle shape" keyword in practice.
            Shape rectangle = builder.InsertShape(
                ShapeType.Rectangle,   // shape type
                100,                  // width in points
                50);                  // height in points

            // Position the rectangle a little away from the left margin.
            rectangle.Left = 100;   // points from the left edge
            rectangle.Top = 100;    // points from the top of the page

            // Insert an ellipse shape to accompany the rectangle.
            Shape ellipse = builder.InsertShape(
                ShapeType.Ellipse,
                80,
                80);
            ellipse.Left = rectangle.Left + rectangle.Width + 20; // place right of rectangle
            ellipse.Top = rectangle.Top; // align tops

            // -------------------------------------------------
            // Step 4: create a GroupShape and append children
            // -------------------------------------------------
            // A GroupShape acts like a container; any shape added to it
            // moves together with the group. This fulfills the
            // "group multiple shapes" requirement.
            GroupShape group = builder.InsertGroupShape();

            // The "append child to group" operation builds the hierarchy.
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Optional: give the group a name for later reference.
            group.Name = "MyShapeGroup";

            // -------------------------------------------------
            // Step 5: save the document containing the grouped shapes
            // -------------------------------------------------
            string outputPath = @"GroupedShapes.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Pourquoi chaque étape est importante

1. **Créer un fichier Word vierge** – Commencer avec un document vierge garantit qu’aucun formatage caché n’interfère avec le positionnement des formes.  
2. **Initialiser DocumentBuilder** – `DocumentBuilder` abstrait la manipulation de nœuds de bas niveau, vous permettant de vous concentrer sur la mise en page.  
3. **Insérer des formes individuelles** – Vous avez d’abord besoin d’objets séparés (`insert rectangle shape` et une ellipse) avant de pouvoir les regrouper. Ajuster `Left` et `Top` garantit qu’ils apparaissent côte à côte.  
4. **Regrouper plusieurs formes** – En créant un `GroupShape` et en utilisant **append child to group**, vous transformez deux dessins indépendants en une unité logique unique. Déplacer ou redimensionner le groupe affectera les deux enfants simultanément.  
5. **Enregistrer le document** – Le fichier final, `GroupedShapes.docx`, peut être ouvert dans Microsoft Word pour vérifier que le rectangle et l’ellipse sont bien groupés (sélectionnez-en un, et les deux se déplacent ensemble).

### Résultat attendu

Ouvrez `GroupedShapes.docx` dans Microsoft Word :

- Vous verrez un rectangle et une ellipse placés côte à côte.  
- Sélectionner l’une ou l’autre forme met en surbrillance les deux, confirmant qu’elles appartiennent au même groupe.  
- Le groupe peut être déplacé, redimensionné ou formaté comme un seul objet.

![Diagram of grouped rectangle and ellipse inside a Word document](https://example.com/grouped-shapes.png){: .center-image alt="Diagramme du rectangle groupé et de l’ellipse dans un document Word"}

*La capture d’écran illustre les formes groupées finales.*

---

## Insérer une forme rectangle – personnalisation de la taille et du style

Si vous avez besoin d’un rectangle avec une couleur de remplissage ou une bordure spécifiques, modifiez l’objet `Shape` après l’insertion :

```csharp
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.LineWidth = 2.0; // points
```

Ces propriétés font partie de la classe `Shape`, et elles fonctionnent pour tout type de forme, pas seulement les rectangles. Ajuster le style avant d’**append child to group** garantit que le groupe hérite des propriétés visuelles que vous avez définies.

---

## Regrouper plusieurs formes – gérer plus de deux objets

L’exemple regroupe un rectangle et une ellipse, mais vous pouvez ajouter n’importe quel nombre de formes :

```csharp
// Create additional shapes as needed
Shape triangle = builder.InsertShape(ShapeType.Triangle, 60, 60);
triangle.Left = ellipse.Left + ellipse.Width + 20;
triangle.Top = ellipse.Top;

// Append the new shape to the existing group
group.AppendChild(triangle);
```

**Astuce :** Après avoir construit un groupe complexe, vous pouvez verrouiller sa mise en page pour éviter les modifications accidentelles :

```csharp
group.LockAspectRatio = true;
group.RelativeHorizontalPosition = RelativeHorizontalPosition.Margin;
group.RelativeVerticalPosition = RelativeVerticalPosition.Margin;
```

---

## Append child to group – l’ordre est important

L’ordre dans lequel vous appelez `AppendChild` définit l’ordre Z (quelle forme apparaît au-dessus). Dans l’exemple, le rectangle est ajouté en premier, puis l’ellipse, de sorte que l’ellipse recouvre le rectangle s’ils se croisent. Ré‑ordonner est aussi simple que d’appeler `RemoveChild` puis de ré‑ajouter :

```csharp
group.RemoveChild(ellipse);
group.AppendChild(ellipse); // now ellipse is on top
```

---

## Créer un fichier Word vierge – méthode d’assistance réutilisable

Si votre application a fréquemment besoin d’un nouveau document, encapsulez la logique de création :

```csharp
/// <summary>
/// Returns a new empty Document with a single section.
/// </summary>
static Document CreateBlankWordFile()
{
    Document emptyDoc = new Document();
    // Optionally set default page size, margins, etc.
    emptyDoc.FirstSection.PageSetup.PageWidth = 595;  // A4 width in points
    emptyDoc.FirstSection.PageSetup.PageHeight = 842; // A4 height in points
    return emptyDoc;
}
```

Vous pouvez alors remplacer la ligne `new Document()` dans le programme principal par `CreateBlankWordFile()`. Cela illustre le concept de **create blank word file** de manière réutilisable.

---

## Pièges courants et comment les éviter

| Problème | Pourquoi cela se produit | Solution |
|----------|--------------------------|----------|
| Les formes apparaissent hors de la page | Les valeurs par défaut de `Left`/`Top` sont 0, ce qui place la forme à la marge. | Définissez explicitement `Left` et `Top` après l’insertion. |
| Le groupe perd le formatage | Modifier une forme enfant après son ajout à un groupe peut casser la mise en page du groupe. | Appliquez toutes les propriétés visuelles **avant** d’appeler `AppendChild`. |
| Le fichier enregistré est vide | `DocumentBuilder` n’a jamais été utilisé pour ajouter un nœud, ou `doc.Save` a été appelé sur une instance `Document` différente. | Vérifiez que vous enregistrez le même `Document` que vous avez construit. |
| Avertissements de compatibilité dans Word | Utilisation de fonctionnalités de forme plus récentes non prises en charge |  |

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités d’API supplémentaires et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Créer une forme groupée dans un document Word en utilisant Aspose.Words pour .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insérer des formes dans des documents Word en utilisant Aspose.Words pour .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Créer une forme rectangle dans Word avec C# – Guide étape par étape](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}