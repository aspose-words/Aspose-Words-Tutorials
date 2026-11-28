---
category: general
date: 2026-06-20
description: Activez les avertissements de substitution de police en C# avec Aspose.Words.
  Apprenez à configurer LoadOptions, à capturer les avertissements et à gérer efficacement
  les polices manquantes.
draft: false
keywords:
- enable font substitution warnings
- Aspose.Words LoadOptions
- C# font substitution warnings
- document warning handling
- font substitution messages
language: fr
og_description: Activez les avertissements de substitution de police en C# avec Aspose.Words.
  Ce guide vous montre comment configurer LoadOptions, lire WarningInfo et afficher
  les messages de police manquante.
og_title: Activer les avertissements de substitution de police dans C# – Guide complet
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Enable font substitution warnings in C# using Aspose.Words. Learn how
    to configure LoadOptions, capture warnings, and handle missing fonts efficiently.
  headline: Enable Font Substitution Warnings in C# with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Font Substitution
- Warnings
title: Activer les avertissements de substitution de polices en C# avec Aspose.Words
url: /fr/net/programming-with-loadoptions/enable-font-substitution-warnings-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Activer les avertissements de substitution de police en C# avec Aspose.Words

Vous êtes‑vous déjà demandé comment **activer les avertissements de substitution de police** lorsqu’un document Word fait référence à une police qui n’est pas installée sur le serveur ? Vous n’êtes pas le seul. Les polices manquantes peuvent corrompre silencieusement la mise en page des PDF ou images générés, et la seule façon de les détecter tôt est d’écouter les avertissements émis par Aspose.Words.

Dans ce tutoriel, nous parcourrons un exemple pratique qui vous montre exactement comment activer ces avertissements, les extraire de la collection `WarningInfo` et afficher des messages pertinents dans la console. À la fin, vous saurez comment configurer **Aspose.Words LoadOptions**, gérer les **avertissements de substitution de police C#** et rendre votre pipeline de traitement de documents à toute épreuve.

Nous aborderons également quelques cas limites — ce qui se passe si vous supprimez les avertissements, ou si vous devez les consigner au lieu de les afficher—et nous vous fournirons un exemple de code complet, prêt à copier‑coller, qui fonctionne avec la dernière version d’Aspose.Words pour .NET (à partir de la version 24.10).

## Ce dont vous avez besoin

- .NET 6.0 ou ultérieur (le code fonctionne également sur .NET Framework 4.7+)
- Une référence NuGet à `Aspose.Words` (installer via `dotnet add package Aspose.Words`)
- Un fichier Word qui fait référence à une police que vous **n’avez pas** installée (par ex., `DocumentWithMissingFont.docx`)
- Un IDE convenable (Visual Studio, Rider ou VS Code)

C’est tout—pas de services supplémentaires, pas d’outils propriétaires. Prêt ? Plongeons‑y.

## Étape 1 : Activer les avertissements de substitution de police

La première chose à faire est d’indiquer à Aspose.Words que vous souhaitez être averti lorsqu’il substitue une police manquante. Cela se fait via la propriété `FontSettings` d’un objet `LoadOptions`. Par défaut, les avertissements sont **désactivés** pour garder l’API silencieuse, nous devons donc activer le commutateur nous‑mêmes.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

// Create LoadOptions and enable detailed font‑substitution warnings.
LoadOptions loadOpts = new LoadOptions
{
    // FontSettings is the gateway for all font‑related behavior.
    FontSettings = new FontSettings()
    // No extra code needed here; simply having a FontSettings instance
    // makes Aspose.Words collect font‑substitution warnings.
};
```

> **Pourquoi cela fonctionne :** Lorsque `FontSettings` n’est pas `null`, la bibliothèque remplit automatiquement `Document.WarningInfo` avec toutes les entrées `WarningType.FontSubstitution` qu’elle rencontre lors du chargement d’un document. Considérez cela comme l’activation d’un « mode débogage » pour les polices.

## Étape 2 : Charger le document avec les options configurées

Maintenant que la collection d’avertissements est active, chargez votre document en utilisant le `LoadOptions` que nous venons de préparer. Si le document contient une police manquante, Aspose.Words substituera une police de secours et ajoutera un avertissement à la liste `WarningInfo`.

```csharp
// Path to a DOCX that references a font not present on the machine.
string docPath = @"C:\Samples\DocumentWithMissingFont.docx";

// Load the document while respecting the LoadOptions we set up.
Document doc = new Document(docPath, loadOpts);
```

> **Astuce :** Si vous traitez de nombreux fichiers dans une boucle, réutilisez la même instance de `LoadOptions`—la créer une fois permet d’économiser quelques millisecondes par itération.

## Étape 3 : Parcourir WarningInfo et afficher les messages de substitution de police

Une fois le document chargé, la collection `WarningInfo` contient tous les avertissements survenus pendant le chargement. Nous ne nous intéressons qu’à `WarningType.FontSubstitution`, nous filtrons donc en conséquence.

```csharp
foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        Console.WriteLine($"Substituted: {warning.Description}");
}
```

Exécuter le fragment ci‑dessus sur un document qui fait référence à la police manquante « Papyrus » peut produire une sortie similaire à :

```
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Comic Sans MS' is not installed. Substituted with 'Times New Roman'.
```

Ce sont les **messages de substitution de police** que vous recherchiez—clairs, exploitables et prêts à être consignés ou envoyés à un système d’alerte.

## Exemple complet fonctionnel

Ci‑dessous se trouve un programme console autonome qui réunit tous les éléments. Copiez‑collez‑le dans un nouveau `.csproj` et cliquez sur **Run**.

```csharp
// ---------------------------------------------------------------
// Enable Font Substitution Warnings – Complete Example
// ---------------------------------------------------------------

