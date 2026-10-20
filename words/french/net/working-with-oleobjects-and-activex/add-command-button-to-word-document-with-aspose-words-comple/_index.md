---
category: general
date: 2026-07-29
description: Ajoutez un bouton de commande à un document Word en utilisant Aspose.Words.
  Apprenez comment définir les propriétés du contrôle ActiveX et définir la légende
  du bouton de commande en quelques étapes simples.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button to word document
- set activex control properties
- set command button caption
- Aspose.Words ActiveX example
- C# insert ActiveX control
language: fr
lastmod: 2026-07-29
og_description: Ajouter un bouton de commande à un document Word avec Aspose.Words.
  Ce tutoriel montre comment définir les propriétés d’un contrôle ActiveX et définir
  rapidement la légende du bouton de commande.
og_image_alt: Screenshot of a Word document with a Submit command button inserted
  via C#
og_title: Ajouter un bouton de commande à un document Word – Aspose.Words étape par
  étape
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  headline: Add Command Button to Word Document with Aspose.Words – Complete Guide
  type: TechArticle
- description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  name: Add Command Button to Word Document with Aspose.Words – Complete Guide
  steps:
  - name: Setting the Caption
    text: 'The caption is the text that appears on the button itself. To **set command
      button caption**, simply assign a string to the `Caption` property:'
  - name: Naming the Control
    text: 'Giving the control a meaningful name makes it easier to reference later
      (for example, when automating Word macros). We’ll set the `Name` property:'
  - name: Positioning on the Page
    text: 'Word uses points (1/72 of an inch) for layout. Adjust the `Left` and `Top`
      properties to place the button where you need it:'
  - name: Expected Result
    text: 1. The Word document opens with a single page. 2. A rectangular button labeled
      **Submit** appears at the coordinates you specified. 3. If you right‑click the
      button and choose **Properties**, you’ll see the name `btnSubmit` and other
      properties you set.
  - name: Inserting Other ActiveX Types
    text: 'The `InsertForms2OleControl` method isn’t limited to command buttons. You
      can embed check boxes, option buttons, or even custom ActiveX objects:'
  - name: Handling Word Versions
    text: Older Word versions (pre‑2007) use the binary `.doc` format, which stores
      ActiveX controls differently. Aspose.Words automatically converts the control
      when you save as `.doc`, but some properties (like precise positioning) may
      shift. If you target legacy formats, test the output in the specific Wor
  - name: Security Settings
    text: 'Word may disable ActiveX controls on machines with strict macro security.
      To avoid a “Security Warning” dialog, consider:'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Ajouter un bouton de commande à un document Word avec Aspose.Words – Guide
  complet
url: /fr/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ajouter un bouton de commande à un document Word – Guide complet de programmation

Vous avez déjà eu besoin d'**ajouter un bouton de commande à un document Word** mais vous ne saviez pas quelles appels d'API utiliser ? Vous n'êtes pas seul ; de nombreux développeurs rencontrent ce problème lorsqu'ils essaient pour la première fois d'intégrer des contrôles interactifs dans un fichier DOCX. La bonne nouvelle, c'est qu'Aspose.Words rend cela étonnamment simple. Dans ce guide, nous allons parcourir la création d'un contrôle ActiveX CommandButton, **définir les propriétés du contrôle ActiveX**, et **définir la légende du bouton de commande** — le tout avec du code C# propre que vous pouvez copier‑coller immédiatement.

À la fin de ce tutoriel, vous disposerez d’un fichier Word entièrement fonctionnel contenant un bouton cliquable « Submit », prêt à être ouvert dans Microsoft Word. Aucun script VBA externe, aucune manipulation manuelle de l’interface — juste un contrôle purement programmatique.

## Ce que vous apprendrez

* Comment créer un document Word vierge et un `DocumentBuilder`.
* L’appel de méthode exact pour **ajouter un bouton de commande à un document Word** avec Aspose.Words.
* Les façons de **définir les propriétés du contrôle ActiveX** telles que la taille, la position et le nom.
* La technique appropriée pour **définir la légende du bouton de commande** afin que le bouton affiche exactement ce que vous souhaitez.
* Des astuces pour gérer les cas limites comme les différents types de boutons, le redimensionnement DPI et la compatibilité des versions de Word.

