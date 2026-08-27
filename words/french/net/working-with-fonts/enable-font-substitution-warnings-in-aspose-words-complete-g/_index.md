---
category: general
date: 2026-01-11
description: Activez les avertissements de substitution de police pour détecter les
  polices manquantes dans vos documents .NET. Apprenez comment obtenir le nom de la
  police manquante et répertorier les polices manquantes avec Aspose.Words.
draft: false
keywords:
- enable font substitution warnings
- detect missing fonts
- get missing font name
- list missing fonts
language: fr
og_description: Activez les avertissements de substitution de police dans Aspose.Words
  pour détecter les polices manquantes, obtenir le nom de la police manquante et répertorier
  les polices manquantes dans vos documents.
og_title: Activer les avertissements de substitution de police – Tutoriel C# étape
  par étape
tags:
- Aspose.Words
- C#
- Document Processing
title: Activer les avertissements de substitution de police dans Aspose.Words – Guide
  complet
url: /fr/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Activer les avertissements de substitution de police – Guide complet

Vous êtes‑vous déjà demandé pourquoi un document Word apparaît légèrement différent après l’avoir chargé sur un serveur ? Il est probable qu’une police utilisée par l’auteur original ne soit pas disponible sur votre machine, et Aspose.Words l’a remplacée silencieusement par la police la plus proche. **Activer les avertissements de substitution de police** vous permettra de savoir immédiatement quelles polices sont manquantes, par quoi elles ont été remplacées, et comment agir en conséquence.

Dans ce tutoriel, nous parcourrons un exemple pratique, de bout en bout, qui vous montre comment **détecter les polices manquantes**, récupérer le **nom de la police manquante**, et même **lister les polices manquantes** pour le reporting. Pas de superflu, juste une solution claire que vous pouvez intégrer à n’importe quel projet .NET dès aujourd’hui.

---

## Ce que vous allez apprendre

- Comment configurer `LoadOptions` afin qu’Aspose.Words émette des avertissements détaillés.
- Le code exact nécessaire pour charger un document et énumérer les avertissements liés aux polices.
- Des méthodes pour extraire le nom de la police manquante et sa substitution, puis générer un rapport propre.
- Conseils pour gérer les cas limites, comme les documents contenant des dizaines de polices manquantes ou des dossiers de polices personnalisés.

### Prérequis

- .NET 6+ (le code fonctionne également avec .NET Framework 4.7+)
- Aspose.Words for .NET 23.10 ou plus récent (vous pouvez l’obtenir via NuGet)
- Un fichier DOCX d’exemple qui référence une police que vous n’avez pas installée (nous l’appellerons `MissingFont.docx`)

Si vous avez ces bases, plongeons‑y.

---

## Étape 1 : Configurer LoadOptions pour activer les avertissements de substitution de police  

La première chose à faire est d’indiquer à Aspose.Words que les polices manquantes vous importent. Par défaut, la bibliothèque ne consigne les avertissements qu’en interne. Définir `SubstitutionWarningLevel` à `Typical` (ou `All` pour la sortie la plus détaillée) active le mécanisme.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Create a new LoadOptions instance
LoadOptions loadOptions = new LoadOptions();

// Attach a FontSettings object so we can tweak font‑related behavior
loadOptions.FontSettings = new FontSettings();

// Enable warnings for typical font substitutions (covers most real‑world cases)
loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;
```

**Pourquoi c’est important :**  
Lorsque `SubstitutionWarningLevel` est défini, chaque fois qu’Aspose.Words ne trouve pas une police référencée, il ajoute un `FontSubstitutionWarning` à la collection `Warnings` du document. Cette collection est le seul moyen fiable de **détecter les polices manquantes** sans analyser le document manuellement.

> **Astuce :** Si vous traitez un lot de documents et que vous voulez être absolument certain de capturer chaque substitution, utilisez `FontSubstitutionWarningLevel.All`. C’est un peu plus bruyant mais cela garantit qu’aucun avertissement ne passe inaperçu.

---

## Étape 2 : Charger le document en utilisant les options configurées  

Maintenant que le système d’avertissement est prêt, chargez votre DOCX avec les `LoadOptions` que nous venons de préparer. Le chemin peut être absolu ou relatif ; assurez‑vous simplement que le fichier existe.

```csharp
// Path to the DOCX that references a font you don’t have
string docPath = @"C:\Docs\MissingFont.docx";

