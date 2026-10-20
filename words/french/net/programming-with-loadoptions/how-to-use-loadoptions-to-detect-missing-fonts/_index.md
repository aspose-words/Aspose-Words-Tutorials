---
category: general
date: 2026-06-08
description: Apprenez à utiliser LoadOptions dans Aspose.Words pour détecter les polices
  manquantes lors de l'importation de documents. Guide étape par étape avec du code,
  des explications et les meilleures pratiques.
draft: false
keywords:
- how to use loadoptions
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
- C# document loading
language: fr
og_description: Comment utiliser LoadOptions dans Aspose.Words et détecter les polices
  manquantes lors du chargement d’un document. Guide complet avec du code et des conseils
  pratiques.
og_title: Comment utiliser LoadOptions pour détecter les polices manquantes
schemas:
- author: Aspose
  dateModified: '2026-06-08'
  description: Learn how to use LoadOptions in Aspose.Words to detect missing fonts
    during document import. Step-by-step guide with code, explanations, and best practices.
  headline: How to Use LoadOptions to Detect Missing Fonts
  type: TechArticle
- description: Learn how to use LoadOptions in Aspose.Words to detect missing fonts
    during document import. Step-by-step guide with code, explanations, and best practices.
  name: How to Use LoadOptions to Detect Missing Fonts
  steps:
  - name: Create a Warning Handler
    text: Aspose.Words uses the `IWarningCallback` interface to notify you about non‑critical
      issues, such as font substitution. Implement the interface and decide what to
      do when a warning arrives.
  - name: Attach the Handler to LoadOptions
    text: Now we create a `LoadOptions` instance and tell it to use our `FontWarningHandler`.
      This is the point where **how to use LoadOptions** really shines.
  - name: Load the Document Using the Configured Options
    text: Finally, we feed the `LoadOptions` into the `Document` constructor. If the
      source file references a font that isn’t installed, Aspose.Words will fire the
      warning and your handler will print a message.
  - name: Multiple Documents in a Loop
    text: Often you’ll process a batch of files. The same `LoadOptions` instance can
      be reused, but remember that the `WarningCallback` persists across loads. If
      you need per‑document isolation, instantiate a fresh `LoadOptions` for each
      iteration.
  - name: Custom Font Substitution Logic
    text: 'Instead of merely logging, you might want to substitute a specific missing
      font with a corporate‑approved alternative. Extend the handler:'
  - name: Silencing Unwanted Warnings
    text: If you only care about font issues and want to suppress everything else,
      filter by `WarningType` as shown. Conversely, to log *all* warnings, drop the
      `if` check and output `info.WarningType` alongside `info.Description`.
  type: HowTo
tags:
- Aspose.Words
- C#
- Font Management
title: Comment utiliser LoadOptions pour détecter les polices manquantes
url: /fr/net/programming-with-loadoptions/how-to-use-loadoptions-to-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment utiliser LoadOptions pour détecter les polices manquantes

Vous êtes-vous déjà demandé **comment utiliser LoadOptions** lors du chargement d’un document Word avec Aspose.Words ? Dans ce tutoriel, nous vous montrerons exactement **comment utiliser LoadOptions** pour **détecter les polices manquantes** et les gérer de façon élégante. Que vous construisiez un service de conversion de documents ou un moteur de reporting, les polices manquantes peuvent provoquer des surprises de mise en page, il est donc indispensable de les repérer tôt.

Nous parcourrons chaque étape — de la connexion d’un rappel d’avertissement à l’interprétation des résultats— afin que vous terminiez avec un exemple C# complet que vous pourrez intégrer dans n’importe quel projet .NET. Aucun document externe, juste une solution autonome. À la fin, vous saurez pourquoi le système d’avertissement existe, comment l’activer et quoi faire lorsque le rappel se déclenche.

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

