---
category: general
date: 2026-10-20
description: Apprenez à créer un document Word vierge, à regrouper des formes dans
  Word, à définir la couleur de remplissage d’une forme et à utiliser le type d’habillage
  en ligne avec un exemple complet en C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- how to group shapes
- set shape fill color
- wrap type inline
language: fr
lastmod: 2026-10-20
og_description: Créez un document Word vierge, regroupez les formes dans Word et définissez
  la couleur de remplissage de la forme avec le type d'habillage en ligne à l'aide
  d'Aspose.Words et de C#. Suivez le tutoriel complet.
og_image_alt: Screenshot of a blank Word document containing a grouped rectangle and
  text box created with Aspose.Words
og_title: Créer un document Word vierge et regrouper des formes dans Word – guide
  étape par étape
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Learn how to create a blank Word document, group shapes in Word, set
    shape fill color, and use wrap type inline with a complete C# example.
  headline: How to create a blank Word document and group shapes in Word using Aspose.Words
  type: TechArticle
- description: Learn how to create a blank Word document, group shapes in Word, set
    shape fill color, and use wrap type inline with a complete C# example.
  name: How to create a blank Word document and group shapes in Word using Aspose.Words
  steps:
  - name: Expected result
    text: '* A .docx file containing a single paragraph. * Inside the paragraph, an
      inline group that looks like a single composite object. * The rectangle is filled
      with light blue, and the text box displays “Grouped text”.'
  - name: What if I need the group to float rather than be inline?
    text: Replace `WrapType.Inline` with `WrapType.TopBottom` (or any other `WrapType`
      enum value). Floating groups can be positioned independently of paragraph flow,
      but they lose the automatic inline alignment.
  - name: Can I add more shapes, such as circles or images?
    text: Yes. Create additional `Shape` objects with `ShapeType.Ellipse` or `ShapeType.Image`,
      configure their properties, and call `group.AppendChild(newShape)`. The group
      will automatically expand to accommodate the new bounds if you update `group.Bounds`
      accordingly.
  - name: How do I change the group’s overall size after adding children?
    text: Adjust `group.Bounds` after all children are appended, or compute the union
      of child bounds programmatically. This ensures the group’s hit‑test area matches
      the visual content.
  - name: What if the output folder does not exist?
    text: 'Aspose.Words throws a `DirectoryNotFoundException`. Create the directory
      first:'
  - name: Does this work with .NET Framework instead of .NET Core?
    text: All APIs used (`Document`, `DocumentBuilder`, `GroupShape`, `Shape`) are
      available in the .NET Framework version of Aspose.Words, so the same code works
      unchanged.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Comment créer un document Word vierge et regrouper des formes dans Word à l’aide
  d’Aspose.Words
url: /fr/net/programming-with-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer un document Word vierge et regrouper des formes dans Word

Si vous devez **créer un document Word vierge** contenant plusieurs formes agissant comme une seule unité, ce guide vous montre exactement comment procéder. Vous verrez comment **regrouper des formes dans Word**, définir la couleur de remplissage d’une forme, et appliquer **wrap type inline** — le tout avec un programme C# concis et exécutable.

Le tutoriel vous guide à travers chaque ligne de code, explique pourquoi chaque étape est importante et met en évidence les pièges courants. À la fin, vous disposerez d’un fichier .docx affichant un rectangle et une zone de texte regroupés, prêts pour une automatisation supplémentaire.

## Ce que vous apprendrez

* Comment initialiser un fichier Word vide avec Aspose.Words.
* La bonne façon de créer un **GroupShape** et d’ajouter des formes enfants.
* Techniques pour **set shape fill color** et contrôler le positionnement.
* Utiliser **wrap type inline** afin que le groupe se comporte comme un seul objet en ligne.
* Comment enregistrer et vérifier le résultat.

Aucune expérience préalable avec Aspose.Words n’est requise, mais vous devez être à l’aise avec la syntaxe de base du C# et disposer de Visual Studio (ou d’un autre IDE) installé.

## Prérequis

