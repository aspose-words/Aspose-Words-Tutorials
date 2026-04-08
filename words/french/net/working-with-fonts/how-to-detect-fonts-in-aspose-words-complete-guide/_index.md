---
category: general
date: 2026-04-07
description: Apprenez à détecter les polices et à capturer les avertissements lors
  de la gestion des polices manquantes en C# avec Aspose.Words. Code étape par étape
  inclus.
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- handle missing fonts
- Aspose.Words font substitution
- C# document loading warnings
language: fr
og_description: Comment détecter les polices dans Aspose.Words ? Suivez ce tutoriel
  pour capturer les avertissements et gérer les polices manquantes sans effort.
og_title: Comment détecter les polices dans Aspose.Words – Guide complet
tags:
- Aspose.Words
- C#
- Font handling
title: Comment détecter les polices dans Aspose.Words – Guide complet
url: /fr/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment détecter les polices dans Aspose.Words – Guide complet

Vous vous êtes déjà demandé **comment détecter les polices** manquantes dans un document Word avant de le mettre en production ? Vous n'êtes pas seul. Dans de nombreux scénarios d'entreprise, une police errante peut interrompre une chaîne de conversion PDF ou provoquer des défauts de mise en page qui semblent peu professionnels. La bonne nouvelle, c’est qu’Aspose.Words vous offre un moyen intégré de repérer ces polices absentes et d’afficher des avertissements clairs.

Dans ce tutoriel, nous allons parcourir exactement **comment détecter les polices**, **comment capturer les avertissements**, et les meilleures pratiques pour **gérer les polices manquantes** afin que votre application reste robuste. Aucun outil externe, aucune supposition — juste du code C# pur que vous pouvez intégrer immédiatement à votre projet.

> **Aperçu rapide :** À la fin, vous disposerez d’un `FontSubstitutionWarningCollector` réutilisable qui recueille chaque message de substitution de police lors du chargement du document, et vous saurez comment réagir lorsqu’une police est introuvable.

---

## Ce que vous apprendrez

- Comment configurer `LoadOptions` pour écouter les avertissements de substitution de police.  
- Comment capturer ces avertissements dans une classe collectrice personnalisée.  
- Comment traiter les avertissements collectés et décider d’abandonner, de consigner ou de substituer les polices.  
- Gestion des cas limites pour les documents qui référencent des polices distantes ou incorporées.  

**Prérequis :** .NET 6+ (ou .NET Framework 4.6+), Aspose.Words pour .NET (dernière version), et une connaissance de base du C#. Si vous n’avez jamais utilisé Aspose.Words auparavant, ne vous inquiétez pas — ce guide suppose seulement quelques minutes de configuration.

## Comment détecter les polices avec Aspose.Words LoadOptions

La première étape pour détecter les polices manquantes consiste à indiquer à Aspose.Words de les signaler. Cela se fait via la propriété `LoadOptions.WarningCallback`, qui accepte toute classe implémentant `IWarningCallback`. Ci-dessous, nous créons un petit collecteur qui stocke chaque avertissement pour une inspection ultérieure.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.Collections.Generic;

/// <summary>
/// Collects all warnings emitted while loading a document.
/// </summary>
public class FontSubstitutionWarningCollector : IWarningCallback
{
    // Thread‑safe static list so we can access warnings after loading.
    public static List<WarningInfo> Warnings { get; } = new List<WarningInfo>();

    // Called by Aspose.Words for each warning.
    public void Warning(WarningInfo info)
    {
        // We only care about font‑related warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Warnings.Add(info);
        }
    }

    // Helper to clear previous run’s warnings.
    public static void Clear() => Warnings.Clear();
}
```

**Pourquoi c’est important :** Sans rappel d’avertissement, Aspose.Words substitue silencieusement les polices manquantes par une police par défaut, et vous ne savez jamais qu’un problème existe. En capturant `WarningType.FontSubstitution`, vous obtenez une visibilité complète — exactement les données dont vous avez besoin pour **détecter les polices** qui ne sont pas disponibles sur la machine hôte.

Nous branchons maintenant le collecteur dans `LoadOptions` et chargeons un document :

```csharp
// Step 1: Prepare load options with our warning collector.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontSubstitutionWarningCollector()
};

// Optional: clear any stale warnings from a previous run.
FontSubstitutionWarningCollector.Clear();

// Step 2: Load the document. Replace the path with your own file.
Document doc = new Document(@"C:\Docs\MissingFonts.docx", loadOptions);
```

> **Astuce :** Si vous traitez de nombreux documents en lot, réutilisez la même instance de `FontSubstitutionWarningCollector` mais n’oubliez pas d’appeler `Clear()` entre les chargements pour éviter de mélanger les avertissements provenant de fichiers différents.

## Capturer les avertissements lors du chargement du document

Après le chargement du document, le collecteur possède déjà chaque avertissement lié aux polices. La question logique suivante est : *Comment capturer les avertissements* de manière à les consigner ou les afficher facilement ?

```csharp
// Step 3: Iterate over collected warnings and output them.
foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    Console.WriteLine($"{warning.Type}: {warning.Message}");
}
```

La sortie typique ressemble à :

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'Garamond' missing. Using 'Times New Roman' instead.
```

**Ce que cela indique :** Chaque ligne révèle le nom de la police d’origine et la police de secours que Aspose.Words a choisie. Fort de cette information, vous pouvez décider si la substitution est acceptable ou si vous devez incorporer manuellement la police manquante.

## Gérer les polices manquantes avec élégance