using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

class Program
{
    static void Main()
    {
        // 1️⃣ Configure LoadOptions to capture font‑substitution warnings.
        LoadOptions loadOpts = new LoadOptions
        {
            FontSettings = new FontSettings()   // Enabling warning collection.
        };

        // 2️⃣ Load the target document (adjust the path to match your environment).
        string docPath = @"C:\Samples\DocumentWithMissingFont.docx";
        Document doc = new Document(docPath, loadOpts);

        // 3️⃣ Process the warning collection.
        Console.WriteLine("=== Font Substitution Warnings ===");
        bool anyWarnings = false;

        foreach (WarningInfo warning in doc.WarningInfo)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                anyWarnings = true;
                Console.WriteLine($"Substituted: {warning.Description}");
            }
        }

        if (!anyWarnings)
            Console.WriteLine("No font substitution warnings were generated.");

        // Optional: keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

### Sortie attendue

Si le document fait référence à des polices qui ne sont pas installées, vous verrez quelque chose de similaire à :

```
=== Font Substitution Warnings ===
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Courier New' is not installed. Substituted with 'Times New Roman'.
Press any key to exit...
```

Si toutes les polices sont présentes sur la machine, le programme affichera simplement :

```
=== Font Substitution Warnings ===
No font substitution warnings were generated.
Press any key to exit...
```

## Pièges courants & astuces professionnelles

| Problème | Pourquoi cela se produit | Comment corriger / éviter |
|----------|--------------------------|---------------------------|
| **Les avertissements disparaissent** | Vous avez vidé `FontSettings` ou utilisé un `LoadOptions` sans celui‑ci. | Instanciez toujours `FontSettings` même si vous ne modifiez aucune propriété. |
| **Trop d’avertissements** | Le document utilise de nombreuses polices exotiques. | Envisagez d’ajouter un dossier de polices personnalisé à `FontSettings` via `SetFontsFolder` pour réduire les substitutions. |
| **Impact sur les performances dans une boucle serrée** | Recréer `LoadOptions` à chaque itération ajoute une surcharge. | Réutilisez une seule instance de `LoadOptions` pour tous les documents. |
| **Sortie console manquante** | Exécution dans une application GUI où `Console.WriteLine` est ignoré. | Redirigez les avertissements vers un logger (`ILogger`) ou écrivez‑les dans un fichier. |

### Gestion des avertissements dans un service réel

Dans une API web, vous ne voulez probablement pas écrire dans la console. À la place, canalisez les avertissements vers un journal structuré :

```csharp
var logger = LoggerFactory.Create(builder => builder.AddConsole()).CreateLogger<Program>();

foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        logger.LogWarning("Font substitution: {Description}", warning.Description);
}
```

Ainsi, vous conservez la **gestion des avertissements de document** tout en gardant votre service propre.

## Extension de l’exemple

- **Capturer d’autres types d’avertissements** (par ex., `WarningType.UnknownFileFormat`) en supprimant le filtre `if`.
- **Enregistrer un rapport** de tous les avertissements au format JSON pour des analyses en aval.
- **Forcer une police de secours spécifique** en définissant `FontSettings.SubstitutionSettings.DefaultFontName`.

Toutes ces extensions sont naturelles une fois que vous avez maîtrisé **l’activation des avertissements de substitution de police**.

## Conclusion

Nous vous avons montré comment **activer les avertissements de substitution de police** en C# avec Aspose.Words, depuis la configuration de `LoadOptions` jusqu’à l’itération sur `WarningInfo` et l’affichage de messages conviviaux. En suivant les étapes ci‑dessus, vous pouvez protéger vos pipelines de traitement de documents contre les changements de mise en page silencieux causés par des polices manquantes.

Ensuite, essayez d’ajouter un dossier de polices personnalisé, de consigner les avertissements dans un fichier, ou même de les envoyer à un tableau de bord de surveillance. Le même schéma fonctionne pour tout scénario de **gestion des avertissements de document**, que vous convertissiez en PDF, rendiez des images ou effectuiez un publipostage.

Des questions sur les **avertissements de substitution de police C#** ou envie de partager une astuce ingénieuse ? Laissez un commentaire ci‑dessous—bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Activer les avertissements de substitution de police dans Aspose.Words – Guide complet](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Comment détecter les polices dans Aspose.Words – Gérer les avertissements & paramètres](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Capturer les avertissements de substitution de police en Java avec Aspose.Words – Guide complet](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}