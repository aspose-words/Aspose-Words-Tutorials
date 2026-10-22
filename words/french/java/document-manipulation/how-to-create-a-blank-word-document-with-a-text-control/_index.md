---
category: general
date: 2026-09-21
description: Apprenez à créer un document Word vierge, à ajouter un contrôle de texte
  brut, à définir un texte d’espace réservé et à enregistrer le fichier docx à l’aide
  d’Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set placeholder text
- save docx file
- add plain text control
language: fr
lastmod: 2026-09-21
og_description: Créez un document Word vierge, ajoutez un contrôle de texte brut,
  définissez un texte d’espace réservé, puis enregistrez le fichier docx avec Aspose.Words.
  Suivez ce tutoriel complet.
og_image_alt: Screenshot showing a blank Word document created to set placeholder
  text in a text control
og_title: Créer un document Word vierge et ajouter un contrôle de texte – guide étape
  par étape
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create a blank Word document, add a plain text control,
    set placeholder text, and save the docx file using Aspose.Words.
  headline: How to create a blank Word document with a text control
  type: TechArticle
tags:
- Aspose.Words
- Word automation
- .NET
- Document generation
title: Comment créer un document Word vierge avec un contrôle de texte
url: /fr/java/document-manipulation/how-to-create-a-blank-word-document-with-a-text-control/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer un document Word vierge avec un contrôle de texte

Si vous devez **créer un document Word vierge** de manière programmatique, ce guide vous montre exactement comment faire. Vous verrez comment ajouter un contrôle de texte brut, définir un texte d’espace réservé, puis **enregistrer le fichier docx** sur le disque.

Dans les sections ci‑dessous, vous apprendrez le flux de travail complet, depuis l’initialisation du document jusqu’à la vérification que l’espace réservé apparaît lorsque le fichier est ouvert dans Microsoft Word. Les étapes fonctionnent avec Aspose.Words .NET 2024‑R2, mais les concepts s’appliquent à toute bibliothèque de génération de documents .NET.

## Ce dont vous avez besoin

- .NET 6.0 ou ultérieur (le code fonctionne également avec .NET Framework 4.8)  
- Aspose.Words for .NET (package NuGet `Aspose.Words`)  
- Un IDE tel que Visual Studio ou VS Code  
- Connaissances de base en C#  

> **Astuce :** Installez le package NuGet avec `dotnet add package Aspose.Words` pour garder votre projet propre.

## Étape 1 : Créer un document Word vierge

La première opération consiste à instancier un `Document` vide. Cet objet représente un **document Word vierge** qui ne contient aucune section, paragraphe ou style.

```csharp
using Aspose.Words;
using Aspose.Words.BuildingBlocks;

// Create a new blank document
Document doc = new Document();
```

Créer un document vierge vous donne une toile propre, indispensable lorsque vous souhaitez un contrôle total sur la mise en page des contrôles insérés.

## Étape 2 : Ajouter un contrôle de texte brut

Un Structured Document Tag (SDT) de type texte brut fonctionne comme un contrôle de contenu dans Word. Il vous permet d’imposer un type de donnée spécifique et d’afficher une indication lorsque le champ est vide.

```csharp
using Aspose.Words.Markup;

// Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a plain‑text StructuredDocumentTag at block level
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, MarkupLevel.Block);
```

La méthode `InsertStructuredDocumentTag` renvoie un objet `StructuredDocumentTag`, que vous pouvez configurer davantage. Ajouter un **contrôle de texte brut** au niveau du bloc garantit que le contrôle se comporte comme un paragraphe distinct, ce qui facilite son style ultérieur.

## Étape 3 : Définir le texte d’espace réservé pour le contrôle

Le texte d’espace réservé guide l’utilisateur pour saisir les informations correctes. Dans Word, il apparaît en texte gris clair jusqu’à ce que l’utilisateur saisisse quelque chose.

```csharp
// Set a title (used for identification in the Word UI)
sdt.Title = "CustomerName";

// Set the placeholder that the user sees
sdt.PlaceholderName = "Enter name";
```

Ici, nous **définissons le texte d’espace réservé** à l’aide de la propriété `PlaceholderName`. La propriété `Title` est optionnelle mais utile pour un accès programmatique ultérieur, notamment si vous devez localiser le contrôle dans un document plus volumineux.

