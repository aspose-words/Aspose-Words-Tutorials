---
category: general
date: 2026-01-14
description: Enregistrez les avertissements de substitution de polices lors du chargement
  de documents Word avec Aspose.Words. Apprenez à détecter les polices manquantes
  et à les capturer en C#.
draft: false
keywords:
- log font substitution warnings
- detect missing fonts
- how to capture missing fonts
language: fr
og_description: Consignez les avertissements de substitution de police lors du chargement
  de documents Word avec Aspose.Words. Découvrez comment détecter les polices manquantes
  et les capturer en C#.
og_title: Journal des avertissements de substitution de police – Guide complet d'Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: Journal des avertissements de substitution de police – Guide complet d'Aspose.Words
url: /fr/net/working-with-fonts/log-font-substitution-warnings-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Journaliser les avertissements de substitution de police – Guide complet d'Aspose.Words

Journaliser les avertissements de substitution de police est essentiel lorsque vous devez garantir qu'un document Word apparaît exactement de la même façon après son chargement par Aspose.Words. Si vous vous êtes déjà demandé comment **détecter les polices manquantes** ou si vous voulez savoir **comment capturer les polices manquantes**, vous êtes au bon endroit.  

Dans ce tutoriel, nous parcourrons un scénario réel, vous montrerons le code C# complet, et expliquerons pourquoi chaque ligne est importante. À la fin, vous pourrez journaliser chaque événement de substitution de police et agir en conséquence—plus aucun avertissement mystérieux.

![Exemple d'avertissements de substitution de police](/images/font-warnings.png "Screenshot showing console output of log font substitution warnings")

## Ce que vous allez apprendre

- Comment configurer `LoadOptions` afin qu'Aspose.Words émette des avertissements typés pour la substitution de police.  
- Les étapes exactes pour **détecter les polices manquantes** lors du chargement du document.  
- Une méthode propre pour **capturer les polices manquantes** et les écrire dans votre propre journal ou système de surveillance.  
- La gestion des cas limites (par ex., lorsqu'un document contient une police qui n'est pas installée sur le serveur).  

### Prérequis

- .NET 6.0 ou version ultérieure (le code fonctionne également avec .NET Framework 4.6+).  
- Une licence valide d'Aspose.Words for .NET (ou l'essai gratuit).  
- Une connaissance de base du C# et des applications console.  

Si vous avez déjà tout cela, plongeons‑y.

## Étape 1 – Configurer LoadOptions pour émettre des avertissements typés

Le cœur de la solution réside dans `LoadOptions.FontSubstitutionWarning`. En le passant à `RaiseTypedWarnings`, vous indiquez à Aspose.Words de déclencher un événement **à chaque fois** qu'il ne trouve pas la police exacte que vous avez demandée.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // Step 1: Create a LoadOptions instance that will raise warnings.
        var loadOptions = new LoadOptions
        {
            // This flag makes Aspose.Words emit detailed warnings instead of silently substituting.
            FontSubstitutionWarning = LoadOptions.FontSubstitutionWarningOption.RaiseTypedWarnings
        };
