---
category: general
date: 2026-07-19
description: Regroupez des formes dans Word avec Aspose.Words. Apprenez à ajouter
  une forme rectangulaire, définir une forme d'ellipse et insérer une forme dans des
  documents Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- how to group shapes
- insert shape into word
- define ellipse shape
language: fr
lastmod: 2026-07-19
og_description: Regroupez des formes dans Word avec Aspose.Words. Maîtrisez l’ajout
  d’une forme rectangle, la définition d’une forme ellipse et l’insertion de formes
  dans des documents Word.
og_image_alt: Screenshot of grouped shapes in a Word document created with Aspose.Words
og_title: Regrouper des formes dans Word – Tutoriel C# étape par étape
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Group shapes in Word using Aspose.Words. Learn how to add rectangle
    shape, define ellipse shape, and insert shape into Word documents.
  headline: Group Shapes in Word with Aspose.Words – Complete C# Guide
  type: TechArticle
- description: Group shapes in Word using Aspose.Words. Learn how to add rectangle
    shape, define ellipse shape, and insert shape into Word documents.
  name: Group Shapes in Word with Aspose.Words – Complete C# Guide
  steps:
  - name: Set Up the Document and Builder
    text: We start by creating an empty `Document` and a `DocumentBuilder`. The builder
      is our “pen” that lets us insert content wherever we need it.
  - name: Add Rectangle Shape (add rectangle shape)
    text: Now we **add rectangle shape** to the document. We set its size, position,
      and fill colour to make it stand out.
  - name: Define Ellipse Shape (define ellipse shape)
    text: Next, we **define ellipse shape**. Notice the different `ShapeType` and
      the offset (`Left = 120`) so the ellipse sits beside the rectangle.
  - name: (Optional) Insert Individual Shapes for Preview
    text: If you want to see each shape before grouping, you can **insert shape into
      Word** individually. This step is optional but handy for debugging.
  - name: How to Group Shapes – Create a GroupShape
    text: 'Here’s the core of the tutorial: **how to group shapes**. We create a `GroupShape`,
      attach our rectangle and ellipse, and decide how the group behaves with surrounding
      text.'
  - name: Insert the Grouped Shape into the Document (insert shape into word)
    text: Now we **insert shape into Word**—but this time it’s the grouped container,
      not the individual pieces.
  - name: Save the Document
    text: Finally, write the file to disk. You can change the path to suit your project
      layout.
  - name: What if I need more than two shapes?
    text: Just keep calling `groupShape.AppendChild(yourNewShape);` before inserting
      the group. The API imposes no limit on the number of child shapes.
  - name: Can I rotate or resize the whole group?
    text: Absolutely. `GroupShape` inherits from `Shape`, so you can set properties
      like `RotationAngle`, `Width`, or `Height` on the group itself, and all child
      shapes will follow.
  - name: How do I change the group’s background colour?
    text: Use `groupShape.FillColor`. This fills the invisible bounding box; it can
      be handy for highlighting.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
title: Regrouper des formes dans Word avec Aspose.Words – Guide complet C#
url: /fr/net/programming-with-shapes/group-shapes-in-word-with-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Regrouper des formes dans Word – Guide complet C#

Vous êtes-vous déjà demandé comment **regrouper des formes dans Word** sans passer par l’interface graphique ? Vous n’êtes pas seul. Que vous génériez des contrats, des flyers ou des diagrammes de façon programmatique, pouvoir **ajouter une forme rectangle**, **définir une forme ellipse**, puis **regrouper des formes dans Word** peut vous faire gagner des heures de travail manuel.

Dans ce tutoriel, nous parcourrons un exemple réel en utilisant **Aspose.Words for .NET**. À la fin, vous saurez exactement comment **insérer une forme dans Word**, les combiner, et produire un document soigné que vous pourrez envoyer à vos clients ou à vos co‑équipiers.

---

## Ce dont vous avez besoin

Avant de commencer, assurez‑vous d’avoir les éléments suivants :

