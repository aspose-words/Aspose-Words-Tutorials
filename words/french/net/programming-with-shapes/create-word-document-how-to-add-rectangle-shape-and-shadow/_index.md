---
category: general
date: 2026-03-19
description: Créer un document Word en C# avec Aspose.Words, apprendre à ajouter une
  forme, ajouter une forme rectangulaire, appliquer une ombre et enregistrer le document
  au format docx en quelques minutes.
draft: false
keywords:
- create word document
- how to add shape
- add rectangle shape
- save document as docx
- add shadow to shape
language: fr
og_description: Créez un document Word avec Aspose.Words, ajoutez une forme rectangle,
  appliquez une ombre extérieure et enregistrez le document au format docx. Guide
  étape par étape.
og_title: Créer un document Word – Ajouter une forme rectangulaire et une ombre
tags:
- Aspose.Words
- C#
- Document Automation
title: Créer un document Word – comment ajouter une forme rectangle et une ombre
url: /fr/net/programming-with-shapes/create-word-document-how-to-add-rectangle-shape-and-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create Word Document – How to Add Rectangle Shape and Shadow

Vous avez déjà eu besoin de **create word document** de manière programmatique et vous vous êtes demandé par où commencer ? Vous n'êtes pas seul. De nombreux développeurs rencontrent le même obstacle lorsqu'ils essaient pour la première fois de générer un fichier .docx contenant des graphiques personnalisés. Dans ce tutoriel, nous parcourrons l’ensemble du processus — comment ajouter une forme, spécifiquement un **add rectangle shape**, lui appliquer une **add shadow to shape** élégante, et enfin **save document as docx**.  

À la fin du guide, vous disposerez d’un extrait C# prêt à l’emploi que vous pourrez insérer dans n’importe quel projet .NET. Pas de références vagues, seulement un exemple complet et exécutable.  

## Prerequisites

- .NET 6.0 ou version ultérieure (le code fonctionne également avec .NET Framework).  
- Aspose.Words for .NET installé (package NuGet `Aspose.Words`).  
- Une compréhension de base de la syntaxe C# — rien de compliqué.  

Si la bibliothèque vous manque, exécutez :

```bash
dotnet add package Aspose.Words
```

C’est tout — pas de SDK supplémentaires, pas d’interop COM, juste une référence NuGet unique.

---

## Step 1: Create a Word Document (Primary Goal)

La première chose dont nous avons besoin est une toile vierge. Considérez la classe `Document` comme une page neuve dans Microsoft Word ; elle contient les sections, paragraphes et tout le reste que vous ajouterez plus tard.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Step 1: Initialize a new blank document
Document doc = new Document();               // This creates an empty .docx in memory
```

Pourquoi commencer avec un `Document` vierge ? Parce que cela garantit qu’aucun formatage caché ne s’infiltre depuis un modèle. D’après mon expérience, repartir de zéro évite les décalages de mise en page mystérieux lorsque vous insérez des formes ultérieurement.

---

## Step 2: Insert a Rectangle Shape – Adding the Visual Element

Maintenant que nous avons un document, ajoutons un **add rectangle shape** au premier paragraphe. L’objet `Shape` est polyvalent ; vous pouvez choisir `ShapeType.Rectangle`, `Ellipse` ou même des dessins personnalisés. Voici le code minimal :

```csharp
// Step 2: Create a rectangle and attach it to the first paragraph
Shape rect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,               // Width in points (≈2.78 inches)
    Height = 100,              // Height in points (≈1.39 inches)
    WrapType = WrapType.Inline // Makes the shape behave like a character
};

