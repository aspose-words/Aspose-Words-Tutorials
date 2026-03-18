---
category: general
date: 2026-03-17
description: Comment détecter les polices en C# avec Aspose.Words et un rappel d’avertissement.
  Apprenez à utiliser le rappel pour capturer les substitutions de polices manquantes
  lors du chargement des documents.
draft: false
keywords:
- how to detect fonts
- how to use callback
- Aspose.Words font detection
- C# missing font warning
- warning callback example
language: fr
og_description: Comment détecter les polices en C# avec Aspose.Words. Ce guide montre
  comment utiliser un callback pour capturer les avertissements de police manquante
  lors du chargement d’un document.
og_title: Comment détecter les polices dans C# – Utiliser un rappel avec Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: Comment détecter les polices dans C# – Utiliser un rappel avec Aspose.Words
url: /fr/net/working-with-fonts/how-to-detect-fonts-in-c-use-callback-with-aspose-words/
---

careful with bold **...** keep formatting.

Also lists.

Let's craft.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment détecter les polices en C# – Utiliser un rappel avec Aspose.Words

Vous avez déjà eu besoin de **comment détecter les polices** dans un document Word de façon programmatique et vous vous êtes demandé pourquoi certains caractères apparaissent étranges après conversion ? Vous n'êtes pas seul. Dans de nombreux projets réels – générateurs de factures, exportateurs de rapports ou pipelines de traitement par lots – l'absence de polices entraîne des défauts de mise en page silencieux difficiles à déboguer.  

Bonne nouvelle : Aspose.Words vous offre un moyen propre de mettre en évidence ces problèmes grâce à un rappel d’avertissement. Dans ce tutoriel, vous verrez **comment utiliser le rappel** pour capturer chaque substitution de police qu’Aspose effectue lors du chargement d’un document, et vous repartirez avec un exemple prêt à l’emploi qui génère un rapport clair des polices manquantes.

Nous couvrirons :

* Les prérequis minimaux (un projet .NET et le package NuGet Aspose.Words).  
* Comment implémenter `IWarningCallback` pour écouter `WarningType.FontSubstitution`.  
* Comment brancher le rappel dans `LoadOptions` et charger un document.  
* À quoi ressemble la sortie, ainsi que quelques astuces pratiques pour le code en production.

À la fin, vous pourrez **détecter automatiquement les polices** dans n’importe quel fichier DOCX, DOC ou RTF et agir sur les informations de police manquante — que ce soit en journalisant, en alertant l’utilisateur ou en substituant une police de secours.

---

![Comment détecter les polices dans un document Word à l’aide du rappel d’avertissement Aspose.Words](https://example.com/images/detect-fonts.png "comment détecter les polices dans un document Word")

## Ce dont vous avez besoin

* **.NET 6.0** ou version ultérieure (l’exemple compile également avec .NET Framework 4.6+).  
* **Aspose.Words for .NET** – installez via NuGet : `Install-Package Aspose.Words`.  
* Un fichier Word d’exemple qui référence délibérément une police que vous n’avez pas installée (par ex. `MissingFont.docx`).  

Aucune bibliothèque supplémentaire n’est requise ; tout se trouve dans l’espace de noms Aspose.

---

## Comment détecter les polices avec un rappel d’avertissement

### Étape 1 : Créer une classe de rappel d’avertissement

Le rappel implémente `IWarningCallback`. Lorsqu’Aspose.Words rencontre une police introuvable, il lève un `WarningInfo` avec `WarningType.FontSubstitution`. Notre classe écrit simplement une ligne conviviale dans la console.

```csharp
using System;
using Aspose.Words.Warnings;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about missing‑font warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Example output: [Font substitution] Missing: "Comic Sans MS"
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
        }
    }
}
```

**Pourquoi c’est important :** En filtrant sur `WarningType.FontSubstitution`, nous évitons les avertissements bruyants (comme les fonctionnalités obsolètes) et nous concentrons le journal sur le problème exact que vous cherchez à résoudre — **détecter les polices** qui ne sont pas présentes sur la machine.

---

### Étape 2 : Brancher le rappel dans `LoadOptions`

`LoadOptions` vous permet de personnaliser la façon dont un document est analysé. Attribuer notre `FontWarningCollector` à la propriété `WarningCallback` indique à Aspose de l’invoquer chaque fois qu’une police manquante est rencontrée.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

// Configure load options with our custom warning handler.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**Astuce :** Vous pouvez également définir `LoadOptions.FontSettings` ici si vous souhaitez fournir une police de secours programmatiquement. C’est un scénario avancé que nous aborderons plus tard.

---

### Étape 3 : Charger le document et observer la sortie

Nous chargeons maintenant réellement le fichier. Dès qu’Aspose analyse le document, toute police qu’il ne trouve pas déclenche notre rappel.

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\MissingFont.docx";

try
{
    Document doc = new Document(docPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to load document: {ex.Message}");
}
```

**Sortie console attendue** (en supposant que le document référence *Comic Sans MS* qui n’est pas installé) :

```
[Font substitution] Missing: "Comic Sans MS"
Document loaded successfully.
```

Si le document contient plusieurs polices manquantes, vous verrez une ligne par police — exactement l’information **comment détecter les polices** dont vous avez besoin.

---

## Comment utiliser le rappel pour des scénarios plus complexes

### Journaliser dans un fichier au lieu de la console

En production vous voudrez probablement un journal persistant. Remplacez `Console.WriteLine` par un `StreamWriter` :

```csharp
class FontWarningCollector : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            File.AppendAllText(_logPath,
                $"[Font substitution] Missing: {info.Description}{Environment.NewLine}");
        }
    }
}
```

### Collecter les avertissements pour une analyse ultérieure

Parfois vous avez besoin de la liste des polices manquantes après le chargement du document, par exemple pour afficher une boîte de dialogue UI. Stockez les avertissements dans une `List<string>` et exposez‑les :

```csharp
class FontWarningCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}

