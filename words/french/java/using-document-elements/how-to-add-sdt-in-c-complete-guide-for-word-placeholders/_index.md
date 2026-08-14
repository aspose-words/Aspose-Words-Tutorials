---
category: general
date: 2026-08-14
description: Comment ajouter rapidement un SDT avec Aspose.Words. Apprenez à créer
  un espace réservé Word et à insérer un contrôle de texte brut dans un fichier .docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add sdt
- create word placeholder
- insert plain text control
- Aspose.Words SDT
- C# Word automation
language: fr
lastmod: 2026-08-14
og_description: Comment ajouter un SDT en C# avec Aspose.Words. Suivez ce tutoriel
  pour créer un espace réservé Word et insérer un contrôle de texte simple pour des
  documents dynamiques.
og_image_alt: Screenshot of a Word document showing a plain‑text Structured Document
  Tag placeholder
og_title: Comment ajouter un SDT en C# – guide pas à pas des espaces réservés Word
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add SDT quickly with Aspose.Words. Learn to create word placeholder
    and insert plain text control in a .docx file.
  headline: How to add SDT in C# – complete guide for Word placeholders
  type: TechArticle
tags:
- Word
- C#
- Aspose.Words
- SDT
- Document Automation
title: Comment ajouter des SDT en C# – guide complet des espaces réservés Word
url: /fr/java/using-document-elements/how-to-add-sdt-in-c-complete-guide-for-word-placeholders/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment ajouter des SDT en C# – guide complet pour les espaces réservés Word

Si vous avez besoin de **how to add sdt** dans un fichier Word, ce tutoriel vous montre les étapes exactes en utilisant Aspose.Words for .NET. À la fin du guide, vous serez capable de **create word placeholder** des balises qui permettent aux utilisateurs finaux de taper directement dans un document, et vous comprendrez comment **insert plain text control** de manière fiable.

Travailler avec les Structured Document Tags (SDT) élimine le besoin de champs de formulaire manuels et vous offre une méthode propre et programmatique pour créer des contrats, rapports ou lettres dynamiques. L'exemple ci‑dessous couvre tout, de la configuration du projet à l'enregistrement du fichier .docx final, afin que vous puissiez copier‑coller le code dans votre propre solution sans manquer aucune dépendance.

## Prérequis

- .NET 6.0 ou ultérieur (le code fonctionne également avec .NET Framework 4.6+)
- Visual Studio 2022 ou tout IDE C# de votre choix
- Une licence Aspose.Words for .NET (une licence temporaire gratuite suffit pour les tests)
- Une connaissance de base de la syntaxe C# et du concept de SDT

> **Astuce :** Si vous prévoyez de distribuer les documents générés, intégrez un fichier de licence pour éviter le filigrane d'évaluation.

## Étape 1 : Configurer le projet et importer Aspose.Words

Créez une nouvelle application console et ajoutez le package NuGet Aspose.Words :

```bash
dotnet new console -n SdtDemo
cd SdtDemo
dotnet add package Aspose.Words
```

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
```

Ces directives `using` vous donnent accès aux classes `Document`, `DocumentBuilder` et `StructuredDocumentTag` nécessaires aux opérations **insert plain text control**.

## Étape 2 : Initialiser le document et le builder

Le premier bloc de code crée un document Word vide et un `DocumentBuilder` qui vous permet d'écrire du contenu dedans.

```csharp
// Step 2: Create a new document and a builder to edit it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` fonctionne comme un curseur ; chaque appel suivant ajoute du contenu à la position actuelle. Initialiser le document est la base de chaque scénario **how to add sdt** car le SDT doit appartenir à une instance `Document` active.

## Étape 3 : Insérer un Structured Document Tag (SDT) en texte brut

Nous allons maintenant **insert plain text control** qui agit comme un espace réservé où un utilisateur peut saisir un nom, une date ou toute valeur personnalisée.

```csharp
// Step 3: Insert a plain‑text Structured Document Tag (SDT)
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
        StructuredDocumentTagType.PlainText, SdtAppearanceTags.Default);
```

- `StructuredDocumentTagType.PlainText` indique à Aspose.Words de créer un champ texte simple.
- `SdtAppearanceTags.Default` donne à la balise le style visuel standard de Word (une boîte ombrée lorsque le document est ouvert dans Word).

## Étape 4 : Configurer le SDT avec un titre et un texte d'espace réservé

Un SDT bien nommé rend le document auto‑explicatif pour les utilisateurs finaux. Ici, nous **create word placeholder** des métadonnées et définissons l'indice qui apparaît à l'intérieur du champ.

```csharp
// Step 4: Give the SDT a meaningful title and placeholder text
plainTextTag.Title = "CustomerName";
plainTextTag.PlaceholderName = "Enter name here";
```

- `Title` est l'identifiant interne que vous pouvez utiliser plus tard pour extraire ou mettre à jour la valeur de façon programmatique.
- `PlaceholderName` est l'indice grisé affiché dans Word, indiquant à l'utilisateur quoi saisir.

