---
category: general
date: 2026-08-04
description: Enregistrez un fichier docx de façon programmatique tout en ajoutant
  une forme rectangulaire et en groupant des formes dans Word. Apprenez à définir
  les dimensions des formes et à créer une zone de texte de manière programmatique.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save docx file
- add rectangle shape
- group shapes word
- set shape dimensions
- create textbox programmatically
language: fr
lastmod: 2026-08-04
og_description: Enregistrez un fichier docx avec C# en ajoutant une forme rectangle,
  en groupant les formes dans Word, en définissant les dimensions de la forme et en
  créant une zone de texte par programmation.
og_image_alt: Screenshot of a saved docx file that contains a grouped rectangle and
  textbox
og_title: Enregistrer un fichier docx avec des formes groupées dans Word – guide pas
  à pas en C#
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  headline: Save docx file with grouped shapes in Word using C#
  type: TechArticle
- description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  name: Save docx file with grouped shapes in Word using C#
  steps:
  - name: 1. Create a new document and a builder
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing; using Aspose.Words.Drawing.Shapes;'
  - name: 2. Add rectangle shape to a group
    text: '```csharp // Create a group container that will hold all shapes. GroupShape
      group = new GroupShape(doc) { Width = 400, // Set shape dimensions for the group.
      Height = 200 };'
  - name: 3. Group shapes in Word document
    text: The `GroupShape` class aggregates multiple drawing objects. Grouping is
      useful when you want to treat several objects as a single unit (e.g., moving,
      rotating, or copying them together).
  - name: 4. Set shape dimensions for precise layout
    text: Both the group and its child shapes need explicit dimensions; otherwise
      Word applies default sizes that may not match your design.
  - name: 5. Create textbox programmatically inside the group
    text: '```csharp // Add a textbox shape with custom text. Shape textBox = new
      Shape(doc, ShapeType.TextBox) { Width = 180, Height = 100, Left = 210, // Position
      relative to the group’s coordinate system. Top = 10 };'
  - name: 6. Insert group shape and **save docx file**
    text: '```csharp // Insert the completed group into the document at the current
      cursor position. builder.InsertNode(group);'
  - name: Expected output
    text: '* A file named **GroupShape.docx** appears in the output directory. * Opening
      the file shows a rectangular shape on the left and a textbox containing “Grouped
      text” on the right, both locked together. * Selecting either shape moves the
      entire group, confirming that **group shapes word** functionalit'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Enregistrer un fichier docx avec des formes groupées dans Word en C#
url: /fr/net/programming-with-shapes/save-docx-file-with-grouped-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Enregistrer un fichier docx avec des formes groupées dans Word en C#

Si vous devez **save docx file** qui contient plusieurs formes disposées ensemble, ce guide vous montre comment le faire avec C#. Vous apprendrez comment **add rectangle shape**, regrouper plusieurs formes dans un document Word, **set shape dimensions**, et **create textbox programmatically**. La solution fonctionne avec la dernière version d'Aspose.Words for .NET et s'exécute sur .NET 6 ou version ultérieure.

Le tutoriel parcourt chaque étape, de la configuration du projet à l'appel final `doc.Save`. À la fin, vous disposerez d'un extrait de code réutilisable que vous pourrez coller dans n'importe quel projet console ou ASP.NET. Aucun script externe ou édition manuelle du fichier DOCX n'est requis.

## Prérequis

