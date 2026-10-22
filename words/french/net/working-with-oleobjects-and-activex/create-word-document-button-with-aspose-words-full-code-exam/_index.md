---
category: general
date: 2026-07-23
description: Créer un bouton de document Word avec Aspose.Words – guide étape par
  étape pour insérer un CommandButton ActiveX dans un fichier .docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document button
- ActiveX CommandButton
- DocumentBuilder
- InsertForms2OleControl
- Aspose.Words
language: fr
lastmod: 2026-07-23
og_description: 'Créez un bouton de document Word avec Aspose.Words : apprenez à intégrer
  un CommandButton ActiveX dans un fichier Word en quelques minutes.'
og_image_alt: Screenshot of a Word document showing an inserted CommandButton control
og_title: Bouton de création de document Word – Guide complet d'Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: create word document button using Aspose.Words – step‑by‑step guide
    to insert an ActiveX CommandButton into a .docx file.
  headline: create word document button with Aspose.Words – Full Code Example
  type: TechArticle
- description: create word document button using Aspose.Words – step‑by‑step guide
    to insert an ActiveX CommandButton into a .docx file.
  name: create word document button with Aspose.Words – Full Code Example
  steps:
  - name: '**Creates** an OLE object inside the Word file.'
    text: '**Creates** an OLE object inside the Word file.'
  - name: '**Registers** it as an ActiveX CommandButton, which Word will render as
      a clickable UI element.'
    text: '**Registers** it as an ActiveX CommandButton, which Word will render as
      a clickable UI element.'
  - name: '**Positions** it according to the rectangle we supplied.'
    text: '**Positions** it according to the rectangle we supplied.'
  - name: Launch Microsoft Word.
    text: Launch Microsoft Word.
  - name: Navigate to **File → Open** and select `CommandButton.docx`.
    text: Navigate to **File → Open** and select `CommandButton.docx`.
  - name: You should see a rectangular button labeled “CommandButton1”.
    text: You should see a rectangular button labeled “CommandButton1”.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- ActiveX
- CommandButton
title: Bouton de création de document Word avec Aspose.Words – Exemple complet de
  code
url: /fr/net/working-with-oleobjects-and-activex/create-word-document-button-with-aspose-words-full-code-exam/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# créer un bouton de document Word avec Aspose.Words – Guide de programmation complet

Vous avez déjà eu besoin de **créer un bouton de document Word** mais vous ne saviez pas quelle API utiliser ? Vous n'êtes pas seul—la plupart des développeurs se heurtent à un mur lorsqu'ils essaient d'intégrer des contrôles interactifs dans un fichier .docx. La bonne nouvelle ? Avec Aspose.Words for .NET, vous pouvez insérer un ActiveX CommandButton entièrement fonctionnel dans un document Word en quelques lignes de code.

Dans ce tutoriel, nous parcourrons l’ensemble du processus : de la configuration du projet, à l’initialisation d’un `DocumentBuilder`, en passant par l’insertion du bouton avec `InsertForms2OleControl`, et enfin l’enregistrement du fichier afin que Word reconnaisse le contrôle. À la fin, vous disposerez d’un fichier Word prêt à l’emploi contenant un bouton cliquable—sans aucune gymnastique d’interop COM requise.

## Ce dont vous avez besoin

- **.NET 6.0** ou version ultérieure (le code fonctionne également avec .NET Framework 4.6+).  
- Package NuGet **Aspose.Words for .NET** (version 23.9 ou plus récente).  
- Une compréhension de base du C# (nous garderons la syntaxe conviviale pour les débutants).  
- Visual Studio 2022 ou tout IDE de votre choix.

C’est tout—pas de références COM supplémentaires, pas d’interop Office, juste du code géré pur.

---

## Étape 1 : Configurer Aspose.Words pour **créer un bouton de document Word**

Tout d’abord, ajoutez le package Aspose.Words à votre projet :

```bash
dotnet add package Aspose.Words
```

Ou, si vous utilisez l’interface NuGet de Visual Studio, recherchez “Aspose.Words” et cliquez sur **Install**. Cette seule ligne vous donne accès aux classes `Document`, `DocumentBuilder` et à la méthode `InsertForms2OleControl` dont nous aurons besoin plus tard.

> **Astuce :** Gardez vos packages NuGet à jour ; les versions plus récentes incluent souvent des corrections de bugs pour la gestion d’ActiveX.

---

## Étape 2 : Initialiser **DocumentBuilder** pour un **ActiveX CommandButton**

Nous créons maintenant un nouveau document Word et lançons un `DocumentBuilder`. Pensez à `DocumentBuilder` comme le pinceau qui vous permet de dessiner du contenu sur la toile.

