---
category: general
date: 2026-09-08
description: Apprenez à créer un document Word vierge, insérer une forme rectangle
  et regrouper plusieurs formes en utilisant C#. Suivez ce guide étape par étape.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert rectangle shape
- group multiple shapes
- add shapes to group
language: fr
lastmod: 2026-09-08
og_description: Créez un document Word vierge, insérez une forme rectangulaire et
  regroupez plusieurs formes en C#. Ce tutoriel vous guide à travers le processus
  complet.
og_image_alt: Screenshot showing a blank Word document with a grouped rectangle and
  ellipse shape
og_title: Créer un document Word vierge avec des formes groupées en C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to create blank Word document, insert rectangle shape and
    group multiple shapes using C#. Follow this step‑by‑step guide.
  headline: How to create blank Word document with grouped shapes
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Comment créer un document Word vierge avec des formes groupées
url: /fr/java/images-shapes/how-to-create-blank-word-document-with-grouped-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer un document Word vierge avec des formes groupées

Si vous avez besoin de **créer un document Word vierge** contenant des graphiques personnalisés, ce guide vous montre exactement comment faire. Vous apprendrez à **insérer une forme rectangulaire**, **regrouper plusieurs formes**, et **ajouter des formes au groupe** en utilisant Aspose.Words for .NET.

Un document vierge vous offre une toile propre, et le regroupement des formes vous permet de les déplacer, redimensionner ou faire pivoter comme une seule unité. Ce tutoriel couvre chaque étape — de l'initialisation du document à l'enregistrement du fichier final — afin que vous puissiez copier le code dans votre propre projet et voir les résultats immédiatement.

## Ce dont vous avez besoin

Avant de commencer, assurez-vous d'avoir :

* .NET 6.0 ou ultérieur (le code fonctionne également avec .NET Framework 4.6+)
* Une licence valide d'Aspose.Words for .NET (l'évaluation gratuite fonctionne pour les tests)
* Un IDE tel que Visual Studio 2022 ou Visual Studio Code
* Une connaissance de base de la syntaxe C#

## Comment créer un document Word vierge

La première étape consiste à instancier un objet `Document`. Cet objet représente un fichier `.docx` vide que vous pouvez modifier avec un `DocumentBuilder`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document and a builder to edit it.
            Document doc = new Document();               // Blank Word document
            DocumentBuilder builder = new DocumentBuilder(doc);
```

Le constructeur `Document` crée un **document Word vierge** en mémoire. Le `DocumentBuilder` fournit une API fluide pour insérer du texte, des images et des objets de dessin.

## Insérer une forme rectangulaire dans le document

Ensuite, ajoutez une forme rectangulaire. Le rectangle sera le premier enfant du groupe que nous créerons plus tard.

```csharp
            // Step 2: Insert a rectangle shape (100 pt wide, 50 pt high).
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            // Optional: give the rectangle a fill color for visibility.
            rectangle.FillColor = System.Drawing.Color.LightBlue;
```

Appeler `InsertShape` avec `ShapeType.Rectangle` **insère une forme rectangulaire** à la position actuelle du curseur. La largeur et la hauteur sont exprimées en points (1 pt ≈ 1/72 in).

## Regrouper plusieurs formes ensemble

Un `GroupShape` agit comme un conteneur. Toutes les formes enfants à l'intérieur du groupe se déplacent et se transforment ensemble. D'abord, créez le groupe, puis ajoutez le rectangle que nous venons de créer.

```csharp
            // Step 3: Create a group shape that will hold multiple child shapes.
            GroupShape group = builder.InsertGroupShape();
            // Append the rectangle as the first child of the group.
            group.AppendChild(rectangle);
```

La méthode `InsertGroupShape` place un groupe vide au curseur du builder. En ajoutant le rectangle, nous **regroupons plusieurs formes** — le rectangle devient partie de la collection interne de nœuds du groupe.

## Ajouter des formes au groupe et enregistrer le fichier

Ajoutez maintenant une deuxième forme — une ellipse — pour démontrer comment plusieurs objets partagent le même conteneur. Ensuite, enregistrez le document.

```csharp
            // Step 4: Insert an ellipse shape (80 pt wide, 80 pt high).
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;

            // Append the ellipse to the same group.
            group.AppendChild(ellipse);

            // Step 5: Save the document containing the grouped shapes.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

