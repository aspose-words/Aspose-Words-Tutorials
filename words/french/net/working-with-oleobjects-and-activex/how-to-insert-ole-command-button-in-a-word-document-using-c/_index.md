---
category: general
date: 2026-10-07
description: Apprenez à insérer un bouton de commande OLE dans un document Word avec
  Aspose.Words C#. Guide étape par étape couvrant DocumentBuilder, les propriétés
  et l’enregistrement du fichier.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert OLE command button
- Aspose.Words OLE control
- C# DocumentBuilder InsertForms2OleControl
- OleControlType CommandButton
- Word OLE command button
language: fr
lastmod: 2026-10-07
og_description: Insérez un bouton de commande OLE dans un document Word à l'aide de
  C#. Suivez ce tutoriel concis pour ajouter, configurer et enregistrer un CommandButton
  fonctionnel avec Aspose.Words.
og_image_alt: Insert OLE command button example in Word document
og_title: Insérer un bouton de commande OLE dans Word avec C# – guide complet Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  headline: How to insert OLE command button in a Word document using C#
  type: TechArticle
- description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  name: How to insert OLE command button in a Word document using C#
  steps:
  - name: Why this works
    text: '* `DocumentBuilder` is the primary API for building Word documents programmatically.
      * `InsertForms2OleControl` tells Aspose.Words to embed a **Forms2 OLE control**,
      which is the legacy Word form technology that supports command buttons, check
      boxes, etc. * The `OleControlType.CommandButton` enum va'
  - name: 1. What if the button does not appear where I expect?
    text: '* Word uses points, not pixels. Convert screen pixels to points (`points
      = pixels * 72 / DPI`). * Ensure the rectangle does not intersect page margins;
      otherwise Word may shift the control.'
  - name: 2. Can I insert the button into an existing document?
    text: Yes. Load the document with `new Document("Existing.docx")` and use the
      same `DocumentBuilder` workflow. Just remember to move the builder’s cursor
      (`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")`, etc.)
      before calling `InsertForms2OleControl`.
  - name: 3. How do I attach a macro to the button?
    text: 'Aspose.Words does not create VBA code, but you can embed a macro after
      the document is generated:'
  - name: 4. Does this work with .NET Core on Linux?
    text: The OLE control is a Windows‑specific feature because it relies on COM.
      On Linux the button will be inserted, but it will appear as a static picture
      without interactive behavior. For cross‑platform interactive forms, consider
      using content controls (`StructuredDocumentTag`) instead.
  - name: 5. What if I need a different size or multiple buttons?
    text: Create additional `Rectangle` objects with unique coordinates and repeat
      the `InsertForms2OleControl` call. Each button can have its own `Caption` and
      `Name`.
  type: HowTo
tags:
- Aspose.Words
- C#
- OLE
- Word automation
title: Comment insérer un bouton de commande OLE dans un document Word en C#
url: /fr/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment insérer un bouton de commande OLE dans un document Word avec C#

Si vous devez **insérer un bouton de commande OLE** dans un fichier Word de manière programmatique, ce guide vous montre exactement comment le faire avec Aspose.Words pour .NET. Que vous créiez un rapport rempli de formulaires ou que vous automatisiez un modèle nécessitant une interaction utilisateur, les étapes ci‑dessous vous offrent une solution complète et exécutable.

Vous apprendrez à créer un document vierge, à utiliser le `DocumentBuilder` pour placer un `Forms2OleControl`, à définir la légende et le nom du bouton, puis à enregistrer le `.docx`. Aucun outil externe n’est nécessaire en dehors de la bibliothèque Aspose.Words.

## Prérequis

* .NET 6.0 ou ultérieur (le code fonctionne également avec .NET Framework 4.7+)
* Une licence valide d’Aspose.Words pour .NET ou une clé d’évaluation gratuite
* Visual Studio 2022 (ou tout IDE C# de votre choix)
* Une connaissance de base de la syntaxe C# et des concepts OLE de Word

> **Astuce :** Si vous utilisez l’évaluation gratuite, le document généré contiendra un petit filigrane. Une version sous licence le supprime automatiquement.

## Étape 1 : Installer Aspose.Words

Ajoutez le package Aspose.Words à votre projet via NuGet :

```bash
dotnet add package Aspose.Words
```

Le package inclut les espaces de noms `Aspose.Words.Drawing` et `Aspose.Words.Drawing.Ole` nécessaires aux contrôles OLE.

## Étape 2 : Insérer un bouton de commande OLE avec DocumentBuilder

Le cœur du tutoriel est la méthode `InsertForms2OleControl`. Elle crée un **Forms2 OLE CommandButton** à un emplacement et une taille spécifiques.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
using System.Drawing;

// Create a new blank document and a DocumentBuilder to edit it
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Define the rectangle where the button will appear (x, y, width, height)
// Values are in points (1 point = 1/72 inch)
Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

// Insert the Forms2 OLE CommandButton control
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // <-- OleControlType CommandButton (secondary keyword)
    buttonRect);

// Set the button's caption and name properties
commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";
```

### Pourquoi cela fonctionne

* `DocumentBuilder` est l’API principale pour créer des documents Word de façon programmatique.  
* `InsertForms2OleControl` indique à Aspose.Words d’intégrer un **contrôle Forms2 OLE**, qui est la technologie de formulaire Word héritée prenant en charge les boutons de commande, les cases à cocher, etc.  
* La valeur d’enum `OleControlType.CommandButton` spécifie que le contrôle inséré est un **bouton de commande** — le type exact que vous avez demandé en voulant **insérer un bouton de commande OLE**.  
* Le `Rectangle` détermine le placement visuel. Ajustez les coordonnées X/Y ou la largeur/hauteur pour correspondre à votre mise en page.

## Étape 3 : Enregistrer le document

Après avoir configuré le bouton, écrivez le document sur le disque. Vous pouvez choisir n’importe quel format pris en charge par Aspose.Words (`.docx`, `.pdf`, `.odt`, …). Pour ce tutoriel, nous enregistrerons au format Word.

```csharp
// Choose a folder you have write access to
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");

