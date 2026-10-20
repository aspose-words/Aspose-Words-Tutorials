---
category: general
date: 2026-08-07
description: Insérer une forme rectangulaire en C# avec Aspose.Words et apprendre
  à masquer la forme, définir la couleur de remplissage et ajouter une forme rectangulaire
  à un document Word de manière efficace.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- how to insert shape
- how to set fill color
- add rectangle shape
language: fr
lastmod: 2026-08-07
og_description: Insérez une forme rectangulaire dans un document Word avec C#. Apprenez
  à masquer la forme, définir la couleur de remplissage et ajouter une forme rectangulaire
  en utilisant Aspose.Words.
og_image_alt: Screenshot showing a hidden yellow rectangle shape inserted into a Word
  document
og_title: Insérer une forme rectangulaire en C# – tutoriel complet Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  headline: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  name: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  steps:
  - name: What each step does
    text: '| Step | Reason | |------|--------| | **Create a new document** | Provides
      a clean canvas; you can also load an existing .docx by passing a file path to
      `new Document(path)`. | | **Initialize DocumentBuilder** | `DocumentBuilder`
      is the high‑level helper that lets you insert text, tables, and shapes'
  - name: 1. Making the shape visible again
    text: 'If a later part of your workflow needs to reveal the hidden rectangle,
      you can toggle the flag:'
  - name: 2. Adding a border (stroke)
    text: 'A hidden shape can still have a visible border when you decide to show
      it. Set the `LineColor` and `LineWidth` properties:'
  - name: 3. Positioning the rectangle absolutely
    text: 'For precise layout control, switch the shape’s `WrapType` to `WrapType.Inline`
      (default) or `WrapType.TopBottom` and adjust `Left`/`Top` properties:'
  - name: 4. Using a different measurement unit
    text: 'Aspose.Words works in points (1 pt = 1/72 inch). If you prefer centimeters,
      convert first:'
  - name: Next steps
    text: '* Explore **how to insert shape** inside tables or headers/footers for
      watermarks. * Combine **add rectangle shape** with content controls to create
      dynamic placeholders. * Review Aspose.Words’ **shape manipulation** API for
      advanced features like rotation, gradient fills, and SVG import.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
- document generation
title: Insérer une forme rectangulaire en C# avec Aspose.Words – guide étape par étape
url: /fr/net/programming-with-shapes/insert-rectangle-shape-in-c-with-aspose-words-step-by-step-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insérer une forme rectangulaire en C# avec Aspose.Words – guide étape par étape

Si vous devez **insérer une forme rectangulaire** dans un document Word depuis C#, ce guide vous montre exactement comment procéder. Vous verrez comment définir la couleur de remplissage, masquer la forme afin qu’elle n’apparaisse pas dans la mise en page finale, et enregistrer le fichier — le tout en quelques lignes de code.

Dans les sections suivantes, nous couvrons tout ce que vous devez savoir : prérequis, la liste complète du code, les explications pour chaque étape, et des astuces pour les variantes courantes comme rendre la forme à nouveau visible ou utiliser une couleur différente. À la fin, vous serez capable de **ajouter une forme rectangulaire** à n’importe quel fichier .docx de manière programmatique.

## Prérequis

* **Aspose.Words for .NET** (version 23.10 ou ultérieure). Vous pouvez l’installer via NuGet:

  ```bash
  dotnet add package Aspose.Words
  ```

* .NET 6.0 SDK ou version ultérieure installée sur votre machine.
* Une compréhension de base du C# et de Visual Studio (ou tout IDE de votre choix).

Aucune bibliothèque supplémentaire n’est requise — les API liées aux formes font partie du package principal d’Aspose.Words.

## Insérer une forme rectangulaire avec Aspose.Words

Le cœur de la solution est un petit programme autonome qui crée un document vierge, insère un rectangle, le colore, le masque, puis enregistre le fichier. Vous trouverez ci‑dessous le code source complet avec des commentaires en ligne qui expliquent le *pourquoi* de chaque ligne.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Required for Color struct

// 1️⃣ Create a new, empty Word document.
Document document = new Document();

