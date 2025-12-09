---
category: general
date: 2025-12-08
description: Ajoutez rapidement une ombre à une forme avec Aspose.Words. Apprenez
  comment créer un document Word avec Aspose, comment ajouter une ombre à une forme
  et appliquer la transparence de l’ombre en C#.
draft: false
keywords:
- add shadow to shape
- create word document using aspose
- how to add shape shadow
- apply shadow transparency
language: fr
og_description: Ajouter une ombre à une forme dans un fichier Word à l'aide d'Aspose.Words.
  Ce guide étape par étape montre comment créer un document, ajouter une forme et
  appliquer la transparence de l'ombre.
og_title: Ajouter une ombre à la forme – Tutoriel Aspose.Words C#
tags:
- Aspose.Words
- C#
- Word Automation
title: Ajouter une ombre à une forme dans un document Word – Guide complet d’Aspose.Words
url: /french/net/images-and-shapes/add-shadow-to-shape-in-a-word-document-complete-aspose-words/
---

{{< layout-start >}}

{{< layout-start >}}

# Ajouter une ombre à une forme – Guide complet Aspose.Words

Vous avez déjà eu besoin d'**ajouter une ombre à une forme** dans un fichier Word mais vous ne saviez pas quelles appels d'API utiliser ? Vous n'êtes pas seul. De nombreux développeurs se heurtent à un mur lorsqu'ils essaient pour la première fois d'ajouter une ombre portée à un rectangle ou à tout autre élément de dessin, surtout lorsqu'ils travaillent avec Aspose.Words pour .NET.

Dans ce tutoriel, nous passerons en revue tout ce que vous devez savoir : de la **création d'un document Word en utilisant Aspose** à la configuration de l'ombre, en ajustant son flou, sa distance, son angle et même **l'application de la transparence de l'ombre**. À la fin, vous disposerez d'un programme C# prêt à l'emploi qui produit un fichier `.docx` avec un rectangle joliment ombré — aucune manipulation manuelle dans Word requise.

---

## Ce que vous apprendrez

- Comment configurer un projet Aspose.Words dans Visual Studio.  
- Les étapes exactes pour **créer un document Word en utilisant Aspose** et insérer une forme.  
- **Comment ajouter une ombre à une forme** avec un contrôle complet sur le flou, la distance, l'angle et la transparence.  
- Conseils pour dépanner les problèmes courants (par ex., licence manquante, unités incorrectes).  
- Un exemple complet, copiable, que vous pouvez exécuter dès aujourd'hui.