```

> **Pourquoi c’est important :**  
> Le comportement par défaut remplace silencieusement une police manquante par la correspondance la plus proche, ce qui peut entraîner des problèmes de mise en page que vous ne voyez jamais venir. Émettre des avertissements typés vous donne une visibilité totale.

## Étape 2 – S'abonner à l'événement d'avertissement

Nous nous accrochons maintenant à `loadOptions.FontSubstitutionWarning`. Le lambda reçoit un objet `e` qui indique exactement quelle police était manquante et laquelle a été utilisée à la place.

```csharp
        // Step 2: Attach an event handler to capture each substitution.
        loadOptions.FontSubstitutionWarning += (sender, e) =>
        {
            // Log to console – replace with your own logger if needed.
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

> **Astuce pro :** Si vous exécutez cela sur un serveur web, remplacez `Console.WriteLine` par un logger structuré (Serilog, NLog, etc.) afin de pouvoir interroger les données plus tard.

## Étape 3 – Charger le document avec les options configurées

Avec le mécanisme d'avertissement en place, chargez simplement le document comme vous le feriez habituellement. L'événement se déclenche automatiquement pour chaque police manquante.

```csharp
        // Step 3: Load the target document while the warning handler is active.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath, loadOptions);

        // Optional: do something with the document – e.g., save as PDF.
        // doc.Save(@"YOUR_DIRECTORY\output.pdf");
    }
}
```

### Sortie console attendue

Si `input.docx` référence une police appelée *MyFancyFont* qui n'est pas installée, vous verrez :

```
Missing font: MyFancyFont – substituted with Arial
Missing font: AnotherMissingFont – substituted with Times New Roman
```

Chaque ligne correspond à un événement de **détection de polices manquantes**, vous offrant une traçabilité complète.

## Étape 4 – Gestion des cas limites et scénarios avancés

### 4.1 Lorsqu'aucune substitution ne se produit

Parfois, un document n'utilise que des polices système déjà présentes. Dans ce cas, l'événement d'avertissement ne se déclenche jamais, et vous obtenez une console propre sans sortie. C’est un bon signe—votre environnement possède déjà toutes les polices requises.

### 4.2 Capturer les avertissements pour une analyse ultérieure

Si vous devez stocker les avertissements pour un rapport nocturne, collectez‑les dans une liste :

```csharp
        var missingFonts = new List<(string Original, string Substituted)>();
        loadOptions.FontSubstitutionWarning += (s, e) =>
        {
            missingFonts.Add((e.FontName, e.SubstitutedFontName));
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

Après le chargement, vous pouvez sérialiser `missingFonts` en JSON, l'écrire dans une base de données, ou envoyer un résumé par e‑mail.

### 4.3 Travailler avec des PDF ou d'autres formats

La même approche `LoadOptions` fonctionne pour les appels `Load` sur les PDF, RTF, et même les fichiers HTML. Il suffit de transmettre la même instance d'options, et Aspose.Words émettra des avertissements pour toute police qu'il ne peut pas faire correspondre.

## Étape 5 – Vérifier le résultat programmatique

Si vous préférez un test automatisé plutôt que de regarder la console, affirmez que la liste contient les entrées attendues :

```csharp
        // Simple verification (use a testing framework in real projects)
        if (missingFonts.Count == 0)
        {
            Console.WriteLine("All fonts were available – no substitution warnings.");
        }
        else
        {
            Console.WriteLine($"Total missing fonts detected: {missingFonts.Count}");
        }
```

Cet extrait montre **comment capturer les polices manquantes** dans le code, pas seulement dans les journaux.

## Pièges courants & comment les éviter

| Piège | Pourquoi cela se produit | Solution |
|-------|--------------------------|----------|
| Oublier de définir `RaiseTypedWarnings` | La valeur par défaut est `DoNotRaise`, donc aucun événement n'est déclenché. | Définissez explicitement `FontSubstitutionWarning` comme indiqué à l'étape 1. |
| Utiliser `Console.WriteLine` dans une application web | La sortie console disparaît sous IIS/ASP.NET Core. | Passez à un logger persistant (par ex., Serilog). |
| Charger un document avec un chemin relatif | Le répertoire de travail peut différer à l'exécution. | Utilisez des chemins absolus ou `Path.Combine(AppContext.BaseDirectory, "input.docx")`. |
| Ignorer le `SubstitutedFontName` | Vous perdez la visibilité sur la police de secours choisie. | Journalisez toujours à la fois `FontName` et `SubstitutedFontName`. |

## Bonus : Automatiser l'installation des polices

Si vous contrôlez l'environnement de déploiement, vous pouvez pré‑installer les polices manquantes à l'aide d'un script PowerShell :

```powershell
$fonts = @("MyFancyFont.ttf", "AnotherMissingFont.otf")
foreach ($font in $fonts) {
    $dest = "$env:SystemRoot\Fonts\$font"
    Copy-Item -Path ".\fonts\$font" -Destination $dest -Force
}
```

Exécuter ce script avant le démarrage de votre application élimine la plupart des avertissements de **détection de polices manquantes**.

## Conclusion

Nous avons couvert tout ce dont vous avez besoin pour **journaliser les avertissements de substitution de police** lors du chargement de documents Word avec Aspose.Words. En configurant `LoadOptions`, en vous abonnant à l'événement d'avertissement, et éventuellement en persistant les résultats, vous pouvez **détecter les polices manquantes** de façon fiable et comprendre **comment capturer les polices manquantes** pour tout projet .NET.

Prenez le code, adaptez le logger à votre stack, et vous ne serez plus jamais surpris par un échange de police silencieux. Les prochaines étapes pourraient inclure :

- Intégrer la liste d'avertissements à votre pipeline CI/CD pour faire échouer les builds lorsque des polices critiques sont manquantes.  
- Étendre l'approche pour surveiller l'utilisation des polices sur un parc de documents.  
- Explorer l'API `FontSettings` d'Aspose.Words pour fournir des polices de secours personnalisées.

Des questions ou un scénario difficile ? Laissez un commentaire, et résolvons-le ensemble. Bon codage !

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}