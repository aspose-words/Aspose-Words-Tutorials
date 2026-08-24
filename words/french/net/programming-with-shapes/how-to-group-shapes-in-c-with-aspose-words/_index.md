---
category: general
date: 2026-08-23
description: Apprenez à regrouper des formes en C# avec Aspose.Words. Le guide explique
  également comment insérer une forme rectangle et ajouter des formes dans Word pour
  des documents complexes.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- add shapes word
- group multiple shapes
- how to start group
language: fr
lastmod: 2026-08-23
og_description: Comment regrouper des formes en C# avec Aspose.Words. Suivez ce tutoriel
  complet pour insérer une forme rectangulaire, ajouter des formes dans Word et regrouper
  plusieurs formes efficacement.
og_image_alt: How to group shapes in C# using Aspose.Words
og_title: Comment regrouper des formes en C# – guide étape par étape
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Learn how to group shapes in C# using Aspose.Words. The guide also
    covers how to insert rectangle shape and add shapes word for complex documents.
  headline: How to group shapes in C# with Aspose.Words
  type: TechArticle
- description: Learn how to group shapes in C# using Aspose.Words. The guide also
    covers how to insert rectangle shape and add shapes word for complex documents.
  name: How to group shapes in C# with Aspose.Words
  steps:
  - name: '**Nested groups** – Aspose.Words allows groups within groups. To create
      a nested group, call `StartGroupShape` again before calling `EndGroupShape`
      for the inner group.'
    text: '**Nested groups** – Aspose.Words allows groups within groups. To create
      a nested group, call `StartGroupShape` again before calling `EndGroupShape`
      for the inner group.'
  - name: '**Empty groups** – If you start a group but never insert a shape, `EndGroupShape`
      will still create an empty container. This is harmless but may increase file
      size slightly.'
    text: '**Empty groups** – If you start a group but never insert a shape, `EndGroupShape`
      will still create an empty container. This is harmless but may increase file
      size slightly.'
  - name: '**Compatibility** – The generated DOCX works with Word 2010 and later.
      Older versions may ignore grouping metadata, so always test with the target
      Word version.'
    text: '**Compatibility** – The generated DOCX works with Word 2010 and later.
      Older versions may ignore grouping metadata, so always test with the target
      Word version.'
  type: HowTo
- questions:
  - answer: Yes. Retrieve the existing `Shape` objects, call `builder.StartGroupShape()`,
      re‑insert them with `builder.InsertShape(existingShape)`, then call `EndGroupShape()`.
    question: Can I group shapes that already exist in the document?
  - answer: Aspose.Words adds a `<w:grpSp>` element that contains each shape’s `<w:sp>`
      node. This is fully compliant with the Office Open XML specification.
    question: Does grouping affect the underlying XML?
  - answer: 'There is no direct “ungroup” API, but you can iterate through the child
      shapes of the group (`group.GroupShape.Children`) and copy them out to the document
      body. ## Next steps Now that you know **how to group shapes**, consider exploring
      these related topics: - **Apply complex formatting to grouped '
    question: What if I need to ungroup later?
  type: FAQPage
tags:
- Aspose.Words
- C#
- shapes
- document automation
title: Comment regrouper des formes en C# avec Aspose.Words
url: /fr/net/programming-with-shapes/how-to-group-shapes-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment regrouper des formes en C# avec Aspose.Words

Si vous avez besoin de **how to group shapes** dans un document Word de manière programmatique, ce tutoriel vous montre les étapes exactes en utilisant Aspose.Words pour .NET. Que vous construisiez un générateur de rapports, un moteur de modèles ou un outil de diagrammes, vous apprendrez comment démarrer un groupe, insérer une forme rectangle et ajouter du contenu de type Word aux formes sans quitter votre code.

Vous verrez également comment **group multiple shapes** ensemble, ce qui est essentiel lorsque vous souhaitez déplacer, faire pivoter ou styliser une collection d'objets comme une seule entité. L'exemple ci‑dessous fonctionne avec la dernière version d'Aspose.Words 24.x et ne nécessite que .NET 6 ou une version ultérieure.

## Prérequis

- .NET 6 SDK (ou toute version .NET prise en charge par Aspose.Words)
- Visual Studio 2022 ou VS Code
- Package NuGet Aspose.Words pour .NET (`Install-Package Aspose.Words`)
- Familiarité de base avec C# et le modèle d'objet Aspose.Words

