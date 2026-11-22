---
category: general
date: 2026-11-22
description: Définir le texte d’espace réservé dans un contrôle de contenu Word avec
  C#. Apprenez à créer une balise personnalisée, insérer un contrôle de texte brut
  et ajouter un espace réservé à la balise à l’aide d’Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set placeholder text
- create custom tag
- how to insert content control
- add placeholder to tag
- insert plain text control
language: fr
lastmod: 2026-11-22
og_description: Définissez le texte d’espace réservé dans un contrôle de contenu Word
  avec C#. Ce tutoriel vous montre comment créer une balise personnalisée, insérer
  un contrôle de texte brut et ajouter un espace réservé à la balise pour améliorer
  l’interactivité du document.
og_image_alt: Screenshot showing a Word document with a content control placeholder
  text set using C#
og_title: Définir le texte d’espace réservé dans un contrôle de contenu Word – Guide
  C#
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Set placeholder text in a Word content control with C#. Learn how to
    create a custom tag, insert a plain text control, and add placeholder to tag using
    Aspose.Words.
  headline: Set placeholder text in a Word content control with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Content Control
- Word Automation
title: Définir le texte de l’espace réservé dans un contrôle de contenu Word avec
  C#
url: /fr/java/using-document-elements/set-placeholder-text-in-a-word-content-control-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Définir le texte d'espace réservé dans un contrôle de contenu Word avec C#

Si vous devez **définir le texte d'espace réservé** dans un document Word de façon programmatique, ce guide vous montre exactement comment le faire. En utilisant Aspose.Words for .NET, vous pouvez créer une balise personnalisée, insérer un contrôle de texte brut, et ajouter un espace réservé à la balise afin que le document soit prêt pour la saisie de l'utilisateur.

Dans ce tutoriel, vous apprendrez comment **créer une balise personnalisée**, **insérer un contrôle de contenu**, et **ajouter un espace réservé à la balise** tout en gardant le code concis et prêt pour la production. Aucun outil externe n'est requis — seulement un projet .NET et la bibliothèque Aspose.Words.

## Prérequis

* SDK .NET 6.0 ou version ultérieure installé  
* Une licence valide d'Aspose.Words for .NET (ou une clé d'évaluation gratuite)  
* Familiarité de base avec C# et Visual Studio (ou tout IDE de votre choix)  

Les sections suivantes supposent que vous avez créé un projet console nommé `WordPlaceholderDemo`.

## Étape 1 : Installer Aspose.Words

Ajoutez le package NuGet à votre projet :

```bash
dotnet add package Aspose.Words
```

> **Astuce :** Utilisez le drapeau `--version` pour verrouiller le package à la dernière version stable (par ex., `Aspose.Words.NET 24.9`).

## Étape 2 : Charger le document source et créer un `DocumentBuilder`

La première chose à faire est de charger un fichier `.docx` existant (ou de créer un nouveau document vide) et d'instancier un `DocumentBuilder`. Le builder vous fournit une API fluide pour insérer des contrôles et du texte.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Building;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // Load an existing Word file or create a new one
            Document doc = new Document("input.docx");   // <-- replace with your path
            DocumentBuilder builder = new DocumentBuilder(doc);
```

Ce code **prépare le terrain** pour insérer un contrôle de contenu. Le `DocumentBuilder` travaille directement sur l'objet `doc`, de sorte que toutes les modifications que vous apportez sont automatiquement reflétées.

## Étape 3 : Créer une balise personnalisée (StructuredDocumentTag)

Une *balise personnalisée* dans Word s'appelle un **StructuredDocumentTag (SDT)**. Vous pouvez la considérer comme un contrôle de contenu qui porte un identifiant unique. En créer une constitue le cœur de l'étape **créer une balise personnalisée**.

```csharp
            // Insert a plain‑text StructuredDocumentTag (SDT) with a tag identifier
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");
```

La méthode `InsertStructuredDocumentTag` prend deux arguments :

1. Le type de contrôle (`PlainText` dans ce cas).  
2. Une chaîne qui identifie de façon unique la balise (`"MyTag"`).  

En utilisant une **balise personnalisée**, vous pouvez ensuite localiser ou manipuler le contrôle de façon programmatique.

## Étape 4 : Définir un titre pour l'accessibilité

Un titre améliore l'accessibilité et rend le contrôle plus facile à trouver dans l'interface Word.

```csharp
            // Set a descriptive title (used by screen readers)
            sdt.Title = "CustomerName";
```

La propriété `Title` est optionnelle, mais l'ajouter constitue une bonne pratique lorsque vous **ajoutez un espace réservé à la balise** pour une meilleure expérience utilisateur.

## Étape 5 : Ajouter du texte d'espace réservé à la balise

Voici le principal objectif : **définir le texte d'espace réservé**. Ce texte apparaît lorsque le contrôle est vide, guidant l'utilisateur sur ce qu'il doit saisir.

```csharp
            // Provide placeholder text that shows when the tag is empty
            sdt.PlaceholderText = "Enter name…";
