---
category: general
date: 2026-02-18
description: Apprenez à capturer les avertissements de police et à détecter les polices
  manquantes en C# avec Aspose.Words. Suivez ce guide pas à pas pour gérer efficacement
  les polices manquantes.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- handle missing fonts
- list missing fonts
language: fr
og_description: Capturez les avertissements de police dans C# et apprenez à détecter
  les polices manquantes, à les gérer et à les répertorier avec un exemple complet
  de code.
og_title: Capturer les avertissements de police dans C# – Guide complet
tags:
- Aspose.Words
- C#
- Font Management
title: Capturer les avertissements de police en C# – Guide complet de programmation
url: /fr/net/working-with-fonts/capture-font-warnings-in-c-complete-programming-guide/
---

showing capture font warnings flow". That should be translated to French, but the alt attribute after {alt="..."} also contains English; we need to translate that too. However the alt attribute is a Hugo attribute; we should translate the string inside alt="...". Keep the syntax.

Also translate the table content.

We must not translate URLs, file paths, variable names, function names. So code blocks placeholders remain unchanged.

We need to translate bullet points, paragraphs, etc.

Let's produce final content.

Be careful with markdown links: there are none except maybe none.

Let's translate.

Start with shortcodes unchanged.

Proceed.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Capture Font Warnings in C# – Complete Programming Guide

Vous êtes-vous déjà demandé comment **capturer les avertissements de police** lorsqu’un document fait référence à une police qui n’est pas installée sur le serveur ? Vous n’êtes pas le seul. Dans de nombreuses applications d’entreprise, les polices manquantes provoquent des dysfonctionnements de mise en page, et la seule façon fiable de les repérer est d’écouter les avertissements générés par la bibliothèque.  

Dans ce tutoriel, nous vous présentons une solution prête à l’emploi qui non seulement **capture les avertissements de police** mais aussi **détecte les polices manquantes**, **gère les polices manquantes**, et même **liste les polices manquantes** afin que vous puissiez décider de les substituer, les incorporer ou alerter l’utilisateur. Aucun document externe n’est nécessaire — il suffit de copier, coller et exécuter.

## What You’ll Learn

- Comment configurer `LoadOptions` pour activer les avertissements de substitution de police.  
- Le code exact dont vous avez besoin pour charger un DOCX et extraire chaque avertissement.  
- Pourquoi chaque étape est importante, y compris les considérations de performance.  
- La gestion des cas limites tels que les documents avec des polices à scripts mixtes ou des dossiers de polices personnalisés.  

**Prerequisites** : .NET 6+ (ou .NET Framework 4.6+), une référence au package NuGet **Aspose.Words**, et une compréhension de base du C#. Si vous n’avez jamais utilisé Aspose.Words, ne vous inquiétez pas — ce guide vous accompagne pas à pas.

![Diagram showing capture font warnings flow](image.png){alt="diagramme de capture des avertissements de police"}

## Capture Font Warnings – Why It Matters

Lorsque Aspose.Words charge un document, il remplace silencieusement toute police indisponible par une police de secours. Cette police de secours maintient l’opération de chargement, mais le rendu visuel peut être complètement désaligné. En activant le drapeau **SubstitutionWarningLevel.All**, la bibliothèque ajoute une entrée `WarningInfo` pour chaque police manquante, vous permettant de **détecter les polices manquantes** avant que le document ne soit rendu ou enregistré.

> **Pro tip** : Si vous traitez des centaines de fichiers dans un travail par lots, consigner ces avertissements dans un stockage central peut vous faire gagner des heures de QA manuelle plus tard.

## Step 1: Set Up Your Project

1. Ouvrez votre IDE préféré (Visual Studio, Rider, VS Code).  
2. Créez un nouveau projet console :

```bash
dotnet new console -n FontWarningDemo
cd FontWarningDemo
```

3. Ajoutez le package Aspose.Words :

```bash
dotnet add package Aspose.Words
```

C’est tout — pas de DLL supplémentaires, pas d’interop COM. La bibliothèque fournit tout ce dont vous avez besoin pour **gérer les polices manquantes**.

## Step 2: Prepare Load Options to Capture All Font Substitution Warnings

Pour que le moteur **capture les avertissements de police**, vous devez lui indiquer d’enregistrer chaque substitution. L’extrait suivant crée une instance `LoadOptions`, active le niveau d’avertissement, et (optionnellement) indique au moteur un dossier contenant des polices personnalisées que vous pourriez vouloir utiliser.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -----------------------------------------------------------------
            // Step 2.1 – Create LoadOptions and turn on font‑substitution warnings
            // -----------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions();

            // Initialise FontSettings if you need to add a custom font folder
            loadOptions.FontSettings = new FontSettings();

            // Capture *all* font substitution events (this is the key for capture font warnings)
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // Optional: add a folder that contains corporate fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);
```

**Pourquoi c’est important** :  
- `SubstitutionWarningLevel.All` garantit que **tous** les événements de police manquante sont enregistrés, pas seulement le premier.  
- Sans ce drapeau, Aspose.Words remplace silencieusement la police et vous ne savez jamais qu’un problème existe.

## Step 3: Load the Document Using the Configured Options

Nous ouvrons maintenant réellement le fichier. Remplacez `DocumentWithMissingFonts.docx` par le chemin de votre document de test.

```csharp
            // -----------------------------------------------------------------
            // Step 2.2 – Load the document with the warning‑enabled options
            // -----------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";

            Document document = new Document(docPath, loadOptions);
