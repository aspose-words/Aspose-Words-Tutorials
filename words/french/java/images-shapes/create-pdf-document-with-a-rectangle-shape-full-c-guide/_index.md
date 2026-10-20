---
category: general
date: 2026-03-25
description: Créez un document PDF en C# et apprenez comment ajouter une forme rectangulaire,
  définir la couleur de remplissage, ajuster la taille de la forme et régler la transparence
  de la forme en quelques étapes seulement.
draft: false
keywords:
- create pdf document
- set shape transparency
- add rectangle shape
- set fill color
- set shape size
language: fr
og_description: Créez un document PDF en C# et découvrez comment ajouter un rectangle,
  définir sa couleur de remplissage, sa taille et sa transparence pour un rendu PDF
  soigné.
og_title: Créer un document PDF avec une forme rectangulaire – Tutoriel C#
tags:
- C#
- PDF
- Aspose.Words
title: Créer un document PDF avec une forme rectangulaire – Guide complet C#
url: /fr/java/images-shapes/create-pdf-document-with-a-rectangle-shape-full-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un document PDF avec une forme rectangulaire – Guide complet C#

Vous avez déjà eu besoin de **créer un document PDF** contenant une forme personnalisée, mais vous ne saviez pas par où commencer ? Vous n'êtes pas seul. Que vous construisiez un générateur de rapports ou un flyer marketing, pouvoir dessiner programmétiquement un rectangle, définir sa couleur de remplissage, ajuster sa taille et même régler sa transparence peut rendre vos PDF beaucoup plus professionnels.

Dans ce tutoriel, nous parcourrons un exemple complet, prêt à l'exécution en C#, qui **crée un document PDF**, **ajoute une forme rectangulaire**, **définit la couleur de remplissage**, **définit la taille de la forme**, et **définit la transparence de la forme** pour une ombre extérieure subtile. À la fin, vous disposerez d'un seul fichier PDF (`shadow.pdf`) que vous pourrez ouvrir pour voir le résultat.

> **Conseil pro :** La même approche fonctionne avec d'autres types de formes (ellipse, ligne, etc.) — il suffit de remplacer `ShapeType.RECTANGLE` par celui dont vous avez besoin.

## Ce dont vous avez besoin

| Prérequis | Pourquoi c'est important |
|--------------|----------------|
| **.NET 6+** (or .NET Framework 4.6+) | La bibliothèque Aspose.Words cible les environnements d'exécution modernes. |
| **Aspose.Words for .NET** NuGet package | Fournit `Document`, `Shape`, `ShadowEffect` et les classes associées. |
| **A C# IDE** (Visual Studio, Rider, VS Code) | Facilite le débogage et l'exécution de l'exemple. |
| **Basic C# knowledge** | Vous comprendrez la syntaxe sans avoir besoin d'une plongée approfondie. |

Vous pouvez installer la bibliothèque via la ligne de commande :

```bash
dotnet add package Aspose.Words
```

C’est tout — pas de DLL supplémentaires, pas de dépendances natives. Une fois le package installé, le code ci‑dessous se compilera et s’exécutera.

## Implémentation étape par étape

Ci‑dessous, nous décomposons le processus en cinq étapes logiques. Chaque étape possède un titre clair (pour que les modèles d'IA puissent l'indexer) et un petit bloc de code que vous pouvez copier‑coller directement.

### ## 1. Créer un document PDF et préparer le canevas

La toute première chose que nous faisons est d’instancier un `Document`. Considérez‑le comme un canevas vierge qui deviendra votre fichier PDF.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document – this is the PDF document we will build.
        Document document = new Document();

        // The rest of the steps follow inside this method.
```

> **Pourquoi ?** `Document` contient toutes les sections, paragraphes et formes. Commencer avec un objet vierge garantit l'absence d'artefacts cachés provenant d'exécutions précédentes.

### ## 2. Ajouter une forme rectangulaire – définir la couleur de remplissage et la taille de la forme

Nous créons maintenant un rectangle, lui appliquons un remplissage jaune vif, et définissons ses dimensions. Cela couvre à la fois **ajouter une forme rectangulaire**, **définir la couleur de remplissage** ainsi que **définir la taille de la forme**.

```csharp
        // Step 2: Create a rectangle shape.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Set the width and height – this is where we set the shape size.
        rectangle.Width = 200;   // 200 points (≈2.78 inches)
        rectangle.Height = 100;  // 100 points (≈1.39 inches)

        // Apply a fill color – here we use a vivid yellow.
        rectangle.FillColor = Color.Yellow;
```

> **Note :** La largeur/hauteur sont mesurées en points (1 point = 1/72 pouce). Ajustez ces valeurs pour correspondre à votre mise en page.

### ## 3. Appliquer une ombre extérieure et définir la transparence de la forme

Les ombres ajoutent de la profondeur, et contrôler leur opacité est l'essence de **définir la transparence de la forme**. Ci‑dessous, nous configurons une ombre extérieure grise avec 30 % de transparence.

```csharp
        // Step 3: Configure the outer shadow effect.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;          // Shadow hue
        shadow.BlurRadius = 5.0;            // How fuzzy the shadow appears
        shadow.DistanceX = 4;               // Horizontal offset
        shadow.DistanceY = 4;               // Vertical offset
        shadow.Transparency = 0.3;          // 0 = opaque, 1 = fully transparent
        shadow.Style = ShadowStyle.Outer;   // Make it an outer shadow
