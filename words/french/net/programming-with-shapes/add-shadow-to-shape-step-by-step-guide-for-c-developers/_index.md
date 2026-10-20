---
category: general
date: 2026-02-21
description: Ajoutez une ombre à une forme en C# et apprenez comment personnaliser
  l'ombre, appliquer l'effet d'ombre et régler l'opacité de l'ombre avec un exemple
  complet et exécutable.
draft: false
keywords:
- add shadow to shape
- how to customize shadow
- apply shadow effect
- how to add shadow
- set shadow opacity
language: fr
og_description: Ajoutez une ombre à une forme en C# avec ce guide. Apprenez à personnaliser
  l'ombre, appliquer l'effet d'ombre et définir l'opacité de l'ombre en quelques lignes
  de code.
og_title: Ajouter une ombre à la forme – Tutoriel complet C#
tags:
- C#
- Aspose.Words
- Graphics
- Shadow Effect
title: Ajouter une ombre à la forme – Guide pas à pas pour les développeurs C#
url: /fr/net/programming-with-shapes/add-shadow-to-shape-step-by-step-guide-for-c-developers/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ajouter une ombre à une forme – Tutoriel complet C#

Vous avez déjà eu besoin d'**ajouter une ombre à une forme** dans un document Word mais vous ne saviez pas par où commencer ? Vous n'êtes pas le seul — de nombreux développeurs rencontrent ce problème lorsqu'ils peaufinent des rapports ou des flyers marketing. La bonne nouvelle ? En quelques étapes seulement, vous pouvez transformer un rectangle plat en un élément poli, tridimensionnel, qui saute de la page.

Dans ce guide, nous parcourrons un **exemple complet et exécutable** qui vous montre comment personnaliser l'ombre, appliquer l'effet d'ombre, et même définir l'opacité de l'ombre pour n'importe quelle forme. À la fin, vous disposerez d'un extrait réutilisable que vous pourrez insérer dans n'importe quel projet Aspose.Words, sans références mystérieuses requises.

## Prérequis

* **.NET 6.0** (ou version ultérieure) installé – le code fonctionne également avec .NET Framework 4.6+.
* **Aspose.Words for .NET** package NuGet – la version 23.9 ou plus récente est recommandée.
* Une compréhension de base du C# et de la programmation orientée objet.

Si le package NuGet vous manque, exécutez :

```bash
dotnet add package Aspose.Words
```

Maintenant que les bases sont posées, mettons les mains dans le cambouis.

## Étape 1 – Charger ou créer un document et récupérer la première forme

La première chose dont nous avons besoin est un objet `Document` contenant réellement une forme. Pour les besoins de l'exemple, nous créerons un nouveau document, insérerons un simple rectangle, puis le récupérerons.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // 1️⃣ Create a blank document
        Document doc = new Document();

        // 2️⃣ Add a new shape (a rectangle) to the first paragraph
        Shape rect = new Shape(doc, ShapeType.Rectangle);
        rect.Width = 150;
        rect.Height = 100;
        rect.WrapType = WrapType.Inline;
        rect.StrokeColor = Color.DarkBlue;
        rect.FillColor = Color.LightBlue;
        rect.StrokeWeight = 2.0;

        // Insert the shape into the document body
        doc.FirstSection.Body.FirstParagraph.AppendChild(rect);

        // 3️⃣ Retrieve the shape we just added (demonstrates add shadow to shape)
        Shape firstShape = doc.GetChild(NodeType.Shape, 0, true) as Shape;
        if (firstShape == null)
        {
            Console.WriteLine("No shape found – aborting.");
            return;
        }

        // The remaining steps modify the shadow of firstShape
