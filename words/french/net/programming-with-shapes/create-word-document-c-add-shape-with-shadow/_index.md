---
category: general
date: 2026-03-27
description: Créer un document Word en C# et apprendre comment ajouter une forme,
  appliquer une ombre à la forme et définir la distance de l'ombre. Guide étape par
  étape pour Aspose.Words.
draft: false
keywords:
- create word document c#
- how to add shape
- apply shadow to shape
- how to create rectangle
- set shadow distance
language: fr
og_description: Créez un document Word en C# avec une forme rectangle et une ombre
  personnalisée. Suivez ce tutoriel complet pour définir la distance et le style de
  l'ombre.
og_title: Créer un document Word C# – Ajouter une forme avec ombre
tags:
- Aspose.Words
- C#
- Document Automation
title: Créer un document Word en C# – Ajouter une forme avec ombre
url: /fr/net/programming-with-shapes/create-word-document-c-add-shape-with-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un document Word C# – Ajouter une forme avec ombre

Vous avez déjà eu besoin de **create word document c#** qui contient un rectangle joliment stylisé ? Peut‑être que vous créez un modèle de rapport et souhaitez une ombre portée subtile pour faire ressortir la mise en page. Dans ce tutoriel, nous allons passer en revue exactement cela – comment ajouter une forme, appliquer une ombre à la forme, et même ajuster la distance de l’ombre en utilisant Aspose.Words.

Nous commencerons avec un document vierge, insérerons un rectangle, lui appliquerons une ombre prédéfinie, puis enregistrerons le fichier. À la fin, vous disposerez d’un .docx prêt à l’emploi que vous pourrez ouvrir dans Word et voir l’effet immédiatement. Aucun outil externe, juste du code C# pur.

## Prérequis

- .NET 6 (ou tout framework .NET récent) installé.
- Visual Studio 2022 ou VS Code avec l’extension C#.
- Package NuGet Aspose.Words pour .NET (`Aspose.Words` version 23.12 ou ultérieure).  
  Vous pouvez l’ajouter via la console du gestionnaire de packages :

  ```powershell
  Install-Package Aspose.Words
  ```

C’est tout – aucune DLL supplémentaire ou interop COM requise.

## Étape 1 : Initialiser un nouveau document et un builder – *create word document c#* bases

Tout d’abord, nous avons besoin d’un objet `Document` qui représente le fichier Word et d’un `DocumentBuilder` pour le modifier.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a blank Word document
Document document = new Document();

// DocumentBuilder lets us add content programmatically
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Pourquoi cette étape est importante :** La classe `Document` est le conteneur de toutes les parties du document Word (pages, styles, images). Le builder est l’API de haut niveau qui abstrait la manipulation des nœuds de bas niveau, facilitant la **create word document c#** sans avoir à gérer le XML directement.

## Étape 2 : Insérer une forme rectangle – *how to create rectangle*

Nous allons maintenant placer un rectangle sur la page. La taille est exprimée en points (1 pt ≈ 1/72 in).

```csharp
// Insert a rectangle 200 pt wide and 100 pt tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);

// Give the rectangle a light‑blue fill so we can see it clearly
rectangleShape.FillColor = Color.LightBlue;
```

> **Astuce :** Si vous avez besoin d’une forme différente, remplacez simplement `ShapeType.Rectangle` par `ShapeType.Ellipse`, `ShapeType.Triangle`, etc. Le même code fonctionne pour **how to add shape** de n’importe quel type.

## Étape 3 : Appliquer une ombre prédéfinie et l’ajuster – *apply shadow to shape*

Aspose.Words propose plusieurs formats d’ombre prédéfinis. Nous utiliserons `Preset1` puis personnaliserons la distance, le flou, la transparence et la couleur.

```csharp
// Choose a predefined shadow style
rectangleShape.Shadow.Format = ShadowFormat.Preset1;

// Adjust the shadow distance – this is the offset from the shape
rectangleShape.Shadow.Distance = 5; // measured in points

// Make the edge of the shadow a little fuzzy
rectangleShape.Shadow.BlurRadius = 3;

// Set the shadow to be 40 % transparent (0 = opaque, 1 = fully transparent)
rectangleShape.Shadow.Transparency = 0.4;

// Pick a gray tone for the shadow color
rectangleShape.Shadow.Color = Color.Gray;
```

> **Pourquoi personnaliser l’ombre ?** La propriété `Distance` contrôle la distance entre l’ombre et le rectangle – pensez‑y comme au « relief » que l’on voit dans un rendu 3D. Modifier `BlurRadius` adoucit les bords, tandis que `Transparency` vous permet de créer un aspect subtil et professionnel. Cela répond à l’exigence **set shadow distance** et vous montre comment **apply shadow to shape** de manière flexible.