```

La propriété `PlaceholderText` est exactement ce dont vous avez besoin pour **ajouter un espace réservé à la balise**. Elle se comporte comme l'indice gris que l'on voit dans les champs de formulaire modernes.

## Étape 6 : Enregistrer le document modifié

Après avoir configuré le contrôle, écrivez le document sur le disque.

```csharp
            // Save the document with the new content control
            doc.Save("output.docx");   // <-- replace with your desired path
        }
    }
}
```

Lorsque vous ouvrez `output.docx` dans Microsoft Word, vous verrez un contrôle de contenu texte brut intitulé « CustomerName » avec l'espace réservé « Enter name… ». Cliquer à l'intérieur du contrôle supprime l'espace réservé, permettant à l'utilisateur de saisir du texte.

### Résultat attendu

* Un fichier Word (`output.docx`) contenant un seul contrôle de contenu texte brut.  
* Le contrôle affiche l'espace réservé « Enter name… » jusqu'à ce que l'utilisateur saisisse quelque chose.  
* L'identifiant de balise du contrôle est `MyTag`, que vous pouvez interroger plus tard avec `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`.

## Étape 7 : Comment insérer un contrôle de contenu ailleurs (avancé)

Si vous devez **insérer un contrôle de contenu** à un emplacement spécifique — par exemple, après un paragraphe particulier — utilisez la méthode `MoveTo` avant d'insérer la balise :

```csharp
            // Move the cursor to the end of the first paragraph
            builder.MoveTo(doc.FirstSection.Body.Paragraphs[0].End);
            // Insert another plain‑text control with a different tag
            StructuredDocumentTag addressTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "AddressTag");
            addressTag.Title = "CustomerAddress";
            addressTag.PlaceholderText = "Enter address…";
```

Cet extrait montre **l'insertion d'un contrôle texte brut** plusieurs fois dans le même document.

## Pièges courants et comment les éviter

| Problème | Pourquoi cela se produit | Solution |
|----------|--------------------------|----------|
| Espace réservé non visible | Le contrôle contient déjà du texte (même un espace) | Assurez-vous que `sdt.Text` est vide avant de définir `PlaceholderText`. |
| Collision d'identifiant de balise | Réutilisation du même nom de balise (`MyTag`) dans le même document | Utilisez des identifiants uniques pour chaque `StructuredDocumentTag`. |
| Exception de licence | Exécution sans licence Aspose.Words valide | Appliquez un fichier de licence (`license.SetLicense("Aspose.Words.lic")`) au début de `Main`. |
| Document non enregistré | Oubli d'appeler `doc.Save` ou utilisation d'un chemin en lecture seule | Vérifiez que le chemin de sortie est inscriptible et appelez `doc.Save`. |

## Exemple complet fonctionnel

Ci-dessous se trouve le programme complet que vous pouvez copier‑coller dans `Program.cs`. Il inclut toutes les étapes — **créer une balise personnalisée**, **insérer un contrôle de contenu**, **ajouter un espace réservé à la balise**, et **insérer un contrôle texte brut** — dans un flux cohérent.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Building;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // Optional: apply your Aspose.Words license here
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // Load the source document (or create a new one)
            Document doc = new Document("input.docx");
            DocumentBuilder builder = new DocumentBuilder(doc);

            // --------- Create custom tag ----------
            StructuredDocumentTag nameTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");
            nameTag.Title = "CustomerName";
            nameTag.PlaceholderText = "Enter name…";

            // Insert a second control after the first paragraph
            builder.MoveTo(doc.FirstSection.Body.Paragraphs[0].End);
            StructuredDocumentTag addressTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "AddressTag");
            addressTag.Title = "CustomerAddress";
            addressTag.PlaceholderText = "Enter address…";

            // Save the result
            doc.Save("output.docx");
            Console.WriteLine("Document saved with placeholder text set.");
        }
    }
}
```

Exécutez le programme avec `dotnet run`. Après l'exécution, ouvrez `output.docx` pour vérifier que les deux contrôles affichent leurs espaces réservés respectifs.

## Prochaines étapes

* **Personnaliser l'apparence** – Utilisez `sdt.Font` pour modifier la taille, la couleur ou le style de police à l'intérieur du contrôle.  
* **Lier à des données XML** – Explorez `sdt.XmlMapping` si vous avez besoin que le contrôle soit mappé  

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Créer un document Word programmatique – ajouter un contrôle de contenu et un espace réservé](/words/english/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/)
- [Définir le texte d'espace réservé dans Aspose.Words – Guide complet C#](/words/english/net/programming-with-sdt/set-placeholder-text-in-aspose-words-complete-c-guide/)
- [Créer un nouveau document Word et insérer un contrôle de contenu en C#](/words/english/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}