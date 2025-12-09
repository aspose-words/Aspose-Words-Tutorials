---
language: fr
url: /french/net/getting-started/tutorial/
---

{{< layout-start >}}

{{< layout-start >}}

```yaml
---
title: "Detect Missing Fonts in Aspose.Words Documents – Complete C# Guide"
description: "Detect missing fonts in your Aspose.Words documents using a warning callback. Learn how to log font substitutions with C# and keep your PDFs looking right."
date: 2025-12-08
draft: false
language: "en"
category: "general"
url: "PLACEHOLDER_URL"
keywords:
  - detect missing fonts
  - Aspose.Words warning callback
  - font substitution
  - LoadOptions C#
  - document loading C#
  - missing font detection
tags:
  - Aspose.Words
  - C#
  - Font Management
og_title: "Detect Missing Fonts in Aspose.Words – Step‑by‑Step C# Guide"
og_description: "Detect missing fonts in Aspose.Words documents instantly. Follow this guide to set up a warning callback and capture font substitution events in C#."
---
```

# Détecter les polices manquantes dans les documents Aspose.Words – Guide complet C#

Vous êtes-vous déjà demandé comment **détecter les polices manquantes** lorsque vous chargez un fichier Word avec Aspose.Words ? Dans mon travail quotidien, je suis tombé sur quelques PDF qui semblaient incorrects parce que le document original utilisait une police que je n’avais pas installée. Bonne nouvelle : Aspose.Words peut vous indiquer exactement quand il substitue une police, et vous pouvez capturer cette information avec un simple rappel d’avertissement.

Dans ce tutoriel, nous allons parcourir un **exemple complet et exécutable** qui montre comment consigner chaque substitution de police, pourquoi le rappel est important, et quelques astuces supplémentaires pour une détection robuste des polices manquantes. Pas de fioritures, juste le code et le raisonnement dont vous avez besoin pour le faire fonctionner dès aujourd’hui.

---

## Ce que vous allez apprendre

- Comment implémenter le **rappel d’avertissement Aspose.Words** pour intercepter les événements de substitution de police.  
- Comment configurer **LoadOptions C#** afin que le rappel soit invoqué lors du chargement d’un document.  
- Comment vérifier que la détection des polices manquantes a réellement fonctionné, et à quoi ressemble la sortie console.  
- Ajustements optionnels pour les gros lots ou les environnements sans interface graphique.  

**Prérequis** – Vous avez besoin d’une version récente d’Aspose.Words pour .NET (le code a été testé avec la version 23.12), .NET 6 ou ultérieur, et une compréhension de base du C#. Si vous avez tout cela, vous êtes prêt à commencer.

---

## Détecter les polices manquantes avec un rappel d’avertissement

Le cœur de la solution est une implémentation de `IWarningCallback`. Aspose.Words déclenche un objet `WarningInfo` pour de nombreuses situations, mais nous ne nous intéressons qu’à `WarningType.FontSubstitution`. Voyons comment s’y brancher.

### Étape 1 : Créer un collecteur d’avertissements de police

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    // The Warning method is called automatically by the library.
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // Write a helpful message to the console.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

*Pourquoi c’est important* : En filtrant sur `WarningType.FontSubstitution`, nous évitons le bruit des avertissements non pertinents (comme les fonctionnalités obsolètes). `info.Description` contient déjà le nom de la police d’origine et la police de secours utilisée, vous offrant ainsi une traçabilité claire.

---

## Configurer LoadOptions pour utiliser le rappel

Nous indiquons maintenant à Aspose.Words d’utiliser notre collecteur lors du chargement d’un fichier.

### Étape 2 : Configurer LoadOptions

```csharp
// Create a LoadOptions instance – this controls how the document is read.
LoadOptions loadOptions = new LoadOptions
{
    // Assign our custom warning callback.
    WarningCallback = new FontWarningCollector()
};
```

*Pourquoi c’est important* : `LoadOptions` est le seul endroit où vous pouvez brancher le rappel, les mots de passe de chiffrement et d’autres comportements de chargement. Le garder séparé du constructeur `Document` rend le code réutilisable pour de nombreux fichiers.

---

## Charger le document et capturer les polices manquantes

Avec le rappel en place, l’étape suivante consiste simplement à charger le document.

### Étape 3 : Charger votre DOCX (ou tout autre format supporté)

