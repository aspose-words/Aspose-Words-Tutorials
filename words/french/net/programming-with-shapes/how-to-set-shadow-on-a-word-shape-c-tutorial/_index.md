---
category: general
date: 2026-03-30
description: Apprenez à définir l'ombre d'une forme Word à l'aide de C#. Ce guide
  montre également comment ajouter une ombre à une forme, ajuster la transparence
  de la forme et ajouter une ombre de rectangle.
draft: false
keywords:
- how to set shadow
- adjust shape transparency
- add shape shadow
- how to add shadow
- add rectangle shadow
language: fr
og_description: Comment définir une ombre sur une forme Word en C# ? Suivez ce guide
  étape par étape pour ajouter une ombre à la forme, ajuster la transparence de la
  forme et ajouter une ombre de rectangle.
og_title: Comment ajouter une ombre à une forme Word – Tutoriel C#
tags:
- Aspose.Words
- C#
- Word Automation
- Shapes
title: Comment ajouter une ombre à une forme Word – Tutoriel C#
url: /fr/net/programming-with-shapes/how-to-set-shadow-on-a-word-shape-c-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment définir une ombre sur une forme Word – Tutoriel C#

Vous vous êtes déjà demandé **comment définir une ombre** sur une forme dans un document Word sans passer par l’interface graphique ? Vous n’êtes pas seul. Dans de nombreux rapports ou présentations, une ombre discrète fait ressortir un rectangle, et le faire de façon programmatique fait gagner des heures.

Dans ce guide, nous parcourrons un exemple complet, prêt à l’emploi, qui montre non seulement **comment définir une ombre**, mais couvre également **add shape shadow**, **adjust shape transparency**, et même **add rectangle shadow** pour ces boîtes d’appel classiques. À la fin, vous disposerez d’un fichier Word (`output.docx`) au rendu soigné, et vous comprendrez pourquoi chaque propriété est importante.

## Prérequis

- .NET 6+ (ou .NET Framework 4.7.2) avec un compilateur C#  
- Package NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)  
- Familiarité de base avec C# et le modèle d’objet de Word  

Aucune bibliothèque supplémentaire n’est requise — tout se trouve dans Aspose.Words.

---

## Comment définir une ombre sur une forme Word en C#

Voici le fichier source complet. Enregistrez‑le sous le nom `Program.cs` et exécutez‑le depuis votre IDE ou avec `dotnet run`. Le code charge un `.docx` existant, trouve la première forme (un rectangle par défaut), active son ombre, ajuste quelques paramètres visuels, puis enregistre le résultat.

```csharp
// Program.cs
using System;
using System.Drawing;               // For Color
using Aspose.Words;                // Core document API
using Aspose.Words.Drawing;        // Shape and shadow classes

class ShadowDemo
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the shape.
        // Replace YOUR_DIRECTORY with the folder where your files live.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Retrieve the first shape in the document.
        // If you have multiple shapes, you can loop or use GetChild with a different index.
        Shape rectangleShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (rectangleShape == null)
        {
            Console.WriteLine("No shape found – make sure input.docx contains at least one shape.");
            return;
        }

        // 3️⃣ Enable the shape's shadow and choose a base color.
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = Color.Black;   // You can pick any System.Drawing.Color

        // 4️⃣ Fine‑tune the shadow appearance.
        rectangleShape.ShadowFormat.Transparency = 0.3;     // 30 % transparent (adjust shape transparency)
        rectangleShape.ShadowFormat.OffsetX = 5;           // Horizontal offset in points
        rectangleShape.ShadowFormat.OffsetY = 5;           // Vertical offset in points
        rectangleShape.ShadowFormat.BlurRadius = 4;       // Soft edge radius

        // 5️⃣ Save the updated document.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Shadow applied! Check {outputPath}");
    }
}
```

> **Ce que vous verrez** – Le rectangle possède maintenant une ombre portée noire à 30 % de transparence, décalée de 5 pt vers la droite et le bas, avec un léger flou. Ouvrez `output.docx` dans Word pour vérifier.

## Ajuster la transparence de la forme – Pourquoi c’est important

La transparence n’est pas seulement un réglage esthétique ; elle influence la lisibilité. Une valeur de 0,0 rend l’ombre totalement opaque, tandis que 1,0 la masque complètement. Dans l’extrait ci‑dessus, nous avons utilisé `0.3` pour obtenir un effet subtil qui fonctionne sur des fonds clairs et sombres. N’hésitez pas à expérimenter :

```csharp
rectangleShape.ShadowFormat.Transparency = 0.1; // Almost solid shadow
rectangleShape.ShadowFormat.Transparency = 0.6; // Very faint
```

