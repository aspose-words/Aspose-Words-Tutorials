---
category: general
date: 2026-01-03
description: Créer une forme rectangulaire dans Word avec C# et ajouter une ombre
  à la forme. Apprenez comment insérer une forme dans Word, ajouter une ombre à la
  forme et générer des documents Word de manière programmatique.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- insert shape in word
- how to add shape
- c# generate word document
language: fr
og_description: Créer une forme rectangulaire dans Word avec C# et ajouter une ombre
  à la forme. Suivez ce guide pour insérer une forme dans Word, configurer les ombres
  et générer des documents de manière programmatique.
og_title: Créer une forme rectangulaire dans Word avec C# – Tutoriel complet
tags:
- C#
- Word Automation
- Aspose.Words
title: Créer une forme rectangulaire dans Word avec C# – Guide étape par étape
url: /fr/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer une forme rectangulaire dans Word avec C# – Tutoriel complet

Vous avez déjà eu besoin de **create rectangle shape** dans un document Word mais vous ne saviez pas par où commencer ? Vous n'êtes pas seul—de nombreux développeurs rencontrent le même problème lorsqu'ils souhaitent **add shadow to shape** pour obtenir un rendu soigné. Dans ce tutoriel, nous passerons en revue les étapes exactes pour **insert shape in Word**, appliquer une ombre subtile, et enfin **c# generate word document** que vous pourrez distribuer aux utilisateurs.

Nous couvrirons tout, de la configuration du projet à l'ajustement des propriétés d'ombre, et nous terminerons avec un exemple de code prêt à l'exécution. Pas de superflu, seulement les éléments pratiques qui font le travail.

## Ce que vous apprendrez

- Comment **create rectangle shape** avec Aspose.Words (ou Open XML) en C#
- Les propriétés exactes dont vous avez besoin pour **add shadow to shape** afin d'ajouter de la profondeur
- Où placer la forme en utilisant `DocumentBuilder`
- Comment enregistrer le fichier afin qu'il s'ouvre correctement dans Microsoft Word
- Conseils, pièges et variantes pour des scénarios réels

### Prérequis

- .NET 6.0 ou ultérieur (le code fonctionne sur .NET Core et .NET Framework)  
- Un package NuGet capable de manipuler des fichiers Word – nous utiliserons **Aspose.Words for .NET** car son API est concise. Si vous préférez Open XML SDK, les concepts sont les mêmes, seules les classes diffèrent.  
- Visual Studio, VS Code, ou tout IDE C# de votre choix  

> **Astuce :** Si vous avez un budget limité, Aspose propose un essai gratuit idéal pour l'apprentissage. Remplacez simplement la ligne de licence par un commentaire lors de vos tests.

## Étape 1 : Installer la bibliothèque de traitement Word

Tout d'abord, ajoutez la bibliothèque à votre projet. Ouvrez un terminal dans le dossier de votre solution et exécutez :

```bash
dotnet add package Aspose.Words
```

Si vous utilisez le SDK Open XML, la commande serait `dotnet add package DocumentFormat.OpenXml`. Le reste de ce guide part du principe que vous utilisez Aspose.Words, mais remplacer les appels d'API est simple.

## Étape 2 : Créer un nouveau document vierge

Maintenant que la bibliothèque est prête, nous pouvons **create rectangle shape** en commençant avec un objet `Document` vierge. Considérez cela comme une toile neuve.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 2: Initialize a blank Word document
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);
```

`DocumentBuilder` nous offre une méthode de haut niveau pour insérer du contenu sans plonger dans les arbres de nœuds de bas niveau.

## Étape 3 : Insérer la forme rectangulaire

Avec le builder en main, nous pouvons **insert shape in Word**. La méthode `InsertShape` prend le type de forme et ses dimensions (largeur, hauteur) en points.

```csharp
// Step 3: Insert a rectangle shape – 150pt wide, 80pt high
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

À ce stade, le rectangle apparaît dans le document, mais il semble un peu plat. C'est là que l'étape suivante intervient.

## Étape 4 : Ajouter une ombre à la forme

Les ombres donnent à la forme une impression de profondeur. L'objet `Shadow` nous permet d'ajuster finement le flou, la distance, l'angle, la couleur et la transparence. Ci-dessous une configuration complète qui fonctionne bien pour la plupart des rapports.

```csharp
// Step 4: Configure a subtle shadow
rectangle.Shadow = new Shadow
{
    BlurRadius = 5.0,          // Soft edges
    Distance = 4.0,            // How far the shadow is offset
    Angle = 45,                // Direction in degrees (45° = down‑right)
    Color = Color.Black,       // Shadow color
    Transparency = 0.3         // 30 % transparent for a gentle look
};
```

**Pourquoi ces valeurs ?**  
- **BlurRadius** de `5.0` garde le bord lisse sans paraître flou.  
- **Distance** de `4.0` décale l'ombre juste assez pour être perceptible.  
- **Angle** `45` imite un éclairage naturel depuis le haut‑gauche, une convention UI courante.  
- **Transparency** `0.3` empêche l'ombre de dominer le remplissage de la forme.

