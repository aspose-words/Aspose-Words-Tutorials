---
category: general
date: 2026-05-04
description: Apprenez à utiliser la substitution de polices Aspose pour détecter les
  polices manquantes lors du chargement d’un document Word et récupérer les détails
  des polices manquantes — guide étape par étape.
draft: false
keywords:
- aspose font substitution
- detect missing fonts
- load word document
- retrieve missing font
language: fr
og_description: Maîtrisez la substitution de polices Aspose pour détecter les polices
  manquantes lors du chargement d’un document Word et récupérer les informations sur
  les polices manquantes avec un code C# complet.
og_title: Substitution de polices Aspose – Détecter les polices manquantes dans les
  documents Word
tags:
- Aspose.Words
- C#
- Font Management
title: 'Substitution de polices Aspose : détecter les polices manquantes dans les
  documents Word'
url: /fr/net/working-with-fonts/aspose-font-substitution-detect-missing-fonts-in-word-docs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution – Détecter les polices manquantes dans les documents Word

Vous êtes‑vous déjà demandé pourquoi un document Word apparaît incorrect sur une autre machine ? Souvent, le coupable est une police manquante, et **Aspose font substitution** est l’outil qui vous permet de repérer ces lacunes avant qu’elles ne deviennent un désastre visuel. Dans ce tutoriel, nous allons vous montrer comment **detect missing fonts** dès que vous **load a Word document**, puis **retrieve missing font** les détails afin que vous puissiez les corriger ou les remplacer.

Nous couvrirons tout, de la configuration du rappel d’avertissement à l’obtention d’une liste propre des polices manquantes. À la fin, vous disposerez d’un extrait C# prêt à l’emploi qui indique exactement quelles polices n’ont pas été trouvées, et vous comprendrez pourquoi cela est important pour la fidélité du document.

---

## Prérequis – Ce dont vous avez besoin avant de commencer

- **Aspose.Words for .NET** (v23.12 ou version ultérieure recommandée).  
- Un environnement de développement .NET (Visual Studio, Rider ou le CLI `dotnet`).  
- Un fichier DOCX d’exemple qui utilise intentionnellement une police que vous n’avez pas installée — appelez‑le `DocumentWithMissingFont.docx`.  
- Connaissances de base en C# — rien de compliqué, juste la capacité d’exécuter une application console.

Si l’un de ces éléments vous est inconnu, faites une pause et installez le package NuGet :

```bash
dotnet add package Aspose.Words
```

C’est tout. Pas de polices supplémentaires, pas de services externes.

## Étape 1 : Charger le document Word (et déclencher la vérification des polices)

La toute première chose à faire est de **load a Word document**. Aspose.Words analyse le fichier et, s’il ne trouve pas une police référencée, il place un avertissement *FontSubstitution*. Voici le code qui effectue le chargement :

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Path to the DOCX that may contain missing fonts
string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";

// Load the document – this is where Aspose starts checking fonts
Document doc = new Document(docPath);
```

> **Pourquoi c’est important :** Charger le document dès le départ donne à Aspose la possibilité d’analyser chaque séquence de texte, style et objet incorporé. Si une police n’est pas trouvée sur le système ou dans le dossier de polices personnalisé, vous recevrez un avertissement ultérieurement.

## Étape 2 : Attacher un rappel d’avertissement pour capturer les événements de substitution

Aspose.Words utilise un mécanisme de rappel pour vous informer des problèmes tels que les polices manquantes. En assignant une implémentation de `IWarningCallback` à `doc.WarningCallback`, vous pouvez intercepter chaque avertissement au moment où il se produit.

```csharp
// Register the callback that will handle font substitution warnings
doc.WarningCallback = new FontSubstitutionWarningCallback();
```

> **Astuce :** Vous pouvez attacher plusieurs rappels (par ex., journalisation, mises à jour UI) en les encapsulant dans un motif composite, mais pour ce tutoriel, un seul rappel garde les choses claires.

## Étape 3 : Implémenter le rappel d’avertissement de substitution de police

Nous définissons maintenant la classe qui effectue réellement le travail. Le rappel reçoit un objet `WarningInfo` ; nous filtrons les éléments de type `WarningType.FontSubstitution` et stockons la description pour une utilisation ultérieure.

```csharp
class FontSubstitutionWarningCallback : IWarningCallback
{
    // A thread‑safe list to collect all missing‑font messages
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        // We only care about font substitution warnings
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write to console for immediate feedback
            Console.WriteLine($"Font substituted: {info.Description}");
            // Keep the message for later retrieval
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

> **Ce qui se passe :** Lorsque Aspose rencontre une police manquante, il crée un avertissement tel que « Font substitution : 'Comic Sans MS' n’a pas été trouvée, utilisation de 'Arial' à la place. ». Notre rappel affiche cette ligne et l’enregistre.

## Étape 4 : Traiter le document (optionnel) et rassembler les polices manquantes

Si vous avez seulement besoin de **detect missing fonts**, l’étape de chargement suffit — les avertissements sont déclenchés automatiquement. Cependant, de nombreux développeurs ont également besoin de **retrieve missing font** après avoir effectué certaines opérations (par ex., sauvegarde, conversion). Ci‑dessous, nous forçons une petite opération — la sauvegarde en PDF — pour garantir que tous les avertissements soient émis, puis nous récupérons les messages collectés.

```csharp
// Force a save to trigger any lazy warnings (optional but safe)
doc.Save("output.pdf");

// After processing, retrieve the list of missing fonts
if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
{
    Console.WriteLine("\n=== Missing Fonts Summary ===");
    foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
    {
        Console.WriteLine(msg);
    }
}
else
{
    Console.WriteLine("\nNo missing fonts were detected.");
}
```

> **Sortie console attendue** (exemple) :
> ```
> Font substituted: Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substituted: Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> 
> === Missing Fonts Summary ===
> Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> ```

Remarquez comment chaque ligne indique clairement la police d’origine et la police de secours choisie par Aspose. C’est le cœur du reporting **aspose font substitution**.

## Étape 5 : Avancé – Utiliser des sources de polices personnalisées pour réduire les substitutions

Parfois, vous *avez* les polices manquantes, mais pas dans le dossier système par défaut. Aspose.Words vous permet de pointer vers un répertoire personnalisé via `FontSettings`. Ajouter cette étape peut réduire considérablement le nombre d’avertissements de substitution.

```csharp
// Optional: Add a folder that contains your custom fonts
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
doc.FontSettings = fontSettings;
```

> **Pourquoi ajouter cela ?** Si vous distribuez des documents sur plusieurs machines, regrouper les polices requises dans un dossier connu garantit la même apparence visuelle partout. Cela rend également votre routine **detect missing fonts** plus précise car Aspose vérifie ce dossier avant de recourir à une police de secours.

## Exemple complet fonctionnel

En réunissant tous les éléments, voici un programme console prêt à copier‑coller. Enregistrez‑le sous `Program.cs` et exécutez‑le avec `dotnet run`.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // ---------- Step 1: Load the Word document ----------
        string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";
        Document doc = new Document(docPath);

