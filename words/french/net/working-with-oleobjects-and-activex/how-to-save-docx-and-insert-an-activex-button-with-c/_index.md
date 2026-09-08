---
category: general
date: 2026-09-08
description: Comment enregistrer un docx tout en insérant un contrôle ActiveX en C#.
  Suivez ce guide étape par étape pour ajouter un bouton de commande de manière programmatique.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to save docx
- insert activex control
- add activex button
- create word document programmatically
- how to add command button
language: fr
lastmod: 2026-09-08
og_description: Comment enregistrer un docx tout en insérant un contrôle ActiveX en
  C#. Ce tutoriel vous guide à travers la création d’un document Word de manière programmatique,
  l’ajout d’un bouton de commande et la persistance du fichier.
og_image_alt: How to save docx with an ActiveX command button displayed in the document
og_title: Comment enregistrer un docx et intégrer un bouton ActiveX en C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: How to save docx while inserting an ActiveX control in C#. Follow this
    step‑by‑step guide to add a command button programmatically.
  headline: How to save docx and insert an ActiveX button with C#
  type: TechArticle
tags:
- C#
- Word automation
- ActiveX
- Docx
title: Comment sauvegarder un docx et insérer un bouton ActiveX avec C#
url: /fr/net/working-with-oleobjects-and-activex/how-to-save-docx-and-insert-an-activex-button-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment enregistrer un docx et insérer un bouton ActiveX avec C#

Si vous devez créer un document Word de manière programmatique puis enregistrer le docx avec un bouton interactif, ce guide vous montre comment procéder. Vous apprendrez à insérer un contrôle ActiveX, ajouter un bouton ActiveX, et enregistrer le fichier .docx résultant en utilisant C# et la bibliothèque Aspose.Words.

Le tutoriel couvre chaque étape nécessaire pour **create word document programmatically**, intégrer un **command button**, et persister le fichier sur le disque. Aucune expérience préalable avec les objets COM n'est requise, mais vous devez posséder des connaissances de base en C# et avoir Visual Studio installé.

## Prérequis

Before you start, make sure you have:

