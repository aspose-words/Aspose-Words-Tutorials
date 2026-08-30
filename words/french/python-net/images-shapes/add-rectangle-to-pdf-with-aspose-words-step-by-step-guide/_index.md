---
category: general
date: 2026-03-01
description: Ajoutez rapidement un rectangle à un PDF à l’aide d’Aspose.Words. Apprenez
  à insérer une forme dans un PDF, à ajouter des graphiques à un PDF et à créer un
  document PDF de manière programmatique avec une ombre personnalisée.
draft: false
keywords:
- add rectangle to pdf
- insert shape pdf
- add graphics to pdf
- create pdf document programmatically
- create pdf with shape
language: fr
og_description: Ajouter un rectangle à un PDF avec Aspose.Words. Ce tutoriel montre
  comment insérer une forme dans un PDF, ajouter des graphiques à un PDF et créer
  un document PDF de façon programmatique en C#.
og_title: Ajouter un rectangle à un PDF avec Aspose.Words – Guide complet
tags:
- pdf
- aspnet
- csharp
- graphics
title: Ajouter un rectangle au PDF avec Aspose.Words – Guide étape par étape
url: /fr/python/images-shapes/add-rectangle-to-pdf-with-aspose-words-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ajouter un rectangle à un PDF avec Aspose.Words – Guide complet

Vous avez déjà eu besoin d'**ajouter un rectangle à un PDF** mais vous n'étiez pas sûr de quel appel d'API faisait le travail ? Vous n'êtes pas le seul—les développeurs demandent constamment « Comment insérer une forme PDF tout en gardant le fichier léger ? ». La bonne nouvelle, c'est qu'Aspose.Words rend cela très simple. Dans ce tutoriel, nous parcourrons l'ensemble du processus, de la création d'un document PDF programmatique à la mise en forme du rectangle avec une ombre.

Nous ajouterons également quelques bonus : vous apprendrez comment **ajouter des graphiques à un PDF**, voir les étapes exactes pour **insérer une forme PDF**, et terminer avec un exemple prêt à l'exécution qui **crée un PDF avec forme**. Aucun lien externe, juste une solution autonome que vous pouvez copier‑coller dès aujourd'hui.

## Prérequis

Avant de mettre les mains dans le cambouis, assurez‑vous d'avoir :

- .NET 6.0 ou version ultérieure (Aspose.Words fonctionne avec .NET Standard 2.0+)
- Une licence valide d'Aspose.Words for .NET ou une clé d'évaluation temporaire
- Visual Studio 2022 (ou tout IDE de votre choix)
- Connaissances de base en C#—rien de sophistiqué, juste la capacité d'exécuter une application console

C'est tout. Si vous avez cela, vous êtes prêt à partir.

## Étape 1 : Créer un document PDF programmatique

La première chose à faire lorsque vous voulez **ajouter un rectangle à un PDF** est de créer un document vide. Considérez la classe `Document` comme une toile vierge ; tout ce que vous ajoutez ensuite vit à l'intérieur.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1 – initialise a new empty document
        Document doc = new Document();

        // The rest of the steps follow...
```

Pourquoi commencer avec un document vide ? Parce que cela vous garantit un contrôle total sur chaque élément—pas d'en‑têtes ou de pieds de page cachés à gérer plus tard.

## Étape 2 : Initialiser un DocumentBuilder pour insérer une forme PDF

Un `DocumentBuilder` est votre pinceau de dessin. Il sait comment placer du texte, des images et, surtout pour nous, des formes. Sans lui, vous devriez manipuler vous‑même l'arbre de nœuds de bas niveau—un cauchemar pour la plupart des développeurs.

```csharp
        // Step 2 – create a builder that will let us add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Remarquez que nous n'avons pas encore ajouté de pages. Le builder créera automatiquement une page la première fois que vous insérez quelque chose, ce qui garde le code propre.

## Étape 3 : Insérer une forme rectangle – le cœur de « ajouter un rectangle à un PDF »

Voici la partie amusante : insérer le rectangle. La méthode `InsertShape` prend en charge des dizaines de valeurs `ShapeType` ; nous choisirons `ShapeType.Rectangle` et lui donnerons une taille de 200 × 100 points.

```csharp
        // Step 3 – insert a rectangle (200 × 100 points) into the document
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

À ce stade, le PDF contient déjà un rectangle simple. Si vous ouvrez le fichier maintenant, vous verrez une boîte simple placée dans le coin supérieur gauche de la première page. C’est la base pour **ajouter des graphiques à un PDF**.

## Étape 4 : Styliser le rectangle – ajouter une ombre personnalisée

Un rectangle sans style est ennuyeux. Donnons‑lui une ombre portée subtile afin qu'il *se démarque* lors du rendu du PDF. L'objet `ShadowFormat` contrôle tout, du rayon de flou à l'opacité.

```csharp
        // Step 4 – configure a custom shadow for the shape
        ShadowFormat shadow = rectangle.ShadowFormat;
        shadow.Visible = true;
        shadow.BlurRadius = 8.0;          // pixels
        shadow.Distance = 5.0;           // points from the shape
        shadow.Direction = 45.0;         // degrees clockwise
        shadow.Opacity = 0.6;            // 0‑1 range
        shadow.Color = Color.Black;