```

**Pourquoi nous faisons cela :**  
Récupérer la forme via `GetChild` imite des scénarios réels où la forme existe déjà (par ex., chargée depuis un modèle). Cela garantit également que le code d'ombre suivant fonctionne sur un objet valide, évitant les exceptions de référence nulle.

> **Astuce :** Si vous travaillez avec plusieurs formes, utilisez `GetChild(NodeType.Shape, index, true)` ou parcourez `doc.GetChildNodes(NodeType.Shape, true)`.

## Étape 2 – Activer l'effet d'ombre

L'ombre d'une forme est désactivée par défaut. L'activer est la première condition préalable à toute personnalisation supplémentaire.

```csharp
        // 4️⃣ Enable the shadow
        firstShape.Shadow.Enabled = true;
```

**Pourquoi c'est important :**  
Sans définir `Enabled = true`, tout changement de propriété ultérieur (couleur, flou, décalage) est ignoré. Pensez-y comme allumer un interrupteur avant de pouvoir régler la luminosité de la lampe.

## Étape 3 – Choisir une couleur d'ombre (et pourquoi le noir est un bon point de départ)

Le choix de la couleur influence fortement la profondeur perçue. Le noir (ou un gris très foncé) est le plus courant car il fonctionne sur n'importe quel arrière-plan.

```csharp
        // 5️⃣ Set the shadow color – black gives a classic look
        firstShape.Shadow.Color = Color.Black;
```

**Alternative :**  
Si votre document a un arrière-plan sombre, essayez une teinte plus claire :

```csharp
        // firstShape.Shadow.Color = Color.FromArgb(150, 150, 150); // light gray
```

## Étape 4 – Définir l'opacité de l'ombre

L'opacité est exprimée par une valeur entre `0.0` (complètement transparent) et `1.0` (complètement opaque). Une ombre à 40 % de transparence paraît naturelle pour la plupart des conceptions UI.

```csharp
        // 6️⃣ Make the shadow 40 % transparent
        firstShape.Shadow.Transparency = 0.4; // 0 = opaque, 1 = invisible
```

**Comment personnaliser :**  
- **Plus subtil :** `0.2` (20 % transparent)  
- **Très léger :** `0.7` (70 % transparent)

## Étape 5 – Définir le flou et la douceur des bords

Le flou contrôle la douceur des bords de l'ombre. Une valeur de `4.0` fonctionne bien pour des formes de taille moyenne.

```csharp
        // 7️⃣ Soften the edges with a blur radius
        firstShape.Shadow.Blur = 4.0;
```

**Cas limites :**  
Si vous définissez `Blur` à `0`, l'ombre devient une silhouette aux bords durs, ce qui peut paraître agressif. À l'inverse, des valeurs supérieures à `10` peuvent faire ressembler l'ombre à une lueur.

## Étape 6 – Positionner l'ombre par rapport à la forme

Les valeurs de décalage déplacent l'ombre horizontalement (`OffsetX`) et verticalement (`OffsetY`). Les nombres positifs déplacent l'ombre vers le bas et vers la droite.

```csharp
        // 8️⃣ Position the shadow 5 points right and 5 points down
        firstShape.Shadow.OffsetX = 5;
        firstShape.Shadow.OffsetY = 5;
