---
category: general
date: 2026-10-10
description: Définir le texte du bouton et ajouter un bouton ActiveX en C# avec Aspose.Words.
  Apprenez comment insérer un bouton, créer un contrôle de bouton et personnaliser
  la légende dans un document Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button text
- how to insert button
- create button control
- add activex control
- add activex button
language: fr
lastmod: 2026-10-10
og_description: Définissez le texte du bouton et ajoutez un bouton ActiveX en C# avec
  Aspose.Words. Suivez ce guide étape par étape pour insérer un bouton, créer le contrôle
  du bouton et personnaliser sa légende.
og_image_alt: Screenshot of a Word document showing an ActiveX button with custom
  text
og_title: Définir le texte d’un bouton et ajouter un bouton ActiveX en C# – guide
  complet
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Set button text and add an ActiveX button in C# using Aspose.Words.
    Learn how to insert button, create button control, and customize the caption in
    a Word document.
  headline: Set button text and add an ActiveX button in C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- button control
- document automation
title: Définir le texte du bouton et ajouter un bouton ActiveX en C#
url: /fr/java/document-manipulation/set-button-text-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Définir le texte du bouton et ajouter un bouton ActiveX en C#

Si vous devez **définir le texte du bouton** sur un bouton ActiveX dans un document Word, ce guide vous montre exactement comment faire. À la fin du tutoriel, vous serez capable **d’insérer un bouton**, de créer un **contrôle de bouton**, et de personnaliser sa légende avec seulement quelques lignes de code C#.

Travailler avec les contrôles ActiveX est courant lorsque vous souhaitez des formulaires interactifs dans Word — que vous construisiez un modèle de contrat, un questionnaire ou un outil interne. L’exemple utilise Aspose.Words pour .NET, une bibliothèque qui vous permet de manipuler des fichiers Word sans avoir Microsoft Office installé.

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

