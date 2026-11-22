---
category: general
date: 2026-11-22
description: Apprenez à insérer un contrôle Forms2Ole dans Word avec C#. Ce guide
  pas à pas couvre DocumentBuilder, le placement du bouton de commande et l’enregistrement
  du .docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert forms2ole control word
- Aspose.Words
- DocumentBuilder
- command button
- C# Word automation
language: fr
lastmod: 2026-11-22
og_description: Insérez le contrôle Forms2Ole dans Word avec C#. Suivez ce guide pour
  ajouter un bouton de commande en utilisant Aspose.Words et DocumentBuilder.
og_image_alt: Screenshot of a Word document showing an inserted Forms2Ole command
  button created with C#
og_title: Insérer le contrôle Forms2Ole dans Word avec C# – guide complet
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn to insert a Forms2Ole control in Word with C#. This step‑by‑step
    guide covers DocumentBuilder, command button placement, and saving the .docx.
  headline: How to insert Forms2Ole control in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Comment insérer le contrôle Forms2Ole dans Word à l'aide de C# et Aspose.Words
url: /fr/net/working-with-oleobjects-and-activex/how-to-insert-forms2ole-control-in-word-using-c-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment insérer le contrôle Forms2Ole dans Word avec C# et Aspose.Words

Si vous devez **insérer le contrôle Forms2Ole dans Word**, ce tutoriel vous montre exactement comment le faire avec C#. Que vous créiez un modèle remplissable ou automatisiez la création de formulaires, la solution ci‑dessous vous permet d’ajouter un bouton de commande programmé.

Vous apprendrez à créer un document vierge, à utiliser `DocumentBuilder` pour placer le contrôle, et à enregistrer le résultat au format `.docx`. Le guide couvre également les pièges courants, tels que les systèmes de coordonnées et la compatibilité avec les anciennes versions de Word.

## Prérequis

* .NET 6.0 ou ultérieur (le code fonctionne également avec .NET Framework 4.6+)
* Aspose.Words pour .NET (package NuGet `Aspose.Words`)
* Une compréhension de base du C# et du modèle d’objet Word
* Un IDE tel que Visual Studio ou VS Code

## Étape 1 : Configurer le projet et importer les espaces de noms

Créez une nouvelle application console et ajoutez le package Aspose.Words :

```bash
dotnet new console -n InsertForms2OleDemo
cd InsertForms2OleDemo
dotnet add package Aspose.Words
```

Dans `Program.cs`, importez les espaces de noms requis :

```csharp
using System;
using System.Drawing;               // for Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;        // for Forms2OleControl
```

> **Astuce :** Utilisez la dernière version d’Aspose.Words pour obtenir la prise en charge complète de l’API `Forms2OleControl`.

## Étape 2 : Créer un document vierge et initialiser DocumentBuilder

La classe `Document` représente le fichier Word, tandis que `DocumentBuilder` fournit des méthodes pour insérer du contenu.

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Initialize DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` fonctionne comme un curseur ; après cette ligne, vous pouvez commencer à placer des éléments n’importe où dans le document.

## Étape 3 : Définir la position et la taille du bouton

Word mesure les coordonnées en points (1 pt ≈ 1/72 po). La structure `Rectangle` de `System.Drawing` décrit les limites du contrôle.

```csharp
// Step 3: Define the button's position and size (x, y, width, height)
Rectangle buttonBounds = new Rectangle(0, 0, 100, 30); // 100 pt wide, 30 pt tall
```

* `0,0` place le contrôle dans le coin supérieur gauche de la page courante.
* Ajustez `x` et `y` pour déplacer le bouton ailleurs (par ex., `new Rectangle(150, 200, 100, 30)`).

## Étape 4 : Insérer le bouton de commande Forms2Ole

Utilisez maintenant `InsertForms2OleControl` pour ajouter le contrôle. La méthode nécessite le type de contrôle, un nom et les limites définies ci‑dessus.

```csharp
// Step 4: Insert a Forms2Ole command button named "ClickMe"
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,   // type of control
    "ClickMe",                  // internal name (used for VBA or macros)
    buttonBounds);              // position and size
