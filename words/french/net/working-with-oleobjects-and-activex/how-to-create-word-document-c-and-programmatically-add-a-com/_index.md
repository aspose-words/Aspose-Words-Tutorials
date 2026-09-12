---
category: general
date: 2026-09-11
description: Apprenez à créer un document Word en C# et à ajouter programmaticalement
  un bouton de commande à l'aide d'Aspose.Words en quelques étapes simples.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- programmatically add command button
language: fr
lastmod: 2026-09-11
og_description: Créer un document Word en C# et ajouter de façon programmatique un
  bouton de commande avec Aspose.Words. Suivez ce guide complet pour une solution
  fonctionnelle.
og_image_alt: Screenshot of a Word document containing a Submit command button created
  with C#
og_title: Créer un document Word en C# – ajouter un bouton de commande par programmation
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document c# and programmatically add a command
    button using Aspose.Words in a few simple steps.
  headline: How to create word document c# and programmatically add a command button
  type: TechArticle
- description: Learn how to create word document c# and programmatically add a command
    button using Aspose.Words in a few simple steps.
  name: How to create word document c# and programmatically add a command button
  steps:
  - name: Launch Word and open `CommandButton.docx`.
    text: Launch Word and open `CommandButton.docx`.
  - name: You should see a button labeled **Submit** in the document body.
    text: You should see a button labeled **Submit** in the document body.
  - name: Hovering over the button reveals the name `btnSubmit` in the **Properties**
      pane (Developer tab → Properties).
    text: Hovering over the button reveals the name `btnSubmit` in the **Properties**
      pane (Developer tab → Properties).
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- ActiveX
title: Comment créer un document Word en C# et ajouter un bouton de commande par programmation
url: /fr/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-and-programmatically-add-a-com/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer un document Word c# et ajouter un bouton de commande programmatique

Si vous devez **create word document c#** et intégrer un bouton interactif, ce guide vous montre exactement comment le faire. En utilisant Aspose.Words, vous pouvez ajouter programmatique un bouton de commande en quelques lignes de code, éliminant ainsi le besoin de travail manuel d'interface utilisateur dans Word.

Dans ce tutoriel, vous apprendrez à :

* Initialiser un fichier Word vierge avec C#.
* Insérer un contrôle ActiveX **CommandButton**.
* Définir les propriétés du bouton telles que le nom et la légende.
* Enregistrer le document afin que le bouton apparaisse lorsque le fichier est ouvert dans Microsoft Word.

Aucun outil externe n’est requis au-delà de la bibliothèque Aspose.Words pour .NET, et les étapes fonctionnent avec .NET 6+ ou .NET Framework 4.6.2 et versions ultérieures.

## Prérequis

Avant de commencer, assurez-vous de disposer de :

