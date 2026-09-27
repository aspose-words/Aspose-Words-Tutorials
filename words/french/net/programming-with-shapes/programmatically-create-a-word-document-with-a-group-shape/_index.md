---
category: general
date: 2026-09-27
description: Créer un document Word avec une forme groupée de façon programmatique
  en utilisant Aspose.Words en C#. Suivez ce guide étape par étape pour générer le
  fichier et découvrir des astuces utiles.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically create word document
- how to create group shape word
- Aspose.Words group shape
- C# Word automation
- StructuredDocumentTag example
language: fr
lastmod: 2026-09-27
og_description: Créer programmétiquement un document Word avec une forme groupée en
  utilisant Aspose.Words. Ce tutoriel vous guide à travers le code C# complet, explique
  chaque étape et montre le résultat final.
og_image_alt: Screenshot of a Word document containing a group shape with a text placeholder
og_title: Créer un document Word avec une forme groupée de façon programmatique –
  guide C#
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Programmatically create a Word document with a group shape using Aspose.Words
    in C#. Follow this step‑by‑step guide to generate the file and learn useful tips.
  headline: Programmatically create a Word document with a group shape
  type: TechArticle
- description: Programmatically create a Word document with a group shape using Aspose.Words
    in C#. Follow this step‑by‑step guide to generate the file and learn useful tips.
  name: Programmatically create a Word document with a group shape
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code also works with .NET Framework 4.7+). - Aspose.Words
      for .NET NuGet package (`Install-Package Aspose.Words`). - A C# IDE such as
      Visual Studio 2022 or VS Code with the C# extension.'
  - name: Expected output screenshot (conceptual)
    text: '``` +-----------------------------------------------------------+ | ┌───────────────────────────────────────────────┐
      | | │ [Enter text here] │ | | └───────────────────────────────────────────────┘
      | +-----------------------------------------------------------+ ```'
  - name: Adding more child shapes
    text: 'You can enrich the group by appending additional drawing objects, such
      as pictures or text boxes:'
  - name: Controlling wrapping style
    text: 'If you need the group shape to stay behind text or to have tight wrapping,
      set the `WrapType` property:'
  - name: 'Edge case: Empty group shape'
    text: A `GroupShape` without children renders as an invisible placeholder. Always
      verify that at least one child (e.g., an SDT or a picture) is added; otherwise
      Word may drop the group during saving.
  - name: Compatibility note
    text: Aspose.Words 23.10+ fully supports `GroupShape` and `StructuredDocumentTag`.
      If you target older versions, the `AppendChild` method may behave differently,
      and you might need to call `UpdatePageLayout` after saving.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Créer un document Word avec une forme groupée de façon programmatique
url: /fr/net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un document Word programmatique avec une forme groupée

Si vous devez **créer un document Word de façon programmatique** contenant un dessin groupé, ce guide vous montre exactement comment le faire avec Aspose.Words for .NET. Que vous construisiez un générateur de contrats, un créateur de rapports ou un outil de remplissage de formulaires, vous apprendrez le code C# complet, pourquoi chaque appel d’API est important et comment gérer les cas limites courants.

Créer une forme groupée dans Word peut sembler délicat parce que le modèle d’objet Word traite les formes groupées comme des conteneurs pour d’autres objets de dessin. Ce tutoriel répond non seulement à **comment créer des documents Word avec une forme groupée**, mais montre également comment intégrer un StructuredDocumentTag (SDT) en texte brut à l’intérieur du groupe afin que la forme puisse contenir du contenu éditable.

## Ce que vous allez accomplir

- Initialiser un nouveau document Word vierge avec `Document` et `DocumentBuilder`.
- Insérer un `GroupShape` à la position actuelle du curseur.
- Ajouter un `StructuredDocumentTag` en texte brut (SDT) à la forme groupée.
- Enregistrer le fichier au format `.docx` pouvant être ouvert dans Microsoft Word.
- Comprendre les propriétés clés de `GroupShape` et `StructuredDocumentTag` pour de futures extensions.

### Prérequis

- .NET 6.0 ou ultérieur (le code fonctionne également avec .NET Framework 4.7+).
- Package NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`).
- Un IDE C# tel que Visual Studio 2022 ou VS Code avec l’extension C#.

---

## Créer un document Word programmatique – configurer le projet

1. **Créer un nouveau projet console**  
   ```bash
   dotnet new console -n WordGroupShapeDemo
   cd WordGroupShapeDemo
   dotnet add package Aspose.Words
   ```
2. **Ouvrir le projet dans votre IDE** et remplacer le contenu de `Program.cs` par le code présenté dans les sections suivantes.

> **Astuce pro :** Gardez votre dossier de projet propre ; Aspose.Words écrit le fichier de sortie dans le répertoire de travail sauf si vous fournissez un chemin absolu.

## Étape 1 : Initialiser le document et le builder

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;

// Create a new blank document.
Document doc = new Document();

// DocumentBuilder gives you a cursor to insert nodes.
DocumentBuilder builder = new DocumentBuilder(doc);

// Optional: set the page size or margins if your shape must fit a specific area.
builder.PageSetup.PageWidth = 595;   // A4 width in points
builder.PageSetup.PageHeight = 842;  // A4 height in points
```

**Pourquoi cela importe :**  
`Document` représente l’ensemble du fichier Word, tandis que `DocumentBuilder` vous permet de positionner de nouveaux éléments sans naviguer manuellement dans l’arbre de nœuds. Définir les dimensions de la page dès le départ garantit que la forme groupée ne déborde pas de la page.

## Étape 2 : Insérer un GroupShape à la position actuelle du curseur

```csharp
// Create an empty GroupShape container.
GroupShape groupShape = new GroupShape(doc)
{
    // Give the group a size that comfortably holds its children.
    Width = 300,
    Height = 150,

    // Position the group relative to the page (you can also use RelativeHorizontalPosition).
    Left = 100,
    Top = 100
};

