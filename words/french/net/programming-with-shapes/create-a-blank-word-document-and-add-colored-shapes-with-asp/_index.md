---
category: general
date: 2026-09-21
description: Créer un document Word vierge avec Aspose.Words, définir la taille de
  la forme, définir la position de la forme, définir la couleur de la forme, puis
  enregistrer le fichier .docx en une seule démonstration.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set shape size
- save docx file
- set shape position
- set shape color
language: fr
lastmod: 2026-09-21
og_description: Créez un document Word vierge, définissez la taille de la forme, définissez
  la position de la forme, définissez la couleur de la forme, puis enregistrez le
  fichier docx avec Aspose.Words en quelques minutes.
og_image_alt: Screenshot of a blank Word document containing two colored rectangles
  grouped together
og_title: Créer un document Word vierge et ajouter des formes colorées – Guide Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create a blank Word document using Aspose.Words, set shape size, set
    shape position, set shape color, and save the docx file in a single walkthrough.
  headline: Create a blank Word document and add colored shapes with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Créer un document Word vierge et ajouter des formes colorées avec Aspose.Words
url: /fr/net/programming-with-shapes/create-a-blank-word-document-and-add-colored-shapes-with-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un document Word vierge et ajouter des formes colorées avec Aspose.Words

Si vous devez **créer un document Word vierge** de façon programmatique, ce guide vous montre comment le faire avec Aspose.Words. Vous apprendrez à **définir la taille d’une forme**, **définir la position d’une forme**, **définir la couleur d’une forme**, et enfin **enregistrer le fichier docx** sans quitter votre IDE.

Travailler avec des fichiers Word en C# implique souvent de manipuler des appels OpenXML de bas niveau, mais Aspose.Words abstrait cette complexité. À la fin de ce tutoriel, vous disposerez d’un fichier `.docx` pleinement fonctionnel contenant un groupe de formes composé de deux rectangles colorés — idéal pour des rapports, des certificats ou des modèles personnalisés.

## Prérequis

- .NET 6.0 ou supérieur (le code fonctionne également avec .NET Framework 4.7+)
- Aspose.Words for .NET 23.9 ou plus récent (installer via NuGet : `Install-Package Aspose.Words`)
- Connaissances de base en C# et Visual Studio (ou tout autre éditeur C#)

Aucun fichier Word existant n’est requis ; le tutoriel commence par **créer un document Word vierge** à partir de zéro.

## Créer un document Word vierge avec Aspose.Words

La première étape consiste à instancier un objet `Document`. Cet objet représente un fichier Word vide en mémoire.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty document.
Document document = new Document();

// DocumentBuilder gives you a cursor to add content.
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` commence vide, ce qui correspond exactement à ce dont vous avez besoin lorsque vous **créez un document Word vierge**. Le `builder` sera utilisé plus tard pour insérer le groupe de formes à la position actuelle du curseur.

## Définir la taille de la forme et créer un GroupShape

Un `GroupShape` fonctionne comme un conteneur pouvant contenir plusieurs formes individuelles. Commencez par définir les dimensions globales du conteneur.

```csharp
// Create a GroupShape that will hold multiple shapes.
// Width = 300 points, Height = 200 points.
GroupShape groupShape = new GroupShape(document, 300, 200);

// Position the group on the page: 100 points from the left, 100 points from the top.
groupShape.Left = 100;
groupShape.Top  = 100;
```

Ici nous **définissons la taille de la forme** pour le groupe lui‑même (300 × 200). Les mêmes noms de propriétés (`Width`, `Height`) sont utilisés pour chaque forme enfant, vous offrant un contrôle granulaire sur chaque élément.

## Ajouter le premier rectangle et définir la couleur de la forme

Ajoutez maintenant un rectangle au groupe et attribuez‑lui une couleur d’arrière‑plan.

```csharp
// First rectangle – light blue background.
Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 0,          // Position relative to the group’s left edge.
    Top = 0,           // Position relative to the group’s top edge.
    FillColor = Color.LightBlue
};

// Append the rectangle to the group.
groupShape.AppendChild(rectangle1);
```

La propriété `FillColor` **définit la couleur de la forme**. Utiliser `System.Drawing.Color` vous permet de choisir n’importe quelle valeur ARGB prédéfinie ou personnalisée.

## Ajouter un deuxième rectangle, définir sa taille, sa position et sa couleur

Un deuxième rectangle montre comment **définir la position de la forme** par rapport au groupe et comment changer sa couleur.

```csharp
// Second rectangle – light coral background.
Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 150,               // 150 points to the right of the group’s left edge.
    Top = 0,                  // Same vertical alignment as the first rectangle.
    FillColor = Color.LightCoral
};

