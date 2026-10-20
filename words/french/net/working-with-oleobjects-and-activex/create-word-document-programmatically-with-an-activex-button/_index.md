---
category: general
date: 2026-10-20
description: Créer un document Word de façon programmatique et ajouter un bouton de
  commande avec Aspose.Words. Apprenez à insérer un contrôle ActiveX et à définir
  la légende du bouton.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add command button
- add activex control
- insert activex button
- set button caption
language: fr
lastmod: 2026-10-20
og_description: Créer un document Word par programmation et intégrer un bouton de
  commande ActiveX. Ce tutoriel explique comment insérer le contrôle et définir sa
  légende avec Aspose.Words.
og_image_alt: Word file showing an ActiveX command button inserted by Aspose.Words
og_title: Créer un document Word par programmation – ajouter un bouton ActiveX
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  headline: Create Word document programmatically with an ActiveX button
  type: TechArticle
- description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  name: Create Word document programmatically with an ActiveX button
  steps:
  - name: 'Open a terminal or Visual Studio and create a new console project:'
    text: 'Open a terminal or Visual Studio and create a new console project:'
  - name: 'Add the Aspose.Words package:'
    text: 'Add the Aspose.Words package:'
  - name: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
    text: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
  - name: Open `ActiveXCommandButton.docx` in Microsoft Word.
    text: Open `ActiveXCommandButton.docx` in Microsoft Word.
  - name: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
    text: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
  - name: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
    text: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
  - name: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
    text: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Créer un document Word de façon programmatique avec un bouton ActiveX
url: /fr/net/working-with-oleobjects-and-activex/create-word-document-programmatically-with-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un document Word programmatique avec un bouton ActiveX

Créer un document Word programmatique avec Aspose.Words, puis ajouter un bouton de commande sur lequel les utilisateurs peuvent cliquer. Ce guide vous montre comment insérer un contrôle ActiveX, configurer ses propriétés et enregistrer le résultat sous forme de fichier **.docx**.

Vous verrez un exemple complet et exécutable que vous pouvez copier dans une application console. À la fin du tutoriel, vous pourrez générer un fichier Word contenant un bouton de commande pleinement fonctionnel, et vous comprendrez comment **add command button**, **add activex control**, **insert activex button**, et **set button caption** sans quitter votre code C#.

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

* SDK .NET 6.0 ou version ultérieure installé  
* Visual Studio 2022 (ou tout IDE compatible C#)  
* Un fichier de licence Aspose.Words for .NET (l’essai gratuit fonctionne pour cet exemple)  
* Une connaissance de base du C# et du système de projets .NET  

Aucun package NuGet supplémentaire n’est requis au‑delà de **Aspose.Words** car la prise en charge d’ActiveX est intégrée à la bibliothèque.

## Étape 1 : Configurer le projet et ajouter Aspose.Words

1. Ouvrez un terminal ou Visual Studio et créez un nouveau projet console :

   ```bash
   dotnet new console -n WordActiveXDemo
   cd WordActiveXDemo
   ```

2. Ajoutez le package Aspose.Words :

   ```bash
   dotnet add package Aspose.Words
   ```

3. (Facultatif) Si vous avez un fichier de licence, placez‑le à la racine du projet et ajoutez la ligne suivante au début de `Program.cs` pour éviter les filigranes d’évaluation :

   ```csharp
   Aspose.Words.License license = new Aspose.Words.License();
   license.SetLicense("Aspose.Words.lic");
   ```

## Étape 2 : Créer un document Word programmatique – initialiser le document

La première opération consiste à **create Word document programmatically**. Vous le faites en instanciant un objet `Document` et un `DocumentBuilder` qui vous permet d’éditer le contenu du document.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;   // Provides ActiveX control types
using System.Drawing;        // For Point and Size structs

// Initialize a new blank document
Document document = new Document();

// DocumentBuilder gives a cursor‑based API for inserting elements
DocumentBuilder builder = new DocumentBuilder(document);
```

Le `Document` représente le fichier complet, tandis que le `DocumentBuilder` maintient un curseur que vous pouvez déplacer à n’importe quel emplacement du document. Cette séparation garde l’API propre et vous permet d’**add activex control** plus tard sans gérer manuellement les structures de bas niveau.

## Étape 3 : Ajouter un bouton de commande – insertion d’un contrôle ActiveX

Vous allez maintenant **add command button** en insérant un contrôle ActiveX de type `OleControlType.CommandButton`. La méthode `InsertForms2OleControl` nécessite le type de contrôle, une position (`Point`) et une taille (`Size`).

```csharp
// Define where the button will appear (X = 100 pt, Y = 150 pt)
Point buttonPosition = new Point(100, 150);

// Define the button dimensions (width = 120 pt, height = 30 pt)
Size buttonSize = new Size(120, 30);

// Insert the ActiveX command button at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton, // control type
    buttonPosition,              // position
    buttonSize);                 // size