| Exigence | Raison |
|----------|--------|
| .NET 6.0 ou version ultérieure | Fournit le runtime pour le projet C#. |
| Aspose.Words pour .NET (dernière version) | Fournit les classes `Document`, `DocumentBuilder` et les classes de formes utilisées dans l’exemple. |
| Un chemin de dossier accessible en écriture | L’appel `doc.Save` nécessite un répertoire valide pour écrire le fichier de sortie. |
| Connaissances de base en C# | Vous permet de suivre le code et de le modifier pour vos propres scénarios. |

Installez Aspose.Words via NuGet :

```bash
dotnet add package Aspose.Words
```

---

## Étape 1 : Créer un document Word vierge

La première opération consiste à **créer un document Word vierge**. La classe `Document` d’Aspose.Words représente un fichier Word en mémoire, et `DocumentBuilder` fournit une API pratique pour le modifier.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Initialize a new empty document.
Document doc = new Document();

// Attach a builder to the document for easy content insertion.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Pourquoi c’est important* : Commencer avec un document vierge garantit que la forme groupée que vous ajoutez sera le seul contenu, ce qui simplifie la vérification.

## Étape 2 : Définir une forme groupée avec wrap type inline

Un **GroupShape** agit comme un conteneur pour d’autres formes. Définir son `WrapType` à `Inline` assure que le groupe se comporte comme un seul objet en ligne dans le flux du paragraphe.

```csharp
// Create a group shape that will hold the rectangle and text box.
GroupShape group = new GroupShape(doc, WrapType.Inline);

// Define the bounding rectangle of the group (x, y, width, height).
group.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
```

*Pourquoi c’est important* : Utiliser **wrap type inline** empêche le groupe de flotter loin du texte environnant, ce qui est essentiel lorsque vous souhaitez que le groupe se déplace comme une unité.

## Étape 3 : Ajouter un rectangle et définir la couleur de remplissage de la forme

Un rectangle est un élément visuel courant. Le constructeur `Shape` accepte un `ShapeType` ; nous spécifions ensuite les dimensions et la couleur de remplissage.

```csharp
// Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width = 150,
    Height = 100,
    FillColor = System.Drawing.Color.LightBlue
};

// Append the rectangle to the group.
group.AppendChild(rectangle);
```

*Pourquoi c’est important* : La propriété `FillColor` montre **set shape fill color** en pratique, donnant au rectangle un arrière‑plan bleu clair qui se démarque dans le document final.

## Étape 4 : Ajouter une zone de texte – comment regrouper efficacement les formes

Une zone de texte fournit du texte modifiable à l’intérieur du groupe. Positionnez‑la par rapport au système de coordonnées du groupe en ajustant la propriété `Top`.

```csharp
// Create a text box shape.
Shape textBox = new Shape(doc, ShapeType.TextBox)
{
    Width = 120,
    Height = 60,
    TextBoxText = "Grouped text",
    Top = 110 // Position below the rectangle inside the group.
};

// Append the text box to the group.
group.AppendChild(textBox);
```

*Pourquoi c’est important* : Cette étape répond à **how to group shapes** — en ajoutant chaque forme enfant à la même instance `GroupShape`. Le décalage `Top` garantit que la zone de texte apparaît sous le rectangle, démontrant un contrôle précis de la mise en page.

## Étape 5 : Insérer la forme groupée terminée dans le document

Maintenant que le groupe contient les deux formes enfants, insérez‑le à la position actuelle du `DocumentBuilder`.

```csharp
// Insert the group shape at the builder’s cursor location.
builder.InsertNode(group);
```

*Pourquoi c’est important* : Insérer le groupe comme un seul nœud garantit que Word traite le rectangle et la zone de texte comme un objet logique unique, préservant leurs positions relatives lors de l’édition.

## Étape 6 : Enregistrer le document et vérifier le résultat

Enfin, écrivez le document sur le disque. Remplacez `YOUR_DIRECTORY` par un chemin réel sur votre machine.

```csharp
// Save the document to the specified folder.
doc.Save("YOUR_DIRECTORY/GroupShape.docx");
```