> **Prérequis :** Visual Studio (ou tout IDE C#) avec Aspose.Words pour .NET installé (package NuGet `Aspose.Words`). Aucune expérience préalable d’ActiveX requise.

---

## Étape 1 : Configurer le projet et importer les espaces de noms

Avant de pouvoir **ajouter un bouton de commande à un document Word**, nous avons besoin d’un projet C# qui référence Aspose.Words. Créez une nouvelle application console .NET, puis ajoutez le package NuGet :

```bash
dotnet add package Aspose.Words
```

Ensuite, importez les espaces de noms requis dans votre fichier source :

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;
```

Ces trois directives `using` vous donnent accès aux classes `Document`, `DocumentBuilder` et `Forms2OleControl` qui permettent l’insertion d’ActiveX.

*Astuce :* Si vous utilisez Visual Studio, l’IDE proposera d’ajouter ces directives automatiquement lorsque vous taperez les noms de classe.

---

## Étape 2 : Créer un document vierge et un constructeur

Un nouvel objet `Document` représente un fichier Word vide. Le `DocumentBuilder` est notre « stylo » pratique qui nous permet de dessiner, d’insérer du texte et—crucialement—de placer des contrôles ActiveX.

```csharp
// Initialize a new, empty Word document.
Document doc = new Document();

// Attach a builder to the document for editing.
DocumentBuilder builder = new DocumentBuilder(doc);
```

À ce stade, le document n’est qu’une toile blanche — pensez-y comme une feuille de papier propre qui attend votre bouton de commande.

---

## Étape 3 : Insérer le contrôle ActiveX CommandButton

Nous allons enfin **ajouter un bouton de commande à un document Word**. Aspose.Words fournit la méthode `InsertForms2OleControl`, qui accepte le type de contrôle et ses dimensions. Nous utiliserons `Forms2OleControlType.CommandButton` et lui donnerons une largeur confortable de 150 points et une hauteur de 30 points.

```csharp
// Insert a CommandButton ActiveX control with a specific size.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton,
    width: 150,
    height: 30);
```

La méthode renvoie une instance `Forms2OleControl`, que nous utiliserons pour **définir les propriétés du contrôle ActiveX** à l’étape suivante.

---

## Étape 4 : Configurer le contrôle – Nom, Légende et Position

### Définir la légende

La légende est le texte qui apparaît sur le bouton lui‑même. Pour **définir la légende du bouton de commande**, il suffit d’assigner une chaîne à la propriété `Caption` :

```csharp
commandButton.Caption = "Submit";
```

Vous pouvez remplacer `"Submit"` par n’importe quoi — « Save », « Export », « Launch », etc. — et Word affichera exactement ce texte.

### Nommer le contrôle

Donner au contrôle un nom significatif facilite les références ultérieures (par exemple, lors de l’automatisation de macros Word). Nous définirons la propriété `Name` :

```csharp
commandButton.Name = "btnSubmit";
```

### Positionnement sur la page

Word utilise des points (1/72 de pouce) pour la mise en page. Ajustez les propriétés `Left` et `Top` pour placer le bouton où vous le souhaitez :

```csharp
commandButton.Left = 100; // 100 points from the left margin
commandButton.Top  = 200; // 200 points from the top of the page
```

Si vous devez aligner le bouton par rapport à un paragraphe, vous pouvez d’abord déplacer le curseur du builder, puis insérer le contrôle ; les coordonnées seront alors relatives à cet emplacement.

*Cas limite :* Sur des écrans à haute résolution DPI, la taille visuelle peut apparaître légèrement différente dans Word. Pour garder la taille physique du bouton cohérente sur tous les appareils, calculez les points en fonction du DPI cible (généralement 96 DPI pour Word).

---

## Étape 5 : Enregistrer le document

Une fois le bouton entièrement configuré, la persistance du fichier se résume à une seule ligne :

```csharp
// Save the document; the ActiveX control is stored inside the DOCX.
doc.Save("CommandButton.docx");
```

Le fichier `CommandButton.docx` résultant contient un bouton ActiveX pleinement fonctionnel. Ouvrez‑le dans Microsoft Word, et vous verrez un bouton « Submit » positionné exactement où vous l’avez placé.

### Résultat attendu

1. Le document Word s’ouvre avec une seule page.  
2. Un bouton rectangulaire libellé **Submit** apparaît aux coordonnées spécifiées.  
3. Si vous faites un clic droit sur le bouton et choisissez **Properties**, vous verrez le nom `btnSubmit` ainsi que les autres propriétés que vous avez définies.

---

## Étape 6 : Variations avancées et pièges courants

### Insertion d'autres types d'ActiveX

La méthode `InsertForms2OleControl` ne se limite pas aux boutons de commande. Vous pouvez intégrer des cases à cocher, des boutons d’option, ou même des objets ActiveX personnalisés :

```csharp
// Example: Insert a CheckBox instead of a CommandButton.
Forms2OleControl checkBox = builder.InsertForms2OleControl(
    Forms2OleControlType.CheckBox,
    width: 20,
    height: 20);
