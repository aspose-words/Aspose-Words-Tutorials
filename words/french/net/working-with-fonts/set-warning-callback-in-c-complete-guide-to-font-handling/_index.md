---
category: general
date: 2026-02-10
description: Définissez le rappel d’avertissement pour surveiller les changements
  de police pendant que vous configurez la police par défaut et définissez la police
  d’importation par défaut dans Aspose.Words. Découvrez la solution complète, étape
  par étape.
draft: false
keywords:
- set warning callback
- configure default font
- monitor font changes
- set default import font
language: fr
og_description: Définissez le rappel d’avertissement pour surveiller les changements
  de police lors de la configuration de la police par défaut et de la définition de
  la police d’importation par défaut. Suivez le tutoriel complet pour Aspose.Words.
og_title: Définir le rappel d’avertissement en C# – Guide complet
tags:
- Aspose.Words
- C#
- Document Import
title: Définir le rappel d'avertissement en C# – Guide complet de la gestion des polices
url: /fr/net/working-with-fonts/set-warning-callback-in-c-complete-guide-to-font-handling/
---

column headers and content.

Let's produce final content.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Définir le rappel d’avertissement en C# – Guide complet de la gestion des polices

Vous avez déjà eu besoin de **définir le rappel d’avertissement** lors du chargement d’un document Word et vous vous êtes demandé comment *configurer la police par défaut* en même temps ? Vous n’êtes pas seul. Dans de nombreux projets réels—comme les générateurs de rapports automatisés ou les pipelines de conversion de documents—les polices manquantes peuvent casser silencieusement la mise en page, et la seule façon de détecter ces problèmes est de **surveiller les changements de police** via un rappel d’avertissement.

Dans ce tutoriel, nous allons parcourir un exemple pratique qui vous montre comment **définir le rappel d’avertissement**, **configurer la police par défaut**, et même **définir la police d’importation par défaut** en utilisant Aspose.Words for .NET. À la fin, vous disposerez d’un extrait prêt à l’emploi, comprendrez pourquoi chaque élément est important, et saurez l’adapter aux cas particuliers tels que les dossiers de polices personnalisés ou les substitutions silencieuses.

---

## Prérequis

- .NET 6.0 ou version ultérieure (le code fonctionne également avec .NET Framework 4.6+)  
- Package NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)  
- Un dossier contenant la police de secours que vous souhaitez utiliser (par ex., `fonts/Arial.ttf`)  
- Une connaissance de base des applications console C#  

Aucune bibliothèque supplémentaire n’est requise.

---

## Étape 1 : Créer LoadOptions et **configurer la police par défaut**

La première chose à faire lorsque vous voulez contrôler la gestion des polices est de créer une instance de `LoadOptions`. Cet objet indique à Aspose.Words comment traiter les polices manquantes lors de l’importation.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Step 1: Build LoadOptions with a default font
LoadOptions loadOptions = new LoadOptions
{
    // FontSettings lets you point to a folder or a specific file that will act as the fallback.
    FontSettings = new FontSettings()
};

// Point the FontSettings to a folder that contains the font you want as the default import font.
loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", /*recursive*/ true);
```

**Pourquoi c’est important :**  
Si le document source fait référence à une police qui n’est pas installée sur le serveur, Aspose.Words consultera le dossier que vous avez fourni. C’est le cœur de **définir la police d’importation par défaut**—vous indiquez explicitement à la bibliothèque où trouver un remplacement avant même que des avertissements ne soient générés.

---

## Étape 2 : **Définir le rappel d’avertissement** pour **surveiller les changements de police**

Aspose.Words émet une `WarningInfoCollection` chaque fois qu’il doit substituer une police, entre autres. En attachant un gestionnaire, vous pouvez consigner ou réagir à chaque substitution.

```csharp
// Step 2: Attach a warning callback to capture font substitution events
var warningCollector = new WarningInfoCollection();
loadOptions.WarningCallback = warningCollector;

// Subscribe to the Warning event
warningCollector.Warning += (sender, e) =>
{
    // We only care about font substitution warnings
    if (e.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {e.Description}");
    }
};
```

**Pourquoi c’est important :**  
Simplement **configurer la police par défaut** ne suffit pas si vous devez auditer quelles polices ont réellement été remplacées. Le rappel vous fournit un journal en temps réel, répondant à l’exigence **surveiller les changements de police** et vous aidant à détecter les substitutions inattendues tôt dans un pipeline CI.

---

## Étape 3 : Charger le document avec les options préparées

Maintenant que les options de chargement sont entièrement configurées, vous pouvez charger en toute sécurité n’importe quel fichier `.docx`. Le rappel se déclenche automatiquement si une substitution se produit.

```csharp
// Step 3: Load the document using the configured LoadOptions
string inputPath = @"C:\MyProject\input.docx";
Document doc = new Document(inputPath, loadOptions);

// Optional: verify the document loaded correctly
Console.WriteLine($"Document loaded – {doc.PageCount} page(s) total.");
```

**Ce que vous verrez :**  
Si la source utilise une police qui n’est pas présente, la console affichera quelque chose comme :

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s) total.
```

Cette sortie confirme que vous avez bien **défini le rappel d’avertissement** et que la **police d’importation par défaut** a été appliquée.