- **Aspose.Words for .NET** (toute version récente ; l’API que nous utilisons est stable depuis 2022).
- Un environnement de développement .NET (Visual Studio, Rider ou VS Code avec l’extension C#).
- Un fichier Word d’exemple (`input.docx`) qui référence une police que vous *n’avez pas* installée sur la machine.

C’est tout — aucun package NuGet supplémentaire en dehors d’Aspose.Words.

## Comment utiliser LoadOptions avec Aspose.Words

La classe **LoadOptions** est la porte d’entrée pour personnaliser la façon dont un document est lu. En y branchant un rappel d’avertissement, vous pouvez **détecter les polices manquantes** dès qu’Aspose.Words analyse le fichier. Décomposons cela.

### Étape 1 : Créer un gestionnaire d’avertissement

Aspose.Words utilise l’interface `IWarningCallback` pour vous notifier des problèmes non critiques, comme la substitution de police. Implémentez l’interface et décidez quoi faire lorsqu’un avertissement arrive.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Warnings;

// Step 1: Define a warning handler that will be notified of font substitutions.
class FontWarningHandler : IWarningCallback
{
    // The Process method is called for every warning Aspose.Words generates.
    public void Process(WarningInfo info)
    {
        // We're only interested in font substitution warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write a helpful message to the console.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

**Pourquoi cela importe :**  
Sans rappel, Aspose.Words remplace silencieusement les polices manquantes par une police par défaut (généralement Arial). En capturant l’avertissement `FontSubstitution`, vous pouvez consigner le problème, alerter l’utilisateur ou même remplacer la police manquante par une alternative personnalisée.

### Étape 2 : Attacher le gestionnaire à LoadOptions

Nous créons maintenant une instance de `LoadOptions` et indiquons qu’elle doit utiliser notre `FontWarningHandler`. C’est à ce moment que **comment utiliser LoadOptions** montre tout son potentiel.

```csharp
using Aspose.Words.LoadOptions;

// Step 2: Create LoadOptions and attach the warning handler.
var loadOptions = new LoadOptions
{
    // The WarningCallback property accepts any IWarningCallback implementation.
    WarningCallback = new FontWarningHandler()
};
```

**Pourquoi cela importe :**  
`LoadOptions` est un guichet unique pour de nombreux paramètres d’importation (encodage, mot de passe, etc.). En définissant `WarningCallback`, vous activez un mécanisme léger, basé sur les événements, qui fonctionne pour tout document chargé avec ces options.

### Étape 3 : Charger le document en utilisant les options configurées

Enfin, nous transmettons le `LoadOptions` au constructeur `Document`. Si le fichier source référence une police qui n’est pas installée, Aspose.Words déclenchera l’avertissement et votre gestionnaire affichera un message.

```csharp
// Step 3: Load the document using the configured LoadOptions.
// Any missing fonts will trigger the FontWarningHandler.
Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Ce que vous verrez :**  
En supposant que `input.docx` utilise une police nommée *« MyCustomFont »* qui n’est pas présente sur la machine, la sortie console sera :

```
Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
```

Si toutes les polices sont présentes, le rappel reste silencieux — aucune sortie, aucun impact sur les performances.

## Détecter les polices manquantes avec un rappel d’avertissement (Mot‑clé secondaire en action)

L’expression **detect missing fonts** apparaît naturellement dans le titre ci‑dessus, renforçant le mot‑clé secondaire. Explorons quelques variantes que vous pourriez rencontrer dans des projets réels.

### Plusieurs documents dans une boucle

Il est fréquent de traiter un lot de fichiers. La même instance de `LoadOptions` peut être réutilisée, mais rappelez‑vous que le `WarningCallback` persiste d’un chargement à l’autre. Si vous avez besoin d’une isolation par document, créez une nouvelle `LoadOptions` à chaque itération.

```csharp
string[] files = Directory.GetFiles(@"C:\Docs", "*.docx");
foreach (var file in files)
{
    var options = new LoadOptions { WarningCallback = new FontWarningHandler() };
    var document = new Document(file, options);
    // Perform further processing...
}
```

### Logique personnalisée de substitution de police

Au lieu de simplement consigner, vous pourriez vouloir substituer une police manquante spécifique par une alternative approuvée par votre entreprise. Étendez le gestionnaire :

```csharp
class FontWarningHandler : IWarningCallback
{
    public void Process(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Extract the missing font name from the description.
            string missingFont = info.Description.Split('\'')[1];
            // Choose a fallback based on your policy.
            string fallback = missingFont.Equals("MyCustomFont") ? "Calibri" : "Arial";
            Console.WriteLine($"Missing '{missingFont}'. Using fallback '{fallback}'.");
            // You could also modify FontSettings here if needed.
        }
    }
}
```

Vous ne **détectez plus seulement les polices manquantes**, vous décidez également comment les remplacer.

### Silencer les avertissements indésirables

Si vous ne vous souciez que des problèmes de police et souhaitez supprimer tout le reste, filtrez par `WarningType` comme indiqué. À l’inverse, pour consigner *tous* les avertissements, supprimez la condition `if` et affichez `info.WarningType` ainsi que `info.Description`.

## Exemple complet, exécutable

En réunissant tous les éléments, voici un programme complet que vous pouvez compiler et exécuter. Remplacez `"YOUR_DIRECTORY/input.docx"` par le chemin de votre fichier de test.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningHandler : IWarningCallback
{
    public void Process(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Ensure the Aspose.Words license is set if you have one.
        // License license = new License();
        // license.SetLicense("Aspose.Words.lic");

        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        string docPath = Path.Combine("YOUR_DIRECTORY", "input.docx");

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
            // You can now work with 'doc' – save, modify, export, etc.
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**Sortie console attendue (quand une police est manquante) :**

```
Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
Document loaded successfully.
```

Si aucune police n’est manquante, vous verrez simplement :

```
Document loaded successfully.
```

## Pièges courants & Astuces professionnelles

- **Pitfall :** Oublier de définir `WarningCallback`. L’API substituera quand même les polices, mais vous ne le saurez jamais.  
  **Pro tip :** Attachez toujours un gestionnaire lorsque vous avez besoin d’une fidélité des polices ; cela ne coûte pratiquement rien.

- **Pitfall:** 

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques présentées dans ce guide. Chaque ressource inclut des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Comment détecter les polices dans Aspose.Words – Gérer les avertissements & paramètres](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Comment capturer les polices dans Aspose.Words – Guide complet](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)
- [Comment charger un DOCX et détecter les polices manquantes – Guide complet C#](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}