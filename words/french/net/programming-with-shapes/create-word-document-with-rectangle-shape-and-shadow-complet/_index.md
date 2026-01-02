---
category: general
date: 2026-01-02
description: Créez un document Word avec une forme rectangulaire, définissez la couleur
  de remplissage de la forme et enregistrez le fichier docx à l’aide d’Aspose.Words.
  Apprenez à créer un rectangle avec ombre en quelques minutes.
draft: false
keywords:
- create word document
- add rectangle shape
- set shape fill color
- save docx file
- how to create rectangle
language: fr
og_description: Créer un document Word avec un rectangle personnalisé, définir sa
  couleur de remplissage, ajouter une ombre et l’enregistrer au format DOCX. Code
  complet et explications.
og_title: Créer un document Word avec une forme rectangulaire – Étape par étape
tags:
- Aspose.Words
- C#
- Document Generation
title: Créer un document Word avec une forme rectangulaire et une ombre – Guide complet
url: /fr/net/programming-with-shapes/create-word-document-with-rectangle-shape-and-shadow-complet/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un document Word avec une forme rectangulaire et une ombre – Guide complet

Vous vous êtes déjà demandé comment **créer un document Word** contenant un rectangle joliment stylisé ? Peut-être avez‑vous besoin d’un espace réservé pour un logo, d’une bannière colorée, ou simplement d’un repère visuel dans un rapport. Dans ce tutoriel, nous allons **ajouter une forme rectangulaire**, lui appliquer une couleur de remplissage, ajouter une ombre subtile, puis **enregistrer le fichier docx** – le tout avec Aspose.Words pour .NET.

Vous repartirez avec un extrait C# prêt à l’exécution, une explication claire de chaque ligne, et une poignée de conseils que vous pourrez réutiliser dans vos propres projets. Pas de fioritures, juste une solution pratique que vous pouvez copier‑coller.

## Ce dont vous avez besoin

- .NET 6 ou ultérieur (le code fonctionne également sur .NET Framework)  
- Visual Studio 2022 (ou tout éditeur de votre choix)  
- Package NuGet **Aspose.Words** (`Install-Package Aspose.Words`)  

Si vous avez déjà tout cela, super – plongeons‑nous dedans.

## Étape 1 – Initialiser un nouveau document (Comment créer un document Word)

La première chose à faire est de **créer un document Word** en mémoire. Considérez cela comme l’ouverture d’une toile vierge où vous dessinerez plus tard votre rectangle.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // for Color struct

// Create a fresh, empty document
Document document = new Document();

// DocumentBuilder helps us add content step‑by‑step
DocumentBuilder builder = new DocumentBuilder(document);

// Write a simple heading so you can see something when you open the file
builder.Writeln("Shadow Demo");
```

> **Pourquoi c’est important :** `Document` représente l’ensemble du fichier DOCX, tandis que `DocumentBuilder` est un assistant pratique qui vous permet d’insérer du texte, des tableaux, des images et des formes sans gérer manuellement l’arbre de nœuds sous‑jacent.

## Étape 2 – Insérer une forme rectangulaire (Ajouter une forme rectangulaire)

Nous allons maintenant **ajouter une forme rectangulaire** au document. La méthode `InsertShape` prend le type de forme et ses dimensions en points (1 point = 1/72 pouce).

```csharp
// Insert a rectangle that will later receive a custom shadow
Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);

// Give the rectangle a light‑blue background so it stands out
rect.FillColor = Color.LightBlue;
```

> **Astuce :** Si vous avez besoin de créer une géométrie différente (ellipse, triangle, etc.), il suffit de remplacer `ShapeType.Rectangle` par la valeur d’énumération souhaitée.

## Étape 3 – Configurer l’ombre (Définir la couleur de remplissage et l’ombre de la forme)

Une ombre peut donner à une forme plate une impression plus tridimensionnelle. Ici, nous activons l’ombre et ajustons son apparence.

```csharp
// Turn the shadow on
rect.ShadowFormat.Enabled = true;

// Choose a subtle gray for the shadow color
rect.ShadowFormat.Color = Color.Gray;

// Blur softens the edge of the shadow – 8 points looks nice
rect.ShadowFormat.BlurRadius = 8;

// Distance controls how far the shadow is offset from the shape
rect.ShadowFormat.Distance = 5;

// Angle determines the direction; 45° gives a bottom‑right offset
rect.ShadowFormat.Angle = 45;

// Transparency makes the shadow partially see‑through (0 = opaque, 1 = invisible)
rect.ShadowFormat.Transparency = 0.3; // 30 % transparent
```

> **Pourquoi ces valeurs ?** Un rayon de flou modeste et une distance de 5 points empêchent l’ombre de dominer la forme, tandis que 45° imite une source de lumière provenant du haut‑gauche – une convention UI courante.

## Étape 4 – Enregistrer le document (Enregistrer le fichier docx)

Enfin, nous **enregistrons le fichier docx** sur le disque. Ajustez le chemin en fonction de votre environnement.

```csharp
// Replace with the folder you actually want to use
string outputPath = @"C:\Temp\ShadowDemo.docx";

