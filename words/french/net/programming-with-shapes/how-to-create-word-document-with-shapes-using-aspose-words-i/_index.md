---
category: general
date: 2026-09-11
description: Apprenez à créer un document Word, ajouter une forme rectangle et définir
  les dimensions de la forme avec Aspose.Words. Guide C# étape par étape pour un dimensionnement
  précis des formes.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- add rectangle shape
- set shape size
- create shapes in word
- set shape dimensions
language: fr
lastmod: 2026-09-11
og_description: Créer un document Word avec Aspose.Words en C#. Ce guide montre comment
  ajouter une forme rectangulaire, définir la taille de la forme et gérer les dimensions
  de la forme de manière programmatique.
og_image_alt: Screenshot of a rectangle shape inside a grouped shape in a newly created
  Word document
og_title: Créer un document Word avec des formes – Tutoriel Aspose.Words C#
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document, add rectangle shape, and set shape
    dimensions with Aspose.Words. Step‑by‑step C# guide for precise shape sizing.
  headline: How to create word document with shapes using Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Comment créer un document Word avec des formes en utilisant Aspose.Words en
  C#
url: /fr/net/programming-with-shapes/how-to-create-word-document-with-shapes-using-aspose-words-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer un document Word avec des formes à l'aide d'Aspose.Words en C#

Si vous devez **créer un document Word** contenant des graphiques personnalisés, vous pouvez le faire entièrement en code. Ce tutoriel vous guide à travers la création d’un fichier Word, l’ajout d’une forme rectangulaire et le contrôle de chaque dimension de la forme. À la fin, vous disposerez d’un extrait réutilisable que vous pourrez intégrer à n’importe quel projet .NET.

Vous apprendrez comment **ajouter une forme rectangulaire**, **définir la taille de la forme**, et **définir les dimensions de la forme** à l’intérieur d’un conteneur groupé. L’exemple utilise Aspose.Words 13.9, mais les concepts s’appliquent également aux versions ultérieures. Aucune expérience préalable avec l’API de dessin Aspose n’est requise—seules des connaissances de base en C# sont nécessaires.

## Prérequis