// Usage
var collector = new FontWarningCollector();
LoadOptions opts = new LoadOptions { WarningCallback = collector };
Document doc = new Document(docPath, opts);

if (collector.MissingFonts.Any())
{
    Console.WriteLine("Missing fonts detected:");
    collector.MissingFonts.ForEach(f => Console.WriteLine($"- {f}"));
}
```

### Fournir une police de secours programmatiquement

Si vous avez une police d’entreprise que vous souhaitez imposer, vous pouvez l’ajouter à `FontSettings` avant le chargement :

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial Unicode MS";

LoadOptions opts = new LoadOptions
{
    WarningCallback = new FontWarningCollector(),
    FontSettings = fontSettings
};

Document doc = new Document(docPath, opts);
```

Aspose substituera alors les polices manquantes par *Arial Unicode MS* tout en signalant la substitution via le rappel. C’est une façon élégante d’**utiliser le rappel** à la fois pour la détection et la remédiation automatique.

---

## Pièges courants et astuces professionnelles

| Piège | Pourquoi cela arrive | Comment l’éviter |
|--------|----------------------|------------------|
| **Oublier de référencer `Aspose.Words.Warnings`** | L’interface `IWarningCallback` se trouve là. | Ajoutez `using Aspose.Words.Warnings;` en haut du fichier. |
| **Charger un document sans `LoadOptions`** | Le chargeur par défaut substitue silencieusement les polices sans notification. | Créez toujours une instance de `LoadOptions` et assignez votre rappel. |
| **Exécuter sur un serveur avec des permissions limitées** | L’écriture dans un fichier de log peut lever `UnauthorizedAccessException`. | Utilisez un dossier accessible en écriture (par ex. le répertoire de données de l’application) ou restez sur des collections en mémoire. |
| **Plusieurs threads partageant le même collecteur** | `FontWarningCollector` n’est pas thread‑safe par défaut. | Créez un collecteur distinct par thread ou protégez la liste avec un verrou. |
| **Supposer que le rappel se déclenche pour les polices incorporées** | Les polices incorporées sont déjà présentes dans le document ; aucun avertissement n’est levé. | Si vous devez vérifier l’intégrité des polices incorporées, inspectez `FontInfo` via `FontSettings`. |

---

## Exemple complet fonctionnel (prêt à copier‑coller)

```csharp
// ------------------------------------------------------------
// Detect missing fonts in a Word document using Aspose.Words
// ------------------------------------------------------------
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningCollector : IWarningCallback
{
    // Store warnings for later use (optional)
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Print to console
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
            // Keep a copy in memory
            MissingFonts.Add(info.Description);
        }
    }
}

class Program
{
    static void Main()
    {
        // Path to the document you want to inspect
        string docPath = @"YOUR_DIRECTORY\MissingFont.docx";

        // 1️⃣ Create the callback collector
        var collector = new FontWarningCollector();

        // 2️⃣ Set up LoadOptions with the callback
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = collector
        };

        // 3️⃣ Load the document – warnings will fire automatically
        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");

            // Optional: act on the collected data
            if (collector.MissingFonts.Count > 0)
            {
                Console.WriteLine("\nSummary of missing fonts:");
                foreach (var font in collector.MissingFonts)
                    Console.WriteLine($"- {font}");
            }
            else
            {
                Console.WriteLine("\nNo missing fonts detected.");
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**Ce que vous devriez voir** (en supposant que le fichier référence deux polices absentes) :

```
[Font substitution] Missing: "Comic Sans MS"
[Font substitution] Missing: "Papyrus"
Document loaded successfully.

Summary of missing fonts:
- Comic Sans MS
- Papyrus
```

Si le fichier n’utilise que des polices installées, la console affichera simplement :

```
Document loaded successfully.

No missing fonts detected.
```

---

## Conclusion

Nous avons parcouru **comment détecter les polices** dans un document Word en branchant un rappel d’avertissement personnalisé dans Aspose.Words. Cette approche est légère, ne nécessite que peu de code et vous permet de :

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}