Rappelez‑vous que **adjust shape transparency** peut également être appliqué à la couleur de remplissage de la forme si vous avez besoin d’un rectangle semi‑transparent.

## Ajouter une ombre à différents objets

Le code que nous avons utilisé cible un objet `Shape`, mais les mêmes propriétés `ShadowFormat` existent sur les objets **Image**, **Chart**, et même **TextBox**. Voici un petit modèle que vous pouvez copier‑coller :

```csharp
// Assuming 'image' is an Aspose.Words.Drawing.Image object
image.ShadowFormat.Visible = true;
image.ShadowFormat.Color = Color.Gray;
image.ShadowFormat.OffsetX = 3;
image.ShadowFormat.OffsetY = 3;
image.ShadowFormat.BlurRadius = 2;
```

Ainsi, que vous **add shape shadow** à un logo ou à une icône décorative, l’approche reste identique.

## Comment ajouter une ombre à n’importe quelle forme – Cas particuliers

1. **Forme sans boîte englobante** – Certaines formes Word (comme les griffonnages libres) ne supportent pas les ombres. Tenter de définir `ShadowFormat.Visible` échouera silencieusement. Vérifiez `shape.IsShadowSupported` si vous avez besoin de sécurité.  
2. **Versions anciennes de Word** – Les propriétés d’ombre correspondent aux fonctionnalités Word 2007+. Si vous devez prendre en charge Word 2003, l’ombre sera ignorée à l’ouverture du fichier.  
3. **Ombres multiples** – Aspose.Words ne prend actuellement en charge qu’une seule ombre par forme. Si vous avez besoin d’un effet à deux couches, dupliquez la forme, décalez‑la, et appliquez des réglages d’ombre différents.

## Ajouter une ombre à un rectangle – Cas d’utilisation réel

Imaginez que vous générez un rapport trimestriel et que chaque en‑tête de section est un rectangle coloré. Ajouter un **add rectangle shadow** donne à la page un aspect « carte ». Les étapes sont identiques à l’exemple de base ; assurez‑vous simplement que la forme ciblée est bien un rectangle (`shape.ShapeType == ShapeType.Rectangle`). Si vous devez créer le rectangle à partir de zéro, consultez l’extrait ci‑dessous :

```csharp
// Create a new rectangle shape programmatically
Shape newRect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,
    Height = 50,
    WrapType = WrapType.Inline
};
newRect.FillColor = Color.LightBlue;

// Apply shadow (same settings as before)
newRect.ShadowFormat.Visible = true;
newRect.ShadowFormat.Color = Color.Black;
newRect.ShadowFormat.Transparency = 0.25;
newRect.ShadowFormat.OffsetX = 4;
newRect.ShadowFormat.OffsetY = 4;
newRect.ShadowFormat.BlurRadius = 3;

// Insert into the first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(newRect);
```

Exécuter le programme complet avec cet ajout vous donnera un nouveau rectangle qui possède déjà l’effet **add rectangle shadow** souhaité.

---

![Forme Word avec ombre](placeholder-image.png){alt="comment définir une ombre sur une forme dans Word"}

*Figure : Le rectangle après l’application des paramètres d’ombre.*

## Récapitulatif rapide (feuille de triche en points)

- **Load** le document avec `new Document(path)`.  
- **Locate** la forme via `doc.GetChild(NodeType.Shape, index, true)`.  
- **Enable** l’ombre : `shape.ShadowFormat.Visible = true;`.  
- **Set color** avec n’importe quel `System.Drawing.Color`.  
- **Adjust transparency** (`0.0–1.0`) pour contrôler l’opacité.  
- **OffsetX / OffsetY** déplacent l’ombre horizontalement/verticalement (points).  
- **BlurRadius** adoucit les bords — des valeurs plus élevées = ombre plus floue.  
- **Save** le fichier et ouvrez‑le dans Word pour voir le résultat.

## Que tester ensuite ?

- **Couleurs dynamiques** – Récupérez la couleur de l’ombre depuis un thème ou une saisie utilisateur.  
- **Ombres conditionnelles** – Appliquez une ombre uniquement lorsque la largeur de la forme dépasse un certain seuil.  
- **Traitement par lots** – Parcourez toutes les formes d’un document et **add shape shadow** automatiquement.  

Si vous avez suivi le tutoriel, vous savez maintenant **comment définir une ombre**, comment **adjust shape transparency**, et comment **add rectangle shadow** pour un rendu professionnel. N’hésitez pas à expérimenter, à casser des choses, puis à les réparer — le codage est le meilleur des professeurs.

---

*Bon codage ! Si ce tutoriel vous a été utile, laissez un commentaire ou partagez vos propres astuces d’ombre. Plus nous apprenons les uns des autres, plus nos documents Word seront beaux.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}