## Étape 4 : Enregistrer le document – *create word document c#* finalisation

Enfin, écrivez le document sur le disque. Ajustez le chemin vers un dossier où vous avez les droits d’écriture.

```csharp
// Save the document as a .docx file
string outputPath = @"C:\Temp\ShadowShape.docx";
document.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Ouvrez le fichier résultant dans Microsoft Word, et vous verrez un rectangle bleu clair avec une ombre grisâtre douce décalée de 5 pt. C’est la preuve visuelle que vous avez réussi à **create word document c#** avec une forme stylisée.

![Create Word Document C# with Shadowed Shape](shadow-example.png){: .img alt="exemple de create word document c# montrant un rectangle avec ombre"}

## Variations optionnelles & cas limites

| Scénario | Ce qu’il faut changer | Pourquoi c’est important |
|----------|-----------------------|---------------------------|
| **Style d’ombre différent** | `rectangleShape.Shadow.Format = ShadowFormat.Preset3;` | Vous donne un rendu plus dramatique sans code supplémentaire. |
| **Pas de preset – ombre personnalisée** | Omit `Format` and set `OffsetX`, `OffsetY` manually. | Contrôle total sur la direction et la profondeur. |
| **Formes multiples** | Call `builder.InsertShape` again before saving. | Utile pour des modèles complexes avec icônes, logos, etc. |
| **Compatibilité avec les versions plus anciennes d’Aspose** | Use `ShadowEffect` class (available in v20.x). | Assure que votre code fonctionne sur des projets hérités. |
| **Enregistrement en PDF** | `document.Save("ShadowShape.pdf");` | Le même rendu d’ombre apparaît dans la sortie PDF. |

> **Question fréquente :** *Et si l’ombre n’apparaît pas dans Word ?*  
> Assurez‑vous d’utiliser une version récente d’Aspose.Words (≥ 22.9). Les versions antérieures avaient un support d’ombre limité. Vérifiez également que le document est ouvert avec une version récente de Word (2016+).

## Exemple complet fonctionnel

Voici le programme complet, prêt à copier‑coller. Il inclut toutes les directives `using`, les commentaires et la gestion des erreurs pour une expérience fluide.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShadowShapeDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document and a builder
                Document doc = new Document();
                DocumentBuilder builder = new DocumentBuilder(doc);

                // 2️⃣ Insert a rectangle (200 pt × 100 pt) and fill it
                Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
                rect.FillColor = Color.LightBlue;

                // 3️⃣ Apply a preset shadow and tweak its properties
                rect.Shadow.Format = ShadowFormat.Preset1;   // predefined style
                rect.Shadow.Distance = 5;                    // set shadow distance
                rect.Shadow.BlurRadius = 3;                  // soften edges
                rect.Shadow.Transparency = 0.4;              // semi‑transparent
                rect.Shadow.Color = Color.Gray;              // shadow color

                // 4️⃣ Save the document
                string outPath = @"C:\Temp\ShadowShape.docx";
                doc.Save(outPath);

                Console.WriteLine($"✅ Document created successfully at {outPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"❌ Error: {ex.Message}");
            }
        }
    }
}
```

Exécutez le programme, accédez à `C:\Temp\ShadowShape.docx`, et vous verrez le rectangle avec l’ombre exacte que nous avons configurée.

## Récapitulatif & prochaines étapes

- Vous savez maintenant comment **create word document c#**, insérer un rectangle, et **apply shadow to shape** avec une **set shadow distance** personnalisée.  
- L’exemple utilise Aspose.Words, qui abstrait les complexités d’OpenXML et garantit un rendu cohérent sur toutes les versions de Word.  
- Vous voulez aller plus loin ? Essayez de combiner plusieurs formes, d’ajouter du texte à l’intérieur du rectangle, ou d’exporter le même document en PDF pour voir comment l’ombre se traduit.

### Sujets connexes que vous pourriez explorer

- **How to add shape** à un en‑tête/pied de page pour le branding.  
- Utiliser **Aspose.Words** pour insérer des graphiques et des tableaux programmatique.  
- Personnaliser les **shadow effects** sur des images au lieu de formes vectorielles.  
- Automatiser la génération massive de documents pour factures ou certificats.

N’hésitez pas à expérimenter, casser le code, puis le reconstruire – c’est la façon la plus rapide d’assimiler les concepts. Si vous rencontrez un problème, laissez un commentaire ci‑dessous ou consultez la documentation officielle d’Aspose.Words pour des informations API plus approfondies.

Bon codage, et profitez de rendre vos fichiers Word un peu plus soignés !

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}