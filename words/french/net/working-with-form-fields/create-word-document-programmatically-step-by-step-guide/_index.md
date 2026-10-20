---
category: general
date: 2026-08-04
description: Créer un document Word de manière programmatique avec C#. Apprenez à
  ajouter un bouton de commande de façon programmatique avec Aspose.Words en quelques
  étapes seulement.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- programmatically add command button
- Aspose.Words InsertForms2OleControl
- C# Word automation
- OLE command button in Word
language: fr
lastmod: 2026-08-04
og_description: Créer un document Word de manière programmatique avec Aspose.Words.
  Ce guide montre comment ajouter de façon programmatique un bouton de commande, le
  configurer et enregistrer le fichier.
og_image_alt: Screenshot of a Word document that contains a Command Button added programmatically
og_title: Créer un document Word programmatique – tutoriel complet C#
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create word document programmatically using C#. Learn how to programmatically
    add command button with Aspose.Words in just a few steps.
  headline: Create word document programmatically – step‑by‑step guide
  type: TechArticle
- description: Create word document programmatically using C#. Learn how to programmatically
    add command button with Aspose.Words in just a few steps.
  name: Create word document programmatically – step‑by‑step guide
  steps:
  - name: The `ControlType` enum value (here `CommandButton`).
    text: The `ControlType` enum value (here `CommandButton`).
  - name: A `RectangleF` that defines the X‑Y position and the width‑height of the
      control (measured in points, where 72 pt = 1 inch).
    text: A `RectangleF` that defines the X‑Y position and the width‑height of the
      control (measured in points, where 72 pt = 1 inch).
  - name: Optionally, additional OLE properties (not needed for the basic button).
    text: Optionally, additional OLE properties (not needed for the basic button).
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Créer un document Word programmatique – guide étape par étape
url: /fr/net/working-with-form-fields/create-word-document-programmatically-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un document Word programmatique – tutoriel complet C#

Si vous devez **créer un document Word programmatique**, ce guide vous montre exactement comment le faire avec Aspose.Words for .NET. En quelques lignes de C#, vous pouvez générer un fichier `.docx` vierge, **ajouter programmétiquement des contrôles de bouton de commande**, définir leurs propriétés et enregistrer le résultat.  

Les étapes ci‑dessous couvrent tout, de la configuration du projet à la gestion des cas limites, afin que vous puissiez copier le code dans votre propre application et l’exécuter sans modifications.

## Ce que vous allez réaliser

À la fin de ce tutoriel, vous serez capable de :

* Initialiser un nouveau document Word entièrement en mémoire.  
* **Ajouter programmétiquement des contrôles de bouton de commande** OLE à n’importe quel emplacement et taille.  
* Configurer la légende du bouton, son nom interne et d’autres propriétés OLE.  
* Enregistrer le document généré sur disque ou dans un flux pour un traitement ultérieur.

### Prérequis

* .NET 6.0 ou version ultérieure (le code fonctionne également avec .NET Framework 4.6+).  
* Une licence valide d’Aspose.Words for .NET (ou une évaluation gratuite).  
* Une connaissance de base du C# et de Visual Studio (ou tout autre IDE de votre choix).  

> **Astuce :** Si vous exécutez l’exemple sans licence, Aspose.Words ajoutera un petit filigrane d’évaluation à la première page.

## Étape 1 : Configurer le projet et importer les espaces de noms requis

Créez une nouvelle application console (ou intégrez‑la à un service existant) et ajoutez le package NuGet Aspose.Words :

```bash
dotnet add package Aspose.Words
```

Puis incluez les espaces de noms essentiels en haut de votre fichier `.cs` :

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
```

Ces importations vous donnent accès à `Document`, `DocumentBuilder`, `Forms2OleControl` et à la structure `RectangleF` utilisée pour le positionnement.

## Étape 2 : Initialiser un nouveau document Word

La première opération dans tout flux **créer un document Word programmatique** consiste à instancier un objet `Document`. Cet objet vit uniquement en mémoire jusqu’à ce que vous l’enregistriez explicitement.

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Attach a DocumentBuilder to simplify content insertion
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` agit comme un curseur qui suit l’endroit où le prochain élément sera placé. L’utiliser rend le code concis et reflète la façon dont vous taperiez directement dans Word.

## Étape 3 : Insérer un contrôle OLE bouton de commande

Aspose.Words fournit la méthode `InsertForms2OleControl` pour incorporer des objets OLE tels que des boutons de commande, des cases à cocher ou des listes déroulantes. La méthode nécessite trois arguments :

1. La valeur d’énumération `ControlType` (ici `CommandButton`).  
2. Un `RectangleF` qui définit la position X‑Y ainsi la largeur‑hauteur du contrôle (mesurées en points, où 72 pt = 1 inch).  
3. Optionnellement, des propriétés OLE supplémentaires (non nécessaires pour le bouton de base).

