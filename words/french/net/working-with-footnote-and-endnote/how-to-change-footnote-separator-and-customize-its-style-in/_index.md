---
category: general
date: 2026-10-13
description: Comment modifier le séparateur de notes de bas de page dans un document
  Word à l’aide d’Aspose.Words. Apprenez à changer la couleur de la police dans un
  document Word de façon programmatique.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to change footnote separator
- change font color in word document
- style footnote separator programmatically
- Aspose.Words footnote formatting
- C# Word automation
language: fr
lastmod: 2026-10-13
og_description: Comment modifier le séparateur de notes de bas de page dans un document
  Word avec Aspose.Words. Ce tutoriel vous montre comment changer la couleur de la
  police dans un document Word en utilisant C#.
og_image_alt: Screenshot of a Word document showing red footnote separator and blue
  endnote separator
og_title: Comment modifier le séparateur de notes de bas de page dans un document
  Word – guide étape par étape
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: How to change footnote separator in a Word document using Aspose.Words.
    Learn to change font color in Word document programmatically.
  headline: How to change footnote separator and customize its style in a Word document
  type: TechArticle
- description: How to change footnote separator in a Word document using Aspose.Words.
    Learn to change font color in Word document programmatically.
  name: How to change footnote separator and customize its style in a Word document
  steps:
  - name: Why each line matters
    text: '* **Loading the document** (`new Document`) gives you an in‑memory representation
      that Aspose.Words can manipulate. * **`GetChild` with `ParagraphNodeType.FootnoteSeparator`**
      returns the hidden paragraph that Word uses to draw the line separating footnotes
      from the main text. The same method works '
  - name: Expected output
    text: 'When you open `FootnoteSeparatorsStyled.docx` in Microsoft Word:'
  - name: 1. Install Aspose.Words
    text: 'Open a terminal in your project folder and run:'
  - name: 2. Prepare the input file
    text: Place `Footnotes.docx` in a known directory (e.g., `C:\Docs`). Ensure the
      file contains at least one footnote and one endnote so the separator nodes exist.
  - name: 3. Write the C# program
    text: Create a new console project (`dotnet new console -n FootnoteStyler`) and
      replace the generated `Program.cs` with the full code block from the **How to
      change footnote separator** section. Remember to adjust the file paths to match
      your environment.
  - name: 4. Run and verify
    text: 'Execute the program:'
  - name: 5. Extend the solution
    text: '* **Different colors:** Use any `System.Drawing.Color` value, e.g., `Color.FromArgb(255,
      128, 0)` for orange. * **Custom line style:** Instead of changing the color,
      you can modify `ParagraphFormat` properties such as `LineSpacing`, `Shading`,
      or even replace the separator character. * **Multiple do'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- footnotes
- document styling
title: Comment modifier le séparateur de notes de bas de page et personnaliser son
  style dans un document Word
url: /fr/net/working-with-footnote-and-endnote/how-to-change-footnote-separator-and-customize-its-style-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment modifier le séparateur de note de bas de page et personnaliser son style dans un document Word

Si vous avez besoin de **how to change footnote separator** dans un document Word, ce guide vous fournit une solution complète, prête à l’emploi. En utilisant Aspose.Words pour .NET, vous pouvez également **change font color in Word document** des éléments tels que les séparateurs de notes de bas de page et de fin de document, afin que le fichier final corresponde à votre identité visuelle ou à votre guide de style.

Les auteurs de documents demandent souvent : *Pourquoi le séparateur de note de bas de page par défaut semble‑t-il simple, et comment le faire ressortir ?* La réponse consiste à accéder directement aux objets paragraphe du séparateur, à ajuster leurs propriétés de police et à enregistrer le résultat. Ce tutoriel vous guide à travers chaque étape, du chargement d’un fichier .docx à la persistance du résultat stylisé.

Vous apprendrez à :

* Charger un fichier Word contenant déjà des notes de bas de page et des notes de fin.  
* Localiser les paragraphes séparateurs de notes de bas de page et de notes de fin.  
* Modifier la couleur de police de chaque séparateur (rouge pour les notes de bas de page, bleu pour les notes de fin).  
* Enregistrer le document modifié sans perdre aucun contenu existant.

Aucun outil externe n’est requis au‑delà de la bibliothèque Aspose.Words et d’un environnement de développement .NET.

## Prérequis

* .NET 6.0 SDK ou version ultérieure (le code fonctionne également avec .NET Framework 4.7+).  
* Visual Studio 2022, Rider ou tout éditeur C# de votre choix.  
* Package NuGet Aspose.Words for .NET (`Aspose.Words`).  
* Un fichier Word d’exemple (`Footnotes.docx`) contenant au moins une note de bas de page et une note de fin.

> **Astuce :** Si vous n’avez pas de fichier d’exemple, créez un nouveau document Word, insérez une note de bas de page (`Références → Insérer une note de bas de page`) et une note de fin (`Références → Insérer une note de fin`). Enregistrez‑le sous le nom `Footnotes.docx` dans un dossier que vous pourrez référencer depuis le code.

## Comment modifier le séparateur de note de bas de page avec Aspose.Words

Le cœur de la tâche consiste à récupérer les paragraphes spéciaux qu’Aspose.Words expose comme nœuds *separator*. Ces nœuds sont de type `Paragraph` et peuvent être formatés comme n’importe quel autre paragraphe.

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

class FootnoteSeparatorStyler
{
    static void Main()
    {
        // Step 1: Load the source document that already contains footnotes/endnotes.
        Document doc = new Document(@"C:\Docs\Footnotes.docx");

        // Step 2: Get the footnote separator paragraph.
        Paragraph footnoteSeparator = (Paragraph)doc.GetChild(
            NodeType.Paragraph, (int)ParagraphNodeType.FootnoteSeparator, true);

        // Step 3: Get the endnote separator paragraph.
        Paragraph endnoteSeparator = (Paragraph)doc.GetChild(
            NodeType.Paragraph, (int)ParagraphNodeType.EndnoteSeparator, true);

        // Step 4: Change the font color of the footnote separator to red.
        footnoteSeparator.Font.Color = Color.Red;

        // Step 5: Change the font color of the endnote separator to blue.
        endnoteSeparator.Font.Color = Color.Blue;

        // Step 6: Save the modified document.
        doc.Save(@"C:\Docs\FootnoteSeparatorsStyled.docx");
    }
}
```

