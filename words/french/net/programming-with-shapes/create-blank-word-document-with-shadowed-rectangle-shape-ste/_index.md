---
category: general
date: 2026-01-08
description: Créer un document Word vierge et apprendre comment ajouter une ombre
  à une forme rectangulaire. Insérer des fichiers Word contenant des formes et ajouter
  une ombre à la forme en C# avec Aspose.Words.
draft: false
keywords:
- create blank word
- how to add shadow
- rectangle shape word
- insert shape word
- add shape shadow
language: fr
og_description: Créer un document Word vierge et voir comment ajouter une ombre à
  une forme rectangulaire en C#. Code complet, explications et astuces.
og_title: Créer un document Word vierge – Ajouter une forme de rectangle ombrée
tags:
- Aspose.Words
- C#
- Document Automation
title: Créer un document Word vierge avec une forme de rectangle ombrée – Guide étape
  par étape
url: /fr/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un document Word vierge avec une forme rectangulaire ombrée – Tutoriel complet

Vous avez déjà eu besoin de **créer des fichiers Word vierges** de façon programmatique puis de les habiller d’un joli rectangle ombré ? Vous n’êtes pas le seul. De nombreux développeurs se heurtent à un mur lorsqu’ils découvrent que l’insertion de formes et l’application d’effets n’est pas aussi simple que de taper du texte.  

Dans ce guide, nous parcourrons l’ensemble du processus — de la création d’un `.docx` vide à **comment ajouter une ombre** à un objet **rectangle shape word**, et enfin **insérer du contenu shape word** avec un effet **add shape shadow** soigné. À la fin, vous disposerez d’un extrait prêt à l’emploi qui fonctionne avec la dernière version d’Aspose.Words pour .NET.

---

## Ce dont vous avez besoin

- **Aspose.Words for .NET** (v24.10 ou plus récent) – la bibliothèque qui alimente tout ce qui suit.  
- Un environnement de développement .NET (Visual Studio, Rider ou le CLI `dotnet`).  
- Connaissances de base en C# – si vous pouvez écrire « Hello World », vous êtes prêt.  

Aucun package NuGet supplémentaire n’est requis ; tout se trouve dans `Aspose.Words` et `System.Drawing`.

## Étape 1 : Créer un document Word vierge

La première chose à faire est d’instancier un objet `Document` vide. Considérez-le comme une toile neuve — tout comme ouvrir manuellement un nouveau fichier Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Initialize a brand‑new blank Word document
Document document = new Document();   // This creates an empty .docx in memory
```

*Pourquoi c’est important :*  
Une instance `Document` représente le fichier Word complet. Commencer avec un document vierge vous donne un contrôle total sur chaque élément que vous ajouterez plus tard, des paragraphes aux formes.

## Étape 2 : Définir une forme rectangulaire (Rectangle Shape Word)

Nous avons maintenant besoin d’une forme avec laquelle travailler. Un rectangle est la géométrie la plus simple et convient bien aux bannières, aux espaces réservés ou aux maquettes UI simples.

```csharp
// Step 2: Create a rectangle shape with specific dimensions
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width  = 200,   // Width in points (≈2.78 inches)
    Height = 100    // Height in points (≈1.39 inches)
};
```

*Pourquoi c’est important :*  
Définir `Width` et `Height` vous permet de contrôler l’empreinte visuelle de la forme. Le `ShapeType.Rectangle` indique à Aspose de rendre une boîte classique — parfait pour démontrer **add shape shadow** plus tard.

## Étape 3 : Appliquer une ombre à la forme (How to Add Shadow)

Les ombres donnent de la profondeur, faisant qu’un rectangle plat ressemble à un objet physique. Aspose.Words expose une propriété `Shadow` où vous pouvez ajuster la couleur, la distance, le flou et la transparence.

```csharp
// Step 3: Enable and configure the shadow effect
rectangleShape.Shadow.Enabled      = true;               // Turn the shadow on
rectangleShape.Shadow.Color        = Color.Gray;         // Shadow color
rectangleShape.Shadow.Distance    = 5.0;                // How far the shadow is offset
rectangleShape.Shadow.BlurRadius  = 3.0;                // Softness of the edge
rectangleShape.Shadow.Transparency = 0.2;               // 0 = opaque, 1 = fully transparent
```

*Pourquoi c’est important :*  
Chaque propriété influence l’indice visuel :

- **Enabled** – sans cela, les autres paramètres sont ignorés.  
- **Color** – choisissez une teinte qui correspond au thème de votre document.  
- **Distance** – des valeurs plus grandes éloignent davantage l’ombre.  
- **BlurRadius** – des nombres plus élevés rendent l’ombre plus douce.  
- **Transparency** – ajustez finement l’opacité pour plus de subtilité.

N’hésitez pas à expérimenter ; pour un effet dramatique, augmentez `Distance` à `10` et réglez `Transparency` à `0.5`.

## Étape 4 : Insérer la forme dans le document (Insert Shape Word)

Avec le rectangle prêt, nous avons besoin d’un endroit où le placer. L’endroit le plus simple est le premier paragraphe du corps du document.

```csharp
// Step 4: Append the shape to the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

*Pourquoi c’est important :*  
`FirstSection.Body.FirstParagraph` est toujours présent dans un nouveau `Document`. En ajoutant la forme ici, vous garantissez que la forme apparaît en haut du fichier — utile pour les en‑têtes ou les bannières de titre.

