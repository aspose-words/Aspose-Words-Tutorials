---
category: general
date: 2026-10-23
description: Apprenez comment insérer une ellipse et comment ajouter une forme rectangulaire
  dans Word en utilisant Aspose.Words. Inclut le déplacement du curseur vers la forme
  et comment créer une forme groupée.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert ellipse
- how to add rectangle
- move cursor to shape
- insert rectangle shape word
- how to create group shape
language: fr
lastmod: 2026-10-23
og_description: Comment insérer une ellipse et comment ajouter une forme rectangulaire
  dans Word avec Aspose.Words. Suivez le guide étape par étape pour déplacer le curseur
  vers la forme et créer une forme groupée.
og_image_alt: Screenshot of a Word document showing a group shape containing a rectangle
  and an ellipse
og_title: Comment insérer des formes ellipse et rectangle dans un groupe de formes
  Word
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to insert ellipse and how to add rectangle shape in Word
    using Aspose.Words. Includes move cursor to shape and how to create group shape.
  headline: How to insert ellipse and rectangle shapes inside a group shape with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Comment insérer des formes ellipse et rectangle dans une forme groupée avec
  Aspose.Words
url: /fr/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment insérer des formes ellipse et rectangle à l'intérieur d'une forme groupée avec Aspose.Words

Si vous devez savoir **comment insérer une ellipse** dans un document Word de manière programmatique, ce guide montre le processus complet. Vous verrez également **comment ajouter une forme rectangle**, apprendrez à **déplacer le curseur vers la forme**, et découvrirez **comment créer une forme groupée** qui contient plusieurs objets de dessin.

L'automatisation de Word nécessite souvent un positionnement précis des objets de dessin. À la fin de ce tutoriel, vous pourrez générer un fichier `.docx` contenant un rectangle et une ellipse groupés, prêts pour un style supplémentaire ou une exportation. Aucun outil externe n'est requis au-delà de la bibliothèque Aspose.Words for .NET et d'un environnement de développement .NET.

## Prérequis

* .NET 6.0 ou version ultérieure installé.
* Aspose.Words for .NET (package NuGet `Aspose.Words`) ajouté à votre projet.
* Connaissances de base de la syntaxe C# et de Visual Studio (ou tout IDE).

Ces exigences garantissent que le code se compile sans configuration supplémentaire.

## Comment créer une forme groupée dans Word

Une forme groupée agit comme un conteneur qui vous permet de déplacer, faire pivoter ou formater plusieurs formes comme une seule unité. Le code suivant crée un groupe avec une taille spécifique (300 × 200 points) et prépare le document pour des opérations de dessin supplémentaires.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapeDemo
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a group shape that will act as a container for other shapes.
        GroupShape group = builder.InsertGroupShape(300, 200);
        
        // The group shape is now part of the document.
        // Subsequent shape insertions will be placed inside this group.
```

*Pourquoi cette étape est importante* : La forme groupée définit un système de coordonnées local. Toutes les formes ajoutées après avoir déplacé le curseur dans le groupe seront positionnées par rapport à l'origine du groupe, ce qui simplifie les calculs de mise en page.

## Comment ajouter une forme rectangle dans Word

Maintenant que le groupe existe, vous pouvez **insérer une forme rectangle** à l'intérieur. Le rectangle servira de fond ou d'espace réservé visuel pour d'autres contenus.

```csharp
        // Move the cursor into the group so that the next shape is added to it.
        builder.MoveTo(group);
        
        // Insert a rectangle of width 100 points and height 50 points.
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

*Explication* : `MoveTo(group)` indique au constructeur que le point d'insertion actif est la forme groupée. Sans déplacer le curseur, `InsertShape` ajouterait le rectangle au corps principal du document au lieu du groupe.

## Comment insérer une ellipse

Avec le rectangle en place, vous pouvez maintenant démontrer **comment insérer une ellipse**. L'ellipse sera centrée dans le même groupe, se superposant au rectangle si désiré.