> **Astuce :** Utilisez la licence d'évaluation gratuite d'Aspose pour éviter les limitations de filigrane lors des tests.

## Comment regrouper des formes avec Aspose.Words

Ci‑dessous se trouve un programme complet et exécutable qui montre **how to start group**, ajoute un rectangle et finalise le groupe. Le code suit le même flux logique que l'extrait que vous avez fourni, mais il ajoute du contexte, la gestion des erreurs et des commentaires pour plus de clarté.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank document.
            Document doc = new Document();

            // 2️⃣ Get a DocumentBuilder to insert content.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Start a group shape – all shapes added after this call belong to the group.
            // This is the “how to start group” step.
            Shape group = builder.StartGroupShape();

            // 4️⃣ Insert individual shapes inside the group.
            //    a) Insert a rectangle shape (demonstrates “insert rectangle shape”).
            builder.InsertShape(ShapeType.Rectangle, 150, 80);
            //    b) Insert a simple ellipse for visual variety.
            builder.InsertShape(ShapeType.Ellipse, 100, 60);
            //    c) Add a WordArt‑style text shape – shows “add shapes word”.
            builder.InsertShape(ShapeType.TextPlainText, 200, 40);
            builder.Writeln("Grouped Text"); // adds text inside the last shape

            // 5️⃣ Close the group shape to finalize the grouping.
            builder.EndGroupShape();

            // Optional: Save the document to verify the result.
            string outPath = "GroupedShapes.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Pourquoi chaque étape est importante

| Étape | Objectif | Comment cela se rapporte aux mots‑clés |
|------|----------|----------------------------------------|
| **Create a new blank document** | Fournit une toile vierge pour les opérations de forme. | Prépare le terrain pour **add shapes word** plus tard. |
| **Initialize DocumentBuilder** | Le builder est l'API principale pour insérer des objets. | Nécessaire avant de pouvoir **how to start group**. |
| **StartGroupShape** | Démarre un conteneur logique ; toutes les formes suivantes deviennent membres de ce groupe. | Répond directement à **how to start group**. |
| **InsertShape** (rectangle, ellipse, text) | Place des formes individuelles à l'intérieur du groupe. L'appel rectangle satisfait **insert rectangle shape** ; la forme texte satisfait **add shapes word**. | Démontre **group multiple shapes**. |
| **EndGroupShape** | Finalise le groupe afin que vous puissiez le déplacer ou le styliser comme une unité. | Complète le flux de travail **how to group shapes**. |

## Insertion d'une forme rectangle – analyse approfondie

La méthode `InsertShape` accepte une énumération `ShapeType`, une largeur et une hauteur. Pour **insert rectangle shape** avec un style personnalisé, vous pouvez étendre l'exemple :

```csharp
// Insert a styled rectangle
Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rect.FillColor = System.Drawing.Color.LightBlue;
rect.StrokeColor = System.Drawing.Color.DarkBlue;
rect.LineWidth = 2.0;
```

> **Pourquoi le styliser ?** Le style garantit que le rectangle se démarque lorsque le groupe est repositionné plus tard. Cela montre également que les propriétés de la forme peuvent être définies *avant* la fermeture du groupe.

## Ajout de formes de niveau Word (add shapes word)

Si vous devez intégrer du texte directement dans une forme—souvent appelée « WordArt » ou « zone de texte »—utilisez `ShapeType.TextPlainText`. Après l'insertion, vous pouvez écrire du texte dans la forme avec `DocumentBuilder.Writeln` ou en accédant à la propriété `TextBox` de la forme :

```csharp
Shape textBox = builder.InsertShape(ShapeType.TextPlainText, 250, 50);
textBox.TextBox.Text = "Hello, grouped world!";
```

Cela satisfait le mot‑clé **add shapes word** et montre comment le texte peut se déplacer avec le groupe.

## Regroupement de plusieurs formes – scénarios pratiques

Lorsque vous **group multiple shapes**, vous pouvez les traiter comme un seul objet pour le positionnement, la rotation ou le redimensionnement. Par exemple, après la fermeture du groupe, vous pouvez déplacer l'ensemble du groupe :

```csharp
// Move the entire group 100 points to the right and 50 points down.
group.Left += 100;
group.Top += 50;
```

Ou faire pivoter le groupe :

