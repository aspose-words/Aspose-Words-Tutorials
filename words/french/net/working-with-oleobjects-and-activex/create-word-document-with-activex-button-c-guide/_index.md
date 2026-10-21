---
category: general
date: 2026-07-19
description: Créer un document Word avec Aspose.Words C# et apprendre comment ajouter
  un bouton de commande ActiveX, définir la taille du bouton et insérer le bouton
  par programmation.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to add activex
- insert command button
- set button size
- how to insert button
language: fr
lastmod: 2026-07-19
og_description: Créez un document Word avec Aspose.Words C# et intégrez un bouton
  de commande ActiveX en quelques secondes. Suivez le guide étape par étape pour définir
  la taille du bouton et l’insérer facilement.
og_image_alt: Screenshot of a Word document showing an ActiveX command button inserted
  via C#
og_title: Créer un document Word avec un bouton ActiveX – Tutoriel C#
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  headline: Create Word Document with ActiveX Button – C# Guide
  type: TechArticle
- description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  name: Create Word Document with ActiveX Button – C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code also works on .NET Framework 4.7+). - A valid
      Aspose.Words for .NET license (or a free evaluation key). - Visual Studio 2022
      (or any IDE you like). - Basic familiarity with C# and object‑oriented programming.'
  - name: Platform Limitations
    text: '- ActiveX controls only run on the Windows version of Word. If your audience
      includes macOS or Word Online users, the button will appear as a static image.
      - Some corporate environments disable ActiveX for security; you may need to
      sign the document or inform users to enable content.'
  - name: VBA Interaction (Optional)
    text: If you want the button to execute a macro, you’ll have to add a VBA project
      to the document after saving. Aspose.Words does not generate VBA code automatically,
      but you can use the `Document.VbaProject` API to inject it.
  - name: Naming Collisions
    text: Always give each control a unique `Name`. Re‑using the same name can cause
      runtime errors when Word tries to resolve the control.
  - name: Performance Tip
    text: When inserting many controls, reuse a single `DocumentBuilder` instance
      and avoid calling `doc.Save` inside a loop. Batch the inserts and save once
      at the end.
  - name: What’s Next?
    text: '- **Style the button** – change fonts, colors, or add an image background.
      - **Attach VBA macros** – make the button perform calculations or launch external
      programs. - **Combine with other controls** – checkboxes, list boxes, or even
      embedded Excel sheets.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Créer un document Word avec un bouton ActiveX – Guide C#
url: /fr/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un document Word avec un bouton ActiveX – Guide complet C#  

Vous vous êtes déjà demandé comment **créer un document Word** qui contient un bouton ActiveX fonctionnel ? Peut-être automatisez‑vous un rapport et avez besoin d’un contrôle « Approve » cliquable directement dans le fichier. Dans ce tutoriel, nous allons passer en revue exactement cela — en utilisant Aspose.Words for .NET pour ajouter un bouton de commande ActiveX, définir sa taille et l’insérer où vous le souhaitez.  

Si vous vous êtes déjà demandé *comment ajouter activex* contrôles sans ouvrir Word manuellement, vous êtes au bon endroit. À la fin, vous disposerez d’un exemple exécutable, d’une explication claire de chaque étape et de conseils pour gérer les pièges courants.

## Ce que vous apprendrez

- Comment configurer Aspose.Words dans un projet C#  
- Le code exact pour **créer un document Word** et intégrer un bouton de commande ActiveX  
- Moyens de **définir la taille du bouton** et de personnaliser sa légende et son nom  
- La méthode appropriée pour **insérer le bouton de commande** et **comment insérer le bouton** à n’importe quel emplacement du document  
- Considérations des cas limites (version de Word, limites de plateforme, avertissements de sécurité)

### Prérequis

- .NET 6.0 ou ultérieur (le code fonctionne également sur .NET Framework 4.7+).  
- Une licence valide d’Aspose.Words for .NET (ou une clé d’évaluation gratuite).  
- Visual Studio 2022 (ou tout IDE de votre choix).  
- Une connaissance de base du C# et de la programmation orientée objet.  

Aucune autre bibliothèque tierce n’est requise.

---

## Étape 1 : Créer un document Word – Configuration du projet

Avant de pouvoir **insérer le bouton de commande**, nous avons besoin d’un fichier Word vierge avec lequel travailler. Cette étape montre également le modèle classique de « créer un document Word » utilisant Aspose.Words.

```csharp
// Add the Aspose.Words NuGet package first:
//   dotnet add package Aspose.Words
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

// 1️⃣  Initialize a new blank document.
Document doc = new Document();

// 1️⃣  Create a DocumentBuilder – it lets us place content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Pourquoi c’est important :** `Document` représente le fichier .docx complet, tandis que `DocumentBuilder` suit la position actuelle du curseur. Tous les insertions suivantes (y compris notre contrôle ActiveX) se font par rapport à ce builder.

---

## Étape 2 : Comment ajouter ActiveX – Construire le contrôle CommandButton

Maintenant que le document existe, abordons la partie **comment ajouter activex**. Aspose.Words expose la classe `Forms2OleControl` pour les objets ActiveX. Ici, nous créerons un bouton de commande et configurerons ses propriétés, y compris l’exigence de **définir la taille du bouton**.

```csharp
// 2️⃣  Create the ActiveX command button.
Forms2OleControl commandButton = new Forms2OleControl(
    doc,                     // Parent document
    Forms2OleControlType.CommandButton); // Control type

// Configure appearance – this is where we **set button size**.
commandButton.Width = 120;          // Width in points (≈1.67 inches)
commandButton.Height = 30;          // Height in points (≈0.42 inches)

