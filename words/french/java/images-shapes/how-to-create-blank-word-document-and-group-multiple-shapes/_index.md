---
category: general
date: 2026-10-26
description: Créez un document Word vierge en C# et apprenez à insérer une forme groupée,
  puis ajoutez une forme rectangle au groupe. Ce guide explique comment regrouper
  plusieurs formes pas à pas.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group multiple shapes
- insert rectangle shape
- how to insert group
- how to add rectangle
language: fr
lastmod: 2026-10-26
og_description: Créez un document Word vierge en C# et découvrez comment insérer un
  groupe, puis ajouter une forme rectangle. Maîtrisez le regroupement de plusieurs
  formes avec un exemple de code complet.
og_image_alt: Screenshot showing a blank Word document with a grouped rectangle shape
og_title: Créer un document Word vierge et regrouper plusieurs formes – Tutoriel C#
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Create a blank Word document in C# and learn how to insert a group
    shape, then add a rectangle shape to the group. This guide covers group multiple
    shapes step‑by‑step.
  headline: How to create blank Word document and group multiple shapes
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Comment créer un document Word vierge et regrouper plusieurs formes
url: /fr/java/images-shapes/how-to-create-blank-word-document-and-group-multiple-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer un document Word vierge et regrouper plusieurs formes

Si vous devez **créer un document Word vierge** de façon programmatique, ce tutoriel vous montre exactement comment faire. Vous verrez comment insérer une forme groupée, puis **ajouter un rectangle** à ce groupe, couvrant le flux complet depuis un document vide jusqu’à un dessin groupé.

Travailler avec des fichiers Word signifie souvent organiser plusieurs dessins ensemble — pensez à un diagramme composé de multiples formes. À la fin de ce guide, vous serez capable de **regrouper plusieurs formes**, d’insérer une **forme rectangle**, et de comprendre **comment insérer un groupe** et **comment ajouter un rectangle** de manière propre et réutilisable.

## Ce dont vous avez besoin

* .NET 6.0 ou version ultérieure (le code fonctionne également avec .NET Framework 4.6+)
* **Aspose.Words for .NET** package NuGet (`Install-Package Aspose.Words`)
* Une compréhension de base du C# et de l’IDE Visual Studio (tout IDE fonctionne)

> **Astuce :** Aspose.Words fonctionne entièrement hors ligne ; vous n’avez pas besoin d’une connexion Internet après l’installation du package.

## Étape 1 : Créer un document Word vierge

La première opération consiste à instancier un objet `Document` vide. Cet objet représente le **document Word vierge** que vous enrichirez ensuite avec des formes.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1 – create a new blank Word document
        Document doc = new Document();               // <-- blank document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Pourquoi c’est important :* Un `Document` sans sections ni paragraphes reste un fichier .docx valide. Commencer à partir d’une page blanche garantit qu’aucun formatage caché n’interfère avec les formes que vous ajouterez plus tard.

## Étape 2 : Insérer une forme groupée (how to insert group)

Une **forme groupée** agit comme un conteneur pouvant contenir d’autres objets de dessin. Dans Aspose.Words, vous la créez avec `InsertGroupShape`.

```csharp
        // Step 2 – insert a group shape that will hold other shapes
        GroupShape group = builder.InsertGroupShape();   // <-- container for shapes
```

*Pourquoi utiliser un groupe ?* Le regroupement vous permet de déplacer, faire pivoter ou redimensionner plusieurs formes comme une seule unité. C’est essentiel pour les diagrammes où les éléments doivent rester alignés.

## Étape 3 : Insérer une forme rectangle (insert rectangle shape)

Ajoutez maintenant un rectangle au document. La méthode `InsertShape` renvoie un objet `Shape` que vous pourrez ensuite attacher au groupe.

```csharp
        // Step 3 – create a rectangle shape with specific dimensions
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50); // width=100pt, height=50pt
```

*Pourquoi un rectangle ?* Les rectangles sont le bloc de construction le plus courant pour les organigrammes, les maquettes d’interface utilisateur et les graphiques de substitution. Les dimensions sont exprimées en points (1 pt ≈ 1/72 pouce).

## Étape 4 : Ajouter le rectangle au groupe (how to add rectangle)

