---
category: general
date: 2026-08-10
description: Formatez le séparateur de note de bas de page en C# avec Aspose.Words
  pour personnaliser les lignes de notes de bas de page et de notes de fin. Apprenez
  le formatage des notes de bas de page en C# en quelques minutes.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- format footnote separator
- Aspose.Words footnote separator
- C# footnote formatting
- modify footnote separator
- style footnote separator
- endnote separator formatting
language: fr
lastmod: 2026-08-10
og_description: Formatez le séparateur de note de bas de page en C# avec Aspose.Words.
  Suivez ce tutoriel pour styliser les séparateurs de notes de bas de page et de notes
  de fin rapidement et de façon fiable.
og_image_alt: Code editor showing C# snippet that styles a footnote separator
og_title: Formater le séparateur de note de bas de page en C# – guide complet d'Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  headline: Format footnote separator in C# using Aspose.Words
  type: TechArticle
- description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  name: Format footnote separator in C# using Aspose.Words
  steps:
  - name: Styling the continuation separator (optional)
    text: 'The continuation separator appears when a footnote spans multiple pages.
      You can style it similarly:'
  - name: Formatting the endnote separator
    text: 'If your document also uses endnotes, you can apply the same logic to the
      `Endnotes` collection:'
  - name: Using a custom string for the separator
    text: 'Sometimes you want the separator to be a series of asterisks (`***`). Replace
      the existing runs with a new run:'
  - name: Handling documents without a separator node
    text: 'A rare edge case is a document that omits the separator node (e.g., when
      the author deleted it). In that scenario `document.Footnotes.Separator` returns
      `null`. Guard against it:'
  type: HowTo
tags:
- Aspose.Words
- C#
- footnotes
- document‑processing
title: Formater le séparateur de note de bas de page en C# avec Aspose.Words
url: /fr/net/working-with-footnote-and-endnote/format-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Formater le séparateur de note de bas de page en C# avec Aspose.Words

Si vous devez **formater le séparateur de note de bas de page** dans un document Word, ce guide vous montre comment le faire avec Aspose.Words pour .NET. Vous verrez un exemple complet et exécutable qui modifie l'alignement et la couleur du paragraphe du séparateur, et vous apprendrez comment appliquer la même technique aux séparateurs de notes de fin.

Le tutoriel couvre chaque étape — du chargement du fichier source à l'enregistrement du document modifié — afin que vous puissiez copier‑coller le code dans votre propre projet sans recherche supplémentaire.

## Ce dont vous aurez besoin

* .NET 6.0 ou ultérieur (le code fonctionne également avec .NET Framework 4.6+)
* Une licence valide Aspose.Words pour .NET (l'essai gratuit fonctionne pour l'évaluation)
* Un fichier Word contenant au moins une note de bas de page ou une note de fin (par ex., `Footnotes.docx`)
* Visual Studio 2022 ou tout IDE C# de votre choix

Avoir ces éléments prêts vous permet de vous concentrer sur la logique de **formatage des notes de bas de page en C#** plutôt que sur la configuration de l'environnement.

## Étape 1 : Charger le document contenant des notes de bas de page et des notes de fin

La première opération consiste à créer un objet `Document` qui pointe vers votre fichier source. Aspose.Words lit l'intégralité du package DOCX en mémoire, vous donnant un accès complet aux nœuds de notes de bas de page et de notes de fin.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System.Drawing;

// Load the source DOCX file
Document document = new Document(@"C:\Docs\Footnotes.docx");
```

*Pourquoi c'est important* : charger le document est le prérequis pour toute manipulation. Si le chemin du fichier est incorrect, Aspose.Words lève une `FileNotFoundException`, donc vérifiez le chemin avant de continuer.

## Étape 2 : Récupérer les nœuds de séparateur et de séparateur de continuation

Les séparateurs de notes de bas de page et de notes de fin sont stockés comme des nœuds spéciaux dans les collections `Footnotes` et `Endnotes`. Chaque collection expose les propriétés `Separator` et `ContinuationSeparator` qui renvoient une référence `Node`.

```csharp
// Footnote separator nodes
Node footnoteSeparator          = document.Footnotes.Separator;
Node footnoteContinuationSep    = document.Footnotes.ContinuationSeparator;

