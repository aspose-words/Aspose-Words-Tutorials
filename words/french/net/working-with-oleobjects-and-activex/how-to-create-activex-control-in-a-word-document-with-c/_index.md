---
category: general
date: 2026-09-14
description: Créer un contrôle ActiveX dans un document Word avec C#. Apprenez à insérer
  un ActiveX, ajouter un bouton interactif et générer le fichier .docx de manière
  programmatique.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- how to insert activex
- add interactive button
- create word document
- create button with code
language: fr
lastmod: 2026-09-14
og_description: Créer un contrôle ActiveX dans un document Word avec C#. Suivez cet
  exemple complet pour insérer un contrôle ActiveX, ajouter un bouton interactif et
  enregistrer le fichier.
og_image_alt: Screenshot of a Word document containing a newly created ActiveX CommandButton
og_title: Créer un contrôle ActiveX dans Word avec C# – guide étape par étape
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Create ActiveX control in a Word document with C#. Learn how to insert
    ActiveX, add interactive button, and generate the .docx file programmatically.
  headline: How to create ActiveX control in a Word document with C#
  type: TechArticle
tags:
- ActiveX
- C#
- Word automation
title: Comment créer un contrôle ActiveX dans un document Word avec C#
url: /fr/net/working-with-oleobjects-and-activex/how-to-create-activex-control-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer un contrôle ActiveX dans un document Word avec C#

Si vous devez **créer un contrôle ActiveX** à l’intérieur d’un fichier Microsoft Word, ce guide vous montre une solution complète, prête à l’emploi. Vous verrez exactement comment insérer un CommandButton ActiveX, définir ses propriétés et enregistrer le fichier `.docx` résultant en n’utilisant que du code C#.

Ajouter un bouton interactif à un document Word est une exigence courante lorsque vous voulez que les utilisateurs finaux déclenchent des macros ou une logique personnalisée directement depuis l’interface du document. L’exemple ci‑dessous montre **comment insérer ActiveX** sans recourir à des outils tiers, et il couvre également **comment créer un document Word** de façon programmatique.

À la fin de ce tutoriel, vous serez capable de **créer un bouton avec du code**, de personnaliser son libellé et de produire un fichier Word portable qui conserve le contrôle ActiveX.

## Prérequis

- .NET 6.0 ou version ultérieure (la bibliothèque Aspose.Words pour .NET fonctionne avec .NET Core et .NET Framework)
- Une référence au package NuGet `Aspose.Words`  
  ```bash
  dotnet add package Aspose.Words
  ```
- Connaissances de base en C# et en programmation orientée objet

## Étape 1 : Configurer le projet et importer les espaces de noms