* .NET 6 SDK (ou version plus récente) installé.
* Une licence valide pour **Aspose.Words for .NET** (l'essai gratuit fonctionne pour les tests).
* Visual Studio 2022, VS Code, ou tout IDE capable de compiler des projets .NET.

Le code n'utilise que l'espace de noms Aspose.Words, aucune package NuGet supplémentaire n'est nécessaire.

## Enregistrer un fichier docx avec des formes groupées dans Word

Le cœur de la solution consiste à créer un `GroupShape` qui contient un rectangle et une zone de texte, puis à insérer le groupe dans le document et à appeler `doc.Save`. Les sections suivantes découpent le processus en morceaux gérables.

### 1. Créer un nouveau document et un builder

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // Initialize a blank document.
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for editing the document.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Pourquoi cette étape est importante* – Un nouvel objet `Document` représente un fichier *.docx* vide. `DocumentBuilder` fournit des méthodes de haut niveau comme `InsertNode`, que nous utiliserons pour placer la forme groupée.

### 2. Ajouter une forme rectangle à un groupe

```csharp
        // Create a group container that will hold all shapes.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,   // Set shape dimensions for the group.
            Height = 200
        };

        // Add a rectangle shape that will be part of the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,   // Set shape dimensions for the rectangle.
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);
```

*Pourquoi cette étape est importante* – L'opération **add rectangle shape** montre comment définir un élément visuel avec une taille et une position précises. Le rectangle vit à l'intérieur de `group`, ainsi déplacer le groupe plus tard déplace automatiquement le rectangle.

### 3. Regrouper des formes dans un document Word

La classe `GroupShape` agrège plusieurs objets de dessin. Le regroupement est utile lorsque vous souhaitez traiter plusieurs objets comme une seule unité (par ex., les déplacer, les faire pivoter ou les copier ensemble).

```csharp
        // The group now contains the rectangle; we will add more shapes next.
```

*Pourquoi nous regroupons* – Le regroupement réduit la complexité de la mise en page. Au lieu de positionner chaque forme individuellement sur la page, vous ajustez une fois les propriétés `Left`, `Top`, `Width` et `Height` du groupe.

### 4. Définir les dimensions des formes pour une mise en page précise

Le groupe et ses formes enfants ont tous deux besoin de dimensions explicites ; sinon Word applique des tailles par défaut qui peuvent ne pas correspondre à votre conception.

```csharp
        // Example of adjusting the group’s overall size.
        group.Width = 400;   // Overall width of the grouped area.
        group.Height = 200;  // Overall height of the grouped area.
```

*Pourquoi nous définissons les dimensions* – Une mesure précise garantit que le rectangle et la zone de texte ne se chevauchent pas involontairement et que le **save docx file** final correspond à la mise en page prévue.

### 5. Créer une zone de texte programmatiquement à l'intérieur du groupe

```csharp
        // Add a textbox shape with custom text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,   // Position relative to the group’s coordinate system.
            Top = 10
        };

        // Populate the textbox with a paragraph containing a run.
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);

        // Append the textbox to the same group.
        group.AppendChild(textBox);
```

*Pourquoi cette étape est importante* – Le segment **create textbox programmatically** montre comment intégrer du texte enrichi à l'intérieur d'une forme. L'utilisation d'un `Paragraph` et d'un `Run` vous donne un contrôle total sur le formatage ultérieur.

### 6. Insérer la forme groupée et **save docx file**

```csharp
        // Insert the completed group into the document at the current cursor position.
        builder.InsertNode(group);

        // Save the document to the file system.
        doc.Save("GroupShape.docx");   // The file now contains a rectangle and a textbox grouped together.
    }
}
```

*Pourquoi cette étape finale est importante* – L'appel `InsertNode` place les formes groupées exactement à l'endroit où se trouve le curseur du builder. La méthode `doc.Save` exécute l'opération **save docx file**, écrivant un document Word complet sur le disque.

> **Résultat :** L'ouverture de *GroupShape.docx* dans Microsoft Word affiche un rectangle à gauche et une zone de texte à droite, tous deux verrouillés ensemble dans un seul groupe. Vous pouvez déplacer le groupe comme une unité, le redimensionner ou appliquer un formatage supplémentaire.

## Exemple complet et exécutable

Copiez le code ci‑dessous dans un nouveau projet console (`dotnet new console`) et exécutez `dotnet run`. Le programme crée `GroupShape.docx` dans le dossier de sortie du projet.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // 1. Initialize document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Create a group shape container.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,
            Height = 200
        };

        // 3. Add rectangle shape.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);

        // 4. Add textbox shape with text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,
            Top = 10
        };
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);
        group.AppendChild(textBox);

        // 5. Insert the group into the document.
        builder.InsertNode(group);

        // 6. Save the document.
        doc.Save("GroupShape.docx");
    }
}
```

### Résultat attendu

* Un fichier nommé **GroupShape.docx** apparaît dans le répertoire de sortie.
* L'ouverture du fichier montre une forme rectangulaire à gauche et une zone de texte contenant « Grouped text » à droite, tous deux verrouillés ensemble.
* Sélectionner l'une ou l'autre forme déplace l'ensemble du groupe, confirmant que la fonctionnalité **group shapes word** fonctionne comme prévu.

## Variations courantes et cas limites

| Situation | Recommandation |
|-----------|----------------|
| Besoin de plus de deux formes | Ajoutez des objets `Shape` supplémentaires à `group` avant d'appeler `builder.InsertNode`. |
| Voulez que le groupe apparaisse sur une page spécifique | Déplacez le curseur du builder avec `builder.MoveToDocumentEnd()` ou `builder.MoveToPage(pageNumber)`. |
| Nécessité d'unités différentes (p. ex., centimètres) | Utilisez `ConvertUtil.InchToPoint(1.0)` pour convertir les pouces en points, l'unité attendue par Word. |
| Voulez que la zone de texte enveloppe le texte | Définissez `textBox.TextBoxWrap = TextBoxWrapType.Square` après la création de la zone de texte. |
| Travail avec d'anciennes versions du .NET Framework | La même API fonctionne avec .NET Framework 4.7+, mais assurez‑vous de référencer la bonne version d'Aspose.Words. |

**Astuce :** Définissez toujours la `Width` et la `Height` du groupe *après* avoir ajouté toutes les formes enfants. Cela garantit que le groupe englobe complètement son contenu, évitant les découpes lors de l'ouverture du document dans Word.

## Conclusion

Vous savez maintenant comment **save docx file** tout en **add rectangle shape**, **group shapes word**, **set shape dimensions**, et **create textbox programmatically** en utilisant Aspose.Words for .NET. L'exemple complet montre un modèle propre et réutilisable que vous pouvez adapter à des mises en page plus complexes, comme des graphiques, des images,

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l'API et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Créer une forme rectangle dans Word avec C# – Guide étape par étape](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Créer une forme groupée dans un document Word avec Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Tutoriel Ombre de forme Aspose.Words – Ajouter une ombre à une forme Word en C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}