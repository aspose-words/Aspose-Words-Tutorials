---
category: general
date: 2026-10-20
description: Définissez du texte de substitution dans un document Word à l'aide de
  C#. Apprenez comment ajouter un contrôle et définir rapidement un texte de substitution
  avec Aspose.Words pour .NET.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set placeholder text
- how to add control
- how to set placeholder
- generate word c#
language: fr
lastmod: 2026-10-20
og_description: Définissez du texte de remplacement dans un document Word avec C#.
  Ce tutoriel vous montre comment ajouter un contrôle, définir un texte de remplacement
  et générer des fichiers Word de manière programmatique.
og_image_alt: Screenshot of a Word document showing placeholder text created with
  C# code
og_title: Définir du texte de remplacement dans un document Word avec C# – guide étape
  par étape
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Set placeholder text in a Word document using C#. Learn how to add
    control and set placeholder quickly with Aspose.Words for .NET.
  headline: Set placeholder text in a Word document using C#
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for .NET is compatible with .NET Core, .NET 5, and .NET
      6+. The same code runs unchanged.
    question: Does this work with .NET Core?
  - answer: Use `sdt.SetText("Default value")` after creating the SDT. The placeholder
      disappears once a value is set.
    question: Can I set a default value in addition to the placeholder?
  - answer: 'Load the document, locate the SDT by its `Title` (`doc.GetChildNodes(NodeType.StructuredDocumentTag,
      true)`) and read `sdt.GetText()`. ## Conclusion You now know how to **set placeholder
      text** in a Word document using C#. By creating a plain‑text `StructuredDocumentTag`,
      assigning a title and place'
    question: What if I need to retrieve the entered value later?
  type: FAQPage
tags:
- C#
- Aspose.Words
- Word automation
- Content control
title: Définir le texte d’espace réservé dans un document Word avec C#
url: /fr/net/programming-with-sdt/set-placeholder-text-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Définir du texte de remplacement dans un document Word avec C#

Si vous devez **définir du texte de remplacement** dans un fichier Microsoft Word lors de sa génération avec C#, ce guide vous montre exactement comment faire. Vous verrez une solution concise, de bout en bout, qui ajoute un contrôle de contenu, définit son texte de remplacement et enregistre le document — le tout avec Aspose.Words pour .NET.

De nombreux développeurs se demandent **comment ajouter un contrôle** à un document Word ou **comment définir un texte de remplacement** sans ouvrir Word manuellement. Ce tutoriel répond à ces questions et montre également une méthode propre pour **générer des fichiers Word C#** prêts à recevoir des entrées utilisateur.

## Ce que vous allez accomplir

* Créer un document Word vierge de manière programmatique.
* Insérer un Structured Document Tag (SDT) en texte brut, qui est le nom technique d’un contrôle de contenu.
* Attribuer un titre significatif et un texte de remplacement au SDT.
* Enregistrer le fichier `.docx` résultant sur le disque.

Aucun outil supplémentaire n’est requis au-delà de la bibliothèque Aspose.Words et d’un environnement de développement .NET 6 (ou ultérieur).

## Prérequis

* SDK .NET 6 ou plus récent installé.  
* Visual Studio 2022 (ou tout IDE supportant .NET).  
* Package NuGet Aspose.Words pour .NET (`Install-Package Aspose.Words`).  

> **Conseil pro :** Utilisez la version d’évaluation gratuite d’Aspose.Words si vous ne faites que tester ; elle ajoute un filigrane mais fonctionne autrement de la même façon que la version sous licence.

## Étape 1 : Configurer le projet et importer les espaces de noms

Créez un nouveau projet console et ajoutez les directives `using` requises. Elles mettent à disposition les classes principales d’Aspose.Words ainsi que l’espace de noms du balisage.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // The complete solution starts here.
        }
    }
}
```

*Pourquoi cette étape est importante :* L’importation de `Aspose.Words.Markup` vous donne accès à `StructuredDocumentTag`, `SdtType` et `MarkupLevel` — les objets nécessaires pour **ajouter un contrôle** et **définir un texte de remplacement**.

## Étape 2 : Créer un document vierge et un DocumentBuilder

Un `Document` représente l’ensemble du fichier Word, tandis qu’un `DocumentBuilder` fournit un curseur pratique pour insérer des éléments.

```csharp
// Step 2: Initialize a new empty document.
Document doc = new Document();

// DocumentBuilder starts at the beginning of the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Pourquoi cette étape est importante :* Commencer avec un document vierge garantit que le texte de remplacement que vous définissez apparaît exactement à l’endroit souhaité, sans interférence du contenu existant.

## Étape 3 : Créer le contrôle de contenu (Structured Document Tag)

Ici nous créons un SDT en texte brut, lui attribuons un titre et définissons le texte de remplacement que l’utilisateur verra lorsque le contrôle sera vide.

```csharp
// Step 3: Build a plain‑text Structured Document Tag (SDT).
StructuredDocumentTag sdt = new StructuredDocumentTag(
    doc,                     // Parent document
    SdtType.PlainText,       // Control type – plain text box
    MarkupLevel.Inline);     // Inline placement (behaves like a word)