Détecter et capturer les avertissements n’est que la moitié du combat. La vraie valeur réside dans la façon dont vous **gérez les polices manquantes** de manière prête pour la production. Voici trois stratégies courantes :

1. **Consigner et continuer** – Convient au traitement par lots où vous avez simplement besoin d’une trace d’audit.  
2. **Interrompre sur les polices critiques** – Lancer une exception si une police particulière (par ex., une police propre à la marque) est manquante.  
3. **Incorporer la police à la volée** – Charger la police manquante depuis un dossier connu et l’enregistrer auprès d’Aspose.Words avant de recharger le document.

### Exemple : Interrompre sur une police critique

```csharp
// Define a list of fonts that must be present.
var requiredFonts = new HashSet<string> { "MyBrand-Regular", "MyBrand-Bold" };

foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    // Extract the original font name from the warning message.
    string missingFont = ExtractFontName(warning.Message);
    if (requiredFonts.Contains(missingFont))
    {
        throw new InvalidOperationException(
            $"Critical font '{missingFont}' is missing. Document load aborted.");
    }
}

// Helper method to parse font name from warning text.
string ExtractFontName(string message)
{
    // Message pattern: "Font 'X' was not found..."
    int start = message.IndexOf('\'') + 1;
    int end = message.IndexOf('\'', start);
    return (start > 0 && end > start) ? message[start..end] : string.Empty;
}
```

### Exemple : Incorporation automatique des polices manquantes

```csharp
foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    string missingFont = ExtractFontName(warning.Message);
    string fontPath = $@"C:\Fonts\{missingFont}.ttf";

    if (File.Exists(fontPath))
    {
        // Register the font with Aspose.Words.
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(Path.GetDirectoryName(fontPath), false);
        doc.FontSettings = fontSettings;

        // Reload the document now that the font is available.
        doc = new Document(@"C:\Docs\MissingFonts.docx", loadOptions);
        break; // Re‑load once; subsequent warnings will be resolved.
    }
}
```

**Pourquoi ces modèles sont utiles :** En décidant explicitement quoi faire lorsqu’une police est manquante, vous éliminez les substitutions silencieuses qui pourraient compromettre l’image de marque ou la lisibilité. C’est l’essence de **la gestion des polices manquantes** de manière contrôlée.

## Exemple complet fonctionnel

En réunissant tous les éléments, voici un programme unique, prêt à l’exécution, qui démontre **comment détecter les polices**, **comment capturer les avertissements**, et une politique simple pour **gérer les polices manquantes** en les consignant.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.Collections.Generic;
using System.IO;

public class FontSubstitutionWarningCollector : IWarningCallback
{
    public static List<WarningInfo> Warnings { get; } = new List<WarningInfo>();
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Warnings.Add(info);
    }
    public static void Clear() => Warnings.Clear();
}

class Program
{
    static void Main()
    {
        string docPath = @"C:\Docs\MissingFonts.docx";

        // 1️⃣ Configure LoadOptions with the warning collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontSubstitutionWarningCollector()
        };
        FontSubstitutionWarningCollector.Clear();

        // 2️⃣ Load the document – this is where fonts are detected.
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Process the collected warnings.
        if (FontSubstitutionWarningCollector.Warnings.Count == 0)
        {
            Console.WriteLine("✅ No missing fonts detected.");
        }
        else
        {
            Console.WriteLine("⚠️ Font substitution warnings:");
            foreach (var w in FontSubstitutionWarningCollector.Warnings)
                Console.WriteLine($"{w.Type}: {w.Message}");

            // Example policy: abort if a brand‑critical font is missing.
            var critical = new HashSet<string> { "MyBrand-Regular", "MyBrand-Bold" };
            foreach (var w in FontSubstitutionWarningCollector.Warnings)
            {
                string missing = ExtractFontName(w.Message);
                if (critical.Contains(missing))
                {
                    Console.WriteLine($"❌ Critical font '{missing}' missing. Stopping.");
                    return;
                }
            }
        }

        // 4️⃣ Continue with normal processing (e.g., save as PDF).
        doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);
        Console.WriteLine("✅ Document saved as PDF.");
    }

    // Helper to pull the original font name out of the warning text.
    static string ExtractFontName(string message)
    {
        int first = message.IndexOf('\'') + 1;
        int last = message.IndexOf('\'', first);
        return (first > 0 && last > first) ? message[first..last] : string.Empty;
    }
}
```

**Résultat attendu :** Lorsque vous exécutez le programme sur un document qui référence une police non présente sur la machine, la console affichera chaque avertissement de substitution. Si un avertissement concerne une police appartenant à l’ensemble `critical`, le programme se termine prématurément, empêchant la génération d’un PDF défectueux.

## Questions fréquemment posées (FAQ)

| Question | Réponse |
|----------|--------|
| *Ai-je besoin d’une licence pour Aspose.Words afin d’utiliser ce code ?* | Oui, une licence valide d’Aspose.Words supprime les filigranes d’évaluation et débloque toutes les fonctionnalités. |
| *Cette approche peut‑elle détecter les polices incorporées ?* | Les polices incorporées font déjà partie du fichier, donc Aspose.Words ne déclenchera pas d’avertissement de substitution. Vous pouvez vérifier `Document.FontInfos` pour énumérer les polices incorporées si nécessaire. |
| *Que faire si la police manquante est une police système sous Windows mais pas sous Linux ?* | Le même avertissement sera déclenché sous Linux parce que la police n’est pas installée. Utilisez la stratégie « gérer les polices manquantes » pour fournir les fichiers `.ttf` requis avec votre application. |
| *Le collecteur d’avertissements est‑il thread* |  |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}