```

Si le fichier contient des références à des polices qui ne sont pas présentes sur la machine (ou dans le dossier optionnel que vous avez ajouté), la collection `document.WarningInfoCollection` sera remplie.

## Step 4: Find and Display Any Font Substitution Warnings

Voici le cœur du tutoriel : parcourir la `WarningInfoCollection` pour **lister les polices manquantes**. Nous filtrons par `WarningType.FontSubstitution` et affichons un message convivial.

```csharp
            // -----------------------------------------------------------------
            // Step 2.3 – Enumerate and output font substitution warnings
            // -----------------------------------------------------------------
            var fontWarnings = document.WarningInfoCollection
                                         .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    // The Description property already contains a readable message
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // Keep console window open when debugging
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### Expected Output

```
⚠️ Missing fonts detected:
- Missing font: "Comic Sans MS"
- Missing font: "Calibri Light"
```

Si le document n’utilise que des polices installées, vous verrez la ligne « ✅ No missing fonts detected ».

## Step 5: Advanced – How to **Handle Missing Fonts** Programmatically

Afficher simplement une liste peut suffire pour un outil de diagnostic, mais de nombreux systèmes de production doivent **gérer les polices manquantes** automatiquement. Voici deux stratégies courantes :

### 5.1 Substitute with a Known Fallback

```csharp
loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution
{
    // Replace any missing font with Arial, which is universally available
    SubstituteFont = "Arial"
};
```

### 5.2 Embed a Custom Font on the Fly

Si vous disposez d’un fichier de police d’entreprise (`MyBrand.ttf`), vous pouvez l’incorporer lorsqu’une police manquante est détectée :

```csharp
foreach (WarningInfo warning in fontWarnings)
{
    string missingFontName = warning.Description.Split('"')[1]; // crude extraction
    // Load your custom font (ensure the path is correct)
    string customFontPath = $@"C:\MyCompany\Fonts\{missingFontName}.ttf";

    if (File.Exists(customFontPath))
    {
        loadOptions.FontSettings.SetFontsFolder(Path.GetDirectoryName(customFontPath), false);
        Console.WriteLine($"🔧 Embedded custom font for \"{missingFontName}\"");
    }
}
```

> **Note** : L’incorporation de polices peut augmenter la taille du fichier de sortie, il faut donc peser le compromis entre fidélité et bande passante.

## Common Pitfalls and How to Avoid Them

| Symptom | Likely Cause | Fix |
|---------|--------------|-----|
| Aucun avertissement n’apparaît même si le document semble incorrect | `SubstitutionWarningLevel` non défini sur `All` | Vérifiez que l’étape 2 définit le drapeau exactement comme indiqué |
| La liste des avertissements répète la même police plusieurs fois | Le document contient la police dans plusieurs styles | Dédupliquez si vous ne avez besoin que d’une liste unique : `fontWarnings.Select(w => w.Description).Distinct()` |
| L’application plante avec de gros fichiers DOCX | Chargement avec les paramètres mémoire par défaut | Utilisez `LoadOptions.LoadFormat` ou lisez le fichier en flux pour réduire la pression mémoire |

## Full Working Example (Copy‑Paste Ready)

```csharp
using System;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ---------------------------------------------------------------
            // Configure LoadOptions to capture font warnings
            // ---------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // OPTIONAL: add a folder with custom fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);

            // ---------------------------------------------------------------
            // Load the document
            // ---------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";
            Document doc = new Document(docPath, loadOptions);

            // ---------------------------------------------------------------
            // Retrieve and display missing‑font warnings
            // ---------------------------------------------------------------
            var fontWarnings = doc.WarningInfoCollection
                                  .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // ---------------------------------------------------------------
            // OPTIONAL: automatic handling (fallback or embedding)
            // ---------------------------------------------------------------
            // Example: substitute everything with Arial
            // loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution { SubstituteFont = "Arial" };

            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

Exécutez le programme avec `dotnet run`. Vous devriez voir la liste des polices manquantes affichée dans la console, confirmant que vous avez bien **capturé les avertissements de police**.

## Conclusion

Vous disposez maintenant d’un modèle complet, prêt pour la production, pour **capturer les avertissements de police**, **détecter les polices manquantes**, **gérer les polices manquantes**, et **lister les polices manquantes** en utilisant Aspose.Words en C#. Cette approche est légère, ne nécessite que quelques lignes de code, et peut être intégrée à n’importe quel pipeline existant—que vous

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}