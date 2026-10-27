---
category: general
date: 2026-10-26
description: Apprenez à insérer un contrôle de contenu texte brut à l'aide d'Aspose.Words
  en C#. Guide étape par étape couvrant StructuredDocumentTag, les titres et les identifiants
  de balise.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert plain text content control
- structured document tag
- Aspose.Words DocumentBuilder
- C# content control
- SDT appearance
language: fr
lastmod: 2026-10-26
og_description: Insérez un contrôle de contenu texte brut à l’aide d’Aspose.Words
  en C#. Suivez ce guide pour ajouter des titres, des ID de balise et personnaliser
  l’apparence.
og_image_alt: Screenshot of a Word document showing an inserted plain text content
  control
og_title: Insérer un contrôle de contenu texte brut dans Word avec C# – guide complet
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn to insert plain text content control using Aspose.Words in C#.
    Step‑by‑step guide covering StructuredDocumentTag, titles, and tag IDs.
  headline: How to insert plain text content control in a Word document with C#
  type: TechArticle
- description: Learn to insert plain text content control using Aspose.Words in C#.
    Step‑by‑step guide covering StructuredDocumentTag, titles, and tag IDs.
  name: How to insert plain text content control in a Word document with C#
  steps:
  - name: Initialize the document and builder
    text: '```csharp using System; using Aspose.Words; using Aspose.Words.Markup;'
  - name: Insert the plain‑text content control (SDT)
    text: '```csharp // Insert a plain‑text Structured Document Tag (SDT) with the
      default appearance. StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
      SdtType.PlainText, // The control type – plain text. SdtAppearance.Default);
      // Visual style; Default shows a light gray shading. ```'
  - name: Set a title and a tag identifier
    text: '```csharp // Give the SDT a friendly title that appears in the Content
      Controls pane. sdt.Title = "MyTag";'
  - name: Variations you might need
    text: '| Scenario | Code change | |----------|-------------| | **No visual shading**
      (border‑less) | Use `SdtAppearance.Hidden` instead of `Default`. | | **Read‑only
      field** | After insertion, set `sdt.LockContentControl = true`. | | **Pre‑populate
      with data** | Set `sdt.Text = "John Doe";` after creating '
  - name: What’s next?
    text: '- Explore other SDT types such as `RichText` or `ComboBox` for dropdowns.
      - Combine multiple content controls inside tables or repeat them using `RepeatingSection`.
      - Use `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` to read or modify
      control values programmatically.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Comment insérer un contrôle de contenu texte brut dans un document Word avec
  C#
url: /fr/java/document-manipulation/how-to-insert-plain-text-content-control-in-a-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insérer un contrôle de contenu texte brut dans un document Word avec C#

Si vous devez **insérer un contrôle de contenu texte brut** dans un fichier Word, ce tutoriel vous montre exactement comment le faire en utilisant Aspose.Words pour .NET. Que vous construisiez un service de génération de documents ou que vous automatisiez la création de formulaires, les étapes ci‑dessous vous permettent d’ajouter une zone réutilisable et éditable que les utilisateurs finaux peuvent remplir.

Vous apprendrez à créer un `Document`, à utiliser `DocumentBuilder` pour placer un Structured Document Tag (SDT) texte brut, à définir un titre convivial et à attribuer un identifiant de balise unique. Le guide explique également les variantes courantes — comme modifier l’apparence ou imbriquer des contrôles — afin que vous puissiez adapter la solution à n’importe quel projet.

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

- .NET 6.0 ou ultérieur (le code fonctionne également avec .NET Framework 4.6+)
- Une licence valide d’Aspose.Words pour .NET (ou une clé d’évaluation gratuite)
- Visual Studio 2022 ou tout IDE compatible C#
- Une connaissance de base de la syntaxe C#

> **Astuce :** Si vous utilisez l’évaluation gratuite, rappelez‑vous que le document de sortie contiendra un filigrane. Une version sous licence le supprime automatiquement.

## Comment insérer un contrôle de contenu texte brut avec Aspose.Words

Le cœur de la solution repose sur un processus en trois étapes :

