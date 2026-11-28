---
category: general
date: 2026-11-18
description: Créez un document Word vierge et insérez un bouton ActiveX avec C#. Apprenez
  à ajouter le contrôle, à définir la légende du bouton et à enregistrer le fichier.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- how to add control
- insert activex button
- set button caption
language: fr
lastmod: 2026-11-18
og_description: Créez un document Word vierge et insérez un bouton ActiveX en C#.
  Suivez ce tutoriel complet pour ajouter le contrôle, définir la légende du bouton
  et enregistrer le résultat.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX button with
  the caption “Press”
og_title: Créer un document Word vierge et insérer un bouton ActiveX – guide étape
  par étape
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  headline: Create a blank Word document and insert an ActiveX button
  type: TechArticle
- description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  name: Create a blank Word document and insert an ActiveX button
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 or later (the code also works with .NET Framework 4.6+). * Aspose.Words
      for .NET installed (`Install-Package Aspose.Words`). * Basic familiarity with
      C# and Visual Studio or any .NET‑compatible IDE.'
  - name: Tip
    text: 'If you need the button to appear on a specific page, move the builder’s
      cursor first:'
  - name: Expected result
    text: Opening `with_button.docx` in Word shows a blank page with a rectangular
      button labeled **Press**. Clicking the button does nothing by default because
      no VBA macro is attached, but the control is fully functional and can be wired
      to code later.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Créer un document Word vierge et insérer un bouton ActiveX
url: /fr/net/working-with-oleobjects-and-activex/create-a-blank-word-document-and-insert-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un document Word vierge et insérer un bouton ActiveX

Si vous devez **créer un document Word vierge** et placer un bouton ActiveX interactif à l'intérieur, ce guide vous montre exactement comment le faire avec Aspose.Words for .NET. Vous verrez le code complet, comprendrez pourquoi chaque ligne est importante, et apprendrez à **définir la légende du bouton** afin que le contrôle semble prêt pour l'interaction utilisateur.

En plus de l'objectif principal, nous couvrirons **comment insérer ActiveX**, les étapes **comment ajouter un contrôle** à un fichier Word, et les nuances de **insérer un bouton ActiveX** avec une légende personnalisée. À la fin, vous disposerez d'un modèle réutilisable pour tout scénario d'automatisation de documents nécessitant des éléments d'interface intégrés.

## Ce que vous apprendrez

* Comment **créer un document Word vierge** de façon programmatique.  
* Les appels d'API exacts nécessaires pour **insérer un bouton ActiveX** et configurer ses propriétés.  
* Comment **définir la légende du bouton** afin que le contrôle affiche le texte souhaité.  
* Conseils pour enregistrer le fichier à l'emplacement de votre choix et gérer les problèmes courants.

### Prérequis

* .NET 6.0 ou ultérieur (le code fonctionne également avec .NET Framework 4.6+).  
* Aspose.Words for .NET installé (`Install-Package Aspose.Words`).  
* Familiarité de base avec C# et Visual Studio ou tout IDE compatible .NET.

---

## Créer un document Word vierge avec Aspose.Words

La première étape consiste à instancier un objet `Document` vide. Cet objet représente un fichier Word qui ne contient aucun contenu jusqu'à ce que nous ajoutions quelque chose.

```csharp
// Step 1: Create a new blank document
Document document = new Document();
```

*Pourquoi c'est important* : Un `Document` vide vous offre une toile vierge. Vous pouvez ensuite ajouter des paragraphes, des tableaux ou des contrôles sans vous soucier du formatage existant.

---

## Initialiser un DocumentBuilder pour travailler avec le document

`DocumentBuilder` est une classe d'aide qui vous permet d'insérer du contenu à la position actuelle du curseur. Elle suit automatiquement où vous vous trouvez dans le document.

```csharp
// Step 2: Initialise a DocumentBuilder for the empty document
DocumentBuilder builder = new DocumentBuilder(document);
```

*Pourquoi c'est important* : Sans `DocumentBuilder`, vous devriez manipuler manuellement l'arbre de nœuds de bas niveau. Le builder simplifie l'insertion de texte, d'images et de contrôles ActiveX.

---

## Comment insérer un bouton ActiveX (insert activex button)

Nous utilisons maintenant `InsertForms2OleControl` pour intégrer un contrôle ActiveX. La méthode nécessite trois arguments :

1. Le type de contrôle (`OleControlType.CommandButton`).  
2. Un nom interne pour le contrôle (utilisé par VBA ou le code macro).  
3. Un `RectangleF` qui définit la position et la taille sur la page.

```csharp
// Step 3: Insert a CommandButton ActiveX control at the current cursor position
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,          // type of control
    "ClickMe",                             // internal name (identifier)
    new System.Drawing.RectangleF(0, 0, 100, 30)); // x, y, width, height
```

*Pourquoi c'est important* : C’est le cœur de **comment insérer activex** dans un document Word. Les coordonnées du rectangle sont exprimées en points (1 point = 1/72 pouce). Ajustez-les pour positionner le bouton où vous le souhaitez.