```

**Expérimentez :**  
- **Ombre portée :** `OffsetX = 0`, `OffsetY = 10`  
- **Effet levé :** `OffsetX = -5`, `OffsetY = -5`

## Étape 7 – Enregistrer et vérifier le résultat

Enfin, écrivez le document sur le disque et ouvrez-le dans Microsoft Word (ou tout visualiseur compatible) pour voir l'ombre en action.

```csharp
        // 9️⃣ Save the document
        string outPath = "ShadowedShape.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}. Open it to see the shadow.");
    }
}
```

Lorsque vous ouvrez **ShadowedShape.docx**, vous devriez voir un rectangle bleu clair avec une ombre noire douce, semi‑transparente, décalée de cinq points. Si l'ombre n'apparaît pas, vérifiez que `firstShape.Shadow.Enabled` est `true` et que vous utilisez une version récente d'Aspose.Words.

### Code source complet (prêt à copier‑coller)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class ShadowDemo
{
    static void Main()
    {
        Document doc = new Document();
        Shape rect = new Shape(doc, ShapeType.Rectangle);
        rect.Width = 150;
        rect.Height = 100;
        rect.WrapType = WrapType.Inline;
        rect.StrokeColor = Color.DarkBlue;
        rect.FillColor = Color.LightBlue;
        rect.StrokeWeight = 2.0;
        doc.FirstSection.Body.FirstParagraph.AppendChild(rect);

        Shape firstShape = doc.GetChild(NodeType.Shape, 0, true) as Shape;
        if (firstShape == null)
        {
            Console.WriteLine("No shape found – aborting.");
            return;
        }

        // Enable shadow
        firstShape.Shadow.Enabled = true;

        // Choose shadow color
        firstShape.Shadow.Color = Color.Black;

        // Set opacity (40 % transparent)
        firstShape.Shadow.Transparency = 0.4;

        // Soften edges
        firstShape.Shadow.Blur = 4.0;

        // Position shadow
        firstShape.Shadow.OffsetX = 5;
        firstShape.Shadow.OffsetY = 5;

        // Save document
        string outPath = "ShadowedShape.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}. Open it to see the shadow.");
    }
}
```

## Questions fréquentes & cas limites

| Question | Réponse |
|----------|--------|
| **Et si la forme est une image au lieu d'un rectangle ?** | Les mêmes propriétés d'ombre s'appliquent ; il suffit de s'assurer que le `ShapeType` de la forme est `Picture`. |
| **Puis-je animer l'ombre ?** | Aspose.Words ne prend pas en charge l'animation, mais vous pouvez générer plusieurs pages avec des décalages incrémentiels et utiliser PowerPoint pour l'animation. |
| **L'ombre fonctionne‑t‑elle lors de l'exportation en PDF ?** | Oui. Lorsque vous enregistrez le document au format PDF (`doc.Save("out.pdf")`), Aspose.Words conserve l'effet d'ombre. |
| **Comment supprimer l'ombre plus tard ?** | Définissez `firstShape.Shadow.Enabled = false;` ou simplement `firstShape.Shadow = null`. |
| **Y a‑t‑il une limite aux valeurs de flou ?** | En pratique, des valeurs supérieures à `15` font ressembler l'ombre à un halo et peuvent augmenter la taille du fichier. |

## Prochaines étapes – Maintenir l'élan

Maintenant que vous savez **comment ajouter une ombre** et **définir l'opacité de l'ombre**, envisagez d'explorer :

* **Comment personnaliser davantage l'ombre** avec `Shadow.Distance` pour un décalage plus prononcé.
* **Appliquer l'effet d'ombre** aux cadres de texte ou WordArt pour des conceptions de documents plus riches.
* **Combiner plusieurs ombres** (par ex., interne + externe) pour obtenir un aspect superposé.
* **Exporter en HTML** et voir comment le CSS `box‑shadow` reproduit les mêmes paramètres.

Si vous créez un générateur de rapports, parsemez d'ombres les en‑têtes, graphiques ou zones d'appel afin de guider le regard du lecteur. Expérimentez avec différentes couleurs et transparences — peut‑être une ombre bleue subtile pour un thème d'entreprise.

---

### TL;DR

Nous avons parcouru un **exemple complet et autonome** qui montre comment **ajouter une ombre à une forme**, **personnaliser l'ombre**, **appliquer l'effet d'ombre**, et **définir l'opacité de l'ombre** avec Aspose.Words en C#. Le code est prêt à être exécuté, les explications couvrent à la fois le *quoi* et le *pourquoi*, et vous disposez désormais d'une base solide pour styliser les formes dans tout projet d'automatisation Word.

Bon codage, et que vos documents aient toujours ce fini extra‑dimensionnel !

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}