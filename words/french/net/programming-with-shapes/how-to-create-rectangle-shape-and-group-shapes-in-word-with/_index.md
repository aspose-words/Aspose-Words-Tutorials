---
category: general
date: 2026-09-05
description: Créez une forme rectangulaire dans un document Word à l'aide d'Aspose.Words,
  puis apprenez comment insérer une ellipse et regrouper des formes dans Word pour
  des mises en page plus riches.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- how to insert rectangle word
- how to insert ellipse word
- aspose.words create shapes
language: fr
lastmod: 2026-09-05
og_description: Créez une forme rectangulaire dans un document Word avec Aspose.Words,
  puis découvrez comment insérer une ellipse et regrouper des formes dans Word pour
  des mises en page complexes.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with Aspose.Words
og_title: Créer une forme rectangulaire et regrouper des formes dans Word – Guide
  Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create rectangle shape in a Word document using Aspose.Words, then
    learn how to insert ellipse word and group shapes in Word for richer layouts.
  headline: How to create rectangle shape and group shapes in Word with Aspose.Words
  type: TechArticle
- description: Create rectangle shape in a Word document using Aspose.Words, then
    learn how to insert ellipse word and group shapes in Word for richer layouts.
  name: How to create rectangle shape and group shapes in Word with Aspose.Words
  steps:
  - name: Pro tip
    text: Always add shapes **before** you group them. If you try to group a shape
      that is already part of another group, Aspose.Words throws an `ArgumentException`.
      Building the group in a single method prevents this runtime error.
  - name: Watch out for
    text: '* **Coordinate system** – `Left` and `Top` are measured from the page’s
      left and top margins, not from the document edge. Misunderstanding this can
      place shapes off‑page. * **Licensing** – Without a valid license, the saved
      document will contain a watermark that says “Aspose.Words for .NET Evaluatio'
  - name: What’s next?
    text: '* Explore **aspose.words create shapes** for more complex geometry such
      as `Polygon` or `Freeform`. * Combine grouped shapes with **content controls**
      to build dynamic templates. * Convert the DOCX to PDF or HTML to see how vector
      shapes are rendered across formats.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Comment créer une forme rectangulaire et regrouper des formes dans Word avec
  Aspose.Words
url: /fr/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer une forme rectangulaire et regrouper des formes dans Word avec Aspose.Words

Si vous devez **créer une forme rectangulaire** dans un document Word, ce guide vous montre les étapes exactes avec Aspose.Words pour .NET. Vous verrez également comment insérer un mot ellipse, regrouper des formes dans Word, et enregistrer le résultat au format DOCX. La solution fonctionne dans n’importe quel projet .NET 6+ et ne nécessite pas Microsoft Office installé sur le serveur.

Le tutoriel couvre tout, de la configuration du projet à la gestion des problèmes courants de mise en page, afin que vous puissiez copier le code et l’exécuter immédiatement.

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

* SDK .NET 6 ou ultérieur installé  
* Un IDE compatible NuGet (Visual Studio, Rider ou VS Code)  
* Une licence Aspose.Words pour .NET (ou une clé d’évaluation temporaire)  
* Des connaissances de base en C# et en structure de documents Word  

Ces éléments permettent au code de se compiler et aux formes de s’afficher correctement.

## Étape 1 : Configurer le projet et ajouter Aspose.Words

Créez un nouveau projet console et ajoutez le package Aspose.Words :

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Le package fournit les classes `Document`, `DocumentBuilder`, `Shape` et `GroupShape` utilisées tout au long de ce tutoriel.

## Étape 2 : Initialiser un document vierge et un builder

L’objet `Document` représente le fichier Word complet, tandis que `DocumentBuilder` vous permet d’insérer du contenu de façon programmatique.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

Document doc = new Document();                 // creates an empty .docx container
DocumentBuilder builder = new DocumentBuilder(doc);
```

Créer le document en premier garantit que toutes les opérations de forme ultérieures disposent d’un conteneur valide.

## Étape 3 : **Créer une forme rectangulaire** et définir ses dimensions

Un rectangle est le conteneur le plus courant pour du texte ou des images. Vous définissez sa taille en points (1 pt ≈ 1/72 pouce).

```csharp
// create a rectangle shape
Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
rectangleShape.Width = 100;      // 100 pt ≈ 1.39 in
rectangleShape.Height = 50;      // 50 pt ≈ 0.69 in

// optional: give the rectangle a light fill and a thin border
rectangleShape.FillColor = System.Drawing.Color.LightGray;
rectangleShape.Line.Width = 0.5;

// insert the rectangle into the document at the current cursor position
builder.InsertNode(rectangleShape);
```

Pourquoi cette étape est importante : la classe `Shape` encapsule la géométrie, le remplissage et les propriétés de ligne. Définir `Width` et `Height` avant l’insertion garantit que la forme apparaît avec la taille attendue.

## Étape 4 : **Comment insérer un mot ellipse** – ajouter une forme ellipse

Une ellipse peut être utilisée pour des icônes, des repères ou des éléments décoratifs. Le code reflète la création du rectangle, seule la valeur de `ShapeType` change.

```csharp
// create an ellipse shape
Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
ellipseShape.Width = 80;      // 80 pt ≈ 1.11 in
ellipseShape.Height = 80;     // a perfect circle because width = height

// style the ellipse
ellipseShape.FillColor = System.Drawing.Color.CornflowerBlue;
ellipseShape.Line.Color = System.Drawing.Color.DarkBlue;