### Astuce

Si vous avez besoin que le bouton apparaisse sur une page spécifique, déplacez d'abord le curseur du builder :

```csharp
builder.MoveToSection(0);  // moves to the first (and only) section
builder.InsertParagraph(); // ensures there is a paragraph to host the control
```

---

## Comment définir la légende du bouton (set button caption)

Après avoir placé le contrôle, vous pouvez modifier ses propriétés. La propriété la plus visible est `Caption`, qui détermine le texte affiché sur le bouton.

```csharp
// Step 4: Set the visible caption of the button
commandButton.Caption = "Press";
```

*Pourquoi c'est important* : Les utilisateurs voient la légende, pas le nom interne. La modifier rend le bouton significatif dans le document final.

---

## Enregistrer le document contenant le bouton

Enfin, écrivez le document sur le disque. Vous pouvez choisir n'importe quel format supporté (`.docx`, `.pdf`, etc.). Ici nous enregistrons sous forme de document Word.

```csharp
// Step 5: Save the document with the ActiveX button
string outputPath = @"C:\Temp\with_button.docx";
document.Save(outputPath);
```

*Pourquoi c'est important* : La persistance du fichier vous permet de l'ouvrir dans Microsoft Word et de tester le bouton. Lorsque le document est ouvert, le bouton apparaîtra avec la légende « Press ».

### Résultat attendu

L'ouverture de `with_button.docx` dans Word affiche une page vierge avec un bouton rectangulaire intitulé **Press**. Cliquer sur le bouton ne fait rien par défaut car aucune macro VBA n'est attachée, mais le contrôle est pleinement fonctionnel et peut être relié à du code ultérieurement.

---

## Comment ajouter un contrôle à un paragraphe spécifique (how to add control)

Parfois, vous souhaitez le bouton à l'intérieur d'un paragraphe particulier, par exemple après un texte d'instruction. Utilisez `MoveTo` pour positionner le builder avant d'insérer le contrôle.

```csharp
// Example: add a paragraph, then insert the button after it
builder.Writeln("Click the button below to continue:");
builder.InsertParagraph(); // creates a new empty paragraph
builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    "ContinueBtn",
    new System.Drawing.RectangleF(0, 0, 120, 35));
```

*Pourquoi c'est important* : Ce modèle montre **comment ajouter un contrôle** dans le contexte, assurant que la mise en page du document reste logique.

---

## Pièges courants et comment les éviter

| Problème | Pourquoi cela se produit | Solution |
|----------|--------------------------|----------|
| Le bouton apparaît hors de la page | Les coordonnées du rectangle sont en dehors des marges de la page | Utilisez `builder.PageSetup` pour obtenir les dimensions de la page et calculer un `RectangleF` sûr. |
| La légende ne s'affiche pas | `Caption` défini avant que le contrôle ne soit entièrement initialisé | Définissez `Caption` **après** l'appel à `InsertForms2OleControl`, comme montré à l'étape 4. |
| Le document s'enregistre sans le bouton | Le curseur du builder a été déplacé après l'insertion sans valider les changements | Gardez le builder sur la même page ou appelez `builder.Document.UpdatePageLayout()` avant d'enregistrer. |

---

## Exemple complet et exécutable

Ci-dessous le programme complet que vous pouvez copier, coller et exécuter. Il crée un fichier Word vierge, insère un bouton ActiveX, définit sa légende et enregistre le résultat.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Initialise DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(document);

        // Optional: add some explanatory text
        builder.Writeln("Below is an ActiveX button created programmatically:");
        builder.InsertParagraph();

        // 3️⃣ Insert the ActiveX CommandButton
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "MyButton",
            new RectangleF(0, 0, 100, 30));

        // 4️⃣ Set the button caption
        commandButton.Caption = "Press";

        // 5️⃣ Save the document
        string outputPath = @"C:\Temp\with_button.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Sortie** : Après avoir exécuté le programme, ouvrez `C:\Temp\with_button.docx` dans Microsoft Word. Vous verrez une page unique avec le texte « Below is an ActiveX button created programmatically: » suivi d'un bouton intitulé **Press**.

---

## Conclusion

Vous savez maintenant comment **créer un document Word vierge**, **insérer un bouton ActiveX**, **définir la légende du bouton**, et **enregistrer** le résultat en utilisant Aspose.Words for .NET. Le même modèle peut être étendu à d'autres contrôles ActiveX (cases à cocher, listes déroulantes, etc.) en modifiant `OleControlType`.  

Ensuite, vous pourriez explorer **comment insérer des événements de bouton ActiveX** avec VBA, ou **comment ajouter un contrôle** à des documents existants contenant déjà du contenu. Les deux sujets s'appuient directement sur les concepts abordés ici.

Bonne programmation, et n'hésitez pas à expérimenter différentes tailles, positions et légendes pour répondre aux exigences UI de votre application !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Comment créer un document Word C# avec un bouton de commande ActiveX](/words/english/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/)
- [Comment ajouter un bouton ActiveX dans un document Word avec Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}