| Exigence | Raison |
|----------|--------|
| .NET 6 SDK (ou .NET Framework 4.6.2+) | Fournit le runtime pour le projet C#. |
| Visual Studio 2022 (ou tout IDE C#) | Facilite l’écriture, la compilation et l’exécution du code. |
| Package NuGet Aspose.Words for .NET | Fournit les classes `Document`, `DocumentBuilder` et `Forms2OleControl` utilisées dans l’exemple. |
| Connaissances de base de la syntaxe C# | Vous permet de suivre le code sans courbe d’apprentissage supplémentaire. |

Vous pouvez ajouter le package Aspose.Words via la console NuGet :

```powershell
Install-Package Aspose.Words
```

## Étape 1 : Configurer un nouveau projet console C#

Créez une application console qui générera le fichier Word. Ouvrez un terminal et exécutez :

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

Le fichier `Program.cs` généré contiendra le code présenté dans les étapes suivantes.

## Étape 2 : Créer un document vierge et un DocumentBuilder

La première opération consiste à instancier un objet `Document`, qui représente un fichier `.docx` vide, ainsi qu’un `DocumentBuilder` qui vous permet de modifier le contenu du document.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Step 2: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Pourquoi c’est important :**  
`Document` est le conteneur de tous les éléments Word (paragraphes, tableaux, contrôles). `DocumentBuilder` fournit une API fluide pour insérer des objets à la position actuelle du curseur sans manipuler les collections de nœuds de bas niveau.

## Étape 3 : Insérer un contrôle ActiveX CommandButton

Aspose.Words prend en charge l’insertion de contrôles ActiveX hérités via la méthode `InsertForms2OleControl`. La méthode nécessite le type de contrôle et la taille souhaitée en points.

```csharp
        // Step 3: Insert an ActiveX CommandButton control (size: 100x30 points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            ControlType.CommandButton, 100, 30);
```

**Ce qui se passe en coulisses :**  
Word traite un contrôle ActiveX comme un objet OLE (Object Linking and Embedding). La classe `Forms2OleControl` encapsule les données OLE et expose des propriétés telles que `Name` et `Caption`.

## Étape 4 : Configurer le nom et la légende du bouton

Après avoir placé le contrôle, vous pouvez personnaliser ses propriétés d’exécution. Définir un `Name` significatif vous aide à identifier le bouton plus tard, tandis que `Caption` définit le texte affiché sur le bouton.

```csharp
        // Step 4: Set the button's name and displayed caption
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";
```

**Astuce pro :**  
Si vous prévoyez de gérer l’événement de clic du bouton avec VBA, le `Name` devient le nom de la macro que vous référencerez, par ex., `Sub btnSubmit_Click()`.

## Étape 5 : Enregistrer le document sur le disque

Enfin, écrivez le document dans un fichier `.docx`. Choisissez un dossier où vous avez les droits d’écriture ; l’exemple utilise un chemin relatif, qui se résout dans le répertoire de sortie du projet.

```csharp
        // Step 5: Save the document containing the button
        string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

L’exécution du programme produit `CommandButton.docx`. L’ouverture du fichier dans Microsoft Word affiche un bouton **Submit** cliquable :

![Document Word avec un bouton de commande Submit](/images/command-button.png "Capture d'écran d'un document Word contenant un bouton de commande Submit créé avec C#")

*Texte alternatif de l'image (og_image_alt) :* `Screenshot of a Word document containing a Submit command button created with C#`

## Vérifier le résultat

1. Lancez Word et ouvrez `CommandButton.docx`.  
2. Vous devriez voir un bouton libellé **Submit** dans le corps du document.  
3. En survolant le bouton, le nom `btnSubmit` apparaît dans le volet **Properties** (onglet Développeur → Propriétés).  

Si le bouton n’apparaît pas, assurez‑vous que l’onglet **Developer** est activé dans Word (Fichier → Options → Personnaliser le ruban → cocher *Developer*). Les contrôles ActiveX sont masqués lorsque cet onglet est désactivé.

## Gestion des variations courantes et des cas limites

| Situation | Ajustement recommandé |
|-----------|-----------------------|
| **Taille du bouton différente** | Modifiez les arguments de largeur et de hauteur dans `InsertForms2OleControl`. Par exemple, `150, 40` crée un bouton plus grand. |
| **Boutons multiples** | Appelez `InsertForms2OleControl` à plusieurs reprises, en déplaçant le curseur du builder entre les appels (`builder.Writeln();`). |
| **Bouton sans ActiveX** | Utilisez `InsertFormField` pour ajouter un champ de formulaire hérité (par ex., une case à cocher) si vous avez besoin de compatibilité avec d’anciennes versions de Word qui bloquent ActiveX. |
| **Utilisation multiplateforme** | Les contrôles ActiveX ne fonctionnent que sur les versions Windows de Word. Pour Mac ou les visionneuses web, envisagez d’insérer un hyperlien stylisé comme un bouton. |
| **Avertissements de sécurité** | Word peut afficher une invite de sécurité à l’ouverture d’un document contenant des contrôles ActiveX. Signer le document avec un certificat de confiance réduit cette friction. |

## Exemple complet, exécutable

Vous trouverez ci‑dessous le programme complet que vous pouvez copier‑coller dans `Program.cs`. Il se compile et s’exécute sans modification après l’ajout du package NuGet Aspose.Words.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control (size: 100x30 points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            ControlType.CommandButton, 100, 30);

        // Set the button's name and displayed caption
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Save the document containing the button
        string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Sortie attendue dans la console :**

```
Document saved to C:\Path\To\WordButtonDemo\bin\Debug\net6.0\CommandButton.docx
```

L’ouverture du fichier généré montre le bouton **Submit** prêt à être utilisé.

## Conclusion

Vous savez maintenant comment **create word document c#** et **programmatically add command button** à l’aide d’Aspose.Words. Le processus se résume à initialiser un `Document`, insérer un `Forms2OleControl`, configurer ses propriétés et enregistrer le fichier. À partir d’ici, vous pouvez :

* Ajouter d’autres contrôles (par ex., cases à cocher, champs de texte) en modifiant `ControlType`.
* Attacher des macros VBA au bouton pour une logique personnalisée.
* Combiner cette technique avec d’autres fonctionnalités d’Aspose.Words telles que la fusion de courrier ou le remplissage de modèles.

Expérimentez avec différentes tailles, légendes et multiples boutons pour adapter votre scénario d’automatisation. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Créer un document Word avec en‑tête et pied de page en utilisant Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Créer un document Word avec Aspose.Words pour .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Créer une forme groupée dans un document Word en utilisant Aspose.Words pour .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}