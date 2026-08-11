---
category: general
date: 2026-08-10
description: Insérer une forme rectangulaire dans Word avec C#. Apprenez à masquer
  une forme, masquer une forme dans Word, et créer une forme cachée avec Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- hide shape in word
- create hidden shape
language: fr
lastmod: 2026-08-10
og_description: Insérez une forme rectangulaire dans Word avec C#. Ce tutoriel explique
  comment masquer une forme, masquer une forme dans Word et créer une forme cachée
  avec des exemples de code complets.
og_image_alt: Screenshot showing a hidden rectangle shape inserted into a Word document
  using C#
og_title: Insérer une forme rectangulaire dans Word avec C# – guide étape par étape
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
    shape in Word, and create hidden shape with Aspose.Words.
  headline: Insert rectangle shape in Word with C# – complete guide
  type: TechArticle
- description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
    shape in Word, and create hidden shape with Aspose.Words.
  name: Insert rectangle shape in Word with C# – complete guide
  steps:
  - name: Can I hide only the outline but keep the fill visible?
    text: Yes. Instead of setting `Hidden = true`, you can set `rectangle.LineFormat.Visible
      = false` to hide the border while keeping the fill color. This is a variation
      of **how to hide shape** that preserves part of the visual appearance.
  - name: Does the hidden flag work in older Word versions (2003, 2007)?
    text: The hidden attribute is part of the Open XML specification introduced with
      Word 2007. Documents saved in the older binary `.doc` format will not preserve
      the flag. To support legacy formats, save the document as `.docx` and, if needed,
      convert it later using Aspose.Words’ `SaveFormat.Doc`.
  - name: What if I need to hide multiple shapes at once?
    text: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` on each shape that meets your criteria (e.g., a specific
      `ShapeType` or a custom `AlternativeText` value).
  - name: Is there a performance impact when hiding shapes?
    text: The hidden flag adds a tiny XML attribute; it does not affect rendering
      speed. However, a very large number of hidden objects can increase file size
      marginally. Remove shapes you never need to keep the document lean.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Insérer une forme rectangulaire dans Word avec C# – guide complet
url: /fr/net/programming-with-shapes/insert-rectangle-shape-in-word-with-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insérer une forme rectangulaire dans Word avec C# – guide complet

Si vous devez **insérer une forme rectangulaire** dans un document Word en utilisant C#, ce guide vous montre les étapes exactes. Vous apprendrez également **comment masquer une forme** afin qu'elle n'apparaisse pas dans le fichier final, ce qui répond à la requête courante **hide shape in Word** et démontre comment **create hidden shape** programmatically.

Le tutoriel couvre tout, de la configuration du SDK Aspose.Words à la vérification que la forme est masquée. À la fin de l'article, vous disposerez d'un extrait de code réutilisable que vous pourrez intégrer dans n'importe quel projet .NET.

## Prérequis

- .NET 6.0 ou version ultérieure installé (le code fonctionne également avec .NET Framework 4.6+)
- Une licence valide d'Aspose.Words for .NET ou une clé d'évaluation temporaire
- Visual Studio 2022 (ou tout IDE supportant C#)
- Familiarité de base avec la syntaxe C# et le Document Object Model (DOM) des fichiers Word

Aucun package NuGet supplémentaire n'est requis au-delà de `Aspose.Words`.

## Étape 1 : Créer un nouveau document vierge et un DocumentBuilder

La première opération consiste à instancier un objet `Document`. Le `DocumentBuilder` fournit une API pratique pour insérer du contenu tel que des formes, des paragraphes et des tableaux.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document document = new Document();

// DocumentBuilder lets you add elements to the document.
DocumentBuilder builder = new DocumentBuilder(document);
```

**Pourquoi c'est important :** `Document` représente l'ensemble du fichier .docx, tandis que `DocumentBuilder` maintient un curseur qui indique où le prochain élément sera placé. L'initialisation des deux objets constitue la base de toute tâche d'automatisation Word.

## Étape 2 : Insérer une forme rectangulaire

Vous insérez maintenant le rectangle. La méthode `InsertShape` nécessite le type de forme et ses dimensions en points (1 point ≈ 1/72 pouce). Une taille de **200 × 100 points** donne un rectangle d'environ 2,78 × 1,39 pouces.