groupShape.AppendChild(rectangle2);
```

Comme la largeur du groupe est de 300 points, les deux rectangles de 120 points s’ajustent confortablement avec un écart de 30 points. Ajustez `Left` et `Top` si vous avez besoin d’une disposition différente.

## Insérer le GroupShape dans le document

Une fois le groupe entièrement configuré, placez‑le à la position actuelle du curseur.

```csharp
// Insert the completed group shape at the builder’s current location.
builder.InsertNode(groupShape);
```

`InsertNode` écrit la forme directement dans le corps du document, en conservant la **position de forme définie** précédemment.

## Enregistrer le fichier docx

L’étape finale consiste à persister le document sur le disque. Cela illustre l’opération **enregistrer le fichier docx**.

```csharp
// Define the output path (ensure the directory exists).
string outputPath = @"C:\Temp\GroupShape.docx";

// Save the document in DOCX format.
document.Save(outputPath);
```

Après l’exécution du programme, ouvrez `GroupShape.docx` dans Microsoft Word. Vous devriez voir une page blanche contenant un groupe de formes avec deux rectangles colorés positionnés côte à côte.

### Résultat attendu

- Un fichier `.docx` d’une seule page.
- La page contient un groupe de formes situé à 100 pts des marges gauche et supérieure.
- À l’intérieur du groupe, un rectangle bleu clair se trouve à gauche, et un rectangle corail clair à droite, chacun mesurant 120 × 80 pts.

## Exemple complet, exécutable

Voici le programme complet que vous pouvez copier‑coller dans une application console. Aucun fichier supplémentaire n’est requis.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Define a GroupShape and set its size and position.
        GroupShape groupShape = new GroupShape(document, 300, 200)
        {
            Left = 100,
            Top = 100
        };

        // 3️⃣ First rectangle – set size, position, and color.
        Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 0,
            Top = 0,
            FillColor = Color.LightBlue
        };
        groupShape.AppendChild(rectangle1);

        // 4️⃣ Second rectangle – set size, position, and color.
        Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 150,
            Top = 0,
            FillColor = Color.LightCoral
        };
        groupShape.AppendChild(rectangle2);

        // 5️⃣ Insert the grouped shape into the document.
        builder.InsertNode(groupShape);

        // 6️⃣ Save the docx file.
        string outputPath = @"C:\Temp\GroupShape.docx";
        document.Save(outputPath);

        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

L’exécution de ce programme crée le document exactement comme décrit précédemment, remplissant les quatre objectifs : **créer un document Word vierge**, **définir la taille de la forme**, **définir la position de la forme**, **définir la couleur de la forme**, et **enregistrer le fichier docx**.

## Variations courantes et cas limites

| Scénario | Ce qu’il faut modifier | Pourquoi c’est important |
|----------|------------------------|---------------------------|
| **Différents types de forme** | Remplacer `ShapeType.Rectangle` par `ShapeType.Ellipse`, `ShapeType.Triangle`, etc. | Vous permet de créer des graphiques plus complexes sans images externes. |
| **Dimensions dynamiques** | Calculer `Width` et `Height` à partir d’une saisie utilisateur ou de fichiers de configuration. | Rend la solution réutilisable sur plusieurs modèles de documents. |
| **Enregistrement en PDF** | Appeler `document.Save("output.pdf", SaveFormat.Pdf);` | Si les destinataires ont besoin d’un format non modifiable, le PDF est une option sûre. |
| **Ajouter du texte dans une forme** | Créer une forme `TextBox` et définir `TextBox.Text`. | Utile pour créer des badges ou des infobulles étiquetés. |
| **Plusieurs groupes sur une même page** | Répéter les étapes 2‑5 avec des valeurs `Left`/`Top` différentes. | Vous permet de construire des tableaux de bord ou des mises en page multi‑sections. |

### Astuce de pro

Lorsque vous devez aligner les formes avec précision, utilisez la propriété `ShapeBase.WrapType = WrapType.Inline` avant d’insérer le groupe. Cela force le groupe à se comporter comme un paragraphe, empêchant un flux de texte inattendu autour de celui‑ci.

## Conclusion

Vous savez maintenant comment **créer un document Word vierge** avec Aspose.Words, **définir la taille d’une forme**, **définir la position d’une forme**, **définir la couleur d’une forme**, et **enregistrer le fichier docx**. L’exemple complet montre un modèle propre et réutilisable pour ajouter des graphiques groupés à tout projet d’automatisation Word.

À partir d’ici, vous pouvez explorer :

- Ajouter d’autres formes ou images au même `GroupShape` (variations de **définir la taille de la forme**, **définir la couleur de la forme**).
- Utiliser `ShapeBase.Rotation` pour faire pivoter les rectangles à des fins décoratives.
- Exporter le même document en PDF ou HTML pour élargir la distribution (alternative **enregistrer le fichier docx**).

N’hésitez pas à expérimenter avec différentes couleurs, tailles et logiques de mise en page pour répondre à vos besoins spécifiques en matière de rapports ou de modèles. Bon codage !

## Que devez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets et fonctionnels avec des explications pas à pas pour vous aider à maîtriser des fonctionnalités API supplémentaires et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}