1. **Créer un `Document` et un `DocumentBuilder`.**  
2. **Insérer un Structured Document Tag (SDT) texte brut avec l’apparence par défaut.**  
3. **Attribuer un titre et un identifiant de balise au SDT.**  

Chaque étape est expliquée ci‑dessous, avec du code complet et exécutable.

### Étape 1 : Initialiser le document et le builder

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Create a new empty document.
        Document doc = new Document();

        // DocumentBuilder lets you insert content into the document.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` représente l’ensemble du fichier Word, tandis que `DocumentBuilder` fournit des méthodes telles que `InsertParagraph`, `InsertImage` et, de façon cruciale pour ce tutoriel, `InsertStructuredDocumentTag`. Les initialiser d’abord vous donne une toile sur laquelle placer le **contrôle de contenu texte brut**.

### Étape 2 : Insérer le contrôle de contenu texte brut (SDT)

```csharp
        // Insert a plain‑text Structured Document Tag (SDT) with the default appearance.
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            SdtType.PlainText,          // The control type – plain text.
            SdtAppearance.Default);    // Visual style; Default shows a light gray shading.
```

`SdtType.PlainText` indique à Aspose.Words de créer un **contrôle de contenu texte brut**, qui se comporte comme une simple zone de texte que les utilisateurs peuvent éditer. `SdtAppearance.Default` rend le contrôle avec un arrière‑plan subtil, rendant évident dans le document que la région est éditable.

> **Pourquoi utiliser `SdtAppearance.Default` ?**  
> L’apparence par défaut est le style le plus universellement compatible entre les versions de Word. Si vous avez besoin d’un rendu sans bordure, vous pouvez passer à `SdtAppearance.Hidden` plus tard.

### Étape 3 : Définir un titre et un identifiant de balise

```csharp
        // Give the SDT a friendly title that appears in the Content Controls pane.
        sdt.Title = "MyTag";

        // Assign a unique tag identifier; this is useful for programmatic access later.
        sdt.Tag = "TagId";

        // (Optional) Add placeholder text inside the control.
        sdt.PlaceholderName = "Enter your text here";

        // Save the document to verify the result.
        doc.Save("output.docx");
    }
}
```

- **Titre** (`sdt.Title`) apparaît dans le volet *Content Controls* de Word, aidant les utilisateurs finaux à comprendre le but du champ.  
- **Balise** (`sdt.Tag`) est un identifiant orienté développeur que vous pouvez interroger plus tard via `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`.  
- **PlaceholderName** fournit un texte d’indication grisé, améliorant l’expérience utilisateur.

L’extrait de code complet ci‑dessus constitue un programme autonome que vous pouvez compiler et exécuter. Après exécution, `output.docx` contiendra un seul contrôle de contenu texte brut avec le titre *MyTag* et la balise *TagId*.

![Diagramme montrant l'insertion d'un contrôle de contenu texte brut dans un document Word](image.png){alt="insert plain text content control"}

## Comprendre StructuredDocumentTag (SDT) et ses propriétés

Un **Structured Document Tag** (SDT) est le modèle d’objet sous‑jacent aux contrôles de contenu Word. Les propriétés les plus pertinentes pour insérer un contrôle texte brut sont :

| Propriété | Rôle | Valeurs typiques |
|----------|------|------------------|
| `SdtType` | Détermine le type de contrôle (texte brut, texte enrichi, image, etc.) | `PlainText`, `RichText`, `ComboBox`, `DatePicker` |
| `SdtAppearance` | Style visuel du contrôle | `Default`, `Hidden`, `BoundingBox`, `Tags` |
| `Title` | Nom lisible affiché dans le volet *Content Controls* | Toute chaîne courte |
| `Tag` | Identifiant lisible par la machine utilisé dans le code | Chaîne alphanumérique |
| `PlaceholderName` | Texte affiché lorsque le contrôle est vide | Texte d’indice personnalisé |

Lorsque vous définissez `SdtType.PlainText`, Word restreint le contenu aux caractères simples, empêchant le formatage riche. Cela rend le contrôle idéal pour des champs de formulaire simples tels que *Nom*, *E‑mail* ou *Numéro de téléphone*.

### Variantes que vous pourriez nécessiter