### Pourquoi chaque ligne est importante

* **Chargement du document** (`new Document`) vous fournit une représentation en mémoire que Aspose.Words peut manipuler.  
* **`GetChild` avec `ParagraphNodeType.FootnoteSeparator`** renvoie le paragraphe caché que Word utilise pour tracer la ligne séparant les notes de bas de page du texte principal. La même méthode fonctionne pour le séparateur de note de fin.  
* **Modification de `Font.Color`** affecte directement l’apparence de la ligne car Word rend le séparateur comme un paragraphe contenant un seul caractère « ‑ ». Définir la couleur sur `Color.Red` (ou toute autre `System.Drawing.Color`) met à jour le style visuel.  
* **Enregistrement** écrit les modifications dans un fichier .docx que n’importe quel traitement de texte peut ouvrir.

### Résultat attendu

Lorsque vous ouvrez `FootnoteSeparatorsStyled.docx` dans Microsoft Word :

* La ligne du séparateur de note de bas de page apparaît **rouge**.  
* La ligne du séparateur de note de fin apparaît **bleue**.  

Tout le contenu original des notes de bas de page et des notes de fin reste intact.

## Modifier la couleur de police dans un document Word avec C#

L’opération démontrée ci‑dessus est un cas particulier d’une capacité plus large : **change font color in Word document** de façon programmatique. Une fois que vous avez un `Paragraph`, `Run` ou tout autre `Node` contenant du texte, vous pouvez ajuster sa propriété `Font.Color`.

```csharp
// Example: Change the color of all headings (style "Heading 1") to dark green.
foreach (Paragraph para in doc.GetChildNodes(NodeType.Paragraph, true))
{
    if (para.ParagraphFormat.StyleIdentifier == StyleIdentifier.Heading1)
        para.Font.Color = Color.DarkGreen;
}
```

* Cet extrait parcourt chaque paragraphe, vérifie s’il utilise le style `Heading 1`, puis définit la couleur de sa police.  
* Vous pouvez adapter la condition pour cibler les notes de bas de page, les tableaux ou tout autre type de nœud.

## Décomposition étape par étape

### 1. Installer Aspose.Words

Ouvrez un terminal dans le dossier de votre projet et exécutez :

```bash
dotnet add package Aspose.Words
```

Le package inclut toutes les assemblées requises pour le code présenté précédemment.

### 2. Préparer le fichier d’entrée

Placez `Footnotes.docx` dans un répertoire connu (par ex., `C:\Docs`). Assurez‑vous que le fichier contient au moins une note de bas de page et une note de fin afin que les nœuds séparateurs existent.

### 3. Écrire le programme C#

Créez un nouveau projet console (`dotnet new console -n FootnoteStyler`) et remplacez le `Program.cs` généré par le bloc de code complet de la section **Comment modifier le séparateur de note de bas de page**. N’oubliez pas d’ajuster les chemins de fichiers pour qu’ils correspondent à votre environnement.

