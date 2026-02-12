---
category: general
date: 2026-02-12
description: Créer un gestionnaire d’avertissements de police pour détecter les polices
  manquantes et suivre les polices manquantes dans Aspose.Words. Apprenez à consigner
  les avertissements efficacement.
draft: false
keywords:
- create font warning handler
- detect missing fonts
- track missing fonts
- how to log warnings
language: fr
og_description: Créer un gestionnaire d’avertissement de police en C# pour détecter
  les polices manquantes et apprendre à consigner les avertissements lorsque Aspose.Words
  remplace les polices.
og_title: Créer un gestionnaire d’avertissements de polices – Détecter les polices
  manquantes
tags:
- Aspose.Words
- C#
- Document Processing
title: Créer un gestionnaire d’avertissements de police – Détecter les polices manquantes
  en C#
url: /fr/net/working-with-fonts/create-font-warning-handler-detect-missing-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un gestionnaire d'avertissement de police – Détecter les polices manquantes en C#

Vous avez déjà eu besoin de **create font warning handler** parce qu'un document Word remplaçait silencieusement une police que vous n'aviez pas prévue ? Vous n'êtes pas le seul. Lorsque Aspose.Words charge un DOCX qui fait référence à une police absente sur le serveur, il revient silencieusement à une police par défaut—laissant votre mise en page subtilement cassée.  

Dans ce tutoriel, nous vous montrerons exactement comment **detect missing fonts**, **track missing fonts**, et **how to log warnings** afin que vous puissiez repérer ces substitutions avant qu'elles ne vous posent problème. À la fin, vous disposerez d'un gestionnaire d'avertissement réutilisable qui imprime chaque événement de substitution de police dans la console (ou tout journal que vous préférez). Pas de mystère, juste du code clair et exploitable.

## Prérequis

- .NET 6.0 ou ultérieur (l'API est la même pour .NET Framework 4.6+)
- Aspose.Words for .NET installé (`dotnet add package Aspose.Words`)
- Un fichier Word qui fait référence à une police non installée sur votre machine (par ex., `MissingFont.docx`)

Si vous avez déjà cela, super—passons à l'action.

## Étape 1 : Configurer LoadOptions avec un rappel d'avertissement  

La première chose à faire lorsque vous voulez **create font warning handler** est d'indiquer à Aspose.Words de déclencher un rappel chaque fois qu'il rencontre un problème. `LoadOptions` est le conteneur de cette configuration.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Create LoadOptions and attach our custom handler
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

**Pourquoi c'est important :**  

`LoadOptions` est le seul endroit où vous pouvez brancher un `IWarningCallback`. Sans cela, Aspose.Words enregistrera les avertissements en interne mais vous ne les verrez jamais. En assignant `FontWarningHandler`, nous obtenons un contrôle total sur ce qui se passe lorsqu'une police manquante est substituée.

## Étape 2 : Implémenter la classe FontWarningHandler  

Nous créons maintenant le code **create font warning handler**. La classe implémente `IWarningCallback` et reçoit un objet `WarningInfo` pour chaque avertissement émis par Aspose.Words.

```csharp
// Step 2: Implement the warning handler that logs substitution details.
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            // This is where we **track missing fonts** and **how to log warnings**
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**Explication :**  

- `info.Type` nous indique la catégorie de l'avertissement. Nous nous intéressons à `WarningType.FontSubstitution` car c'est ce qui signale une police manquante.
- `info.Description` contient un message lisible par l'homme comme *“Font 'Comic Sans MS' was not found. Substituted with 'Arial'.”*
- En écrivant dans `Console.WriteLine`, nous **log warnings** instantanément. Dans une application réelle, vous pourriez remplacer cela par `ILogger`, un écrivain de fichier, ou un service de télémétrie.

> **Astuce :** Si vous devez collecter toutes les polices manquantes pour un rapport ultérieur, stockez `info.Description` dans une `List<string>` au lieu de l'imprimer.

## Étape 3 : Charger le document en utilisant les LoadOptions configurés  

Avec le rappel en place, le chargement d'un document déclenchera automatiquement notre gestionnaire chaque fois qu'une police est manquante.

```csharp
// Step 3: Load the document using the configured LoadOptions.
Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

**Ce que vous verrez :**  

L'exécution du programme affiche quelque chose de similaire à :

```
Font substitution detected: Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

Cette ligne confirme que vous avez bien **detected missing fonts** et que vous **track missing fonts** maintenant en temps réel.

## Étape 4 : Vérifier que le gestionnaire fonctionne avec différents scénarios  

Il est facile de supposer que le gestionnaire ne fonctionne que pour les fichiers DOCX, mais Aspose.Words prend en charge de nombreux formats. Essayez de charger un PDF qui fait référence à une police intégrée, ou un ancien fichier `.doc`. Le même rappel se déclenche pour tout format qui passe par le pipeline de résolution de police.

```csharp
// Loading a PDF that uses an unavailable font
Document pdfDoc = new Document("MissingFont.pdf", loadOptions);
```

Si le PDF fait référence à une police qui n'est pas installée, vous obtiendrez la même sortie console. Cela démontre que votre solution **create font warning handler** est indépendante du format.

## Étape 5 : Étendre le gestionnaire – Enregistrement dans un fichier  

La sortie console est pratique pour les démonstrations, mais le code de production écrit généralement dans un fichier de journal. Voici un petit ajustement.

```csharp
using System.IO;

class FontWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] {info.Description}";
            // Append to the log file
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}
```

Désormais, chaque fois qu'une police est substituée, le message est ajouté à `font-warnings.log`. Cela répond à la partie **how to log warnings** du brief et vous fournit une trace d'audit persistante.

## Étape 6 : Mettre tout ensemble – Exemple complet et exécutable  

Ci-dessous le programme complet que vous pouvez copier‑coller dans une application console. Aucun morceau ne manque ; il suffit de remplacer le chemin du fichier par votre propre document.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 2: Implement the warning handler
    class FontWarningHandler : IWarningCallback
    {
        private readonly string _logPath = "font-warnings.log";

        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                string message = $"[{DateTime.Now}] {info.Description}";
                Console.WriteLine(message);               // Immediate feedback
                File.AppendAllText(_logPath, message + Environment.NewLine);
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 1: Configure LoadOptions with our handler
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningHandler()
            };

            // Step 3: Load a document that likely has missing fonts
            string docPath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            doc.Save("output.pdf");
            Console.WriteLine("Document processed. Check console and font-warnings.log for any font substitutions.");
        }
    }
}
```

