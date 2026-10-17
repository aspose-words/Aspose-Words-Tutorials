---
category: general
date: 2026-04-10
description: Comment définir une ombre sur une forme en C# – apprenez comment appliquer
  une ombre portée, modifier la transparence, ajuster le flou et ajouter une ombre
  de forme avec Aspose.Words.
draft: false
keywords:
- how to set shadow
- apply drop shadow
- how to change transparency
- how to adjust blur
- add shape shadow
language: fr
og_description: Comment ajouter une ombre à une forme en C# – ce tutoriel montre comment
  appliquer une ombre portée, modifier la transparence, ajuster le flou et ajouter
  une ombre de forme avec des exemples de code clairs.
og_title: Comment ajouter une ombre à une forme en C# – Guide complet
tags:
- Aspose.Words
- C#
- Document Automation
title: Comment ajouter une ombre à une forme en C# – guide étape par étape
url: /fr/net/programming-with-shapes/how-to-set-shadow-on-a-shape-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# comment appliquer une ombre à une forme en C# – Guide complet

Vous vous êtes déjà demandé **comment appliquer une ombre** à une forme lorsque vous créez un document Word de façon programmatique ? Vous n'êtes pas seul. De nombreux développeurs se heurtent à un mur lorsqu'ils ont besoin d'une ombre portée subtile pour une zone de texte, un logo ou une boîte d'appel, et la documentation de l'API reste parfois trop maigre.  

Dans ce tutoriel, nous parcourrons l’ensemble du processus : du chargement d’un fichier `.docx`, à la récupération de la première `Shape`, en passant par l’application d’une ombre portée, le réglage de sa transparence, l’ajustement du rayon de flou, et enfin le positionnement précis. À la fin, vous disposerez d’un extrait réutilisable fonctionnant avec Aspose.Words .NET 2023 ou ultérieur, et vous comprendrez *pourquoi* chaque propriété est importante.

## Ce dont vous avez besoin

- **Aspose.Words for .NET** (package NuGet `Aspose.Words`) – la bibliothèque qui nous fournit les classes `Document`, `Shape` et `ShadowFormat`.  
- **.NET 6+** (ou .NET Framework 4.7.2) – n’importe quel runtime récent convient.  
- Un simple fichier Word (`input.docx`) contenant déjà au moins une forme, comme une zone de texte.  
- Visual Studio, VS Code ou votre IDE préféré.

C’est tout. Aucun outil tiers supplémentaire, aucune interopérabilité COM, juste du C# pur.

![exemple d'application d'ombre](image-placeholder.png){:alt="comment appliquer une ombre à une forme dans un document Word"}

## Comment appliquer une ombre – Vue d’ensemble

L’idée principale derrière **comment appliquer une ombre** consiste à manipuler l’objet `ShadowFormat` qui appartient à une `Shape`. Pensez à `ShadowFormat` comme à une petite « feuille de style » pour l’ombre elle‑même : elle indique au moteur de rendu si l’ombre est visible, de quelle couleur elle doit être, son niveau de transparence, son degré de flou et où elle se situe par rapport à la forme.  

Ci‑dessous se trouve le programme *complet* exécutable. N’hésitez pas à le copier‑coller dans une application console, à appuyer sur **F5**, et à observer l’ombre apparaître dans le fichier `output.docx` enregistré.

```csharp
using System;
using System.Drawing;               // For Color
using Aspose.Words;                 // Core document classes
using Aspose.Words.Drawing;         // Shape & ShadowFormat

class ShadowDemo
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1: Load the Word document that contains the shape.
        // -------------------------------------------------
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // -------------------------------------------------
        // Step 2: Retrieve the first shape (e.g., a textbox) from the document.
        // -------------------------------------------------
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found – make sure input.docx has a textbox.");
            return;
        }

        // -------------------------------------------------
        // Step 3: Make the shadow visible.
        // -------------------------------------------------
        shape.ShadowFormat.Visible = true;

        // -------------------------------------------------
        // Step 4: Set the shadow colour to a dark gray.
        // -------------------------------------------------
        shape.ShadowFormat.Color = Color.DarkGray;

        // -------------------------------------------------
        // Step 5: Define the shadow's transparency (30 % transparent).
        // -------------------------------------------------
        shape.ShadowFormat.Transparency = 0.3;   // 0 = opaque, 1 = fully transparent

        // -------------------------------------------------
        // Step 6: Configure the blur radius (size) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Size = 6;            // Larger value = softer edges

        // -------------------------------------------------
        // Step 7: Set the offset distance and direction (angle) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Distance = 2;        // How far the shadow is from the shape
        shape.ShadowFormat.Angle = 45;          // Angle in degrees (0 = right, 90 = down)

        // -------------------------------------------------
        // Save the modified document.
        // -------------------------------------------------
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Shadow applied successfully! Check output.docx.");
    }
}
```

### Pourquoi ces réglages sont importants

- **Visible** – Sans activer ce drapeau, toutes les autres propriétés sont ignorées.  
- **Color** – Un gris foncé imite une ombre portée typique d’interface ; vous pouvez remplacer par n’importe quelle `Color`.  
- **Transparency** – 0,3 donne un aspect *doux* tout en conservant la lisibilité de la forme.  
- **Size** – Contrôle le flou ; une valeur de 6 suffit généralement pour un rendu professionnel.  
- **Distance & Angle** – Ensemble, ils définissent le *décalage* ; 2 pts à 45° produisent une ombre diagonale subtile.

