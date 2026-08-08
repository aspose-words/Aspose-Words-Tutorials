---
category: general
date: 2026-08-07
description: Récupérez le séparateur de note de bas de page avec Aspose.Words pour
  .NET. Apprenez à extraire les séparateurs de notes de bas de page et de notes de
  fin, à inspecter les types de nœuds et à les modifier en C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- retrieve footnote separator
- Aspose.Words footnote separator
- C# footnote extraction
- endnote separator retrieval
- document node type
language: fr
lastmod: 2026-08-07
og_description: Récupérer le séparateur de note de bas de page avec Aspose.Words pour
  .NET. Ce guide montre comment extraire les séparateurs de notes de bas de page et
  de notes de fin, vérifier leurs types de nœuds et enregistrer les modifications.
og_image_alt: Console output demonstrating retrieve footnote separator results
og_title: récupérer le séparateur de notes de bas de page en C# – tutoriel Aspose.Words
  étape par étape
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: retrieve footnote separator using Aspose.Words for .NET. Learn how
    to extract footnote and endnote separators, inspect node types, and modify them
    in C#.
  headline: retrieve footnote separator in C# – complete Aspose.Words guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
title: récupérer le séparateur de note de bas de page en C# – guide complet Aspose.Words
url: /fr/net/working-with-footnote-and-endnote/retrieve-footnote-separator-in-c-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# récupérer le séparateur de note de bas de page en C# – guide complet Aspose.Words

Si vous devez **retrieve footnote separator** depuis un document Word, ce tutoriel vous montre exactement comment le faire avec Aspose.Words pour .NET. Que vous construisiez un service de traitement de documents ou que vous nettoyiez le formatage des notes de bas de page, vous verrez un exemple complet et exécutable qui extrait à la fois les séparateurs de notes de bas de page et de notes de fin.

Dans ce guide, vous apprendrez comment charger un fichier `.docx`, appeler les propriétés `FootnoteSeparator` et `EndnoteSeparator`, inspecter les objets `Node` retournés, et éventuellement remplacer la ligne de séparateur. Aucune documentation externe n’est requise—tout ce dont vous avez besoin est inclus ci‑dessous.

## Prérequis

* .NET 6.0 ou ultérieur (le code fonctionne également sur .NET Framework 4.7.2)
* Package NuGet Aspose.Words pour .NET (version 24.9 ou plus récente)
* Un document Word contenant des notes de bas de page et/ou des notes de fin (par ex., `Footnotes.docx`)

Vous pouvez ajouter le package Aspose.Words avec la commande CLI suivante :

```bash
dotnet add package Aspose.Words --version 24.9.0
```

## Étape 1 : Configurer le projet et importer les espaces de noms

Créez un nouveau projet console ou ajoutez le code à un projet existant. Les directives `using` requises sont listées ci‑dessous.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
```

Ces espaces de noms vous donnent accès à la classe `Document`, à la hiérarchie `Node` et à l’énumération `NodeType` nécessaires aux opérations de **retrieve footnote separator**.

## Étape 2 : Charger le document contenant des notes de bas de page et des notes de fin

La première opération dans tout flux de travail Aspose.Words consiste à charger le fichier source. Remplacez le chemin de substitution par l’emplacement réel de votre `.docx`.

```csharp
// Load a document that contains footnotes and endnotes
Document doc = new Document(@"C:\Docs\Footnotes.docx");

// Verify that the document was loaded
Console.WriteLine($"Document loaded: {doc.OriginalFileName}");
```

Le chargement du fichier prépare l’arbre de nœuds interne, ce qui est essentiel pour **retrieve footnote separator** car les nœuds de séparateur résident dans cet arbre.

## Étape 3 : Récupérer le nœud du séparateur de note de bas de page

Vous pouvez maintenant **retrieve footnote separator** en accédant à la propriété `FootnoteSeparator` de l’objet `Document`. Ce nœud représente la ligne qui sépare les notes de bas de page du texte principal.

```csharp
// Retrieve the footnote separator node (the line that separates footnotes from the main text)
Node footnoteSeparator = doc.FootnoteSeparator;

// Output its type for verification
Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");
```

Le `NodeType` sera `Paragraph` pour une ligne de séparateur standard. Connaître le type de nœud vous aide à décider si vous devez modifier le séparateur ou le remplacer entièrement.

## Étape 4 : Récupérer le nœud du séparateur de note de fin

De même, vous pouvez **retrieve endnote separator** en utilisant la propriété `EndnoteSeparator`. Ce nœud sépare les notes de fin du contenu principal.

```csharp
// Retrieve the endnote separator node (the line that separates endnotes from the main text)
Node endnoteSeparator = doc.EndnoteSeparator;

