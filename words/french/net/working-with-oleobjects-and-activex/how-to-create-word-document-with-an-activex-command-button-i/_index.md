---
category: general
date: 2026-09-05
description: Créer un document Word avec Aspose.Words en C# et apprendre comment insérer
  un bouton de commande ActiveX, définir la taille du bouton et ajouter une fonctionnalité
  interactive au bouton.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to insert activex
- add command button
- add interactive button
- set button size
language: fr
lastmod: 2026-09-05
og_description: Créer un document Word en C# et insérer un bouton de commande ActiveX.
  Ce tutoriel montre comment définir la taille du bouton et ajouter des fonctionnalités
  interactives au bouton.
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
  created with C#
og_title: Créer un document Word avec un bouton de commande ActiveX en C# – guide
  étape par étape
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  headline: How to create Word document with an ActiveX command button in C#
  type: TechArticle
- description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  name: How to create Word document with an ActiveX command button in C#
  steps:
  - name: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
    text: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
  - name: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
    text: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
  - name: '**Configure the button** – caption, size, and position.'
    text: '**Configure the button** – caption, size, and position.'
  - name: '**Save** the document to disk.'
    text: '**Save** the document to disk.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
- UI controls
title: Comment créer un document Word avec un bouton de commande ActiveX en C#
url: /fr/net/working-with-oleobjects-and-activex/how-to-create-word-document-with-an-activex-command-button-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer un document Word avec un bouton de commande ActiveX en C#

Si vous devez **créer un document Word** de manière programmatique et intégrer un élément d'interface cliquable, ce guide vous montre exactement comment procéder. En utilisant Aspose.Words pour .NET, vous pouvez **créer un document Word**, **ajouter un bouton de commande**, et contrôler son apparence — le tout sans ouvrir Microsoft Word.

Vous apprendrez **comment insérer des contrôles ActiveX**, **définir la taille du bouton**, et faire en sorte que le bouton se comporte comme un composant d'interface interactif. Aucune expérience préalable avec COM ou VBA n'est requise ; il suffit d'un environnement de développement .NET et de la bibliothèque Aspose.Words.

## Ce que vous allez réaliser

À la fin de ce tutoriel, vous pourrez :

* **Créer un document Word** à partir de zéro avec C#.
* **Insérer un bouton de commande ActiveX** (le contrôle classique « Click Me »).
* **Définir la taille du bouton** et sa position avec précision.
* Ajouter éventuellement une logique simple de **bouton interactif** (par ex., un espace réservé pour une macro).
* Enregistrer le fichier au format `.docx` qui peut être ouvert dans Microsoft Word ou tout visualiseur compatible.

### Prérequis

| Exigence | Raison |
|-------------|--------|
| .NET 6.0 ou version ultérieure | Fournit le runtime pour le code C#. |
| Aspose.Words pour .NET (dernière version) | Fournit les API `Document`, `DocumentBuilder` et `Forms2OleControl` utilisées dans l'exemple. |
| Visual Studio 2022 (ou tout IDE C#) | Facilite la compilation et l'exécution de l'exemple. |
| Connaissances de base en C# | Nécessaires pour comprendre le flux du code. |

> **Astuce :** Si vous utilisez une version d'évaluation d'Aspose.Words, assurez‑vous de définir la licence avant d'exécuter le code afin d'éviter les filigranes d'évaluation.

## Comment créer un document Word – flux de travail global

Le processus se compose de quatre étapes logiques :

1. **Initialiser un nouveau document** et un `DocumentBuilder` pour le modifier.  
2. **Insérer un bouton de commande ActiveX** à l'aide de `InsertForms2OleControl`.  
3. **Configurer le bouton** – légende, taille et position.  
4. **Enregistrer** le document sur le disque.

Chaque étape est expliquée dans sa propre section ci‑dessous.

![Document Word avec un bouton ActiveX](/images/activex-button.png "Capture d'écran d'un document Word contenant un bouton de commande ActiveX créé avec C#")

## Comment insérer un bouton de commande ActiveX

La partie **comment insérer activex** commence avec la méthode `InsertForms2OleControl`. Cette méthode crée un contrôle basé sur COM que Word considère comme un objet ActiveX.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// 1️⃣ Create a blank document and a builder.
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 2️⃣ Insert an ActiveX CommandButton control.
//    Parameters: control type, width, height, left, top (all in points).
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // ActiveX type
    150,                           // Width (points)
    100,                           // Height (points)
    50,                            // Left offset from page margin
    50);                           // Top offset from page margin
```

**Pourquoi cela fonctionne :** `OleControlType.CommandButton` indique à Aspose.Words de créer le bouton classique de style VB. La taille et la position sont exprimées en points (1 point = 1/72 pouce), ce qui offre un contrôle précis de la mise en page.

## Comment ajouter un bouton de commande et définir la taille du bouton

Après l'insertion du contrôle, vous pouvez ajuster ses propriétés visuelles. L'étape **ajouter un bouton de commande** couvre également **définir la taille du bouton**.

```csharp
// 3️⃣ Set the button's caption – the text the user sees.
commandButton.Caption = "Click Me";

