---
category: general
date: 2026-04-04
description: Créer une forme rectangulaire en C# avec Aspose.Words et apprendre à
  ajouter une ombre, appliquer un flou à l'ombre et rendre l'ombre transparente –
  guide étape par étape.
draft: false
keywords:
- create rectangle shape
- how to add shadow
- how to create document
- apply blur to shadow
- make shadow transparent
language: fr
og_description: Créer une forme rectangulaire en C# avec Aspose.Words. Apprenez comment
  ajouter une ombre, appliquer un flou à l'ombre et rendre l'ombre transparente dans
  un tutoriel concis.
og_title: Créer une forme rectangulaire et comment ajouter une ombre en C#
tags:
- Aspose.Words
- C#
- Document Automation
title: Créer une forme rectangulaire et comment ajouter une ombre en C#
url: /fr/net/programming-with-shapes/create-rectangle-shape-and-how-to-add-shadow-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer une forme rectangulaire et comment ajouter une ombre en C#

Vous avez déjà eu besoin de **create rectangle shape** dans un document Word mais vous ne saviez pas comment lui donner une ombre portée subtile ? Vous n’êtes pas seul. Dans de nombreux scénarios de reporting ou de branding, un simple rectangle avec une ombre douce et semi‑transparente peut rendre la mise en page plus raffinée sans beaucoup d’effort.

Dans ce tutoriel, nous allons parcourir **how to create document** avec Aspose.Words, puis montrer **how to add shadow**, **apply blur to shadow**, et même **make shadow transparent**. À la fin, vous disposerez d’un extrait C# prêt à l’exécution qui produit un fichier *.docx* avec un rectangle joliment ombré — le tout en quelques minutes.

## Ce dont vous aurez besoin

- .NET 6 ou version ultérieure (l’API fonctionne également avec .NET Framework 4.6+)
- Aspose.Words for .NET (l’essai gratuit suffit pour cet exemple)
- Un éditeur de code – Visual Studio, VS Code, Rider, ou celui que vous préférez
- Connaissances de base en C# – rien de compliqué, juste la capacité d’exécuter une application console

Si vous avez tout cela, nous pouvons passer directement à la solution.

## Étape 1 – How to create document et initialiser le canevas

