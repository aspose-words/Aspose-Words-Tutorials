---
category: general
date: 2026-10-13
description: Regrouper des formes dans Word avec C# – apprenez comment regrouper des
  formes et ajouter des formes à un groupe en utilisant Aspose.Words en quelques étapes
  simples.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- add shapes to group
language: fr
lastmod: 2026-10-13
og_description: Regroupez des formes dans Word avec C# et Aspose.Words. Suivez ce
  guide pour apprendre à regrouper des formes et à ajouter des formes à un groupe
  dans un document Word.
og_image_alt: Screenshot of a Word document showing two shapes combined into a single
  grouped shape
og_title: Regrouper des formes dans Word avec C# – guide étape par étape
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: group shapes in Word with C# – learn how to group shapes and add shapes
    to group using Aspose.Words in a few easy steps.
  headline: Group shapes in Word using C# – complete programming guide
  type: TechArticle
- description: group shapes in Word with C# – learn how to group shapes and add shapes
    to group using Aspose.Words in a few easy steps.
  name: Group shapes in Word using C# – complete programming guide
  steps:
  - name: Load the Word document
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Retrieve the shapes you want to group
    text: '```csharp // Get the first shape (index 0) and second shape (index 1) from
      the whole document. Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0,
      true); Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true); ```'
  - name: Create a new `GroupShape` container
    text: '```csharp GroupShape groupShape = new GroupShape(doc); ```'
  - name: Add the individual shapes to the group
    text: '```csharp groupShape.AppendChild(firstShape); groupShape.AppendChild(secondShape);
      ```'
  - name: Insert the group shape into the document body
    text: '```csharp // Insert the group as the last child of the first paragraph.
      Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph; firstParagraph.AppendChild(groupShape);
      ```'
  - name: Save the modified document
    text: '```csharp string outputPath = @"YOUR_DIRECTORY\output.docx"; doc.Save(outputPath);
      ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Regrouper les formes dans Word avec C# – guide complet de programmation
url: /fr/net/programming-with-shapes/group-shapes-in-word-using-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Regrouper des formes dans Word avec C# – guide complet de programmation

Si vous devez **regrouper des formes dans Word** de manière programmatique, ce guide vous montre exactement comment faire. À la fin des deux premières phrases, vous connaîtrez le code requis, la raison de chaque étape, et comment **ajouter des formes à un groupe** sans surprise.

Nous couvrirons tout, du chargement d'un fichier `.docx` à l'enregistrement du document mis à jour. Le tutoriel suppose que vous avez des connaissances de base en C# et une référence à la bibliothèque Aspose.Words for .NET. Aucune documentation externe n'est requise — il suffit de copier, coller et exécuter.

## Prérequis

- .NET 6.0 ou supérieur (le code fonctionne également avec .NET Framework 4.7+)
- Package NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)
- Un document Word (`input.docx`) contenant déjà au moins deux formes (par ex., images, AutoShapes)

> **Astuce :** Si vous testez, créez un fichier Word simple avec deux rectangles via l'interface Word. Enregistrez‑le sous le nom `input.docx` dans un dossier que vous contrôlez.

## Regrouper des formes dans Word – guide étape par étape

Ci-dessous, nous décomposons le processus en cinq étapes logiques. Chaque étape comprend le code C# exact, une explication du *pourquoi* de la ligne, et une courte note sur les pièges courants.

### Étape 1 : Charger le document Word

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

string inputPath = @"YOUR_DIRECTORY\input.docx";
Document doc = new Document(inputPath);
```

**Pourquoi :** `Document` est le point d'entrée pour toute manipulation Word. Fournir le chemin complet du fichier charge le document en mémoire, ce qui nous permet d'interroger et de modifier son arbre de nœuds.

**Piège :** Passer un chemin relatif peut échouer lorsque le répertoire de travail diffère. Utilisez un chemin absolu ou `Path.Combine` avec `AppContext.BaseDirectory`.

### Étape 2 : Récupérer les formes que vous souhaitez regrouper

```csharp
// Get the first shape (index 0) and second shape (index 1) from the whole document.
Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true);
```

**Pourquoi :** `GetChild` parcourt l'arbre du document et renvoie le *n‑ième* nœud du type demandé. Mettre `isDeep` à `true` recherche dans tout le document, pas seulement dans la section courante.

**Cas limite :** Si le document contient moins de deux formes, `firstShape` ou `secondShape` sera `null` et une exception sera levée lorsque nous tenterons de le convertir. Protégez‑vous contre cela :

```csharp
if (firstShape == null || secondShape == null)
    throw new InvalidOperationException("The document must contain at least two shapes to group.");
