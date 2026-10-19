---
category: general
date: 2026-03-01
description: Créer un document Word avec Aspose.Words et apprendre comment ajouter
  une forme rectangulaire, comment ajouter une ombre, comment définir la transparence
  et comment créer une forme — le tout en C#.
draft: false
keywords:
- create word document
- add rectangle shape
- how to add shadow
- how to create shape
- how to set transparency
language: fr
og_description: Créer un document Word avec Aspose.Words en C#. Apprenez à ajouter
  une forme rectangulaire, appliquer une ombre extérieure et régler la transparence
  en quelques étapes seulement.
og_title: Créer un document Word avec une forme rectangulaire et une ombre – Guide
tags:
- Aspose.Words
- C#
- Document Generation
title: Créer un document Word avec une forme rectangle et une ombre – Guide étape
  par étape
url: /fr/net/programming-with-shapes/create-word-document-with-a-rectangle-shape-and-shadow-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un document Word avec une forme rectangulaire et une ombre – Guide étape par étape

Vous avez déjà eu besoin de **créer un document Word** contenant un rectangle au style personnalisé ? Peut‑être que vous construisez un modèle de rapport et que vous voulez une ombre portée subtile pour faire ressortir la mise en page. Vous n’êtes pas le seul — les développeurs demandent constamment : « Comment ajouter une forme rectangulaire et une ombre par programme ? » La bonne nouvelle, c’est qu’avec Aspose.Words, vous pouvez le faire en quelques lignes.

Dans ce tutoriel, nous parcourrons l’ensemble du processus : de la création d’un fichier Word vierge, à l’ajout d’une forme rectangulaire, en passant par la configuration d’une ombre extérieure avec transparence. À la fin, vous disposerez d’un fichier `Shadow.docx` prêt à l’emploi que vous pourrez ouvrir dans Word et voir l’effet immédiatement. Aucun outil externe, aucun XML compliqué — juste du code C# propre et des explications claires.

## Ce que vous allez apprendre

- **Comment créer des objets shape** dans un document Word avec Aspose.Words.  
- **Comment ajouter une forme rectangulaire** à un paragraphe sans perturber le contenu existant.  
- **Comment ajouter une ombre** (ombre extérieure) et contrôler sa couleur, son décalage, son flou et sa transparence.  
- **Comment définir la transparence** de l’ombre pour un rendu professionnel.  
- Astuces, pièges et variantes utiles dans des projets réels.

### Prérequis

- .NET 6.0 ou supérieur (l’API fonctionne également avec .NET Framework 4.6+).  
- Aspose.Words for .NET installé via NuGet (`Install-Package Aspose.Words`).  
- Une compréhension de base de la syntaxe C# — rien de compliqué, juste les habituelles instructions `using` et la création d’objets.

> **Astuce pro :** Si vous utilisez Visual Studio, activez les “nullable reference types” pour détecter les éventuels bugs de référence nulle dès le départ.

## Étape 1 – Créer un document Word vierge

Pour **créer un document Word** nous commençons avec la classe `Document`. Considérez‑la comme une toile vide ; vous pourrez ensuite ajouter des sections, paragraphes, tableaux ou formes.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Initialize a new blank document
Document document = new Document();
```

Pourquoi avons‑nous besoin d’une nouvelle instance `Document ?` Parce que chaque forme, paragraphe ou style vit à l’intérieur d’un modèle d’objet de document (DOM). Commencer avec un document propre garantit que le rectangle que vous ajoutez n’interférera pas avec le contenu existant.

## Étape 2 – Définir la forme rectangulaire

Maintenant nous **comment créer shape** un rectangle. Le constructeur `Shape` prend le document propriétaire et le type de forme. Nous définissons également sa largeur et sa hauteur en points (1 pt ≈ 1/72 in).

```csharp
// Create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width = 200;   // 200 pt ≈ 2.78 in
rectangleShape.Height = 100; // 100 pt ≈ 1.39 in
```

Vous vous demandez peut‑être : « Puis‑je utiliser des centimètres au lieu de points ? » L’API n’accepte que les points, mais vous pouvez convertir : `points = centimeters * 28.35`. Cette petite conversion est pratique lorsque vous alignez les formes sur les marges de la page.

## Étape 3 – Ajouter une ombre extérieure et définir la transparence

Voici où la magie opère : **comment ajouter shadow** et **comment définir transparency** sur cette ombre. La propriété `ShadowFormat` vous donne un contrôle total.

```csharp
// Enable shadow visibility
rectangleShape.ShadowFormat.Visible = true;

