---
category: general
date: 2025-12-29
description: Créez une forme rectangulaire dans un document Word en utilisant Aspose.Words
  C#. Apprenez à définir la transparence de la forme, à régler la couleur de l'ombre
  et à enregistrer le document Word sans effort.
draft: false
keywords:
- create rectangle shape
- set shape transparency
- set shadow color
- save word document
- create word document
language: fr
og_description: Créer une forme rectangulaire dans un document Word avec Aspose.Words
  C#. Ce guide montre comment définir la transparence de la forme, définir la couleur
  de l’ombre et enregistrer le document Word.
og_title: Créer une forme rectangulaire dans Word – Tutoriel complet Aspose.Words
tags:
- Aspose.Words
- C#
- Word Automation
title: Créer une forme rectangulaire dans Word avec Aspose.Words – Guide étape par
  étape
url: /fr/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer une forme rectangulaire dans Word – Tutoriel complet Aspose.Words

Vous avez déjà eu besoin de **créer une forme rectangulaire** dans un document Word mais vous ne saviez pas par où commencer ? Vous n'êtes pas seul ; de nombreux développeurs rencontrent ce problème lorsqu'ils automatisent des rapports ou des factures. Dans ce guide, nous passerons en revue les étapes exactes pour créer une forme rectangulaire, définir la transparence de la forme, définir la couleur de l'ombre, et enfin **enregistrer le document Word** en utilisant Aspose.Words pour .NET.  

Nous couvrirons tout, depuis l'objet document initial jusqu'au fichier `.docx` final sur le disque, de sorte qu'à la fin vous pourrez **créer un document Word** de manière programmatique sans deviner. Aucun référentiel externe, juste une solution autonome que vous pouvez copier‑coller dans votre projet.

## Prérequis

- .NET 6.0 ou ultérieur (le code fonctionne également avec .NET Framework 4.7+)
- Package NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)
- Familiarité de base avec la syntaxe C#
- Un IDE de votre choix (Visual Studio, Rider, VS Code, etc.)

> **Astuce pro :** Si vous utilisez une version d'essai gratuite d'Aspose.Words, la bibliothèque ajoutera un filigrane au fichier de sortie. En production, vous aurez besoin d'une licence valide.

## Étape 1 : Initialiser le Document et le Builder

La première chose que nous faisons est de créer un nouveau document Word vide et un `DocumentBuilder` qui nous permet d'insérer du contenu. Pensez au builder comme à un stylo virtuel qui dessine sur la page.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();

// The builder provides methods to add text, tables, shapes, etc.
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Pourquoi c'est important :** Sans un `DocumentBuilder`, vous devriez manipuler directement l'arbre de nœuds de bas niveau, ce qui est source d'erreurs et plus difficile à lire.

## Étape 2 : Créer une forme rectangulaire

Nous allons maintenant réellement **créer une forme rectangulaire**. La méthode `InsertShape` prend une énumération `ShapeType`, une largeur et une hauteur (en points). L'objet `Shape` retourné nous permet d'ajuster les propriétés visuelles ultérieurement.

```csharp
// Insert a rectangle 150 pts wide and 80 pts tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

À ce stade, rectangle est une boîte noire solide ancrée au paragraphe actuel. Vous pouvez le déplacer, le redimensionner, ou même le faire pivoter plus tard si nécessaire.

![créer une forme rectangulaire avec ombre](/images/rectangle-shadow.png "Un document Word affichant une forme rectangulaire avec une ombre grise")

*Texte alternatif de l'image : créer une forme rectangulaire avec ombre dans un document Word*

## Étape 3 : Définir la transparence de la forme

La transparence est le niveau de « voir‑à‑travers » du remplissage de la forme. Aspose.Words utilise une propriété `Transparency` allant de `0.0` (opaque) à `1.0` (totalement transparent). Ici, nous **définissons la transparence de la forme** à 40 % afin que le texte sous-jacent reste lisible.

```csharp
// Make the rectangle 40 % transparent
rectangleShape.Fill.Transparency = 0.4; // 0.0 = opaque, 1.0 = invisible
```

> **Cas particulier :** Si vous avez besoin d'une forme complètement invisible mais que vous souhaitez toujours que l'ombre apparaisse, définissez `Transparency` à `1.0` et donnez à la forme une largeur de contour non nulle.

## Étape 4 : Configurer l'ombre

Une ombre portée subtile ajoute de la profondeur. Nous allons **définir la couleur de l'ombre** à un gris moyen, ajuster son rayon de flou, et la décaler de quelques points à la fois horizontalement et verticalement.

```csharp
// Enable the shadow effect
rectangleShape.Shadow.Enabled = true;

// Shadow color – a neutral gray
rectangleShape.Shadow.Color = System.Drawing.Color.Gray;

// 40 % transparent shadow (same as shape's fill)
rectangleShape.Shadow.Transparency = 0.4;

