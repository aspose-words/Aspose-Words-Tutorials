---
category: general
date: 2026-09-18
description: Créer un document Word vierge en C# et définir un texte de remplacement,
  puis enregistrer le document au format docx. Apprenez à insérer un contrôle de texte
  brut et à ajouter un nom de remplacement.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set placeholder text
- save document as docx
- insert plain text control
- add placeholder name
language: fr
lastmod: 2026-09-18
og_description: Créer un document Word vierge en C#. Définir le texte de l'espace
  réservé, insérer un contrôle de texte brut, ajouter le nom de l'espace réservé et
  enregistrer le document au format docx.
og_image_alt: Screenshot of a Word document showing a plain‑text content control with
  placeholder text
og_title: Créer un document Word vierge avec du texte de substitution – Guide C#
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank Word document using C# and set placeholder text, then
    save document as docx. Learn to insert plain text control and add placeholder
    name.
  headline: Create blank Word document and insert a plain‑text control
  type: TechArticle
- description: Create blank Word document using C# and set placeholder text, then
    save document as docx. Learn to insert plain text control and add placeholder
    name.
  name: Create blank Word document and insert a plain‑text control
  steps:
  - name: An empty Word file (the **blank Word document** you created)
    text: An empty Word file (the **blank Word document** you created)
  - name: A plain‑text content control (the **insert plain text control** step)
    text: A plain‑text content control (the **insert plain text control** step)
  - name: Placeholder text that appears inside the control until the user types something
      (the **set placeholder text** step)
    text: Placeholder text that appears inside the control until the user types something
      (the **set placeholder text** step)
  - name: A placeholder name that can be used for programmatic access later (the **add
      placeholder name** step)
    text: A placeholder name that can be used for programmatic access later (the **add
      placeholder name** step)
  - name: A line of regular text after the control, demonstrating that normal content
      can follow
    text: A line of regular text after the control, demonstrating that normal content
      can follow
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Créer un document Word vierge et insérer un contrôle de texte brut
url: /fr/java/using-document-elements/create-blank-word-document-and-insert-a-plain-text-control/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un document Word vierge et insérer un contrôle de texte brut

Si vous devez **créer un document Word vierge** de manière programmatique, ce guide vous montre comment le faire avec C#. Vous apprendrez à **insérer un contrôle de texte brut**, **définir le texte d’espace réservé**, **ajouter un nom d’espace réservé**, et enfin **enregistrer le document au format docx**. Les étapes sont entièrement autonomes, vous pouvez donc copier le code dans n’importe quel projet .NET et l’exécuter immédiatement.

Travailler avec des fichiers Word nécessite souvent un point de départ propre — un document vide qui contient déjà les contrôles que vos utilisateurs rempliront. À la fin de ce tutoriel, vous disposerez d’un fichier `.docx` contenant un contrôle de contenu texte brut avec un espace réservé utile, suivi d’un contenu normal.

## Prérequis

- .NET 6.0 ou ultérieur (le code fonctionne également avec .NET Framework 4.6+)
- Une référence à la bibliothèque **Aspose.Words for .NET** (disponible via NuGet `Install-Package Aspose.Words`)
- Une connaissance de base des applications console C#
- Permission d’écriture sur le dossier de sortie que vous spécifiez dans `doc.save(...)`

## Ce que vous allez créer

Le document final (`SDT.docx`) contient :

1. Un fichier Word vide (le **document Word vierge** que vous avez créé)
2. Un contrôle de contenu texte brut (l’étape **insérer un contrôle de texte brut**)
3. Le texte d’espace réservé qui apparaît dans le contrôle jusqu’à ce que l’utilisateur saisisse quelque chose (l’étape **définir le texte d’espace réservé**)
4. Un nom d’espace réservé qui peut être utilisé pour un accès programmatique ultérieur (l’étape **ajouter un nom d’espace réservé**)
5. Une ligne de texte normal après le contrôle, démontrant que le contenu ordinaire peut suivre

## Étape 1 : Créer un document Word vierge

La première opération consiste à instancier un objet `Document` vide. Cet objet représente un **document Word vierge** complètement nouveau en mémoire.

```csharp
using Aspose.Words;
using Aspose.Words.BuildingBlocks;

// Step 1: Create a new blank document
Document doc = new Document();
```

*Pourquoi c’est important :* Un `Document` vide vous donne un contrôle total sur chaque élément que vous ajoutez, garantissant qu’aucun style ou section caché n’interfère avec le contrôle de contenu que vous insérerez plus tard.

## Étape 2 : Initialiser un DocumentBuilder

`DocumentBuilder` est la classe d’assistance qui vous permet d’écrire dans le `Document`. Elle suit la position actuelle du curseur et fournit des méthodes pour insérer tous types d’objets Word.

```csharp
// Step 2: Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Pourquoi c’est important :* Utiliser un `DocumentBuilder` simplifie le processus d’ajout d’un **contrôle de texte brut** car le builder connaît le point d’insertion exact.

## Étape 3 : Insérer un contrôle de texte brut

Nous ajoutons maintenant un **contrôle de contenu texte brut** (également appelé Structured Document Tag, ou SDT). Le type de contrôle `StructuredDocumentTagType.PLAIN_TEXT` indique à Word de traiter le contenu comme du texte brut, et non comme une mise en forme riche.

```csharp
// Step 3: Insert a plain‑text StructuredDocumentTag (SDT) with a tag ID
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");
```

*Pourquoi c’est important :* La méthode `InsertStructuredDocumentTag` crée le contrôle et renvoie une référence (`sdt`) que vous pouvez configurer davantage, par exemple en ajoutant du texte d’espace réservé ou un nom personnalisé.

## Étape 4 : Définir le texte d’espace réservé et ajouter un nom d’espace réservé

Le texte d’espace réservé donne aux utilisateurs un indice visuel sur ce qu’ils doivent saisir. L’étape **ajouter un nom d’espace réservé** attribue un identifiant programmatique que vous pouvez interroger plus tard avec `doc.GetChildNodes` ou des API similaires.

```csharp
// Step 4a: Set a placeholder text that appears when the SDT is empty
sdt.SetPlaceholderName("Enter text…");