Créez un nouveau projet console (ou intégrez le code dans n’importe quelle application C# existante). Importez les espaces de noms requis afin que le compilateur puisse localiser les classes de traitement Word.

```csharp
using System;
using System.Drawing;               // Provides RectangleF
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
```

> **Pourquoi cette étape est importante** – L’API `Aspose.Words` fournit les classes `Document`, `DocumentBuilder` et `Forms2OleControl` qui vous permettent de manipuler les fichiers Word au niveau objet. Sans ces références, le reste du code ne compilerait pas.

## Étape 2 : Créer un nouveau document Word et un DocumentBuilder

L’objet `Document` représente l’ensemble du package `.docx`, tandis que `DocumentBuilder` offre une API fluide pour insérer du contenu.

```csharp
// Step 2: Initialize a fresh Word document
Document document = new Document();

// Attach a builder to the document – the builder knows where to write next
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Explication** – Instancier un nouveau `Document` vous donne une toile vierge. Le curseur du builder commence au début de la première section, prêt pour la prochaine insertion.

## Étape 3 : Insérer le CommandButton ActiveX

Utilisez `InsertForms2OleControl` pour placer un contrôle ActiveX à un emplacement précis. La méthode nécessite le type de contrôle et un `RectangleF` qui définit les coordonnées X/Y ainsi que la taille (en points).

```csharp
// Step 3: Add an ActiveX CommandButton at (100,100) with width 120 and height 30
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **Pourquoi cela fonctionne** – `OleControlType.CommandButton` indique à l’API de créer un CommandButton Windows standard. Le rectangle positionne le bouton par rapport au coin supérieur gauche de la page, vous permettant d’**ajouter un bouton interactif** exactement où vous le souhaitez.

## Étape 4 : Configurer les propriétés du bouton

Définissez maintenant le texte visible du bouton (`Caption`) et son nom interne (`Name`). Ces propriétés sont ce que les utilisateurs voient et ce que le code VBA pourra référencer ultérieurement.

```csharp
// Step 4: Define the button’s caption and programmatic name
commandButton.Caption = "Click Me";
commandButton.Name = "btnClick";
```

> **Conseil pratique** – Le `Name` doit être unique dans le document ; sinon, les macros VBA pourraient référencer le mauvais contrôle.

## Étape 5 : Enregistrer le document

Enfin, écrivez le fichier sur le disque. Le contrôle ActiveX est stocké à l’intérieur du package Word, de sorte que le fichier enregistré conservera toutes ses fonctionnalités lorsqu’il sera ouvert dans Microsoft Word.

```csharp
// Step 5: Persist the document – the ActiveX control stays embedded
string outputPath = @"C:\Temp\CommandButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

> **Résultat** – L’ouverture de `CommandButton.docx` dans Word affiche un CommandButton cliquable libellé « Click Me ». Le contrôle peut être lié à une macro via l’interface Word (`Développeur → Mode Création → Propriétés`).

## Listing complet du code source

Assembler toutes les étapes donne un programme autonome que vous pouvez copier, coller et exécuter.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert an ActiveX CommandButton at the desired location
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new RectangleF(100, 100, 120, 30));

        // Set the button's caption and internal name
        commandButton.Caption = "Click Me";
        commandButton.Name = "btnClick";

        // Save the document – the control is preserved
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### Résultat attendu

L’exécution du programme affiche une ligne de confirmation :

```
Document saved to C:\Temp\CommandButton.docx
```

Lorsque vous ouvrez le fichier généré dans Microsoft Word, vous verrez un **CommandButton** placé aux coordonnées spécifiées. Cliquer sur le bouton en mode création le met en surbrillance ; en mode exécution il se comporte comme n’importe quel bouton ActiveX standard.

## Variantes courantes et cas particuliers

| Scénario | Ajustement |
|----------|------------|
| **Type de contrôle différent** | Remplacez `OleControlType.CommandButton` par `OleControlType.CheckBox`, `OleControlType.OptionButton`, etc. |
| **Boutons multiples** | Appelez `InsertForms2OleControl` plusieurs fois, en mettant à jour les coordonnées du `RectangleF` pour chaque nouveau bouton. |
| **Dimensionnement dynamique** | Calculez les dimensions du rectangle en fonction de la taille de la page (`builder.PageSetup.PageWidth`). |
| **Enregistrement dans un flux** | Utilisez `document.Save(stream, SaveFormat.Docx)` lorsque vous devez renvoyer le fichier depuis une API web. |
| **Format Word 97‑2003** | Changez le format d’enregistrement en `SaveFormat.Doc` pour produire un fichier `.doc` qui intègre toujours le contrôle ActiveX. |

> **Astuce de pro** : Testez toujours le document généré sur la version cible de Word, car les versions plus anciennes peuvent appliquer des paramètres de sécurité qui désactivent les contrôles ActiveX par défaut.

## Questions fréquentes

**Cela fonctionne‑t‑il avec .NET Core ?**  
Oui. La bibliothèque Aspose.Words est multiplateforme et entièrement compatible avec .NET Core et .NET 5/6+.

**Puis‑je assigner une macro au bouton par programme ?**  
L’API n’insère pas directement de code VBA. Après la génération du document, ouvrez‑le dans Word, activez l’onglet Développeur et enregistrez ou écrivez une macro qui référence `btnClick`.

**Et si le bouton n’apparaît pas ?**  
Vérifiez que l’onglet **Développeur** est activé dans Word et que le document n’est pas ouvert en **Affichage protégé**. Assurez‑vous également que les coordonnées du rectangle se trouvent à l’intérieur des marges de la page.

## Conclusion

Vous savez maintenant comment **créer un contrôle ActiveX** à l’intérieur d’un fichier Word en utilisant C#. Le tutoriel a couvert **comment insérer ActiveX**, a démontré **l’ajout d’un bouton interactif**, a montré **comment créer un document Word** à partir de zéro, et a illustré **comment créer un bouton avec du code** qui persiste après l’enregistrement.  

À partir d’ici, vous pouvez explorer d’autres types d’ActiveX, connecter le bouton à des macros VBA, ou intégrer la logique dans un service de génération de documents plus vaste. Expérimentez avec différentes tailles, positions et propriétés de contrôle pour obtenir exactement l’expérience utilisateur souhaitée.

---


## Que devriez‑vous apprendre ensuite ?


Les tutoriels suivants traitent de sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications pas à pas pour vous aider à maîtriser des fonctionnalités API supplémentaires et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Créer un nouveau document Word](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Créer un projet VBA dans un document Word](/words/english/net/working-with-vba-macros/create-vba-project/)
- [Créer et styliser un document Word avec Aspose.Words pour .NET](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}