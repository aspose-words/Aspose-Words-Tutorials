---
category: general
date: 2026-10-13
description: Remplacez les espaces réservés dans un docx en utilisant Aspose.Words
  et apprenez à remplir un modèle Word avec des données en quelques minutes.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- replace placeholders in docx
- fill word template with data
language: fr
lastmod: 2026-10-13
og_description: Remplacez les espaces réservés dans un fichier .docx avec Aspose.Words
  et remplissez le modèle Word avec des données. Suivez ce tutoriel étape par étape
  pour automatiser la génération de documents.
og_image_alt: Illustration of a Word document where {{FirstName}} and {{LastName}}
  have been replaced with real values
og_title: Remplacer les espaces réservés dans les fichiers docx – guide rapide pour
  les développeurs C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: replace placeholders in docx using Aspose.Words and learn to fill word
    template with data in a few minutes
  headline: How to replace placeholders in docx files with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Comment remplacer les espaces réservés dans les fichiers docx avec Aspose.Words
url: /fr/net/find-and-replace-text/how-to-replace-placeholders-in-docx-files-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment remplacer les espaces réservés dans les fichiers docx avec Aspose.Words

Si vous devez **remplacer les espaces réservés dans les fichiers docx**, ce guide vous montre comment le faire avec Aspose.Words pour .NET. Vous apprendrez également à **remplir un modèle Word avec des données** afin de générer automatiquement des documents personnalisés.

L'automatisation de documents est une exigence courante dans la facturation, l'intégration des RH et les rapports. À la fin de ce tutoriel, vous disposerez d'une application console complète et exécutable qui charge un modèle Word, remplace tous les jetons `{{Placeholder}}`, et enregistre le résultat dans un nouveau fichier.

## Prérequis

Avant de commencer, assurez-vous d'avoir :

* .NET 6.0 SDK ou version ultérieure installé  
* Visual Studio 2022 (ou tout IDE supportant .NET)  
* Une licence Aspose.Words pour .NET ou une copie d'évaluation gratuite (l'API fonctionne sans licence mais ajoute un filigrane)  
* Un modèle Word (`Template.docx`) contenant des jetons d'espace réservé tels que `{{FirstName}}` et `{{LastName}}`

Ces éléments sont suffisants pour exécuter le code exactement comme indiqué.

## Étape 1 : Créer un nouveau projet console

Ouvrez un terminal et exécutez la commande suivante pour créer une application console minimale :

```bash
dotnet new console -n DocxPlaceholderReplacer
cd DocxPlaceholderReplacer
```

Ajoutez le package NuGet Aspose.Words :

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.LowCode
```

Le projet référence maintenant les bibliothèques nécessaires au remplacement des espaces réservés.

## Étape 2 : Charger le modèle DOCX

Créez un fichier nommé `Program.cs` (ou remplacez celui existant) et ajoutez les directives using :

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.LowCode;
```

La première étape logique consiste à charger le document modèle. Cette opération crée une représentation en mémoire du fichier Word, que vous pouvez manipuler programmaticalement.

```csharp
// Step 2: Load the DOCX template
string templatePath = @"YOUR_DIRECTORY/Template.docx";
Document template = new Document(templatePath);
Console.WriteLine($"Loaded template from '{templatePath}'.");
```

**Pourquoi c’est important :** Charger le fichier une seule fois réduit la surcharge d'E/S et vous donne un accès complet à l'arborescence des nœuds du document, que la classe `Replacer` parcourra pour trouver les espaces réservés.

## Étape 3 : Configurer le Replacer

Aspose.Words.LowCode fournit l'utilitaire `Replacer`, qui analyse automatiquement le document à la recherche de marqueurs `{{…}}` et les remplace par les valeurs fournies.

```csharp
// Step 3: Create a Replacer instance for the loaded document
Replacer replacer = new Replacer(template);
Console.WriteLine("Replacer initialized.");
```

**Astuce :** Le `Replacer` fonctionne avec toute forme contenant du texte (paragraphes, tableaux, en-têtes, pieds de page, etc.). Vous n’avez pas besoin de parcourir manuellement l'arborescence des nœuds.

## Étape 4 : Définir les valeurs des espaces réservés

Préparez un dictionnaire où chaque clé correspond exactement à un jeton d'espace réservé tel qu'il apparaît dans le modèle, et chaque valeur est le texte que vous souhaitez injecter.

```csharp
// Step 4: Define placeholder values to insert
var placeholderValues = new Dictionary<string, string>
{
    { "{{FirstName}}", "Alice" },
    { "{{LastName}}", "Smith" },
    // Add more entries as required, e.g.:
    // { "{{Date}}", DateTime.Today.ToShortDateString() }
};

Console.WriteLine("Placeholder values prepared:");
foreach (var kvp in placeholderValues)
{
    Console.WriteLine($"  {kvp.Key} => {kvp.Value}");
}
```

**Pourquoi c’est important :** Utiliser un dictionnaire vous permet de faire évoluer la solution à des dizaines de champs sans modifier la logique de remplacement.

## Étape 5 : Effectuer le remplacement

Appelez la méthode `Replace` en passant le dictionnaire. La méthode parcourt chaque nœud de texte, détecte le motif `{{…}}` et le remplace par la valeur correspondante.

```csharp
// Step 5: Replace placeholders with actual data
replacer.Replace(placeholderValues);
Console.WriteLine("All placeholders have been replaced.");
```

