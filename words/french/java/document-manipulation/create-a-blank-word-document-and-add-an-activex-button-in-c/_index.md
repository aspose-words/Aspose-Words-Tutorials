---
category: general
date: 2026-10-23
description: Créer un document Word vierge avec C# et apprendre à insérer des contrôles
  ActiveX, y compris un bouton, à l'aide d'Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- create activex control
- word document activex button
language: fr
lastmod: 2026-10-23
og_description: Créez un document Word vierge avec C# et apprenez à insérer des contrôles
  ActiveX, y compris un bouton, en utilisant Aspose.Words.
og_image_alt: Result of creating a blank Word document with an ActiveX Submit button
og_title: Créer un document Word vierge et ajouter un bouton ActiveX en C#
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button in C#
  type: TechArticle
- description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  name: Create a blank Word document and add an ActiveX button in C#
  steps:
  - name: Instantiate a `Document`.
    text: Instantiate a `Document`.
  - name: Use `DocumentBuilder` to work with the file.
    text: Use `DocumentBuilder` to work with the file.
  - name: Call `InsertForms2OleControl` to **how to insert activex** controls.
    text: Call `InsertForms2OleControl` to **how to insert activex** controls.
  - name: Configure the control’s properties (**create activex control**).
    text: Configure the control’s properties (**create activex control**).
  - name: Save the file, yielding a **word document activex button** ready for VBA
      integration.
    text: Save the file, yielding a **word document activex button** ready for VBA
      integration.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Créer un document Word vierge et ajouter un bouton ActiveX en C#
url: /fr/java/document-manipulation/create-a-blank-word-document-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un document Word vierge et ajouter un bouton ActiveX en C#

Si vous devez **créer un document Word vierge** de manière programmatique, ce guide vous montre exactement comment faire. Vous verrez un exemple complet et exécutable qui crée un nouveau document, insère un CommandButton ActiveX et enregistre le fichier — le tout avec Aspose.Words pour .NET.

Travailler avec des fichiers Word nécessite souvent plus que du texte brut. Ajouter un **bouton ActiveX** vous permet d’intégrer une fonctionnalité interactive qui peut être utilisée dans des modèles activés par macro ou des solutions uniquement Windows. À la fin de ce tutoriel, vous serez capable d’insérer n’importe quel contrôle ActiveX, mais nous nous concentrons sur le scénario le plus courant : un **bouton ActiveX dans un document Word** qui soumet un formulaire.

## Prérequis

* .NET 6.0 ou version ultérieure (le code fonctionne également avec .NET Framework 4.7+)
* Visual Studio 2022 (ou tout IDE C#)
* **Aspose.Words for .NET** package NuGet  
  ```bash
  dotnet add package Aspose.Words
  ```
* Familiarité de base avec la syntaxe C#

> **Astuce :** Aspose.Words est une bibliothèque commerciale, mais elle propose une licence temporaire gratuite pour les tests. Installez la licence dès le début pour éviter le filigrane d’évaluation.

## Étape 1 : Créer un document Word vierge avec Aspose.Words

La première étape consiste à instancier un objet `Document`. Cela représente un fichier `.docx` vide en mémoire.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();
```

`Document` commence sans sections, pages ou contenu. C’est la page blanche dont vous avez besoin pour les scénarios de **création d’un document Word vierge** comme la génération de rapports à partir de zéro.

## Étape 2 : Obtenir un DocumentBuilder pour modifier le document

`DocumentBuilder` fournit une API pratique pour ajouter du texte, des images et des contrôles. Nous l’utiliserons pour positionner le contrôle ActiveX.

```csharp
// Obtain a DocumentBuilder tied to the blank document
DocumentBuilder builder = new DocumentBuilder(document);
```

Le builder ajoute automatiquement une section par défaut et une première page, vous permettant de commencer à insérer des objets immédiatement.

## Étape 3 : Comment insérer des contrôles ActiveX dans le document

Aspose.Words expose `InsertForms2OleControl` pour intégrer des objets OLE/ActiveX. La méthode nécessite le type de contrôle, la largeur et la hauteur (en points). Ci-dessous, nous insérons un **CommandButton** — le bouton de formulaire classique que l’on trouve dans les modèles Word hérités.

```csharp
// Insert an ActiveX CommandButton control (100 × 30 points)
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.COMMANDBUTTON, 100, 30);
```

> **Pourquoi cela fonctionne :** `Forms2OleControlType.COMMANDBUTTON` indique à Word de créer un bouton capable de répondre aux événements de clic lorsque le document est ouvert dans un environnement Windows qui prend en charge ActiveX.

## Étape 4 : Créer un contrôle ActiveX – définir ses propriétés

Nous attribuons maintenant au bouton un nom programmatique et une légende visible. C’est la partie de **création d’un contrôle activex** que les développeurs négligent souvent.

```csharp
// Set the button's name (used in VBA) and the text shown to users
commandButton.Name = "btnSubmit";
commandButton.Caption = "Submit";
```

* `Name` est l’identifiant que vous référencerez depuis les macros VBA (`ActiveDocument.InlineShapes("btnSubmit")`).
* `Caption` est le libellé affiché sur le bouton lui‑-même.

## Étape 5 : Enregistrer le document Word avec le bouton ActiveX

Enfin, écrivez le document sur le disque. L’extension du fichier doit être `.docx` (ou `.docm` si vous prévoyez d’ajouter des macros plus tard). L’exemple enregistre dans un dossier factice — remplacez-le par votre propre chemin.

```csharp
// Save the document containing the ActiveX button
string outputPath = @"C:\Temp\ActiveXButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Lorsque vous ouvrez le fichier résultant dans Microsoft Word (Windows uniquement), vous verrez un **bouton activex dans un document Word** fonctionnel qui peut être relié à du code VBA.

