---
category: general
date: 2026-08-20
description: Apprenez comment définir la propriété « cachée » d’une forme dans Aspose.Words
  pour C#. Ce guide montre comment insérer une image et masquer la forme afin qu’elle
  n’apparaisse jamais dans l’interface utilisateur ou la sortie imprimée.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set shape hidden property
- insert image into document
- hide shape in Aspose.Words
- C# shape hidden property
- Aspose.Words DocumentBuilder
- prevent shape from printing
language: fr
lastmod: 2026-08-20
og_description: Définir la propriété cachée d’une forme dans Aspose.Words avec C#.
  Insérer une image, masquer la forme et s’assurer qu’elle n’apparaît jamais dans
  l’interface utilisateur ni dans la sortie imprimée.
og_image_alt: Diagram illustrating set shape hidden property on a Word document shape
og_title: Définir la propriété cachée d’une forme dans Aspose.Words – guide complet
  C#
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to set shape hidden property in Aspose.Words for C#. This
    guide shows inserting an image and hiding the shape so it never appears in the
    UI or print output.
  headline: How to set shape hidden property in Aspose.Words for C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document Automation
- Shape Handling
title: Comment définir la propriété cachée d’une forme dans Aspose.Words pour C#
url: /fr/java/images-shapes/how-to-set-shape-hidden-property-in-aspose-words-for-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment définir la propriété « hidden » d’une forme dans Aspose.Words pour C#

Si vous devez **définir la propriété hidden d’une forme** dans un document Word, ce tutoriel vous montre les étapes exactes à l’aide d’Aspose.Words pour .NET. Que vous construisiez un moteur de modèles, génériez des rapports ou intégriez un logo qui doit rester invisible, vous apprendrez comment insérer une image et masquer la forme afin qu’elle n’apparaisse jamais dans l’interface utilisateur ni dans la sortie imprimée.

Dans ce guide, nous couvrons également **l’insertion d’image dans le document**, expliquons pourquoi masquer une forme est important pour l’impression, et parcourons le code complet et exécutable. Aucun référentiel externe n’est requis — il suffit de copier, coller et exécuter.

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

* .NET 6.0 ou version ultérieure (la dernière version d’Aspose.Words cible .NET 6+)
* Une licence valide d’Aspose.Words pour .NET (ou utilisez le mode d’évaluation gratuit)
* Visual Studio 2022 ou tout IDE C# de votre choix
* Un fichier image (par ex., `logo.png`) placé dans un dossier que vous pouvez référencer depuis le code

## Étape 1 : Créer un nouveau Document et DocumentBuilder

La classe `DocumentBuilder` est le point d’entrée pour créer du contenu Word de façon programmatique. Elle vous permet d’insérer des paragraphes, des tableaux et des formes telles que des images.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Initialize a new blank document
        Document doc = new Document();
        // DocumentBuilder provides methods to add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Pourquoi cette étape ?*  
Créer un `Document` vous fournit une représentation en mémoire d’un fichier .docx, tandis que le `DocumentBuilder` offre l’API fluide qui insère les objets. Sans ces objets, vous ne pouvez pas placer une forme dans le document.

## Étape 2 : Insérer l’image en tant que forme

Aspose.Words traite chaque image comme une `Shape`. La méthode `InsertImage` renvoie cette instance de `Shape`, que vous pouvez ensuite manipuler.

```csharp
        // Step 2: Insert an image into the document
        // The returned Shape object lets us modify properties like size, rotation, and visibility.
        Shape picture = builder.InsertImage(@"YOUR_DIRECTORY\logo.png");
```

*Pourquoi cette étape ?*  
Utiliser `InsertImage` ajoute non seulement l’image au flux de texte, mais vous donne également une référence (`picture`) que vous pouvez configurer. C’est essentiel pour la **propriété hidden de forme C#** que nous définirons ensuite.

## Étape 3 : Définir la propriété hidden de la forme

La propriété `Hidden` contrôle si la forme participe à l’interface utilisateur et à l’impression. La régler sur `true` rend la forme invisible dans l’UI Word et garantit qu’elle ne sera pas imprimée.

```csharp
        // Step 3: Hide the inserted shape so it won't appear in the UI or print output
        picture.Hidden = true;
```

*Pourquoi cette étape ?*  
Lorsqu’une forme est marquée comme cachée, Word la traite comme un commentaire — présente dans la structure du document mais jamais rendue. C’est le cœur de **définir la propriété hidden d’une forme**.

## Étape 4 : Enregistrer le document

Enfin, écrivez le document sur le disque. Vous pouvez choisir n’importe quel format pris en charge par Aspose.Words (`.docx`, `.pdf`, `.html`, etc.).