**Gestion des cas limites :** Si un espace réservé dans le document n'existe pas dans le dictionnaire, le `Replacer` le laisse tel quel. Ce comportement empêche la perte accidentelle de données et rend le code sûr pour les modèles partiellement remplis.

## Étape 6 : Enregistrer le document rempli

Enfin, écrivez le document modifié dans un nouveau fichier. Conserver le modèle original inchangé vous permet de le réutiliser pour les exécutions suivantes.

```csharp
// Step 6: Save the filled document
string outputPath = @"YOUR_DIRECTORY/FilledTemplate.docx";
template.Save(outputPath);
Console.WriteLine($"Filled document saved to '{outputPath}'.");
```

Lorsque vous ouvrez `FilledTemplate.docx`, vous devriez voir :

```
Alice Smith
```

au lieu des jetons originaux `{{FirstName}} {{LastName}}`.

## Code source complet

Ci-dessous le programme complet et autonome. Copiez‑le dans `Program.cs`, remplacez `YOUR_DIRECTORY` par un chemin de dossier réel, et exécutez `dotnet run`.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.LowCode;

class Program
{
    static void Main()
    {
        // Load the template
        string templatePath = @"YOUR_DIRECTORY/Template.docx";
        Document template = new Document(templatePath);
        Console.WriteLine($"Loaded template from '{templatePath}'.");

        // Initialize the replacer
        Replacer replacer = new Replacer(template);
        Console.WriteLine("Replacer initialized.");

        // Prepare placeholder values
        var placeholderValues = new Dictionary<string, string>
        {
            { "{{FirstName}}", "Alice" },
            { "{{LastName}}", "Smith" }
        };

        Console.WriteLine("Placeholder values prepared:");
        foreach (var kvp in placeholderValues)
        {
            Console.WriteLine($"  {kvp.Key} => {kvp.Value}");
        }

        // Perform replacement
        replacer.Replace(placeholderValues);
        Console.WriteLine("All placeholders have been replaced.");

        // Save the result
        string outputPath = @"YOUR_DIRECTORY/FilledTemplate.docx";
        template.Save(outputPath);
        Console.WriteLine($"Filled document saved to '{outputPath}'.");
    }
}
```

### Sortie attendue dans la console

```
Loaded template from 'YOUR_DIRECTORY/Template.docx'.
Replacer initialized.
Placeholder values prepared:
  {{FirstName}} => Alice
  {{LastName}} => Smith
All placeholders have been replaced.
Filled document saved to 'YOUR_DIRECTORY/FilledTemplate.docx'.
```

### Contenu attendu dans `FilledTemplate.docx`

Si le modèle original contenait la ligne :

```
{{FirstName}} {{LastName}}
```

le fichier enregistré affichera :

```
Alice Smith
```

## Questions fréquentes et variantes

**Puis-je remplacer les espaces réservés à l'intérieur des tableaux ?**  
Oui. Le `Replacer` analyse chaque nœud contenant du texte, y compris les cellules, les en-têtes et les pieds de page. Aucun code supplémentaire n’est requis.

**Et si j’ai besoin d’une logique conditionnelle (par ex., masquer un paragraphe lorsqu’une valeur est vide) ?**  
Vous pouvez supprimer des nœuds avant d’appeler `Replace` :

```csharp
if (string.IsNullOrEmpty(placeholderValues["{{OptionalField}}"]))
{
    // Find the paragraph that contains the placeholder and remove it
    Node paragraph = template.GetChildNodes(NodeType.Paragraph, true)
                             .FirstOrDefault(p => p.GetText().Contains("{{OptionalField}}"));
    paragraph?.Remove();
}
```

**Le remplacement est‑il sensible à la casse ?**  
La correspondance par défaut est exacte, y compris la casse. Assurez‑vous que les clés de votre dictionnaire correspondent précisément aux jetons du modèle.

**Comment travailler avec de gros documents sans consommer trop de mémoire ?**  
Aspose.Words traite les documents de façon flux lors de l’enregistrement. Pour des fichiers extrêmement volumineux, envisagez d’utiliser la classe `LoadOptions` avec `LoadFormat.Docx` et la propriété `LoadFormat` afin d’ajuster finement la consommation de mémoire.

## Conclusion

Vous savez maintenant comment **remplacer les espaces réservés dans les fichiers docx** et **remplir un modèle Word avec des données** en utilisant Aspose.Words pour .NET. Le tutoriel a couvert le chargement d’un modèle, la configuration d’un `Replacer`, la fourniture d’un dictionnaire de valeurs, l’exécution de la substitution et l’enregistrement du résultat. Ce modèle s’adapte à n’importe quel nombre d’espaces réservés et fonctionne avec toutes les structures de documents Word.

## Prochaines étapes

* Explorez les options de mise en forme comme l’application de styles au texte inséré.  
* Combinez cette approche avec des données provenant d’une base de données pour générer en masse des lettres personnalisées.  
* Examinez d’autres utilitaires low‑code comme `SmartTagProcessor` pour des scénarios de modèles plus avancés.  

N’hésitez pas à expérimenter avec des espaces réservés supplémentaires, des sections conditionnelles ou l’insertion d’images pour étendre les capacités de votre flux d’automatisation Word. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Insérer une image en ligne dans un document Word avec Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Insérer une date d’en-tête dynamique dans un document Word avec Aspose.Words pour .NET](/words/english/net/working-with-headers-and-footers/insert-header-date/)
- [Créer un document Word vierge avec Aspose.Words – Guide étape par étape](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}