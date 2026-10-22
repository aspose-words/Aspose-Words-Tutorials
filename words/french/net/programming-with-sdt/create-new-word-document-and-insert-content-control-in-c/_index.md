---
category: general
date: 2026-10-13
description: Créer un nouveau document Word en C# et insérer un contrôle de contenu
  avec du texte de substitution. Apprenez comment définir le texte de substitution
  et enregistrer le document Word efficacement.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create new word document
- insert content control
- set placeholder text
- how to create sdt
- save word document c#
language: fr
lastmod: 2026-10-13
og_description: Créer un nouveau document Word en C# avec Aspose.Words, insérer un
  contrôle de contenu, définir un texte de substitution et enregistrer le document
  Word — le tout dans un guide unique.
og_image_alt: Screenshot of a Word document showing a content control placeholder
og_title: Créer un nouveau document Word et insérer un contrôle de contenu en C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Create new Word document in C# and insert a content control with placeholder
    text. Learn how to set placeholder text and save the Word document efficiently.
  headline: Create new Word document and insert content control in C#
  type: TechArticle
- description: Create new Word document in C# and insert a content control with placeholder
    text. Learn how to set placeholder text and save the Word document efficiently.
  name: Create new Word document and insert content control in C#
  steps:
  - name: Run the console app.
    text: Run the console app.
  - name: Open `output.docx` in Microsoft Word.
    text: Open `output.docx` in Microsoft Word.
  - name: Verify that the placeholder text appears inside a gray‑shaded box.
    text: Verify that the placeholder text appears inside a gray‑shaded box.
  - name: Click the box, type a name, and save the file. The entered text replaces
      the placeholder.
    text: Click the box, type a name, and save the file. The entered text replaces
      the placeholder.
  type: HowTo
tags:
- Aspose.Words
- C#
- Content Control
- Word Automation
title: Créer un nouveau document Word et insérer un contrôle de contenu en C#
url: /fr/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un nouveau document Word et insérer un contrôle de contenu en C#

Si vous devez **créer un nouveau document Word** de manière programmatique, ce guide vous montre comment le faire avec Aspose.Words for .NET. Vous apprendrez à **insérer un contrôle de contenu**, à attribuer du **texte de substitution**, et enfin à **enregistrer le document Word C#** avec du code que vous pouvez copier dans votre projet.

Le tutoriel parcourt chaque étape, explique pourquoi chaque appel d'API est important, et couvre les variantes courantes telles que l'ajout d'un SDT texte enrichi ou la gestion de documents existants. À la fin, vous disposerez d'un exemple complet et exécutable que vous pourrez adapter aux factures, contrats ou tout autre rendu Word basé sur un modèle.

## Prérequis

* .NET 6.0 ou ultérieur (le code fonctionne également avec .NET Framework 4.7+)
* Package NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)
* Un IDE tel que Visual Studio 2022 ou Visual Studio Code

Aucune bibliothèque supplémentaire n'est requise.

## Créer un nouveau document Word avec Aspose.Words

La première étape consiste à instancier un objet `Document`. Cet objet représente un fichier Word vide en mémoire.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

// Step 1: Create a new, empty document
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` vous fournit une API fluide pour insérer des éléments à la position du curseur actuel. Comme le document est vide, le curseur commence au début de la première (et unique) section.

## Insérer un contrôle de contenu (StructuredDocumentTag)

Un **contrôle de contenu** dans Word s'appelle un Structured Document Tag (SDT). Le code suivant crée un SDT texte brut, définit son titre et spécifie le texte de substitution qui apparaît lorsque l'utilisateur ouvre le fichier.

```csharp
// Step 2: Create a plain‑text StructuredDocumentTag (SDT)
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PlainText, true)
{
    // Title is used for identification in the document outline
    Title = "CustomerName",
    // Placeholder text is visible until the user types a value
    PlaceholderName = "Enter name here"
};