## Étape 5 : Ajouter du contenu environnant

Un document contient rarement un seul SDT. Vous avez généralement besoin de paragraphes normaux avant et après l'espace réservé. Utilisez la méthode `WriteLine` du builder pour ajouter du texte statique.

```csharp
// Step 5: Add regular content before and after the SDT
builder.Writeln("Dear ");
builder.InsertNode(plainTextTag);   // Re‑insert the tag at the current cursor position
builder.Writeln(",");
builder.Writeln("After the SDT");
```

L'appel à `InsertNode` place le SDT créé précédemment exactement où vous le souhaitez, en préservant le flux de texte environnant.

## Étape 6 : Enregistrer le document dans un fichier .docx

Enfin, persistez le document sur le disque. Le chemin peut être absolu ou relatif au dossier du projet.

```csharp
// Step 6: Save the document to a file
string outputPath = Path.Combine(Environment.CurrentDirectory, "SDT.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

L'ouverture de `SDT.docx` dans Microsoft Word affiche un espace réservé gris contenant le texte **Enter name here**. Les utilisateurs peuvent cliquer sur le champ, saisir une valeur, et le document conservera cette valeur lors d'un nouvel enregistrement.

## Exemple complet, exécutable

Assembler toutes les pièces vous fournit un programme autonome que vous pouvez exécuter immédiatement :

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a plain‑text SDT
        StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
            StructuredDocumentTagType.PlainText, SdtAppearanceTags.Default);

        // Configure the SDT
        plainTextTag.Title = "CustomerName";
        plainTextTag.PlaceholderName = "Enter name here";

        // Add surrounding content
        builder.Writeln("Dear ");
        builder.InsertNode(plainTextTag);
        builder.Writeln(",");
        builder.Writeln("After the SDT");

        // Save the file
        string outputPath = Path.Combine(Environment.CurrentDirectory, "SDT.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Sortie attendue** lorsque vous exécutez le programme :

```
Document saved to C:\YourProject\bin\Debug\net6.0\SDT.docx
```

L'ouverture du `SDT.docx` généré montre :

```
Dear [Enter name here],
After the SDT
```

Le texte entre crochets est l'espace réservé **insert plain text control** que les utilisateurs peuvent remplacer.

## Variantes courantes et cas limites

| Situation | Comment adapter le code |
|-----------|--------------------------|
| **Plusieurs espaces réservés** | Call `InsertStructuredDocumentTag` repeatedly and give each tag a unique `Title`. |
| **SDT texte enrichi** | Use `StructuredDocumentTagType.RichText` instead of `PlainText`. |
| **Verrouiller l'espace réservé** | Set `plainTextTag.LockContentControl = true;` to prevent users from deleting the field. |
| **Pré‑remplir avec une valeur** | Assign `plainTextTag.Text = "John Doe";` before saving. |
| **Apparence conditionnelle** | Use `plainTextTag.SdtType = StructuredDocumentTagType.CheckBox;` for a tick‑box control. |

Ces variantes vous permettent de **create word placeholder** des structures qui correspondent à presque n'importe quel scénario de type formulaire.

## Conseils de dépannage

- **Placeholder not visible** – Assurez‑vous d'ouvrir le fichier dans Microsoft Word (ou un visualiseur compatible). Certains éditeurs légers masquent les SDT.
- **License warning** – Si vous voyez un filigrane d'évaluation, vérifiez que votre fichier de licence est correctement chargé (`License license = new License(); license.SetLicense("Aspose.Words.lic");`).
- **Incorrect cursor position** – Après l'insertion d'un SDT, le curseur du builder reste *après* la balise. Si vous devez ajouter du texte *à l'intérieur* de la balise, utilisez `builder.MoveTo(plainTextTag);` avant d'écrire.

## Conclusion

Vous savez maintenant **how to add sdt** à un document Word en utilisant Aspose.Words for .NET, comment **create word placeholder** des balises, et comment **insert plain text control** que les utilisateurs peuvent modifier directement dans Word. L'exemple complet montre l'initialisation, l'insertion de balises, la configuration, le contenu environnant et l'enregistrement — le tout dans un seul programme exécutable.

Ensuite, explorez des sujets connexes tels que **insert rich text control**, **populate SDTs from a database**, ou **convert the final document to PDF**. Tous ces sujets s'appuient sur les mêmes fondamentaux présentés ici, vous permettant d'étendre votre pipeline d'automatisation en toute confiance.

Bon codage, et n'hésitez pas à expérimenter différents types de SDT pour répondre à vos besoins d'automatisation de documents !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et à explorer des approches d'implémentation alternatives dans vos propres projets.

- [Comment créer des champs de formulaire et ajouter du contenu avec DocumentBuilder dans Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Comment créer des plages modifiables dans des documents en lecture seule avec Aspose.Words for Java](/words/english/java/security-protection/editable-ranges-aspose-words-java/)
- [Ajouter des signets Word avec Aspose.Words for Java – Insérer, Mettre à jour, Supprimer](/words/english/java/content-management/aspose-words-java-manage-bookmarks/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}