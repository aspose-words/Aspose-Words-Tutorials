---
category: general
date: 2026-01-13
description: Créer un document Word avec Aspose.Words et apprendre comment insérer
  une forme rectangulaire, comment ajouter une ombre et ajouter l’ombre de la forme
  en C#. Exemple complet inclus.
draft: false
keywords:
- create word document
- insert rectangle shape
- how to add shadow
- how to insert shape
- add shape shadow
language: fr
og_description: Créer un document Word avec Aspose.Words, voir comment insérer une
  forme rectangulaire et comment ajouter une ombre. Suivez l'exemple complet en C#.
og_title: Créer un document Word avec un rectangle ombré – Tutoriel complet
tags:
- Aspose.Words
- C#
- Document Automation
title: Créer un document Word avec un rectangle ombré – Guide étape par étape
url: /fr/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un document Word avec un rectangle ombré – Guide étape par étape

Vous avez déjà eu besoin de **créer un document Word** contenant un rectangle joliment ombré, mais vous ne saviez pas par où commencer ? Vous n'êtes pas le seul—de nombreux développeurs rencontrent le même obstacle lorsqu'ils commencent à utiliser Aspose.Words.  

Dans ce tutoriel, nous passerons en revue tout ce dont vous avez besoin pour **créer un document Word** de façon programmatique, **insérer une forme rectangle**, et montrer **comment ajouter une ombre** afin que la forme ressorte vraiment. À la fin, vous disposerez d'un extrait C# prêt à l'emploi que vous pourrez intégrer dans n'importe quel projet .NET.

## Ce que vous apprendrez

- Le code exact pour **comment insérer une forme** (un rectangle) dans un fichier Word.
- Les propriétés que vous devez ajuster pour **ajouter une ombre à la forme** et contrôler son apparence.
- Comment enregistrer le résultat et vérifier que l'ombre est visible.
- Quelques conseils pratiques et notes sur les cas limites qui vous éviteront des maux de tête plus tard.

Aucune documentation externe requise—tout se trouve ici.

## Prérequis

Avant de commencer, assurez-vous d'avoir :

1. **.NET 6.0** (ou toute version récente de .NET) installé.  
2. Une **licence** pour Aspose.Words for .NET, ou vous pouvez utiliser le mode d'évaluation gratuit pour les tests.  
3. Un environnement de développement—Visual Studio 2022 fonctionne très bien, mais tout éditeur capable de compiler du C# convient.

C'est tout. Aucun package NuGet supplémentaire au-delà de `Aspose.Words` n'est nécessaire.

## Étape 1 – Configurer le projet et référencer Aspose.Words

Tout d'abord, créez une nouvelle application console et ajoutez le package Aspose.Words :

```bash
dotnet new console -n ShadowRectangleDemo
cd ShadowRectangleDemo
dotnet add package Aspose.Words
```

> **Astuce :** Si vous utilisez la version d'essai gratuite, n'oubliez pas d'appeler `License.SetLicense` avec votre fichier de licence ; sinon la bibliothèque ajoutera un filigrane.

## Étape 2 – Initialiser le DocumentBuilder

Nous allons maintenant démarrer le processus réel de **création d'un document Word**. La classe `Document` nous fournit une toile vierge, et `DocumentBuilder` nous permet d'y dessiner.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing; // For Color

// Initialise a new blank document
Document document = new Document();

// Initialise a builder to start adding content
DocumentBuilder builder = new DocumentBuilder(document);
```

Pourquoi avons‑nous besoin d'un builder ? Il masque les détails bas‑niveau d'OpenXML, vous permettant de vous concentrer sur *ce que* vous voulez plutôt que sur *comment* le fichier est structuré. C'est le cœur de **comment insérer une forme** rapidement.

## Étape 3 – Insérer une forme rectangle

C'est ici que nous **insérons la forme rectangle**. Le rectangle mesurera 150 × 100 points (environ 2 po × 1,3 po).

```csharp
// Insert a rectangle shape at the current cursor position
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 100);
```

La méthode `InsertShape` renvoie un objet `Shape`, que nous pouvons personnaliser davantage. À ce stade, le rectangle n'est qu'une boîte blanche solide—sans ombre pour l'instant.

## Étape 4 – Comment ajouter une ombre (Ajouter une ombre à la forme)

Ajouter une ombre est étonnamment simple une fois que vous savez quelles propriétés modifier. L'objet `ShadowFormat` contrôle la visibilité, la couleur, le flou, le décalage et la taille.

```csharp
// Make the shadow visible
rectangleShape.ShadowFormat.Visible = true;

// Choose a subtle gray tone
rectangleShape.ShadowFormat.Color = Color.Gray;

// Set 30 % transparency – the shadow will be faint but noticeable
rectangleShape.ShadowFormat.Transparency = 0.3;

// Offset the shadow 5 points right and 5 points down
rectangleShape.ShadowFormat.OffsetX = 5;
rectangleShape.ShadowFormat.OffsetY = 5;

