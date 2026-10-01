---
category: general
date: 2026-09-30
description: Créer un document vierge et insérer une forme rectangulaire, une ellipse,
  puis regrouper plusieurs formes en C# avec Aspose.Words. Apprenez comment insérer
  des formes et comment créer un groupe.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- insert rectangle shape
- group multiple shapes
- how to insert shapes
- how to create group
language: fr
lastmod: 2026-09-30
og_description: Créez un document vierge en C# et apprenez à insérer des formes et
  à regrouper plusieurs formes avec Aspose.Words. Suivez le tutoriel étape par étape.
og_image_alt: Screenshot of a C# program that creates a blank document, inserts a
  rectangle and ellipse, and groups them together.
og_title: Créer un document vierge et regrouper des formes en C# – Guide Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Create blank document and insert rectangle shape, ellipse, and group
    multiple shapes in C# using Aspose.Words. Learn how to insert shapes and how to
    create group.
  headline: How to create blank document and add shapes with Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- document automation
- shapes
title: Comment créer un document vierge et ajouter des formes avec Aspose.Words en
  C#
url: /fr/java/images-shapes/how-to-create-blank-document-and-add-shapes-with-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer un document vierge et ajouter des formes avec Aspose.Words en C#

Si vous devez **créer un document vierge** et le remplir avec des graphiques, ce guide vous montre exactement comment faire. Vous verrez comment **insérer une forme rectangle**, ajouter d’autres objets de dessin, puis **regrouper plusieurs formes** afin qu’elles se comportent comme une seule unité.

Travailler avec des formes est une exigence courante lors de la génération de contrats, de certificats ou de rapports personnalisés. Dans ce tutoriel, vous apprendrez le flux de travail complet, depuis l’initialisation du document jusqu’à l’enregistrement du fichier final, en utilisant l’API Aspose.Words pour .NET.

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

* SDK .NET 6.0 (ou version ultérieure) installé  
* Une licence valide d’Aspose.Words pour .NET (l’essai gratuit fonctionne pour cet exemple)  
* Un IDE tel que Visual Studio 2022 ou Visual Studio Code  

Aucun package NuGet supplémentaire n’est requis au‑delà de `Aspose.Words`.

## Comment créer un document vierge et travailler avec des formes

La première étape consiste à instancier un objet `Document`. Cet objet représente le fichier Word en mémoire et vous donne accès au `DocumentBuilder`, qui est l’outil principal pour insérer du contenu.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Pourquoi c’est important :** Un document vierge vous offre une toile propre. Le `DocumentBuilder` maintient le point d’insertion actuel, de sorte que chaque forme que vous ajoutez est automatiquement placée sur la page appropriée.

## Insérer une forme rectangle et d’autres formes

Ensuite, nous ajoutons un rectangle et une ellipse. Les deux appels utilisent la même méthode `InsertShape`, qui est la façon recommandée **d’insérer des formes** dans Aspose.Words.

```csharp
        // Step 2: Insert a rectangle shape (100 × 50 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;   // optional styling
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Insert an ellipse shape (80 × 80 points)
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;
```

*La méthode `InsertShape` positionne automatiquement la forme à l’emplacement du curseur actuel.* Si vous avez besoin d’un placement précis, vous pouvez ajuster `Shape.Left` et `Shape.Top` après l’insertion.

## Regrouper plusieurs formes en un seul objet

Nous combinons maintenant le rectangle et l’ellipse en une entité logique unique. Le regroupement est utile lorsque vous souhaitez déplacer ou redimensionner plusieurs formes ensemble.

```csharp
        // Step 4: Create a group shape that will hold multiple shapes
        GroupShape groupShape = builder.InsertGroupShape();

        // Step 5: Add the rectangle and ellipse to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional: Apply a border to the whole group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;
```

**Comment cela fonctionne :** `InsertGroupShape` crée un conteneur qui se comporte comme n’importe quelle autre `Shape`. En appelant `AppendChild`, vous déplacez les formes existantes dans le conteneur, qui met automatiquement à jour leurs coordonnées relatives.

### Astuce pratique

Si vous devez plus tard **créer un groupe** de façon programmatique pour plus de deux formes, répétez simplement `AppendChild` pour chaque instance supplémentaire de `Shape`. Le groupe peut contenir n’importe quel nombre d’objets de dessin, y compris des images, des zones de texte ou même d’autres groupes.

## Exemple complet – comment insérer des formes et enregistrer le document

Voici le programme complet et exécutable qui démontre chaque étape abordée jusqu’à présent. L’exécution du code produit un fichier `ShapesDemo.docx` contenant un rectangle, une ellipse et une forme groupée.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Insert rectangle shape
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // 3. Insert ellipse shape
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;

        // 4. Create a group shape
        GroupShape groupShape = builder.InsertGroupShape();

        // 5. Add shapes to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional styling for the group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;

        // 6. Save the document
        string outputPath = "ShapesDemo.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Résultat attendu :** L’ouverture de `ShapesDemo.docx` dans Microsoft Word affiche une seule page avec un rectangle bleu, une ellipse verte et une bordure grise entourant le groupe. Déplacer le groupe déplace les deux formes simultanément, confirmant que l’opération **regrouper plusieurs formes** a réussi.

## Questions fréquentes et gestion des cas particuliers

| Question | Réponse |
|----------|---------|
| *Et si j’ai besoin des formes sur une page spécifique ?* | Appelez `builder.MoveToDocumentEnd();` avant d’insérer les formes, ou utilisez `builder.MoveToSection(sectionIndex);` pour cibler une section particulière. |
| *Puis‑je ajouter du texte à l’intérieur d’une forme groupée ?* | Oui. Créez une `Shape` de type `ShapeType.TextBox`, configurez son texte, puis `AppendChild` à la `GroupShape`. |
| *Les dimensions des formes utilisent‑elles des points ou des pixels ?* | Aspose.Words utilise des **points** (1 pt = 1/72 pouce). Cela garantit une taille cohérente sur les imprimantes et les écrans. |
| *Comment modifier la rotation du groupe ?* | Définissez `groupShape.RotationAngle = 45;` (degrés). Toutes les formes enfants tournent autour de l’origine du groupe. |

## Conclusion

Vous savez maintenant comment **créer un document vierge**, **insérer une forme rectangle**, **insérer des formes** comme des ellipses, et **regrouper plusieurs formes** en un seul objet en utilisant Aspose.Words pour .NET. L’exemple complet de code montre l’approche recommandée, et les astuces ci‑dessus vous aident à adapter la solution à des scénarios plus complexes, tels que l’ajout de zones de texte ou la rotation de groupes.

Prêt à explorer davantage ? Essayez d’ajouter une forme image au groupe, expérimentez différentes couleurs de remplissage, ou générez un rapport multi‑pages où chaque page contient son propre diagramme groupé. Les mêmes principes s’appliquent, vous permettant d’étendre ce modèle à tout projet d’automatisation de documents.

## Que devez‑vous apprendre ensuite ?


Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Créer une forme groupée dans un document Word avec Aspose.Words pour .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insérer des formes dans des documents Word avec Aspose.Words pour .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Créer un document Word vierge avec Aspose.Words – Guide étape par étape](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}