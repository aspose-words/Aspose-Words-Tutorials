---
category: general
date: 2026-07-23
description: Créez un document Word vierge et ajoutez une forme rectangulaire en C#.
  Apprenez comment insérer des formes et regrouper des formes Word à l'aide d'Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- group shapes word
- how to insert shapes
- how to group shapes
language: fr
lastmod: 2026-07-23
og_description: Créez un document Word vierge en C# et apprenez à insérer des formes,
  ajouter une forme rectangle et regrouper des formes Word avec Aspose.Words.
og_image_alt: Screenshot showing a blank Word document with two rectangle shapes grouped
  together
og_title: Créer un document Word vierge avec des rectangles groupés – Tutoriel C#
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: Create blank word document and add rectangle shape in C#. Learn how
    to insert shapes and group shapes word using Aspose.Words.
  headline: Create blank word document with grouped rectangles – C# guide
  type: TechArticle
- description: Create blank word document and add rectangle shape in C#. Learn how
    to insert shapes and group shapes word using Aspose.Words.
  name: Create blank word document with grouped rectangles – C# guide
  steps:
  - name: What if I need more than two shapes?
    text: Just keep calling `builder.InsertShape(...)` and `group.AppendChild(...)`
      for each new shape. The group can hold any number of children.
  - name: Can I set fill colour or border on the rectangles?
    text: 'Absolutely. After creating a rectangle you can tweak its `FillColor`, `OutlineColor`,
      and `LineWidth`:'
  - name: How do I move the whole group after it’s been created?
    text: 'Use the group''s `Left` and `Top` properties, measured in points:'
  - name: What about scaling the group?
    text: Set `group.Width` and `group.Height` or use `group.ScaleX` / `group.ScaleY`.
      The child rectangles retain their proportions relative to the group.
  - name: Does this work with older .doc files?
    text: Aspose.Words abstracts the file format, so the same code works for `.doc`
      and `.docx`. The only limitation is that some newer shape features may be down‑sampled
      when saving to the older binary format.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Créer un document Word vierge avec des rectangles groupés – Guide C#
url: /fr/java/images-shapes/create-blank-word-document-with-grouped-rectangles-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un document Word vierge avec des rectangles groupés – Guide C#  

Vous avez déjà eu besoin de **créer un document Word vierge** contenant déjà un ensemble de formes, mais vous ne saviez pas comment les regrouper proprement ? Vous n'êtes pas le seul. Dans de nombreux scénarios de reporting ou de génération de modèles, vous souhaitez une toile propre avec quelques rectangles servant de zones réservées, et vous aimeriez qu'ils se déplacent ensemble comme une seule unité.

Dans ce tutoriel, nous parcourrons les étapes exactes pour **créer un document Word vierge**, **ajouter une forme rectangle**, puis **regrouper des formes Word** en utilisant la bibliothèque Aspose.Words. À la fin, vous disposerez d’un fichier `.docx` prêt à l’emploi où les deux rectangles font partie d’un groupe, de sorte que tout repositionnement ou redimensionnement ultérieur les affecte tous les deux simultanément.

Nous répondrons également aux questions courantes « **how to insert shapes** » et « **how to group shapes** » qui apparaissent sur les forums et Stack Overflow. Aucun document externe n’est requis — tout ce dont vous avez besoin se trouve ici.

---

## Prérequis

- .NET 6 ou ultérieur (le code se compile également avec .NET Core)  
- Aspose.Words pour .NET (package NuGet `Aspose.Words`)  
- Une compréhension de base de la syntaxe C# (si vous avez écrit un « Hello World », vous êtes bon)  

Si vous n’avez pas encore installé Aspose.Words, exécutez :

```bash
dotnet add package Aspose.Words
```

C’est tout — pas de DLL supplémentaires, pas d’interop COM, juste une référence NuGet propre.

---

## Étape 1 : Créer un document Word vierge et initialiser le builder

La première chose que nous faisons est de créer un objet `Document` vide. Considérez-le comme une feuille blanche. Ensuite, nous attachons un `DocumentBuilder`, qui est l’outil pratique fourni par Aspose pour insérer du contenu.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document doc = new Document();               // <-- create blank word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Pourquoi c’est important :** Sans `DocumentBuilder`, vous devriez manipuler manuellement l’arbre de nœuds de bas niveau, ce qui est source d’erreurs. Le builder abstrait les complexités XML d’un fichier `.docx`.

---

## Étape 2 : Comment insérer des formes – ajouter d’abord un conteneur de groupe

Aspose vous permet d’insérer une *forme de groupe* qui pourra ensuite contenir d’autres formes. C’est la base pour **group shapes word**.

```csharp
        // Step 2: Insert a group shape that will act as a container
        Shape group = builder.InsertGroupShape();
```

> **Astuce :** Le groupe lui‑-même est invisible tant que vous n’ajoutez pas de formes enfants, vous ne verrez donc aucun artefact dans le document résultant avant l’étape suivante.

---

## Étape 3 : Ajouter une forme rectangle – les objets réellement visibles

Nous allons maintenant **ajouter une forme rectangle** deux fois, chacune avec sa propre taille. La méthode `InsertShape` prend un `ShapeType` et des dimensions en points (1 pt ≈ 1/72 pouce).