// Endnote separator nodes
Node endnoteSeparator           = document.Endnotes.Separator;
Node endnoteContinuationSep     = document.Endnotes.ContinuationSeparator;
```

*Pourquoi c'est important* : le nœud `Separator` représente la ligne qui sépare visuellement le texte principal du bloc de note de bas de page. En obtenant une référence, vous pouvez modifier son format de paragraphe, sa police, ou même remplacer le nœud entièrement.

## Étape 3 : Modifier le style visuel du séparateur de note de bas de page

Dans la plupart des documents Word, le séparateur est un seul paragraphe contenant un tiret ou un astérisque. Le code ci‑dessous vérifie si le séparateur est un `Paragraph` et, le cas échéant, le centre et change la couleur du texte en gris.

```csharp
// Ensure the separator is a Paragraph before casting
if (footnoteSeparator is Paragraph separatorParagraph)
{
    // Center the separator paragraph
    separatorParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;

    // Set the separator text color to gray
    if (separatorParagraph.Runs.Count > 0)
    {
        separatorParagraph.Runs[0].Font.Color = Color.Gray;
    }
}
```

### Styliser le séparateur de continuation (optionnel)

Le séparateur de continuation apparaît lorsqu'une note de bas de page s'étend sur plusieurs pages. Vous pouvez le styliser de manière similaire :

```csharp
if (footnoteContinuationSep is Paragraph contParagraph)
{
    contParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (contParagraph.Runs.Count > 0)
        contParagraph.Runs[0].Font.Color = Color.DarkGray;
}
```

*Pourquoi c'est important* : aligner le séparateur améliore la lisibilité, et changer la couleur le distingue du texte de paragraphe ordinaire. Vous pouvez remplacer `ParagraphAlignment.Center` par `Left` ou `Right` pour correspondre aux directives de conception de votre document.

## Étape 4 : Enregistrer le document modifié

Après avoir appliqué le style souhaité, écrivez le document de nouveau sur le disque. Vous pouvez écraser le fichier original ou créer une nouvelle version.

```csharp
// Save the document with the modified separator
document.Save(@"C:\Docs\Footnotes_Styled.docx");
```

Lorsque vous ouvrez `Footnotes_Styled.docx` dans Microsoft Word, le séparateur de note de bas de page apparaît centré et gris, exactement comme spécifié dans le code.

## Variations avancées

### Formater le séparateur de note de fin

Si votre document utilise également des notes de fin, vous pouvez appliquer la même logique à la collection `Endnotes` :

```csharp
if (endnoteSeparator is Paragraph endSepParagraph)
{
    endSepParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (endSepParagraph.Runs.Count > 0)
        endSepParagraph.Runs[0].Font.Color = Color.SlateGray;
}
```

### Utiliser une chaîne personnalisée pour le séparateur

Parfois, vous voulez que le séparateur soit une série d'astérisques (`***`). Remplacez les runs existants par un nouveau run :

```csharp
if (footnoteSeparator is Paragraph sepPara)
{
    // Clear existing content
    sepPara.Runs.Clear();

    // Add a custom separator string
    Run newRun = new Run(document, "***");
    newRun.Font.Color = Color.Gray;
    sepPara.Runs.Add(newRun);
}
```

### Gérer les documents sans nœud de séparateur

Un cas rare est un document qui omet le nœud de séparateur (par ex., lorsque l'auteur l'a supprimé). Dans ce scénario, `document.Footnotes.Separator` renvoie `null`. Protégez-vous contre cela :

```csharp
if (footnoteSeparator != null && footnoteSeparator is Paragraph sepPara)
{
    // Apply styling as shown earlier
}
else
{
    // Optionally create a new separator paragraph
    Paragraph newSep = new Paragraph(document);
    newSep.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    Run run = new Run(document, "-");
    run.Font.Color = Color.Gray;
    newSep.Runs.Add(run);
    document.Footnotes.InsertAfter(newSep, document.Footnotes.LastParagraph);
}
```

## Pièges courants et comment les éviter

| Piège | Pourquoi cela se produit | Solution |
|---------|----------------|-----|
| **Separator is not a `Paragraph`** | Certains modèles Word utilisent une `Table` ou une `Shape` comme séparateur. | Vérifiez le type du nœud avec `is Paragraph` avant le cast. |
| **`Runs` collection is empty** | Le séparateur peut être un paragraphe vide. | Vérifiez que `Runs.Count > 0` avant d'accéder à `Runs[0]`. |
| **License not applied** | Sans licence, Aspose.Words insère un filigrane et peut limiter l'utilisation de l'API. | Appelez `License license = new License(); license.SetLicense("Aspose.Words.lic");` au début de votre programme. |
| **Saving to a read‑only folder** | La méthode `Save` lève une `UnauthorizedAccessException`. | Assurez‑vous que le répertoire cible possède les permissions d'écriture. |

Résoudre ces problèmes dès le départ évite les exceptions d'exécution et garantit une expérience fluide de **modification du séparateur de note de bas de page**.

## Exemple complet et exécutable

Ci‑dessous se trouve une application console autonome qui démontre chaque étape abordée ci‑dessus. Copiez le code dans un nouveau projet console .NET, remplacez les chemins de fichiers, et exécutez‑le.

```csharp
using Aspose.Words;
using System;
using System.Drawing;

