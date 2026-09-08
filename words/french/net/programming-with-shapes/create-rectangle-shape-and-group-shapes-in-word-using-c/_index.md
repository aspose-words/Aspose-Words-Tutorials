---
category: general
date: 2026-09-08
description: Créer une forme rectangulaire dans un document Word avec C#. Apprenez
  à définir la taille de la forme, à regrouper plusieurs formes et à créer un document
  Word vierge de façon programmatique.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- set shape size
- group multiple shapes
- create blank word document
language: fr
lastmod: 2026-09-08
og_description: Créer une forme rectangulaire dans un document Word avec C#. Ce guide
  montre comment définir la taille de la forme, regrouper plusieurs formes et créer
  un document Word vierge de manière programmatique.
og_image_alt: Screenshot showing how to create rectangle shape in a Word document
  using C#
og_title: Créer une forme rectangulaire et regrouper des formes dans Word avec C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Create rectangle shape in a Word document with C#. Learn to set shape
    size, group multiple shapes, and create blank Word document programmatically.
  headline: Create rectangle shape and group shapes in Word using C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Créer une forme rectangulaire et regrouper des formes dans Word en C#
url: /fr/net/programming-with-shapes/create-rectangle-shape-and-group-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer une forme rectangulaire et regrouper des formes dans Word avec C#

Si vous devez **create rectangle shape** dans un fichier Word, ce tutoriel vous fournit une solution complète, prête à l'exécution. Vous verrez comment définir la taille de la forme, regrouper plusieurs formes et créer un document Word vierge à partir de zéro — le tout avec la bibliothèque Aspose.Words for .NET.

Travailler avec des documents Word de manière programmatique ressemble souvent à jongler avec de nombreux petits détails. À la fin de ce guide, vous disposerez d’une méthode unique qui génère un fichier `.docx` contenant un rectangle et une ellipse regroupés, prêts pour des modifications ou impressions ultérieures.

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

* .NET 6.0 ou supérieur (le code fonctionne également avec .NET Framework 4.6+)
* Une copie sous licence de **Aspose.Words for .NET** (vous pouvez utiliser une clé d’évaluation gratuite)
* Un IDE tel que Visual Studio 2022 ou Visual Studio Code
* Une connaissance de base de la syntaxe C#

Aucun package NuGet supplémentaire n’est requis au‑delà de `Aspose.Words`.

## Étape 1 : Créer un document Word vierge

La première étape consiste à créer un document vide qui accueillera les formes. Cela satisfait le besoin *create blank word document*.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty Word document
Document doc = new Document();

// The document already contains one section and one empty paragraph
// You can add additional sections later if needed
```

Créer un document vierge vous donne une toile propre. L’objet `Document` représente l’ensemble du fichier `.docx`, et son `FirstSection.Body.FirstParagraph` constitue le point d’insertion par défaut pour les nouveaux nœuds.

## Étape 2 : Créer une forme rectangulaire

Vous pouvez maintenant ajouter le rectangle. C’est ici que l’opération **create rectangle shape** a lieu.

```csharp
// Initialize a DocumentBuilder to simplify node insertion
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape instance
Shape rectangle = new Shape(doc, ShapeType.Rectangle);

// Set the rectangle's size (width and height) and position
rectangle.Width  = 100;   // points; 1 point = 1/72 inch
rectangle.Height = 50;
rectangle.Left   = 10;    // distance from the left edge of the container
rectangle.Top    = 20;    // distance from the top edge of the container

// Optional: give the rectangle a visible border
rectangle.StrokeColor = Color.Blue;
rectangle.FillColor   = Color.LightGray;
```

Définir les dimensions directement répond au mot‑clé **set shape size**. Toutes les valeurs de taille sont exprimées en points, ce qui offre un contrôle précis sur l’apparence de la forme dans le document final.

## Étape 3 : Créer une forme supplémentaire (ellipse)

Un cas d’utilisation typique consiste à combiner plusieurs formes. Ici, nous ajoutons une ellipse qui partagera plus tard le même conteneur.

```csharp
// Create an ellipse shape instance
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width  = 80;
ellipse.Height = 80;
ellipse.Left   = 120;   // Position it to the right of the rectangle
ellipse.Top    = 30;

