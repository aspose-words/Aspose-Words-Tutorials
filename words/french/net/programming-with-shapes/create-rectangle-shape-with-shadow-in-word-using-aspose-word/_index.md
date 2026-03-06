---
category: general
date: 2026-03-06
description: Créer une forme rectangulaire dans Word et ajouter une ombre à la forme
  avec Aspose.Words. Apprenez comment insérer un rectangle dans Word et comment ajouter
  une ombre à la forme en C#.
draft: false
keywords:
- create rectangle shape
- add shape shadow
- how to insert rectangle in word
- how to add shadow to shape
language: fr
og_description: Créer une forme rectangulaire dans Word et ajouter une ombre à la
  forme avec Aspose.Words. Guide étape par étape sur la façon d’insérer un rectangle
  dans Word et d’ajouter une ombre à la forme.
og_title: Créer une forme rectangulaire avec ombre dans Word à l'aide d'Aspose.Words
tags:
- Aspose.Words
- C#
- Word Automation
title: Créer une forme rectangulaire avec ombre dans Word à l'aide d'Aspose.Words
url: /fr/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-word-using-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer une forme rectangulaire avec ombre dans Word avec Aspose.Words

Vous avez déjà eu besoin de **créer une forme rectangulaire** dans un document Word mais vous ne saviez pas comment lui donner cet aspect soigné ? Vous n’êtes pas seul — la plupart des développeurs rencontrent le même problème lorsqu’ils essaient d’ajouter du style visuel à des documents générés automatiquement. Bonne nouvelle : avec Aspose.Words for .NET, vous pouvez à la fois **créer une forme rectangulaire** et **ajouter une ombre à la forme** en quelques lignes de C#.

Dans ce tutoriel, nous allons voir **comment insérer un rectangle dans Word**, puis **comment ajouter une ombre à la forme** pour qu’elle ressorte de la page. À la fin, vous disposerez d’un fichier `Shadow.docx` prêt à être ouvert dans Word, affichant un rectangle grisâtre avec une douce ombre portée. Aucun fichier image supplémentaire, aucune retouche manuelle — juste du code.

## Ce que vous allez apprendre

- Les instructions C# exactes nécessaires pour **créer une forme rectangulaire** avec Aspose.Words.  
- Comment activer et configurer une ombre à l’aide de l’objet `Shadow`.  
- Pourquoi chaque propriété est importante (par ex., `Transparency`, `Blur`, `Angle`).  
- Les pièges courants (unités, compatibilité de version) et leurs solutions rapides.  
- Un programme complet, prêt à copier‑coller, que vous pouvez exécuter dès aujourd’hui.

### Prérequis

- .NET 6+ (ou .NET Framework 4.7+).  
- Aspose.Words for .NET 23.10 ou ultérieur (le package NuGet est `Aspose.Words`).  
- Une compréhension de base du C# et de Visual Studio (ou tout autre IDE de votre choix).  

Si vous avez déjà tout cela, passons directement à l’action.

---

## Étape 1 : Configurer le projet et importer les espaces de noms

Tout d’abord, créez une nouvelle application console (ou réutilisez-en une existante) et ajoutez le package NuGet Aspose.Words :

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Ensuite, importez les espaces de noms requis dans votre `Program.cs` :

```csharp
using System.Drawing;               // For Color
using Aspose.Words;                  // Core document classes
using Aspose.Words.Drawing;          // Shape and Shadow types
```

> **Astuce :** Si vous ciblez .NET 6+, vous pouvez activer les directives `using` globales pour éviter de répéter ces lignes dans chaque fichier.

---

## Étape 2 : **Créer une forme rectangulaire** dans un document Word vierge

Nous allons commencer avec un objet `Document` vierge et un `DocumentBuilder` pour le manipuler. La méthode `InsertShape` du builder est là où la magie opère.