// Persist the document as a .docx file
document.Save(outputPath);
```

Lorsque vous ouvrez `ShadowDemo.docx` dans Word, vous devriez voir un rectangle bleu clair avec une ombre grisâtre douce, exactement comme la capture d’écran ci‑dessous.

![Create Word Document with rectangle shape and shadow](https://example.com/images/rectangle-shadow.png "Create Word Document with rectangle shape and shadow")

*Texte alternatif de l’image :* **Créer un document Word** montrant une forme rectangulaire avec une ombre.

## Exemple complet, prêt à l’exécution (Comment créer un rectangle et enregistrer)

En réunissant tous les éléments, voici le programme complet que vous pouvez copier dans une application console :

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace AsposeRectangleDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 1: Initialize the document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);
            builder.Writeln("Shadow Demo");

            // Step 2: Insert the rectangle
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
            rect.FillColor = Color.LightBlue;   // set shape fill color

            // Step 3: Apply shadow formatting
            rect.ShadowFormat.Enabled = true;
            rect.ShadowFormat.Color = Color.Gray;
            rect.ShadowFormat.BlurRadius = 8;
            rect.ShadowFormat.Distance = 5;
            rect.ShadowFormat.Angle = 45;
            rect.ShadowFormat.Transparency = 0.3;

            // Step 4: Save the file
            string output = @"C:\Temp\ShadowDemo.docx";
            doc.Save(output);

            System.Console.WriteLine($"Document saved to {output}");
        }
    }
}
```

### Résultat attendu

- Un fichier nommé **ShadowDemo.docx** apparaît dans le dossier cible.  
- L’ouvrir dans Microsoft Word affiche une page unique avec le texte « Shadow Demo » suivi d’un rectangle bleu clair.  
- Le rectangle projette une ombre grisâtre douce à un angle de 45°, lui donnant une légère impression 3 D.

## Questions fréquentes et cas particuliers

### Et si j’ai besoin d’une taille différente ?

Il suffit de modifier les arguments `200, 100` dans `InsertShape`. Ces nombres représentent la largeur et la hauteur en points. Pour un carré, utilisez des valeurs identiques.

### Puis‑je rendre l’ombre plus prononcée ?

Augmentez `BlurRadius` pour un bord plus doux, augmentez `Distance` pour un décalage plus important, ou diminuez `Transparency` (par ex., `0.1`) pour la rendre plus sombre.

### Comment ajouter une bordure autour du rectangle ?

```csharp
rect.LineColor = Color.DarkBlue;   // border color
rect.LineWidth = 2;                // thickness in points
```

### Cette méthode est‑elle compatible avec les versions plus anciennes d’Aspose.Words ?

Oui. La classe `ShadowFormat` existe depuis les versions début 2020. Si vous utilisez une version très ancienne, il se peut que vous deviez la mettre à jour pour accéder à toutes les propriétés.

## Conseils et pièges

- **Astuce :** Toujours libérer les gros documents (`doc.Dispose()`) une fois terminé, surtout dans les applications web, afin de libérer les ressources natives.  
- **Attention :** Utiliser un chemin relatif sans les permissions adéquates peut provoquer `UnauthorizedAccessException`. Privilégiez les chemins absolus ou assurez‑vous que le pool d’applications dispose des droits d’écriture.  
- **Rappel :** La propriété `FillColor` accepte n’importe quel `System.Drawing.Color`. N’hésitez pas à utiliser `Color.FromArgb(255, 173, 216, 230)` pour une teinte pastel personnalisée.

## Prochaines étapes

Maintenant que vous savez comment **créer un document Word**, **ajouter une forme rectangulaire**, **définir la couleur de remplissage de la forme**, et **enregistrer le fichier docx**, vous pouvez expérimenter davantage :

- Insérer plusieurs formes et les disposer avec `RelativeHorizontalPosition` et `RelativeVerticalPosition`.  
- Combiner le rectangle avec du texte en utilisant `Shape.TextBox` pour les légendes.  
- Exporter le même document en PDF (`doc.Save("output.pdf")`) pour la distribution.

Si vous êtes curieux des graphiques plus avancés, consultez le support d’Aspose.Words pour **WordArt**, **charts**, et **inline images**. Chaque fonctionnalité suit le même schéma : créer un nœud, configurer ses propriétés, puis enregistrer.

---

### TL;DR

- Utilisez `Document` et `DocumentBuilder` pour **créer un document Word**.  
- Appelez `InsertShape(ShapeType.Rectangle, …)` pour **ajouter une forme rectangulaire**.  
- Définissez `FillColor` pour le fond souhaité.  
- Activez `ShadowFormat` et ajustez ses propriétés pour un rendu soigné.  
- Terminez avec `document.Save("yourPath.docx")` pour **enregistrer le fichier docx**.

Bon codage, et amusez‑vous à rendre vos fichiers Word un peu plus stylés !

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}