---
category: general
date: 2026-03-04
description: Apprenez à créer une forme rectangulaire, ajouter une ombre à la forme
  et appliquer l'effet d'ombre dans un document Word, puis enregistrer automatiquement
  le document Word.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- apply shadow effect
- save word document
- create blank document
language: fr
og_description: Create rectangle shape, add shadow to shape and apply shadow effect
  in a Word document using C#. Follow this guide to save Word document effortlessly.
og_title: Créer une forme rectangulaire dans Word – Tutoriel complet C#
tags:
- C#
- Aspose.Words
- Document Automation
title: Create rectangle shape in Word with C# – Step‑by‑Step Guide
url: /fr/java/advanced-text-processing/create-rectangle-shape-in-word-with-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer une forme rectangulaire dans Word avec C# – Tutoriel complet de programmation

Vous avez déjà eu besoin de **créer une forme rectangulaire** dans un fichier Word mais vous ne saviez pas par où commencer ? Vous n'êtes pas seul — de nombreux développeurs rencontrent ce problème lorsqu'ils s'initient à la génération de documents par programme. La bonne nouvelle, c’est qu’avec quelques lignes de C# vous pouvez insérer un rectangle, **ajouter une ombre à la forme**, et **appliquer un effet d’ombre** sans jamais ouvrir Word vous‑même. Dans ce guide, nous parcourrons l’ensemble du processus, depuis la **création d’un document vierge** jusqu’à l’enregistrement du **document Word** final sur le disque.

Nous couvrirons tout ce dont vous avez besoin : le package NuGet requis, les API exactes, pourquoi chaque propriété est importante, et quelques astuces pour éviter les pièges les plus courants. À la fin, vous disposerez d’un exemple pleinement fonctionnel que vous pourrez intégrer à n’importe quel projet .NET.

## Prérequis

- .NET 6.0 ou version ultérieure (le code fonctionne également avec .NET Framework 4.7+)
- Visual Studio 2022 ou tout autre IDE de votre choix
- **Aspose.Words for .NET** installé via NuGet (`Install-Package Aspose.Words`)
- Familiarité de base avec la syntaxe C#

Aucune bibliothèque d’interopérabilité Word supplémentaire n’est nécessaire — Aspose.Words gère tout en mémoire.

## Étape 1 – Créer un document vierge

La première chose que nous faisons est de **créer un document vierge**. Pensez‑y comme à une toile vide sur laquelle nous **créerons une forme rectangulaire** plus tard.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Initialize a new blank document
Document doc = new Document();   // This gives us a fresh Word file
```

> **Pourquoi c’est important :** Commencer avec un objet `Document` propre garantit qu’aucun style ou section caché n’interfère avec le positionnement de la forme ultérieurement.

## Étape 2 – Insérer une forme rectangulaire dans le document

Nous allons maintenant réellement **créer une forme rectangulaire**. Nous définirons sa taille, son positionnement, et indiquerons à Word de ne pas enrouler le texte autour.

```csharp
// Step 2: Add a rectangle shape
Shape rectangle = new Shape(doc, ShapeType.Rectangle);
rectangle.Width = 200;          // Width in points (1 point = 1/72 inch)
rectangle.Height = 100;         // Height in points
rectangle.WrapType = WrapType.None; // No text wrapping
```

> **Astuce pro :** Si vous avez besoin que le rectangle se trouve à l’intérieur d’une cellule de tableau, changez `WrapType` en `WrapType.Inline`. Pour la plupart des rapports, `None` maintient la forme en flottant au-dessus du texte.

## Étape 3 – Ajouter une ombre à la forme et configurer son apparence

C’est ici que la magie opère : nous **ajoutons une ombre à la forme** et **appliquons l’effet d’ombre**. L’ombre fait ressortir le rectangle sur la page, surtout à l’impression.

```csharp
// Step 3: Enable shadow and set its properties
rectangle.ShadowFormat.Visible = true;          // Turn on the shadow
rectangle.ShadowFormat.BlurRadius = 5.0;        // Softness of the shadow edge
rectangle.ShadowFormat.Transparency = 0.3;      // 30 % transparent
rectangle.ShadowFormat.OffsetX = 8;             // Horizontal shift
rectangle.ShadowFormat.OffsetY = 8;             // Vertical shift
rectangle.ShadowFormat.Color = Color.Blue;     // Shadow colour
```

> **Pourquoi ces valeurs ?**  
> - **BlurRadius** contrôle le degré de flou des bords ; une valeur autour de `5` donne un rendu subtil et professionnel.  
> - **Transparency** permet au texte sous‑jacent de rester lisible.  
> - **OffsetX/Y** déplacent l’ombre par rapport à la forme, créant de la profondeur.  
> - Utiliser une teinte **bleue** n’est qu’un exemple — n’importe quel `System.Drawing.Color` fonctionne.

## Étape 4 – Ajouter la forme configurée au corps du document

Une fois le rectangle entièrement stylisé, nous **ajoutons la forme rectangulaire** à la première section du document. Cette étape place réellement la forme dans le fichier.

```csharp
// Step 4: Append the shape to the first section's body
doc.FirstSection.Body.AppendChild(rectangle);
```

> **Cas particulier :** Si votre document contient déjà plusieurs sections, vous voudrez peut‑être cibler une section spécifique (`doc.Sections[2]` par exemple). Le code ci‑dessus fonctionne pour un document à section unique, ce qui est fréquent pour les rapports rapides.

## Étape 5 – Enregistrer le document Word

Enfin, nous **enregistrons le document Word** sur le disque. Le fichier contiendra le rectangle avec son ombre, prêt à être ouvert dans Microsoft Word.

```csharp
// Step 5: Persist the document
string outputPath = @"C:\Temp\shadowed_rectangle.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

