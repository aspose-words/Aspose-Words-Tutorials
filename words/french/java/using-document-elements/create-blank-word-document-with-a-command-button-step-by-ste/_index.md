---
category: general
date: 2026-08-04
description: Créer un document Word vierge et insérer un bouton de commande à l'aide
  d'Aspose.Words. Apprenez à définir la taille du bouton et à ajouter un bouton cliquable
  en C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert command button
- add clickable button
- set button size
- create command button
language: fr
lastmod: 2026-08-04
og_description: Créer un document Word vierge avec Aspose.Words et insérer un bouton
  de commande. Ce guide montre comment définir la taille du bouton, ajouter un bouton
  cliquable et enregistrer le fichier.
og_image_alt: Screenshot of a Word document containing a clickable command button
  created with C#
og_title: Créer un document Word vierge et ajouter un bouton de commande – tutoriel
  complet C#
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  headline: Create blank word document with a command button – step‑by‑step guide
  type: TechArticle
- description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  name: Create blank word document with a command button – step‑by‑step guide
  steps:
  - name: The ProgID of the OLE control – `"CommandButton"` for a standard button.
    text: The ProgID of the OLE control – `"CommandButton"` for a standard button.
  - name: A `Rectangle` that defines the **set button size** and position.
    text: A `Rectangle` that defines the **set button size** and position.
  - name: The caption that appears on the button.
    text: The caption that appears on the button.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Créer un document Word vierge avec un bouton de commande – guide étape par
  étape
url: /fr/java/using-document-elements/create-blank-word-document-with-a-command-button-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un document Word vierge avec un bouton de commande – guide étape par étape

Si vous devez **créer un document Word vierge** contenant un bouton interactif, ce tutoriel vous montre exactement comment le faire avec Aspose.Words for .NET. Vous apprendrez à **insérer un bouton de commande**, à ajuster son apparence et à le rendre cliquable — le tout en quelques lignes de C#.

Le guide couvre tout, de la configuration du projet à l’enregistrement du fichier final, afin que vous puissiez copier‑coller la solution complète dans votre propre application. En cours de route, nous expliquerons également comment **ajouter un bouton cliquable**, **définir la taille du bouton** et **créer un bouton de commande** de façon programmatique.

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

* SDK .NET 6.0 ou version ultérieure installé.
* Visual Studio 2022 (ou tout IDE supportant .NET).
* Package NuGet Aspose.Words for .NET (`Aspose.Words` version 23.12 ou plus récent).
* Une connaissance de base du C# et de la programmation orientée objet.

Aucun assembly d’interop Office supplémentaire n’est requis car Aspose.Words fonctionne de manière totalement indépendante de Microsoft Word.

## Étape 1 : Configurer le projet .NET

Créez une application console qui hébergera le code d’automatisation Word.

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

Cette commande crée un nouveau dossier `WordButtonDemo` avec un `Program.cs` prêt à l’exécution et ajoute la bibliothèque Aspose.Words.

## Étape 2 : Créer un document Word vierge

La première opération consiste à **créer un document Word vierge**. Aspose.Words fournit une classe `Document` qui représente un fichier Word vide dès le départ.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a new, empty Word document.
Document doc = new Document();
```

Créer un document vierge vous donne une toile propre sur laquelle vous pouvez ajouter des paragraphes, des tableaux ou, dans ce cas, un bouton de commande OLE.

## Étape 3 : Initialiser DocumentBuilder

`DocumentBuilder` est l’assistant qui vous permet d’insérer du contenu dans le document. Vous devez le lier au document que vous venez de créer.

```csharp
// Attach a DocumentBuilder to the empty document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Le builder maintient la position actuelle du curseur, de sorte que toute insertion ultérieure se fasse exactement à l’endroit souhaité.

## Étape 4 : Insérer un bouton de commande

Nous **insérons maintenant un bouton de commande** (un `Forms2OleControl` OLE) dans le document. La méthode `InsertForms2OleControl` nécessite trois arguments :

1. Le ProgID du contrôle OLE – `"CommandButton"` pour un bouton standard.
2. Un `Rectangle` qui définit la **définition de la taille du bouton** et la position.
3. La légende qui apparaît sur le bouton.

```csharp
// Define the button's position (x, y) and size (width, height).
Rectangle buttonRect = new Rectangle(0, 0, 120, 30); // 120 px wide, 30 px high

// Insert the command button with the desired caption.
Forms2OleControl cmdButton = builder.InsertForms2OleControl(
    "CommandButton",   // ProgID for a CommandButton control
    buttonRect,        // Position and size
    "Click Me");       // Caption displayed on the button
```

Lorsque le document est ouvert dans Word, le bouton se comporte comme n’importe quel contrôle de formulaire natif : vous pouvez le cliquer, et Word déclenchera la macro associée (si elle existe). Cela satisfait le besoin d’**ajouter un bouton cliquable**.

### Pourquoi utiliser Forms2OleControl ?

`Forms2OleControl` intègre un objet OLE directement dans le fichier DOCX, préservant les propriétés du contrôle sans nécessiter l’assembly Word Interop. C’est la méthode la plus fiable pour **créer un bouton de commande** fonctionnant sur toutes les versions de Word.