## Exemple complet fonctionnel

Voici le programme complet que vous pouvez copier‑coller dans un nouveau projet console.

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
            // 1. Create a blank Word document
            Document document = new Document();

            // 2. Get a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // 3. Insert an ActiveX CommandButton (100 × 30 points)
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);

            // 4. Configure the button
            commandButton.Name = "btnSubmit";
            commandButton.Caption = "Submit";

            // 5. Save the file
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Sortie attendue lorsque vous exécutez le programme**

```
Document saved to C:\Temp\ActiveXButton.docx
```

Ouvrez le `ActiveXButton.docx` généré dans Word, et vous verrez un bouton intitulé **Submit** positionné en haut de la première page.

## Cas limites et pièges courants

| Situation | Ce qu’il faut surveiller | Recommandation |
|-----------|--------------------------|----------------|
| Exécution sur macOS ou Linux | ActiveX est une technologie réservée à Windows, donc le bouton apparaîtra comme un espace réservé. | Utilisez le tutoriel uniquement pour des modèles ciblant Windows. |
| Document ouvert dans Word Online | Les contrôles ActiveX ne sont pas pris en charge dans la vue navigateur. | Fournissez une interface de secours ou indiquez aux utilisateurs d’ouvrir le fichier dans le client de bureau. |
| Besoin d’un fichier activé par macro | Les fichiers `.docx` ne peuvent pas contenir de code VBA. | Enregistrez en tant que `.docm` (`document.Save("MyFile.docm", SaveFormat.Docm)`) et ajoutez la macro séparément. |
| Incohérence de taille du contrôle | Les valeurs de largeur/hauteur sont en points (1 pt ≈ 1/72 po). | Ajustez les valeurs numériques pour obtenir la taille visuelle souhaitée. |

## Questions fréquemment posées

**Comment insérer des contrôles ActiveX autres qu’un bouton ?**  
Utilisez la même méthode `InsertForms2OleControl` mais passez une valeur différente de l’énumération `Forms2OleControlType`, comme `COMBOBOX` ou `LISTBOX`.

**Puis-je changer la police ou la couleur du bouton ?**  
L’apparence du bouton ActiveX est régie par l’application hôte (Word) et le thème Windows sous‑jacent. Vous pouvez modifier des propriétés comme `ForeColor` et `BackColor` via VBA après l’ouverture du document.

**Existe‑t‑il un moyen d’ajouter un gestionnaire de clic directement depuis C# ?**  
Non. L’événement de clic doit être géré par VBA ou un add‑in Word car le bouton s’exécute dans le processus de Word, pas dans votre application .NET.

## Conclusion

Vous savez maintenant comment **créer un document Word vierge** de manière programmatique et intégrer un **bouton ActiveX** en utilisant Aspose.Words pour .NET. Les étapes couvertes :

1. Instancier un `Document`.
2. Utiliser `DocumentBuilder` pour travailler avec le fichier.
3. Appeler `InsertForms2OleControl` pour **comment insérer des contrôles activex**.
4. Configurer les propriétés du contrôle (**création d’un contrôle activex**).
5. Enregistrer le fichier, obtenant un **bouton activex dans un document Word** prêt pour l’intégration VBA.

À partir de là, vous pouvez explorer l’ajout d’autres types de contrôles, le raccordement de macros VBA, ou la conversion du document en PDF tout en conservant le bouton (comme image statique). Expérimentez avec différentes tailles, légendes et noms.

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Comment ajouter un bouton ActiveX dans un document Word avec Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [Créer un document Word avec un bouton ActiveX – Guide C#](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}