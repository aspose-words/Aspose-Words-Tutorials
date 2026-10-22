---
category: general
date: 2026-10-07
description: Créer un document Word vierge en C# et apprendre à ajouter une forme
  rectangle, insérer une forme image et regrouper plusieurs formes pour des rapports
  dynamiques.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- insert image shape
- group multiple shapes
- add image to word
language: fr
lastmod: 2026-10-07
og_description: Créer un document Word vierge en C# avec Aspose.Words. Apprenez à
  ajouter une forme rectangulaire, insérer une forme image et regrouper plusieurs
  formes pour des documents professionnels.
og_image_alt: Screenshot of a Word file showing a grouped rectangle and logo created
  with C#
og_title: Créer un document Word vierge et regrouper des formes en C# – guide étape
  par étape
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create blank Word document in C# and learn to add rectangle shape,
    insert image shape, and group multiple shapes for dynamic reports.
  headline: How to create blank Word document and group shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Comment créer un document Word vierge et regrouper des formes en C#
url: /fr/net/programming-with-shapes/how-to-create-blank-word-document-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer un document Word vierge et regrouper des formes en C#

Si vous devez **create blank Word document** programmatically, ce guide vous montre exactement comment faire. Vous verrez comment **add rectangle shape**, **insert image shape**, et **group multiple shapes** afin qu'elles se comportent comme un seul objet lorsque vous **add image to Word** plus tard.

Travailler avec des fichiers Word depuis le code peut sembler intimidant, mais Aspose.Words rend le processus simple. À la fin de ce tutoriel, vous disposerez d’un extrait C# réutilisable qui génère un fichier Word propre et vide contenant un rectangle groupé et un logo. Vous pouvez intégrer le résultat dans des factures, des rapports ou tout flux de travail de documents automatisé.

## Prérequis

* .NET 6.0 ou ultérieur (le code fonctionne également avec .NET Framework 4.7+).  
* Une licence valide Aspose.Words for .NET ou une clé d’évaluation gratuite.  
* Un fichier image (par ex., `logo.png`) placé dans un dossier que vous pouvez référencer depuis le code.  
* Visual Studio 2022 ou tout IDE compatible C#.

Aucun package NuGet supplémentaire n’est requis au-delà de `Aspose.Words`.

## Comment créer un document Word vierge avec Aspose.Words

La première étape consiste toujours à **create blank Word document**. Cet objet hébergera toutes les formes suivantes.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// 1️⃣ Initialize a new empty document.
Document doc = new Document();

// 2️⃣ Prepare a DocumentBuilder – it simplifies adding content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` représente le fichier `.docx` complet. À ce stade, le fichier est vide, ce qui satisfait le besoin de *create blank Word document*.

## Créer un conteneur pour regrouper plusieurs formes

Regrouper des formes vous permet de les déplacer, faire pivoter ou redimensionner ensemble. Aspose.Words fournit la classe `GroupShape` à cet effet.

```csharp
// 3️⃣ Create a GroupShape that will hold our drawing objects.
GroupShape group = new GroupShape(doc)
{
    // Define the container’s position and size on the page.
    Bounds = new Rectangle(50, 50, 300, 200)
};

// Append the group to the first paragraph of the first section.
doc.FirstSection.Body.FirstParagraph.AppendChild(group);
```

Le rectangle `Bounds` détermine où le groupe apparaît sur la page. En plaçant le groupe dans le premier paragraphe, vous garantissez que le **create blank Word document** contiendra immédiatement un conteneur visuel.

## Comment ajouter une forme rectangle à l’intérieur du groupe

Une exigence courante est de **add rectangle shape** comme arrière-plan ou bordure. Le code suivant crée un rectangle et l’ajoute au groupe précédemment défini.

```csharp
// 4️⃣ Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width = 100,
    Height = 80,
    Left = 20,
    Top = 20,
    // Optional: give the rectangle a light gray fill.
    FillColor = Color.LightGray
};

// Add the rectangle to the group.
group.AppendChild(rectangle);
```

Comme le rectangle vit à l’intérieur du `GroupShape`, il se déplacera avec toutes les autres formes que vous ajouterez plus tard. C’est le cœur de la fonctionnalité **group multiple shapes**.

## Comment insérer une forme image à l’intérieur du groupe

Ensuite, vous allez **insert image shape** (le logo) et le placer à côté du rectangle. Cela illustre le flux de travail **add image to Word**.