L'appel `InsertShape` **ajoute des formes au groupe** lorsque vous ajoutez le `Shape` retourné au `GroupShape`. En enregistrant le `Document`, on écrit un fichier `.docx` que vous pouvez ouvrir avec Microsoft Word, LibreOffice ou tout visualiseur compatible.

### Résultat attendu

Lorsque vous ouvrez *GroupShapeDemo.docx*, vous verrez une page blanche contenant un objet groupé qui comprend un rectangle bleu clair et une ellipse rose. Sélectionner le groupe vous permet de déplacer les deux formes ensemble, confirmant que **regrouper plusieurs formes** a fonctionné comme prévu.

## Pourquoi utiliser un GroupShape ?

* **Transformations atomiques** – Redimensionner, faire pivoter ou déplacer le groupe affecte tous les enfants de manière uniforme.
* **Organisation logique** – Garde les graphiques liés ensemble, facilitant la maintenance de la structure du document.
* **Performance** – Rendre un seul conteneur est souvent plus rapide que de gérer de nombreuses formes indépendantes.

Si vous devez modifier un enfant unique plus tard, vous pouvez le récupérer depuis `group.ChildNodes` par indice ou par sa propriété `Name`.

## Variantes courantes et cas limites

| Scénario                                 | Comment adapter le code                                                            |
|------------------------------------------|------------------------------------------------------------------------------------|
| **Différents types de formes**                | Remplacez `ShapeType.Rectangle` ou `ShapeType.Ellipse` par tout autre `ShapeType` |
| **Ajout de texte à l'intérieur d'une forme**           | Utilisez `Shape.TextPath.Text = "Hello"` après avoir inséré la forme                    |
| **Définir un angle de rotation**             | `group.Rotation = 45;` (degrees)                                                 |
| **Enregistrement au format PDF au lieu de DOCX**        | `doc.Save("GroupShapeDemo.pdf");`                                                |
| **Appliquer une bordure au groupe**       | `group.LineStyle = LineStyle.Single;`<br>`group.LineWidth = 1.5;`               |

## Astuces pro

* **Nommez vos formes** – `rectangle.Name = "MyRect";` facilite leur localisation ultérieure.
* **Utilisez le positionnement relatif** – Définissez `group.RelativeHorizontalPosition` sur `RelativeHorizontalPosition.Page` si vous souhaitez que le groupe reste ancré aux marges de la page.
* **Libérez les ressources** – Encapsulez le `Document` dans un bloc `using` lorsque vous travaillez dans des applications plus importantes afin de libérer rapidement la mémoire non gérée.

## Code source complet pour copier‑coller rapidement

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document and a builder to edit it.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a rectangle shape (100 pt × 50 pt) and give it a light‑blue fill.
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // Create a group shape and add the rectangle as its first child.
            GroupShape group = builder.InsertGroupShape();
            group.AppendChild(rectangle);

            // Insert an ellipse shape (80 pt × 80 pt) with a pink fill.
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;
            group.AppendChild(ellipse);

            // Save the document. The file will contain the grouped rectangle and ellipse.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Copiez le code dans un nouveau projet console, restaurez le paquet NuGet `Aspose.Words`, puis exécutez. Le fichier de sortie apparaît dans le dossier `bin/Debug/net6.0` du projet (ou équivalent).

## Étapes suivantes

Maintenant que vous pouvez **créer un document Word vierge**, **insérer une forme rectangulaire**, et **regrouper plusieurs formes**, vous pourriez explorer :

* Ajouter des **zones de texte** à l'intérieur d'un groupe pour créer des diagrammes annotés.
* Exporter le graphique groupé en image avec `doc.Save("image.png", SaveFormat.Png)`.
* Combiner des groupes avec des tableaux pour des rapports richement formatés.

Expérimentez avec différentes propriétés de forme, hiérarchies de groupes et formats d'exportation pour exploiter pleinement les capacités de dessin d'Aspose.Words.

--- 

*Rappel* : regrouper les formes est un moyen puissant de garder vos documents Word ordonnés et votre code maintenable. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Créer une forme rectangulaire dans Word avec C# – Guide étape par étape](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Insérer des formes dans des documents Word avec Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Créer une forme groupée dans un document Word avec Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}