```csharp
        // Step 4: Save the document to a .docx file
        doc.Save(@"OUTPUT\HiddenImageDocument.docx");
        // Optional: Save as PDF to verify the shape really stays hidden when printed
        doc.Save(@"OUTPUT\HiddenImageDocument.pdf");
    }
}
```

*Pourquoi cette étape ?*  
L’enregistrement finalise les modifications en mémoire. Ouvrir le `.docx` résultant dans Microsoft Word ne montre aucune image visible, et l’exportation en PDF confirme que la forme n’apparaît jamais dans la sortie imprimée.

## Exemple complet et exécutable

En rassemblant tous les éléments, voici le programme complet que vous pouvez compiler et exécuter :

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeHiddenDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Initialize a blank document and a builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert an image as a shape
            // Replace YOUR_DIRECTORY with the actual folder that contains logo.png
            Shape picture = builder.InsertImage(@"YOUR_DIRECTORY\logo.png");

            // 3️⃣ Set the shape hidden property
            picture.Hidden = true; // This hides the shape in UI and when printing

            // 4️⃣ Save the document in both DOCX and PDF formats
            doc.Save(@"OUTPUT\HiddenImageDocument.docx");
            doc.Save(@"OUTPUT\HiddenImageDocument.pdf");

            Console.WriteLine("Document created successfully. The image is hidden.");
        }
    }
}
```

**Résultat attendu**

* L’ouverture de `HiddenImageDocument.docx` dans Microsoft Word ne montre aucune image visible.
* L’exportation ou l’impression du document (ou l’ouverture du PDF) ne montre également aucune image.
* La forme cachée existe toujours dans le XML du document, que vous pouvez vérifier en ouvrant le `.docx` comme une archive zip et en inspectant `word/document.xml` — vous verrez un élément `<w:pict>` avec `w:hidden="true"`.

## Variations courantes et cas limites

| Situation | Que faire | Pourquoi c’est important |
|-----------|-----------|---------------------------|
| **Fichier image manquant** | Enveloppez `InsertImage` dans un `try/catch` et gérez `FileNotFoundException`. | Empêche le plantage de l’application et vous permet de consigner une erreur claire. |
| **Plusieurs formes cachées** | Appelez `picture.Hidden = true` pour chaque `Shape` que vous insérez, ou parcourez `doc.GetChildNodes(NodeType.Shape, true)`. | Garantit que chaque élément visuel indésirable reste invisible. |
| **Besoin que la forme soit visible uniquement en mode édition** | Réglez `picture.Hidden = false` après l’édition, puis basculez à nouveau avant l’enregistrement. | Vous permet de travailler avec la forme dans l’UI tout en gardant la sortie finale propre. |
| **Impression sur d’anciennes versions de Word** | Vérifiez le document avec Word 2010 ou ultérieur ; le drapeau hidden est pris en charge par toutes les versions modernes. | Assure la compatibilité pour l’ensemble de votre base d’utilisateurs. |
| **Utilisation d’un format de fichier différent (par ex., PDF directement)** | Le drapeau `Hidden` fonctionne de la même façon ; Aspose.Words le respecte lors de la conversion PDF. | Confirme que **empêcher la forme d’être imprimée** fonctionne pour toutes les cibles d’exportation. |

## Astuce pro : Vérifier le drapeau hidden par programme

Si vous devez confirmer qu’une forme est cachée avant l’enregistrement, vous pouvez inspecter la propriété :

```csharp
bool isHidden = picture.Hidden;
Console.WriteLine($"Shape hidden? {isHidden}");
```

Cette vérification simple est utile dans les pipelines automatisés où vous devez garantir le respect des politiques de génération de documents.

## Conclusion

Vous savez maintenant comment **définir la propriété hidden d’une forme** dans Aspose.Words pour C#. En insérant une image, en appliquant `picture.Hidden = true` et en enregistrant le document, la forme reste hors de l’UI et n’apparaît jamais dans la sortie imprimée. Cette technique est indispensable lorsque vous avez besoin d’espaces réservés, de filigranes ou d’éléments de marque qui doivent rester invisibles pour les utilisateurs finaux.

### Et après ?

* Explorez d’autres propriétés de forme telles que `picture.WrapType`, `picture.Rotation` et `picture.RelativeHorizontalPosition`.
* Apprenez comment **masquer une forme dans Aspose.Words** de façon conditionnelle selon les entrées utilisateur ou la configuration.
* Combinez les formes cachées avec des boucles **d’insertion d’image dans le document** pour générer des marqueurs invisibles dynamiques destinés à un traitement ultérieur (par ex., champs de publipostage).

N’hésitez pas à expérimenter avec différents formats d’image, mises en page de document et cibles d’exportation. Masquer les formes vous donne un contrôle granulaire sur ce que vos lecteurs voient réellement — et ce qui reste en arrière‑plan. Bon codage !


## Que devez‑vous apprendre ensuite ?


Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}