// 2️⃣ Obtain a DocumentBuilder – the primary API for editing the document.
DocumentBuilder builder = new DocumentBuilder(document);

// 3️⃣ Insert a rectangle shape of 100 × 50 points.
//    ShapeType.Rectangle tells Aspose.Words to create a simple rectangular drawing object.
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Set the shape's fill color to yellow.
//    The FillColor property accepts a System.Drawing.Color value.
rectangleShape.FillColor = Color.Yellow;

// 5️⃣ Hide the shape so it does not appear in the rendered document.
//    When Hidden = true, the shape is stored in the file but omitted from layout.
//    This is useful for placeholders, bookmarks, or metadata.
rectangleShape.Hidden = true;

// 6️⃣ Save the document to disk.
//    Change the path to a folder you have write access to.
document.Save(@"C:\Temp\HiddenRectangleShape.docx");
```

### Ce que fait chaque étape

| Étape | Raison |
|------|--------|
| **Create a new document** | Fournit une toile vierge ; vous pouvez également charger un .docx existant en passant un chemin de fichier à `new Document(path)`. |
| **Initialize DocumentBuilder** | `DocumentBuilder` est l’assistant de haut niveau qui vous permet d’insérer du texte, des tableaux et des formes sans manipuler les arbres de nœuds de bas niveau. |
| **Insert rectangle shape** | La méthode `InsertShape` renvoie un objet `Shape` que vous pouvez personnaliser davantage (taille, position, bordures, etc.). |
| **Set fill color** | La propriété `FillColor` contrôle la couleur intérieure ; vous pouvez utiliser n’importe quelle valeur `Color` (`Color.Red`, `Color.FromArgb(255, 0, 255, 0)`, etc.). |
| **Hide the shape** | `Hidden = true` indique à Word d’ignorer la forme lors de la mise en page tout en la conservant dans le XML du document. C’est la méthode standard pour stocker des objets invisibles. |
| **Save the document** | Enregistre les modifications dans un fichier .docx. Le fichier enregistré contiendra la forme rectangulaire masquée. |

## Comment définir la couleur de remplissage d’une forme

Modifier la couleur de remplissage est aussi simple que d’attribuer un `System.Drawing.Color` à la propriété `FillColor`. Si vous avez besoin d’une teinte personnalisée, utilisez `Color.FromArgb` :

```csharp
// Example: set a semi‑transparent teal fill
rectangleShape.FillColor = Color.FromArgb(128, 0, 128, 128);
```

*Pourquoi c’est important* : La couleur de remplissage est stockée dans le XML de la forme (`<w:fill>` attribut). Lorsque la forme est masquée, la couleur demeure, ce qui peut être utile pour un traitement en aval (par ex., extraire des métadonnées basées sur des codes couleur).

## Comment masquer une forme dans le document final

Le drapeau `Hidden` est une propriété booléenne de la classe `Shape`. Le définir à `true` garantit que la forme est ignorée par le moteur de mise en page de Word.

```csharp
rectangleShape.Hidden = true;
```

**Écueils courants**

* **Masqué vs. Visible** – Si vous avez besoin plus tard que la forme apparaisse, il suffit de définir `Hidden = false`.
* **Compatibilité** – Les versions plus anciennes de Word (pré‑2007) peuvent gérer les objets de dessin masqués différemment. Aspose.Words maintient la compatibilité en stockant le drapeau dans l’élément OOXML approprié.

## Comment insérer une forme programmatique

Bien que l’exemple utilise un rectangle, la même méthode `InsertShape` fonctionne pour de nombreuses autres formes (ellipse, triangle, ligne, etc.). Le premier argument est une valeur d’énumération `ShapeType` :

```csharp
// Insert an ellipse with the same dimensions
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
ellipse.FillColor = Color.LightBlue;
```

**Astuce** : Si vous devez placer la forme à un emplacement précis sur la page, utilisez `builder.MoveTo` pour définir le point d’insertion avant d’appeler `InsertShape`.

## Ajouter une forme rectangulaire à un document existant

Souvent, vous améliorerez un modèle plutôt que de partir de zéro. Remplacez l’étape 1 par :

```csharp
// Load an existing .docx file
Document document = new Document(@"C:\Templates\ReportTemplate.docx");
```

Toutes les étapes suivantes restent identiques, et le rectangle sera ajouté à l’endroit où le curseur du builder est positionné (généralement à la fin du document par défaut).

## Gestion des cas limites et des variantes

### 1. Rendre la forme à nouveau visible

Si une étape ultérieure de votre flux de travail doit révéler le rectangle masqué, vous pouvez basculer le drapeau :

```csharp
rectangleShape.Hidden = false;   // Shape will now be rendered
```

### 2. Ajouter une bordure (trait)

Une forme masquée peut toujours avoir une bordure visible lorsque vous décidez de l’afficher. Définissez les propriétés `LineColor` et `LineWidth` :

```csharp
rectangleShape.LineColor = Color.Black;
rectangleShape.LineWeight = 1.5; // points
```

### 3. Positionner le rectangle de façon absolue

Pour un contrôle précis de la mise en page, changez le `WrapType` de la forme en `WrapType.Inline` (par défaut) ou `WrapType.TopBottom` et ajustez les propriétés `Left`/`Top` :

```csharp
rectangleShape.WrapType = WrapType.TopBottom;
rectangleShape.Left = 72;   // 1 inch from the left margin
rectangleShape.Top = 144;   // 2 inches from the top margin
```

### 4. Utiliser une unité de mesure différente

Aspose.Words travaille en points (1 pt = 1/72 pouce). Si vous préférez les centimètres, convertissez d’abord :

```csharp
float cmToPoints = 28.3465f; // 1 cm ≈ 28.3465 pt
float width = 5 * cmToPoints;   // 5 cm wide
float height = 2 * cmToPoints;  // 2 cm tall
Shape cmRectangle = builder.InsertShape(ShapeType.Rectangle, width, height);
```

## Exemple complet exécutable

Ci‑dessous se trouve le programme *complet* que vous pouvez copier, coller et exécuter. Il inclut toutes les directives `using` nécessaires et utilise des chemins absolus que vous devrez ajuster à votre environnement.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class InsertRectangleShapeDemo
{
    static void Main()
    {
        // Create a blank document.
        Document doc = new Document();

        // Use DocumentBuilder to edit the document.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 100 × 50 pt rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // Set the fill color to yellow.
        rect.FillColor = Color.Yellow;

        // Hide the shape so it does not affect layout.
        rect.Hidden = true;

        // Save the result.
        string outputPath = @"C:\Temp\HiddenRectangleShape.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Résultat attendu** : Le fichier `HiddenRectangleShape.docx` s’ouvre dans Microsoft Word sans *forme visible*, mais le rectangle masqué est présent dans le XML du document. Vous pouvez vérifier son existence en ouvrant le .docx comme une archive zip et en inspectant `word/document.xml` pour un élément `<w:shape>` avec les attributs `w:fill="yellow"` et `w:hidden="true"`.

## Conclusion

Vous savez maintenant comment **insérer une forme rectangulaire** dans un document Word en utilisant C# et Aspose.Words, comment **définir la couleur de remplissage**, et comment **masquer la forme** afin qu’elle reste invisible dans la mise en page finale. Le même schéma fonctionne pour d’autres types de formes, couleurs personnalisées et modèles existants. Expérimentez avec les bordures, le positionnement absolu et différentes unités de mesure pour adapter la forme à vos exigences précises.

### Prochaines étapes

* Explorez **how to insert shape** à l’intérieur des tableaux ou des en-têtes/pieds de page pour des filigranes.
* Combinez **add rectangle shape** avec des contrôles de contenu pour créer des espaces réservés dynamiques.
* Consultez l’API **shape manipulation** d’Aspose.Words pour des fonctionnalités avancées comme la rotation, les remplissages en dégradé et l’importation SVG.

N’hésitez pas à adapter le code à votre propre projet, et dites‑nous dans les commentaires quel défi lié aux formes vous avez résolu ensuite !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Créer une forme rectangulaire dans Word avec C# – Guide étape par étape](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Tutoriel Ombre de forme Aspose.Words – Ajouter une ombre à une forme Word en C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Créer une forme groupée dans un document Word en utilisant Aspose.Words pour .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}