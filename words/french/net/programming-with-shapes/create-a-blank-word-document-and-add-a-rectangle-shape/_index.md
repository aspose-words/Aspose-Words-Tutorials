---
category: general
date: 2026-09-05
description: Apprenez à créer un document Word vierge et à ajouter une forme rectangulaire
  qui peut être masquée en utilisant Aspose.Words en C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- blank word document
- add rectangle shape
- how to hide shape
- hide shape word
- create hidden shape
language: fr
lastmod: 2026-09-05
og_description: Création d'un document Word vierge et insertion d'une forme rectangulaire
  cachée avec Aspose.Words – guide étape par étape pour les développeurs C#.
og_image_alt: Screenshot of a blank Word document with a hidden rectangle shape created
  by Aspose.Words in C#
og_title: Créer un document Word vierge avec une forme rectangulaire cachée
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  headline: Create a blank word document and add a rectangle shape
  type: TechArticle
- description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  name: Create a blank word document and add a rectangle shape
  steps:
  - name: Expected result
    text: 'Open `HiddenRectangle.docx` in Word:'
  - name: Can I hide multiple shapes at once?
    text: Yes. Create each shape, set `Hidden = true`, and insert them sequentially.
      The hidden flag works per node, so mixing hidden and visible shapes in the same
      document is supported.
  - name: What if I need the shape to be hidden only in the print view?
    text: 'Word distinguishes between **display** and **print** visibility through
      the `DisplayWhen` property. Aspose.Words does not expose a direct API for that
      flag, but you can modify the underlying XML:'
  - name: Does the hidden shape affect file size?
    text: A hidden shape adds the same XML payload as a visible one, so the file size
      increase is identical. However, because the shape
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Créer un document Word vierge et ajouter une forme rectangulaire
url: /fr/net/programming-with-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un document Word vierge et ajouter une forme rectangulaire

Si vous avez besoin de créer un **document Word vierge** qui contient également une forme que vous ne souhaitez pas voir apparaître dans la mise en page, ce guide vous montre exactement comment le faire avec Aspose.Words pour .NET. Vous verrez un exemple complet et exécutable qui crée un nouveau document, ajoute une forme rectangulaire, masque cette forme et enregistre le fichier — aucune outil supplémentaire requis.

Le tutoriel couvre tout, de la configuration du projet au dépannage des problèmes courants. À la fin, vous serez capable de générer un fichier Word qui semble vide pour le lecteur mais qui contient toujours des métadonnées cachées, ce qui est utile pour des éléments tels que les filigranes, le stockage XML personnalisé ou les ancres de mise en page.

## Prérequis