## Étape 4 : Ajouter du contenu normal après le contrôle

Il est souvent nécessaire de continuer à écrire après le contrôle. La méthode `DocumentBuilder.Writeln` ajoute un nouveau paragraphe contenant le texte fourni.

```csharp
// Write a normal paragraph after the SDT
builder.Writeln("After the SDT");
```

Cela montre que le document reste modifiable après l’insertion du contrôle, et que vous pouvez mélanger librement paragraphes ordinaires et contrôles de contenu.

## Étape 5 : Enregistrer le fichier docx

Enfin, persistez le document en mémoire dans un fichier physique. La méthode `Save` détermine automatiquement le format à partir de l’extension du fichier.

```csharp
// Save the document to a .docx file
string outputPath = @"C:\Temp\SDTExample.docx";
doc.Save(outputPath);
```

Après l’exécution du programme, ouvrez `SDTExample.docx` dans Microsoft Word. Vous verrez un document vide avec un **contrôle de texte brut** affichant « Enter name » comme texte d’espace réservé, suivi de la ligne « After the SDT ».

### Résultat attendu

Lorsque le fichier est ouvert :

1. La première ligne est un espace réservé grisé affichant **Enter name** à l’intérieur d’une boîte de contrôle de contenu.  
2. La deuxième ligne affiche **After the SDT** comme paragraphe normal.

Si vous tapez un nom et appuyez sur **Enter**, l’espace réservé disparaît, confirmant que le contrôle fonctionne comme prévu.

## Variations courantes et cas limites

| Situation | Ce qu’il faut modifier |
|-----------|------------------------|
| **Plusieurs espaces réservés** | Appelez `InsertStructuredDocumentTag` plusieurs fois et attribuez des valeurs différentes à `Title`/`PlaceholderName`. |
| **Contrôle en ligne** | Utilisez `MarkupLevel.Inline` au lieu de `MarkupLevel.Block`. |
| **Contrôle de texte enrichi** | Remplacez `StructuredDocumentTagType.PlainText` par `StructuredDocumentTagType.RichText`. |
| **Enregistrement dans un flux** | Utilisez `doc.Save(stream, SaveFormat.Docx)` lorsque vous devez transmettre le fichier via HTTP. |

> **Attention :** Tenter de définir `PlaceholderName` sur un SDT de type `RichText` lève une `ArgumentException`. Seuls les contrôles de texte brut prennent en charge les espaces réservés.

## Exemple complet fonctionnel

```csharp
using System;
using Aspose.Words;
using Aspose.Words.BuildingBlocks;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank document
        Document doc = new Document();

        // Step 2: Prepare a builder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a plain‑text control (SDT)
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            StructuredDocumentTagType.PlainText, MarkupLevel.Block);

        // Step 4: Set title and placeholder text
        sdt.Title = "CustomerName";
        sdt.PlaceholderName = "Enter name";

        // Step 5: Add normal content after the control
        builder.Writeln("After the SDT");

        // Step 6: Save the document
        string path = @"C:\Temp\SDTExample.docx";
        doc.Save(path);

        Console.WriteLine($"Document saved to {path}");
    }
}
```

L’exécution du programme produit le fichier décrit dans la section *Résultat attendu* ci‑dessus.

## Conclusion

Vous savez maintenant comment **créer un document Word vierge**, **ajouter un contrôle de texte brut**, **définir un texte d’espace réservé**, et **enregistrer le fichier docx** à l’aide d’Aspose.Words. Cette solution de bout en bout vous permet de générer des modèles Word qui guident les utilisateurs avec des indications claires, rendant l’automatisation de documents fiable et conviviale.

**Prochaines étapes**

- Explorez les variations **add plain text control** telles que les contrôles en ligne ou les balises de texte enrichi.  
- Combinez plusieurs espaces réservés pour créer des formulaires complets (par ex., blocs d’adresse, dates).  
- Utilisez le `DocumentBuilder` pour appliquer des styles ou fusionner des données depuis une base de données, en étendant le flux **save docx file**.

N’hésitez pas à expérimenter avec différentes valeurs d’espace réservé et types de contrôle — la génération de documents est un moyen puissant d’automatiser les rapports, contrats et tout autre rendu Word récurrent. Bon codage !

## Que devriez‑vous apprendre ensuite ?


Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser des fonctionnalités supplémentaires de l’API et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}