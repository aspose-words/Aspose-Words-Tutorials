---
category: general
date: 2026-02-26
description: Créez une forme rectangulaire dans Word en utilisant Aspose.Words et
  apprenez comment ajouter une forme à Word, appliquer une ombre à la forme et régler
  la transparence de la forme en quelques minutes.
draft: false
keywords:
- create rectangle shape
- add shape to word
- apply shadow to shape
- set shape transparency
- rectangle with shadow
language: fr
og_description: Créez une forme rectangulaire dans Word avec Aspose.Words. Apprenez
  à ajouter une forme à Word, à appliquer une ombre à la forme et à régler rapidement
  la transparence de la forme.
og_title: Créer une forme rectangulaire dans Word – Guide complet d'Aspose.Words
tags:
- Aspose.Words
- C#
- Word Automation
title: Créer une forme rectangulaire dans Word – Guide complet d’Aspose.Words
url: /fr/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/
---

Let's construct final output.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer une forme rectangulaire dans Word – Guide complet Aspose.Words

Vous avez déjà eu besoin de **create rectangle shape** dans un document Word mais vous ne saviez pas par où commencer ? Vous n'êtes pas seul—de nombreux développeurs rencontrent ce problème lorsqu'ils automatisent des rapports ou des factures. Dans ce tutoriel, nous allons parcourir un exemple complet, prêt à l'exécution, qui vous montre comment **add shape to Word**, appliquer une ombre subtile et contrôler la transparence de la forme, le tout avec Aspose.Words pour .NET.

À la fin du guide, vous disposerez d'un fichier `.docx` contenant un rectangle propre avec une ombre soignée—parfait pour le branding, les encadrés, ou simplement pour rendre votre document un peu plus professionnel. Aucun outil externe n'est requis, juste quelques lignes de C#.

## Ce dont vous avez besoin

- **Aspose.Words for .NET** (la dernière version au début de 2026). Vous pouvez l'obtenir depuis NuGet (`Install-Package Aspose.Words`).
- Un environnement de développement .NET (Visual Studio, Rider ou VS Code avec l'extension C#).
- Une connaissance de base de la syntaxe C#—rien de compliqué, juste les déclarations `using` habituelles et la création d'objets.

Si vous avez déjà tout cela, super—plongeons‑y.

## Créer une forme rectangulaire – Étapes principales

Voici le code source complet. Copiez‑collez‑le dans un nouveau projet console, appuyez sur **F5**, et vous verrez `ShadowDemo.docx` apparaître dans le dossier que vous spécifiez.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Needed for Color

// Step 1: Create a new blank document.
Document document = new Document();

// Step 2: Insert a rectangle shape and define its size.
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width  = 200,   // Width in points (≈2.78 inches)
    Height = 100    // Height in points (≈1.39 inches)
};

// Step 3: Apply a shadow with fine‑grained control over its appearance.
rectangleShape.Shadow = new Shadow
{
    BlurRadius   = 5.0,                     // Softness of the shadow edge
    Distance     = 4.0,                     // How far the shadow is offset
    Direction    = 45,                      // Angle of the offset (degrees)
    Color        = Color.Gray,              // Shadow colour
    Transparency = 0.2,                     // Opacity (0 = opaque, 1 = fully transparent)
    Spread       = 0.3                      // Size of the shadow spread
};

// Step 4: Add the shape to the first paragraph of the document.
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

