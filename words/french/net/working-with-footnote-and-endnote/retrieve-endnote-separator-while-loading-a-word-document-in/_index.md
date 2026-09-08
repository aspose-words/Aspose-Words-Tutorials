---
category: general
date: 2026-09-08
description: Récupérez le séparateur de note de fin et affichez le séparateur de note
  de bas de page lorsque vous chargez un document Word à l'aide d'Aspose.Words pour
  .NET.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- retrieve endnote separator
- load word document
- display footnote separator
- Aspose.Words C#
- footnote and endnote handling
language: fr
lastmod: 2026-09-08
og_description: Récupérez le séparateur de note de fin et affichez le séparateur de
  note de bas de page lorsque vous chargez un document Word à l'aide d'Aspose.Words
  pour .NET.
og_image_alt: Console screenshot showing the footnote separator text printed by a
  C# program
og_title: Récupérer le séparateur de notes de fin lors du chargement d’un document
  Word en C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Retrieve endnote separator and display footnote separator when you
    load a Word document using Aspose.Words for .NET.
  headline: Retrieve endnote separator while loading a Word document in C#
  type: TechArticle
tags:
- C#
- Aspose.Words
- Word processing
title: Récupérer le séparateur de notes de fin lors du chargement d'un document Word
  en C#
url: /fr/net/working-with-footnote-and-endnote/retrieve-endnote-separator-while-loading-a-word-document-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Récupérer le séparateur de note de fin lors du chargement d’un document Word en C#

Si vous devez **récupérer le séparateur de note de fin** d’un fichier Word, ce guide vous montre exactement comment le faire. Vous apprendrez également comment **charger un document Word** avec Aspose.Words et **afficher le texte du séparateur de note de bas de page** dans la console, le tout dans un exemple complet et exécutable.

Travailler avec les notes de bas de page et les notes de fin est une exigence courante pour les applications juridiques, académiques ou d’édition. Ce tutoriel couvre tout ce dont vous avez besoin — de l’ouverture du fichier à la gestion des cas où un séparateur est absent—afin que vous puissiez intégrer la solution dans n’importe quel projet .NET sans deviner.

## Ce que couvre ce tutoriel

* Comment **charger un document Word** en utilisant l’API Aspose.Words.  
* Comment **récupérer le séparateur de note de fin** et pourquoi ce séparateur est important.  
* Comment **afficher le séparateur de note de bas de page** dans la console pour le débogage ou la journalisation.  
* Gestion des cas limites lorsqu’un document ne contient aucune note de bas de page ou note de fin.  
* Un exemple complet, prêt à copier‑coller, qui s’exécute sur .NET 6 ou version ultérieure.

### Prérequis

| Exigence | Raison |
|----------|--------|
| .NET 6 SDK ou plus récent | Fournit le runtime pour l’exemple C#. |
| Aspose.Words for .NET (package NuGet `Aspose.Words`) | La bibliothèque qui expose `Document.Footnotes` et `Document.Endnotes`. |
| Un fichier Word (`Footnotes.docx`) contenant au moins une note de bas de page ou une note de fin | Permet de démontrer les séparateurs. |
| Un IDE quelconque (Visual Studio, Rider, VS Code) | Pour compiler et exécuter le programme. |

> **Astuce pro :** Si vous n’avez pas de document avec des notes de bas de page, créez‑en rapidement un dans Microsoft Word : Insertion → Note de bas de page → saisissez du texte, puis enregistrez sous `Footnotes.docx`.

## Charger un document Word avec Aspose.Words

La première étape consiste à **charger le document Word** en mémoire. Aspose.Words lit le format du fichier et construit un modèle d’objet que vous pouvez interroger.

```csharp
using Aspose.Words;
using System;

class Program
{
    static void Main()
    {
        // Step 1: Load the document containing footnotes and endnotes
        // Adjust the path to point to your local file.
        Document doc = new Document("YOUR_DIRECTORY/Footnotes.docx");
        Console.WriteLine("Document loaded successfully.");
```

*Pourquoi c’est important* : le chargement du document est la condition préalable à toute manipulation ultérieure. Si le chemin du fichier est incorrect, `Document` lève une `FileNotFoundException`, il faut donc vérifier le chemin avant d’exécuter.

## Récupérer le paragraphe du séparateur de note de bas de page

Un séparateur de note de bas de page est le paragraphe qui sépare visuellement le texte principal de la liste des notes de bas de page. Le récupérer vous permet d’en inspecter ou de modifier le formatage.

```csharp
        // Step 2: Retrieve the footnote separator paragraph
        Paragraph footnoteSeparator = doc.Footnotes.Separator;

        // The separator may be null if the document has no footnotes.
        if (footnoteSeparator != null)
        {
            // Step 3: **display footnote separator** text in the console
            Console.WriteLine("Footnote separator text: " + footnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No footnote separator found – the document may not contain footnotes.");
        }
```

*Pourquoi c’est important* : **Afficher le séparateur de note de bas de page** vous aide à vérifier que le bon paragraphe est accédé, surtout lorsque vous devez appliquer un style personnalisé (par ex. une ligne ou une police spécifique).

## Récupérer le paragraphe du séparateur de note de fin

Nous **récupérons maintenant le séparateur de note de fin**. Le processus reflète celui des notes de bas de page mais utilise la collection `Endnotes`.

```csharp
        // Step 4: Retrieve the endnote separator paragraph
        Paragraph endnoteSeparator = doc.Endnotes.Separator;

        // The separator can also be null if there are no endnotes.
        if (endnoteSeparator != null)
        {
            Console.WriteLine("Endnote separator text: " + endnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No endnote separator found – the document may not contain endnotes.");
        }
    }
}
```