**Résultat attendu :**  

- La console imprime chaque ligne de substitution.  
- `font-warnings.log` contient maintenant un enregistrement horodaté de chaque événement de police manquante.  
- Le fichier `output.pdf` est créé en utilisant les polices substituées, garantissant que la conversion réussisse même lorsque les polices d'origine ne sont pas disponibles.

## Questions fréquentes & cas limites  

| Question | Answer |
|----------|--------|
| *Et si je veux ignorer certaines polices ?* | Dans `Warning`, vérifiez `info.Description` pour le nom de la police et `return;` tôt pour les polices que vous considérez acceptables. |
| *Le gestionnaire se déclenchera-t-il pour les polices intégrées ?* | Non—les polices intégrées sont toujours disponibles pour le document, donc aucun avertissement de substitution ne se produit. |
| *Puis-je capturer d'autres types d'avertissements (par ex., problèmes de résolution d'image) ?* | Absolument. Supprimez la garde `if (info.Type == WarningType.FontSubstitution)` ou ajoutez des blocs `if` supplémentaires pour `WarningType.ImageResolution`. |
| *Le gestionnaire est‑il thread‑safe ?* | L'implémentation par défaut présentée écrit dans un fichier sans synchronisation. Pour les scénarios multi‑threads, encapsulez les écritures de fichier dans un lock ou utilisez un logger concurrent. |

## Prochaines étapes  

Maintenant que vous savez **how to log warnings** pour les polices manquantes, vous pourriez vouloir :

- **Detect missing fonts** pendant un processus d'importation par lots et générer un rapport récapitulatif.  
- **Track missing fonts** sur plusieurs documents et envoyer une alerte email lorsqu'une police particulière apparaît fréquemment.  
- **Integrate with a monitoring system** (par ex., Azure Application Insights) pour mettre en évidence les tendances de substitution de police au fil du temps.  

Toutes ces extensions s'appuient sur la même fondation `IWarningCallback` que nous avons créée.

---

*Bon codage ! Si vous rencontrez des particularités—peut‑être un dossier de polices personnalisé ou un partage réseau—laissez un commentaire ci‑dessous. La communauté (et moi) sommes toujours heureux de vous aider à affiner votre stratégie d'avertissement de police.* 

![create font warning handler example](image-placeholder.png "create font warning handler example")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}