// Choose a shadow color
rectangleShape.ShadowFormat.Color = System.Drawing.Color.DarkGray;

// Set transparency (0 = opaque, 1 = fully transparent)
rectangleShape.ShadowFormat.Transparency = 0.3; // 30 % transparent

// Position the shadow relative to the shape
rectangleShape.ShadowFormat.OffsetX = 5; // horizontal offset in points
rectangleShape.ShadowFormat.OffsetY = 5; // vertical offset in points

// Blur makes the shadow look softer
rectangleShape.ShadowFormat.BlurRadius = 4;

// Specify that this is an outer shadow (instead of inner)
rectangleShape.ShadowFormat.Style = ShadowStyle.OuterShadow;
```

**Pourquoi ces réglages ?**  
- **Transparency** laisse la texture de la page sous‑jacent transparaître, évitant que l’ombre ne paraisse trop lourde.  
- **OffsetX/Y** créent l’illusion que la forme est soulevée de la page.  
- **BlurRadius** adoucit les bords — sans cela, l’ombre serait un rectangle dur, ce qui paraît artificiel.  

Si vous désirez un effet plus dramatique, augmentez `OffsetX/Y` à 10 et `BlurRadius` à 8. À l’inverse, pour une suggestion subtile, conservez‑les à 2 et 2 respectivement.

## Étape 4 – Insérer la forme dans le document

Nous **ajoutons rectangle shape** au premier paragraphe du document. Si le document ne contient aucun contenu, `FirstParagraph` est créé automatiquement pour vous.

```csharp
// Append the rectangle to the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

Et si vous voulez la forme dans une cellule de tableau spécifique ou dans un paragraphe ultérieur ? Localisez simplement ce nœud (`doc.GetChild(NodeType.Paragraph, index, true)`) et appelez `AppendChild` dessus. Le même objet `Shape` peut être cloné si vous avez besoin de plusieurs copies.

## Étape 5 – Enregistrer le document

Enfin, nous **créons word document** sur le disque. Utilisez un chemin qui convient à votre environnement ; l’exemple utilise un espace réservé.

```csharp
// Save the document as a .docx file
document.Save(@"YOUR_DIRECTORY/Shadow.docx");
```

Lorsque vous ouvrirez `Shadow.docx` dans Microsoft Word, vous verrez un rectangle gris clair avec une ombre extérieure douce décalée vers le bas‑à‑droite. La transparence de 30 % de l’ombre garantit qu’elle ne domine pas la page.

---

![Create word document with a shadowed rectangle shape](image.png "Create word document with a shadowed rectangle shape")

*Texte alternatif de l’image : créer un document Word avec une forme rectangulaire ombrée*

## Code complet, prêt à être exécuté