Une forme créée avec `InsertShape` se trouve directement dans le corps du document. Pour l’intégrer au groupe, appelez `AppendChild` sur le `GroupShape`.

```csharp
        // Step 4 – add the rectangle to the previously created group
        group.AppendChild(rectangle);   // <-- rectangle now belongs to the group
```

*Que se passe-t-il en coulisses ?* `AppendChild` déplace le nœud rectangle de l’histoire principale du document vers la collection interne du groupe, en préservant sa taille et sa position par rapport à l’origine du groupe.

## Étape 5 : Enregistrer le document

Enfin, écrivez le fichier sur le disque. Vous pouvez ouvrir le `.docx` résultant dans Microsoft Word pour voir le rectangle groupé.

```csharp
        // Step 5 – save the document to a file
        doc.Save("GroupedShapeExample.docx");
    }
}
```

> **Cas particulier :** Si vous avez l’intention d’ajouter d’autres formes (par ex., des cercles, des lignes) au même groupe, répétez **l’étape 3** et **l’étape 4** pour chaque nouvelle forme avant d’enregistrer. Le groupe ajustera automatiquement sa boîte englobante pour inclure tous les enfants.

## Comment regrouper plusieurs formes – extension de l’exemple

Ci-dessous, un extrait rapide qui ajoute une deuxième forme (une ellipse) au même groupe, démontrant **le regroupement de plusieurs formes** dans un seul document.

```csharp
        // Additional shape: an ellipse
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 40);
        group.AppendChild(ellipse);   // now the group contains rectangle + ellipse
```

Lorsque vous ouvrez `GroupedShapeExample.docx`, vous verrez le rectangle et l’ellipse se déplacer ensemble lorsque vous sélectionnez le groupe dans Word.

## Questions fréquentes et dépannage

| Question | Réponse |
|----------|--------|
| **Ai-je besoin d’une licence pour Aspose.Words ?** | Une évaluation gratuite fonctionne sans licence, mais elle ajoute un filigrane. En production, appliquez une licence pour supprimer le filigrane et débloquer les performances complètes. |
| **Puis-je positionner les formes avec précision ?** | Oui. Après avoir inséré une forme, vous pouvez définir les propriétés `Shape.Left`, `Shape.Top`, `Shape.Width` et `Shape.Height`. |
| **Que faire si le rectangle disparaît après l’enregistrement ?** | Assurez‑vous d’appeler `group.AppendChild(rectangle)` *après* avoir inséré le rectangle. Il est nécessaire d’ajouter d’abord la forme au corps du document, puis de la déplacer dans le groupe. |
| **Est‑il possible de regrouper des formes provenant de sections différentes ?** | Non. Toutes les formes d’un groupe doivent appartenir à la même histoire (section). Créez des groupes séparés par section si nécessaire. |

## Récapitulatif

Vous savez maintenant comment **créer un document Word vierge**, **insérer un groupe**, **ajouter un rectangle**, et **regrouper plusieurs formes** en utilisant Aspose.Words pour .NET. L’exemple complet et exécutable ci‑dessus peut être copié dans une application console et exécuté immédiatement.

## Prochaines étapes

* Expérimentez avec les tailles et les couleurs de **insert rectangle shape** (`rectangle.FillColor = Color.LightBlue;`).  
* Explorez d’autres types de formes (`ShapeType.Polygon`, `ShapeType.Line`) pour enrichir vos diagrammes.  
* Apprenez à convertir le `.docx` final en PDF (`doc.Save("output.pdf");`) pour la distribution.  
* Plongez dans **how to add rectangle** aux documents existants contenant déjà du texte — utilisez `DocumentBuilder.MoveTo` pour positionner le groupe où vous le souhaitez.

N’hésitez pas à adapter le code à vos propres besoins de reporting ou de génération de diagrammes. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Comment créer un document Word vierge et regrouper des formes en C#](/words/english/net/programming-with-shapes/how-to-create-blank-word-document-and-group-shapes-in-c/)
- [Comment regrouper des formes dans Word et ajouter des formes à un document Word](/words/english/net/programming-with-shapes/how-to-group-shapes-in-word-and-add-shapes-to-word-document/)
- [Comment créer une forme rectangle et regrouper des formes dans Word avec Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}