```

### Étape 3 : Créer un nouveau conteneur `GroupShape`

```csharp
GroupShape groupShape = new GroupShape(doc);
```

**Pourquoi :** `GroupShape` agit comme un nœud parent pouvant contenir plusieurs objets `Shape`. Il hérite de `Shape`, il peut donc être inséré partout où une forme ordinaire est autorisée (par ex., à l'intérieur d'un paragraphe).

### Étape 4 : Ajouter les formes individuelles au groupe

```csharp
groupShape.AppendChild(firstShape);
groupShape.AppendChild(secondShape);
```

**Pourquoi :** `AppendChild` déplace les formes de leurs emplacements d'origine vers le nouveau groupe. Après cet appel, les formes originales n'existent plus en tant que nœuds indépendants ; elles deviennent partie de `groupShape`.

**Astuce :** Le regroupement ajuste automatiquement les positions relatives des formes enfants. Si vous avez besoin d'une disposition spécifique, définissez la propriété `GroupShape.Bounds` *avant* d'ajouter les enfants.

```csharp
// Example: set the group to start at (100, 100) points and be 300x200 points large.
groupShape.Bounds = new System.Drawing.RectangleF(100, 100, 300, 200);
```

### Étape 5 : Insérer le groupe de formes dans le corps du document

```csharp
// Insert the group as the last child of the first paragraph.
Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
firstParagraph.AppendChild(groupShape);
```

**Pourquoi :** Un `GroupShape` doit être placé à l'intérieur d'un paragraphe (ou d'une cellule de tableau) pour être rendu. En l'ajoutant au premier paragraphe, nous garantissons un placement visible sans perturber la mise en page existante.

### Étape 6 : Enregistrer le document modifié

```csharp
string outputPath = @"YOUR_DIRECTORY\output.docx";
doc.Save(outputPath);
```

**Pourquoi :** `Save` écrit les modifications en mémoire dans un fichier `.docx`. Vous pouvez également enregistrer dans un flux ou en PDF en changeant la surcharge.

**Vérification du résultat :** Ouvrez `output.docx` dans Microsoft Word. Vous devriez voir les deux formes originales maintenant combinées en un seul objet groupé. Sélectionner le groupe affichera les poignées de groupement standard de Word.

## Comment regrouper des formes programmatique­ment – approfondissements

- **Propriété du nœud :** Lorsque vous appelez `AppendChild`, la référence `ParentNode` de la forme change automatiquement. Cela empêche les nœuds « orphelins » qui pourraient corrompre le document.
- **Conservation du formatage :** Le groupement ne **perd** aucun format de forme (couleur de remplissage, style de ligne, etc.). Toutes les formes enfants conservent leurs propriétés d'origine.
- **Groupes imbriqués :** `GroupShape` peut contenir d'autres objets `GroupShape`, permettant des hiérarchies à plusieurs niveaux. Traitez simplement le groupe interne comme n'importe quelle autre forme.

## Ajouter des formes au groupe et les gérer ultérieurement

Si vous devez ajouter d'autres formes après la création du groupe initial, vous pouvez réutiliser la même instance `GroupShape` :

```csharp
// Assume we have a third shape somewhere in the document.
Shape thirdShape = (Shape)doc.GetChild(NodeType.Shape, 2, true);
groupShape.AppendChild(thirdShape);
```

Lorsque vous devez ensuite dégrouper, parcourez `groupShape.GetChildNodes(NodeType.Shape, true)` et réinsérez chaque enfant à l'endroit souhaité.

```csharp
foreach (Shape child in groupShape.GetChildNodes(NodeType.Shape, true))
{
    // Example: move each child back to the original paragraph.
    firstParagraph.AppendChild(child);
}
firstParagraph.RemoveChild(groupShape); // Remove the empty group container.
```

**Pourquoi c'est important :** Certains flux de travail nécessitent un groupement temporaire (par ex., aligner plusieurs objets) suivi d'un dégrouper pour des modifications individuelles ultérieures.

## Exemple complet exécutable

Ci‑dessus se trouve un programme autonome que vous pouvez compiler et exécuter tel quel. Remplacez `YOUR_DIRECTORY` par le chemin réel d'un dossier sur votre machine.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Load the document.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath);

        // 2. Retrieve the first two shapes.
        Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true);

        if (firstShape == null || secondShape == null)
        {
            Console.WriteLine("Document must contain at least two shapes.");
            return;
        }

        // 3. Create a GroupShape container.
        GroupShape groupShape = new GroupShape(doc);

        // Optional: define the group’s bounding box.
        groupShape.Bounds = new System.Drawing.RectangleF(100, 100, 300, 200);

        // 4. Add the shapes to the group.
        groupShape.AppendChild(firstShape);
        groupShape.AppendChild(secondShape);

        // 5. Insert the group into the first paragraph.
        Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(groupShape);

        // 6. Save the result.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Grouped shapes saved to {outputPath}");
    }
}
```

**Sortie attendue :** Lorsque vous ouvrez `output.docx`, les deux formes originales apparaissent comme un seul objet groupé. Sélectionner le groupe montre les poignées de groupement familières de Word, vous permettant de déplacer, redimensionner ou faire pivoter l'ensemble en même temps.

## Conclusion

Vous savez maintenant comment **regrouper des formes dans Word** en utilisant C# et Aspose.Words, et vous avez vu les étapes exactes pour **ajouter des formes à un groupe** puis les manipuler ou les dégrouper ultérieurement. Cette technique est idéale pour automatiser la mise en page de rapports, créer des diagrammes composites, ou préparer des modèles Word nécessitant un positionnement précis de plusieurs objets.

Ensuite, explorez des sujets connexes tels que **comment regrouper des formes** avec différents types d'ancrage, appliquer un **formatage avancé** aux objets groupés, ou exporter le résultat groupé en PDF. Expérimentez le nesting de groupes pour créer des graphiques complexes de façon programmatique.

Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Insérer des formes dans des documents Word avec Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Créer une forme de groupe dans un document Word avec Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Ajouter un effet d'ombre aux formes Word – Guide complet C#](/words/english/net/programming-with-shapes/add-shadow-effect-to-word-shapes-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}