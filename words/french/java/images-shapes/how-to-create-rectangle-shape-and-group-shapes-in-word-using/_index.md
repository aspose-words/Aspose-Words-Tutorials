---
category: general
date: 2026-11-18
description: Apprenez à créer une forme rectangulaire dans un document Word avec C#.
  Le guide couvre également la définition de la taille de la forme, la définition
  de la position de la forme et le regroupement des formes dans Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- set shape size
- group shapes in word
- set shape dimensions
- set shape position
language: fr
lastmod: 2026-11-18
og_description: Créer une forme rectangulaire dans un fichier Word en utilisant C#
  et apprendre à définir les dimensions de la forme, à définir sa position et à regrouper
  les formes dans Word.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape created with C#
og_title: Créer une forme rectangulaire et regrouper des formes dans Word avec C#
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  headline: How to create rectangle shape and group shapes in Word using C#
  type: TechArticle
- description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  name: How to create rectangle shape and group shapes in Word using C#
  steps:
  - name: Initialize the document and builder
    text: '```csharp using System; using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert a group shape
    text: '```csharp // Step 2: Insert a group shape that will hold multiple child
      shapes GroupShape group = builder.InsertGroupShape(); ```'
  - name: Create the rectangle and set its size
    text: '```csharp // Step 3: Create a rectangle shape, set its size, and add it
      to the group Shape rectangle = new Shape(doc, ShapeType.Rectangle); rectangle.Width
      = 100; // set shape size (width) in points rectangle.Height = 50; // set shape
      size (height) in points group.AppendChild(rectangle); ```'
  - name: Create the ellipse, set dimensions, and position it
    text: '```csharp // Step 4: Create an ellipse shape, set its size and position,
      and add it to the group Shape ellipse = new Shape(doc, ShapeType.Ellipse); ellipse.Width
      = 80; // set shape dimensions (width) ellipse.Height = 80; // set shape dimensions
      (height) ellipse.Left = 120; // set shape position rela'
  - name: Save the document
    text: '```csharp // Step 5: Save the document containing the grouped shapes doc.Save("GroupShape.docx");
      Console.WriteLine("Document saved successfully."); } } ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Comment créer une forme rectangle et regrouper des formes dans Word avec C#
url: /fr/java/images-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-using/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer une forme rectangulaire et regrouper des formes dans Word avec C#

Si vous devez **create rectangle shape** dans un document Word, ce tutoriel vous montre une solution complète, prête à l'exécution. Vous verrez comment définir la taille de la forme, définir la position de la forme, et regrouper des formes dans Word afin qu'elles se comportent comme un seul objet.

Travailler avec des formes est une exigence courante lors de la génération de rapports, factures ou diagrammes de manière programmatique. À la fin de ce guide, vous serez capable de générer un fichier `.docx` contenant un rectangle, une ellipse et un conteneur groupé — tous créés avec Aspose.Words for .NET.

## Prérequis

- .NET 6.0 SDK ou version ultérieure (le code fonctionne également avec .NET Framework 4.7+)
- Package NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)
- Un éditeur de code ou un IDE (Visual Studio, VS Code, Rider, etc.)

Aucune bibliothèque supplémentaire n'est requise.

## Comment créer une forme rectangulaire et regrouper des formes dans Word

Les étapes principales sont :

1. **Create a blank document** et un `DocumentBuilder`.
2. **Insert a `GroupShape`** qui contiendra les formes individuelles.
3. **Create a rectangle shape**, définissez ses dimensions et ajoutez‑la au groupe.
4. **Create an ellipse shape**, définissez sa taille et sa position, et ajoutez‑la au groupe.
5. **Save** le document.

Chaque étape est expliquée ci‑dessous, et le code source complet suit l'explication.

### Étape 1 : Initialiser le document et le builder

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` représente le fichier Word complet, tandis que `DocumentBuilder` fournit une API fluide pour insérer du contenu. Les initialiser est obligatoire avant de pouvoir ajouter des formes.

### Étape 2 : Insérer une forme groupée

```csharp
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape group = builder.InsertGroupShape();
```

Un `GroupShape` fonctionne comme un conteneur ; toutes les formes enfants se déplacent ensemble. C’est la méthode recommandée pour **group shapes in Word** lorsque vous avez besoin de transformations collectives (par ex., déplacer, faire pivoter ou supprimer).

### Étape 3 : Créer le rectangle et définir sa taille

```csharp
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle);
```

Ici nous **create rectangle shape** et **set shape size** en assignant `Width` et `Height`. Dans Aspose.Words, les tailles sont exprimées en points (1 pt ≈ 1/72 in). Définir explicitement les dimensions garantit que le rectangle apparaît exactement comme prévu.

### Étape 4 : Créer l'ellipse, définir les dimensions et la positionner

```csharp
        // Step 4: Create an ellipse shape, set its size and position, and add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position relative to the group
        group.AppendChild(ellipse);