// Load the document while respecting our warning configuration
Document document = new Document(docPath, loadOptions);
```

**Ce qui se passe en coulisses :**  
Aspose.Words analyse le XML du document, résout chaque élément `<w:font>` et vérifie le catalogue de polices du système (plus tout dossier personnalisé que vous avez éventuellement ajouté à `FontSettings`). Lorsqu’il ne trouve pas une police, il enregistre un avertissement — exactement ce dont nous avons besoin pour **lister les polices manquantes** plus tard.

---

## Étape 3 : Parcourir les avertissements et extraire les détails des polices manquantes  

Avec le document en mémoire, la collection `Warnings` contient chaque `FontSubstitutionWarning`. Nous allons la parcourir, filtrer le type approprié, et afficher un rapport convivial.

```csharp
Console.WriteLine("=== Missing Font Report ===");
foreach (WarningInfo warning in document.Warnings)
{
    // Only interested in font substitution warnings
    if (warning is FontSubstitutionWarning fontWarning)
    {
        // The name of the font that was missing
        string missingFont = fontWarning.FontName;

        // The font Aspose.Words used instead
        string substitutedFont = fontWarning.SubstitutedFontName;

        Console.WriteLine($"Missing font: {missingFont}");
        Console.WriteLine($"Substituted with: {substitutedFont}");
        Console.WriteLine(new string('-', 30));
    }
}
```

**Sortie attendue** (en supposant que le document source référence `MyCustomFont` qui n’est pas installé) :

```
=== Missing Font Report ===
Missing font: MyCustomFont
Substituted with: Arial
------------------------------
Missing font: FancyScript
Substituted with: Times New Roman
------------------------------
```

Remarquez que chaque entrée vous fournit à la fois le **nom de la police manquante** (`MyCustomFont`) et la police de secours (`Arial`). C’est exactement l’information dont vous avez besoin pour décider d’incorporer la police originale, de demander à l’auteur un remplacement, ou simplement d’accepter la substitution.

---

## Étape 4 : Optionnel – Collecter les données dans une liste pour un traitement ultérieur  

Si vous devez exporter le rapport en CSV, l’envoyer via une API, ou simplement le garder en mémoire pour plus tard, vous pouvez stocker les avertissements dans une liste fortement typée.

```csharp
// Define a simple DTO to hold the warning details
public class MissingFontInfo
{
    public string MissingFont { get; set; }
    public string SubstitutedFont { get; set; }
}

// Build the list
List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();

foreach (WarningInfo warning in document.Warnings)
{
    if (warning is FontSubstitutionWarning fsw)
    {
        missingFonts.Add(new MissingFontInfo
        {
            MissingFont = fsw.FontName,
            SubstitutedFont = fsw.SubstitutedFontName
        });
    }
}

