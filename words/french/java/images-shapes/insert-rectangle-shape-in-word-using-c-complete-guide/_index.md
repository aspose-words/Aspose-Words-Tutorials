---
category: general
date: 2026-08-04
description: Insérer une forme rectangulaire dans un document Word avec C#. Apprenez
  à regrouper des formes dans Word, à enregistrer le document au format docx et à
  utiliser DocumentBuilder pour des mises en page avancées.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to group shapes
- group shapes in word
- save document as docx
- how to use builder
language: fr
lastmod: 2026-08-04
og_description: Insérez une forme rectangulaire dans un fichier Word en utilisant
  C# puis regroupez les formes pour des mises en page avancées. Ce tutoriel couvre
  également l’enregistrement du document au format docx et l’utilisation efficace
  de DocumentBuilder.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with C# DocumentBuilder
og_title: Insérer une forme rectangulaire dans Word – Guide pas à pas en C#
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Insert rectangle shape in a Word document with C#. Learn how to group
    shapes in Word, save document as docx, and use DocumentBuilder for advanced layouts.
  headline: Insert rectangle shape in Word using C# – complete guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Insérer une forme rectangulaire dans Word avec C# – guide complet
url: /fr/java/images-shapes/insert-rectangle-shape-in-word-using-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insérer une forme rectangulaire dans Word avec C# – guide complet

Si vous devez **insérer une forme rectangulaire** dans un document Word en utilisant C#, ce tutoriel vous montre exactement comment faire. Vous apprendrez également **comment regrouper des formes** dans Word, **enregistrer le document au format docx**, et **comment utiliser Builder** pour un code propre et maintenable.

Travailler avec des formes est une exigence courante lors de la génération de rapports, de certificats ou de mises en page personnalisées de façon programmatique. À la fin de ce guide, vous disposerez d’un exemple complet et exécutable qui crée un rectangle, ajoute une ellipse, les regroupe, puis enregistre le résultat sous forme de fichier DOCX.

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

