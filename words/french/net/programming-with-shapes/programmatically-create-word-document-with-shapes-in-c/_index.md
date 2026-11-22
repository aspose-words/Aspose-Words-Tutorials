---
category: general
date: 2026-11-22
description: Créer un document Word de manière programmatique en C#, insérer une forme
  rectangle, insérer plusieurs formes et écrire les formes dans Word à l’aide d’Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically create word document
- insert rectangle shape
- insert multiple shapes
- write shapes to word
language: fr
lastmod: 2026-11-22
og_description: Créer un document Word en C# de façon programmatique en insérant une
  forme rectangle, en ajoutant plusieurs formes et en écrivant les formes dans Word
  à l’aide d’Aspose.Words.
og_image_alt: Screenshot of a Word document showing a rectangle and an ellipse grouped
  together
og_title: Créer un document Word avec des formes en C# de façon programmatique
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  headline: Programmatically create Word document with shapes in C#
  type: TechArticle
- description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  name: Programmatically create Word document with shapes in C#
  steps:
  - name: '**Initialize** a new `Document` and a `DocumentBuilder`.'
    text: '**Initialize** a new `Document` and a `DocumentBuilder`.'
  - name: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
    text: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
  - name: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
    text: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Créer un document Word avec des formes en C# de façon programmatique
url: /fr/net/programming-with-shapes/programmatically-create-word-document-with-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un document Word avec des formes de manière programmatique en C#

Si vous devez **créer un document Word de manière programmatique** contenant des graphiques personnalisés, ce guide vous montre comment le faire avec Aspose.Words pour .NET. Vous apprendrez à insérer une forme rectangle, à ajouter des formes supplémentaires, à les regrouper, et enfin à écrire les formes dans Word—le tout en quelques lignes de C#.

Créer un fichier Word avec des graphiques ne nécessite plus d'édition manuelle ou de scripts macro. À la fin de ce tutoriel, vous disposerez d’une méthode réutilisable qui génère un fichier `.docx` contenant un rectangle et une ellipse regroupés, prêts pour le traitement en aval ou la génération de rapports.

## Ce dont vous avez besoin

- .NET 6.0 ou version ultérieure (le code fonctionne également avec .NET Framework 4.6+)
- Aspose.Words pour .NET (package NuGet `Aspose.Words`)
- Un IDE tel que Visual Studio 2022 (tout éditeur capable de compiler du C# convient)

> **Astuce :** Installez le package avec la commande CLI `dotnet add package Aspose.Words` avant de commencer à coder.

## Création programmatique d’un document Word – aperçu

Le flux global se compose de trois phases logiques :

1. **Initialiser** un nouveau `Document` et un `DocumentBuilder`.  
2. **Insérer plusieurs formes** (un rectangle et une ellipse) et les placer dans un `GroupShape`.  
3. **Écrire les formes dans Word** en enregistrant le `Document` dans un fichier `.docx`.

Chaque phase est encapsulée dans une étape dédiée ci‑dessous, vous permettant de copier‑coller le code directement dans votre projet.

![Créer un document Word avec des formes groupées](grouped-shapes.png){: .align-center alt="Créer un document Word avec des formes groupées"}

## Étape 1 : Initialiser le document et le builder

La classe `Document` représente l’ensemble du fichier Word, tandis que `DocumentBuilder` fournit une API fluide pour ajouter du contenu.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document document = new Document();

// Initialize a DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(document);
```

*Pourquoi c’est important :* Créer d’abord le `Document` vous donne une toile vierge. Le `DocumentBuilder` suit le point d’insertion actuel, ce qui est essentiel lorsque vous attachez plus tard des formes à une hiérarchie de paragraphes.

## Étape 2 : Insérer un conteneur de forme groupée

Un `GroupShape` vous permet de traiter plusieurs formes individuelles comme une seule unité. Ceci est utile lorsque vous souhaitez les déplacer ou les redimensionner ensemble.

```csharp
// Insert a group shape container at the current cursor position
GroupShape groupShape = builder.InsertGroupShape();
```

*Explication :* `InsertGroupShape` insère un conteneur vide et le désigne automatiquement comme forme courante. Toutes les insertions de formes suivantes seront ajoutées à ce conteneur jusqu’à ce que vous fermiez le groupe.

## Insérer une forme rectangle

Nous ajoutons maintenant le premier graphique — un rectangle. Cela répond à l’exigence **insérer une forme rectangle**.

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

Le rectangle hérite du contexte de formatage du groupe, il apparaît donc à l’intérieur du `GroupShape`. Vous pouvez également définir la couleur de ligne, le remplissage ou le texte ultérieurement si nécessaire.

## Insérer plusieurs formes

Pour démontrer la capacité **insérer plusieurs formes**, nous ajoutons une ellipse immédiatement après le rectangle. Vous pouvez continuer à ajouter autant de formes que vous le souhaitez (par ex., triangles, étoiles) avant de fermer le groupe.

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

À ce stade, le groupe contient deux formes distinctes : un rectangle et une ellipse. Comme elles partagent le même parent, vous pouvez les déplacer comme une unité.

## Étape 3 : Attacher la forme groupée à la hiérarchie de paragraphes

Les documents Word stockent le contenu dans un arbre de paragraphes. Pour rendre le groupe visible dans le fichier final, nous devons l’attacher au paragraphe actuel.

```csharp
// Append the group shape to the current paragraph so it becomes part of the document flow
groupShape.AppendChild(builder.CurrentParagraph);
```

*Pourquoi cette étape est nécessaire :* Sans ajouter le groupe à un paragraphe, les formes n’existent que en mémoire et sont omises lors de l’enregistrement du document.

## Étape 4 : Enregistrer le document – écrire les formes dans Word

Enfin, nous persistons le `Document` en mémoire sur le disque. Cela répond à l’objectif **écrire les formes dans Word**.

```csharp
// Define the output path (adjust the folder as needed)
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");

// Save the document in DOCX format
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Lorsque vous ouvrez `GroupShape.docx` dans Microsoft Word, vous verrez un rectangle et une ellipse regroupés, exactement comme le code les a insérés.

### Résultat attendu

- Un fichier nommé **GroupShape.docx** situé dans le dossier de sortie du projet.
- Dans le fichier Word : un seul paragraphe contenant un rectangle groupé (100 pt × 50 pt) et une ellipse (80 pt × 40 pt). Sélectionner l’une des formes sélectionne l’ensemble du groupe.

## Gestion des cas limites courants

| Situation | Recommandation |
|-----------|----------------|
| **Différente résolution DPI ou taille de page** | Définissez explicitement `builder.PageSetup.PaperSize` avant d’insérer les formes pour éviter un redimensionnement inattendu. |
| **Besoin de positionner les formes avec précision** | Utilisez `builder.MoveTo` pour déplacer le point d’insertion, puis définissez les propriétés `groupShape.Left` et `groupShape.Top` (les valeurs sont en points). |

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Créer un document Word – Insérer une forme rectangle & ombre en C#](/words/english/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/)
- [Créer un document Word programmatique et regrouper des formes en C#](/words/english/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/)
- [Créer programmatique un document Word avec une forme groupée](/words/english/net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}