> **Conseil :** Utilisez `doc.Save(outputPath, SaveFormat.Docx)` si vous devez être explicite sur le format. La méthode `Save` détecte automatiquement l’extension, mais être explicite peut éviter des confusions lorsque le chemin est généré par programme.

## Exemple complet, exécutable

Voici le programme complet que vous pouvez copier‑coller dans une application console. Il inclut toutes les instructions `using` et la méthode `Main`, afin que vous puissiez l’exécuter immédiatement.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank document
            Document doc = new Document();

            // 2️⃣ Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle);
            rectangle.Width = 200;
            rectangle.Height = 100;
            rectangle.WrapType = WrapType.None;

            // 3️⃣ Apply shadow effect
            rectangle.ShadowFormat.Visible = true;
            rectangle.ShadowFormat.BlurRadius = 5.0;
            rectangle.ShadowFormat.Transparency = 0.3;
            rectangle.ShadowFormat.OffsetX = 8;
            rectangle.ShadowFormat.OffsetY = 8;
            rectangle.ShadowFormat.Color = Color.Blue;

            // 4️⃣ Insert the shape into the document body
            doc.FirstSection.Body.AppendChild(rectangle);

            // 5️⃣ Save the document
            string outputPath = @"C:\Temp\shadowed_rectangle.docx";
            doc.Save(outputPath);
            Console.WriteLine($"✅ Document saved at {outputPath}");
        }
    }
}
```

### Résultat attendu

Lorsque vous ouvrez *shadowed_rectangle.docx* dans Microsoft Word, vous verrez un rectangle à bord bleu flottant près du haut de la première page, avec une ombre bleue douce décalée de 8 pt vers la droite et le bas. Aucun texte supplémentaire ne l’entoure parce que nous avons défini `WrapType.None`.

## Questions fréquentes & variantes

| Question | Réponse |
|----------|---------|
| **Puis‑je changer la forme en une ellipse ?** | Oui — remplacez `ShapeType.Rectangle` par `ShapeType.Ellipse`. Toutes les propriétés d’ombre restent identiques. |
| **Et si j’ai besoin de plusieurs formes ?** | Répétez simplement les Étapes 2‑4 pour chaque nouvelle instance de `Shape`, en ajustant `OffsetX/Y` ou `Left/Top` pour éviter le chevauchement. |
| **Existe‑t‑il un moyen de faire correspondre la couleur de l’ombre à celle du remplissage de la forme ?** | Absolument. Définissez d’abord `rectangle.FillColor`, puis affectez `rectangle.ShadowFormat.Color = rectangle.FillColor;`. |
| **Comment insérer la forme dans une cellule de tableau ?** | Utilisez `cell.FirstParagraph.AppendChild(rectangle);` après avoir localisé l’objet `Cell` souhaité. |
| **Cela fonctionnera‑t‑il sur .NET Core ?** | Oui—Aspose.Words est multiplateforme. Assurez‑vous simplement de référencer la version NuGet appropriée pour .NET Core/5/6. |

## Pièges courants & astuces pro

- **Piège :** Oublier de définir `ShadowFormat.Visible = true`. Les propriétés d’ombre seront alors ignorées silencieusement.  
  **Solution :** Activez toujours la visibilité avant de modifier les autres paramètres d’ombre.

- **Piège :** Utiliser un `BlurRadius` très grand (par ex., 20) peut rendre l’ombre floue et non professionnelle.  
  **Solution :** Restez entre `3` et `8` pour la plupart des documents d’entreprise.

- **Astuce pro :** Si vous avez besoin que la forme soit sélectionnable ultérieurement (par ex., pour une édition par l’utilisateur final), évitez `WrapType.Inline`. Les formes flottantes (`WrapType.None`) sont plus faciles à déplacer programmaticalement.

- **Astuce pro :** Lors de la génération de nombreux documents dans une boucle, réutilisez une seule instance de `Document` et appelez `doc.Clone(true)` pour chaque itération afin d’améliorer les performances.

## Sujets connexes à explorer ensuite

- **Ajouter du texte à l’intérieur d’une forme rectangulaire** – apprenez à utiliser `Shape.TextPath` pour les libellés.  
- **Créer des diagrammes complexes** – combinez plusieurs formes, connecteurs et groupes.  
- **Exporter en PDF** – convertissez le même document en PDF avec un simple `doc.Save("output.pdf")`.  
- **Appliquer différents styles de remplissage** – dégradés, textures ou même images à l’intérieur des formes.

## Conclusion

Nous venons de **créer une forme rectangulaire**, **ajouter une ombre à la forme**, et **appliquer un effet d’ombre** dans un fichier Word à l’aide de C#. En suivant ces cinq étapes concises, vous disposez maintenant d’un modèle réutilisable pour tout scénario d’automatisation de documents, et vous savez comment **enregistrer le document Word** de façon fiable. N’hésitez pas à ajuster les dimensions, les couleurs, ou même à remplacer le rectangle par une autre géométrie — Aspose.Words rend tout cela simple.

Si ce tutoriel vous a été utile, donnez‑lui une étoile sur GitHub, ou partagez vos propres variantes dans les commentaires. Bon codage, et que vos documents soient toujours aussi soignés que ce rectangle ombré !

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}