```

L’objet `Forms2OleControl` retourné vous permet de modifier des propriétés telles que `Enabled`, `Visible`, ou même d’attacher un nom de macro ultérieurement.

### Pourquoi utiliser Forms2Ole ?

* **Compatibilité héritée** – Les contrôles Forms2Ole fonctionnent dans Word 97‑2003 (`.doc`) et les fichiers `.docx` plus récents.
* **Support des macros** – Ils peuvent déclencher des macros VBA, ce qui les rend idéaux pour les modèles interactifs.
* **Placement précis** – Contrairement aux contrôles de contenu, vous contrôlez les coordonnées exactes.

## Étape 5 : Enregistrer le document

Enfin, écrivez le fichier sur le disque. Choisissez un dossier auquel vous avez des droits d’écriture.

```csharp
// Step 5: Save the document to see the inserted button
string outputPath = @"./output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Ouvrez `output.docx` dans Microsoft Word. Vous verrez un bouton intitulé **ClickMe** dans le coin supérieur gauche de la première page. Cliquer dessus dans Word ne fera rien tant que vous n’aurez pas assigné une macro, mais le contrôle est pleinement fonctionnel.

## Gestion des cas limites courants

| Situation | Comment y remédier |
|-----------|-------------------|
| **Le bouton apparaît hors page** | Vérifiez que les coordonnées du `Rectangle` sont à l’intérieur des marges de la page. Utilisez `builder.PageSetup.PageWidth` et `PageHeight` pour calculer des limites sûres. |
| **Le contrôle n’est pas visible dans les anciennes versions de Word** | Enregistrez le document au format `.doc` (`doc.Save("output.doc", SaveFormat.Doc)`) pour garantir la compatibilité Forms2Ole avec Word 97‑2003. |
| **Besoin de changer la légende** | Après l’insertion, définissez `commandButton.Caption = "Submit";`. |
| **Attribuer une macro** | Définissez `commandButton.MacroName = "MyMacro"` ; la macro doit exister dans le projet VBA du document. |
| **Boutons multiples** | Répétez l’Étape 4 avec des valeurs `Rectangle` différentes et des noms uniques. |

## Exemple complet et exécutable

En réunissant tous les éléments, voici un programme autonome que vous pouvez copier, coller et exécuter :

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace InsertForms2OleDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document
            Document doc = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Define button bounds (x, y, width, height) in points
            Rectangle buttonBounds = new Rectangle(0, 0, 100, 30);

            // Insert a Forms2Ole command button named "ClickMe"
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                "ClickMe",
                buttonBounds);

            // Optional: set button caption
            commandButton.Caption = "Click Me!";

            // Save the document
            string outputPath = "output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Sortie attendue :** Après l’exécution du programme, `output.docx` s’ouvre dans Word avec un bouton cliquable intitulé *Click Me!* placé en haut‑gauche de la première page.

## Conclusion

Vous savez maintenant comment **insérer un contrôle Forms2Ole dans Word** en utilisant C# et Aspose.Words. Le processus consiste à créer un `Document`, positionner un `Rectangle` et appeler `InsertForms2OleControl` via `DocumentBuilder`. Avec l’exemple complet de code et les conseils pour les cas limites, vous pouvez intégrer des boutons de commande dans n’importe quel flux de travail Word automatisé.

### Prochaines étapes

* Explorez d’autres valeurs `ControlType` telles que `CheckBox` ou `OptionButton`.
* Combinez les contrôles Forms2Ole avec des macros VBA pour des formulaires interactifs.
* Utilisez `DocumentBuilder.MoveTo` pour placer des boutons sur des paragraphes ou des tableaux spécifiques.
* Consultez la documentation **Forms2Ole** d’Aspose.Words pour les paramètres de propriétés avancées.

Bonne programmation, et profitez de la création de documents Word plus riches avec C# et Aspose.Words !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Comment insérer un bouton de commande OLE dans un document Word avec C#](/words/english/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/)
- [Comment ajouter un contrôle ActiveX dans Word avec Aspose.Words – guide étape par étape](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/)
- [Ajouter un bouton de commande à un document Word avec Aspose.Words – guide complet](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}