// Append the shape to the first paragraph (creates one if missing)
Paragraph firstPara = doc.FirstSection.Body.FirstParagraph;
firstPara.AppendChild(rect);
```

**What’s happening under the hood?**  
- `ShapeType.Rectangle` indique à Aspose que nous voulons une simple boîte.  
- `WrapType.Inline` assure que le rectangle se déplace avec le flux du texte, ce qui est généralement attendu dans un scénario de traitement de texte.  
- En l’ajoutant à `FirstParagraph`, nous évitons d’insérer manuellement un nouveau paragraphe ; Aspose en crée un pour nous si le document est réellement vide.

> **Pro tip:** Si vous avez besoin que la forme se situe *derrière* le texte, passez `WrapType` à `WrapType.Transparent`. Ce petit changement peut produire une différence visuelle majeure.

---

## Step 3: Apply an Outer Shadow – Enhancing the Look

Un rectangle plat est… eh bien, plat. Ajouter une **add shadow to shape** lui donne de la profondeur sans images supplémentaires. Le `ShadowFormat` d’Aspose rend cela possible en une seule ligne.

```csharp
// Step 3: Configure an outer shadow for the rectangle
rect.ShadowFormat.Type = ShadowType.OuterShadow;
rect.ShadowFormat.Blur = 5.0;           // Softness of the shadow edge
rect.ShadowFormat.Distance = 3.0;      // How far the shadow is offset
rect.ShadowFormat.Angle = 45;          // Direction in degrees (45° = bottom‑right)
rect.ShadowFormat.Color = Color.Gray; // Classic gray shadow
```

Pourquoi choisir ces valeurs précises ?  
- Un **Blur** de `5.0` offre un bord légèrement estompé qui paraît professionnel sur la plupart des écrans.  
- Une **Distance** de `3.0` et un **Angle** de `45` créent une source de lumière naturelle depuis le haut‑gauche, une convention de design courante.  
- **Color.Gray** fonctionne aussi bien sur les thèmes clairs que sombres ; vous pouvez le remplacer par `Color.Black` si vous avez besoin d’un contraste plus fort.

Si vous avez besoin d’une ombre *interne* (pensez à un bouton enfoncé), changez simplement `ShadowType.OuterShadow` en `ShadowType.InnerShadow`. Les mêmes propriétés s’appliquent.

---

## Step 4: Save the Document as DOCX – Persisting Your Work

Tout cela est amusant, mais vous voudrez finalement un fichier sur le disque. L’étape **save document as docx** est simple :

```csharp
// Step 4: Persist the document to a .docx file
string outputPath = @"C:\Temp\ShadowedRectangle.docx";
doc.Save(outputPath, SaveFormat.Docx);
```

Quelques remarques :  
- L’énumération `SaveFormat.Docx` garantit le format moderne Office Open XML, compatible avec Word 2007+.  
- Si vous devez diffuser le fichier directement dans une réponse web, remplacez le chemin du fichier par un `MemoryStream` et écrivez‑le dans la réponse HTTP.

Après avoir exécuté le code, ouvrez `ShadowedRectangle.docx` dans Microsoft Word. Vous devriez voir un rectangle gris avec une ombre douce, placé en ligne avec le premier paragraphe—exactement ce que nous voulions obtenir.

---

## How to Add Shape – Alternative Approaches

L’exemple ci‑dessus utilise l’approche *inline*, mais parfois vous voulez une forme qui flotte au-dessus du texte. C’est là que **how to add shape** avec différents types d’enveloppe entre en jeu.

```csharp
Shape floatingRect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 250,
    Height = 120,
    WrapType = WrapType.Square, // Allows text to wrap around the shape
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    HorizontalAlignment = HorizontalAlignment.Center
};

doc.FirstSection.Body.FirstParagraph.AppendChild(floatingRect);
```

Ici nous avons changé `WrapType` en `Square` et centré la forme sur la page. Ce schéma est utile pour les pages de garde ou les bannières décoratives. N’oubliez pas : les formes flottantes augmentent légèrement la taille du fichier car Word stocke des données de position supplémentaires.

---

## Expected Output & Verification

Lorsque vous ouvrez le fichier généré, vous devez voir :

- Un seul paragraphe contenant un rectangle gris.  
- Le rectangle mesurant approximativement 2,8 × 1,4 pouces.  
- Une ombre extérieure subtile décalée vers le bas‑droite.  

Si la forme apparaît *en dehors* du paragraphe, revérifiez le `WrapType`. Si l’ombre semble trop dure, réduisez la valeur du `Blur` ou changez la `Color` pour une teinte plus claire.

---

## Common Pitfalls & How to Avoid Them

| Issue | Why it Happens | Fix |
|-------|----------------|-----|
| Shape disappears after saving | `WrapType` set to `Inline` but paragraph was removed | Ensure the paragraph exists; use `doc.FirstSection.Body.FirstParagraph` to guarantee it. |
| Shadow looks pixelated | Using a very low `Blur` value | Increase `Blur` to at least `3.0` for smooth edges. |
| File size balloons | Adding many high‑resolution images alongside shapes | Use `doc.RemoveUnusedResources()` before saving if you added images. |
| Color not showing on dark mode | Using a dark `Color` for the shape itself | Choose a contrasting color (e.g., `Color.White`) for better visibility. |

---

## Full Working Example

Below is the complete, copy‑and‑paste‑ready code that incorporates everything we’ve discussed. Feel free to run it as a console app.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank Word document
        Document doc = new Document();

        // 2️⃣ Add a rectangle shape to the first paragraph
        Shape rect = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 200,
            Height = 100,
            WrapType = WrapType.Inline
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(rect);

        // 3️⃣ Apply an outer shadow to the rectangle
        rect.ShadowFormat.Type = ShadowType.OuterShadow;
        rect.ShadowFormat.Blur = 5.0;
        rect.ShadowFormat.Distance = 3.0;
        rect.ShadowFormat.Angle = 45;
        rect.ShadowFormat.Color = Color.Gray;

        // 4️⃣ Save the document as a .docx file
        string outPath = @"C:\Temp\ShadowShape.docx";
        doc.Save(outPath, SaveFormat.Docx);

        // Optional: Let the user know we’re done
        System.Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**Explanation of each block** is inline as comments, satisfying both SEO readers and AI assistants that love self‑contained answers.

---

## Conclusion

We’ve just **create word document** from scratch, learned **how to add shape**, specifically an **add rectangle shape**, gave it an **add shadow to shape**, and finally **save document as docx**. The steps are simple, the code is compact, and the result looks polished.  

If you’re ready to take it further, try swapping the rectangle for a custom image, experiment with different shadow colors, or generate a whole report with multiple shaped sections. The Aspose.Words API is flexible enough to handle everything from invoices to marketing brochures.

Got questions about other shape types or need help integrating this into an ASP.NET Core service? Drop a comment below, and happy coding! 

![create word document with rectangle shape and shadow](placeholder-image.png "create word document with rectangle shape and shadow

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}