Voilà l’essence de **comment appliquer une ombre**. Ensuite, nous détaillerons chaque partie afin que vous puissiez **appliquer une ombre portée**, **modifier la transparence**, **ajuster le flou**, et **ajouter une ombre à une forme** de façon isolée.

---

## Appliquer une ombre portée à une forme

Lorsque les gens demandent « comment **appliquer une ombre portée** en C# ?», ils ont souvent seulement besoin du basculement de visibilité et d’une couleur. Le fragment suivant isole ces deux lignes :

```csharp
shape.ShadowFormat.Visible = true;          // Turns the shadow on
shape.ShadowFormat.Color   = Color.Black;   // Classic black drop shadow
```

> **Astuce :** Si vous ciblez des versions plus anciennes de Word (2003‑2007), limitez‑vous aux couleurs standard. Certaines valeurs ARGB exotiques peuvent être ignorées par le moteur de rendu hérité.

---

## Comment modifier la transparence de l’ombre

La transparence s’exprime sous forme de **float compris entre 0 et 1**. Une valeur de **0** signifie une ombre totalement opaque ; **1** la rend invisible. La plupart des designers se situent autour de **0,2‑0,4** pour un rendu naturel.

```csharp
shape.ShadowFormat.Transparency = 0.35; // 35 % transparent
```

### Cas particuliers

- **Valeurs négatives** – Aspose.Words les ramènera à 0, mais il vaut mieux valider l’entrée.  
- **Valeurs > 1** – Raménées à 1, ce qui masque effectivement l’ombre.  

Si vous devez laisser les utilisateurs choisir un pourcentage, convertissez‑le d’abord :

```csharp
float percent = 30;                     // User enters 30 %
shape.ShadowFormat.Transparency = percent / 100f;
```

---

## Comment ajuster le flou (Size) de l’ombre

La propriété **Size** contrôle le rayon de flou. Des nombres plus grands produisent une ombre plus douce et plus diffusée. Elle est mesurée en points (pt), pas en pixels.

```csharp
shape.ShadowFormat.Size = 10;  // A generous blur for a “soft” effect
```

#### Quand utiliser un petit ou un grand flou

- **Petit flou (2‑4 pt)** – Idéal pour les appels d’interface où vous voulez un bord net.  
- **Grand flou (8‑12 pt)** – Convient aux rapports imprimés ou lorsque la forme est éloignée de l’arrière‑plan.

---

## Ajouter une ombre à une forme – Positionnement et direction

Le dernier élément de **ajouter une ombre à une forme** est le décalage. Deux propriétés travaillent ensemble :

| Propriété | Signification |
|----------|----------------|
| **Distance** | Distance entre l’ombre et la forme (en points). |
| **Angle**    | Direction du décalage (0° = droite, 90° = bas, 180° = gauche, 270° = haut). |

Exemple créant une ombre subtile en bas‑à‑droite :

```csharp
shape.ShadowFormat.Distance = 1.5; // Slight lift
shape.ShadowFormat.Angle    = 135; // Down‑left direction (135°)
```

Vous pouvez expérimenter avec les angles pour simuler une lumière provenant de différentes sources. Une astuce courante consiste à laisser l’utilisateur choisir une « source de lumière » dans une liste déroulante et à la mapper à une valeur d’angle.

---

## Exemple complet fonctionnel (Toutes les étapes combinées)

Voici le même programme que précédemment, mais avec **des commentaires supplémentaires** qui rendent la logique parfaitement claire. Copiez‑le dans `Program.cs` et exécutez‑le ; le fichier de sortie contiendra une zone de texte avec une ombre parfaitement réglée.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeShadowDemo
{
    class Program
    {
        static void Main()
        {
            // Load the source document (must contain at least one shape)
            Document doc = new Document("YOUR_DIRECTORY/input.docx");

            // Grab the first shape we encounter – usually a textbox or picture
            Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
            if (shape == null)
            {
                Console.WriteLine("No shape found in the document.");
                return;
            }

            // ---------- Apply Drop Shadow ----------
            shape.ShadowFormat.Visible = true;          // Turn it on
            shape.ShadowFormat.Color   = Color.DarkGray; // Soft dark colour

            // ---------- How to Change Transparency ----------
            shape.ShadowFormat.Transparency = 0.3; // 30 % transparent – looks natural

            // ---------- How to Adjust Blur ----------
            shape.ShadowFormat.Size = 6; // Moderate blur for a professional feel

            // ---------- Add Shape Shadow (position) ----------
            shape.ShadowFormat.Distance = 2; // Slight offset
            shape.ShadowFormat.Angle    = 45; // Diagonal down‑right

            // Save the result
            doc.Save("YOUR_DIRECTORY/output.docx");
            Console.WriteLine("Document saved with shadow. Open output.docx to verify.");
        }
    }
}
```

**Résultat attendu :** Ouvrez `output.docx`. La première zone de texte affichera une ombre gris foncé, 30 % transparente, légèrement floue (size = 6) et décalée de 2 pt à un angle de 45°. L’effet est subtil mais perceptible—exactement ce que recherchent la plupart des designers d’interface.

---

## Questions fréquentes & pièges

- **« Cela fonctionne‑t‑il aussi avec les images ? »**  
  Oui. Toute `Shape`—qu’il s’agisse d’une zone de texte, d’une image ou d’une forme auto‑générée—expose `ShadowFormat`. Remplacez simplement la logique de récupération de la forme par l’index ou le nom approprié.

- **« Et si le document contient plusieurs formes ? »**  
  Parcourez `doc.GetChildNodes(NodeType.Shape, true)` et appliquez les mêmes paramètres à chacune. Vous pouvez également filtrer par `shape.Name` ou `shape

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}