## Étape 5 : Personnaliser le bouton (optionnel)

Vous pourriez vouloir **définir la taille du bouton** de façon plus précise ou modifier d’autres propriétés comme la police ou la couleur d’arrière‑plan. Aspose.Words expose l’objet OLE sous‑jacent, permettant des ajustements supplémentaires.

```csharp
// Example: change the button's background color (requires OLE automation).
// Note: This step is optional and demonstrates additional customization.
cmdButton.OleFormat.Icon = true; // Show an icon instead of the default appearance.
```

Si vous avez besoin d’une taille différente, ajustez simplement les valeurs du `Rectangle` à l’Étape 4. Les coordonnées sont exprimées en points (1 pt = 1/72 pouce), ainsi `120` correspond à environ 1,67 pouces de largeur.

## Étape 6 : Enregistrer le document

Enfin, écrivez le document sur le disque. Le fichier résultant contient un **document Word vierge** avec un bouton de commande pleinement fonctionnel.

```csharp
// Save the document as a .docx file.
doc.Save("CommandButtonDemo.docx");
```

Lorsque vous ouvrez `CommandButtonDemo.docx` dans Microsoft Word, vous verrez un bouton libellé « Click Me ». Cliquer sur le bouton affichera la boîte de dialogue de macro par défaut, sauf si vous y attachez une macro personnalisée.

## Code source complet

Vous trouverez ci‑dessous le programme complet que vous pouvez copier dans `Program.cs`. Il inclut toutes les étapes décrites ci‑above et se compile sans modification.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordButtonDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 2: Create a blank word document.
            Document doc = new Document();

            // Step 3: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 4: Define button size and insert command button.
            Rectangle buttonRect = new Rectangle(0, 0, 120, 30);
            Forms2OleControl cmdButton = builder.InsertForms2OleControl(
                "CommandButton",
                buttonRect,
                "Click Me");

            // Optional: further customization (e.g., set icon).
            // cmdButton.OleFormat.Icon = true;

            // Step 6: Save the document.
            doc.Save("CommandButtonDemo.docx");

            System.Console.WriteLine("Document created successfully.");
        }
    }
}
```

### Résultat attendu

L’exécution du programme produit `CommandButtonDemo.docx`. L’ouverture du fichier dans Word montre :

* Une page unique contenant un bouton libellé **Click Me**.
* Le bouton respecte la **définition de la taille du bouton** (120 × 30 points).
* Cliquer sur le bouton déclenche le comportement par défaut du bouton de commande Word, confirmant que l’opération **ajouter un bouton cliquable** a réussi.

## Questions fréquentes et cas particuliers

| Question | Réponse |
|----------|--------|
| **Cela fonctionne‑t‑il avec les fichiers .doc ?** | Oui. Changez l’extension du fichier dans `doc.Save("file.doc")`. Le contrôle OLE est également stocké dans le format binaire hérité. |
| **Et si j’ai besoin de plusieurs boutons ?** | Appelez `InsertForms2OleControl` plusieurs fois, en ajustant le `Rectangle` pour chaque nouveau bouton afin d’éviter les chevauchements. |
| **Puis‑je attacher une macro au bouton ?** | Le bouton lui‑même ne contient pas de code macro. Vous devez ajouter une macro VBA au document manuellement ou via la collection `Modules` de l’objet `Document`. |
| **Le bouton est‑il visible lors de l’exportation en PDF ?** | Lors de l’exportation du DOCX vers PDF avec Aspose.Words, le bouton est rendu comme une image statique, pas comme un contrôle interactif. |
| **Quelles versions de Word sont prises en charge ?** | Le bouton de commande OLE fonctionne dans Word 2007 et versions ultérieures, car il suit la spécification standard Forms2.0. |

## Conclusion

Vous savez maintenant comment **créer un document Word vierge**, **insérer un bouton de commande**, **ajouter un bouton cliquable** et **définir la taille du bouton** en utilisant Aspose.Words for .NET. L’exemple complet illustre le flux de travail **créer un bouton de commande** du début à la fin, vous offrant une base solide pour des tâches d’automatisation Word plus avancées.

## Étapes suivantes

* Explorez d’autres contrôles OLE (par ex., `CheckBox`, `ListBox`) en modifiant le ProgID dans `InsertForms2OleControl`.
* Combinez le bouton avec une macro VBA pour exécuter des actions personnalisées lorsque l’utilisateur clique dessus.
* Utilisez `DocumentBuilder` d’Aspose.Words pour ajouter du contenu supplémentaire tel que des tableaux, des images ou des notes de bas de page avant d’insérer le bouton.
* Expérimentez avec les valeurs de **définition de la taille du bouton** pour les adapter aux exigences de mise en page de votre document.

Bon codage, et profitez de la création de documents Word plus riches avec des contrôles interactifs !

## Que devriez‑vous apprendre ensuite ?


Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser d’autres fonctionnalités de l’API et à explorer des approches d’implémentation alternatives dans vos projets.

- [Créer une forme de groupe dans un document Word avec Aspose.Words pour .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Créer un document Word vierge avec une forme rectangle ombrée – Guide étape par étape](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Créer un document Word avec Aspose.Words pour .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}