```csharp
// Step 2: Initialize a new document and builder
Document document = new Document();                     // Blank Word file
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle – 200 × 100 points (≈2.78 × 1.39 inches)
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

Pourquoi 200 × 100 points ? Dans Word, un point vaut 1/72 de pouce, donc le rectangle mesure environ 2,8 × 1,4 pouces — assez grand pour être remarqué sans être envahissant. Vous pouvez modifier ces valeurs selon votre mise en page ; rappelez‑vous simplement qu’elles sont exprimées en **points**, pas en pixels.

---

## Étape 3 : **Ajouter une ombre à la forme** – configuration de l’apparence

Maintenant que nous avons un rectangle, ajoutons‑lui une subtile ombre grise. L’objet `Shadow` appartient à la `Shape` et expose plusieurs propriétés pratiques.

```csharp
// Step 3: Turn on the shadow and tweak its appearance
rectangle.Shadow.Enabled = true;               // Switch the shadow on
rectangle.Shadow.Color = Color.Gray;           // Shadow hue
rectangle.Shadow.Transparency = 0.3;           // 30 % transparent – looks softer
rectangle.Shadow.Blur = 5;                     // Blur radius (points)
rectangle.Shadow.Distance = 4;                 // How far the shadow sits from the shape
rectangle.Shadow.Angle = 45;                   // Direction in degrees (45° = down‑right)
rectangle.Shadow.Size = 100;                   // 100 % of the original shape size
```

### Ce que fait chaque propriété

| Propriété | Effet | Valeurs typiques |
|-----------|-------|------------------|
| **Enabled** | Active ou désactive l’ombre | `true` ou `false` |
| **Color** | Couleur de base de l’ombre | Tout `System.Drawing.Color` |
| **Transparency** | Opacité (0 = opaque, 1 = transparent) | 0.0 – 1.0 |
| **Blur** | Douceur du bord | 0 – 10 (plus élevé = plus doux) |
| **Distance** | Écart entre la forme et l’ombre | 0 – 20 points |
| **Angle** | Direction de la source de lumière | 0 – 360 degrés |
| **Size** | Échelle de l’ombre par rapport à la forme | 0 – 200 % |

> **Pourquoi ces réglages ?**  
> Ajuster finement l’ombre vous permet de respecter les chartes graphiques de l’entreprise (par ex., une transparence de 20 % pour un rendu professionnel) sans recourir à des éditeurs d’images externes.

---

## Étape 4 : Enregistrer le document et vérifier le résultat

Enfin, écrivez le fichier sur le disque. Vous pouvez choisir n’importe quel dossier ; remplacez simplement `YOUR_DIRECTORY` par un chemin réel.

```csharp
// Step 4: Persist the document
string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Ouvrez `Shadow.docx` dans Microsoft Word et vous devriez voir un rectangle gris avec une douce ombre portée décalée à 45° . Cette indication visuelle donne l’impression que la forme est « levée » de la page — exactement ce que l’on attend d’un rapport ou d’une facture bien présentés.

---

## Exemple complet fonctionnel

Voici le programme complet que vous pouvez copier‑coller dans `Program.cs`. Aucun morceau ne manque ; il compile et s’exécute tel quel.

```csharp
using System;
using System.Drawing;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape (200 × 100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // 3️⃣ Enable the shape's shadow and configure its appearance
        rectangle.Shadow.Enabled = true;               // Turn the shadow on
        rectangle.Shadow.Color = Color.Gray;           // Shadow colour
        rectangle.Shadow.Transparency = 0.3;           // 30 % transparent
        rectangle.Shadow.Blur = 5;                     // Blur radius
        rectangle.Shadow.Distance = 4;                 // Offset from the shape
        rectangle.Shadow.Angle = 45;                   // Direction in degrees
        rectangle.Shadow.Size = 100;                   // Shadow size as a percentage

        // 4️⃣ Save the document with the shadowed shape
        string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### Résultat attendu

- **Fichier :** `Shadow.docx` placé dans le répertoire d’exécution du projet.  
- **Visuel :** Un seul rectangle centré sur la page, rempli de blanc par défaut, avec une ombre grise décalée de 4 points vers le bas‑droite, légèrement floutée pour un rendu naturel.

---

## Questions fréquentes & cas particuliers

### 1. Et si j’ai besoin d’une autre unité (par ex., centimètres) ?

Aspose.Words travaille en points, mais vous pouvez convertir les centimètres en points avec la formule simple :  
`points = centimeters * 28.3465`.  

```csharp
double cmWidth = 5.0; // 5 cm
double cmHeight = 2.5; // 2.5 cm
Shape rectCm = builder.InsertShape(ShapeType.Rectangle,
                                   (float)(cmWidth * 28.3465),
                                   (float)(cmHeight * 28.3465));
```

### 2. Cette fonctionnalité fonctionne‑t‑elle avec les versions plus anciennes d’Aspose.Words ?

L’API `Shadow` a été introduite dans la version 14.0. Si vous utilisez une version antérieure, vous devrez mettre à jour via NuGet. Le reste du code (création de formes) est stable depuis de nombreuses années, vous ne rencontrerez donc pas de changements majeurs.

### 3. Puis‑je ajouter une ombre à d’autres formes (par ex., des cercles) ?

Absolument — tout objet `Shape` expose une propriété `Shadow`. Remplacez simplement `ShapeType.Rectangle` par `ShapeType.Ellipse` ou `ShapeType.Cloud`, puis appliquez les mêmes paramètres d’ombre.

### 4. Et si je veux une ombre colorée (par ex., bleue pour une marque) ?

Remplacez `Color.Gray` par la couleur désirée :

```csharp
rectangle.Shadow.Color = Color.FromArgb(30, 0, 120); // Dark blue
```

N’oubliez pas d’ajuster `Transparency` afin que la couleur ne devienne pas trop dominante.

---

## 🎨 Résumé visuel

![create rectangle shape with shadow in Word using Aspose.Words](image-placeholder.png "create rectangle shape with shadow in Word using Aspose.Words")

*Texte alternatif : créer une forme rectangulaire avec ombre dans Word avec Aspose.Words*

La capture d’écran (espace réservé) montre le document final — seulement le rectangle et son ombre grise douce.

---

## Conclusion

Vous savez maintenant comment **créer une forme rectangulaire** dans un fichier Word, **ajouter une ombre à la forme**, et affiner chaque aspect visuel à l’aide d’Aspose.Words for .NET. Le petit programme que nous avons construit couvre l’ensemble du flux de travail — de

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}