```csharp
// Step 3: Programmatically add command button at (100,100) with size 120×30 points
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **Pourquoi cela fonctionne :** `InsertForms2OleControl` crée un conteneur OLE dans le document et renvoie un wrapper `Forms2OleControl`. Ce wrapper vous permet de manipuler l’objet OLE sous‑jacent (le bouton réel) sans gérer l’interopérabilité COM de bas niveau.

## Étape 4 : Configurer la légende et le nom interne du bouton

Après l’insertion, vous souhaitez généralement donner au bouton une étiquette visible par l’utilisateur et un identifiant interne que votre macro ou add‑in pourra référencer plus tard.

```csharp
// Step 4: Set caption and name of the button
commandButton.OleFormat.OleObject.Caption = "Click Me";
commandButton.OleFormat.OleObject.Name = "cmdClickMe";
```

* `Caption` est le texte affiché sur le bouton dans l’interface Word.  
* `Name` est l’identifiant programmatique utilisé par VBA ou les scripts d’automatisation externes.

### Optionnel : Assigner une macro au bouton

Si vous prévoyez d’exécuter une macro VBA lorsque le bouton est cliqué, vous pouvez attacher le nom de la macro :

```csharp
commandButton.OleFormat.OleObject.MacroName = "MyMacro";
```

> **Cas limite :** Lorsque le document cible sera ouvert sur une machine dépourvue de la macro, Word affichera un avertissement de sécurité. Signez toujours vos macros ou informez les utilisateurs des paramètres requis.

## Étape 5 : Enregistrer le document

Vous pouvez écrire le fichier sur disque, dans un `MemoryStream`, ou directement dans un objet de réponse d’une API web. L’approche la plus simple pour une démo console consiste à enregistrer dans un dossier local :

```csharp
// Step 5: Persist the document containing the button
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Le fichier `.docx` résultant s’ouvre dans Microsoft Word avec un bouton fonctionnel affichant « Click Me ». Cliquer sur le bouton déclenchera la macro assignée (le cas échéant) ou affichera simplement un message par défaut.

## Exemple complet fonctionnel

Copiez le programme suivant dans `Program.cs` et exécutez‑le. Il montre l’ensemble du flux **créer un document Word programmatique**, y compris la gestion des erreurs.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        try
        {
            // 1️⃣ Initialise a new document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a CommandButton OLE control
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                new RectangleF(100, 100, 120, 30));

            // 3️⃣ Set button properties
            commandButton.OleFormat.OleObject.Caption = "Click Me";
            commandButton.OleFormat.OleObject.Name = "cmdClickMe";
            // Optional macro assignment (uncomment if needed)
            // commandButton.OleFormat.OleObject.MacroName = "MyMacro";

            // 4️⃣ Save the document
            string outputPath = @"C:\Temp\CommandButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"✅ Document created successfully at {outputPath}");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"❌ Error: {ex.Message}");
        }
    }
}
```

**Résultat attendu :** L’ouverture de `CommandButton.docx` dans Word montre un bouton libellé « Click Me ». Le survol du bouton révèle le nom `cmdClickMe` dans le volet des propriétés.

## Questions fréquentes et dépannage

| Question | Réponse |
|----------|---------|
| *Puis‑je ajouter le bouton à un document existant ?* | Oui. Chargez le fichier avec `new Document("Existing.docx")`, puis utilisez le même appel `InsertForms2OleControl`. |
| *Quelle unité utilise `RectangleF` ?* | Points (1 inch = 72 pt). Ajustez les valeurs pour positionner le bouton avec précision. |
| *Le bouton fonctionnera‑t‑il sur Word pour Mac ?* | Les contrôles OLE sont pris en charge uniquement sur Word Windows. Sur Mac, le bouton apparaît comme une image statique. |
| *Ai‑je besoin d’une licence pour la production ?* | Une licence commerciale supprime les filigranes d’évaluation et débloque toutes les fonctionnalités. |
| *Comment modifier la taille du bouton après insertion ?* | Modifiez `commandButton.Width` et `commandButton.Height` ou ré‑insérez avec un nouveau `RectangleF`. |

## Étendre la solution

Maintenant que vous savez **ajouter programmétiquement des contrôles de bouton de commande**, vous pouvez explorer les sujets connexes suivants :

* **Insérer d’autres contrôles de formulaire** – utilisez `ControlType.CheckBox`, `ControlType.OptionButton`, etc. (couvre le mot‑clé secondaire *Aspose.Words InsertForms2OleControl*).  
* **Peupler le document avec des données dynamiques** – fusionnez des données provenant d’une base de données dans des tableaux ou des champs de publipostage.  
* **Exporter en PDF** – après avoir ajouté le bouton, appelez `doc.Save("output.pdf", SaveFormat.Pdf)` pour produire une version PDF (pertinent à *C# Word automation*).  

## Conclusion

Vous disposez maintenant d’un modèle complet, prêt pour la production, pour **créer un document Word programmatique** et **ajouter programmétiquement des boutons de commande** à l’aide d’Aspose.Words for .NET. Le tutoriel a couvert la configuration du projet, l’initialisation du document, l’insertion du bouton OLE, la configuration des propriétés et l’enregistrement du fichier. N’hésitez pas à adapter le code pour insérer d’autres contrôles de formulaire, attacher des macros ou intégrer la logique dans des services web ou des tâches en arrière‑plan.

Bon codage et profitez de l’automatisation des documents Word !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants abordent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Créer un document Word avec Aspose.Words – Guide étape par étape](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)
- [Créer un document Word avec un tableau en utilisant Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Créer une forme groupée dans un document Word en utilisant Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}