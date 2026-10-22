---
category: general
date: 2026-09-21
description: Apprenez à regrouper des formes dans Word à l’aide d’Aspose.Words pour
  C#. Ce guide étape par étape couvre la création, le positionnement et l’enregistrement
  des formes groupées.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in Word
- Aspose.Words shape grouping
- C# Word shape manipulation
- DocumentBuilder insert shape
- GroupShape container
language: fr
lastmod: 2026-09-21
og_description: Regroupez des formes dans Word à l'aide d'Aspose.Words pour C#. Suivez
  ce tutoriel concis pour créer, positionner et enregistrer des formes groupées de
  manière programmatique.
og_image_alt: Screenshot of grouped shapes in Word document created with Aspose.Words
og_title: Regrouper les formes dans Word avec Aspose.Words – guide complet C#
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  headline: How to group shapes in Word with Aspose.Words for C#
  type: TechArticle
- description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  name: How to group shapes in Word with Aspose.Words for C#
  steps:
  - name: Create a blank document and a `DocumentBuilder`
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert the first rectangle shape
    text: '```csharp // Insert a rectangle that is 100 points wide and 50 points tall.
      Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50); ```'
  - name: Insert the second rectangle and offset it
    text: '```csharp // Insert the second rectangle with the same dimensions. Shape
      shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);'
  - name: Create a `GroupShape` large enough for both rectangles
    text: '```csharp // The group must be wide enough to contain both shapes (100
      pt + 120 pt + 100 pt = 320 pt). // We give a little extra margin, so the group
      width is set to 300 pt and height to 100 pt. GroupShape group = new GroupShape(doc,
      300, 100); ```'
  - name: Append the individual shapes to the group
    text: '```csharp group.AppendChild(shape1); group.AppendChild(shape2); ```'
  - name: Insert the grouped shape back into the document
    text: '```csharp // Insert the GroupShape at the current builder position. builder.InsertNode(group);
      ```'
  - name: Save the document
    text: '```csharp // Replace YOUR_DIRECTORY with an absolute or relative path where
      you have write permission. doc.Save("YOUR_DIRECTORY/GroupedShapes.docx"); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Comment regrouper des formes dans Word avec Aspose.Words pour C#
url: /fr/net/programming-with-shapes/how-to-group-shapes-in-word-with-aspose-words-for-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment regrouper des formes dans Word avec Aspose.Words pour C#

Si vous devez **regrouper des formes dans Word** de façon programmatique, Aspose.Words le rend simple. Ce tutoriel vous montre comment créer deux formes rectangulaires, les placer côte à côte, les combiner dans un `GroupShape` et enregistrer le résultat sous forme de fichier DOCX.

Vous verrez un exemple complet et exécutable, des explications sur l’importance de chaque étape, ainsi que des astuces pour gérer les cas particuliers comme les formes qui se chevauchent ou le redimensionnement dynamique. À la fin de ce guide, vous pourrez intégrer le regroupement de formes dans n’importe quel projet d’automatisation Word.

## Prérequis

Avant de commencer, assurez-vous d’avoir :