// Blur radius makes the edge softer
rectangleShape.Shadow.Blur = 6;

// Horizontal and vertical offsets (in points)
rectangleShape.Shadow.OffsetX = 5;
rectangleShape.Shadow.OffsetY = 5;
```

> **Pourquoi c'est important :** Une ombre trop nette ou trop sombre peut ressembler à un artefact d'impression. Ajustez `Blur` et `Transparency` jusqu'à ce que cela paraisse naturel.

## Étape 5 : Enregistrer le document Word

Enfin, nous **enregistrons le document Word** sur le disque. La méthode `Save` détermine automatiquement le format du fichier à partir de l'extension ; `.docx` est le format OpenXML moderne.

```csharp
// Save the document to the desired folder
document.Save(@"C:\Temp\ShadowRectangle.docx");
```

Si le dossier n'existe pas, Aspose.Words lèvera une `ArgumentException`. Assurez-vous que le chemin est valide ou créez le répertoire au préalable.

## Exemple complet fonctionnel

Ci-dessous le programme complet, prêt à être exécuté, qui regroupe toutes les étapes. Copiez-le dans un nouveau projet console et appuyez sur **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace AsposeRectangleDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Initialize document and builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert rectangle shape
            Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Set shape transparency (40 % transparent)
            rectangleShape.Fill.Transparency = 0.4;

            // 4️⃣ Configure shadow (color, blur, offset, transparency)
            rectangleShape.Shadow.Enabled = true;
            rectangleShape.Shadow.Color = System.Drawing.Color.Gray;
            rectangleShape.Shadow.Transparency = 0.4;
            rectangleShape.Shadow.Blur = 6;
            rectangleShape.Shadow.OffsetX = 5;
            rectangleShape.Shadow.OffsetY = 5;

            // 5️⃣ Save the document
            string outputPath = @"C:\Temp\ShadowRectangle.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Résultat attendu

Ouvrez `ShadowRectangle.docx` dans Microsoft Word. Vous devriez voir un rectangle gris clair avec une ombre douce, légèrement décalée, tous deux rendus à 40 % de transparence. La forme se trouve sur une page blanche, prête pour du contenu supplémentaire.

## Questions fréquentes & variantes

**Et si j'ai besoin d'une forme différente ?**  
Remplacez `ShapeType.Rectangle` par n'importe quelle autre valeur d'énumération (`Ellipse`, `Triangle`, `Star`, etc.). Le reste du code reste identique.

**Puis-je changer la couleur du contour ?**  
Oui—utilisez `rectangleShape.StrokeColor = System.Drawing.Color.Blue;` et éventuellement définissez `rectangleShape.StrokeWeight = 1.5;`.

**Comment placer la forme à un emplacement précis sur la page ?**  
Définissez `rectangleShape.WrapType = WrapType.None;` puis ajustez les propriétés `rectangleShape.Left` et `rectangleShape.Top` (les valeurs sont en points).

**Est‑il possible d'ajouter du texte à l'intérieur du rectangle ?**  
Absolument. Après avoir créé la forme, vous pouvez appeler `rectangleShape.AppendChild(new Paragraph(document))` puis ajouter un `Run` avec votre texte. N'oubliez pas de définir les propriétés `rectangleShape.TextBox` si vous souhaitez un formatage plus riche.

## Astuces pro & pièges

- **Licence tôt :** Si vous oubliez d'appliquer une licence, Aspose.Words insérera un filigrane sur la première page, ce qui peut prêter à confusion lors des tests.
- **Astuce de performance :** Lors de la génération de nombreux documents dans une boucle, réutilisez une seule instance `Document` et appelez `document.RemoveAllChildren();` après chaque enregistrement afin d'éviter une pression excessive sur le GC.
- **Visibilité de l'ombre :** Sur des écrans à basse résolution, une ombre subtile peut sembler invisible. Augmentez `Blur` ou `OffsetX/Y` pour le débogage, puis réduisez pour la production.

## Prochaines étapes

Maintenant que vous savez comment **créer une forme rectangulaire**, **définir la transparence de la forme**, **définir la couleur de l'ombre**, et **enregistrer le document Word**, envisagez d'étendre le tutoriel :

- Ajouter plusieurs formes et les regrouper.
- Insérer le rectangle à l'intérieur d'une cellule de tableau pour une mise en page de rapport.
- Combiner la forme avec `DocumentBuilder.InsertHtml` pour superposer du contenu au style HTML.
- Explorer d'autres effets visuels comme `Glow` ou `Reflection` pour des documents plus riches, semblables à une interface UI.

Expérimentez, cassez des choses, puis affinez — la génération programmatique de documents est un terrain de jeu où le design visuel rencontre le code.

---

*Bon codage ! Si vous avez rencontré des problèmes, laissez un commentaire ci‑dessous et nous résoudrons cela ensemble.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}