```csharp
// 5️⃣ Create an image shape.
Shape picture = new Shape(doc, ShapeType.Image)
{
    Width = 80,
    Height = 80,
    Left = 150,
    Top = 30
};

// Load the image from disk. Replace the path with your actual image location.
picture.ImageData.SetImage(Image.FromFile(@"YOUR_DIRECTORY/logo.png"));

// Add the image shape to the same group.
group.AppendChild(picture);
```

La méthode `SetImage` lit le fichier et l’intègre directement dans le document Word, garantissant que l’image persiste même si le fichier source est déplacé. Cela complète l’étape **insert image shape** et finalise le besoin **add image to Word**.

## Enregistrer le document

Enfin, persistez le fichier sur le disque. Le fichier enregistré contient le document vierge, le rectangle groupé et le logo intégré.

```csharp
// 6️⃣ Save the document with the grouped shapes.
doc.Save(@"YOUR_DIRECTORY/GroupShape.docx");
```

Lorsque vous ouvrez `GroupShape.docx` dans Microsoft Word, vous verrez un seul groupe qui comprend un rectangle gris clair et le logo positionné côte à côte. Sélectionner n’importe quelle partie du groupe vous permet de déplacer ou redimensionner l’ensemble de la collection, prouvant que les formes sont bien **group multiple shapes**.

## Exemple complet et exécutable

Voici le programme complet que vous pouvez copier, coller et exécuter. Remplacez `YOUR_DIRECTORY` par un chemin absolu ou relatif qui existe sur votre machine.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank Word document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Create a GroupShape to hold the rectangle and image.
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new Rectangle(50, 50, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);

        // Step 3: Add a rectangle shape inside the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 100,
            Height = 80,
            Left = 20,
            Top = 20,
            FillColor = Color.LightGray
        };
        group.AppendChild(rectangle);

        // Step 4: Insert an image shape inside the group.
        Shape picture = new Shape(doc, ShapeType.Image)
        {
            Width = 80,
            Height = 80,
            Left = 150,
            Top = 30
        };
        picture.ImageData.SetImage(Image.FromFile(@"YOUR_DIRECTORY/logo.png"));
        group.AppendChild(picture);

        // Step 5: Save the document.
        doc.Save(@"YOUR_DIRECTORY/GroupShape.docx");
    }
}
```

### Résultat attendu

* Un fichier nommé `GroupShape.docx` situé dans `YOUR_DIRECTORY`.  
* L’ouverture du fichier dans Word affiche un seul groupe visuel contenant un rectangle gris à gauche et le `logo.png` à droite.  
* Sélectionner n’importe quelle partie du groupe visuel vous permet de déplacer ou redimensionner l’ensemble de la collection, confirmant que les formes sont correctement **group multiple shapes**.

## Questions fréquentes et gestion des cas limites

| Question | Réponse |
|---|---|
| **Puis-je ajouter plus de deux formes au même groupe ?** | Oui. Appelez `group.AppendChild(yourShape)` pour chaque `Shape` supplémentaire. Le groupe peut contenir un nombre quelconque d’objets de dessin. |
| **Que se passe-t-il si le fichier image est manquant ?** | `SetImage` lèvera une `FileNotFoundException`. Enveloppez l’appel dans un bloc try‑catch et fournissez une solution de secours (par ex., une forme de substitution). |
| **Do I need to set `WrapType` for the shapes?** | Par défaut, les formes sont en ligne. Si vous avez besoin d’un comportement flottant, définissez `picture.WrapType = WrapType.Inline;` ou un autre mode d’enveloppe avant d’ajouter au groupe. |
| **Comment la taille du document affecte-t-elle les limites du groupe ?** | Le rectangle `Bounds` est défini en points (1 pt ≈ 1/72 in). Ajustez la taille si vous placez le groupe sur une mise en page de page différente (par ex., A4 vs. Letter). |
| **Puis-je réutiliser le même groupe dans un autre document ?** | Oui. Clonez le groupe avec `GroupShape cloned = (GroupShape)group.Clone(true);` et insérez‑le dans un autre `Document`. |

## Astuces professionnelles

* **Reuse the `DocumentBuilder`** pour ajouter du texte avant ou après le groupe. Il respecte automatiquement la position actuelle du curseur.  
* **Set `Shape.StrokeColor`** si vous avez besoin d’une bordure visible autour du rectangle.  
* **Use high‑resolution PNGs** pour le logo afin d’éviter la pixellisation lorsque

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Créer une forme de groupe dans un document Word avec Aspose.Words pour .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Créer une forme rectangle dans Word avec C# – Guide étape par étape](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Insérer une image en ligne dans un document Word avec Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}