```csharp
        // Keep the cursor inside the same group.
        builder.MoveTo(group);
        
        // Insert an ellipse of width 80 points and height 80 points.
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

*Pourquoi le curseur doit être déplacé* : Chaque appel à `InsertShape` respecte la position actuelle du curseur. Rappeler `MoveTo(group)` garantit que l'ellipse est également un enfant du groupe, préservant la hiérarchie prévue.

## Déplacer le curseur vers la forme avant d'insérer des objets supplémentaires

Si vous devez ajouter d'autres formes plus tard, déplacez toujours **le curseur vers la forme** avant chaque insertion. Ce modèle évite un placement accidentel en dehors du groupe.

```csharp
        // Example: add a third shape, such as a line.
        builder.MoveTo(group);
        builder.InsertShape(ShapeType.Line, 150, 0);
```

*Astuce* : Réutiliser `MoveTo(group)` est peu coûteux et améliore la lisibilité du code. Cela facilite également la maintenance future car le contexte d'insertion est explicite.

## Enregistrer le document

Enfin, persistez le document sur le disque. L'exemple enregistre le fichier sous le nom `GroupShape.docx` dans le dossier que vous spécifiez.

```csharp
        // Save the document to the desired location.
        document.Save(@"C:\Temp\GroupShape.docx");
    }
}
```

Lorsque vous ouvrez le fichier enregistré dans Microsoft Word, vous verrez un seul groupe contenant un rectangle et une ellipse, tous deux correctement positionnés.

### Résultat attendu

* Un fichier `.docx` nommé `GroupShape.docx`.
* Dans le document, un objet de dessin groupé de taille 300 × 200 points.
* À l'intérieur du groupe :
  * Un rectangle (100 × 50 points) situé à l'origine du groupe.
  * Une ellipse (80 × 80 points) se superposant au rectangle.
  * Toutes les formes supplémentaires que vous avez ajoutées après avoir déplacé le curseur.

## Variations courantes et cas limites

| Situation | Approche recommandée |
|-----------|----------------------|
| **Différentes tailles d'unité** | Aspose.Words utilise des points (1 pt = 1/72 in). Convertissez les centimètres ou pouces en points avant d'appeler `InsertShape`. |
| **Faire pivoter des formes à l'intérieur du groupe** | Après avoir inséré une forme, récupérez son objet `ShapeBase` et définissez `ShapeBase.RotationAngle`. |
| **Ajouter du texte à l'intérieur d'une forme** | Utilisez `ShapeBase.AppendChild(new Paragraph(document))` puis ajoutez un `Run` avec le texte souhaité. |
| **Enregistrer en PDF au lieu de DOCX** | Appelez `document.Save("GroupShape.pdf", SaveFormat.Pdf);` – la hiérarchie du groupe est préservée dans la sortie PDF. |

Ces variations démontrent que la même logique **comment insérer une ellipse** peut être adaptée à de nombreux scénarios réels.

## Astuces professionnelles

* **Réutilisez la même instance de `DocumentBuilder`** – cela réduit la charge mémoire et maintient l'état du document cohérent.
* **Validez les dimensions des formes** – des largeurs ou hauteurs extrêmement grandes peuvent provoquer des problèmes de rendu dans les anciennes versions de Word.
* **Groupez avant le style** – appliquer des couleurs de remplissage ou des styles de ligne au groupe après avoir ajouté tous les enfants garantit une apparence uniforme.

## Conclusion

Vous comprenez maintenant **comment insérer une ellipse** et **comment ajouter une forme rectangle** à l'intérieur d'un conteneur groupé dans un document Word en utilisant Aspose.Words. En déplaçant systématiquement **le curseur vers la forme** avant chaque insertion, vous maintenez une hiérarchie propre et évitez les placements accidentels. L'exemple complet compile, s'exécute et produit une forme groupée qui peut être personnalisée davantage ou exportée.

Prêt à explorer davantage ? Essayez de combiner cette technique avec **comment créer une forme groupée** pour des diagrammes complexes, ou expérimentez **insérer une forme rectangle dans Word** avec des zones de texte pour une génération de rapports riche. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Comment créer une forme rectangle et des formes groupées dans Word avec Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)
- [Comment créer un document Word vierge et ajouter une forme ellipse cachée en C#](/words/english/java/images-shapes/how-to-create-blank-word-document-and-add-a-hidden-ellipse-s/)
- [Comment créer un docx avec forme groupée et ajouter des contrôles interactifs en C#](/words/english/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}