// Example: write to a CSV (requires System.IO)
var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);
```

Vous avez maintenant **list missing fonts** dans un format que tout système en aval peut consommer. Que vous alimentiez un tableau de bord ou génériez un journal d’audit, les données sont prêtes.

---

## Étape 5 : Gestion des cas limites et des pièges courants  

### Polices manquantes multiples dans une même exécution  

Les grands modèles d’entreprise référencent souvent des dizaines de polices personnalisées. La collection d’avertissements peut devenir volumineuse, mais le schéma d’itération présenté ci‑dessus s’échelonne linéairement, donc les performances ne sont pas un problème. Gardez simplement le résultat lisible — regrouper par page ou par style peut être utile si vous avez besoin d’une analyse plus approfondie.

### Dossiers de polices personnalisés  

Si vous stockez les polices dans un répertoire non standard (par ex., un partage réseau), indiquez à Aspose.Words où chercher :

```csharp
loadOptions.FontSettings.SetFontsFolder(@"\\fileserver\SharedFonts", recursive: true);
```

Définir cela *avant* de charger le document donne à la bibliothèque la possibilité de trouver les polices, ce qui peut éliminer certains avertissements.

### Suppression d’avertissements spécifiques  

Parfois, vous savez qu’une substitution particulière est acceptable (par ex., une police décorative que vous n’avez aucun problème à remplacer). Vous pouvez les filtrer après coup :

```csharp
missingFonts = missingFonts
    .Where(f => f.MissingFont != "DecorativeFont")
    .ToList();
```

### Compatibilité des versions  

L’énumération `FontSubstitutionWarningLevel` est stable depuis Aspose.Words 20.12. Si vous utilisez une version antérieure, vous devrez peut‑être la mettre à jour pour accéder à la fonctionnalité de niveau d’avertissement.

---

## Exemple complet fonctionnel  

Voici le programme complet, prêt à être exécuté, qui intègre toutes les étapes ci‑dessus. Collez‑le dans un nouveau projet console, ajoutez le package NuGet Aspose.Words, et pointez `docPath` vers un document qui référence une police manquante.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    // DTO for storing missing font info
    public class MissingFontInfo
    {
        public string MissingFont { get; set; }
        public string SubstitutedFont { get; set; }
    }

    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure LoadOptions to enable font substitution warnings
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;

            // Optional: add a custom fonts folder
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", true);

            // 2️⃣ Load the document with the above options
            string docPath = @"C:\Docs\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Gather warnings into a list
            List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();
            foreach (WarningInfo warning in doc.Warnings)
            {
                if (warning is FontSubstitutionWarning fsw)
                {
                    missingFonts.Add(new MissingFontInfo
                    {
                        MissingFont = fsw.FontName,
                        SubstitutedFont = fsw.SubstitutedFontName
                    });
                }
            }

            // 4️⃣ Output a human‑readable report
            Console.WriteLine("=== Missing Font Report ===");
            foreach (var info in missingFonts)
            {
                Console.WriteLine($"Missing font: {info.MissingFont}");
                Console.WriteLine($"Substituted with: {info.SubstitutedFont}");
                Console.WriteLine(new string('-', 30));
            }

            // 5️⃣ (Optional) Export to CSV for further analysis
            var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
            File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);

            Console.WriteLine("Report saved to C:\\Docs\\MissingFontsReport.csv");
        }
    }
}
```

L’exécution de ce programme **activera les avertissements de substitution de police**, **détectera les polices manquantes**, **obtiendra le nom de la police manquante**, et **listera les polices manquantes** à la fois dans la console et dans un fichier CSV.

---

## Conclusion  

Nous venons de couvrir tout ce dont vous avez besoin pour **activer les avertissements de substitution de police** dans Aspose.Words, de la configuration initiale à l’extraction d’une liste propre des polices manquantes. En suivant les étapes ci‑dessus, vous pourrez auditer vos documents, garantir la fidélité visuelle, et éviter les mauvaises surprises lors du rendu sur un serveur.

Ensuite, vous pourriez explorer :

- **Incorporer les polices manquantes** directement dans le PDF ou le DOCX de sortie (utilisez `FontSettings.EmbeddedFonts`).
- **Automatiser l’installation des polices** sur les agents de build en fonction du rapport généré.
- **Intégrer aux pipelines CI** pour faire échouer les builds lorsqu’il manque des polices critiques.

Essayez-les, et vous transformerez un simple système d’avertissement en un flux complet de gestion des polices.

Bon codage, et que toutes vos polices soient trouvées !

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}