// place the ellipse after the rectangle
builder.InsertNode(ellipseShape);
```

Les propriétés `FillColor` et `Line.Color` illustrent comment personnaliser l’apparence sans images externes.

## Étape 5 : **Regrouper des formes dans Word** – combiner rectangle et ellipse

Le regroupement vous permet de déplacer, redimensionner ou faire pivoter plusieurs formes comme une seule unité. C’est essentiel lorsque vous avez besoin d’un graphique composite (par ex., une icône avec libellé).

```csharp
// create a group shape container
GroupShape groupShape = new GroupShape(doc);

// add the previously created shapes to the group
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);

// optional: set the group's position on the page
groupShape.Left = 150;   // distance from the left margin in points
groupShape.Top = 100;    // distance from the top margin in points

// insert the grouped shape into the document
builder.InsertNode(groupShape);
```

Lorsque vous appelez `AppendChild`, les formes d’origine sont retirées du flux principal du document et deviennent des enfants du `GroupShape`. Le groupe se comporte comme une forme unique, ce qui simplifie les ajustements de mise en page ultérieurs.

## Étape 6 : Enregistrer le document

Enfin, écrivez le document sur le disque. Vous pouvez choisir n’importe quel format supporté (`.docx`, `.pdf`, `.html`, etc.). Pour ce tutoriel, nous conservons le format Word natif.

```csharp
// replace "YOUR_DIRECTORY" with an absolute or relative path you control
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Après l’exécution du programme, ouvrez *GroupShape.docx* dans Microsoft Word. Vous verrez un rectangle et une ellipse regroupés, positionnés aux coordonnées que vous avez spécifiées.

## Variations courantes et cas limites

| Situation | Ce qu’il faut modifier | Raison |
|-----------|------------------------|--------|
| **Unités de taille différentes** | Utilisez `ConvertUtil.InchToPoint(2.5)` pour les pouces ou `ConvertUtil.MillimeterToPoint(30)` pour les millimètres. | Facilite la lisibilité du code lorsqu’on travaille avec des mesures autres que les points. |
| **Ajouter du texte à l’intérieur du rectangle** | Créez un nœud `Paragraph`, définissez sa propriété `Text`, puis ajoutez‑le à `rectangleShape` via `AppendChild`. | Vous permet d’étiqueter la forme sans boîtes de texte séparées. |
| **Faire pivoter le groupe** | Définissez `groupShape.Rotation = 45;` (degrés). | Utile pour créer des badges ou filigranes diagonaux. |
| **Enregistrer en PDF** | Appelez `doc.Save("GroupShape.pdf");`. | Aspose.Words rasterise automatiquement les formes vectorielles pour la sortie PDF. |
| **Groupes multiples** | Créez d’autres instances de `GroupShape` et répétez les étapes d’ajout/insertion. | Permet des mises en page complexes avec plusieurs composites indépendants. |

### Astuce pro

Ajoutez toujours les formes **avant** de les regrouper. Si vous essayez de regrouper une forme déjà appartenant à un autre groupe, Aspose.Words lève une `ArgumentException`. Construire le groupe dans une seule méthode évite cette erreur d’exécution.

### Points d’attention

* **Système de coordonnées** – `Left` et `Top` sont mesurés à partir des marges gauche et supérieure de la page, pas depuis le bord du document. Une mauvaise compréhension peut placer les formes hors de la page.  
* **Licence** – Sans licence valide, le document enregistré contiendra un filigrane indiquant “Aspose.Words for .NET Evaluation”. Appliquez votre licence tôt dans le code (`License license = new License(); license.SetLicense("Aspose.Words.lic");`) pour l’éviter.

## Code source complet (exécutable)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Create rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
        rectangleShape.Width = 100;
        rectangleShape.Height = 50;
        rectangleShape.FillColor = System.Drawing.Color.LightGray;
        rectangleShape.Line.Width = 0.5;
        builder.InsertNode(rectangleShape);

        // 3️⃣ Create ellipse shape
        Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
        ellipseShape.Width = 80;
        ellipseShape.Height = 80;
        ellipseShape.FillColor = System.Drawing.Color.CornflowerBlue;
        ellipseShape.Line.Color = System.Drawing.Color.DarkBlue;
        builder.InsertNode(ellipseShape);

        // 4️⃣ Group rectangle and ellipse
        GroupShape groupShape = new GroupShape(doc);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        groupShape.Left = 150;
        groupShape.Top = 100;
        builder.InsertNode(groupShape);

        // 5️⃣ Save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

L’exécution de ce programme produit *GroupShape.docx* avec les formes regroupées exactement comme décrit.

## Conclusion

Vous savez maintenant comment **créer une forme rectangulaire**, **insérer un mot ellipse**, et **regrouper des formes dans Word** en utilisant Aspose.Words. L’exemple complet montre le flux complet — de l’initialisation du document à l’enregistrement du fichier final—afin que vous puissiez intégrer la gestion des formes dans n’importe quelle solution d’automatisation de rapports ou de génération de documents.

### Et après ?

* Explorez **aspose.words create shapes** pour des géométries plus complexes comme `Polygon` ou `Freeform`.  
* Combinez les formes groupées avec des **contrôles de contenu** pour créer des modèles dynamiques.  
* Convertissez le DOCX en PDF ou HTML pour voir comment les formes vectorielles sont rendues selon les formats.  

N’hésitez pas à expérimenter avec différentes tailles, couleurs et rotations. Une fois que vous maîtrisez le regroupement de formes, vous pouvez créer des diagrammes sophistiqués, des badges et des éléments d’interface personnalisés directement dans les documents Word.

## Que devez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}