sdt.Title = "CustomerName";                 // Logical name for the control
sdt.PlaceholderName = "Enter name here";    // Text shown when empty
```

*Pourquoi cette étape est importante :* La propriété `Title` vous permet de référencer le contrôle ultérieurement (par ex., pour la liaison de données). `PlaceholderName` correspond exactement au **texte de remplacement** que vous souhaitez afficher, guidant l’utilisateur final.

## Étape 4 : Insérer le contrôle à la position actuelle du curseur

En utilisant le `DocumentBuilder`, insérez le SDT dans le document à l’endroit où le builder est actuellement positionné.

```csharp
// Step 4: Insert the SDT into the document.
builder.InsertNode(sdt);
```

*Pourquoi cette étape est importante :* L’insertion du nœud attache le contrôle au DOM du document. Si vous devez ajouter plusieurs textes de remplacement, vous pouvez déplacer le curseur du builder et répéter cette étape.

## Étape 5 : Enregistrer le document

Enfin, écrivez le document sur le disque. Remplacez `YOUR_DIRECTORY` par un chemin réel sur votre machine.

```csharp
// Step 5: Save the .docx file.
string outputPath = @"C:\Temp\SDT.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Lorsque vous ouvrez `SDT.docx` dans Microsoft Word, vous verrez une zone de texte en ligne ombrée en gris contenant le texte **Enter name here**. Cliquer à l’intérieur de la zone supprime le texte de remplacement, permettant à l’utilisateur de saisir un nom de client.

### Résultat attendu

| Emplacement du fichier | Aperçu du contenu |
|------------------------|-------------------|
| `C:\Temp\SDT.docx` | Placeholder en ligne **Enter name here** à l'intérieur d'un contrôle de contenu en texte brut intitulé *CustomerName*. |

## Cas limites et variantes

| Situation | Ajustement recommandé |
|-----------|------------------------|
| **Plusieurs textes de remplacement** | Créer des objets `StructuredDocumentTag` supplémentaires avec des valeurs `Title` et `PlaceholderName` différentes, puis insérer chacun là où c’est nécessaire. |
| **Texte de remplacement enrichi** | Utiliser `SdtType.RichText` au lieu de `PlainText` pour autoriser le formatage à l’intérieur du texte de remplacement. |
| **Contrôle de niveau bloc** | Changer `MarkupLevel.Inline` en `MarkupLevel.Block` pour que le contrôle se comporte comme un paragraphe complet. |
| **Texte de remplacement non visible** | Vérifiez que les paramètres d’affichage du document dans Word ne sont pas configurés pour masquer les contrôles de contenu (`File → Options → Advanced → Show content controls`). |
| **Enregistrement dans un flux** | Appeler `doc.Save(stream, SaveFormat.Docx)` si vous devez envoyer le fichier via HTTP au lieu de l’écrire sur le disque. |

## Exemple complet, exécutable

Voici le programme complet que vous pouvez copier, coller et exécuter. Il inclut toutes les étapes ci‑dessus dans une seule méthode `Main`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank document.
            Document doc = new Document();

            // 2️⃣ Position a builder at the start of the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Define a plain‑text content control (SDT) with placeholder text.
            StructuredDocumentTag sdt = new StructuredDocumentTag(
                doc,
                SdtType.PlainText,
                MarkupLevel.Inline);

            sdt.Title = "CustomerName";                 // Logical identifier
            sdt.PlaceholderName = "Enter name here";    // The placeholder you see in Word

            // 4️⃣ Insert the SDT into the document.
            builder.InsertNode(sdt);

            // 5️⃣ Save the document to disk.
            string outputPath = @"C:\Temp\SDT.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document successfully saved to {outputPath}");
        }
    }
}
```

Exécutez le programme, ouvrez le fichier généré, et vous verrez le texte de remplacement prêt à être saisi par l’utilisateur.

## Questions fréquentes

**Q : Cela fonctionne-t-il avec .NET Core ?**  
R : Oui. Aspose.Words pour .NET est compatible avec .NET Core, .NET 5 et .NET 6+. Le même code s’exécute sans modification.

**Q : Puis‑je définir une valeur par défaut en plus du texte de remplacement ?**  
R : Utilisez `sdt.SetText("Default value")` après la création du SDT. Le texte de remplacement disparaît dès qu’une valeur est définie.

**Q : Et si je dois récupérer la valeur saisie plus tard ?**  
R : Chargez le document, localisez le SDT par son `Title` (`doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`) et lisez `sdt.GetText()`.

## Conclusion

Vous savez maintenant comment **définir du texte de remplacement** dans un document Word avec C#. En créant un `StructuredDocumentTag` en texte brut, en attribuant un titre et un texte de remplacement, en l’insérant avec un `DocumentBuilder` et en enregistrant le fichier, vous pouvez **ajouter un contrôle** et **générer des fichiers Word C#** de manière programmatique.  

À partir d’ici, vous pouvez explorer :

* Ajouter des contrôles de texte enrichi ou des listes déroulantes (`SdtType.RichText`, `SdtType.DropDownList`).  
* Remplir plusieurs textes de remplacement à partir d’une base de données.  
* Convertir le `.docx` généré en PDF avec Aspose.Words.

Expérimentez différents types de contrôles et styles de texte de remplacement pour répondre aux besoins de votre application. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Définir le texte de remplacement dans Aspose.Words – Guide complet C#](/words/english/net/programming-with-sdt/set-placeholder-text-in-aspose-words-complete-c-guide/)
- [Créer un document Word programmatique – ajouter un contrôle de contenu et un texte de remplacement](/words/english/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/)
- [Comment ajouter un contrôle de contenu et créer un document Word avec Aspose – Complet](/words/english/net/programming-with-sdt/how-to-add-content-control-and-create-word-document-with-asp/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}