// Set the text the user sees.
commandButton.Caption = "Click Me";

// Give the control a unique name for later reference.
commandButton.Name = "cmdButton1";
```

> **Astuce :** La taille est mesurée en points (1 point = 1/72 pouce). Ajustez les valeurs pour correspondre à votre mise en page ; pour un bouton de barre d’outils typique, 120 × 30 convient parfaitement.

---

## Étape 3 : Insérer le bouton de commande – Le cœur de **Insert Command Button**

Avec le contrôle prêt, nous allons maintenant **insérer le bouton de commande** dans le document à l’emplacement actuel du builder. Vous pouvez déplacer le builder n’importe où (par ex., après un paragraphe) avant d’appeler cette méthode.

```csharp
// 3️⃣  Insert the prepared ActiveX control into the document.
builder.InsertForms2OleControl(commandButton);
```

Si vous devez **comment insérer le bouton** à un signet spécifique, déplacez simplement le builder d’abord :

```csharp
builder.MoveToBookmark("MyPlace"); // Ensure a bookmark named 'MyPlace' exists
builder.InsertForms2OleControl(commandButton);
```

> **Que se passe-t-il en coulisses ?** Aspose.Words écrit les flux d’objets OLE nécessaires dans le package .docx, de sorte que Word puisse afficher le bouton sans macros supplémentaires.

---

## Étape 4 : Enregistrer le document – Finaliser le cycle **Create Word Document**

L’étape finale est simple : enregistrer le fichier sur le disque. Cela complète le cycle de **créer un document Word**, d’intégrer l’ActiveX et d’enregistrer.

```csharp
// 4️⃣  Save the document where you want it.
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
```

Ouvrez le fichier résultant dans Microsoft Word (Windows uniquement). Vous devriez voir un bouton cliquable libellé « Click Me ». En cliquant dessus, l’action par défaut d’un CommandButton sera déclenchée — rien ne se passe à moins d’attacher du code VBA, mais le contrôle est pleinement fonctionnel.

> **Résultat attendu :** Un fichier .docx avec une seule page, un bouton centré au point d’insertion, de taille 120 × 30 pt, intitulé « Click Me ».  
> ![ActiveX button inserted into a Word document](placeholder-image.png)  
> *Texte alternatif de l’image :* **ActiveX button inserted into a Word document using C#** (matches `og_image_alt`).

---

## Étape 5 : Cas limites, sécurité et bonnes pratiques

### Limitations de plateforme
- Les contrôles ActiveX ne fonctionnent que sur la version Windows de Word. Si votre public inclut des utilisateurs macOS ou Word Online, le bouton apparaîtra comme une image statique.  
- Certains environnements d’entreprise désactivent ActiveX pour des raisons de sécurité ; vous devrez peut‑être signer le document ou informer les utilisateurs d’activer le contenu.

### Interaction VBA (Optionnel)
Si vous souhaitez que le bouton exécute une macro, vous devrez ajouter un projet VBA au document après l’enregistrement. Aspose.Words ne génère pas automatiquement du code VBA, mais vous pouvez utiliser l’API `Document.VbaProject` pour l’injecter.

### Collisions de noms
Attribuez toujours à chaque contrôle un `Name` unique. Réutiliser le même nom peut provoquer des erreurs d’exécution lorsque Word tente de résoudre le contrôle.

### Astuce de performance
Lors de l’insertion de nombreux contrôles, réutilisez une seule instance de `DocumentBuilder` et évitez d’appeler `doc.Save` à l’intérieur d’une boucle. Regroupez les insertions et enregistrez une seule fois à la fin.

---

## Exemple complet fonctionnel

En rassemblant tous les éléments, voici un programme complet, prêt à copier‑coller :

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Create and configure the ActiveX command button.
        Forms2OleControl commandButton = new Forms2OleControl(
            doc, Forms2OleControlType.CommandButton);
        commandButton.Width = 120;          // Set button size – width
        commandButton.Height = 30;          // Set button size – height
        commandButton.Caption = "Click Me";
        commandButton.Name = "cmdButton1";

        // Insert the button at the current cursor position.
        builder.InsertForms2OleControl(commandButton);

        // Save the document.
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Exécutez le programme, ouvrez le fichier enregistré, et vous verrez le bouton exactement à l’endroit où le builder était positionné.

---

## Conclusion

Nous venons de **créer un document Word** à partir de zéro, d’apprendre **comment ajouter activex** en configurant un `Forms2OleControl`, de maîtriser les propriétés de **définir la taille du bouton**, et de démontrer la bonne façon d’**insérer le bouton de commande** et **comment insérer le bouton** à n’importe quel endroit du fichier.  

À partir d’un seul exemple de code, vous disposez désormais d’une base solide pour une automatisation Word plus riche — que vous créiez des modèles avec des formulaires interactifs, génériez des contrats nécessitant l’acceptation de l’utilisateur, ou simplement ajoutiez quelques contrôles pratiques dans un rapport.

### Et après ?

- **Style the button** – changer les polices, les couleurs, ou ajouter une image d’arrière‑plan.  
- **Attach VBA macros** – faire en sorte que le bouton effectue des calculs ou lance des programmes externes.  
- **Combine with other controls** – cases à cocher, listes déroulantes, ou même des feuilles Excel intégrées.  

N’hésitez pas à expérimenter, et si vous rencontrez un problème, laissez un commentaire ci‑dessous. Bon codage, et profitez de l’automatisation de Word avec Aspose.Words !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Créer un document Word avec Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Créer une forme groupée dans un document Word avec Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insérer une image en ligne dans un document Word avec Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}