- **Aspose.Words for .NET** (dernière version, par ex. 24.9). Vous pouvez l’obtenir via NuGet avec `Install-Package Aspose.Words`.
- Un environnement de développement .NET (Visual Studio 2022 ou VS Code avec l’extension C# fonctionne très bien).
- Une connaissance de base de la syntaxe C# — rien de compliqué, juste les habituelles instructions `using` et la création d’objets.

C’est tout. Pas de bibliothèques supplémentaires, pas d’interop COM, uniquement du code géré pur.

---

## Comment regrouper des formes dans Word avec Aspose.Words

Voici une décomposition étape par étape qui reflète le code que vous avez déjà. Chaque étape explique **pourquoi** nous faisons cela, pas seulement **ce que** fait la ligne, afin que vous puissiez adapter le modèle à n’importe quelle forme.

### Étape 1 : Configurer le document et le builder

Nous commençons par créer un `Document` vide et un `DocumentBuilder`. Le builder est notre « stylo » qui nous permet d’insérer du contenu où nous le souhaitons.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();
// The builder will help us place shapes and text
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Pourquoi ?** L’objet `Document` représente le fichier .docx complet, tandis que `DocumentBuilder` fournit une API pratique pour insérer des nœuds (comme des formes) sans manipuler directement l’arbre de nœuds sous‑jacent.

### Étape 2 : Ajouter une forme rectangle (add rectangle shape)

Nous **ajoutons une forme rectangle** au document. Nous définissons sa taille, sa position et sa couleur de remplissage pour la faire ressortir.

```csharp
// Create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 100;                     // Width in points
rectangleShape.Height = 50;                      // Height in points
rectangleShape.Left   = 0;                       // X‑coordinate
rectangleShape.Top    = 0;                       // Y‑coordinate
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
```

> **Astuce :** Vous pouvez changer `FillColor` en n’importe quelle `System.Drawing.Color` de votre choix. Cela est utile lorsque vous avez besoin de sections codées par couleur dans un rapport.

### Étape 3 : Définir une forme ellipse (define ellipse shape)

Ensuite, nous **définissons une forme ellipse**. Remarquez le `ShapeType` différent et le décalage (`Left = 120`) afin que l’ellipse se place à côté du rectangle.

```csharp
// Create an ellipse shape
Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
ellipseShape.Width  = 80;
ellipseShape.Height = 40;
ellipseShape.Left   = 120;   // Position it to the right of the rectangle
ellipseShape.Top    = 0;
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```

> **Pourquoi c’est important :** En positionnant les formes explicitement, vous contrôlez leur apparence avant de les regrouper. Si vous vous fiez à la mise en page automatique, le groupement pourrait être mal centré.

### Étape 4 : (Optionnel) Insérer les formes individuelles pour prévisualiser

Si vous voulez voir chaque forme avant le groupement, vous pouvez **insérer une forme dans Word** individuellement. Cette étape est optionnelle mais pratique pour le débogage.

```csharp
// Insert the rectangle and ellipse separately (useful for preview)
builder.InsertNode(rectangleShape);
builder.InsertNode(ellipseShape);
```

> **Pro tip :** Commentez ces deux lignes une fois que vous êtes sûr que les formes ont l’air correct ; sinon vous vous retrouverez avec des visuels dupliqués après le groupement.

### Étape 5 : Comment regrouper des formes – Créer un GroupShape

Voici le cœur du tutoriel : **comment regrouper des formes**. Nous créons un `GroupShape`, y attachons notre rectangle et notre ellipse, et décidons comment le groupe se comporte avec le texte environnant.

```csharp
// Create a container for the group
GroupShape groupShape = new GroupShape(document);

// Add the rectangle and ellipse to the group
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);

// Set wrapping – Inline makes the group act like a character in the text flow
groupShape.WrapType = WrapType.Inline;
```

> **Explication :** `GroupShape` est essentiellement une mini‑toile qui contient d’autres formes. En définissant `WrapType` à `Inline`, tout le groupe se déplace comme une unité unique lorsque vous ajoutez ou supprimez du texte.

### Étape 6 : Insérer la forme groupée dans le document (insert shape into word)

Nous **insérons maintenant la forme dans Word**—mais cette fois il s’agit du conteneur groupé, pas des pièces individuelles.

```csharp
// Insert the grouped shape at the current cursor position
builder.InsertNode(groupShape);
```

> **Que se passe‑t‑il en coulisses ?** L’appel `InsertNode` ajoute le `GroupShape` à la collection de nœuds du document. Comme le groupe contient déjà le rectangle et l’ellipse, ils apparaissent ensemble comme un seul objet.

### Étape 7 : Enregistrer le document

Enfin, écrivez le fichier sur le disque. Vous pouvez modifier le chemin pour l’adapter à la structure de votre projet.

```csharp
// Save the resulting .docx file
document.Save("YOUR_DIRECTORY/GroupShape.docx");
```

> **Résultat :** Ouvrez `GroupShape.docx` dans Microsoft Word et vous verrez un rectangle bleu clair et une ellipse corail verrouillés ensemble. Faire glisser l’un déplace l’autre—exactement ce que promet « regrouper des formes dans word ».

---

## Confirmation visuelle

Voici une maquette de ce à quoi ressemblent les formes groupées dans le fichier Word.  

![Capture d'écran des formes groupées dans un document Word créé avec Aspose.Words](grouped_shapes_placeholder.png "regrouper des formes dans word")

*Le texte alternatif de l’image contient le mot‑clé principal pour l’accessibilité et le SEO.*

---

## Questions fréquentes & cas particuliers

### Et si j’ai besoin de plus de deux formes ?

Continuez simplement d’appeler `groupShape.AppendChild(votreNouvelleForme);` avant d’insérer le groupe. L’API n’impose aucune limite au nombre de formes enfants.

### Puis‑je faire pivoter ou redimensionner tout le groupe ?

Absolument. `GroupShape` hérite de `Shape`, vous pouvez donc définir des propriétés comme `RotationAngle`, `Width` ou `Height` sur le groupe lui‑même, et toutes les formes enfants suivront.

```csharp
groupShape.RotationAngle = 15;   // Rotate the entire group 15 degrees
groupShape.Width = 250;          // Stretch the group uniformly
```

### Comment changer la couleur d’arrière‑plan du groupe ?

Utilisez `groupShape.FillColor`. Cela remplit la boîte englobante invisible ; cela peut être pratique pour mettre en évidence.

```csharp
groupShape.FillColor = System.Drawing.Color.LightGray;
```

### Cela fonctionne‑t‑il avec les anciens formats Word (.doc) ?

`Aspose.Words` peut également enregistrer au format `.doc`—il suffit de remplacer l’extension de fichier dans `Save`. Cependant, certaines fonctionnalités avancées de forme (comme le groupement) ne sont pleinement prises en charge que dans le format OOXML `.docx`.

---

## Exemple complet fonctionnel

Copiez‑collez le bloc suivant dans une nouvelle application console pour voir le processus complet en action. Aucun élément ne manque ; il s’agit d’un **exemple complet et exécutable**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing; // For Color

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Add rectangle shape
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width  = 100;
        rectangleShape.Height = 50;
        rectangleShape.Left   = 0;
        rectangleShape.Top    = 0;
        rectangleShape.FillColor = Color.LightBlue;

        // 3️⃣ Define ellipse shape
        Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
        ellipseShape.Width  = 80;
        ellipseShape.Height = 40;
        ellipseShape.Left   = 120;
        ellipseShape.Top    = 0;
        ellipseShape.FillColor = Color.LightCoral;

        // 4️⃣ (Optional) Preview individual shapes
        // builder.InsertNode(rectangleShape);
        // builder.InsertNode(ellipseShape);

        // 5️⃣ Group the shapes together
        GroupShape groupShape = new GroupShape(document);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        groupShape.WrapType = WrapType.Inline;

        // 6️⃣ Insert the grouped shape into the document
        builder.InsertNode(groupShape);

        // 7️⃣ Save the file
        document.Save("GroupShape.docx");

        System.Console.WriteLine("Document created successfully!");
    }
}
```

**Sortie attendue :** Lorsque vous ouvrirez `GroupShape.docx`, vous verrez un seul objet groupé composé d’un rectangle bleu clair et d’une ellipse corail clair, parfaitement alignés côte à côte.

---

## Récapitulatif

Nous venons de couvrir tout ce qu’il faut savoir pour **regrouper des formes dans Word** avec Aspose.Words :

1. Créez un document et un builder.  
2. **Ajoutez une forme rectangle** et **définissez une forme ellipse** avec des dimensions explicites.  
3. (Facultatif) **Insérez une forme dans Word** pour un aperçu rapide.  
4. Utilisez `GroupShape` pour **comment regrouper des formes** — ajoutez chaque enfant, définissez l’enveloppe, puis insérez.  
5. Enregistrez le fichier et vérifiez le

## Que devez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}