namespace FootnoteSeparatorStyler
{
    class Program
    {
        static void Main()
        {
            // OPTIONAL: Apply your Aspose.Words license
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // 1. Load the source document
            string inputPath = @"C:\Docs\Footnotes.docx";
            Document doc = new Document(inputPath);

            // 2. Retrieve separator nodes
            Node footnoteSeparator = doc.Footnotes.Separator;
            Node footnoteContinuationSep = doc.Footnotes.ContinuationSeparator;
            Node endnoteSeparator = doc.Endnotes.Separator;
            Node endnoteContinuationSep = doc.Endnotes.ContinuationSeparator;

            // 3. Style footnote separator
            if (footnoteSeparator is Paragraph footSepPara)
            {
                footSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footSepPara.Runs.Count > 0)
                    footSepPara.Runs[0].Font.Color = Color.Gray;
            }

            // 3a. (Optional) Style footnote continuation separator
            if (footnoteContinuationSep is Paragraph footContPara)
            {
                footContPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footContPara.Runs.Count > 0)
                    footContPara.Runs[0].Font.Color = Color.DarkGray;
            }

            // 4. Style endnote separator (optional)
            if (endnoteSeparator is Paragraph endSepPara)
            {
                endSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (endSepPara.Runs.Count > 0)
                    endSepPara.Runs[0].Font.Color = Color.SlateGray;
            }

            // 5. Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Styled.docx";
            doc.Save(outputPath);

            Console.WriteLine("Footnote separator formatted successfully.");
            Console.WriteLine($"Saved to: {outputPath}");
        }
    }
}
```

**Résultat attendu**  

Lorsque vous ouvrez `Footnotes_Styled.docx` :

* La ligne du séparateur de note de bas de page est centrée sous le texte principal.
* Sa couleur apparaît en gris clair, la rendant visuellement distincte.
* Si le document contient des notes de fin, leurs séparateurs sont également centrés et colorés en gris (ou ardoise

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Traitement de texte avec notes de bas de page et notes de fin](/words/english/net/working-with-footnote-and-endnote/)
- [Définir la position des notes de bas de page et des notes de fin](/words/english/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [Travailler avec les notes de bas de page et les notes de fin](/words/german/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}