Si vous avez besoin d'un effet plus dramatique, augmentez `BlurRadius` et diminuez `Transparency`. Pour un soulèvement subtil, presque invisible, inversez ces valeurs.

## Étape 5 : Enregistrer le document

Enfin, écrivez le fichier sur le disque. La méthode `Save` détecte le format à partir de l'extension du fichier, ainsi `.docx` vous donne le format Word moderne.

```csharp
// Step 5: Persist the document
string outputPath = @"C:\Temp\ShadowRectangle.docx";
document.Save(outputPath);
```

Ouvrez `ShadowRectangle.docx` dans Microsoft Word, et vous verrez un rectangle net avec une ombre douce—exactement ce que vous vouliez lorsque vous avez demandé “**how to add shape**” avec une finition professionnelle.

![Créer une forme rectangulaire avec ombre dans Word](placeholder-image.png "Créer une forme rectangulaire avec ombre dans Word")

*Texte alternatif de l'image : créer une forme rectangulaire avec ombre dans Word*

## Exemple complet fonctionnel

En réunissant tous les éléments, voici le programme complet, prêt à l'exécution. Copiez‑collez-le dans une application console et appuyez sur **F5**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a new blank document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a rectangle shape (150pt × 80pt)
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Add a subtle shadow
            rect.Shadow = new Shadow
            {
                BlurRadius = 5.0,
                Distance = 4.0,
                Angle = 45,
                Color = Color.Black,
                Transparency = 0.3
            };

            // 4️⃣ Save the file
            string filePath = @"C:\Temp\ShadowRectangle.docx";
            doc.Save(filePath);

            System.Console.WriteLine($"Document saved to {filePath}");
        }
    }
}
```

### Résultat attendu

- Le `ShadowRectangle.docx` généré contient **une forme rectangulaire** centrée à l'endroit où le curseur était positionné.  
- Le rectangle affiche une **ombre noire douce, 30 % transparente**, décalée à un angle de 45°.  
- Aucun autre contenu n'est ajouté, gardant le fichier léger et facile à intégrer dans des rapports plus volumineux.

## Questions fréquentes & cas particuliers

### Et si j’ai besoin d’une forme différente ?

Remplacez `ShapeType.Rectangle` par n'importe quelle autre valeur de l'énumération `ShapeType` (par ex., `Ellipse`, `Triangle`). L'API d'ombre fonctionne de la même manière, vous pouvez donc réutiliser la configuration.

### Comment changer la couleur de remplissage ?

```csharp
rect.FillColor = Color.LightBlue;   // or any System.Drawing.Color
```

### Puis-je ajouter la forme à un paragraphe spécifique ?

Oui. Déplacez le `DocumentBuilder` vers le paragraphe cible avec `builder.MoveToParagraph(index)` avant d'appeler `InsertShape`. Cela garantit que la forme apparaît exactement où vous le souhaitez.

### Qu’en est‑il des anciens formats Word (.doc) ?

Just change the extension:

```csharp
doc.Save(@"C:\Temp\ShadowRectangle.doc", SaveFormat.Doc);
```

La fonction d'ombre est prise en charge dans Word 2003 et versions ultérieures, vous verrez donc toujours l'effet.

### Utiliser le SDK Open XML au lieu d'Aspose ?

Les étapes restent les mêmes : créez un `WordprocessingDocument`, ajoutez un élément `Drawing`, définissez les propriétés `<a:shadow>`. Le XML est plus verbeux, mais les mêmes concepts (taille, flou, distance, angle) s'appliquent.

## Conseils pour éviter les pièges

- **N'oubliez pas la licence** si vous utilisez une version payante d'Aspose ; sinon vous obtiendrez un filigrane.  
- **Les unités sont en points**, pas en pixels. Un pixel d'écran typique ≈ 0,75 pt, ajustez donc les dimensions en conséquence.  
- **Les propriétés d'ombre sont ignorées** si le `WrapType` de la forme est défini sur `Inline`. Utilisez `WrapType = WrapType.Square` pour les formes flottantes qui respectent le rendu de l'ombre.  
- **Enregistrer sur un partage réseau** peut nécessiter les autorisations appropriées ; testez toujours le chemin d'abord.

## Conclusion

Vous savez maintenant comment **create rectangle shape** dans un document Word avec C#, **add shadow to shape**, et **c# generate word document** qui ont un aspect soigné dès le départ. Les étapes principales—installer la bibliothèque, instancier `Document`, insérer la forme, configurer l'ombre et enregistrer—sont faciles à retenir et adaptables à d'autres formes, couleurs ou même à des données dynamiques.

Et ensuite ? Essayez de superposer plusieurs formes, d'intégrer des images, ou de générer un rapport complet avec tableaux et graphiques. Vous pouvez également explorer le formatage conditionnel—modifier l'intensité de l'ombre en fonction des valeurs de données—pour rendre vos documents non seulement fonctionnels mais aussi visuellement attractifs.

N'hésitez pas à expérimenter, et si vous rencontrez des problèmes, laissez un commentaire ci‑dessous. Bon codage, et que vos documents Word aient toujours cette ombre portée parfaite !

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}