* .NET 6.0 ou version ultérieure installé  
* Visual Studio 2022 (ou tout IDE supportant C#)  
* La bibliothèque **Aspose.Words for .NET** (disponible via NuGet)  

Vous pouvez ajouter la bibliothèque avec la commande suivante :

```bash
dotnet add package Aspose.Words
```

## Insérer une forme rectangulaire avec DocumentBuilder

La première étape consiste à créer un nouveau `Document` et un `DocumentBuilder`. Le builder vous offre une API fluide pour insérer du contenu, y compris des formes.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document.
        Document document = new Document();

        // Initialize the builder that will edit the document.
        DocumentBuilder builder = new DocumentBuilder(document);
```

L’instance `DocumentBuilder` est l’objet central que vous utiliserez pour **insérer une forme rectangulaire** et d’autres éléments. Elle suit la position actuelle du curseur dans le document, de sorte que toute insertion se fait exactement à l’endroit souhaité.

## Comment insérer une forme rectangulaire

Une fois le builder prêt, appelez `InsertShape`. Vous spécifiez le `ShapeType`, la largeur et la hauteur en points (1 pt ≈ 1/72 in).

```csharp
        // Insert a rectangle of 100 pt width and 50 pt height.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
```

*Pourquoi c’est important* : définir `FillColor` et `StrokeColor` rend le rectangle visuellement distinct, ce qui facilite son regroupement ultérieur avec d’autres formes.

## Comment regrouper des formes dans Word

Regrouper des formes vous permet de déplacer, faire pivoter ou formater plusieurs objets comme une seule entité. Après avoir inséré le rectangle, ajoutez une autre forme (une ellipse dans cet exemple) puis créez un `GroupShape`.

```csharp
        // Insert an ellipse of 80 pt diameter.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // Insert an empty group container.
        GroupShape groupShape = builder.InsertGroupShape();

        // Add the rectangle and ellipse to the group.
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
```

L’appel `InsertGroupShape` crée un espace réservé pouvant contenir un nombre quelconque de formes enfants. En ajoutant le rectangle et l’ellipse, vous **regroupez les formes dans Word**. Le groupe se comporte comme une forme unique : vous pouvez le repositionner, appliquer une bordure ou le redimensionner sans affecter la disposition interne de chaque enfant.

### Astuce

Après le regroupement, vous pouvez modifier la position du groupe par rapport à la page :

```csharp
        // Move the whole group 150 pt right and 100 pt down.
        groupShape.Left = 150;
        groupShape.Top = 100;
```

## Enregistrer le document au format docx

Une fois les formes disposées, il faut persister le fichier. La méthode `Document.Save` détermine automatiquement le format à partir de l’extension du fichier. Pour **enregistrer le document au format docx**, fournissez un chemin se terminant par `.docx`.

```csharp
        // Save the document to the output folder.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

L’exécution du programme crée `output.docx`. Ouvrez le fichier dans Microsoft Word et vous verrez un rectangle bleu clair et une ellipse corail clair regroupés. Vous pouvez cliquer sur le groupe et le déplacer comme un seul objet.

## Comment utiliser DocumentBuilder efficacement

`DocumentBuilder` est plus qu’un simple inserteur de formes ; il gère également le texte, les tableaux, les en‑têtes et les pieds de page. Lorsque vous combinez la création de formes avec du texte, pensez à réinitialiser le curseur si vous devez insérer du contenu ailleurs :

```csharp
        // Move the cursor to a new paragraph after the group.
        builder.Writeln(); // Inserts a line break.
        builder.Font.Size = 12;
        builder.Writeln("Shapes have been added and grouped successfully.");
```

Garder l’état du builder explicite évite les écrasements accidentels et rend le code plus facile à maintenir.

## Cas limites et variantes

| Situation | Approche recommandée |
|-----------|----------------------|
| **Plus de deux formes** | Insérez chaque forme, puis appelez `AppendChild` pour chaque forme avant d’enregistrer. |
| **Groupes imbriqués** | Créez un groupe, ajoutez des formes, puis insérez ce groupe dans un autre `GroupShape`. |
| **Unités de mesure différentes** | Utilisez `builder.ConvertPixelsToPoints` si vous avez des dimensions en pixels. |
| **Compatibilité avec les versions plus anciennes de Word** | Enregistrez en `.doc` en changeant l’extension ; la plupart des fonctionnalités de forme fonctionnent toujours. |

## Exemple complet fonctionnel

Voici le programme complet que vous pouvez copier‑coller dans un nouveau projet console. Aucun extrait supplémentaire n’est requis.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;

        // 3️⃣ Insert an ellipse shape.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // 4️⃣ Create a group shape and add both shapes.
        GroupShape groupShape = builder.InsertGroupShape();
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Optional: reposition the group.
        groupShape.Left = 150;
        groupShape.Top = 100;

        // 5️⃣ Add a caption below the group.
        builder.Writeln();
        builder.Font.Size = 12;
        builder.Writeln("Grouped rectangle and ellipse created with DocumentBuilder.");

        // 6️⃣ Save the document as DOCX.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

**Résultat attendu** : l’ouverture de `output.docx` montre un rectangle bleu clair et une ellipse corail clair regroupés, positionnés à 150 pt du bord gauche et à 100 pt du haut. La légende apparaît sous le groupe.

## Conclusion

Vous savez maintenant comment **insérer une forme rectangulaire** dans un fichier Word avec C#, **regrouper des formes dans Word**, et **enregistrer le document au format docx** avec le `DocumentBuilder` d’Aspose.Words. En maîtrisant ces étapes, vous pouvez créer des mises en page complexes — certificats, rapports ou formulaires personnalisés — entièrement via le code.

Ensuite, explorez des sujets connexes tels que **l’ajout de zones de texte**, **le travail avec les tableaux**, ou **l’exportation en PDF**. Chacun de ces sujets s’appuie sur les mêmes fondamentaux du `DocumentBuilder` que vous venez de pratiquer.

Prêt à automatiser vos documents Word ? Essayez d’étendre l’exemple avec davantage de formes, d’appliquer des dégradés, ou de boucler sur des données pour générer un rapport complet en une seule exécution. Bon codage !

## Que devez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}