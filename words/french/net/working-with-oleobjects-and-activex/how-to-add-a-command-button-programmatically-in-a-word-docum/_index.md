---
category: general
date: 2026-10-13
description: Apprenez comment ajouter un bouton de commande programmatique en utilisant
  Aspose.Words. Ce guide montre également comment créer un bouton dans un document
  Word avec le code C# complet.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button programmatically
- create word document button
language: fr
lastmod: 2026-10-13
og_description: Ajoutez un bouton de commande de manière programmatique à un document
  Word en utilisant Aspose.Words. Suivez ce tutoriel complet pour créer un bouton
  dans un document Word avec C#.
og_image_alt: Screenshot of a Word document with a command button inserted programmatically
og_title: Ajouter un bouton de commande par programmation à un document Word – guide
  étape par étape
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  headline: How to add a command button programmatically in a Word document
  type: TechArticle
- description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  name: How to add a command button programmatically in a Word document
  steps:
  - name: 'Create a new console project:'
    text: 'Create a new console project:'
  - name: 'Add the Aspose.Words NuGet package:'
    text: 'Add the Aspose.Words NuGet package:'
  - name: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
    text: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Comment ajouter un bouton de commande par programmation dans un document Word
url: /fr/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment ajouter un bouton de commande programmatique dans un document Word  

Si vous devez **ajouter un bouton de commande programmatique**, Aspose.Words fournit une API claire qui vous permet d'intégrer des contrôles de formulaire OLE directement dans un fichier .docx. Ce tutoriel vous guide à travers chaque étape nécessaire pour **créer un bouton dans un document Word** qui se comporte comme un bouton de formulaire ordinaire lorsque le document est ouvert dans Microsoft Word.  

Vous apprendrez comment configurer l'environnement de développement, insérer le bouton, configurer ses propriétés et vérifier le résultat. Aucun utilitaire externe n'est requis — juste un projet .NET et la bibliothèque Aspose.Words pour .NET.  

## Prérequis  

Avant de commencer, assurez-vous d'avoir :  

* SDK .NET 6.0 ou une version ultérieure installé.  
* Une version récente d'Aspose.Words pour .NET (les exemples utilisent la 23.12, mais toute version 22.x+ fonctionne).  
* Un IDE tel que Visual Studio 2022 ou Visual Studio Code.  

Le code fonctionne sous Windows, macOS et Linux car Aspose.Words est indépendant de la plateforme.  

## Étape 1 : Configurer le projet et référencer Aspose.Words  

1. Créer un nouveau projet console :  

   ```bash
   dotnet new console -n WordButtonDemo
   cd WordButtonDemo
   ```  

2. Ajouter le package NuGet Aspose.Words :  

   ```bash
   dotnet add package Aspose.Words
   ```  

3. Ouvrez **Program.cs** et remplacez son contenu par le squelette présenté dans les étapes suivantes.  

Configurer le projet de cette manière garantit que le compilateur peut localiser les espaces de noms `Aspose.Words` et `Aspose.Words.Drawing.Forms` nécessaires aux contrôles de formulaire.  

## Étape 2 : Initialiser un document vierge et un DocumentBuilder  

La classe `Document` représente l'ensemble du fichier Word, tandis que `DocumentBuilder` offre une API fluide pour ajouter du contenu.  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;
using System.Drawing;   // required for RectangleF

// Create an empty document.
Document doc = new Document();

// Create a builder linked to the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```  

*Pourquoi cette étape est importante* – Sans `DocumentBuilder`, vous ne pouvez pas positionner le bouton avec précision sur la page. Le builder respecte également la position actuelle du curseur, ce qui facilite l'insertion de plusieurs contrôles ultérieurement.  

## Étape 3 : Insérer le contrôle OLE du bouton de commande  

Aspose.Words considère un bouton de commande comme un contrôle OLE de type `ControlType.CommandButton`. Vous définissez son emplacement et sa taille avec un `RectangleF` mesuré en points (1 point = 1/72 pouce).  

```csharp
// Define the button rectangle: X=100, Y=150, Width=120, Height=30 (points)
RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

// Insert the command button at the current cursor position.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    buttonRect);
```  

**Points clés**  

* L'origine du rectangle (X, Y) est relative au coin supérieur gauche de la page.  
* Modifier le `Width` ou le `Height` change la taille visuelle du bouton.  
* `InsertForms2OleControl` renvoie un objet `Forms2OleControl` que vous pouvez configurer davantage.  

## Étape 4 : Configurer le nom et la légende du bouton  

Le **nom** est utilisé par le moteur de macros de Word pour identifier le contrôle, tandis que la **légende** est le texte que l'utilisateur voit.  

```csharp
// Set a unique identifier for the button.
commandButton.Name = "cmdSubmit";

// Set the text displayed on the button.
commandButton.Caption = "Submit";
```  