// Step 4b: Add a placeholder name (tag ID) for later retrieval
sdt.Tag = "MyTag";
```

*Pourquoi c’est important :* `SetPlaceholderName` contrôle le texte d’indice gris affiché à l’intérieur du contrôle de contenu. Définir `Tag` (l’action **ajouter un nom d’espace réservé**) vous permet de localiser le contrôle dans l’arbre du document sans parcourir tout le fichier.

## Étape 5 : Ajouter du contenu normal après le contrôle

Pour prouver que le document continue normalement après le contrôle, nous écrivons une simple ligne de texte.

```csharp
// Step 5: Add regular content after the SDT
builder.Writeln("After the tag.");
```

## Étape 6 : Enregistrer le document au format docx

Enfin, nous persistons le document en mémoire sur le disque. Il s’agit de l’opération **enregistrer le document au format docx** qui génère le fichier que vous pouvez ouvrir dans Microsoft Word.

```csharp
// Step 6: Save the document as a .docx file
string outputPath = @"YOUR_DIRECTORY/SDT.docx";
doc.Save(outputPath);
```

*Pourquoi c’est important :* Utiliser le format `.docx` assure une compatibilité maximale avec les versions modernes de Word, Google Docs et d’autres outils compatibles Office.

## Exemple complet, exécutable

Voici le programme complet que vous pouvez copier dans un projet d’application console. Remplacez `YOUR_DIRECTORY` par un chemin de dossier réel sur votre machine.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.BuildingBlocks;

namespace WordSdtExample
{
    class Program
    {
        static void Main()
        {
            // Create a new blank Word document
            Document doc = new Document();

            // Initialize a DocumentBuilder to work with the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a plain‑text StructuredDocumentTag (SDT) with a tag ID
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");

            // Set a placeholder text that appears when the SDT is empty
            sdt.SetPlaceholderName("Enter text…");

            // Add a placeholder name (tag) for later retrieval
            sdt.Tag = "MyTag";

            // Add regular content after the SDT
            builder.Writeln("After the tag.");

            // Save the document as a .docx file
            string outputPath = @"C:\Temp\SDT.docx"; // change to your folder
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

### Résultat attendu

- L’ouverture de `SDT.docx` dans Word affiche une boîte grise vide avec le texte **Enter text…** à l’intérieur.
- La boîte est un contrôle de contenu texte brut ; vous pouvez y taper directement.
- Sous la boîte, la ligne **After the tag.** apparaît comme texte de paragraphe normal.

Si l’espace réservé n’apparaît pas, vérifiez que vous utilisez une version récente d’Aspose.Words (v23.1 ou ultérieure) et que le document est ouvert dans une version de Word qui prend en charge les contrôles de contenu (Word 2007+).

## Variations courantes et cas limites

| Scenario | How to adapt the code |
|----------|-----------------------|
| **Multiple placeholders** | Appelez `InsertStructuredDocumentTag` à nouveau avec un ID de tag différent et un nom d’espace réservé. |
| **Rich‑text control** | Utilisez `StructuredDocumentTagType.RichText` au lieu de `PlainText`. |
| **Setting default text** | Après l’insertion, attribuez `sdt.Text = "Default value";` – ce texte remplace l’espace réservé lorsque le document se charge. |
| **Saving to a stream** | Remplacez `doc.Save(outputPath);` par `doc.Save(stream, SaveFormat.Docx);` pour envoyer le fichier via HTTP. |
| **Changing placeholder color** | Utilisez `sdt.PlaceholderTextColor = System.Drawing.Color.Gray;` (nécessite `using System.Drawing`). |

## Astuces professionnelles

- **Réutiliser l’ID du tag** : Conserver le tag (`MyTag`) cohérent entre les documents vous permet d’automatiser le remplissage de données plus tard avec `doc.Range.Replace` ou la `StructuredDocumentTagCollection`.
- **Éviter les chemins codés en dur** : Utilisez `Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), "SDT.docx")` pour un emplacement de sortie portable.
- **Performance** : Si vous devez générer des milliers de documents, créez un seul modèle `Document` avec le SDT déjà présent, puis clonez‑le avec `doc.Clone()` pour chaque itération.

## Conclusion

Vous savez maintenant comment **créer un document Word vierge**, **insérer un contrôle de texte brut**, **définir le texte d’espace réservé**, **ajouter un nom d’espace réservé**, et **enregistrer le document au format docx** en utilisant Aspose.Words for .NET. Ce modèle constitue la base pour créer des modèles Word remplis de formulaires, des rapports automatisés, ou toute solution nécessitant des espaces réservés éditables par l’utilisateur.

N’hésitez pas à expérimenter d’autres types de contrôles, à combiner plusieurs espaces réservés, ou à intégrer ce code dans une API web qui renvoie le fichier `.docx` généré directement aux appelants. Pour l’étape suivante, explorez **remplir un contrôle de contenu avec des données programmatique** ou **convertir le fichier Word généré en PDF** en utilisant les fonctionnalités de conversion intégrées d’Aspose.Words. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l’API et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Insérer un champ de saisie de texte dans un document Word](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)
- [Créer un document Word avec un tableau en utilisant Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Créer un document Word avec en-tête et pied de page en utilisant Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}