* .NET 6.0 (ou version ultérieure) installé – Aspose.Words prend en charge .NET Standard 2.0+, .NET Core et .NET Framework.  
* Une licence valide d’Aspose.Words pour .NET (ou une clé d’évaluation temporaire) – la bibliothèque fonctionne sans licence mais ajoute un filigrane.  
* Visual Studio 2022 (ou tout IDE C#) pour compiler et exécuter l’exemple.

Aucun package NuGet supplémentaire n’est requis au‑delà de `Aspose.Words`.

## Comment regrouper des formes dans Word avec Aspose.Words

Le cœur de la solution est un objet **`GroupShape`** qui agit comme conteneur pour les formes individuelles. Ci‑dessous, nous décomposons le processus en étapes claires.

### Étape 1 : Créer un document vierge et un `DocumentBuilder`

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty Word document.
Document doc = new Document();

// DocumentBuilder provides convenient methods for inserting content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Pourquoi cette étape ?*  
`Document` représente l’ensemble du fichier DOCX, tandis que `DocumentBuilder` fournit des méthodes fluides (par ex., `InsertShape`) qui placent automatiquement les nouveaux éléments à la position actuelle du curseur.

### Étape 2 : Insérer la première forme rectangulaire

```csharp
// Insert a rectangle that is 100 points wide and 50 points tall.
Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

L’appel `InsertShape` ajoute la forme au document et renvoie un objet `Shape` que vous pouvez configurer davantage (couleur, bordure, etc.). La taille est exprimée en points (1 pt ≈ 1/72 in).

### Étape 3 : Insérer le deuxième rectangle et le décaler

```csharp
// Insert the second rectangle with the same dimensions.
Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// Move the second shape 120 points to the right so the two rectangles do not overlap.
shape2.Left = 120; // Horizontal offset from the left edge of the page.
```

Définir `Left` positionne la forme par rapport à la marge de la page. Le décalage doit être supérieur à la largeur de la première forme (100 pt) pour éviter le chevauchement ; nous utilisons 120 pt pour laisser un petit espace.

### Étape 4 : Créer un `GroupShape` assez grand pour les deux rectangles

```csharp
// The group must be wide enough to contain both shapes (100 pt + 120 pt + 100 pt = 320 pt).
// We give a little extra margin, so the group width is set to 300 pt and height to 100 pt.
GroupShape group = new GroupShape(doc, 300, 100);
```

`GroupShape` prend le `Document` propriétaire et les dimensions du conteneur. La largeur du conteneur doit dépasser le bord droit de la forme la plus éloignée ; sinon, la deuxième forme serait tronquée.

### Étape 5 : Ajouter les formes individuelles au groupe

```csharp
group.AppendChild(shape1);
group.AppendChild(shape2);
```

L’ajout déplace les formes dans la collection interne du groupe. Après cet appel, les formes ne sont plus des objets indépendants dans l’arbre du document ; elles appartiennent au groupe.

### Étape 6 : Réinsérer la forme groupée dans le document

```csharp
// Insert the GroupShape at the current builder position.
builder.InsertNode(group);
```

`InsertNode` place le `GroupShape` complet à l’endroit où le curseur se trouve actuellement. Si vous avez besoin du groupe dans un paragraphe spécifique, déplacez d’abord le builder vers ce paragraphe.

### Étape 7 : Enregistrer le document

```csharp
// Replace YOUR_DIRECTORY with an absolute or relative path where you have write permission.
doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
```

Le fichier résultant contient deux rectangles qui se comportent comme un seul objet — vous pouvez les déplacer, les redimensionner ou les supprimer ensemble dans Microsoft Word.

## Code source complet

Assembler toutes les étapes donne un programme autonome :

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first rectangle (100 pt × 50 pt).
        Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // 3️⃣ Insert the second rectangle and offset it horizontally.
        Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        shape2.Left = 120; // Prevent overlap.

        // 4️⃣ Create a GroupShape container large enough for both.
        GroupShape group = new GroupShape(doc, 300, 100);

        // 5️⃣ Add both rectangles to the group.
        group.AppendChild(shape1);
        group.AppendChild(shape2);

        // 6️⃣ Insert the grouped shape back into the document.
        builder.InsertNode(group);

        // 7️⃣ Save the document.
        doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
    }
}
```

**Résultat attendu :** L’ouverture de *GroupedShapes.docx* dans Microsoft Word montre deux rectangles côte à côte, traités comme un seul objet sélectionnable. Faire glisser le groupe déplace les deux rectangles simultanément.

## Variations courantes et cas particuliers

| Situation | Ajustement recommandé |
|-----------|------------------------|
| **Plus de deux formes** | Créez des objets `Shape` supplémentaires, positionnez‑les en conséquence, et ajoutez‑les tous au même `GroupShape`. |
| **Taille dynamique** | Calculez la largeur/hauteur du groupe à partir des valeurs maximales `Right` et `Bottom` des formes enfants. |
| **Types de forme différents** | `ShapeType.Ellipse`, `ShapeType.Triangle`, etc., peuvent être insérés de la même façon ; le conteneur du groupe ne se soucie pas du type. |
| **Formes pivotées** | Définissez `shape.Rotation = 45;` avant d’ajouter ; la rotation est conservée dans le groupe. |
| **Enregistrement au format PDF** | Appelez `doc.Save("GroupedShapes.pdf");` – le groupe est conservé dans le rendu PDF. |

**Astuce :** Après le regroupement, vous pouvez toujours modifier les formes individuelles en accédant à `group.GetChildNodes(NodeType.Shape, true)`. Cela est utile quand vous devez changer la couleur de remplissage d’un rectangle sans rompre le groupe.

## Comment vérifier le regroupement de façon programmatique

Si vous devez confirmer que les formes sont correctement regroupées (par ex., dans des tests unitaires), examinez la hiérarchie des nœuds du document :

```csharp
NodeCollection groups = doc.GetChildNodes(NodeType.GroupShape, true);
Console.WriteLine($"Number of groups: {groups.Count}");
Console.WriteLine($"Children in first group: {groups[0].GetChildNodes(NodeType.Shape, true).Count}");
```

La sortie doit être :

```
Number of groups: 1
Children in first group: 2
```

Cela confirme que les **group shapes in Word** ont été créées comme prévu.

## Conclusion

Vous savez maintenant comment **regrouper des formes dans Word** avec Aspose.Words pour C#. Le processus consiste à créer des formes individuelles, les positionner, les envelopper dans un `GroupShape`, puis réinsérer le groupe dans le document. Avec l’exemple complet ci‑dessus, vous pouvez étendre la technique à n’importe quel nombre de formes, à différents types, ou même la combiner avec des zones de texte et des images.

Ensuite, explorez des sujets connexes tels que **Aspose.Words shape grouping**, **C# Word shape manipulation**, et **DocumentBuilder insert shape** pour des scénarios d’automatisation de documents plus avancés. Expérimentez le redimensionnement dynamique, le regroupement conditionnel et l’exportation en PDF afin de tirer pleinement parti de la puissance d’Aspose.Words.

## Que devez‑vous apprendre ensuite ?


Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}