```

L’appel ci‑dessus **insert activex button** dans le document aux coordonnées exactes que vous spécifiez. Les coordonnées sont mesurées en points (1 pt ≈ 1/72 in). Si vous avez besoin du bouton dans un paragraphe spécifique, déplacez d’abord le curseur du builder :

```csharp
builder.Writeln("Click the button below:");
builder.MoveToDocumentEnd(); // places the cursor after the paragraph
```

## Étape 4 : Définir la légende du bouton – personnaliser le texte du bouton de commande

Un bouton sans libellé est déroutant, vous allez donc **set button caption** à quelque chose de significatif. La propriété `Caption` définit le texte affiché sur le bouton, tandis que `Name` donne au contrôle un identifiant programmatique.

```csharp
// Give the button a unique name for later reference
commandButton.Name = "btnSubmit";

// Set the visible text on the button
commandButton.Caption = "Submit";

// Optional: assign a macro name that Word will call when the button is clicked
commandButton.OnClick = "SubmitForm()";
```

Si vous exportez plus tard le document vers un format macro‑activé (`.docm`), la valeur `OnClick` doit correspondre à un nom de macro VBA. Pour un simple `.docx`, la propriété est stockée mais n’est pas exécutée, ce qui convient à la plupart des scénarios d’automatisation.

## Étape 5 : Enregistrer le document contenant le bouton ActiveX

Après avoir configuré le contrôle, vous pouvez **save the document**. Choisissez un répertoire où vous avez les droits d’écriture et utilisez l’extension `.docx` pour une compatibilité maximale.

```csharp
// Replace with your desired output folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ActiveXCommandButton.docx");

// Save the document to disk
document.Save(outputPath);
```

Lorsque vous ouvrez le fichier généré dans Microsoft Word, vous verrez un bouton intitulé **Submit** aux coordonnées que vous avez spécifiées. Cliquer sur le bouton dans le client de bureau tentera d’exécuter la macro `SubmitForm` (si elle existe).

## Étape 6 : Vérifier le résultat et dépanner les problèmes courants

1. Ouvrez `ActiveXCommandButton.docx` dans Microsoft Word.  
2. Passez en **Design Mode** (onglet Développeur → **Design Mode**) pour voir les bordures du bouton.  
3. Si le bouton n’apparaît pas, vérifiez que l’onglet **Developer** est activé et que votre version de Word prend en charge les contrôles ActiveX.  
4. Pour les fichiers macro‑activés (`.docm`), assurez‑vous que le nom de macro dans `OnClick` correspond à une routine VBA ; sinon Word affichera un avertissement de sécurité.

### Astuce

Les contrôles ActiveX sont réservés à Windows. Si vous avez besoin d’interactivité multiplateforme, envisagez d’utiliser des **Content Controls** (`RichTextContentControl`) à la place d’un bouton ActiveX.

## Code source complet

Voici le programme complet, prêt à être exécuté. Copiez‑le dans `Program.cs` et lancez `dotnet run`.



## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Create Word Document with ActiveX Button – C# Guide](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)
- [Add Command Button to Word Document with Aspose.Words – Complete Guide](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)
- [create word document button with Aspose.Words – Full Code Example](/words/english/net/working-with-oleobjects-and-activex/create-word-document-button-with-aspose-words-full-code-exam/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}