// Save the document containing the button
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Lorsque vous ouvrez `CommandButton.docx` dans Microsoft Word, vous verrez un bouton cliquable intitulé **Click Me**. En l’appuyant dans Word, cela déclenche la boîte de dialogue par défaut « Exécuter la macro » car le bouton est un contrôle de formulaire OLE ; vous pouvez ensuite y attacher une macro ou du code VBA si nécessaire.

## Étape 4 : Vérifier le résultat (sortie attendue)

Ouvrez le fichier généré :

1. Le bouton apparaît aux coordonnées que vous avez spécifiées (environ 1,4 po depuis la gauche et le haut de la page).  
2. La légende indique **Click Me**.  
3. La propriété Name (`cmdSubmit`) est visible dans le volet **Développeur → Propriétés** de Word, ce qui est utile lorsque vous devez référencer le contrôle depuis VBA.

![Exemple d'insertion d'un bouton de commande OLE dans un document Word](insert-ole-button.png)

*Texte alternatif de l'image*: **Exemple d'insertion d'un bouton de commande OLE dans un document Word** (inclut le mot‑clé principal pour l'accessibilité et le SEO).

## Cas limites et questions fréquentes

### 1. Que faire si le bouton n’apparaît pas à l’endroit attendu ?

* Word utilise des points, pas des pixels. Convertissez les pixels d’écran en points (`points = pixels * 72 / DPI`).  
* Assurez‑vous que le rectangle n’intersecte pas les marges de la page ; sinon Word peut déplacer le contrôle.

### 2. Puis‑je insérer le bouton dans un document existant ?

Oui. Chargez le document avec `new Document("Existing.docx")` et utilisez le même flux de travail `DocumentBuilder`. N’oubliez pas de déplacer le curseur du builder (`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")`, etc.) avant d’appeler `InsertForms2OleControl`.

### 3. Comment attacher une macro au bouton ?

Aspose.Words ne crée pas de code VBA, mais vous pouvez intégrer une macro après la génération du document :

```csharp
// Load the generated document
Document doc = new Document(outputPath);

// Add a VBA macro module (requires Aspose.Words licensing)
doc.VbaProject.Modules.Add("Module1", "Sub cmdSubmit_Click()\n MsgBox \"Button clicked!\"\nEnd Sub");

// Save again
doc.Save(outputPath);
```

### 4. Cela fonctionne‑t‑il avec .NET Core sous Linux ?

Le contrôle OLE est une fonctionnalité spécifique à Windows car il repose sur COM. Sous Linux, le bouton sera inséré, mais il apparaîtra comme une image statique sans comportement interactif. Pour des formulaires interactifs multiplateformes, envisagez d’utiliser des contrôles de contenu (`StructuredDocumentTag`) à la place.

### 5. Que faire si j’ai besoin d’une taille différente ou de plusieurs boutons ?

Créez des objets `Rectangle` supplémentaires avec des coordonnées uniques et répétez l’appel `InsertForms2OleControl`. Chaque bouton peut avoir son propre `Caption` et `Name`.

## Exemple complet fonctionnel

Ci‑dessous se trouve le programme complet que vous pouvez copier‑coller dans une application console. Il inclut toutes les directives `using` nécessaires, la gestion des erreurs et les commentaires.

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

namespace OleCommandButtonDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document
                Document document = new Document();
                DocumentBuilder builder = new DocumentBuilder(document);

                // 2️⃣ Define button rectangle (x, y, width, height) in points
                Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

                // 3️⃣ Insert the Forms2 OLE CommandButton control
                Forms2OleControl commandButton = builder.InsertForms2OleControl(
                    OleControlType.CommandButton,
                    buttonRect);

                // 4️⃣ Set visual properties
                commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
                commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";

                // 5️⃣ Save the document
                string outputPath = Path.Combine(
                    Environment.CurrentDirectory,
                    "CommandButton.docx");

                document.Save(outputPath);
                Console.WriteLine($"Document saved successfully: {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Error: {ex.Message}");
            }
        }
    }
}
```

Exécutez le programme, ouvrez le `CommandButton.docx` généré, et vous verrez le bouton **Click Me** prêt pour une personnalisation supplémentaire.

## Conclusion

Vous savez maintenant comment **insérer un bouton de commande OLE** dans un document Word en utilisant C# et Aspose.Words. Le tutoriel a couvert :

* Installation du package Aspose.Words  
* Utilisation de `DocumentBuilder.InsertForms2OleControl` avec `OleControlType.CommandButton`  
* Définition des propriétés du bouton (`Caption`, `Name`)  
* Enregistrement et vérification du résultat  

À partir de là, vous pouvez explorer des sujets connexes tels que **Aspose.Words OLE control** pour les cases à cocher, les listes déroulantes ou l’intégration de feuilles de calcul Excel complètes. Vous pouvez également expérimenter l’automatisation du **bouton de commande OLE Word** dans des modèles plus grands, ou remplacer les contrôles OLE par des **contrôles de contenu** modernes pour un meilleur support multiplateforme.

N’hésitez pas à adapter les valeurs du rectangle, ajouter plusieurs boutons ou attacher des macros VBA pour répondre aux besoins de votre application. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Insérer un objet Ole dans un document Word](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object/)
- [Insérer un objet Ole dans un document Word en tant qu’icône](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-as-icon/)
- [Insérer un objet Ole dans Word avec le package Ole](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-with-ole-package/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}