- .NET 6.0 ou version ultérieure installé  
- Package NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)  
- Un IDE tel que Visual Studio 2022 (tout éditeur supportant le C# convient)  

Avoir ces outils prêts vous permet d’exécuter le code immédiatement sans configuration supplémentaire.

## Étape 1 : Initialiser le document et le builder – créer les bases d’un document Word

La première opération consiste à instancier un objet `Document` et un `DocumentBuilder`. Le `Document` représente le fichier lui‑-même, tandis que le `DocumentBuilder` fournit une API fluide pour insérer du contenu.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Create a new, empty Word document
        Document doc = new Document();

        // DocumentBuilder gives us a cursor to insert nodes
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Pourquoi c’est important :**  
Créer le document dès le départ vous donne une toile propre. Le curseur du builder commence au premier paragraphe, c’est là que nous **créerons des formes dans Word** plus tard.

## Étape 2 : Construire un GroupShape pour contenir plusieurs graphiques

Un `GroupShape` agit comme un conteneur ; vous pouvez déplacer, faire pivoter ou redimensionner l’ensemble du groupe comme une seule unité. Ici nous définissons la largeur et la hauteur du conteneur en points (1 pt ≈ 1/72 po).

```csharp
        // Define a group that is 300 pt wide and 200 pt high
        GroupShape group = new GroupShape(doc, 300, 200);

        // Position the group 50 pt from the left and top margins
        group.Left = 50;
        group.Top  = 50;
```

**Pourquoi c’est important :**  
Regrouper les formes simplifie la gestion de la mise en page. Si vous devez ajouter d’autres formes ultérieurement (par ex. des cercles ou des zones de texte), elles hériteront de la position et de l’échelle du groupe.

## Étape 3 : Créer une forme rectangulaire et configurer ses dimensions

Nous ajoutons maintenant le rectangle réel. Le constructeur `Shape` nécessite la référence du document et le type de forme. Après la création, nous **définissons explicitement la taille de la forme** et **définissons les dimensions de la forme**.

```csharp
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);

        // Set the rectangle’s width to 100 pt and height to 50 pt
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height

        // Position the rectangle 10 pt from the group’s left/top edges
        rectangle.Left = 10;
        rectangle.Top  = 10;
```

**Pourquoi c’est important :**  
Spécifier la largeur, la hauteur, la position gauche et supérieure vous donne un contrôle pixel‑perfect sur la forme. Ceci est essentiel lorsque le document doit respecter une spécification de conception ou un formulaire imprimé.

## Étape 4 : Assembler le groupe en ajoutant le rectangle

L’ajout du rectangle au `GroupShape` en fait un nœud enfant. Vous pouvez ajouter autant d’enfants que nécessaire avant d’insérer le groupe dans le document.

```csharp
        // Add the rectangle to the group
        group.AppendChild(rectangle);
```

**Astuce :** Si vous prévoyez d’ajouter une deuxième forme, créez‑la de la même manière et appelez `group.AppendChild(secondShape)`. Tous les enfants partagent le système de coordonnées du groupe.

## Étape 5 : Insérer la forme groupée dans le document et enregistrer

Une fois le groupe entièrement construit, nous le plaçons dans le paragraphe courant. La propriété `CurrentParagraph` du builder donne un accès direct à l’arbre de nœuds sous‑jacent.

```csharp
        // Insert the group into the first paragraph of the document
        builder.CurrentParagraph.AppendChild(group);

        // Save the document to disk (adjust the path as needed)
        doc.Save("GroupShape.docx");

        // Optional: open the file automatically (Windows only)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**Pourquoi c’est important :**  
Ajouter le groupe à un paragraphe garantit que la forme apparaît en ligne avec le flux du texte. Enregistrer le document finalise l’opération **create word document**.

## Variantes courantes et cas particuliers

| Scénario | Ajustement |
|----------|------------|
| **Orientation de page différente** | Définissez `doc.FirstSection.PageSetup.Orientation = Orientation.Landscape;` avant de créer le groupe. |
| **Plusieurs rectangles** | Créez des objets `Shape` supplémentaires et appelez `group.AppendChild(newRect)` pour chacun. |
| **Taille dynamique basée sur le contenu** | Calculez la largeur/hauteur à partir des dimensions d’une image ou des métriques du texte, puis assignez à `rectangle.Width` / `rectangle.Height`. |
| **Exportation en PDF** | Après `doc.Save`, appelez `doc.Save("GroupShape.pdf", SaveFormat.Pdf);`. |
| **Compatibilité avec les versions plus anciennes de Word** | Enregistrez avec `SaveFormat.Doc` au lieu de `Docx` pour la compatibilité Word 97‑2003. |

Ces variantes illustrent comment la même logique de base peut être adaptée à de nombreux besoins réels.

## Exemple complet, exécutable

Voici le programme complet que vous pouvez copier, coller et exécuter. Il comprend toutes les directives `using`, un point d’entrée `Main`, et des commentaires expliquant chaque ligne.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Define a group shape (300 pt × 200 pt) positioned at (50, 50)
        GroupShape group = new GroupShape(doc, 300, 200);
        group.Left = 50;
        group.Top  = 50;

        // 3️⃣ Create a rectangle (100 pt × 50 pt) positioned at (10, 10) inside the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height
        rectangle.Left = 10;
        rectangle.Top  = 10;

        // 4️⃣ Add the rectangle to the group
        group.AppendChild(rectangle);

        // 5️⃣ Insert the group into the first paragraph and save the file
        builder.CurrentParagraph.AppendChild(group);
        doc.Save("GroupShape.docx");

        // Open the resulting file automatically (optional)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**Résultat attendu :**  
Lorsque vous ouvrez *GroupShape.docx*, la première page affiche un rectangle à bord gris positionné à 50 pt du bord gauche/haut, le rectangle lui‑même étant décalé de 10 pt à l’intérieur du groupe. Les dimensions correspondent aux valeurs définies dans le code.

## Conclusion

Vous savez maintenant comment **create word document**, **add rectangle shape**, et définir précisément **shape size** ainsi que **shape dimensions** à l’aide d’Aspose.Words. L’approche du groupe de formes maintient votre mise en page flexible et prête pour de futures extensions telles que des graphiques supplémentaires ou des zones de texte.

Ensuite, explorez des sujets connexes comme **create shapes in word** pour les cercles, les flèches ou les chemins SVG personnalisés, et apprenez à **set shape fill color** ou à **apply rotation**. Expérimentez avec différentes mesures pour voir comment Word rend les points versus les centimètres, et intégrez le code dans des pipelines de génération de documents plus larges.

Bon codage, et n’hésitez pas à adapter ce modèle à tout scénario d’automatisation de rapports ou de remplissage de formulaires que vous rencontrez !

## Que devriez‑vous apprendre ensuite ?


Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser d’autres fonctionnalités de l’API et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Créer une forme rectangulaire dans Word avec C# – Guide étape par étape](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Créer un document Word vierge avec une forme rectangulaire ombrée – Guide étape par étape](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Tutoriel Aspose.Words Shape Shadow – Ajouter une ombre à une forme Word en C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}