```

Les **set shape dimensions** de l'ellipse sont identiques pour la largeur et la hauteur, produisant un cercle parfait. La propriété `Left` illustre **set shape position** : l'ellipse commence à 120 pt à droite de l'origine du groupe, de sorte qu'elle ne chevauche pas le rectangle.

### Étape 5 : Enregistrer le document

```csharp
        // Step 5: Save the document containing the grouped shapes
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document saved successfully.");
    }
}
```

L'enregistrement écrit le fichier Word sur le disque. Vous pouvez ouvrir `GroupShape.docx` dans Microsoft Word pour vérifier que le rectangle et l'ellipse sont groupés et positionnés correctement.

## Définir les dimensions et la taille d'une forme – examen approfondi

- **Points vs. inches** : 72 pt = 1 in. Si vous préférez les pouces, multipliez par 72 (par ex., `2.5 * 72` pour 2,5 in).
- **Automatic scaling** : Si vous omettez `Width` ou `Height`, la forme utilise sa taille par défaut. Définissez explicitement **set shape size** pour éviter les surprises de mise en page.
- **Aspect ratio** : Pour des formes comme `Ellipse`, garder `Width` et `Height` égaux maintient une apparence circulaire.

## Positionner une forme dans Word

Les propriétés `Left` et `Top` contrôlent le décalage de la forme à l'intérieur de son conteneur (le groupe ou la page). Les valeurs positives déplacent la forme vers la droite/bas ; les valeurs négatives la déplacent vers la gauche/haut. Lors du groupement, les positions sont relatives à l'origine du groupe, ce qui simplifie les calculs de mise en page.

## Regrouper des formes dans Word avec Aspose.Words

Le groupement est essentiel lorsque vous voulez que plusieurs formes agissent comme une seule unité. L'objet `GroupShape` :

- Prend en charge `AppendChild` pour ajouter n'importe quel `Shape` (rectangle, ellipse, image, etc.).
- Vous permet de déplacer, faire pivoter ou supprimer tout le groupe avec un seul appel.
- Conserve les positions des formes enfants relatives au groupe, ce qui rend les diagrammes complexes plus faciles à gérer.

**Astuce :** Après avoir ajouté toutes les formes enfants, vous pouvez ajuster le `Width`, le `Height`, le `Left` et le `Top` du groupe pour repositionner l'ensemble de la collection en une seule étape.

## Exemple complet exécutable

Voici le programme complet que vous pouvez copier, coller et exécuter. Il inclut toutes les directives `using`, une méthode `Main`, et des commentaires qui expliquent chaque ligne.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a GroupShape to hold child shapes
        GroupShape group = builder.InsertGroupShape();

        // 3️⃣ Create a rectangle, set its dimensions, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle); // add rectangle to the group

        // 4️⃣ Create an ellipse, set size and position, then add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position inside the group
        group.AppendChild(ellipse); // add ellipse to the group

        // 5️⃣ Save the document
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document 'GroupShape.docx' created with a rectangle and an ellipse grouped together.");
    }
}
```

**Résultat attendu** : après l'exécution du programme, `GroupShape.docx` apparaît dans le dossier d'exécution. L'ouvrir dans Word montre un rectangle (100 pt × 50 pt) à gauche et une ellipse (80 pt × 80 pt) positionnée à 120 pt à droite, les deux à l'intérieur d'un même objet groupé.

![Word document with grouped rectangle and ellipse](grouped_shapes.png){: .center alt="Capture d'écran d'un document Word montrant une forme rectangulaire et une ellipse groupées créées avec C#" }

*L'image ci‑dessus illustre le résultat final ; le rectangle et l'ellipse sont sélectionnables comme un seul groupe.*

## Questions fréquentes et cas particuliers

| Question | Réponse |
|----------|--------|
| **Puis-je ajouter plus de deux formes ?** | Oui. Appelez `group.AppendChild(yourShape)` pour chaque forme supplémentaire. |
| **Et si je dois faire pivoter le groupe ?** | Utilisez `group.RotationAngle = 45;` (degrés) après avoir ajouté tous les enfants. |
| **Comment changer la couleur d'arrière‑plan du groupe ?** | Définissez `group.FillColor = System.Drawing.Color.LightGray;`. |
| **Cela fonctionnera‑t‑il avec les fichiers .doc ?** | Aspose.Words prend en charge les fichiers `.doc` et `.docx`. Le même code fonctionne ; il suffit de changer l'extension du fichier dans `Save`. |
| **Y a‑t‑il un impact mémoire lors du groupement de nombreuses formes ?** | Le groupement lui‑même ajoute un overhead minimal. La principale préoccupation est le nombre total de formes ; gardez‑le raisonnable pour les documents volumineux. |

## Conclusion

Dans ce tutoriel vous avez appris comment **create rectangle shape** dans un fichier Word avec C#, comment **set shape size**, **set shape dimensions**, **set shape position**, et enfin comment **group shapes in Word** avec Aspose.Words. L'exemple complet montre une approche claire et maintenable que vous pouvez étendre à des diagrammes, graphiques ou graphiques personnalisés plus complexes.

Ensuite, vous pourriez explorer :

- Ajouter du texte à l'intérieur des formes (`Shape.TextPath.Text = "Hello"`).
- Insérer des images dans un `GroupShape`.
- Exporter les formes groupées en PDF avec `doc.Save("output.pdf")`.

N'hésitez pas à expérimenter avec différentes tailles, positions et types de formes supplémentaires pour répondre aux besoins de votre projet. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Créer une forme groupée dans un document Word en utilisant Aspose.Words pour .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}