        // ---------- Optional: Point to a custom font folder ----------
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
        doc.FontSettings = fontSettings;

        // ---------- Step 2: Register the warning callback ----------
        doc.WarningCallback = new FontSubstitutionWarningCallback();

        // ---------- Step 3: Force a save to trigger all warnings ----------
        doc.Save("output.pdf");

        // ---------- Step 4: Retrieve and display missing fonts ----------
        if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
        {
            Console.WriteLine("\n=== Missing Fonts Summary ===");
            foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
            {
                Console.WriteLine(msg);
            }
        }
        else
        {
            Console.WriteLine("\nNo missing fonts were detected.");
        }
    }
}

// ---------- Callback implementation ----------
class FontSubstitutionWarningCallback : IWarningCallback
{
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

**Ce que vous devriez voir :** Si le DOCX source référence des polices que vous n’avez pas, la console affiche chaque ligne de substitution suivie d’un résumé concis. Si toutes les polices sont présentes, vous recevrez le message « No missing fonts were detected. ».

## Écueils courants et comment les éviter

| Issue | Why it Happens | Fix |
|-------|----------------|-----|
| **Aucun avertissement n’apparaît** | Le document n’utilise que des polices système, ou vous avez déjà ajouté un dossier personnalisé contenant les polices manquantes. | Vérifiez que le DOCX référence réellement une police indisponible. Vous pouvez l’ouvrir dans Word et changer un paragraphe pour une police rare (par ex., « Papyrus »). |
| **Messages dupliqués** | La même police est utilisée dans plusieurs séquences, entraînant plusieurs avertissements. | Dédupliquez la liste avec `Distinct()` si vous avez besoin uniquement d’un ensemble unique. |
| **Impact sur les performances avec de gros documents** | Chaque avertissement est traité sur le thread UI. | Exécutez le chargement dans une tâche en arrière‑plan ou utilisez `Parallel.ForEach` pour le post‑traitement. |
| **Police de secours incorrecte** | Le secours par défaut d’Aspose peut ne pas correspondre à votre identité visuelle. | Définissez `FontSettings.SubstitutionSettings.DefaultFontName` sur une police de secours préférée (par ex., « Calibri »). |

## Extension de la solution – Exporter les polices manquantes en JSON

Si vous créez un service web qui doit signaler les polices manquantes à un client, la sérialisation de la liste est triviale :

```csharp
using System.Text.Json;

// After gathering messages...
string json = JsonSerializer.Serialize(FontSubstitutionWarningCallback.MissingFontMessages);
File.WriteAllText("missing-fonts.json", json);
Console.WriteLine("Missing fonts exported to missing-fonts.json");
```

Votre API peut maintenant renvoyer une charge utile JSON propre qu’un autre système pourra consommer.

## Conclusion

Dans ce guide, nous avons démontré **Aspose font substitution** de bout en bout : charger un document Word, attacher un rappel d’avertissement, capturer chaque événement *detect missing fonts*, et enfin **retrieve missing font** pour le reporting ou la remédiation. En ajoutant des dossiers de polices personnalisés optionnels, vous pouvez réduire la liste des substitutions, et avec quelques lignes supplémentaires, vous pouvez même exporter les résultats en JSON.

Rappelez‑vous que l’intégrité visuelle de vos documents dépend des polices qu’ils utilisent. Avec la technique présentée ici, vous ne serez plus jamais surpris par un remplacement inattendu.  

Prêt à passer à l’étape suivante ? Essayez d’intégrer cette logique dans un pipeline de traitement de documents plus vaste, ou explorez les autres fonctionnalités d’Aspose.Words comme l’incorporation de polices (`doc.FontSettings.EmbeddedFonts`). Les possibilités sont infinies, et vos utilisateurs vous remercieront pour le rendu soigné.

---

![Screenshot of

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}