---
category: general
date: 2026-09-14
description: Apprenez à masquer une forme dans Word avec C# — y compris le code de
  création de document Word, l’insertion d’une forme rectangle dans Word et le masquage
  de la forme dans Word de façon programmatique.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape
- hide shape in word
- create word document code
- insert rectangle shape word
language: fr
lastmod: 2026-09-14
og_description: Comment masquer une forme dans Word avec C# — guide étape par étape
  qui montre également comment créer du code de document Word et insérer une forme
  rectangle.
og_image_alt: Word document preview with a visible rectangle shape and a hidden ellipse
  shape
og_title: Comment masquer une forme dans un document Word avec du code C#
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Learn how to hide shape in Word using C#—including create word document
    code, insert rectangle shape word, and hide shape in word programmatically.
  headline: How to hide shape in a Word document with C# code
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Comment masquer une forme dans un document Word avec du code C#
url: /fr/net/programming-with-shapes/how-to-hide-shape-in-a-word-document-with-c-code/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment masquer une forme dans un document Word avec du code C# 

Si vous devez **how to hide shape** dans un fichier Word, ce tutoriel montre la solution complète. Vous verrez comment créer un document Word, insérer une forme rectangle, ajouter une ellipse, et masquer cette ellipse afin que seul le rectangle apparaisse lorsque le fichier est ouvert.

Le guide couvre tout ce dont vous avez besoin — aucune référence externe, seulement le code et les explications. À la fin, vous serez capable d’intégrer des graphiques cachés dans n’importe quel document Word que vous générez programmaticalement.

## Prérequis

- .NET 6.0 ou supérieur (le code fonctionne également avec .NET Framework 4.7+)
- Aspose.Words for .NET (version d’essai gratuite ou version sous licence)  
  Installez-le via NuGet : `dotnet add package Aspose.Words`
- Familiarité de base avec C# et Visual Studio ou tout IDE de votre choix

## Étape 1 : Configurer le projet et importer les espaces de noms

Créez une nouvelle application console et ajoutez les instructions `using` requises. Ces importations vous donnent accès aux classes `Document`, `DocumentBuilder` et de dessin nécessaires pour manipuler les formes.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The rest of the code follows in the next steps
        }
    }
}
```

**Pourquoi c’est important** – Importer les bons espaces de noms évite les erreurs de compilation et rend l’API disponible pour la création de formes et le contrôle de leur visibilité.

## Étape 2 : Créer un nouveau document Word et un builder

Un `Document` représente le fichier, tandis qu’un `DocumentBuilder` fournit une API fluide pour ajouter du contenu. C’est le premier endroit où vous appliquez la logique **how to hide shape** : vous avez besoin d’un contexte de document avant qu’une forme puisse exister.

```csharp
// Step 2: Create a new blank document and a builder to edit it
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);
```

**Explication** – L’objet `Document` commence vide. Le `DocumentBuilder` est positionné au début du premier paragraphe, prêt à insérer des formes ou du texte.

## Étape 3 : Insérer une forme rectangle visible

Le rectangle sera la forme qui restera visible lorsque le document sera ouvert. Vous pouvez contrôler sa taille, sa position et son formatage directement via l’objet forme.

```csharp
// Step 3: Insert a visible rectangle shape and position it
Shape visibleRectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
visibleRectangle.Left = 50;                 // 50 points from the left margin
visibleRectangle.Top = 100;                 // 100 points from the top of the page
visibleRectangle.FillColor = System.Drawing.Color.LightBlue;
visibleRectangle.LineColor = System.Drawing.Color.DarkBlue;
```

**Pourquoi cette étape** – Ajouter un rectangle illustre l’exigence **insert rectangle shape word**. Définir `FillColor` et `LineColor` rend la forme facile à repérer dans le document final.

## Étape 4 : Insérer une forme ellipse et la masquer

Vous ajoutez maintenant la forme que vous souhaitez dissimuler. La propriété `Hidden` indique à Word de ne pas rendre la forme dans l’interface utilisateur, bien qu’elle reste partie intégrante de la structure du document.

```csharp
// Step 4: Insert an ellipse shape, position it, and hide it from view
Shape hiddenEllipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
hiddenEllipse.Left = 200;      // Position away from the rectangle
hiddenEllipse.Top = 100;
hiddenEllipse.Hidden = true;   // This flag implements how to hide shape
```

**Explication** – Définir `Hidden = true` est le cœur de **hide shape in word**. Word respecte ce drapeau lors de la visualisation et de l’impression normales, mais la forme peut toujours être accédée programmaticalement si nécessaire.

## Étape 5 : Enregistrer le document

Enfin, écrivez le document sur le disque. Choisissez un dossier où vous avez les droits d’écriture, et donnez au fichier un nom clair reflétant l’objectif du tutoriel.

```csharp
// Step 5: Save the document with both shapes
string outputPath = @"C:\Temp\ShapeVisibility.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

