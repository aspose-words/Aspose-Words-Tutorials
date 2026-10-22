---
category: general
date: 2026-09-08
description: Définir le nom de la balise et créer un contrôle de contenu (SDT) dans
  un document Word en C#. Apprenez comment ajouter un SDT, écrire du texte dans la
  balise et modifier le document.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set tag name
- how to add sdt
- modify word document
- create content control
- write text to tag
language: fr
lastmod: 2026-09-08
og_description: Définissez le nom de la balise et créez un contrôle de contenu (SDT)
  dans un document Word avec C#. Suivez ce guide étape par étape pour ajouter un SDT,
  écrire du texte dans la balise et modifier le document.
og_image_alt: Screenshot showing a Word document with a StructuredDocumentTag whose
  tag name is set
og_title: Définir le nom de la balise et ajouter un SDT dans un document Word – Guide
  C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Set tag name and create a content control (SDT) in a Word document
    using C#. Learn how to add SDT, write text to tag, and modify the document.
  headline: How to set tag name and add SDT in a Word document with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Comment définir le nom de balise et ajouter un SDT dans un document Word avec
  C#
url: /fr/java/document-manipulation/how-to-set-tag-name-and-add-sdt-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment définir le nom de balise et ajouter un SDT dans un document Word avec C#

Si vous devez **définir le nom de balise** pour un StructuredDocumentTag (SDT) lors de la manipulation de fichiers Word, ce guide vous montre exactement comment procéder. Vous verrez un exemple complet et exécutable qui **crée un contrôle de contenu**, écrit du texte dans la balise, et **modifie le document Word** de bout en bout.

Les développeurs demandent souvent, *« comment ajouter un sdt* à un .docx existant puis *écrire du texte dans la balise* ?* – la réponse réside dans l’utilisation de l’API Aspose.Words for .NET. À la fin de ce tutoriel, vous serez capable d’ouvrir un fichier Word, d’insérer un SDT en texte brut, de définir son nom de balise, de le remplir avec du contenu, et d’enregistrer les modifications sans laisser de ressources pendantes.

## Prérequis

* .NET 6.0 ou version ultérieure installé.
* Une licence valide Aspose.Words for .NET (ou vous pouvez travailler avec la version d’évaluation).
* Visual Studio 2022 (ou tout IDE supportant C#).
* Un document Word d’entrée (`input.docx`) placé dans un dossier que vous pouvez référencer depuis le code.

## Étape 1 : Configurer le projet et importer les espaces de noms

Créez un nouveau projet Console App et ajoutez le package NuGet Aspose.Words :

```bash
dotnet new console -n WordSdtDemo
cd WordSdtDemo
dotnet add package Aspose.Words
```

Ensuite, ajoutez les directives `using` nécessaires en haut de `Program.cs` :

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Markup;
```

Ces espaces de noms vous donnent accès aux classes `Document`, `DocumentBuilder` et `StructuredDocumentTag`, qui sont essentielles pour **modifier un document Word**.

## Étape 2 : Charger le document Word existant

La première opération consiste à charger le fichier que vous souhaitez modifier. Cette étape est requise pour chaque scénario où vous **modifiez le contenu d’un document Word**.

```csharp
// Load an existing Word document from disk
string inputPath = @"YOUR_DIRECTORY\input.docx";
Document doc = new Document(inputPath);
Console.WriteLine($"Loaded document: {inputPath}");
```

> **Pourquoi charger le document en premier** – L’objet `Document` représente l’ensemble du package .docx en mémoire. Ce n’est qu’après le chargement que vous pouvez insérer en toute sécurité de nouveaux nœuds tels qu’un SDT.

## Étape 3 : Insérer un StructuredDocumentTag (SDT) et définir son nom de balise

Nous répondons maintenant à la question principale : **comment ajouter un sdt** et **définir le nom de balise**. Nous utilisons `DocumentBuilder.InsertStructuredDocumentTag` avec `SdtType.PlainText`. Le deuxième argument est le nom de la balise, que vous pouvez ensuite référencer programmatiquement ou via l’interface Word.

```csharp
// Create a DocumentBuilder attached to the loaded document
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a plain‑text StructuredDocumentTag (content control) at the cursor position
// The second parameter ("MyTag") is the tag name we are setting.
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText, "MyTag");

// Confirm that the tag name has been set
Console.WriteLine($"Inserted SDT with tag name: {sdt.Tag}");
```

> **Explication** – `InsertStructuredDocumentTag` renvoie une instance de `StructuredDocumentTag`. En passant `"MyTag"` nous **définissons le nom de balise** directement lors de la création. Si vous devez le modifier plus tard, vous pouvez assigner une nouvelle valeur à `sdt.Tag`.

## Étape 4 : Écrire du texte dans la balise nouvellement créée

Une fois le SDT créé, vous souhaitez généralement **écrire du texte dans la balise** afin que les utilisateurs voient un texte de remplacement ou par défaut. La méthode `SetText` fait exactement cela.

```csharp
// Populate the SDT with sample content
sdt.SetText("Sample content");