```csharp
// Insert a rectangle of 200x100 points.
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

**Pourquoi c'est important :** L'objet `Shape` que vous obtenez est entièrement configurable — la couleur, la bordure, le texte et la visibilité peuvent tous être modifiés avant l'enregistrement du document.

## Étape 3 : Masquer la forme

Pour empêcher le rectangle d'être affiché ou imprimé, définissez sa propriété `Hidden` sur `true`. Cette propriété correspond directement à l'attribut « Hidden » de Word, que Word respecte à la fois en mode affichage et impression.

```csharp
// Hide the shape so it never appears.
rectangle.Hidden = true;
```

**Pourquoi c'est important :** Définir `Hidden` est la méthode standard pour **hide shape in Word** sans supprimer la forme de la structure du document. La forme reste accessible au code, permettant des manipulations ultérieures telles que le formatage conditionnel ou les basculements de visibilité basés sur les données.

## Étape 4 : Enregistrer le document

Enfin, persistez le document sur le disque. Choisissez n'importe quel dossier ; l'exemple utilise un chemin factice que vous devez remplacer par un chemin réel.

```csharp
// Save the document with the hidden rectangle.
document.Save(@"C:\Temp\HiddenShape.docx");
```

**Pourquoi c'est important :** L'enregistrement finalise le fichier et écrit le drapeau hidden dans l'Open XML sous‑jacent. Lorsque vous ouvrez le document dans Microsoft Word, le rectangle sera invisible, confirmant que vous avez bien **created hidden shape**.

## Étape 5 : Vérifier la forme masquée

Ouvrez le fichier généré `HiddenShape.docx` dans Microsoft Word :

1. Accédez à **Fichier → Options → Affichage** et assurez‑vous que *« Afficher le texte masqué »* est **désactivé**.  
2. Le rectangle ne doit apparaître sur aucune page.  
3. Pour vérifier à nouveau, activez *« Afficher le texte masqué »* ; le rectangle apparaîtra avec un contour pointillé pâle, prouvant que la forme existe mais est masquée.

Si le rectangle est encore visible, vérifiez que vous avez enregistré le fichier après avoir défini `Hidden = true` et que vous ouvrez le bon fichier.

## Exemple complet exécutable

Voici le programme complet que vous pouvez copier, coller et exécuter directement.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a rectangle shape of 200x100 points.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // Step 3: Hide the shape so it does not appear when viewed or printed.
        rectangle.Hidden = true;

        // Step 4: Save the document with the hidden shape.
        string outputPath = @"C:\Temp\HiddenShape.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
        Console.WriteLine("Open the file in Word to verify that the rectangle is hidden.");
    }
}
```

**Sortie attendue :** La console affiche le chemin du fichier et un bref rappel. Lorsque le fichier est ouvert dans Word, le rectangle est invisible sauf si le texte masqué est activé.

## Questions fréquentes et cas particuliers

### Puis‑je masquer uniquement le contour tout en conservant le remplissage visible ?

Oui. Au lieu de définir `Hidden = true`, vous pouvez définir `rectangle.LineFormat.Visible = false` pour masquer la bordure tout en conservant la couleur de remplissage. Il s'agit d'une variante de **how to hide shape** qui préserve une partie de l'apparence visuelle.

### Le drapeau hidden fonctionne‑t‑il dans les versions plus anciennes de Word (2003, 2007) ?

L'attribut hidden fait partie de la spécification Open XML introduite avec Word 2007. Les documents enregistrés au format binaire `.doc` plus ancien ne conserveront pas ce drapeau. Pour prendre en charge les formats hérités, enregistrez le document au format `.docx` et, si nécessaire, convertissez‑le ultérieurement à l'aide de `SaveFormat.Doc` d'Aspose.Words.

### Que faire si je dois masquer plusieurs formes en même temps ?

Parcourez la collection `Document.GetChildNodes(NodeType.Shape, true)` et définissez `Hidden = true` sur chaque forme qui répond à vos critères (par ex., un `ShapeType` spécifique ou une valeur personnalisée `AlternativeText`).

```csharp
foreach (Shape shp in document.GetChildNodes(NodeType.Shape, true))
{
    if (shp.AlternativeText == "HideMe")
        shp.Hidden = true;
}
```

### Y a‑t‑il un impact sur les performances lors du masquage des formes ?

Le drapeau hidden ajoute un minuscule attribut XML ; il n'affecte pas la vitesse de rendu. Cependant, un très grand nombre d'objets masqués peut augmenter légèrement la taille du fichier. Supprimez les formes dont vous n'avez jamais besoin afin de garder le document léger.

## Astuces et bonnes pratiques

- **Donnez à la forme un nom significatif** en utilisant `rectangle.Name = "MyHiddenRectangle"` ; cela facilite la recherche de la forme dans le DOM ultérieurement.
- **Définissez `AlternativeText`** avec une balise personnalisée (par ex., `"HiddenShape"`). Cela vous permet de localiser la forme sans dépendre de son index.
- **Encapsulez le code dans un bloc try‑catch** pour gérer les erreurs de licence ou les exceptions d'E/S de manière élégante.
- **Libérez le Document** après l'enregistrement si vous traitez de nombreux fichiers dans une boucle afin de libérer les ressources non gérées : `document.Dispose();`.

## Conclusion

Vous savez maintenant comment **insert rectangle shape** dans un document Word avec C#, comment **hide shape in Word**, et comment **create hidden shape** qui reste partie intégrante de la structure du document tout en restant invisible pour les utilisateurs finaux. L'exemple complet et exécutable montre l'ensemble du flux de travail, de la création du document à la vérification.

Ensuite, vous pourriez explorer **how to hide shape** en fonction des entrées utilisateur, ou combiner des formes masquées avec des contrôles de contenu pour une génération dynamique de documents. Vous pouvez également appliquer la même technique à d'autres types de formes comme les ellipses, les flèches ou les dessins personnalisés.

N'hésitez pas à expérimenter avec différentes dimensions, couleurs et paramètres de visibilité. Si vous rencontrez des problèmes, revenez aux étapes ci‑dessus ou consultez la documentation d'Aspose.Words pour des détails plus approfondis sur l'API. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Créer une forme rectangulaire dans Word avec C# – Guide étape par étape](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Créer une forme rectangulaire dans Word avec Aspose.Words – Guide étape par étape](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Tutoriel Aspose.Words Shape Shadow – Ajouter une ombre à une forme Word en C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}