Lorsque vous ouvrez `GroupShape.docx` dans Microsoft Word, vous devez voir un rectangle bleu clair avec une zone de texte libellée « Grouped text » positionnée directement en dessous. Sélectionner l’une ou l’autre forme sélectionnera tout le groupe, confirmant que **group shapes in Word** fonctionne comme prévu.

### Résultat attendu

* Un fichier .docx contenant un seul paragraphe.
* À l’intérieur du paragraphe, un groupe en ligne qui ressemble à un seul objet composite.
* Le rectangle est rempli de bleu clair, et la zone de texte affiche « Grouped text ».

![Capture d'écran du document Word généré](grouped_shapes.png){.center width=600 alt="Capture d'écran d'un document Word vierge avec rectangle groupé et zone de texte créée avec Aspose.Words"}

## Questions fréquentes et gestion des cas limites

### Et si j’ai besoin que le groupe flotte plutôt qu’il soit en ligne ?

Remplacez `WrapType.Inline` par `WrapType.TopBottom` (ou toute autre valeur de l’énumération `WrapType`). Les groupes flottants peuvent être positionnés indépendamment du flux du paragraphe, mais ils perdent l’alignement automatique en ligne.

### Puis‑je ajouter d’autres formes, comme des cercles ou des images ?

Oui. Créez des objets `Shape` supplémentaires avec `ShapeType.Ellipse` ou `ShapeType.Image`, configurez leurs propriétés, et appelez `group.AppendChild(newShape)`. Le groupe s’étendra automatiquement pour accueillir les nouvelles limites si vous mettez à jour `group.Bounds` en conséquence.

### Comment modifier la taille globale du groupe après avoir ajouté des enfants ?

Ajustez `group.Bounds` après avoir ajouté tous les enfants, ou calculez l’union des limites des enfants par programme. Cela garantit que la zone de test du groupe correspond au contenu visuel.

### Que faire si le dossier de sortie n’existe pas ?

Aspose.Words lève une `DirectoryNotFoundException`. Créez d’abord le répertoire :

```csharp
string outputPath = "YOUR_DIRECTORY";
Directory.CreateDirectory(outputPath);
doc.Save(Path.Combine(outputPath, "GroupShape.docx"));
```

### Cela fonctionne‑t‑il avec .NET Framework au lieu de .NET Core ?

Toutes les API utilisées (`Document`, `DocumentBuilder`, `GroupShape`, `Shape`) sont disponibles dans la version .NET Framework d’Aspose.Words, donc le même code fonctionne sans modification.

## Astuces professionnelles

* **Conseil de performance** – Réutilisez une seule instance de `DocumentBuilder` lors de l’insertion de nombreux groupes ; créer un nouveau builder par groupe ajoute une surcharge.
* **Cohérence visuelle** – Définissez `rectangle.StrokeColor` pour qu’il corresponde à `FillColor` afin d’obtenir un rendu homogène, ou définissez `rectangle.LineWidth = 0` pour masquer la bordure.
* **Débogage** – Appelez `doc.UpdatePageLayout()` avant d’enregistrer si vous modifiez de nombreuses formes ; cela force Word à recalculer la mise en page et peut éviter des découpes inattendues.

## Conclusion

Vous savez maintenant comment **créer un document Word vierge**, **regrouper des formes dans Word**, **définir la couleur de remplissage d’une forme**, et appliquer **wrap type inline** en utilisant Aspose.Words pour .NET. L’exemple complet montre l’approche standard pour créer des graphiques composites qui se comportent comme un seul objet dans Word.

À partir d’ici, vous pouvez explorer :

* Ajouter des formes supplémentaires telles que des images ou des graphiques.
* Expérimenter différentes valeurs de `WrapType` pour les groupes flottants.
* Automatiser la génération en lot de diagrammes groupés sur plusieurs documents.

N’hésitez pas à adapter le code à vos propres scénarios d’automatisation, et à partager vos résultats dans les commentaires !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Créer une forme groupée dans un document Word avec Aspose.Words pour .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Créer un document Word vierge avec Aspose.Words – Guide étape par étape](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Comment enregistrer un PDF depuis Word avec des formes en ligne – Guide complet](/words/english/java/document-conversion-and-export/how-to-save-pdf-from-word-with-inline-shapes-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}