Si vous devez insérer la forme ailleurs, vous pouvez localiser un `Paragraph` ou `Run` spécifique et utiliser `InsertAfter` ou `InsertBefore`.

## Étape 5 : Enregistrer le fichier Word

L’étape finale consiste à enregistrer le document en mémoire sur le disque. Choisissez un dossier où vous avez les droits d’écriture et donnez au fichier un nom significatif.

```csharp
// Step 5: Save the document with the shadowed rectangle
string outputPath = @"C:\Temp\ShadowedRectangle.docx";
document.Save(outputPath);
```

*Pourquoi c’est important :*  
Appeler `Save` écrit un fichier `.docx` entièrement conforme. Ouvrez-le dans Microsoft Word, LibreOffice ou tout autre visualiseur, et vous verrez un rectangle avec une ombre gris clair — exactement ce que nous avons configuré.

## Exemple complet fonctionnel

Ci-dessous se trouve le programme complet que vous pouvez copier‑coller dans une application console. Il inclut toutes les directives `using`, la création de la forme, la configuration de l’ombre, l’insertion et l’enregistrement.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Define a rectangle shape (rectangle shape word)
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
        {
            Width  = 200,
            Height = 100
        };

        // 3️⃣ How to add shadow – configure the shadow effect
        rectangleShape.Shadow.Enabled      = true;
        rectangleShape.Shadow.Color        = Color.Gray;
        rectangleShape.Shadow.Distance    = 5.0;
        rectangleShape.Shadow.BlurRadius  = 3.0;
        rectangleShape.Shadow.Transparency = 0.2;

        // 4️⃣ Insert shape word into the first paragraph
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // 5️⃣ Save the file (add shape shadow persisted)
        string outputPath = @"C:\Temp\ShadowedRectangle.docx";
        document.Save(outputPath);

        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Sortie attendue :**  
Ouvrez `ShadowedRectangle.docx` et vous verrez un rectangle gris clair centré en haut de la page avec une ombre portée subtile décalée de 5 pts. Aucun texte supplémentaire, seulement la forme — exactement ce que le code produit.

## Questions fréquentes & cas particuliers

### Et si j’ai besoin d’une forme différente ?

Remplacez `ShapeType.Rectangle` par n’importe quelle autre valeur de l’énumération `ShapeType` (`Ellipse`, `Triangle`, `Star`, etc.). Les propriétés d’ombre fonctionnent de la même manière.

### Puis‑je ajouter plusieurs ombres ?

Aspose.Words ne prend en charge qu’une seule ombre par forme. Si vous avez besoin d’effets superposés, créez deux formes qui se chevauchent avec des paramètres d’ombre différents.

### Comment cela fonctionne‑t‑il sur .NET Core ?

La même API fonctionne sur .NET 6/7/8. Assurez‑vous simplement de référencer le package **Aspose.Words.NETCore** (ou le package standard, qui est désormais multiplateforme).

### `System.Drawing` est‑il toujours pris en charge sous Linux ?

`System.Drawing.Common` est uniquement disponible sous Windows à partir de .NET 6. Pour les projets multiplateformes, utilisez `Aspose.Drawing` (un NuGet séparé) ou restez sur les couleurs définies par `Aspose.Words` lui‑même.

### Qu’en est‑il du redimensionnement DPI ?

Les dimensions de la forme sont en points (1 pt = 1/72 pouce). Si vous avez besoin d’une taille pixel‑parfaite pour un DPI spécifique, calculez les points comme `pixels * 72 / dpi`.

## Astuces pro & pièges à éviter

- **Astuce pro :** Définissez `rectangleShape.WrapType = WrapType.Inline;` si vous voulez que la forme s’écoule avec le texte au lieu de flotter au-dessus.  
- **Attention à** : Oublier d’activer l’ombre (`Enabled = true`). Les autres paramètres seront silencieusement ignorés.  
- **Note de performance** : Ajouter de nombreuses formes dans une boucle serrée peut être lent. Regroupez‑les dans une seule `Section` et appelez `document.UpdatePageLayout()` une fois à la fin.  
- **Vérification de version** : L’API d’ombre a été introduite dans Aspose.Words 20.2. Si vous utilisez une version antérieure, mettez‑à‑jour pour éviter les propriétés manquantes.

## Conclusion

Nous avons **créé un document Word vierge**, construit une **rectangle shape word**, appris **comment ajouter une ombre**, et enfin **inséré du contenu shape word** avec un effet **add shape shadow** soigné — le tout en utilisant Aspose.Words pour .NET.  

L’extrait est entièrement exécutable, fonctionne sous Windows et .NET multiplateforme, et peut être étendu à d’autres formes, couleurs ou même des GIF animés. Ensuite, vous pourriez explorer l’ajout de texte à l’intérieur du rectangle, l’application de remplissages en dégradé, ou la génération d’un rapport complet avec plusieurs formes stylisées.  

Vous avez d’autres idées ? Essayez de remplacer l’ombre grise par une bleue, augmentez le flou pour un rendu onirique, ou combinez plusieurs formes pour créer un logo personnalisé. Le ciel est la limite, et vous avez maintenant les blocs de construction pour le faire.  

Bon codage, et que vos documents soient toujours impeccables (avec juste la bonne quantité d’ombre) !

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}