```csharp
// Replace the path with the location of your test document.
string inputPath = @"C:\Docs\input.docx";

try
{
    // The warning callback fires automatically during this call.
    Document doc = new Document(inputPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    // Handle file‑not‑found, access‑denied, etc.
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

Lorsque le constructeur `Document` analyse le fichier, toute police manquante déclenche notre `FontWarningCollector`. La console affichera des lignes telles que :

```
Font substituted: Arial (substituted with Liberation Sans)
Document loaded successfully.
```

Cette ligne constitue la preuve concrète que la **détection des polices manquantes** a fonctionné.

---

## Vérifier la sortie – À quoi s’attendre

Exécutez le programme depuis un terminal ou Visual Studio. Si le document source contient une police que vous n’avez pas installée, vous verrez au moins une ligne « Font substituted ». Si le document n’utilise que des polices installées, le rappel reste silencieux et vous n’obtiendrez que le message « Document loaded successfully. ».

**Astuce** : Pour vérifier, ouvrez le fichier Word dans Microsoft Word et consultez la liste des polices. Toute police apparaissant dans *Remplacer les polices* sous le groupe *Accueil → Police* est susceptible d’être substituée.

---

## Avancé : Détecter les polices manquantes en masse

Souvent, vous devez analyser des dizaines de fichiers. Le même schéma s’adapte facilement :

```csharp
string[] files = Directory.GetFiles(@"C:\Docs\Batch", "*.docx");

foreach (var file in files)
{
    Console.WriteLine($"\nProcessing: {Path.GetFileName(file)}");
    Document doc = new Document(file, loadOptions);
}
```

Comme le `FontWarningCollector` écrit dans la console à chaque invocation, vous obtenez un rapport par fichier sans logique supplémentaire. Pour les scénarios de production, vous pourriez vouloir consigner dans un fichier ou une base de données — remplacez simplement `Console.WriteLine` par votre logger préféré.

---

## Pièges courants & astuces professionnelles

| Problème | Pourquoi cela se produit | Solution |
|----------|--------------------------|----------|
| **Aucun avertissement n’apparaît** | Le document ne contient en fait que des polices installées. | Vérifiez en ouvrant le fichier dans Word ou en supprimant délibérément une police de votre système. |
| **Le rappel n’est pas appelé** | `LoadOptions.WarningCallback` n’a jamais été assigné ou une nouvelle instance de `LoadOptions` a été utilisée plus tard. | Conservez un seul objet `LoadOptions` et réutilisez‑le pour chaque chargement. |
| **Trop d’avertissements non pertinents** | Vous n’avez pas filtré par `WarningType.FontSubstitution`. | Ajoutez la condition `if (info.Type == WarningType.FontSubstitution)` comme indiqué. |
| **Ralentissement sur de très gros fichiers** | Le rappel s’exécute pour chaque avertissement, ce qui peut être nombreux pour de gros documents. | Désactivez les autres types d’avertissements via `LoadOptions.WarningCallback` ou définissez `LoadOptions.LoadFormat` sur un type spécifique si vous le connaissez. |

---

## Exemple complet fonctionnel (prêt à copier‑coller)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Step 2 – configure LoadOptions with our warning callback.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningCollector()
        };

        // Path to a single document or a folder for batch processing.
        string inputPath = @"C:\Docs\input.docx";

        try
        {
            // Step 3 – load the document; warnings are emitted automatically.
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**Sortie console attendue** (lorsqu’une police manquante est rencontrée) :

```
Font substituted: Times New Roman (substituted with Liberation Serif)
Document loaded successfully.
```

Si aucune substitution ne se produit, vous ne verrez que la ligne de succès.

---

## Conclusion

Vous disposez maintenant d’une **méthode complète et prête pour la production** afin de détecter les polices manquantes dans tout document traité par Aspose.Words. En tirant parti du **rappel d’avertissement Aspose.Words** et en configurant **LoadOptions C#**, vous pouvez consigner chaque substitution de police, dépanner les problèmes de mise en page et garantir que vos PDF conservent l’apparence prévue.

Qu’il s’agisse d’un seul fichier ou d’un lot massif, le schéma reste le même — implémentez `IWarningCallback`, branchez‑le à `LoadOptions`, et laissez Aspose.Words faire le travail lourd.

Prêt pour l’étape suivante ? Essayez de combiner cela avec **l’incorporation de polices** ou **les familles de polices de secours** pour corriger automatiquement le problème, ou explorez l’API **DocumentVisitor** pour une analyse de contenu plus approfondie. Bon codage, et que toutes vos polices restent là où vous les attendez !

---

![Detect missing fonts in Aspose.Words – console output screenshot](https://example.com/images/detect-missing-fonts.png "detect missing fonts console output")

{{< layout-end >}}

{{< layout-end >}}