Voici le programme complet que vous pouvez copier‑coller dans une application console. Aucun morceau manquant, aucune référence « voir la documentation ».

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Step 2: Add a rectangular shape and define its size
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width = 200;   // width in points
        rectangleShape.Height = 100;  // height in points

        // Step 3: Configure an outer shadow for the shape
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = System.Drawing.Color.DarkGray;
        rectangleShape.ShadowFormat.Transparency = 0.3;   // 30 % transparent
        rectangleShape.ShadowFormat.OffsetX = 5;          // horizontal offset
        rectangleShape.ShadowFormat.OffsetY = 5;          // vertical offset
        rectangleShape.ShadowFormat.BlurRadius = 4;
        rectangleShape.ShadowFormat.Style = ShadowStyle.OuterShadow;

        // Step 4: Insert the shape into the first paragraph of the document
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // Step 5: Save the document with the shadowed shape
        document.Save(@"YOUR_DIRECTORY/Shadow.docx");

        Console.WriteLine("Word document created successfully at YOUR_DIRECTORY/Shadow.docx");
    }
}
```

### Résultat attendu

- Un fichier nommé **Shadow.docx** apparaît dans le dossier cible.  
- En l’ouvrant dans Word, vous voyez un rectangle (200 × 100 pt) avec une ombre extérieure gris‑foncé.  
- L’ombre est décalée de 5 pt horizontalement et verticalement, floutée, et possède 30 % de transparence.

## Questions fréquentes & cas particuliers

| Question | Réponse |
|----------|--------|
| **Puis‑je changer la couleur de l’ombre pour qu’elle corresponde à ma charte ?** | Absolument — remplacez simplement `System.Drawing.Color.DarkGray` par la `Color` de votre choix, par ex. `Color.FromArgb(255, 0, 120, 215)` pour un accent bleu. |
| **Et si j’ai besoin d’une ombre intérieure au lieu d’une ombre extérieure ?** | Réglez `ShadowFormat.Style = ShadowStyle.InnerShadow`. Le reste des propriétés fonctionne de la même façon. |
| **La transparence est‑elle prise en charge dans les anciennes versions de Word ?** | Oui. Aspose.Words écrit le XML approprié que Word 2007+ comprend. Les versions plus anciennes peuvent ignorer la valeur de transparence mais afficheront tout de même l’ombre. |
| **Puis‑je ajouter plusieurs formes avec des ombres différentes ?** | Bien sûr — créez simplement de nouvelles instances `Shape`, configurez chaque ombre indépendamment, puis ajoutez‑les aux nœuds souhaités. |
| **Qu’en est‑il des performances avec des centaines de formes ?** | Créer de nombreuses formes peut augmenter l’utilisation de mémoire. Réutilisez une même instance `Document` et ajoutez les formes dans une boucle ; libérez les objets temporaires si vous rencontrez des contraintes. |

## Conseils pour les projets réels

- **Génération par lots :** Lors de la création de rapports pour de nombreux utilisateurs, instanciez un seul modèle `Document` et clonez‑le pour chaque itération. Remplacez les espaces réservés avant d’ajouter les formes.  
- **Dimensionnement dynamique :** Utilisez les dimensions de page (`document.FirstSection.PageSetup.PageWidth`) pour calculer la taille de la forme en fonction de la page, assurant une mise en page cohérente sur différents formats de papier.  
- **Tests :** Ouvrez toujours le `.docx` généré dans Word après chaque modification des paramètres d’ombre. Le retour visuel est plus rapide que de deviner les valeurs.  

## Prochaines étapes

Maintenant que vous savez **comment ajouter rectangle shape**, **comment ajouter shadow**, et **comment définir transparency**, explorez :

- Ajouter des **dégradés de remplissage** aux formes (`Shape.FillFormat`).  
- Intégrer des **images** à l’intérieur des formes pour des effets de filigrane.  
- Utiliser des **tableaux** pour aligner plusieurs formes ombrées en grille.  
- Exporter le même document en PDF (`document.Save("output.pdf")`) tout en conservant les ombres.  

Chacune de ces extensions repose sur les mêmes concepts de base, vous vous sentirez donc à l’aise pour les développer.

---

### Récapitulatif

Nous avons commencé par **créer un document Word** avec Aspose.Words, puis **comment créer shape** un rectangle, appliqué **comment ajouter shadow**, ajusté **comment définir transparency**, et enregistré le résultat. Le processus complet tient dans un modèle compact et réutilisable que vous pouvez adapter à n’importe quel scénario d’automatisation.

N’hésitez pas à expérimenter — changez les couleurs, jouez avec les décalages, ou empilez plusieurs formes. Si vous rencontrez un obstacle, revenez aux sections précédentes ; elles sont conçues comme une référence rapide. Bon codage, et que vos documents soient toujours impeccables !

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}