* .NET 6.0 SDK ou version ultérieure (le code fonctionne également avec .NET Framework 4.7+)
* Visual Studio 2022 (ou tout IDE qui prend en charge C#)
* Une licence NuGet **Aspose.Words** active (l'essai gratuit fonctionne pour les tests)
* Familiarité de base avec C# et le concept de nœuds de document

Vous pouvez installer la bibliothèque avec la commande CLI suivante :

```bash
dotnet add package Aspose.Words
```

> **Conseil pro :** Gardez votre version d'Aspose.Words à jour ; l'API utilisée dans ce tutoriel est stable depuis la version 23.10.

## Comment créer un document Word vierge avec Aspose.Words

La première étape consiste à instancier un objet `Document`. Un `Document` vierge représente un **document Word vierge**—aucun paragraphe, aucune section, seulement le conteneur du fichier.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, empty Word document
Document document = new Document();
```

> **Pourquoi c'est important :** Commencer avec un document vierge garantit que la forme cachée que vous ajouterez plus tard n'interférera pas avec le contenu ou les styles existants.

## Ajouter une forme rectangulaire au document

Ensuite, nous créons une forme rectangulaire. Dans Aspose.Words, une forme est un nœud qui peut être placé n'importe où dans l'arbre du document, et il peut être configuré avec la taille, le remplissage, le style de ligne et la visibilité.

```csharp
// Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Define a rectangle shape (the "add rectangle shape" step)
Shape rectangle = new Shape(document, ShapeType.Rectangle)
{
    Width = 150,   // Width in points (1 point = 1/72 inch)
    Height = 80,   // Height in points
    FillColor = System.Drawing.Color.LightGray,
    StrokeColor = System.Drawing.Color.DarkGray,
    StrokeWeight = 0.5
};
```

Le code ci‑above crée un rectangle visible. À ce stade, vous pourriez l'insérer dans le document avec `builder.InsertNode(rectangle)`. Cependant, comme nous voulons que la forme reste cachée, nous ajusterons sa propriété `Hidden` avant l'insertion.

## Comment masquer une forme dans un document Word

Word fournit un attribut `Hidden` pour les nœuds de forme. Lorsqu'il est défini sur `true`, la forme n'apparaît pas dans la mise en page, mais elle reste partie du XML du document. C'est le cœur de la exigence **comment masquer une forme**.

```csharp
// Hide the shape so it won't be displayed
rectangle.Hidden = true;
```

> **Explication :** Définir `Hidden = true` ajoute l'attribut `<w:hide>` au XML de la forme. Les processeurs Word ignorent la forme lors du rendu, mais la forme reste accessible programmatiquement ou via la vue XML de Word.

## Insérer la forme cachée dans le document vierge

Nous plaçons maintenant le rectangle caché dans l'arbre du document. Comme le document est encore vide, la forme devient le premier nœud de l'histoire principale.

```csharp
// Insert the hidden rectangle at the current cursor position
builder.InsertNode(rectangle);
```

Si vous ouvrez le fichier résultant dans Microsoft Word, vous verrez une page apparemment vide. La forme est présente, mais elle est invisible.

## Enregistrer le document

Enfin, écrivez le document sur le disque. Vous pouvez choisir n'importe quel format supporté (`.docx`, `.pdf`, `.odt`, etc.). Pour ce tutoriel, nous utiliserons le format DOCX moderne.

```csharp
// Save the file – adjust the path as needed
string outputPath = Path.Combine(Environment.CurrentDirectory, "HiddenRectangle.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

### Résultat attendu

Ouvrez `HiddenRectangle.docx` dans Word :

* Le document apparaît vierge (aucune forme ou texte visible).
* Si vous inspectez le fichier avec un outil comme **Open XML SDK** ou le **Word XML Viewer**, vous verrez l'élément `<w:pict>` contenant le rectangle avec l'attribut `hidden`.

![blank word document with hidden rectangle shape](image.png){: .align-center alt="document Word vierge avec forme rectangulaire cachée"}

## Exemple complet et exécutable

Voici le programme complet que vous pouvez copier‑coller dans une application console. Il inclut toutes les directives `using` nécessaires, la gestion des erreurs et les commentaires.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Prepare a DocumentBuilder to manipulate the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Define a rectangle shape (add rectangle shape)
        Shape rectangle = new Shape(document, ShapeType.Rectangle)
        {
            Width = 150,
            Height = 80,
            FillColor = System.Drawing.Color.LightGray,
            StrokeColor = System.Drawing.Color.DarkGray,
            StrokeWeight = 0.5,
            // 4️⃣ Hide the shape (how to hide shape)
            Hidden = true
        };

        // 5️⃣ Insert the hidden shape into the blank document
        builder.InsertNode(rectangle);

        // 6️⃣ Save the document (create hidden shape)
        string outputPath = Path.Combine(
            Environment.CurrentDirectory, "HiddenRectangle.docx");
        document.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Exécutez le programme (`dotnet run`) et vérifiez le fichier de sortie. La console confirmera l'emplacement d'enregistrement.

## Questions fréquentes et cas particuliers

### Puis-je masquer plusieurs formes à la fois ?

Oui. Créez chaque forme, définissez `Hidden = true`, et insérez‑les séquentiellement. Le drapeau caché fonctionne par nœud, donc le mélange de formes cachées et visibles dans le même document est pris en charge.

### Et si je veux que la forme soit cachée uniquement dans la vue d'impression ?

Word distingue la visibilité **affichage** et **impression** via la propriété `DisplayWhen`. Aspose.Words n'expose pas d'API directe pour ce drapeau, mais vous pouvez modifier le XML sous‑jacent :

```csharp
rectangle.GetShapeRenderer().GetShapeXml()
    .SetAttribute("w:display", "print");
```

Utilisez ceci uniquement lorsque vous avez besoin d'une visibilité uniquement à l'impression.

### La forme cachée affecte‑t‑elle la taille du fichier ?

Une forme cachée ajoute la même charge XML qu'une forme visible, donc l'augmentation de la taille du fichier est identique. Cependant, parce que la forme

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l'API et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Créer un document Word vierge avec forme rectangulaire ombrée – Guide étape par étape](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Créer une forme rectangulaire dans Word avec C# – Guide étape par étape](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Tutoriel sur l'ombre de forme Aspose.Words – Ajouter une ombre à une forme Word en C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}