checkBox.Name = "chkAgree";
checkBox.Caption = "I Agree";
```

Le même schéma **définir les propriétés du contrôle ActiveX** s’applique — il suffit d’échanger l’énumération du type.

### Gestion des versions de Word

Les versions plus anciennes de Word (pré‑2007) utilisent le format binaire `.doc`, qui stocke les contrôles ActiveX différemment. Aspose.Words convertit automatiquement le contrôle lorsque vous enregistrez en `.doc`, mais certaines propriétés (comme le positionnement précis) peuvent être décalées. Si vous ciblez des formats hérités, testez la sortie dans la version spécifique de Word dont vous avez besoin.

### Paramètres de sécurité

Word peut désactiver les contrôles ActiveX sur des machines avec une sécurité macro stricte. Pour éviter une boîte de dialogue « Security Warning », envisagez :

* Signer le document avec un certificat de confiance.  
* Indiquer aux utilisateurs d’activer le contenu ActiveX pour cet emplacement de fichier.  
* Utiliser une alternative sans macro (par ex., des contrôles de contenu simples) si la sécurité est une préoccupation.

---

## Étape 7 : Exemple complet fonctionnel

Voici le programme complet, prêt à être exécuté, qui intègre chaque étape décrite. Copiez‑le dans votre `Program.cs`, ajustez le chemin de sortie si nécessaire, puis cliquez sur **Run**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            width: 150,   // Width in points
            height: 30);  // Height in points

        // Step 3: Set the control's name and caption.
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Step 4: Position the control on the page.
        commandButton.Left = 100; // 100 points from left edge
        commandButton.Top  = 200; // 200 points from top edge

        // Optional: Add a paragraph above the button for context.
        builder.MoveToDocumentEnd();
        builder.Writeln("Click the button below to submit the form:");

        // Step 5: Save the document.
        string outputPath = "CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved successfully to {outputPath}");
    }
}
```

**Ce que fait ce code :**

* Commence avec un document vierge.  
* Insère un bouton de commande, **définit les propriétés du contrôle ActiveX**, et **définit la légende du bouton de commande**.  
* Ajoute un court paragraphe explicatif.  
* Enregistre le fichier sous le nom `CommandButton.docx`.

Exécutez le programme, ouvrez le fichier généré, et vous verrez le bouton placé sous le texte explicatif.

---

## Conclusion

Nous venons de démontrer comment **ajouter un bouton de commande à un document Word** avec Aspose.Words, comment **définir les propriétés du contrôle ActiveX**, et comment **définir la légende du bouton de commande** — le tout dans un extrait C# concis et prêt pour la production. L’approche est extensible : changez le type de contrôle, ajustez les dimensions, ou parcourez une source de données pour insérer des dizaines de boutons automatiquement.

Vous voulez aller plus loin ? Essayez :

* Lier le bouton à une macro qui déclenche une exportation de données.  
* Ajouter des images ou des icônes personnalisées à l’intérieur du bouton via la propriété `Picture`.  
* Construire un formulaire complet avec plusieurs contrôles ActiveX (zones de texte, listes déroulantes, etc.).

L’expérimentation est le meilleur moyen de maîtriser l’automatisation Word. Si vous rencontrez un problème, pensez à revérifier vos calculs DPI et les paramètres de sécurité de Word. Bon codage, et que vos documents deviennent toujours plus interactifs !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser des fonctionnalités API supplémentaires et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Ajouter du contenu avec Document Builder dans Aspose.Words pour .NET](/words/english/net/add-content-using-document-builder/)
- [Créer une forme groupée dans un document Word avec Aspose.Words pour .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Créer un document Word avec en-tête et pied de page avec Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}