* SDK .NET 6.0 ou version ultérieure installé  
* Visual Studio 2022 (ou tout IDE supportant C#)  
* Une licence Aspose.Words pour .NET (l’évaluation gratuite suffit pour l’apprentissage)  

Vous avez également besoin d’une référence au package NuGet `Aspose.Words` :

```bash
dotnet add package Aspose.Words
```

## Comment insérer un bouton dans un document Word

La première étape consiste à créer un nouveau `Document` et un `DocumentBuilder`. Le builder est le point d’entrée pour ajouter du contenu, y compris les contrôles ActiveX.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Pourquoi c’est important :** `Document` représente le fichier .docx complet, tandis que `DocumentBuilder` fournit des méthodes de haut niveau comme `InsertParagraph` et `InsertFormField`. Commencer avec un document vierge garantit que le bouton apparaît exactement à l’endroit souhaité.

## Créer un contrôle de bouton avec Forms2OleControl

Nous créons maintenant le véritable contrôle de bouton. `Forms2OleControl` est la classe qu’Aspose.Words utilise pour tous les objets ActiveX, et le type `COMMANDBUTTON` s’affiche comme un bouton cliquable dans Word.

```csharp
        // Step 2: Insert a Forms2OleControl of type COMMANDBUTTON
        Forms2OleControl button = builder.InsertForms2OleControl(
            Forms2OleControlType.COMMANDBUTTON, // control type
            100,  // left position (points)
            50,   // top position (points)
            200,  // width (points)
            150); // height (points)
```

**Explication :**  
* `InsertForms2OleControl` place le contrôle aux coordonnées exactes que vous fournissez.  
* La taille est définie en points (1 point = 1/72 pouce). Ajustez ces valeurs pour correspondre à votre mise en page.

## Ajouter le contrôle ActiveX et lui attribuer un nom unique

Chaque objet ActiveX doit avoir un nom distinct afin que vous puissiez le référencer plus tard (par exemple, lors du traitement d’événements en VBA).

```csharp
        // Step 3: Assign a unique name to the control
        button.SetName("MyActiveXButton");
```

**Astuce :** Évitez les espaces ou les caractères spéciaux dans le nom ; Word traite le nom comme un identifiant dans son modèle de formulaire interne.

## Définir le texte du bouton (légende) sur le bouton ActiveX

C’est ici que le mot‑clé principal **set button text** entre en jeu. La propriété `Caption` définit le libellé que les utilisateurs voient sur le bouton.

```csharp
        // Step 4: Set the text that appears on the button
        button.SetCaption("Click Me");
```

Vous pouvez modifier la légende à tout moment avant d’enregistrer le document. Si vous devez plus tard localiser l’interface, appelez simplement `SetCaption` à nouveau avec une chaîne différente.

## Enregistrer le document et vérifier le résultat

Enfin, écrivez le document sur le disque. L’ouverture du fichier dans Microsoft Word affichera le bouton avec la légende personnalisée.

```csharp
        // Step 5: Save the document
        doc.Save("ActiveXButton.docx");
        System.Console.WriteLine("Document created with an ActiveX button.");
    }
}
```

**Résultat attendu :** Lorsque vous ouvrez *ActiveXButton.docx* dans Word, vous verrez un bouton positionné aux coordonnées spécifiées, libellé **Click Me**. Cliquer sur le bouton déclenchera le comportement par défaut du bouton de commande Word (que vous pourrez personnaliser plus tard avec VBA).

![Set button text example](https://example.com/activex-button.png){alt="Exemple de définition du texte du bouton"}

## Ajouter un bouton ActiveX et gérer les événements (optionnel)

Si vous avez besoin que le bouton exécute une action personnalisée, vous pouvez ajouter une macro VBA qui réagit à l’événement `Click`. La macro peut être injectée programmatiquement, mais cela dépasse le cadre de ce tutoriel. L’important est que le bouton soit déjà présent et que sa légende soit définie — prêt pour tout traitement d’événement que vous choisirez.

## Pièges courants et comment les éviter

| Problème | Pourquoi cela se produit | Solution |
|----------|--------------------------|----------|
| Le bouton apparaît mal aligné | Les coordonnées sont en points, pas en pixels | Convertir les valeurs en pixels en points (`points = pixels * 72 / DPI`) |
| La légende ne change pas après l’enregistrement | `SetCaption` appelé après `Save` | Toujours définir la légende **avant** d’appeler `doc.Save` |
| Le contrôle n’est pas visible dans les versions plus anciennes de Word | Certaines versions anciennes de Word ne supportent pas pleinement ActiveX | Tester sur la version cible de Word ; envisager d’utiliser un `CheckBox` ou `DropDownList` comme solution de secours |
| Avertissement de licence dans la sortie | La licence d’évaluation expire | Appliquer une licence Aspose.Words valide via `License license = new License(); license.SetLicense("Aspose.Words.lic");` |

## Exemple complet, exécutable

Voici le programme complet que vous pouvez copier, coller et exécuter. Il inclut toutes les directives `using` nécessaires et montre le flux complet, de la création du document à son enregistrement.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXButtonDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert an ActiveX command button at a specific location
            Forms2OleControl button = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON,
                100,   // left (points)
                50,    // top (points)
                200,   // width (points)
                150);  // height (points)

            // Give the button a unique identifier
            button.SetName("MyActiveXButton");

            // Set the visible text on the button (set button text)
            button.SetCaption("Click Me");

            // Save the document
            const string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}. Open it in Word to see the button.");
        }
    }
}
```

Exécutez le programme avec `dotnet run`. Après l’exécution, ouvrez *ActiveXButton.docx* pour confirmer que la légende du bouton indique **Click Me**.

## Récapitulatif de ce que vous avez appris

* Vous avez appris comment **set button text** sur un bouton ActiveX en utilisant Aspose.Words.  
* Vous avez vu les étapes exactes pour **how to insert button**, **create button control**, et **add activex control** dans un document Word.  
* Vous disposez maintenant d’un extrait de code réutilisable que vous pouvez adapter à tout projet d’automatisation Word basé sur des formulaires.

## Prochaines étapes

* Explorer d’autres valeurs `Forms2OleControlType` comme `CHECKBOX` ou `LISTBOX` pour créer des formulaires plus riches.  
* Combiner le bouton avec une macro VBA pour effectuer des calculs ou des validations de données.  
* Utiliser l’API `FormField` d’Aspose.Words pour lire les entrées utilisateur après que le document a été rempli.

N’hésitez pas à expérimenter la taille, la position et la légende afin qu’elles correspondent à vos exigences de conception. Si vous rencontrez des problèmes, la documentation d’Aspose.Words fournit des références détaillées pour chaque classe utilisée dans ce tutoriel.

Bon codage !

## Que devez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser des fonctionnalités API supplémentaires et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Add Shadow to Shape in Word with Aspose.Words – Step‑by‑Step](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)
- [Add Page Numbers to the Footer of a Word Document Using Aspose.Words for .NET](/words/english/net/working-with-headers-and-footers/add-page-numbers/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}