// Optionally, you can also set the placeholder text that appears when the tag is empty
sdt.PlaceholderName = "Enter your text here";
Console.WriteLine("Text written to the SDT.");
```

> **Pourquoi utiliser SetText** – L’affectation directe de la propriété `Text` remplacerait toute la hiérarchie de nœuds. `SetText` met à jour en toute sécurité le texte interne du contrôle de contenu tout en préservant sa structure.

## Étape 5 : Enregistrer le document modifié

Enfin, persistez les modifications dans un nouveau fichier. Cela complète le flux de travail de **modification d’un document Word**.

```csharp
// Define the output path
string outputPath = @"YOUR_DIRECTORY\output.docx";

// Save the document with the inserted content control
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Lorsque vous ouvrez `output.docx` dans Microsoft Word, vous verrez un contrôle de contenu en texte brut intitulé **MyTag** contenant le texte « Sample content ». Le contrôle peut être édité manuellement, et le nom de balise reste accessible via les outils développeur de Word.

## Code source complet

Ci-dessous le programme complet et autonome. Copiez‑le dans `Program.cs` et exécutez‑le ; aucun extrait supplémentaire n’est requis.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Markup;

namespace WordSdtDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the existing Word document
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(inputPath);
            Console.WriteLine($"Loaded document: {inputPath}");

            // 2️⃣ Create a DocumentBuilder to work with the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert a plain‑text StructuredDocumentTag (SDT) and set its tag name
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText, "MyTag");
            Console.WriteLine($"Inserted SDT with tag name: {sdt.Tag}");

            // 4️⃣ Write text to the tag (and optionally set a placeholder)
            sdt.SetText("Sample content");
            sdt.PlaceholderName = "Enter your text here";
            Console.WriteLine("Text written to the SDT.");

            // 5️⃣ Save the modified document
            string outputPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

### Sortie attendue dans la console

```
Loaded document: YOUR_DIRECTORY\input.docx
Inserted SDT with tag name: MyTag
Text written to the SDT.
Document saved to: YOUR_DIRECTORY\output.docx
```

### À quoi ressemble le fichier Word résultant

![Document Word montrant un contrôle de contenu nommé MyTag avec le texte “Sample content”](/images/word-sdt-example.png){: .img-fluid alt="Exemple de définition du nom de balise dans un document Word"}

*La capture d’écran illustre le SDT avec le **nom de balise** défini sur *MyTag* et le texte intégré visible.*

## Variations courantes et cas limites

| Situation | Comment le gérer |
|-----------|------------------|
| **Créer un SDT en texte enrichi** | Utilisez `SdtType.RichText` au lieu de `PlainText`. |
| **Définir un nom de balise différent après insertion** | `sdt.Tag = "NewTag";` – vous pouvez ré‑assigner le nom de balise à tout moment. |
| **Ajouter le SDT à l’intérieur d’un paragraphe spécifique** | Déplacez le curseur du builder (`builder.MoveToParagraph(index)`) avant d’appeler `InsertStructuredDocumentTag`. |
| **Plusieurs SDT dans le même document** | Répétez les étapes 3‑4 pour chaque contrôle ; chacun peut avoir un nom de balise unique. |
| **Travailler avec des documents protégés** | Assurez‑vous que le document est déprotégé (`doc.Unprotect()`) avant d’insérer un SDT. |

## Astuces pro pour une automatisation Word robuste

* **Licencier tôt** – Appelez `Aspose.Words.License license = new Aspose.Words.License(); license.SetLicense("Aspose.Words.lic");` au début de `Main` pour éviter les filigranes d’évaluation.
* **Libérer les objets** – Encapsulez `Document` dans un bloc `using` si vous ciblez .NET Framework afin de garantir la libération des poignées de fichiers.
* **Valider l’existence d’une balise** – Lors de la lecture d’un document ultérieurement, utilisez `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` pour localiser les balises par la propriété `Tag`.
* **Performance** – Pour les gros documents, chargez uniquement les sections requises en utilisant `LoadOptions` avec `LoadFormat.Docx` et `LoadFormat.Auto`.  

## Conclusion

Vous savez maintenant comment **définir le nom de balise**, **créer un contrôle de contenu**, **écrire du texte dans la balise**, et **modifier un document Word** en utilisant C#. L’exemple complet montre le modèle standard pour **comment ajouter un sdt** et persister les modifications en toute sécurité.  

À partir d’ici

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Ajouter du contenu avec Document Builder dans Aspose.Words pour .NET](/words/english/net/add-content-using-document-builder/)
- [Document Word – Comment supprimer du contenu](/words/english/net/remove-content/)
- [Créer un document Word avec Aspose.Words – Guide étape par étape](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}