*Pourquoi c’est important* : l’étape **récupérer le séparateur de note de fin** est essentielle lorsque vous devez ajuster la rupture visuelle entre le contenu principal et la liste des notes de fin—courant dans les publications académiques où les notes de fin apparaissent à la fin d’un chapitre.

### Gestion des séparateurs manquants

`Footnotes.Separator` et `Endnotes.Separator` renvoient `null` lorsque le document ne définit pas de séparateur. Vérifiez toujours la valeur `null` avant d’appeler `GetText()` afin d’éviter une `NullReferenceException`. Si vous avez besoin d’un séparateur par défaut, vous pouvez en créer un :

```csharp
if (endnoteSeparator == null)
{
    endnoteSeparator = new Paragraph(doc);
    endnoteSeparator.AppendChild(new Run(doc, "—")); // Simple dash as a separator
    doc.Endnotes.InsertSeparator(endnoteSeparator);
}
```

Ce code injecte un séparateur minimal afin que le traitement ultérieur puisse compter sur son existence.

## Sortie console attendue

Lorsque l’exemple s’exécute sur un document contenant une note de bas de page et une note de fin, vous devriez voir quelque chose de similaire à :

```
Document loaded successfully.
Footnote separator text: — 
Endnote separator text: — 
```

Si le document ne comporte pas de notes de bas de page ou de notes de fin, le programme affiche les messages « non trouvé » correspondants, démontrant une gestion d’erreur élégante.

## Exemple complet et exécutable

Voici le programme complet que vous pouvez copier dans un nouveau projet console C#. Aucun code supplémentaire n’est requis.

```csharp
using Aspose.Words;
using System;

class RetrieveSeparatorsDemo
{
    static void Main()
    {
        // Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/Footnotes.docx");
        Console.WriteLine("Document loaded successfully.");

        // Retrieve and display the footnote separator
        Paragraph footnoteSeparator = doc.Footnotes.Separator;
        if (footnoteSeparator != null)
        {
            Console.WriteLine("Footnote separator text: " + footnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No footnote separator found – the document may not contain footnotes.");
        }

        // Retrieve and display the endnote separator
        Paragraph endnoteSeparator = doc.Endnotes.Separator;
        if (endnoteSeparator != null)
        {
            Console.WriteLine("Endnote separator text: " + endnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No endnote separator found – the document may not contain endnotes.");
        }
    }
}
```

Enregistrez le fichier sous le nom `Program.cs`, ajoutez le package NuGet Aspose.Words (`dotnet add package Aspose.Words`), puis exécutez `dotnet run`. Le programme affichera les textes des séparateurs ou vous informera s’ils sont absents.

## Variations courantes et scénarios « et si »

| Scénario | Comment adapter le code |
|----------|--------------------------|
| **Séparateurs personnalisés multiples** | Utilisez `doc.Footnotes.Separator` pour remplacer le séparateur par défaut, puis ajoutez des paragraphes de séparateur supplémentaires manuellement avec `doc.Footnotes.Add(separatorParagraph)`. |
| **Modification du style du séparateur** | Après avoir récupéré le séparateur, modifiez son `ParagraphFormat` (par ex. `footnoteSeparator.ParagraphFormat.Alignment = ParagraphAlignment.Center;`). |
| **Travail avec des fichiers .doc** | La même API fonctionne ; assurez‑vous simplement que le chemin du fichier se termine par `.doc`. |
| **Traitement de nombreux documents** | Enveloppez le chargement et la récupération du séparateur dans une boucle `foreach` ; réutilisez une seule instance `Document` uniquement si vous la réinitialisez avec `doc = new Document(path)`. |

## Checklist des meilleures pratiques

- ✅ **Toujours vérifier `null`** avant d’accéder au texte du séparateur.  
- ✅ **Trim** le résultat de `GetText()` pour supprimer les caractères de saut de ligne invisibles.  
- ✅ **Dispose** des gros objets `Document` si vous traitez de nombreux fichiers en lot (utilisez `using` ou appelez `doc.Dispose()`).  
- ✅ **Loguez** le texte du séparateur uniquement en développement ; évitez de l’exposer dans les journaux de production sauf si nécessaire.  

## Conclusion

Vous savez maintenant comment **récupérer le séparateur de note de fin** tout en **chargeant un document Word** et **affichant le séparateur de note de bas de page** dans une application console .NET. L’exemple complet montre le chargement, l’interrogation et la gestion sécurisée des séparateurs manquants, vous offrant une base solide pour toute tâche de manipulation de notes de bas de page ou de notes de fin.

Ensuite, vous pourriez explorer :

* **Personnaliser le formatage des notes de bas de page/de fin** – ajustez les polices, bordures ou styles de numérotation.  
* **Extraire le contenu des notes de bas de page/de fin** – parcourez les collections `doc.Footnotes` ou `doc.Endnotes`.  
* **Enregistrer le document modifié** – utilisez `doc.Save("output.docx")` pour persister les changements.

N’hésitez pas à expérimenter avec différents fichiers Word, styles de séparateur et fonctionnalités d’Aspose.Words. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques présentées dans ce guide. Chaque ressource inclut des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser d’autres fonctionnalités de l’API et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [How to Load Word Documents Using Aspose.Words LoadOptions](/words/english/net/programming-with-loadoptions/)
- [Get Paragraph Style Separator In Word Document](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Create and Style a Word Document in Aspose.Words for .NET](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}