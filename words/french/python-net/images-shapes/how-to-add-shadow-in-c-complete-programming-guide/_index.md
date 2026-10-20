---
category: general
date: 2025-12-25
description: Comment ajouter une ombre en C# avec un exemple de code simple. Apprenez
  à définir la distance de l’ombre, à personnaliser la couleur et à créer de la profondeur
  pour vos graphiques.
draft: false
keywords:
- how to add shadow
- how to set shadow distance
language: fr
og_description: Comment ajouter une ombre en C# est expliqué étape par étape. Suivez
  le guide pour définir la distance de l’ombre, la couleur et le flou afin d’obtenir
  des formes au rendu professionnel.
og_title: Comment ajouter une ombre en C# – Guide complet de programmation
tags:
- C#
- graphics
- Aspose.Words
- shadows
title: Comment ajouter une ombre en C# – Guide complet de programmation
url: /fr/python/images-shapes/how-to-add-shadow-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment ajouter une ombre en C# – Guide complet de programmation

Comment ajouter une ombre en C# est un besoin fréquent lorsque vous voulez que vos graphiques ressortent de la page. Dans ce tutoriel, nous parcourrons les étapes exactes pour configurer l’ombre d’une forme, y compris comment définir la distance de l’ombre, ajuster le flou et choisir la bonne couleur.  

Si vous avez déjà regardé un rectangle plat et pensé « cela pourrait gagner en profondeur », vous êtes au bon endroit. Nous partirons d’un document vierge, ajouterons une forme, et finirons avec une ombre soignée qui semble avoir été placée par un designer. Pas de fioritures, juste un exemple pratique et exécutable que vous pouvez copier‑coller dès aujourd’hui.

## Ce que vous allez apprendre

- Créer un nouveau document et insérer une forme programmatique.  
- Appliquer un flou doux à l’ombre de la forme.  
- **Comment définir la distance de l’ombre** afin que l’ombre apparaisse naturellement décalée.  
- Choisir une couleur d’ombre qui fonctionne sur n’importe quel arrière‑plan.  
- Enregistrer le résultat en PDF (ou tout autre format dont vous avez besoin).  

### Prérequis

- .NET 6.0 ou version ultérieure (le code fonctionne avec .NET Core et .NET Framework).  
- Aspose.Words for .NET (version d’essai gratuite ou version sous licence).  
- Une compréhension de base de la syntaxe C#.  

C’est tout—pas de bibliothèques supplémentaires, pas de magie. Plongeons‑y.