**Résultat** – L’ouverture de `ShapeVisibility.docx` dans Microsoft Word affiche uniquement le rectangle bleu clair. L’ellipse masquée n’apparaît pas, confirmant que vous avez maîtrisé avec succès **how to hide shape** dans un fichier Word.

## Exemple complet fonctionnel

Assembler tous les extraits donne un programme unique et exécutable :

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a new document and builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert a visible rectangle
            Shape visibleRectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            visibleRectangle.Left = 50;
            visibleRectangle.Top = 100;
            visibleRectangle.FillColor = System.Drawing.Color.LightBlue;
            visibleRectangle.LineColor = System.Drawing.Color.DarkBlue;

            // Insert a hidden ellipse
            Shape hiddenEllipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
            hiddenEllipse.Left = 200;
            hiddenEllipse.Top = 100;
            hiddenEllipse.Hidden = true; // hides the shape

            // Save the document
            string outputPath = @"C:\Temp\ShapeVisibility.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Résultat attendu

- **Visuel** : Lorsque vous ouvrez `ShapeVisibility.docx`, vous voyez un rectangle bleu clair positionné près de la marge gauche. Aucune ellipse n’est visible.
- **Programmatique** : L’ellipse masquée reste dans le XML du document (élément `<w:drawing>`) avec l’attribut `w:hidden` défini, ce que vous pouvez vérifier en ouvrant le fichier comme une archive zip et en inspectant `document.xml`.

## Questions fréquentes et cas particuliers

| Question | Réponse |
|----------|--------|
| *Puis-je masquer plusieurs formes ?* | Oui. Définissez `Hidden = true` sur chaque forme que vous souhaitez dissimuler. |
| *Les formes masquées s’impriment-elles ?* | Par défaut, Word n’imprime pas les objets masqués. Si vous avez besoin qu’ils soient imprimés, supprimez le drapeau `Hidden` avant l’impression. |
| *La propriété hidden est‑elle prise en charge dans les versions plus anciennes de Word ?* | L’attribut `Hidden` fait partie de la norme Office Open XML et fonctionne dans Word 2007 et versions ultérieures. |
| *Et si je dois basculer la visibilité à l’exécution ?* | Récupérez la forme via `document.GetChildNodes(NodeType.Shape, true)` et inversez la propriété `Hidden` selon votre logique. |

## Astuces professionnelles

- **Performance** : Si vous générez de nombreux documents, réutilisez une seule instance de `DocumentBuilder` au lieu d’en créer une nouvelle pour chaque fichier.
- **Contrôle de version** : Stockez les fichiers `.docx` générés dans un dossier sous contrôle de version ; les formes masquées peuvent servir de marqueurs de métadonnées pour le traitement en aval.
- **Tests** : Automatisez un test visuel rapide en convertissant le DOCX en PDF avec Aspose.Words (`document.Save("out.pdf")`). Le PDF masquera également l’ellipse, confirmant que le drapeau hidden se propage lors des conversions de format.

## Conclusion

Vous savez maintenant **how to hide shape** dans un document Word en utilisant C#. Le tutoriel a parcouru la création d’un document, **insert rectangle shape word**, l’ajout d’une ellipse, et l’application du drapeau `Hidden` pour obtenir le comportement **hide shape in word**. Avec le code complet et exécutable, vous pouvez intégrer des graphiques cachés dans n’importe quel flux de travail de génération de rapports ou de modèles automatisés.

### Prochaines étapes

- Explorez d’autres propriétés de forme telles que la rotation, l’ombre et le texte d’habillage.  
- Combinez les formes masquées avec des propriétés de document personnalisées pour intégrer des données lisibles par machine.  
- Examinez les modèles **create word document code** pour les tableaux, graphiques et contrôles de contenu afin d’élargir votre boîte à outils d’automatisation.

N’hésitez pas à expérimenter différents types de formes et réglages de visibilité — votre prochain projet d’automatisation Word n’est qu’à quelques lignes de code !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}