| Scénario | Modification du code |
|----------|----------------------|
| **Pas d’ombrage visuel** (sans bordure) | Utilisez `SdtAppearance.Hidden` au lieu de `Default`. |
| **Champ en lecture‑seule** | Après insertion, définissez `sdt.LockContentControl = true`. |
| **Pré‑remplir avec des données** | Définissez `sdt.Text = "John Doe";` après la création de la balise. |
| **Contrôles multiples dans un tableau** | Insérez le SDT à l’intérieur d’une cellule de tableau avec `builder.InsertCell();` avant l’appel `InsertStructuredDocumentTag`. |

## Pièges courants et comment les éviter

1. **Oublier de définir un titre** – Word créera tout de même le contrôle, mais les utilisateurs ne verront aucune description significative dans le volet *Content Controls*. Assignez toujours `sdt.Title`.  
2. **Utiliser le mauvais `SdtType`** – Si vous avez besoin de texte brut mais choisissez accidentellement `RichText`, le contrôle autorisera le formatage, ce qui peut casser le traitement en aval. Vérifiez la valeur de l’énumération.  
3. **Enregistrer dans un dossier en lecture‑seule** – L’appel `doc.Save` lèvera une `UnauthorizedAccessException`. Assurez‑vous que le répertoire cible est accessible en écriture ou utilisez `Path.GetTempPath()` pour les tests.  
4. **Licence non appliquée** – Sans licence valide, le document de sortie contient un filigrane d’évaluation. Appliquez la licence dès le début de votre programme :  

```csharp
License lic = new License();
lic.SetLicense("Aspose.Words.lic");
```

## Exemple complet, exécutable

Voici le programme entier, prêt à être copié‑collé dans un nouveau projet console.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace InsertPlainTextContentControl
{
    class Program
    {
        static void Main()
        {
            // Apply license (optional for evaluation)
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // 1️⃣ Create a new document and a builder to edit it
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a plain‑text Structured Document Tag (SDT) with default appearance
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText,          // Plain text control
                SdtAppearance.Default);    // Light gray shading

            // 3️⃣ Assign a title and a tag identifier to the SDT
            sdt.Title = "MyTag";          // Human‑readable title
            sdt.Tag = "TagId";            // Unique machine identifier
            sdt.PlaceholderName = "Enter your text here";

            // (Optional) Add some introductory text before the control
            builder.MoveToDocumentStart();
            builder.Writeln("Please fill in the following field:");

            // 4️⃣ Save the document
            string outputPath = "output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Résultat attendu :** L’ouverture de `output.docx` dans Microsoft Word affiche une ligne de texte *« Please fill in the following field: »* suivie d’une zone encadrée gris‑clair intitulée *MyTag*. Le texte d’espace réservé *Enter your text here* apparaît en gris clair jusqu’à ce que l’utilisateur saisisse du texte.

## Conclusion

Vous savez maintenant comment **insérer un contrôle de contenu texte brut** dans un document Word en utilisant Aspose.Words pour .NET. Le tutoriel a couvert l’initialisation d’un `Document`, l’insertion d’un `StructuredDocumentTag` de type `PlainText`, et la personnalisation de son titre, de sa balise et de son texte d’espace réservé. En comprenant les options `SdtAppearance` et les pièges courants, vous pouvez créer en toute confiance des formulaires, des modèles et des rapports automatisés reposant sur des contrôles de contenu éditables.

### Et après ?

- Explorez d’autres types de SDT comme `RichText` ou `ComboBox` pour les listes déroulantes.  
- Combinez plusieurs contrôles de contenu à l’intérieur de tableaux ou répétez‑les avec `RepeatingSection`.  
- Utilisez `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` pour lire ou modifier les valeurs des contrôles programmatique­ment.

N’hésitez pas à expérimenter avec les variantes présentées plus haut et à intégrer ce modèle dans vos pipelines de génération de documents plus larges. Bon codage !

## Que devez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [How to create content control in C# with Aspose.Words](/words/english/net/programming-with-sdt/how-to-create-content-control-in-c-with-aspose-words/)
- [Create new Word document and insert content control in C#](/words/english/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/)
- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}