![Exemple d’une forme avec une ombre noire douce – comment ajouter une ombre](https://example.com/placeholder-shadow.png "exemple d’ajout d’ombre")

## Étape 1 : Configurer le projet et importer les espaces de noms

Tout d’abord, créez une nouvelle application console (ou tout projet C#) et ajoutez le package NuGet Aspose.Words :

```bash
dotnet new console -n ShadowDemo
cd ShadowDemo
dotnet add package Aspose.Words
```

Ouvrez maintenant `Program.cs` et importez les espaces de noms requis :

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shadows;
using Aspose.Words.Drawing.Shapes;
using Aspose.Words.Saving;
```

> **Astuce :** Si vous utilisez Visual Studio, l’IDE vous proposera les instructions `using` au fur et à mesure que vous tapez `Document`.

## Étape 2 : Créer un nouveau document et ajouter une forme

Avec les bibliothèques prêtes, nous pouvons instancier un objet `Document` et déposer un simple rectangle sur la première page.

```csharp
// Step 2: Initialize the document
Document doc = new Document();

// Add a blank page (Aspose.Words creates one automatically)
Section section = doc.FirstSection;

// Insert a rectangle shape – this will be the object we give a shadow
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    // Size the shape (width, height) in points (1 point = 1/72 inch)
    Width = 200,
    Height = 100,
    
    // Position the shape 100 points from the left and 150 from the top
    Left = 100,
    Top = 150,
    
    // Fill the shape with a light gray so the shadow stands out
    FillColor = System.Drawing.Color.LightGray
};

// Add the shape to the document's first page
section.Body.FirstParagraph.AppendChild(rectangle);
```

Pourquoi un rectangle ? C’est une toile neutre qui permet de juger l’effet de l’ombre sans distraction. Vous pouvez remplacer `ShapeType.Rectangle` par `Ellipse` ou `Star`—la logique de l’ombre reste la même.

## Étape 3 : Comment ajouter une ombre – Appliquer le flou, la distance et la couleur

Voici le cœur du tutoriel : **comment ajouter une ombre** à ce rectangle. Aspose.Words expose un objet `Shadow` sur chaque forme, vous permettant de régler le flou, la distance et la couleur.

```csharp
// Step 3: Access the shape's shadow settings
Shadow shadow = rectangle.Shadow;

// 3a) Apply a soft blur – larger values make the shadow fuzzier
shadow.Blur = 5.0;          // 5 points blur gives a subtle, professional look

// 3b) Set the shadow's offset distance – this determines how far the shadow is displaced
shadow.Distance = 3.0;      // 3 points offset is enough to suggest depth without looking detached

// 3c) Choose a shadow color – black works on most backgrounds, but you can experiment
shadow.Color = Color.Black; // Solid black; you could use Color.FromArgb(128, 0, 0, 0) for semi‑transparent

// OPTIONAL: Rotate the shadow to match a light source direction (45 degrees works well)
shadow.Angle = 45.0;
```

Remarquez le commentaire `// 3b) Set the shadow's offset distance`. Cette ligne répond directement à **comment définir la distance de l'ombre**. En ajustant `shadow.Distance`, vous contrôlez l’écart visuel entre la forme et son ombre, simulant une source lumineuse placée à un angle précis.

### Pourquoi ces valeurs ?

- **Blur = 5.0** – Un flou doux évite une silhouette trop dure tout en restant visible.  
- **Distance = 3.0** – Garde l’ombre suffisamment proche pour paraître projetée par la forme elle‑même.  
- **Color = Black** – Garantit le contraste sur les arrière‑plans clairs et sombres.  

N’hésitez pas à modifier ces chiffres ; l’API accepte n’importe quelle valeur `double` dont vous avez besoin.

## Étape 4 : Enregistrer le document et vérifier le résultat

Une fois l’ombre configurée, il suffit d’écrire le fichier sur le disque. Aspose.Words peut générer de nombreux formats ; le PDF est un choix courant pour le partage.

```csharp
// Step 4: Save the document as a PDF (you could also use .docx, .png, etc.)
string outputPath = "ShadowedShape.pdf";
doc.Save(outputPath, SaveFormat.Pdf);

Console.WriteLine($"Document saved to {outputPath}. Open it to see the shadow effect.");
```

Ouvrez `ShadowedShape.pdf` et vous devriez voir un rectangle gris avec une ombre noire douce légèrement décalée vers le bas‑droite. Si l’ombre paraît trop pâle, augmentez `shadow.Blur` ou `shadow.Distance` et relancez.

## Questions fréquentes & Cas particuliers

### Et si j’ai besoin d’une ombre transparente ?

Utilisez une couleur ARGB avec un canal alpha inférieur à 255 :

```csharp
shadow.Color = Color.FromArgb(80, 0, 0, 0); // 80/255 opacity = ~31% transparent
```

### Puis‑je appliquer la même ombre à plusieurs formes ?

Absolument. Créez une méthode d’aide :

```csharp
static void ApplyStandardShadow(Shape shape)
{
    shape.Shadow.Blur = 5.0;
    shape.Shadow.Distance = 3.0;
    shape.Shadow.Color = Color.Black;
}
```

Appelez `ApplyStandardShadow(rectangle);` pour chaque forme que vous ajoutez.

### Cela fonctionne‑t‑il avec les anciennes versions du .NET Framework ?

Oui. Aspose.Words 22.9+ prend en charge le .NET Framework 4.5 et supérieur. Ajustez simplement votre fichier projet en conséquence.

## Exemple complet fonctionnel

Voici le programme complet que vous pouvez copier dans `Program.cs`. Il compile et s’exécute immédiatement (à condition que le package NuGet soit installé).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shadows;
using Aspose.Words.Drawing.Shapes;
using Aspose.Words.Saving;

namespace ShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Initialize the document
            Document doc = new Document();
            Section section = doc.FirstSection;

            // Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100,
                Left = 100,
                Top = 150,
                FillColor = System.Drawing.Color.LightGray
            };
            section.Body.FirstParagraph.AppendChild(rectangle);

            // Apply shadow – this is the core of "how to add shadow"
            Shadow shadow = rectangle.Shadow;
            shadow.Blur = 5.0;                // Soft blur
            shadow.Distance = 3.0;            // How to set shadow distance
            shadow.Color = Color.Black;       // Classic black shadow
            shadow.Angle = 45.0;              // Light source direction

            // Save as PDF
            string outputPath = "ShadowedShape.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);

            Console.WriteLine($"Document saved to {outputPath}. Open it to see the shadow effect.");
        }
    }
}
```

Exécutez le programme :

```bash
dotnet run
```

Vous trouverez `ShadowedShape.pdf` dans le dossier du projet. Ouvrez‑le avec n’importe quel lecteur PDF pour confirmer que l’ombre apparaît comme décrit.

## Conclusion

Nous avons couvert **comment ajouter une ombre** à une forme en C# du début à la fin, et nous avons montré **comment définir la distance de l’ombre** ainsi que le flou et la couleur. En quelques lignes de code seulement, vous pouvez donner à vos graphiques un aspect professionnel, tridimensionnel—sans outils de conception externes.

Maintenant que vous maîtrisez les bases, expérimentez :

- Changez la couleur de l’ombre en un bleu subtil pour une ambiance plus fraîche.  
- Augmentez le flou pour un effet onirique et diffus.  
- Appliquez la même technique aux graphiques, images ou zones de texte.  

Chaque variante renforce les mêmes concepts fondamentaux, vous permettant de personnaliser les ombres pour n’importe quel scénario.  

Des questions supplémentaires ? Laissez un commentaire, et bon codage !

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}