// Step 3: Insert the SDT at the builder's current insertion point
builder.InsertNode(sdt);
```

**Pourquoi c'est important :**  
* `SdtType.PlainText` limite le contenu à une seule ligne de texte brut, ce qui est idéal pour des champs simples comme un nom ou un e‑mail.  
* Définir `PlaceholderName` fournit un indice visuel (`Enter name here`) qui guide l'utilisateur final.

Si vous avez besoin d'un champ plus riche (par ex., texte multi‑lignes ou sélecteur de date), remplacez `SdtType.PlainText` par `SdtType.RichText` ou `SdtType.Date`.

## Ajouter du texte d'entourage optionnel

La plupart des modèles incluent une étiquette avant le contrôle de contenu. Vous pouvez l'ajouter avec la même instance de `DocumentBuilder` :

```csharp
// Optional: add a label before the content control
builder.Writeln("Customer Name:");
builder.InsertNode(sdt);   // Re‑insert the SDT after the label
```

Le fichier Word résultant affiche :

```
Customer Name: [Enter name here]
```

## Enregistrer le document Word à la manière C#

Enfin, écrivez le document sur le disque. Aspose.Words détermine automatiquement le format à partir de l'extension du fichier.

```csharp
// Step 4: Save the document to verify the result
string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Lorsque vous ouvrez `output.docx` dans Microsoft Word, vous verrez le texte de substitution à l'intérieur d'un contrôle de contenu ombré en gris. Les utilisateurs peuvent cliquer sur le contrôle et remplacer le texte de substitution par leur propre valeur.

## Exemple complet et exécutable

Ci-dessous se trouve un programme console autonome qui réunit tous les éléments. Copiez le code dans un nouveau projet console et exécutez-le.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordSdtDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Add a descriptive label
            builder.Writeln("Customer Name:");

            // Create and configure a plain‑text content control (SDT)
            StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PlainText, true)
            {
                Title = "CustomerName",
                PlaceholderName = "Enter name here"
            };

            // Insert the SDT after the label
            builder.InsertNode(sdt);

            // Save the document
            string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Sortie attendue** (console) :

```
Document saved to C:\YourProject\bin\Debug\net6.0\output.docx
```

L'ouverture de `output.docx` montre une seule ligne avec l'étiquette *Customer Name:* suivie d'un contrôle de contenu affichant *Enter name here*.

## Variantes courantes et cas limites

| Scénario | Modification du code | Raison |
|----------|----------------------|--------|
| **Champ texte enrichi** | `new StructuredDocumentTag(doc, SdtType.RichText, true)` | Autorise la saisie multi‑lignes et le formatage de base. |
| **Contrôle en lecture seule** | `sdt.LockContentControl = true;` | Empêche les utilisateurs de modifier le contenu du contrôle. |
| **Pré‑remplir avec des données** | `sdt.AppendChild(new Run(doc, "John Doe"));` | Insère une valeur par défaut qui remplace le texte de substitution. |
| **Ajouter à un document existant** | Load with `new Document("template.docx")` instead of an empty `Document` | Permet des scénarios de templating où le contrôle est placé dans une mise en page prédéfinie. |
| **Contrôles multiples** | Repeat the creation block with different titles and placeholders | Utile pour les formulaires qui collectent plusieurs informations. |

### Astuce pro

Lors de la génération de documents volumineux, réutilisez une seule instance de `DocumentBuilder` au lieu d'en créer une nouvelle pour chaque contrôle. Cela réduit la charge mémoire et améliore les performances.

## Tester le résultat

1. Exécutez l'application console.  
2. Ouvrez `output.docx` dans Microsoft Word.  
3. Vérifiez que le texte de substitution apparaît à l'intérieur d'une boîte ombrée en gris.  
4. Cliquez sur la boîte, saisissez un nom, puis enregistrez le fichier. Le texte saisi remplace le texte de substitution.

Si le texte de substitution n'apparaît pas, assurez-vous d'utiliser Aspose.Words version 23.9 ou ultérieure, car les versions antérieures comportaient un bug avec `PlaceholderName` sur les SDT texte brut.

## Conclusion

Vous savez maintenant comment **créer un nouveau document Word**, **insérer un contrôle de contenu**, **définir le texte de substitution**, et **enregistrer le document Word C#** en utilisant Aspose.Words. L'exemple complet illustre le modèle standard, et le tableau des variantes montre comment adapter la solution à des scénarios plus riches.

Ensuite, vous pourriez explorer :

* **Insérer un contrôle de contenu pour les dates** – utilisez l'énumération `SdtType.Date`.  
* **Remplir un modèle avec des données** – combinez `StructuredDocumentTag` avec des champs de publipostage.  
* **Exporter en PDF** – appelez `doc.Save("output.pdf")` après avoir ajouté les contrôles.

N'hésitez pas à expérimenter différents types de SDT, paramètres de verrouillage et styles pour répondre aux exigences de votre projet. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications pas à pas pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Créer un nouveau document Word](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Insérer un champ de formulaire texte dans un document Word](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)
- [Créer un document Word avec Aspose.Words pour .NET](/words/english/net/add-content-using-documentbuilder/insert-paragraph/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}