// Output its type for verification
Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");
```

Les deux nœuds de séparateur partagent le même `NodeType` (`Paragraph`) dans la plupart des documents, mais ils peuvent être personnalisés indépendamment.

## Étape 5 : Inspecter ou modifier le contenu du séparateur (optionnel)

Si vous devez changer l’apparence visuelle du séparateur—par exemple remplacer une ligne de tirets par une règle fine—vous pouvez éditer directement le nœud `Paragraph`. Ci‑dessous un exemple qui remplace le texte du séparateur par défaut par une chaîne personnalisée.

```csharp
// Cast to Paragraph to access its text
Paragraph footnotePara = (Paragraph)footnoteSeparator;
footnotePara.Clear(); // Remove existing runs
footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

// Do the same for the endnote separator
Paragraph endnotePara = (Paragraph)endnoteSeparator;
endnotePara.Clear();
endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));
```

Après avoir modifié les nœuds, vous pouvez enregistrer le document pour voir les changements reflétés dans Word.

```csharp
// Save the updated document
string outputPath = @"C:\Docs\Footnotes_Updated.docx";
doc.Save(outputPath);
Console.WriteLine($"Updated document saved to: {outputPath}");
```

## Sortie console attendue

Lorsque vous exécutez le programme avec le `Footnotes.docx` original, vous devriez voir quelque chose de similaire à :

```
Document loaded: Footnotes.docx
Footnote separator node type: Paragraph
Endnote separator node type: Paragraph
Updated document saved to: C:\Docs\Footnotes_Updated.docx
```

Si vous ouvrez `Footnotes_Updated.docx` dans Microsoft Word, les séparateurs de notes de bas de page et de notes de fin afficheront le texte personnalisé que vous avez inséré.

## Questions fréquentes et cas particuliers

**Que se passe-t-il si le document n’a pas de notes de bas de page ?**  
La propriété `FootnoteSeparator` renvoie toujours un nœud `Paragraph` car Word inclut toujours un espace réservé pour le séparateur. Le nœud sera vide, vous pouvez donc ajouter du contenu en toute sécurité ou le laisser tel quel.

**Puis-je récupérer le séparateur pour une section spécifique ?**  
Les séparateurs de notes de bas de page et de notes de fin sont valables pour tout le document, pas pour une section spécifique. Si vous avez besoin d’un contrôle au niveau de la section, vous devez travailler avec `Section.FootnoteOptions` et `Section.EndnoteOptions` au lieu des nœuds de séparateur globaux.

**Cela fonctionne-t-il avec .NET Core ?**  
Oui. Aspose.Words pour .NET est multiplateforme, et le même code s’exécute sur Windows, Linux et macOS avec .NET 6+.

**Quel type de nœud dois‑je attendre ?**  
Les deux propriétés `FootnoteSeparator` et `EndnoteSeparator` renvoient un nœud `Paragraph` (`NodeType.Paragraph`). Si vous rencontrez un type différent, le document peut être corrompu, et vous devriez le recharger ou valider le fichier source.

## Code source complet pour copier‑coller rapidement

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace RetrieveFootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // Load the document containing footnotes and endnotes
            Document doc = new Document(@"C:\Docs\Footnotes.docx");
            Console.WriteLine($"Document loaded: {doc.OriginalFileName}");

            // Retrieve footnote separator
            Node footnoteSeparator = doc.FootnoteSeparator;
            Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");

            // Retrieve endnote separator
            Node endnoteSeparator = doc.EndnoteSeparator;
            Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");

            // OPTIONAL: Customize separator text
            Paragraph footnotePara = (Paragraph)footnoteSeparator;
            footnotePara.Clear();
            footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

            Paragraph endnotePara = (Paragraph)endnoteSeparator;
            endnotePara.Clear();
            endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));

            // Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Updated.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Updated document saved to: {outputPath}");
        }
    }
}
```

Copiez le code dans un fichier `Program.cs`, ajustez les chemins de fichiers, et exécutez `dotnet run`. Le programme montre le flux complet de **retrieve footnote separator**, du chargement du document à la persistance des modifications.

## Conclusion

Vous savez maintenant comment **retrieve footnote separator** et **endnote separator retrieval** avec Aspose.Words pour .NET, inspecter leur `document node type`, et éventuellement remplacer leur contenu. Cette technique vous permet d’automatiser le formatage des notes de bas de page, de générer des lignes de séparateur personnalisées, ou de valider la structure du document dans n’importe quelle application C#.

Ensuite, vous pourriez explorer des sujets connexes tels que **C# footnote extraction** pour extraire les textes des notes de bas de page individuelles, ou apprendre à **modify footnote reference marks** en utilisant `FootnoteOptions`. Les deux concepts s’appuient directement sur les fondamentaux de l’arbre de nœuds présentés ici.

Bon codage, et n’hésitez pas à expérimenter différents styles de séparateur pour correspondre à l’identité visuelle de votre projet !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Words Processing with Footnote and Endnote](/words/english/net/working-with-footnote-and-endnote/)
- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Working With Footnote And Endnote](/words/hindi/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}