```csharp
        // Step 3: Insert two rectangle shapes with desired dimensions
        Shape rect1 = builder.InsertShape(ShapeType.Rectangle, 100, 50); // 100 pt × 50 pt
        Shape rect2 = builder.InsertShape(ShapeType.Rectangle, 80, 40);  // 80 pt × 40 pt
```

> **Pourquoi des rectangles ?** Ce sont les formes géométriques les plus simples, parfaites pour des zones réservées, des maquettes d’interface type bouton, ou des éléments graphiques simples.

---

## Étape 4 : Comment regrouper des formes – attacher les rectangles au groupe

Avec les rectangles créés, nous allons maintenant **regrouper les formes** en les ajoutant comme enfants de la forme de groupe que nous avons insérée précédemment.

```csharp
        // Step 4: Append the rectangles to the group shape
        group.AppendChild(rect1);
        group.AppendChild(rect2);
```

> **Que se passe-t-il en coulisses ?** La forme de groupe devient le nœud parent dans l’arbre XML du document. Déplacer le groupe déplace les deux rectangles ensemble, en préservant leurs positions relatives.

---

## Étape 5 : Enregistrer le document – vous avez maintenant un fichier Word avec des formes groupées

Enfin, nous enregistrons le document sur le disque. Modifiez le chemin vers un emplacement qui existe sur votre machine.

```csharp
        // Step 5: Save the document with the grouped shapes
        doc.Save("GroupShape.docx");   // Creates a blank word document with grouped rectangles
    }
}
```

C’est tout le programme. Exécutez‑le, ouvrez `GroupShape.docx`, et vous verrez deux rectangles côte à côte. Si vous en sélectionnez un, tout le groupe est mis en surbrillance — exactement ce que **group shapes word** est censé faire.

---

## Code source complet en un seul endroit

Pour plus de commodité, voici l’exemple complet, prêt à copier‑coller :

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a group shape that will contain other shapes
        Shape group = builder.InsertGroupShape();

        // Insert two rectangle shapes with desired dimensions
        Shape rect1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        Shape rect2 = builder.InsertShape(ShapeType.Rectangle, 80, 40);

        // Add the rectangles to the group shape
        group.AppendChild(rect1);
        group.AppendChild(rect2);

        // Save the document
        doc.Save("GroupShape.docx");
    }
}
```

**Résultat attendu :** L’ouverture de `GroupShape.docx` affiche une page blanche avec deux rectangles groupés. Sélectionner un rectangle sélectionne automatiquement l’autre, confirmant que le groupement a réussi.

---

## Questions fréquentes & gestion des cas limites

### Et si j’ai besoin de plus de deux formes ?

Continue simplement d’appeler `builder.InsertShape(...)` et `group.AppendChild(...)` pour chaque nouvelle forme. Le groupe peut contenir un nombre illimité d’enfants.

### Puis‑je définir la couleur de remplissage ou la bordure des rectangles ?

Absolument. Après avoir créé un rectangle, vous pouvez ajuster son `FillColor`, `OutlineColor` et `LineWidth` :

```csharp
rect1.FillColor = System.Drawing.Color.LightBlue;
rect1.OutlineColor = System.Drawing.Color.DarkBlue;
rect1.LineWidth = 1.5;
```

### Comment déplacer tout le groupe après sa création ?

Utilisez les propriétés `Left` et `Top` du groupe, mesurées en points :

```csharp
group.Left = 150;   // move 150 pt from the left margin
group.Top  = 200;   // move 200 pt from the top of the page
```

### Et le redimensionnement du groupe ?

Définissez `group.Width` et `group.Height` ou utilisez `group.ScaleX` / `group.ScaleY`. Les rectangles enfants conservent leurs proportions par rapport au groupe.

### Cela fonctionne‑t‑il avec les anciens fichiers .doc ?

Aspose.Words abstrait le format de fichier, ainsi le même code fonctionne pour `.doc` et `.docx`. La seule limitation est que certaines fonctionnalités de forme plus récentes peuvent être réduites lors de l’enregistrement au format binaire plus ancien.

---

## Astuces pro pour un code prêt à la production

- **Libérer les ressources** – Enveloppez `Document` dans un bloc `using` si vous manipulez de gros fichiers afin de libérer rapidement la mémoire.  
- **Gestion des erreurs** – Capturez `Aspose.Words.Fonts.FontSettingsException` si vous prévoyez d’intégrer des polices personnalisées.  
- **Performance** – Lors de l’insertion de nombreuses formes, désactivez temporairement les mises à jour de mise en page avec `doc.LayoutOptions = new LayoutOptions { UpdateFields = false };` puis réactivez-les ensuite.

---

## Conclusion

Vous savez maintenant **comment créer un document Word vierge**, **ajouter une forme rectangle**, et **regrouper des formes Word** en utilisant Aspose.Words en C#. L’exemple couvre les étapes essentielles « **how to insert shapes** » et « **how to group shapes** », explique pourquoi chaque ligne existe, et aborde même la personnalisation, les cas limites et les bonnes pratiques.

Ensuite, vous pourriez explorer **how to insert images**, **add text inside grouped shapes**, ou **export the document to PDF** — tous suivant le même schéma d’utilisation de `DocumentBuilder` et de la manipulation des formes. Continuez à expérimenter ; l’API Aspose est suffisamment riche pour gérer presque tous les scénarios d’automatisation Word que vous pouvez imaginer.

Bon codage, et n’hésitez pas à laisser un commentaire si vous rencontrez des problèmes !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code fonctionnels complets avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}