// 4️⃣ Optionally change size after insertion (if you need dynamic sizing).
//    Width and height are mutable properties.
commandButton.Width = 200;   // New width in points
commandButton.Height = 80;   // New height in points

// 5️⃣ Move the button if you need a different position.
commandButton.Left = 100;    // New left offset
commandButton.Top = 120;     // New top offset
```

**Explication :**  

* `Caption` est le libellé affiché sur le bouton.  
* `Width` et `Height` vous permettent de **définir la taille du bouton** après l'insertion initiale — utile lorsque la taille dépend de données d'exécution.  
* `Left` et `Top` repositionnent le contrôle sans recréer le document.

> **Erreur fréquente :** Oublier d'utiliser des points au lieu de pixels fera apparaître le bouton trop petit ou trop grand. Convertissez toujours les valeurs en pixels (`px * 72 / DPI`) si vous partez de mesures d'écran.

## Comment ajouter un bouton interactif (optionnel)

Un bouton ActiveX peut exécuter une macro lorsqu'il est cliqué, mais l'intégration de code VBA depuis C# dépasse le cadre d'un flux de travail purement Aspose.Words. À la place, vous pouvez ajouter une propriété d'espace réservé que Word reconnaîtra comme le nom d'une macro.

```csharp
// 6️⃣ Assign a macro name (the macro must exist in the Word template).
commandButton.OleFormat.Object = "MyMacroName";
```

Lorsque l'utilisateur ouvre le `.docx` généré dans Word, cliquer sur le bouton tentera d'exécuter `MyMacroName`. Si la macro n'existe pas, Word demandera à l'utilisateur de la créer.

**Pourquoi vous pourriez l'utiliser :** Pour les formulaires d'entreprise où une macro remplit les champs, le code C# n'a besoin que de placer le bouton ; la logique de la macro réside dans le projet VBA du document.

## Enregistrer le document et vérifier le résultat

```csharp
// 7️⃣ Save the document to the desired folder.
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), "CommandButton.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

**Sortie attendue :** L'ouverture de `CommandButton.docx` dans Microsoft Word affiche un bouton intitulé **Click Me** positionné à 100 pts du bord gauche et 120 pts du haut. Les dimensions du bouton sont **200 pts × 80 pts**. Cliquer sur le bouton déclenche l'espace réservé de macro (si présent).

## Exemple complet fonctionnel

Ci‑dessous se trouve le programme complet et exécutable qui assemble tous les éléments. Copiez‑le dans un nouveau projet Console App, ajoutez le package NuGet Aspose.Words, puis exécutez.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton, // ActiveX type
            150,                         // Initial width
            100,                         // Initial height
            50,                          // Left offset
            50);                         // Top offset

        // Set button caption and resize.
        commandButton.Caption = "Click Me";
        commandButton.Width = 200;   // Set button size (width)
        commandButton.Height = 80;   // Set button size (height)
        commandButton.Left = 100;    // Re‑position horizontally
        commandButton.Top = 120;     // Re‑position vertically

        // Optional: link to a macro named MyMacroName.
        commandButton.OleFormat.Object = "MyMacroName";

        // Save the document.
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Exécutez le programme, puis ouvrez le fichier généré. Vous verrez le **bouton interactif** prêt à être personnalisé davantage.

## Questions fréquemment posées

| Question | Réponse |
|----------|--------|
| **Cela fonctionne‑t‑il avec .NET Core ?** | Oui. Aspose.Words prend en charge .NET Standard, donc le même code fonctionne sur .NET 5/6/7. |
| **Puis‑je utiliser d’autres contrôles ActiveX (p. ex., CheckBox) ?** | Absolument. Remplacez `OleControlType.CommandButton` par `OleControlType.CheckBox`, `OleControlType.OptionButton`, etc. |
| **Que faire si j’ai besoin d’un bouton plus grand sur une page en orientation paysage ?** | Ajustez les propriétés `Width`, `Height`, `Left` et `Top` proportionnellement. N’oubliez pas que les points restent les mêmes quel que soit l’orientation de la page. |
| **Une macro est‑elle requise pour que le bouton soit cliquable ?** | Non. Le bouton est pleinement fonctionnel en tant qu’élément d’interface ; une macro ajoute seulement un comportement personnalisé lors du clic. |

## Conclusion

Vous savez maintenant comment **créer un document Word** avec Aspose.Words, **ajouter un bouton de commande**, **définir la taille du bouton**, et éventuellement lier le bouton à une macro pour le comportement **ajouter un bouton interactif**. Cette approche vous permet d'automatiser la création de formulaires, de générer des rapports dynamiques, ou de construire des prototypes d'interface basés sur Word directement depuis C#.

Ensuite, vous pourriez explorer :

* **Comment insérer des cases à cocher ActiveX** pour les formulaires d'enquête.  
* **Comment ajouter du contenu texte enrichi** autour du bouton en utilisant `DocumentBuilder`.  
* **Comment protéger le document** tout en conservant le bouton fonctionnel.  

N'hésitez pas à expérimenter différents types de contrôles, tailles et noms de macro pour les adapter à votre scénario spécifique. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l'API et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Créer un document Word avec Aspose.Words pour .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Insérer une image en ligne dans un document Word avec Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Créer un document Word avec un tableau en utilisant Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}