---

## Étape 4 : (Facultatif) Ajuster finement le comportement de substitution des polices

Parfois, vous pouvez vouloir remplacer *toutes* les polices manquantes par une seule famille, quel que soit la demande originale. Aspose.Words vous permet de définir une *police de secours* globalement.

```csharp
// Step 4: Force all missing fonts to use a specific fallback
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";
```

**Quand l’utiliser :**  
Si vous générez des PDF pour une marque qui n’autorise qu’un nombre limité de polices, cela garantit la cohérence de chaque document, même si la source tente d’utiliser quelque chose d’exotique.

---

## Étape 5 : Enregistrer ou poursuivre le traitement du document

Après le chargement, vous pouvez continuer avec tout le traitement nécessaire—édition, conversion en PDF, extraction de texte, etc. Voici un exemple rapide d’enregistrement du document au format PDF tout en conservant les polices substituées.

```csharp
// Step 5: Save the document as PDF to verify the visual result
string outputPath = @"C:\MyProject\output.pdf";
doc.Save(outputPath, SaveFormat.Pdf);
Console.WriteLine($"PDF saved to {outputPath}");
```

Le PDF résultant affichera la police de secours partout où une substitution a eu lieu, vous offrant une confirmation visuelle que le **rappel d’avertissement** a fonctionné comme prévu.

---

## Pièges courants & Astuces pro

| Piège | Pourquoi cela se produit | Solution |
|-------|--------------------------|----------|
| **Le rappel ne se déclenche jamais** | `LoadOptions.WarningCallback` n’a pas été assigné *avant* le chargement du document. | Attachez toujours le rappel **avant** d’appeler `new Document(...)`. |
| **Dossier de polices incorrect** | Faute de frappe dans le chemin ou permissions de lecture manquantes. | Vérifiez que le dossier existe et que l’application possède l’accès `Read`. Utilisez des chemins absolus pour plus de fiabilité. |
| **Multiples substitutions, sortie bruyante** | Documents volumineux avec de nombreuses polices manquantes. | Filtrez les avertissements par `WarningType.FontSubstitution` (comme montré) ou écrivez‑les dans un fichier de log au lieu de la console. |
| **Police de secours non appliquée** | La police de secours n’est pas installée sur la machine. | Placez le fichier `.ttf`/`.otf` dans le dossier que vous avez passé à `SetFontsFolder`. Aspose.Words le charge directement, aucune installation OS requise. |

**Astuce pro :** Lorsque vous exécutez cela dans un pipeline CI/CD, redirigez la sortie console vers un artefact de build. Vous disposerez ainsi d’une trace d’audit de chaque substitution de police survenue pendant la construction.

---

## Exemple complet fonctionnel (prêt à copier‑coller)

Voici le programme complet que vous pouvez placer dans un nouveau projet Console App. Il comprend toutes les étapes, les directives `using`, et les commentaires nécessaires.

```csharp
// Full example: Set warning callback, configure default font, and monitor font changes
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create LoadOptions and point to a fallback font folder
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            // Adjust the path to where your fallback fonts live
            loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", true);

            // 2️⃣ Set up the warning callback to catch font substitutions
            var warningCollector = new WarningInfoCollection();
            loadOptions.WarningCallback = warningCollector;
            warningCollector.Warning += (sender, e) =>
            {
                if (e.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font substituted: {e.Description}");
                }
            };

            // 3️⃣ Load the document with the prepared options
            string inputPath = @"C:\MyProject\input.docx";
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine($"Document loaded – {doc.PageCount} page(s).");

            // 4️⃣ (Optional) Force a single default font for *all* missing fonts
            // loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";

            // 5️⃣ Save as PDF to see the visual result
            string outputPath = @"C:\MyProject\output.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

**Sortie console attendue** (en supposant que `Times New Roman` était manquante) :

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s).
PDF saved to C:\MyProject\output.pdf
```

Exécutez le programme, ouvrez `output.pdf`, et vous verrez le document rendu avec la police de secours là où c’est nécessaire.

---

## Conclusion

Vous disposez maintenant d’un modèle solide, prêt pour la production, afin de **définir le rappel d’avertissement** en C#, **configurer la police par défaut**, **surveiller les changements de police**, et **définir la police d’importation par défaut** lors de l’utilisation d’Aspose.Words. En attachant un collecteur d’avertissements avant le chargement, en pointant `FontSettings` vers un dossier de polices fiable, et éventuellement en imposant une police de secours globale, vous obtenez une visibilité et un contrôle complets sur les substitutions de polices—exactement ce dont tout pipeline de traitement de documents robuste a besoin.

Prêt pour le niveau suivant ? Essayez de combiner cette approche avec :

- **Chargement dynamique de polices** depuis une base de données (utilisez `FontSettings.SetFontsFolder` à l’exécution).  
- **Gestionnaires d’avertissement personnalisés** qui écrivent dans un journal structuré (JSON ou CSV) pour l’analyse.  
- **Traitement parallèle de documents** où chaque thread possède son propre `LoadOptions` afin d’éviter les interférences.

N’hésitez pas à expérimenter, à adapter le code à votre architecture, et à partager vos découvertes dans les commentaires. Bon codage !

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}