// Insert the group shape into the document where the builder is currently positioned.
builder.InsertNode(groupShape);
```

**Explication :**  
Un `GroupShape` est un objet de dessin qui peut contenir d’autres formes, images ou zones de texte. En définissant `Width`, `Height`, `Left` et `Top`, vous contrôlez son placement exact sur la page. La méthode `InsertNode` place la forme dans le flux principal du document, se comportant comme un objet flottant.

## Étape 3 : Ajouter un StructuredDocumentTag (SDT) en texte brut à l’intérieur du groupe

```csharp
// Create a plain‑text SDT that will act as a content placeholder.
StructuredDocumentTag sdtTag = new StructuredDocumentTag(doc, SdtType.PlainText, true)
{
    // Provide a helpful tag title that appears as a tooltip in Word.
    Title = "GroupShapeText",
    // Set default placeholder text.
    PlaceholderName = "Enter text here"
};

// Append the SDT to the group shape's child collection.
groupShape.AppendChild(sdtTag);
```

**Pourquoi utiliser un SDT ?**  
Les StructuredDocumentTags sont les contrôles de contenu natifs de Word. Ils permettent aux utilisateurs de modifier le texte directement dans le document enregistré, et ils peuvent être accédés programmatique ultérieurement pour l’extraction de données. Placer un SDT à l’intérieur d’une forme groupée vous permet de combiner un regroupement visuel avec du contenu éditable.

## Étape 4 : Enregistrer le document

```csharp
// Define the output path – replace with your desired directory.
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShapeDemo.docx");

// Save the document in DOCX format.
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved to: {outputPath}");
```

**Résultat :**  
L’ouverture de `GroupShapeDemo.docx` dans Microsoft Word affiche un rectangle flottant (la forme groupée) contenant un espace réservé de texte affichant « Enter text here ». Les utilisateurs peuvent cliquer à l’intérieur de la forme et taper directement.

### Capture d'écran du résultat attendu (conceptuel)

```
+-----------------------------------------------------------+
|   ┌───────────────────────────────────────────────┐   |
|   │  [Enter text here]                               │   |
|   └───────────────────────────────────────────────┘   |
+-----------------------------------------------------------+
```

La boîte extérieure représente le `GroupShape` ; la zone grise intérieure représente le `StructuredDocumentTag`.

---

## Comment créer un group shape word – considérations supplémentaires

### Ajout de formes enfants supplémentaires

Vous pouvez enrichir le groupe en ajoutant d’autres objets de dessin, tels que des images ou des zones de texte :

```csharp
// Example: add a picture inside the same group.
Shape picture = new Shape(doc, ShapeType.Image)
{
    ImageData = ImageData.FromFile("logo.png"),
    Width = 100,
    Height = 50,
    Left = 10,
    Top = 80
};
groupShape.AppendChild(picture);
```

### Contrôle du style d’habillage

Si vous avez besoin que la forme groupée reste derrière le texte ou possède un habillage serré, définissez la propriété `WrapType` :

```csharp
groupShape.WrapType = WrapType.Inline; // Makes the shape behave like a paragraph.
```

### Cas limite : forme groupée vide

Un `GroupShape` sans enfants s’affiche comme un espace réservé invisible. Vérifiez toujours qu’au moins un enfant (par ex., un SDT ou une image) est ajouté ; sinon Word peut supprimer le groupe lors de l’enregistrement.

### Note de compatibilité

Aspose.Words 23.10+ prend pleinement en charge `GroupShape` et `StructuredDocumentTag`. Si vous ciblez des versions antérieures, la méthode `AppendChild` peut se comporter différemment, et il peut être nécessaire d’appeler `UpdatePageLayout` après l’enregistrement.

---

## Exemple complet exécutable

Copiez l’ensemble du fragment ci‑dessous dans `Program.cs` et exécutez le projet. Le code inclut toutes les étapes ci‑above dans un programme autonome.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.PageSetup.PageWidth = 595;
        builder.PageSetup.PageHeight = 842;

        // 2️⃣ Create and insert a GroupShape.
        GroupShape groupShape = new GroupShape(doc)
        {
            Width = 300,
            Height = 150,
            Left = 100,
            Top = 100
        };
        builder.InsertNode(groupShape);

        // 3️⃣ Add a plain‑text StructuredDocumentTag (SDT) inside the group.
        StructuredDocumentTag sdtTag = new StructuredDocumentTag(doc, SdtType.PlainText, true)
        {
            Title = "GroupShapeText",
            PlaceholderName = "Enter text here"
        };
        groupShape.AppendChild(sdtTag);

        // 4️⃣ Optional: add a picture to demonstrate multiple children.
        // Uncomment and adjust the path if you want to test this.
        /*
        Shape picture = new Shape(doc, ShapeType.Image)
        {
            ImageData = ImageData.FromFile("logo.png"),
            Width = 100,
            Height = 50,
            Left


## Que devriez‑vous apprendre ensuite ?


Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Créer une forme groupée dans un document Word avec Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Créer une forme rectangulaire dans Word avec C# – Guide étape par étape](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Créer un document Word vierge avec Aspose.Words – Guide étape par étape](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}