// Step 5: Save the document with the shadowed shape.
document.Save("ShadowDemo.docx");
```

### Pourquoi cela fonctionne

- `Document` est le point d'entrée ; il représente le fichier Word complet.
- `Shape` avec `ShapeType.Rectangle` indique à Aspose que nous voulons un objet de dessin rectangulaire.
- Définir `Width` et `Height` donne à la forme une taille déterministe ; sinon elle utilise un petit espace réservé.
- L'objet `Shadow` nous permet d'ajuster finement chaque aspect visuel : flou, distance, direction, couleur, transparence et étendue. C’est le cœur de *apply shadow to shape*.
- Enfin, `AppendChild` insère la forme dans le premier paragraphe du document, ce qui est la façon la plus simple de *add shape to Word* sans gérer les tableaux ou les en‑têtes.

Lorsque vous ouvrez `ShadowDemo.docx`, vous verrez un rectangle gris posé confortablement dans le document, son ombre s'inclinant vers le bas‑droite à un angle de 45°. L'ombre n'est pas un bloc solide ; le rayon de flou adoucit les bords, et la transparence lui donne l'aspect d'une ombre portée naturelle plutôt que d'une superposition dure.

![exemple de création de forme rectangulaire](image.png "créer une forme rectangulaire avec ombre dans Word avec Aspose.Words")

*(L'image ci‑dessus montre le résultat final du fragment de code.)*

## Ajouter une forme à un document Word – Options de placement

L'exemple utilise le **premier paragraphe** car c'est le moyen le plus rapide de voir quelque chose à l'écran. Dans des scénarios réels, vous pourriez vouloir :

- Insérer la forme dans une **section** ou un **en‑tête/pied de page** spécifique.
- La placer à l'intérieur d'une **cellule de tableau** pour l'aligner avec des données tabulaires.
- L'envelopper avec des options de **habillage du texte** (par ex., `WrapType.Square`) afin que le texte environnant s'écoule autour du rectangle.

Voici une petite variante qui place la forme dans un nouveau paragraphe avec un style personnalisé :

```csharp
Paragraph para = new Paragraph(document);
para.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
para.AppendChild(rectangleShape);
document.FirstSection.Body.AppendChild(para);
```

*Astuce :* Ajoutez toujours la forme **après** avoir configuré ses propriétés ; sinon vous pourriez devoir appeler `UpdateLayout` pour rafraîchir l'apparence visuelle.

## Appliquer une ombre à la forme – Affiner l'apparence

Les ombres peuvent modifier de façon spectaculaire l'esthétique d'un document. La classe `Shadow` expose plusieurs propriétés :

| Propriété      | Ce qu'elle contrôle                                   | Valeurs typiques |
|----------------|-------------------------------------------------------|------------------|
| `BlurRadius`   | Douceur des bords de l'ombre                          | 2.0 – 10.0       |
| `Distance`     | Distance du décalage de l'ombre par rapport à la forme | 1.0 – 8.0        |
| `Direction`    | Angle en degrés (0 = gauche, 90 = haut)               | 0 – 360          |
| `Color`        | Couleur de l'ombre (tout `System.Drawing.Color`)     | Gray, Black, Custom |
| `Transparency` | Opacité (0 = totalement opaque, 1 = invisible)       | 0.0 – 0.5        |
| `Spread`       | Expansion de l'ombre avant l'application du flou     | 0.0 – 1.0        |

Si vous souhaitez un **aspect subtil et professionnel**, gardez `BlurRadius` autour de 4‑6 et `Transparency` près de 0,2, comme dans le code ci‑dessus. Pour un **effet dramatique**, augmentez `Distance` à 6, définissez `Direction` à 135° et réduisez `Transparency` à 0,05.

## Définir la transparence de la forme et l'étendue de l'ombre

La transparence ne concerne pas seulement l'ombre ; vous pouvez également rendre le rectangle lui‑même partiellement transparent :

```csharp
rectangleShape.FillColor = Color.LightBlue;
rectangleShape.Transparency = 0.3; // 30% transparent fill
```

### Cas limites à surveiller

1. Les versions plus anciennes de Word (pré‑2007) ne prennent pas en charge certaines propriétés d'ombre. Si vous ciblez des fichiers `.doc`, envisagez de simplifier l'ombre (par ex., définir `BlurRadius` à 0).
2. Les écrans à haute résolution DPI peuvent rendre l'ombre légèrement différemment. Testez dans l'environnement cible si la fidélité visuelle est cruciale.
3. Formes qui se chevauchent—Aspose rend les ombres dans l'ordre où elles sont ajoutées. Insérez les formes de l'arrière vers l'avant pour éviter une occlusion indésirable.

## Enregistrer et vérifier le résultat

La méthode `Document.Save` détecte automatiquement le format de sortie à partir de l'extension du fichier. Pour un fichier **`.docx`**, vous obtenez le format Open XML, que la plupart des processeurs Word modernes comprennent. Si vous avez besoin d'une version **PDF** avec le même style visuel, il suffit de changer l'extension :

```csharp
document.Save("ShadowDemo.pdf");
```

Ouvrir le `ShadowDemo.docx` généré (ou `ShadowDemo.pdf`) devrait afficher un **rectangle propre avec ombre**, confirmant que vous avez réussi à *create rectangle shape* et *apply shadow to shape* avec Aspose.Words.

## Questions fréquentes

**Q : Puis‑je utiliser une forme différente, comme une ellipse ?**  
**R : Absolument. Remplacez `ShapeType.Rectangle` par `ShapeType.Ellipse` (ou tout autre valeur de l'énumération `ShapeType`). Les propriétés d'ombre restent les mêmes.**

**Q : Et si je veux que le rectangle soit cliquable ?**  
**R : Vous pouvez assigner un hyperlien à la forme :**

```csharp
rectangleShape.Href = "https://example.com";
```

**Q : Cela fonctionne‑t‑il sur .NET 6+ ?**  
**R : Oui. Aspose.Words 23.11 et versions ultérieures supportent pleinement .NET 6, .NET 7 et .NET 8. Il suffit de référencer le package NuGet approprié.**

**Q : Comment changer la couleur de l'ombre pour qu'elle corresponde à ma marque ?**  
**R : Utilisez n'importe quel `System.Drawing.Color` que vous souhaitez :**

```csharp
rectangleShape.Shadow.Color = Color.FromArgb(255, 30, 144, 255); // DodgerBlue
```

## Conclusion

Nous avons couvert tout ce dont vous avez besoin pour **create rectangle shape** dans un document Word, **add shape to Word**, **apply shadow to shape**, et **set shape transparency**. Le code complet et exécutable se trouve en haut de cette page, et les explications devraient vous donner suffisamment de confiance pour ajuster les tailles, les couleurs et les paramètres d'ombre pour tout projet.

Prêt pour l'étape suivante ? Essayez d'expérimenter avec :

- Plusieurs formes superposées pour créer un effet de badge.
- Dimensionnement dynamique basé sur le contenu du document (par ex., calculer la largeur à partir d'une colonne de tableau).
- Exporter le document en PDF ou HTML tout en conservant l'ombre.

N'hésitez pas à laisser un commentaire si vous rencontrez des problèmes, ou à partager vos propres variantes du thème « rectangle avec ombre ».

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}