```

Pourquoi se donner la peine d'ajouter une ombre ? En plus d'améliorer l'esthétique, une ombre peut aider à différencier des graphiques qui se chevauchent—quelque chose dont vous pourriez avoir besoin lorsque vous **ajoutez des graphiques à un PDF** dans des rapports plus complexes.

## Étape 5 : Enregistrer le fichier – finaliser le flux « créer un PDF avec forme »

La dernière ligne écrit tout sur le disque. Aspose.Words choisit automatiquement la bonne version du PDF et intègre les ressources nécessaires.

```csharp
        // Step 5 – save the document as a PDF file
        doc.Save(@"C:\Temp\ShapeWithShadow.pdf");
    }
}
```

Ouvrez `ShapeWithShadow.pdf` et vous verrez un rectangle joliment ombré posé fièrement sur la page. C’est l’ensemble du flux **créer un document PDF programmatique**, condensé en moins de 30 lignes de code.

## Exemple complet fonctionnel – créer un PDF avec forme de A à Z

Ci-dessous le programme complet que vous pouvez copier‑coller dans un nouveau projet d'application console. Il inclut toutes les instructions `using`, la méthode `Main`, et un bref en‑tête de commentaire pour référence future.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectanglePdfDemo
{
    /// <summary>
    /// Demonstrates how to add a rectangle to PDF, configure a shadow,
    /// and save the result using Aspose.Words for .NET.
    /// </summary>
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create an empty PDF document
            Document doc = new Document();

            // 2️⃣ Initialise a DocumentBuilder – the tool that lets us add content
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert a rectangle shape (200 × 100 points) – this is the core of "add rectangle to pdf"
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);

            // 4️⃣ Apply a custom shadow – makes the graphic stand out
            ShadowFormat shadow = rect.ShadowFormat;
            shadow.Visible = true;
            shadow.BlurRadius = 8.0;   // pixels
            shadow.Distance = 5.0;    // points
            shadow.Direction = 45.0;  // degrees
            shadow.Opacity = 0.6;     // semi‑transparent
            shadow.Color = Color.Black;

            // 5️⃣ Save the document – the final step in creating a PDF with shape
            string outputPath = @"C:\Temp\ShapeWithShadow.pdf";
            doc.Save(outputPath);

            Console.WriteLine($"PDF saved successfully to {outputPath}");
        }
    }
}
```

**Résultat attendu :** un PDF d'une seule page où un rectangle de 200 × 100 points se trouve près du coin supérieur gauche, orné d'une ombre douce à 45 degrés. Ouvrez le fichier dans n'importe quel lecteur PDF pour vérifier.

## Questions fréquentes & cas particuliers

### Cela fonctionne-t-il avec d'autres types de forme ?

Absolument. Remplacez `ShapeType.Rectangle` par `ShapeType.Ellipse`, `ShapeType.Triangle`, ou toute autre des plus de 150 options prises en charge par Aspose.Words. Les mêmes propriétés `ShadowFormat` s'appliquent.

### Et si j'ai besoin du rectangle sur une page spécifique ?

Après avoir inséré la forme, vous pouvez la déplacer vers une autre page en ajustant la propriété `CurrentPage` du builder avant d'appeler `InsertShape`. Par exemple :

```csharp
builder.MoveToPage(3);
Shape rectOnPage3 = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

### Puis-je changer la couleur de remplissage du rectangle ?

Bien sûr. Utilisez la propriété `FillColor` :

```csharp
rect.FillColor = Color.LightBlue;
```

### Quel impact cela a-t-il sur la taille du fichier ?

Ajouter une forme simple et une ombre n'ajoute que quelques kilo‑octets. Si vous commencez à empiler de nombreux graphiques, envisagez de compresser les images ou d'utiliser des formes vectorielles pour garder le PDF léger.

### Une licence est‑elle requise pour la production ?

Aspose.Words fonctionne en mode évaluation, mais le PDF généré contiendra un filigrane. Achetez une licence pour une utilisation illimitée et pour supprimer le filigrane.

## Astuces & conseils (niveau Pro)

- **Insertion en lot :** Si vous avez besoin de dizaines de rectangles, parcourez une collection de coordonnées et réutilisez le même `DocumentBuilder`—les performances restent linéaires.
- **Superposition :** Définissez `rect.WrapType = WrapType.Inline` si vous voulez que le rectangle s'écoule avec le texte, ou `WrapType.Square` pour que le texte s'enroule autour.
- **Conformité PDF/A :** Appelez `doc.CompatibilityOptions.OptimizeForPdfA = true;` avant d'enregistrer si vous avez besoin d'un PDF adapté à l'archivage.

## Résumé visuel

![exemple d'ajout de rectangle à un pdf](https://example.com/rectangle-shadow.png "exemple d'ajout de rectangle à un pdf")

L'image illustre la mise en page finale du PDF : un rectangle épuré avec une ombre subtile, exactement ce que notre code produit.

## Conclusion

Vous savez maintenant **comment ajouter un rectangle à un PDF** en utilisant Aspose.Words, comment **insérer une forme PDF**, et comment **ajouter des graphiques à un PDF** avec un style personnalisé—tout en **créant un document PDF programmatique** et en terminant avec un exemple **créer un PDF avec forme** que vous pourrez réutiliser demain.  

Ensuite, essayez de remplacer le rectangle par un logo, ou combinez plusieurs formes pour créer un diagramme simple. Vous pouvez également explorer le texte enveloppé, la rotation, ou même l'intégration d'un hyperlien à l'intérieur de la forme. L'API est suffisamment riche pour vous permettre de transformer un PDF statique en un rapport interactif et riche en graphiques sans jamais quitter C#.

N'hésitez pas à expérimenter, et si vous rencontrez un problème, laissez un commentaire ci‑dessous. Bon codage !

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}