// Soften the edges with a blur radius of 4 points
rectangleShape.ShadowFormat.BlurRadius = 4;

// Scale the shadow to 75 % of the shape size (percentage)
rectangleShape.ShadowFormat.Size = 75;
```

Ce bloc répond à **comment ajouter une ombre** en termes simples : l'activer, choisir une couleur, ajuster la transparence, le décalage, le flou et la taille. Vous pouvez expérimenter avec ces valeurs pour obtenir une ombre portée lourde ou une ombre très fine.

### Variations courantes

- **Couleurs différentes :** Utilisez `Color.Black` pour une ombre portée classique, ou `Color.BlueViolet` pour un effet stylisé.  
- **Aucun flou :** Définissez `BlurRadius = 0` pour un bord net et précis.  
- **Décalages plus grands :** Augmentez `OffsetX`/`OffsetY` pour éloigner davantage l'ombre de la forme.

## Étape 5 – Enregistrer le document et vérifier

Enfin, écrivez le document sur le disque. Le fichier sera un `.docx` standard que tout traitement de texte moderne pourra ouvrir.

```csharp
// Save the document to the desired folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowRectangle.docx");
document.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Ouvrez le *ShadowRectangle.docx* résultant dans Microsoft Word. Vous devriez voir un rectangle avec une ombre grise douce décalée vers le bas‑à‑droite—exactement ce que le code spécifie.

> **Résultat attendu :** Un fichier Word d'une seule page contenant un rectangle de 150 × 100 points avec une ombre grise à 30 % de transparence, décalée de 5 pts, floutée de 4 pts, et dimensionnée à 75 % de la forme.

## Exemple complet fonctionnel

En réunissant tous les éléments, voici le programme complet, prêt à être exécuté :

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialise a new blank document
        Document document = new Document();

        // 2️⃣ Create a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Insert a rectangle shape (150 × 100 points)
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 100);

        // 4️⃣ How to add shadow – configure the ShadowFormat
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = Color.Gray;
        rectangleShape.ShadowFormat.Transparency = 0.3; // 30 % transparent
        rectangleShape.ShadowFormat.OffsetX = 5;        // horizontal offset
        rectangleShape.ShadowFormat.OffsetY = 5;        // vertical offset
        rectangleShape.ShadowFormat.BlurRadius = 4;    // softer edge
        rectangleShape.ShadowFormat.Size = 75;         // size as a percentage

        // 5️⃣ Save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowRectangle.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Exécutez le programme (`dotnet run`) et vous obtiendrez un nouveau fichier Word avec un rectangle joliment ombré—parfait pour les rapports, certificats ou tout indice visuel dont vous avez besoin.

## Questions fréquentes (FAQ)

**Q : Puis‑je insérer d'autres formes (ellipse, étoile) et utiliser le même code d'ombre ?**  
R : Absolument. La méthode `InsertShape` accepte n'importe quelle valeur de l'énumération `ShapeType`. Une fois que vous avez une instance de `Shape`, les propriétés `ShadowFormat` fonctionnent de la même façon, donc **comment ajouter une ombre** est indépendant de la forme.

**Q : Et si j'ai besoin de l'ombre des deux côtés de la forme ?**  
R : Aspose.Words ne prend en charge qu'une seule ombre portée par forme. Pour simuler un effet à double côté, dupliquez la forme, décalez chaque copie différemment, et définissez `ShadowFormat.Visible` à `false` pour l'une tout en conservant l'ombre visible pour l'autre.

**Q : Cette méthode fonctionne‑t‑elle sur .NET Framework 4.8 ?**  
R : Oui. L'API est indépendante de la version ; il suffit de référencer le DLL Aspose.Words approprié pour votre framework cible.

## Astuces & pièges

- **N’oubliez pas de définir `Visible = true`**—les propriétés d'ombre sont ignorées sinon.  
- **Les valeurs de transparence vont de 0,0 (opaque) à 1,0 (complètement transparent).** Une erreur fréquente consiste à utiliser `30` au lieu de `0.3`.  
- **Enregistrer dans un dossier en lecture‑seule génère une exception.** Assurez‑vous que le répertoire de sortie est accessible en écriture.

## Prochaines étapes

Maintenant que vous savez **comment insérer une forme**, **ajouter une ombre à la forme**, et **créer un document Word** avec Aspose.Words, vous pourriez vouloir explorer :

- Ajouter du **texte à l'intérieur du rectangle** en utilisant `builder.InsertParagraph()` avant d'insérer la forme.  
- Appliquer des **remplissages en dégradé** ou des **bordures à motifs** pour un style visuel plus riche.  
- Automatiser la génération de plusieurs pages, chacune avec une forme ombrée différente, afin de créer des rapports dynamiques.

N'hésitez pas à expérimenter—modifier la couleur, le flou ou la taille de l'ombre peut transformer radicalement l'apparence de votre document.

---

*Prêt à mettre cela en production ? Prenez le code, ajustez les paramètres, et voyez vos fichiers Word gagner un fini professionnel en quelques secondes.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}