> **Prérequis :** .NET 6+ (ou .NET Framework 4.7.2+), une licence valide Aspose.Words (ou l'essai gratuit), et une connaissance de base du C#.

---

## Étape 1 – Configurez votre projet et ajoutez Aspose.Words

Tout d'abord, ouvrez Visual Studio, créez une nouvelle **Application console (.NET Core)**, puis ajoutez le package NuGet Aspose.Words :

```bash
dotnet add package Aspose.Words
```

> **Astuce :** Si vous avez un fichier de licence (`Aspose.Words.lic`), copiez‑le à la racine du projet et chargez‑le au démarrage. Cela évite le filigrane qui apparaît en mode d'évaluation gratuit.

```csharp
// Load the license (optional but recommended)
var license = new Aspose.Words.License();
license.SetLicense("Aspose.Words.lic");
```

---

## Étape 2 – Créez un nouveau document vierge

Nous allons maintenant **créer un document Word en utilisant Aspose**. Cet objet servira de toile pour notre forme.

```csharp
// Step 2: Initialize a new blank document
Document doc = new Document();   // Represents an empty .docx file
```

La classe `Document` est le point d'entrée pour tout le reste — paragraphes, sections, et bien sûr, objets de dessin.

---

## Étape 3 – Insérez une forme rectangulaire

Avec le document prêt, nous pouvons ajouter une forme. Ici nous choisissons un simple rectangle, mais la même logique fonctionne pour des cercles, des lignes ou des polygones personnalisés.

```csharp
// Step 3: Create a rectangular shape that will hold the shadow
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width  = 150,   // Width in points (1 point = 1/72 inch)
    Height = 100    // Height in points
};
```

> **Pourquoi une forme ?** Dans Aspose.Words, un objet `Shape` peut contenir du texte, des images, ou simplement servir d'élément décoratif. Ajouter une ombre à une forme est bien plus simple que de manipuler un cadre d'image.

---

## Étape 4 – Configurez l'ombre (Ajouter une ombre à une forme)

C’est le cœur du tutoriel — **comment ajouter une ombre à une forme** et affiner son apparence. La propriété `ShadowFormat` vous donne un contrôle total.

```csharp
// Step 4: Enable the shadow and configure its appearance
rectangle.ShadowFormat.Visible       = true;   // Turn the shadow on
rectangle.ShadowFormat.Blur          = 5.0;    // Blur radius – higher = softer edges
rectangle.ShadowFormat.Distance      = 3.0;    // Offset distance from the shape
rectangle.ShadowFormat.Angle         = 45;     // Direction in degrees (0 = right, 90 = down)
rectangle.ShadowFormat.Transparency  = 0.3;    // 30 % transparent – this is how we **apply shadow transparency**
```

### Ce que chaque propriété fait

| Propriété | Effet | Valeurs typiques |
|-----------|-------|-------------------|
| **Visible** | Active ou désactive l'ombre. | `true` / `false` |
| **Blur** | Adoucit les bords de l'ombre. | `0` (dur) à `10` (très doux) |
| **Distance** | Déplace l'ombre loin de la forme. | `1`–`5` points est courant |
| **Angle** | Contrôle la direction du décalage. | `0`–`360` degrés |
| **Transparency** | Rend l'ombre partiellement transparente. | `0` (opaque) à `1` (invisible) |

> **Cas limite :** Si vous définissez `Transparency` à `1`, l'ombre disparaît complètement — utile pour la désactiver programmatique.

---

## Étape 5 – Ajoutez la forme au document

Nous attachons maintenant la forme au premier paragraphe du corps du document. Aspose crée automatiquement un paragraphe s'il n'en existe pas.

```csharp
// Step 5: Append the shape to the first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(rectangle);
```

Si votre document contient déjà du contenu, vous pouvez insérer la forme à n'importe quel nœud en utilisant `InsertAfter` ou `InsertBefore`.

---

## Étape 6 – Enregistrez le document

Enfin, écrivez le fichier sur le disque. Vous pouvez choisir n'importe quel format supporté (`.docx`, `.pdf`, `.odt`, etc.), mais pour ce tutoriel nous resterons sur le format natif Word.

```csharp
// Step 6: Save the document with the shadowed shape
string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowedShape.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Ouvrez le `ShadowedShape.docx` résultant dans Microsoft Word, et vous verrez un rectangle avec une ombre douce à 45 degrés, 30 % transparente — exactement ce que nous avons configuré.

---

## Exemple complet fonctionnel

Voici le programme **complet, prêt à copier‑coller** qui intègre toutes les étapes ci‑dessus. Enregistrez‑le sous `Program.cs` et exécutez‑le avec `dotnet run`.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // OPTIONAL: Load Aspose.Words license (remove if using trial)
        // -------------------------------------------------
        try
        {
            var license = new License();
            license.SetLicense("Aspose.Words.lic");
        }
        catch (Exception ex)
        {
            Console.WriteLine("License not found – running in evaluation mode: " + ex.Message);
        }

        // -------------------------------------------------
        // 1. Create a new blank document
        // -------------------------------------------------
        Document doc = new Document();

        // -------------------------------------------------
        // 2. Insert a rectangle shape
        // -------------------------------------------------
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width  = 150,
            Height = 100
        };

        // -------------------------------------------------
        // 3. Configure the shadow – this is where we **add shadow to shape**
        // -------------------------------------------------
        rectangle.ShadowFormat.Visible      = true;   // Show the shadow
        rectangle.ShadowFormat.Blur         = 5.0;    // Soft edges
        rectangle.ShadowFormat.Distance     = 3.0;    // Offset distance
        rectangle.ShadowFormat.Angle        = 45;     // Direction in degrees
        rectangle.ShadowFormat.Transparency = 0.3;    // 30 % transparent (apply shadow transparency)

        // -------------------------------------------------
        // 4. Add the shape to the document
        // -------------------------------------------------
        doc.FirstSection.Body.FirstParagraph.AppendChild(rectangle);

        // -------------------------------------------------
        // 5. Save the file
        // -------------------------------------------------
        string outFile = Path.Combine(Environment.CurrentDirectory, "ShadowedShape.docx");
        doc.Save(outFile);
        Console.WriteLine($"Document created successfully: {outFile}");
    }
}
```

**Sortie attendue :** Un fichier nommé `ShadowedShape.docx` contenant un seul rectangle avec une ombre subtile, semi‑transparente, inclinée à 45°.

---

## Variantes & astuces avancées

### Changer la couleur de l'ombre

Par défaut, l'ombre hérite de la couleur de remplissage de la forme, mais vous pouvez définir une couleur personnalisée :

```csharp
rectangle.ShadowFormat.Color = System.Drawing.Color.Gray;
```

### Plusieurs formes avec des ombres différentes

Si vous avez besoin de plusieurs formes, répétez simplement les étapes de création et de configuration. Pensez à donner à chaque forme un nom unique si vous prévoyez de les référencer plus tard.

### Exportation en PDF avec les ombres conservées

Aspose.Words conserve les effets d'ombre lors de l'enregistrement en PDF :

```csharp
doc.Save("ShadowedShape.pdf");
```

### Pièges courants

| Symptom | Likely Cause | Fix |
|---------|--------------|-----|
| Ombre non visible | `ShadowFormat.Visible` left as `false` | Définir sur `true`. |
| L'ombre semble trop dure | `Blur` set to `0` | Augmenter `Blur` à 3–6. |
| L'ombre disparaît dans le PDF | Using an old Aspose.Words version (< 22.9) | Mettre à jour vers la dernière bibliothèque. |

---

## Conclusion

Nous avons couvert **comment ajouter une ombre à une forme** avec Aspose.Words, depuis l'initialisation d'un document jusqu'à l'ajustement du flou, de la distance, de l'angle et **l'application de la transparence de l'ombre**. L'exemple complet montre une approche propre, prête pour la production, que vous pouvez adapter à n'importe quelle forme ou mise en page de document.

Vous avez des questions sur **créer un document Word en utilisant Aspose** pour des scénarios plus complexes — comme des tableaux avec des ombres ou des formes dynamiques alimentées par des données ? Laissez un commentaire ci‑dessous ou consultez les tutoriels associés sur la gestion des images et le formatage des paragraphes avec Aspose.Words.

Bon codage, et profitez de donner à vos documents Word ce petit plus visuel !

--- 

![exemple d'ajout d'ombre à une forme](shadowed_shape.png "exemple d'ajout d'ombre à une forme")

{{< layout-end >}}

{{< layout-end >}}