```

> **Pourquoi définir la transparence ?** Une ombre à 30 % de transparence apparaît subtile, empêchant le rectangle de paraître « plat » sur la page.

### ## 4. Insérer la forme dans le corps du document

Nous plaçons maintenant le rectangle dans le premier paragraphe de la première section du document. Cette étape assemble le tout.

```csharp
        // Step 4: Insert the rectangle into the first paragraph.
        // If the document has no paragraphs yet, Aspose creates one automatically.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);
```

> **Cas particulier :** Si vous avez besoin de la forme sur une nouvelle page, préfixez `document.Sections[0].PageSetup.SectionStart = SectionStart.NewPage;` avant d’ajouter la forme.

### ## 5. Enregistrer le document en tant que fichier PDF

Enfin, nous persistons la structure en mémoire dans un fichier PDF physique. Le fichier sera écrit dans le dossier que vous spécifiez.

```csharp
        // Step 5: Save the document as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF saved successfully to {outputPath}");
    }
}
```

Lorsque vous exécutez le programme, un fichier nommé `shadow.pdf` apparaît. L'ouvrir montre un rectangle jaune avec une ombre grise douce décalée de 4 points — exactement ce que notre code décrit.

> **Résultat attendu :** Un PDF d'une seule page où le rectangle se trouve près du coin supérieur gauche de la page, rempli de jaune, de taille 200 × 100 points, et projetant une ombre extérieure semi‑transparente.

## Exemple complet fonctionnel (prêt à copier‑coller)

Ci‑dessous se trouve le fichier source complet, prêt à être intégré dans un nouveau projet console.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new empty document – this will become the PDF.
        Document document = new Document();

        // 2️⃣ Add a rectangle shape, set its size and fill color.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.Width = 200;          // shape size – width
        rectangle.Height = 100;         // shape size – height
        rectangle.FillColor = Color.Yellow; // set fill color

        // 3️⃣ Apply an outer shadow and adjust transparency.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;
        shadow.BlurRadius = 5.0;
        shadow.DistanceX = 4;
        shadow.DistanceY = 4;
        shadow.Transparency = 0.3;      // set shape transparency
        shadow.Style = ShadowStyle.Outer;

        // 4️⃣ Insert the shape into the first paragraph of the document.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);

        // 5️⃣ Save everything as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF created at: {outputPath}");
    }
}
```

> **Astuce :** Remplacez `YOUR_DIRECTORY` par un chemin absolu comme `C:\Temp` ou un chemin relatif tel que `.\output`. Le programme créera le dossier s’il n’existe pas déjà.

## Questions fréquentes (FAQ)

**Q : Puis‑je changer la position du rectangle sur la page ?**  
R : Absolument. Définissez `rectangle.Left` et `rectangle.Top` (tous deux mesurés en points) avant de l’ajouter au paragraphe.

**Q : Et si j’ai besoin d’un remplissage transparent au lieu d’une ombre transparente ?**  
R : Utilisez `rectangle.FillColor = Color.FromArgb(128, Color.Yellow);` – le premier argument est le canal alpha (0‑255), où 128 donne environ 50 % de transparence.

**Q : Cette méthode fonctionne‑t‑elle avec .NET Core ?**  
R : Oui. Aspose.Words prend en charge .NET Standard 2.0+, vous pouvez donc exécuter le même code sur .NET 6, .NET 7 ou .NET Framework 4.6+.

**Q : Comment ajouter plusieurs formes ?**  
R : Répétez simplement les étapes 2‑4 pour chaque forme, en les insérant éventuellement dans différents paragraphes ou sections.

## Conclusion

Nous venons de **créer un document PDF** à partir de zéro, **ajouter une forme rectangulaire**, **définir sa couleur de remplissage**, **définir sa taille**, et **ajuster la transparence de la forme** pour obtenir un effet d’ombre soigné. Le code d’exemple est autonome, s’exécute en moins d’une minute, et illustre les concepts de base dont vous aurez besoin pour des mises en page PDF plus élaborées.

Prêt pour le prochain défi ? Essayez de remplacer le rectangle par une forme à coins arrondis, d’intégrer une image à l’intérieur de la forme, ou de générer automatiquement une table des matières. La même API vous permet de superposer texte, images et vecteurs — les possibilités sont infinies.

Si vous avez trouvé ce guide utile, mettez‑lui une étoile sur GitHub, partagez‑le avec un collègue, ou laissez un commentaire avec vos propres variantes. Bon codage !

![exemple de création de document PDF avec forme rectangulaire](/images/rectangle-shadow.png "Capture d'écran montrant le PDF créé avec un rectangle jaune et une ombre extérieure grise")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}