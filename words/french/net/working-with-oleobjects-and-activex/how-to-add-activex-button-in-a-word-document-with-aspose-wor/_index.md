---
category: general
date: 2026-08-14
description: Comment ajouter un bouton ActiveX dans un document Word à l'aide d'Aspose.Words
  – apprenez à créer un document Word vierge et à insérer un bouton ActiveX par programmation.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert activex button
- create empty word document
- create word document aspose
language: fr
lastmod: 2026-08-14
og_description: Comment ajouter un bouton ActiveX dans un document Word avec Aspose.Words.
  Ce tutoriel vous montre comment créer un document Word vierge, insérer un bouton
  ActiveX et enregistrer le résultat.
og_image_alt: Screenshot of an ActiveX button inserted into a Word document using
  Aspose.Words
og_title: Comment ajouter un bouton ActiveX dans Word – Guide Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  headline: How to add ActiveX button in a Word document with Aspose.Words
  type: TechArticle
- description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  name: How to add ActiveX button in a Word document with Aspose.Words
  steps:
  - name: Does the button work in all Word versions?
    text: ActiveX controls are supported in the desktop version of Word on Windows.
      They are not rendered in Word Online, Word for macOS, or mobile clients. If
      you need cross‑platform interactivity, consider using content controls or HTML‑based
      solutions instead.
  - name: What if I need a different size or position?
    text: '`InsertForms2OleControl` places the control at the current builder cursor.
      To move it, adjust the cursor with `builder.MoveTo` before insertion, or modify
      the control’s `Left` and `Top` properties after creation:'
  - name: Can I add other ActiveX types?
    text: Yes. The `Forms2OleControlType` enumeration includes `CheckBox`, `OptionButton`,
      `ListBox`, and more. Replace `CommandButton` with the desired enum value and
      adjust properties accordingly.
  - name: Is a macro required for the button to do something?
    text: The button itself does nothing until you attach VBA code. In Word, press
      **Alt+F11** to open the VBA editor, locate `btnSubmit_Click`, and write the
      desired logic. The generated document will retain the VBA project if you enable
      the **SaveFormat.Doc** (legacy `.doc`) format, but `.docx` files cannot
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- Word automation
- C#
title: Comment ajouter un bouton ActiveX dans un document Word avec Aspose.Words
url: /fr/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment ajouter un bouton ActiveX dans un document Word avec Aspose.Words

Si vous devez **how to add ActiveX** controls à un fichier Word généré, ce guide vous montre les étapes exactes. Vous apprendrez à **insert ActiveX button** de façon programmatique, en partant d’un **create empty Word document** et en terminant par un fichier enregistré qui peut être ouvert dans Microsoft Word.

Ajouter un bouton qui exécute du code VBA ou déclenche une macro est une exigence courante pour les générateurs de rapports automatisés, les modèles de formulaires ou les contrats interactifs. Utiliser Aspose.Words pour .NET vous permet de créer le document sans lancer Office, ce qui rend le processus rapide et adapté aux serveurs.

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

* .NET 6.0 (ou version ultérieure) SDK installé.  
* Visual Studio 2022 ou tout IDE compatible C#.  
* Le package NuGet Aspose.Words for .NET (`Aspose.Words` version 24.9 ou plus récent).  
  Installez‑le avec :
  ```bash
  dotnet add package Aspose.Words
  ```
* Un environnement Windows si vous prévoyez de tester le bouton ActiveX, car les contrôles ActiveX nécessitent la version Windows de Microsoft Word.

## Étape 1 : Créer un document Word vide

La première tâche consiste à **create empty Word document** en mémoire. Aspose.Words fournit la classe `Document` à cet effet.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, blank Word document.
Document doc = new Document();
```

`Document` représente l’ensemble du fichier .docx. À ce stade, le document ne contient aucune page, mais vous pouvez commencer à ajouter du contenu immédiatement.

## Étape 2 : Initialiser un DocumentBuilder

`DocumentBuilder` est un assistant qui vous permet d’insérer du texte, des images et d’autres objets dans le document. Il travaille sur l’instance `Document` que vous venez de créer.

```csharp
// Initialise the builder with the blank document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Le builder maintient une position de curseur ; tout ce que vous insérez après cette ligne apparaît au début de la première page.

## Étape 3 : Insérer un contrôle ActiveX CommandButton

Aspose.Words expose la méthode `InsertForms2OleControl` pour ajouter des contrôles de formulaire hérités, y compris ActiveX. La méthode nécessite le type de contrôle et sa taille en points.

```csharp
// Insert an ActiveX CommandButton (150x30 points).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton, 150, 30);
```