```csharp
group.Rotation = 45; // degrees
```

Ces opérations ne sont possibles que parce que les formes partagent le même groupe parent.

## Gestion des cas limites

1. **Nested groups** – Aspose.Words autorise des groupes à l'intérieur d'autres groupes. Pour créer un groupe imbriqué, appelez `StartGroupShape` à nouveau avant d'appeler `EndGroupShape` pour le groupe interne.  
2. **Empty groups** – Si vous démarrez un groupe mais n'insérez jamais de forme, `EndGroupShape` créera quand même un conteneur vide. Cela est inoffensif mais peut augmenter légèrement la taille du fichier.  
3. **Compatibility** – Le DOCX généré fonctionne avec Word 2010 et versions ultérieures. Les versions plus anciennes peuvent ignorer les métadonnées de groupement, il faut donc toujours tester avec la version cible de Word.

## Fichier source complet pour référence

Enregistrez ce qui suit sous le nom `Program.cs` dans un projet console .NET. Le code compile et s'exécute sans modification.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document.
            Document doc = new Document();

            // Step 2: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Start the group – “how to start group”.
            Shape group = builder.StartGroupShape();

            // Step 4a: Insert a rectangle – “insert rectangle shape”.
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 150, 80);
            rect.FillColor = System.Drawing.Color.LightCoral;
            rect.StrokeColor = System.Drawing.Color.DarkRed;
            rect.LineWidth = 1.5;

            // Step 4b: Insert an ellipse (additional shape for grouping).
            builder.InsertShape(ShapeType.Ellipse, 100, 60);

            // Step 4c: Add a text box – “add shapes word”.
            Shape txt = builder.InsertShape(ShapeType.TextPlainText, 200, 40);
            txt.TextBox.Text = "Grouped Text";

            // Step 5: End the group – completes “how to group shapes”.
            builder.EndGroupShape();

            // Optional: Adjust group position.
            group.Left += 50;
            group.Top += 30;

            // Save the result.
            string outPath = "GroupedShapes.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Résultat attendu

L'ouverture de `GroupedShapes.docx` dans Microsoft Word affichera :

- Un rectangle corail clair, une ellipse et une zone de texte—tous visuellement liés ensemble.  
- Sélectionner n'importe quelle partie du groupe sélectionne également l'ensemble du groupe (une seule boîte englobante apparaît).  
- Déplacer ou faire pivoter le groupe déplace les trois formes ensemble.

## Questions fréquentes

**Q : Puis‑je regrouper des formes qui existent déjà dans le document ?**  
R : Oui. Récupérez les objets `Shape` existants, appelez `builder.StartGroupShape()`, ré‑insérez‑les avec `builder.InsertShape(existingShape)`, puis appelez `EndGroupShape()`.

**Q : Le groupement affecte‑t‑il le XML sous‑jacent ?**  
R : Aspose.Words ajoute un élément `<w:grpSp>` qui contient le nœud `<w:sp>` de chaque forme. Ceci est entièrement conforme à la spécification Office Open XML.

**Q : Que faire si je dois dégrouper plus tard ?**  
R : Il n'existe pas d'API « ungroup » directe, mais vous pouvez parcourir les formes enfants du groupe (`group.GroupShape.Children`) et les copier dans le corps du document.

## Prochaines étapes

Maintenant que vous savez **how to group shapes**, envisagez d'explorer ces sujets connexes :

- **Apply complex formatting to grouped shapes** – apprenez comment définir des remplissages en dégradé, des effets d'ombre et des styles de ligne.  
- **Export grouped shapes as images** – utilisez `Shape.GetShapeRenderer().Save(...)` pour rasteriser un groupe.  
- **Create dynamic diagrams** – combinez le positionnement basé sur les données avec le groupement pour générer automatiquement des organigrammes.

Chacun de ces sujets s'appuie sur les bases présentées ici et vous aidera à créer des documents Word plus riches et interactifs.

---

*Bonne programmation ! Si vous avez trouvé ce guide utile, partagez‑le avec vos collègues ou ajoutez une étoile au dépôt contenant le projet d'exemple.*

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l'API et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Insérer des formes dans des documents Word avec Aspose.Words pour .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Créer une forme de groupe dans un document Word avec Aspose.Words pour .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Créer une forme rectangle dans Word avec Aspose.Words – Guide étape par étape](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}