Si vous prévoyez d'ajouter des macros VBA plus tard, utilisez un nom descriptif car l'enregistreur de macros de Word fait référence à cette propriété.  

## Étape 5 : (Facultatif) Enregistrer le document et vérifier le résultat  

Enregistrer le fichier vous permet de l'ouvrir dans Microsoft Word pour confirmer que le bouton apparaît et fonctionne.  

```csharp
// Save the document to the output folder.
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButtonDemo.docx");
doc.Save(outputPath);

Console.WriteLine($"Document saved to: {outputPath}");
```  

Lorsque vous ouvrez *CommandButtonDemo.docx* dans Word, vous devez voir un bouton intitulé **Submit** positionné à environ 1,4 pouces de la marge gauche et 2,1 pouces du haut de la page. Cliquer sur le bouton ne fait rien par défaut car aucune macro n'est attachée, mais le contrôle visuel est pleinement fonctionnel.  

## Étape 6 : Cas limites et pièges courants  

| Situation | Ce qu’il faut surveiller | Correction recommandée |
|-----------|--------------------------|------------------------|
| **Le bouton chevauche du texte existant** | Le rectangle peut intersecter un paragraphe, entraînant des problèmes de mise en page. | Insérez le bouton après avoir appelé `builder.Writeln()` pour déplacer le curseur à une nouvelle ligne, ou ajustez la coordonnée `Y`. |
| **Le document s'ouvre avec un avertissement** | Certaines versions de Word signalent les contrôles OLE qui n'ont pas de programme lié. | Assurez-vous que le type de contrôle est `CommandButton` ; Word le considère comme un élément de formulaire standard et ne nécessite aucun programme externe. |
| **Exécution sous Linux avec un environnement sans interface** | Word ne peut pas être lancé pour tester l'interface, mais le fichier reste valide. | Utilisez un test unitaire qui lit les propriétés du contrôle (`commandButton.Name`, `commandButton.Caption`) pour vérifier qu'elles ont été correctement définies. |
| **Plusieurs boutons nécessaires** | Réutiliser le même `DocumentBuilder` sans déplacer le curseur ajoute le bouton au-dessus du précédent. | Appelez `builder.MoveToDocumentEnd()` ou ajustez la valeur `Y` du rectangle avant chaque insertion. |

Traiter ces cas limites dès le départ permet d'économiser du temps lors de la mise à l'échelle de la solution vers des formulaires complets contenant des dizaines de contrôles.  

## Étape 7 : Exemple complet et exécutable  

Voici un programme autonome que vous pouvez copier, coller et exécuter sans modification (à l'exception de la restauration du package NuGet).  

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

namespace WordButtonDemo
{
    class Program
    {
        static void Main()
        {
            // 1. Create a new empty document.
            Document doc = new Document();

            // 2. Create a DocumentBuilder to work with the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Define the button rectangle (position + size).
            RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

            // 4. Insert the command button OLE control.
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                buttonRect);

            // 5. Set identifying properties.
            commandButton.Name = "cmdSubmit";
            commandButton.Caption = "Submit";

            // 6. Save the document.
            string outputPath = Path.Combine(
                Environment.CurrentDirectory,
                "CommandButtonDemo.docx");
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

**Sortie attendue**  

L'exécution du programme affiche un chemin similaire à :  

```
Document saved to: C:\Path\To\WordButtonDemo\CommandButtonDemo.docx
```  

L'ouverture du *CommandButtonDemo.docx* généré montre un seul bouton **Submit** placé aux coordonnées définies dans le code. Aucun élément d'interface supplémentaire n'apparaît, confirmant que le flux de travail **add command button programmatically** a réussi.  

## Conclusion  

Vous savez maintenant comment **ajouter un bouton de commande programmatique** à un document Word en utilisant Aspose.Words, et vous comprenez également comment **créer un bouton dans un document Word** qui pourra ensuite être relié à des macros VBA ou à des outils d'automatisation externes. Le processus consiste à initialiser un document, insérer un contrôle OLE `CommandButton`, configurer ses propriétés et enregistrer le fichier.  

À partir d'ici, vous pourriez :  

* Ajouter d'autres contrôles (cases à cocher, champs de texte) en répétant l'étape 3 avec différentes valeurs `ControlType`.  
* Attacher des macros VBA au bouton pour effectuer des actions comme enregistrer un formulaire ou envoyer un e‑mail.  
* Générer des formulaires complets dynamiquement en parcourant une collection de définitions de champs basée sur les données.  

Expérimentez avec les coordonnées du rectangle et la légende du bouton pour correspondre à votre conception d'interface. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l'API et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Ajouter un champ de formulaire Combo Box à un document Word avec Aspose.Words pour .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Ajouter un champ de formulaire Check Box à un document Word avec Aspose.Words pour .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)
- [Créer un document Word vierge avec Aspose.Words – Guide étape par étape](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}