L’objet `Forms2OleControl` retourné vous permet de configurer des propriétés telles que le nom et la légende du contrôle.

## Étape 4 : Configurer les propriétés du bouton

Définir un `Name` significatif vous permet de référencer le contrôle depuis le code VBA ultérieurement. La `Caption` est le texte que l’utilisateur voit sur le bouton.

```csharp
// Set the button’s programmatic name (used in VBA) and displayed caption.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

> **Astuce** : Gardez le nom court et alphanumérique ; Word rejettera les noms contenant des espaces ou des caractères spéciaux.

## Étape 5 : Enregistrer le document

Enfin, écrivez le document sur le disque. Utilisez l’extension `.docx` pour les fichiers Word modernes ; le bouton ActiveX fonctionne de la même façon dans les fichiers `.doc`, mais le format `.docx` est préféré pour les nouveaux projets.

```csharp
// Save the document containing the ActiveX button.
doc.Save(@"C:\Temp\ActiveXButton.docx");
```

Lorsque vous ouvrez `ActiveXButton.docx` dans Microsoft Word, vous verrez un bouton **Submit** cliquable. Si vous activez les macros, vous pouvez attacher du code VBA à `btnSubmit_Click` et le faire exécuter lorsque l’utilisateur clique sur le bouton.

## Exemple complet et exécutable

Assembler toutes les pièces vous donne un programme autonome que vous pouvez copier, coller et exécuter.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create an empty Word document.
            Document doc = new Document();

            // Step 2: Initialise DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Insert an ActiveX CommandButton control.
            Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, 150, 30);

            // Step 4: Set button properties.
            cmdBtn.Name = "btnSubmit";
            cmdBtn.Caption = "Submit";

            // Step 5: Save the document.
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Résultat attendu** – Après l’exécution du programme, la console affiche l’emplacement d’enregistrement, et l’ouverture du fichier généré dans Word montre un bouton libellé **Submit** positionné en haut de la première page.

## Gestion des questions courantes et des cas limites

### Le bouton fonctionne-t-il dans toutes les versions de Word ?

Les contrôles ActiveX sont pris en charge dans la version de bureau de Word sous Windows. Ils ne sont pas rendus dans Word Online, Word pour macOS ou les clients mobiles. Si vous avez besoin d’interactivité multiplateforme, envisagez d’utiliser des contrôles de contenu ou des solutions basées sur HTML à la place.

### Et si j’ai besoin d’une taille ou d’une position différente ?

`InsertForms2OleControl` place le contrôle au curseur actuel du builder. Pour le déplacer, ajustez le curseur avec `builder.MoveTo` avant l’insertion, ou modifiez les propriétés `Left` et `Top` du contrôle après sa création :

```csharp
cmdBtn.Left = 100;   // points from the left margin
cmdBtn.Top = 200;    // points from the top margin
```

### Puis‑je ajouter d’autres types d’ActiveX ?

Oui. L’énumération `Forms2OleControlType` comprend `CheckBox`, `OptionButton`, `ListBox`, et plus encore. Remplacez `CommandButton` par la valeur d’énumération souhaitée et ajustez les propriétés en conséquence.

### Une macro est‑elle requise pour que le bouton fasse quelque chose ?

Le bouton lui‑même ne fait rien tant que vous n’attachez pas du code VBA. Dans Word, appuyez sur **Alt+F11** pour ouvrir l’éditeur VBA, localisez `btnSubmit_Click` et écrivez la logique désirée. Le document généré conservera le projet VBA si vous activez le format **SaveFormat.Doc** (format hérité `.doc`), mais les fichiers `.docx` ne peuvent pas stocker de macros VBA. Utilisez le format `.doc` si vous avez besoin de VBA intégré.

## Conclusion

Vous savez maintenant **how to add ActiveX** controls à un fichier Word en utilisant Aspose.Words. En suivant les étapes pour **create empty Word document**, initialiser un `DocumentBuilder`, **insert ActiveX button**, configurer ses propriétés et enregistrer le fichier, vous pouvez générer des modèles Word interactifs directement depuis votre code .NET.

Ensuite, explorez des sujets connexes tels que la gestion des événements **insert ActiveX button**, l’ajout de **create word document aspose** pour les tableaux ou les images, et la sécurisation des documents activés par macro pour le déploiement en entreprise. Expérimentez avec différents types de contrôles et options de mise en page pour adapter l’expérience utilisateur aux besoins de votre application.

Bonne programmation !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Créer un document Word avec en‑tête et pied de page en utilisant Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Créer une forme groupée dans un document Word en utilisant Aspose.Words pour .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Créer un document Word avec un tableau en utilisant Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}