* .NET 6.0 SDK ou version ultérieure  
* Visual Studio 2022 (ou tout IDE C#)  
* Package NuGet Aspose.Words pour .NET (`Install-Package Aspose.Words`)  
* Compréhension de la structure d'un projet C#  

Ces éléments garantissent que le code se compile et s'exécute sans configuration supplémentaire.

## Étape 1 : Configurer un nouveau projet console C#

Créez une application console qui hébergera la logique d'automatisation Word.

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
dotnet add package Aspose.Words
```

La commande ci‑dessus crée un dossier nommé **WordActiveXDemo**, ajoute la référence Aspose.Words, et prépare le projet pour la compilation.

## Étape 2 : Créer un document Word programmatique

Ouvrez le fichier `Program.cs` généré et ajoutez les directives `using` requises.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;   // not used directly but required for some overloads
```

Instanciez maintenant un objet `Document` vierge. Cet objet représente l'intégralité du fichier Word en mémoire.

```csharp
// Step 2: Create a new blank document
Document document = new Document();
```

La classe `Document` est le point d'entrée pour toutes les opérations de traitement Word. À ce stade, le document ne contient aucune page, mais Aspose.Words créera automatiquement une section par défaut lorsque vous ajouterez du contenu.

## Étape 3 : Insérer un contrôle ActiveX – ajouter un bouton activex

Un objet **Forms2OleControl** vous permet d'intégrer un contrôle ActiveX dans un paragraphe Word. Le code suivant insère un **CommandButton** d'une largeur de 150 pt et d'une hauteur de 30 pt.

```csharp
// Step 3: Initialize a DocumentBuilder to edit the document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert an ActiveX CommandButton control with the desired size
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton, 150, 30);
```

`InsertForms2OleControl` crée le contrôle et renvoie une instance fortement typée `Forms2OleControl`, que vous pouvez configurer davantage. La méthode ajoute automatiquement un nouveau paragraphe pour héberger le contrôle, vous n'avez donc pas besoin de gérer les objets paragraphe manuellement.

## Étape 4 : Configurer le bouton de commande – comment ajouter les propriétés du bouton de commande

Définissez les propriétés **Name** et **Caption** du bouton pour le rendre identifiable à l'exécution et convivial dans l'interface utilisateur.

```csharp
// Step 4: Set the control's name and caption
commandButton.Name = "cmdSubmit";
commandButton.Caption = "Submit";
```

L'attribut `Name` est utile lorsque vous gérez ultérieurement l'événement de clic du bouton via VBA ou une macro Word. La `Caption` est le texte que l'utilisateur final voit sur la surface du bouton.

### Astuce pro
Si vous prévoyez d'automatiser la gestion du clic depuis C#, intégrez une macro VBA qui référence `cmdSubmit`. Word demandera à l'utilisateur d'activer les macros à l'ouverture du document, ce qui est le comportement de sécurité standard pour les contrôles ActiveX.

## Étape 5 : Comment enregistrer le docx

Une fois le contrôle en place, persistez le document dans un fichier .docx. La méthode `Save` choisit automatiquement le format approprié en fonction de l'extension du fichier.

```csharp
// Step 5: Save the document containing the CommandButton
string outputPath = @"C:\Temp\CommandButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

L'enregistrement du fichier complète le flux de travail **how to save docx**. Le fichier résultant peut être ouvert dans Microsoft Word, où le bouton ActiveX apparaîtra sur la première page. Lorsque vous cliquez sur le bouton, Word affichera un message de substitution à moins qu'une macro ne soit attachée.

## Étape 6 : Exécuter le programme et vérifier le résultat

Compilez et exécutez l'application console :

```bash
dotnet run
```

Après la fin du programme, ouvrez `C:\Temp\CommandButton.docx` dans Microsoft Word :

* Le document contient une seule page avec un bouton **Submit** près du haut.  
* Passer la souris sur le bouton affiche l'infobulle avec le nom `cmdSubmit`.  
* Aucun contenu n'est perdu, et la taille du fichier est comparable à celle d'un .docx vierge standard.

Si le bouton n'apparaît pas, vérifiez que :

1. Les paramètres du **Trust Center** de Word autorisent les contrôles ActiveX.  
2. Le fichier a été enregistré avec l'extension `.docx` (et non `.doc`).  

## Cas limites et variations courantes

| Situation | Ajustement recommandé |
|-----------|------------------------|
| Vous avez besoin d'une taille de bouton différente | Modifiez les arguments de largeur et de hauteur dans `InsertForms2OleControl`. |
| Vous voulez le bouton sur une page spécifique | Utilisez `builder.MoveToDocumentEnd();` après avoir ajouté des pages, ou insérez un saut de page avant le contrôle. |
| Vous devez prendre en charge des environnements sans Aspose.Words | Utilisez le SDK Open XML pour insérer un élément `w:object`, mais le code devient considérablement plus complexe. |
| Un document activé par macro est requis | Enregistrez avec l'extension `.docm` (`document.Save("MyDoc.docm");`) et intégrez un module VBA qui gère `cmdSubmit_Click`. |

## Code source complet

Ci‑dessus se trouve le programme complet et autonome que vous pouvez copier dans `Program.cs` et exécuter sans modifications (sauf le chemin de sortie).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document
            Document document = new Document();

            // Initialize a DocumentBuilder to edit the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert an ActiveX CommandButton control with the desired size
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, 150, 30);

            // Set the control's name and caption
            commandButton.Name = "cmdSubmit";
            commandButton.Caption = "Submit";

            // Save the document containing the CommandButton
            string outputPath = @"C:\Temp\CommandButton.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Sortie attendue dans la console

```
Document saved to C:\Temp\CommandButton.docx
```

L'ouverture du fichier dans Word affiche un bouton intitulé **Submit**. Cliquer sur le bouton déclenche le comportement ActiveX par défaut (une boîte de dialogue indiquant qu'aucune macro n'est attachée).

## Conclusion

Ce tutoriel a démontré **how to save docx** tout en intégrant un **ActiveX control**, spécifiquement un **add activex button** qui fonctionne comme un bouton de commande. Vous savez maintenant comment **create word document programmatically**, configurer les propriétés du bouton, et persister le fichier pour l'interaction avec l'utilisateur final.

À partir d'ici, vous pouvez explorer :

* Ajouter des macros VBA pour gérer `cmdSubmit_Click`.  
* Insérer d'autres contrôles ActiveX tels que des cases à cocher ou des listes déroulantes.  
* Générer des documents multi‑pages avec plusieurs éléments interactifs.  

Expérimentez différents types de contrôles et options de mise en page pour créer des modèles Word riches et interactifs qui rationalisent vos processus métier.

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Aspose.Words – Enregistrer le docx en txt et exporter les équations Word en LaTeX – Guide complet](/words/english/net/basic-conversions/save-docx-as-txt-complete-guide-to-export-word-equations-as/)
- [Comment récupérer un docx – Guide C# pour les fichiers Word corrompus](/words/english/net/programming-with-loadoptions/how-to-recover-docx-c-guide-for-corrupted-word-files/)
- [Comment enregistrer Word en Markdown – Guide complet C#](/words/english/net/programming-with-markdownsaveoptions/how-to-save-word-as-markdown-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}