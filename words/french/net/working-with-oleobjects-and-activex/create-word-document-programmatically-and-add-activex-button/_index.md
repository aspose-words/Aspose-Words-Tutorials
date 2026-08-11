---
category: general
date: 2026-08-10
description: Créer un document Word de façon programmatique avec Aspose.Words, puis
  ajouter un bouton ActiveX. Insérer un bouton de commande ActiveX en quelques minutes.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add activex control word
- insert activex command button
language: fr
lastmod: 2026-08-10
og_description: Créez un document Word de façon programmatique avec Aspose.Words,
  puis ajoutez un bouton de contrôle ActiveX. Apprenez à insérer rapidement un bouton
  de commande ActiveX.
og_image_alt: Screenshot of a Word document created programmatically with an ActiveX
  command button
og_title: Créer un document Word par programmation – ajouter un bouton ActiveX en
  C#
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  headline: Create word document programmatically and add ActiveX button
  type: TechArticle
- description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  name: Create word document programmatically and add ActiveX button
  steps:
  - name: Open `ActiveX_CommandButton.docx` in Microsoft Word.
    text: Open `ActiveX_CommandButton.docx` in Microsoft Word.
  - name: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
    text: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
  - name: Click **Design Mode**. The button should appear with the label “Submit”.
    text: Click **Design Mode**. The button should appear with the label “Submit”.
  - name: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
    text: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- C#
title: Créer un document Word programmatiquement et ajouter un bouton ActiveX
url: /fr/net/working-with-oleobjects-and-activex/create-word-document-programmatically-and-add-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un document Word programmatique et ajouter un bouton ActiveX

Si vous devez **créer un document Word programmatique**, ce guide vous accompagne tout au long du processus avec Aspose.Words for .NET. Vous apprendrez également comment **ajouter des éléments de contrôle ActiveX** et **insérer des objets bouton de commande ActiveX** dans un exemple unique et autonome.

Générer des fichiers Word à partir du code supprime l'étape manuelle d'ouverture de Microsoft Word, vous permettant de créer automatiquement des rapports, factures ou contrats basés sur des données. À la fin de ce tutoriel, vous disposerez d’une application console C# prête à l’emploi qui produit un fichier `.docx` contenant un bouton de commande ActiveX interactif.

## Prérequis

* .NET 6.0 SDK ou version ultérieure (le code fonctionne également avec .NET Framework 4.6+)
* Visual Studio 2022 ou tout IDE supportant le développement .NET
* Une licence valide d’Aspose.Words for .NET (vous pouvez utiliser la clé d’évaluation gratuite pour les tests)
* Une connaissance de base de la syntaxe C# et du concept de contrôles COM/ActiveX

> **Astuce :** Si vous prévoyez de distribuer le document généré à des utilisateurs qui n’ont pas Word installé, intégrez les fichiers d’exécution du contrôle ActiveX à côté du `.docx` ou fournissez un modèle activé par macro.

## Créer un document Word programmatique – configuration initiale

Tout d'abord, ajoutez le package NuGet Aspose.Words à votre projet :

```bash
dotnet add package Aspose.Words
```

Ensuite, créez un nouveau projet console (si vous n’en avez pas déjà un) :

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
```

Ouvrez le fichier `Program.cs` généré – nous remplacerons son contenu par la solution complète ci‑dessous.

## Étape 1 : Importer les espaces de noms et configurer la licence

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // OPTIONAL: Apply your Aspose.Words license to remove evaluation watermarks.
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");
```

*Pourquoi c’est important* : L’importation de `Aspose.Words.Drawing` vous donne accès à `Forms2OleControl`, la classe qui représente un contrôle ActiveX dans un document Word. Définir une licence dès le départ évite les avertissements d’exécution en production.

## Étape 2 : Créer un document vierge et un DocumentBuilder

```csharp
            // Create a new empty Word document.
            Document doc = new Document();

            // DocumentBuilder provides a convenient API for inserting text, tables, and controls.
            DocumentBuilder builder = new DocumentBuilder(doc);
```

L’objet `Document` est la représentation en mémoire d’un fichier `.docx`. `DocumentBuilder` fonctionne comme un curseur que vous déplacez dans le document pour y insérer des éléments.

## Étape 3 : Insérer un contrôle ActiveX CommandButton

```csharp
            // Insert an ActiveX CommandButton.
            // Parameters: control type, width, height, left position, top position (all in points).
            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, // ActiveX type
                100,   // Width in points
                50,    // Height in points
                150,   // Left offset from the page margin
                200);  // Top offset from the page margin
```

`InsertForms2OleControl` crée un objet OLE que Word considère comme un contrôle ActiveX. Le système de coordonnées utilise des points (1 point = 1/72 pouce), ce qui correspond au moteur de mise en page de Word.

## Étape 4 : Définir la légende du bouton et les propriétés optionnelles

```csharp
            // Set the text that appears on the button.
            commandBtn.Caption = "Submit";

            // Optional: assign a macro name that Word will call when the button is clicked.
            // commandBtn.OnAction = "MyMacroName";
```

Définir la propriété `Caption` est la façon la plus courante d’étiqueter le bouton. Si vous avez besoin que le bouton exécute une macro VBA, attribuez le nom de la macro à `OnAction`. Ce tutoriel se concentre sur la partie visuelle ; l’intégration des macros est abordée dans la section « Étapes suivantes ».

## Étape 5 : Enregistrer le document

```csharp
            // Define the output path – change this to a folder that exists on your machine.
            string outputPath = @"ActiveX_CommandButton.docx";

            // Save the document with the embedded ActiveX control.
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Lorsque vous exécuterez le programme, vous verrez un message dans la console confirmant que `ActiveX_CommandButton.docx` a été écrit sur le disque.

### Code source complet (prêt à copier‑coller)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton,
                100, 50, 150, 200);

            commandBtn.Caption = "Submit";
            // commandBtn.OnAction = "MyMacroName";

            string outputPath = @"ActiveX_CommandButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

L’exécution du fragment produit un fichier Word contenant un **bouton de commande ActiveX** cliquable. Ouvrez le fichier dans Microsoft Word, passez en **Mode Création** (onglet Développeur → Mode Création), et vous verrez le bouton rendu exactement à l’endroit où vous l’avez placé.

## Étape 6 : Vérifier le résultat

1. Ouvrez `ActiveX_CommandButton.docx` dans Microsoft Word.
2. Activez l’onglet **Développeur** s’il n’est pas visible (`Fichier → Options → Personnaliser le ruban → cocher Développeur`).
3. Cliquez sur **Mode Création**. Le bouton doit apparaître avec le libellé « Submit ».
4. Si vous avez ajouté une macro `OnAction`, cliquez sur le bouton lorsque le Mode Création est désactivé pour déclencher la macro.

Si le bouton n’apparaît pas, assurez‑vous que les paramètres de sécurité de Word autorisent les contrôles ActiveX (`Fichier → Options → Centre de confiance → Paramètres du Centre de confiance → Paramètres ActiveX`).

## Questions fréquentes et cas particuliers

| Question | Réponse |
|----------|---------|
| **Puis-je insérer d’autres types d’ActiveX ?** | Oui. L’énumération `Forms2OleControlType` comprend `CheckBox`, `OptionButton`, `ComboBox`, etc. Remplacez `CommandButton` par la valeur d’énumération souhaitée |

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques présentées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Créer une forme groupée dans un document Word avec Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Créer un document Word avec en‑tête et pied de page avec Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Insérer une image en ligne dans un document Word avec Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}