### 4. Exécuter et vérifier

Exécutez le programme :

```bash
dotnet run
```

Une fois l’exécution terminée, ouvrez `FootnoteSeparatorsStyled.docx`. Vous devriez voir les lignes séparatrices rouge et bleue comme décrit.

### 5. Étendre la solution

* **Couleurs différentes :** Utilisez n’importe quelle valeur `System.Drawing.Color`, par ex., `Color.FromArgb(255, 128, 0)` pour l’orange.  
* **Style de ligne personnalisé :** Au lieu de changer la couleur, vous pouvez modifier les propriétés `ParagraphFormat` telles que `LineSpacing`, `Shading`, ou même remplacer le caractère du séparateur.  
* **Traitement de plusieurs documents :** Encapsulez la logique dans une méthode qui accepte les chemins d’entrée et de sortie, puis appelez‑la dans une boucle pour un traitement par lots.

## Problèmes courants et comment les éviter

| Symptôme | Cause | Solution |
|----------|-------|----------|
| `GetChild` renvoie `null` | Le document source ne possède aucun séparateur de note de bas de page/fin (par ex., aucune note). | Ajoutez au moins une note de bas de page ou de fin, ou vérifiez la valeur `null` avant d’accéder à `Font`. |
| Le changement de couleur n’est pas visible | Le séparateur est rendu comme une ligne plutôt que comme un caractère dans certaines versions de Word. | Définissez `ParagraphFormat.LineSpacingRule = LineSpacingRule.Exactly` et `ParagraphFormat.LineSpacing = 1` pour forcer l’affichage d’un caractère visible. |
| Exception d’exécution `FileNotFoundException` | Chemin de fichier incorrect. | Utilisez des chemins absolus ou `Path.Combine` avec `Environment.CurrentDirectory`. |

## Exemple complet et exécutable

Voici le programme complet que vous pouvez copier‑coller dans une application console. Il comprend la gestion des erreurs et des commentaires expliquant chaque opération.

```csharp
using System;
using System.Drawing;
using Aspose.Words;

namespace FootnoteSeparatorStyler
{
    class Program
    {
        static void Main()
        {
            // Paths – update these to match your environment.
            const string inputPath = @"C:\Docs\Footnotes.docx";
            const string outputPath = @"C:\Docs\FootnoteSeparatorsStyled.docx";

            // Load the document.
            Document doc = new Document(inputPath);

            // Retrieve footnote separator.
            Paragraph footnoteSeparator = (Paragraph)doc.GetChild(
                NodeType.Paragraph, (int)ParagraphNodeType.FootnoteSeparator, true);

            // Retrieve endnote separator.
            Paragraph endnoteSeparator = (Paragraph)doc.GetChild(
                NodeType.Paragraph, (int)ParagraphNodeType.EndnoteSeparator, true);

            // Guard against missing separators.
            if (footnoteSeparator == null || endnoteSeparator == null)
            {
                Console.WriteLine("The document does not contain footnote or endnote separators.");
                return;
            }

            // Change colors – this is the core of “change font color in word document”.
            footnoteSeparator.Font.Color = Color.Red;   // Footnote separator → red
            endnoteSeparator.Font.Color = Color.Blue; // Endnote separator → blue

            // Save the result.
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

L’exécution de ce programme produit un fichier Word où la ligne du séparateur de note de bas de page est rouge et celle du séparateur de note de fin est bleue, répondant ainsi à la demande **how to change footnote separator** tout en démontrant **change font color in word document**.

## Conclusion

Vous savez maintenant **how to change footnote separator** dans un document Word en utilisant Aspose.Words pour .NET et comment **change font color in Word document** de façon programmatique. Le processus est :

1. Charger le document.  
2. Récupérer les paragraphes séparateurs cachés.  
3. Définir leurs propriétés `Font.Color`.  
4. Enregistrer le fichier modifié.

À partir d’ici, vous pouvez explorer des styles plus avancés — ajuster l’épaisseur de la ligne, appliquer différentes polices ou automatiser le processus sur de nombreux fichiers. Maîtriser ces techniques vous donne un contrôle granulaire sur l’apparence des documents Word directement depuis le code C#.

---


## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets et fonctionnels avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et à explorer des approches d’implémentation alternatives dans vos projets.

- [Obtenir le séparateur de style de paragraphe dans un document Word](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Créer un document Word avec en‑tête et pied de page en utilisant Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Ajouter des numéros de page au pied de page d’un document Word en utilisant Aspose.Words pour .NET](/words/english/net/working-with-headers-and-footers/add-page-numbers/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}