// Give the ellipse a distinct border and fill
ellipse.StrokeColor = Color.DarkGreen;
ellipse.FillColor   = Color.LightYellow;
```

Les deux formes restent indépendantes à ce stade. L’étape suivante montre comment **group multiple shapes** ensemble.

## Étape 4 : Regrouper les formes dans Word

Regrouper les formes vous permet de les déplacer, redimensionner ou formater comme une seule unité. Cela satisfait les exigences **group shapes in word** et **group multiple shapes**.

```csharp
// Create a GroupShape container that will hold the rectangle and ellipse
GroupShape group = new GroupShape(doc);

// Define the container's bounding box – it must be large enough for all children
group.Bounds = new RectangleF(0, 0, 300, 200);

// Append the group to the document's first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(group);

// Add the rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

La propriété `GroupShape.Bounds` détermine le système de coordonnées pour les formes enfants. En plaçant le rectangle et l’ellipse dans le même `GroupShape`, vous pourrez les déplacer ou les faire pivoter ensemble avec un seul appel.

## Étape 5 : Enregistrer le document

Enfin, écrivez le document sur le disque. Le fichier contiendra les formes groupées que vous venez de créer.

```csharp
// Choose an output path – ensure the directory exists and you have write permission
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");

// Save the document in DOCX format
doc.Save(outputPath);
```

Après l’exécution du programme, ouvrez `GroupedShapes.docx` dans Microsoft Word. Vous devriez voir un rectangle et une ellipse regroupés ; sélectionner une forme sélectionne également l’autre, confirmant que le regroupement a réussi.

## Code source complet

Copiez le programme complet suivant dans un nouveau projet console‑app et exécutez‑le. Aucun code supplémentaire n’est requis.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System;
using System.Drawing;
using System.IO;

class Program
{
    static void Main()
    {
        // Step 1: create a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: create rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width  = 100,
            Height = 50,
            Left   = 10,
            Top    = 20,
            StrokeColor = Color.Blue,
            FillColor   = Color.LightGray
        };

        // Step 3: create ellipse shape
        Shape ellipse = new Shape(doc, ShapeType.Ellipse)
        {
            Width  = 80,
            Height = 80,
            Left   = 120,
            Top    = 30,
            StrokeColor = Color.DarkGreen,
            FillColor   = Color.LightYellow
        };

        // Step 4: group the shapes
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new RectangleF(0, 0, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);
        group.AppendChild(rectangle);
        group.AppendChild(ellipse);

        // Step 5: save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### Résultat attendu

L’exécution du programme produit `GroupedShapes.docx`. L’ouverture du fichier dans Word montre :

* Un **rectangle** (100 pt × 50 pt) avec une bordure bleue et un remplissage gris clair.
* Une **ellipse** (80 pt × 80 pt) avec une bordure vert foncé et un remplissage jaune clair.
* Les deux formes sont à l’intérieur d’un même groupe, de sorte que déplacer l’une déplace l’autre.

## Questions fréquentes et cas particuliers

| Question | Réponse |
|----------|--------|
| **Puis‑je ajouter plus de deux formes au groupe ?** | Oui. Créez des objets `Shape` supplémentaires et appelez `group.AppendChild(votreForme)` pour chacun. |
| **Que faire si je dois faire pivoter le groupe ?** | Définissez `group.RotationAngle = 45;` (degrés). Toutes les formes enfants pivoteront ensemble. |
| **Est‑il possible de regrouper les formes après l’enregistrement du document ?** | Vous devez modifier la structure du document avant l’enregistrement ; sinon il vous faudrait charger le fichier, localiser les formes et recréer le groupe. |
| **Dois‑je libérer certains objets ?** | Aspose.Words gère ses propres ressources, mais vous devez libérer les objets `FileStream` si vous ouvrez des flux manuellement. |
| **Le code fonctionnera‑t‑il avec le format .doc (binaire) ?** | Oui, changez `doc.Save("output.doc")`. Le comportement de regroupement est identique. |

## Conclusion

Vous savez maintenant comment **create rectangle shape**, **set shape size** et **group multiple shapes** à l’intérieur d’un fichier Word en utilisant C#. Cette approche vous permet de créer programmétiquement des diagrammes complexes, des filigranes ou des rapports basés sur des modèles sans édition manuelle.

### Prochaines étapes

* Explorez davantage **group shapes in word** en ajoutant des zones de texte ou des images au même groupe.
* Utilisez le modèle `SetShapeSize` pour calculer dynamiquement les dimensions en fonction de la mise en page.
* Combinez cette technique avec des champs de publipostage pour générer des documents personnalisés à grande échelle.

N’hésitez pas à expérimenter avec différents types de formes, couleurs et transformations de groupe. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create Word Document with a Shadowed Rectangle – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}