```csharp
using System;
using System.Drawing;               // For Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 2.1: Create a new empty document
        Document document = new Document();

        // Step 2.2: Initialize DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

Remarquez que nous importons `System.Drawing`—la structure `Rectangle` définit l’emplacement et la taille du bouton. C’est ici que le **ActiveX CommandButton** résidera.

---

## Étape 3 : Utiliser **InsertForms2OleControl** pour **ajouter un CommandButton**

Voici le cœur du tutoriel : insérer le bouton lui‑-même. La méthode `InsertForms2OleControl` prend trois arguments—le type de contrôle, un `Rectangle`, et éventuellement un nom. Nous utiliserons `OleControlType.CommandButton` pour spécifier le contrôle exact que nous voulons.

```csharp
        // Step 3: Insert an ActiveX CommandButton at (0,0) with width=100, height=30
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new Rectangle(0, 0, 100, 30));
```

Cet appel unique fait beaucoup :

1. **Crée** un objet OLE à l’intérieur du fichier Word.  
2. **L’enregistre** comme un ActiveX CommandButton, que Word affichera comme un élément d’interface cliquable.  
3. **Le positionne** selon le rectangle que nous avons fourni.

Si vous devez modifier la légende du bouton ou d’autres propriétés, vous pouvez le faire après l’insertion en accédant au `OleFormat` sous‑jacent. Dans la plupart des cas, la légende par défaut (“CommandButton1”) suffit.

---

## Étape 4 : Enregistrer le document Word contenant le **CommandButton**

L’enregistrement est simple—il suffit de pointer vers un dossier où vous avez les droits d’écriture. L’extension du fichier doit être `.docx` pour que le bouton survive au aller‑retour.

```csharp
        // Step 4: Save the document with the embedded button
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Lorsque vous ouvrez `CommandButton.docx` dans Microsoft Word, vous verrez un petit bouton dans le coin supérieur gauche de la première page. Cliquer dessus ne fait rien par défaut (cela nécessiterait du VBA), mais le contrôle est entièrement fonctionnel et pourra être relié plus tard.

> **Pourquoi cela fonctionne :** Aspose.Words écrit le flux OLE directement dans le package DOCX, contournant la nécessité pour Word de générer le contrôle à l’exécution. Cela garantit que le bouton apparaît exactement où vous l’avez placé.

---

## Étape 5 : Vérifier le bouton dans Word

Ouvrez le fichier généré :

1. Lancez Microsoft Word.  
2. Allez dans **File → Open** et sélectionnez `CommandButton.docx`.  
3. Vous devriez voir un bouton rectangulaire intitulé “CommandButton1”.

Si vous ne voyez pas le bouton, assurez‑vous que le **Design Mode** est activé (Developer → Design Mode). Cela bascule la représentation visuelle des contrôles ActiveX.

---

## Étape 6 : Options avancées – Personnaliser le **ActiveX CommandButton**

Voici quelques ajustements rapides qui pourraient vous être utiles :

| Objectif | Extrait de code |
|------|--------------|
| Change caption | ```csharp<br/>OleFormat ole = builder.CurrentParagraph.Runs[0].OleFormat;<br/>ole.OleControlCaption = "Submit";``` |
| Set macro name (requires Word macro support) | ```csharp<br/>ole.OleControlMacroName = "MyMacro";``` |
| Resize after insertion | ```csharp<br/>builder.MoveToDocumentEnd();<br/>builder.InsertForms2OleControl(OleControlType.CommandButton, new Rectangle(0,0,150,40));``` |

Ces extraits démontrent la flexibilité de `InsertForms2OleControl`. Vous pouvez même intégrer d’autres contrôles ActiveX comme `CheckBox` ou `ListBox` en échangeant l’énumération `OleControlType`.

---

## Exemple complet fonctionnel

Voici le programme complet, prêt à copier‑coller, qui **crée un bouton de document Word** à partir de zéro :

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class CreateWordDocumentButton
{
    static void Main()
    {
        // 1️⃣ Create a new empty document
        Document document = new Document();

        // 2️⃣ Initialize DocumentBuilder – the tool that lets us edit the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Insert an ActiveX CommandButton at position (0,0) with size 100x30
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new Rectangle(0, 0, 100, 30));

        // 4️⃣ Save the .docx file – this is where the button lives
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);

        Console.WriteLine($"✅ Document with button saved to: {outputPath}");
    }
}
```

**Sortie attendue lors de l’exécution du programme :**

```
✅ Document with button saved to: C:\Temp\CommandButton.docx
```

Ouvrez le fichier résultant et vous verrez le bouton exactement à l’endroit où le code l’a placé.

---

## Pièges courants et comment les éviter

- **Référence `System.Drawing` manquante** – La structure `Rectangle` s’y trouve ; sans elle le compilateur se plaindra.  
- **Utilisation d’une version plus ancienne d’Aspose.Words** – Les premières versions ne supportaient pas pleinement `InsertForms2OleControl`. Mettez à jour vers le dernier package stable.  
- **Enregistrement en `.doc` au lieu de `.docx`** – Le flux OLE est supprimé dans le format binaire plus ancien, ce qui fait disparaître le bouton.  
- **Exécution sur un serveur sans interface (headless) sans Word installé** – Le bouton sera toujours présent dans le fichier, mais vous ne pourrez pas le prévisualiser sans Word. Cela convient aux pipelines de génération automatisée.

---

## Prochaines étapes – Étendre le flux de travail **créer un bouton de document Word**

Maintenant que vous avez maîtrisé les bases, envisagez ces idées de niveau supérieur :

- **Attacher des macros VBA** au bouton pour une logique métier personnalisée.  
- **Générer plusieurs boutons** dans une boucle pour des formulaires dynamiques.  
- **Combiner avec Aspose.PDF** pour exporter le même document en PDF tout en préservant la mise en page visuelle (le bouton devient une image statique dans le PDF).  
- **

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités d’API supplémentaires et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Créer un document Word avec Aspose.Words pour .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Créer une forme rectangle dans Word avec Aspose.Words – Guide étape par étape](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Insérer une image en ligne dans un document Word avec Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}