Tout d’abord : vous avez besoin d’un objet `Document` vierge. Pensez‑y comme à une feuille blanche qu’Aspose.Words transformera ensuite en fichier Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Create a new blank document
Document doc = new Document();
```

Pourquoi instancier `Document` au lieu de charger un modèle ? Partir de zéro garantit qu’aucun style ou section caché n’interfère avec notre rectangle. Cela maintient également la taille du fichier minime – une bonne habitude lorsque vous générez de nombreux documents en boucle.

## Étape 2 – Create rectangle shape (le cœur de notre mot‑clé principal)

Nous allons maintenant **create rectangle shape**. La classe `Shape` est flexible ; vous indiquez le type (Rectangle), la taille, et comment il doit s’enrouler autour du texte environnant.

```csharp
// Define a rectangular shape
Shape rect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,               // Width in points (≈2.8 inches)
    Height = 100,              // Height in points (≈1.4 inches)
    WrapType = WrapType.Inline // Makes the shape behave like a character
};
```

Remarquez l’utilisation de la syntaxe d’initialisation d’objet – c’est concis et réduit le risque d’oublier de définir une propriété plus tard. Le rectangle sera placé dans le premier paragraphe, que nous ajouterons à l’étape suivante.

## Étape 3 – How to add shadow et personnaliser son apparence

Ajouter une ombre n’est pas une simple ligne ; vous avez plusieurs propriétés à ajuster. C’est ici que les mots‑clés secondaires **apply blur to shadow** et **make shadow transparent** entrent en jeu.

```csharp
// Configure the shadow
rect.Shadow.Format.Color = Color.DarkGray;   // Shadow colour
rect.Shadow.Format.BlurRadius = 5.0;         // Apply blur to shadow (points)
rect.Shadow.Format.OffsetX = 3;              // Horizontal offset
rect.Shadow.Format.OffsetY = 3;              // Vertical offset
rect.Shadow.Format.Transparency = 0.3;       // 30 % transparent (make shadow transparent)
```

Une petite note sur les valeurs : `BlurRadius` de 5 donne un flou doux ; augmentez à 10 pour un rendu plus moelleux, ou réduisez à 2 pour un bord net. La valeur `Transparency` varie de 0 (opaque) à 1 (invisible). Ajustez selon les exigences de contraste de votre marque.

### Astuce pro

Si vous avez besoin d’une ombre colorée (par exemple un bleu d’entreprise), remplacez simplement `Color.DarkGray` par `Color.FromArgb(80, 0, 120, 215)`. Le premier argument représente le canal alpha – gardez‑le bas pour plus de subtilité.

## Étape 4 – Insert the shape into the document

Avec le rectangle et son ombre prêts, nous le plaçons maintenant dans le premier paragraphe du document. Cette étape garantit que la forme apparaît tout en haut du fichier.

```csharp
// Append the shape to the first paragraph of the first section
doc.FirstSection.Body.FirstParagraph.AppendChild(rect);
```

Pourquoi le premier paragraphe ? C’est une valeur sûre qui fonctionne même lorsque le document est complètement vide. Si vous avez un emplacement spécifique (par ex. après un titre), vous localiseriez ce nœud et inséreriez la forme à cet endroit.

## Étape 5 – Save the file and verify the result

Enfin, nous enregistrons le document sur le disque. Vous pouvez choisir n’importe quel chemin ; assurez‑vous simplement que le dossier existe.

```csharp
// Save the document
doc.Save(@"C:\Temp\ShadowRectangle.docx");
```

Lorsque vous ouvrez *ShadowRectangle.docx* dans Microsoft Word, vous devriez voir un rectangle de 200 × 100 points avec une ombre gris‑foncé, légèrement floutée, à 30 % de transparence, décalée de trois points vers la droite et le bas. L’effet est subtil mais ajoute de la profondeur à des mises en page autrement plates.

![create rectangle shape with shadow in Aspose.Words](https://example.com/placeholder-image.png "create rectangle shape with shadow in Aspose.Words")

*Texte alternatif de l’image :* **create rectangle shape with shadow in Aspose.Words** – l’image montre le document final avec le rectangle ombré.

## Variations courantes et cas limites

### Changer la couleur de l’ombre dynamiquement

Si votre application prend en charge les thèmes, vous pouvez récupérer la couleur de l’ombre depuis un fichier de configuration :

```csharp
Color themeShadow = ColorTranslator.FromHtml(ConfigurationManager.AppSettings["ShadowColor"]);
rect.Shadow.Format.Color = themeShadow;
```

### Rendre la forme non‑inline

Parfois, vous voulez que le rectangle flotte au-dessus du texte. Changez `WrapType` en `WrapType.Square` et définissez `RelativeHorizontalPosition` sur `RelativeHorizontalPosition.Margin` pour plus de contrôle.

```csharp
rect.WrapType = WrapType.Square;
rect.RelativeHorizontalPosition = RelativeHorizontalPosition.Margin;
rect.Left = 72; // 1 inch from the left margin
```

### Gestion de plusieurs pages

Si vous avez besoin d’un rectangle sur chaque page, parcourez `doc.Sections` et ajoutez une forme clonée au premier paragraphe de chaque section. N’oubliez pas d’appeler `rect.Clone(true)` pour dupliquer également les paramètres d’ombre.

## Récapitulatif – Ce que nous avons accompli

- **Created rectangle shape** avec Aspose.Words
- **How to add shadow** avec couleur, décalage, flou et transparence
- Démonstration de **apply blur to shadow** et **make shadow transparent**
- Enregistrement d’un fichier Word que vous pouvez ouvrir immédiatement

Tout cela a été réalisé avec seulement quelques lignes, prouvant que des ajustements visuels sophistiqués ne nécessitent pas toujours des bibliothèques graphiques lourdes.

## Et après ?

- Expérimentez avec d’autres `ShapeType`s (Ellipse, Cloud, etc.) et observez le comportement des ombres.
- Combinez le rectangle avec des zones de texte pour créer des encadrés annotés.
- Plongez dans **how to create document** templates contenant déjà des espaces réservés pour les formes, puis remplissez‑les programmatiquement.

N’hésitez pas à ajuster le rayon du flou, la couleur ou la transparence jusqu’à ce que l’ombre corresponde parfaitement à votre langage de design. L’API est indulgente, et les changements sont visibles instantanément lorsque vous relancez l’application console.

Bon codage, et que vos documents possèdent toujours cette touche supplémentaire de profondeur !

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}