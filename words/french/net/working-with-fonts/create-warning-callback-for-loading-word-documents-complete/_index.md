---
category: general
date: 2026-03-25
description: Créer un rappel d’avertissement pour charger un document Word et détecter
  les polices manquantes. Apprenez comment configurer les paramètres de police dans
  Aspose.Words pour .NET.
draft: false
keywords:
- create warning callback
- load word document
- detect missing fonts
- configure font settings
language: fr
og_description: Créez un rappel d’avertissement pour charger un document Word tout
  en détectant les polices manquantes. Ce guide montre comment configurer les paramètres
  de police dans Aspose.Words.
og_title: Créer un rappel d’avertissement – Charger le document Word et détecter les
  polices manquantes
tags:
- Aspose.Words
- C#
- Font handling
title: Créer un rappel d’avertissement pour le chargement de documents Word – Guide
  complet
url: /fr/net/working-with-fonts/create-warning-callback-for-loading-word-documents-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un rappel d’avertissement – Charger un document Word et détecter les polices manquantes

Vous avez déjà eu besoin de **créer un rappel d’avertissement** lors du chargement d’un document Word et vous vous êtes demandé pourquoi certaines polices disparaissent simplement ? Vous n’êtes pas seul. Dans de nombreuses applications d’entreprise, les polices manquantes provoquent des désastres de mise en page, et sans un rappel approprié vous pourriez ne jamais remarquer le problème.  

Bonne nouvelle ? Avec Aspose.Words for .NET, vous pouvez **charger un document Word**, **détecter les polices manquantes**, et **configurer les paramètres de police** en quelques lignes de code bien organisées. Dans ce tutoriel, nous parcourrons un exemple complet et exécutable, expliquerons pourquoi chaque élément est important, et vous montrerons comment vérifier que le rappel d’avertissement fait son travail.

> **Ce que vous retiendrez**  
> * Un programme C# complet qui charge un DOCX, signale toute substitution de police, et vous permet de personnaliser les chemins de recherche des polices.  
> * Compréhension des classes `FontSettings`, `LoadOptions` et `IWarningCallback`.  
> * Astuces pour gérer les cas limites comme les polices intégrées ou les dossiers de polices système.

---

## Prérequis

- .NET 6+ (ou .NET Framework 4.7.2+) avec un compilateur C#.  
- Package NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`).  
- Un fichier Word d’exemple (`input.docx`) qui utilise au moins une police non installée sur la machine (par ex., *Calibri Light* dans un conteneur Windows minimal).  
- Une connaissance de base des applications console C#.

Aucune bibliothèque supplémentaire n’est requise ; tout se trouve dans Aspose.Words.

---

## Étape 1 : Créer un rappel d’avertissement pour détecter les polices manquantes

L’élément **principal** de ce puzzle est une classe qui implémente `IWarningCallback`. Aspose.Words invoquera ce rappel chaque fois qu’il rencontre une situation justifiant un avertissement – la substitution de police étant la plus courante.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

/// <summary>
/// Handles warning events raised by Aspose.Words during document loading.
/// Specifically looks for FontSubstitution warnings and writes them to the console.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution detected: {info.Description}");
        }
    }
}
```

**Pourquoi c’est important** – Sans rappel, vous devriez fouiller les journaux après coup. En gérant les avertissements en temps réel, vous pouvez décider d’interrompre le chargement, de remplacer la police manquante par une alternative, ou simplement d’enregistrer le problème pour une révision ultérieure.

---

## Étape 2 : Configurer FontSettings pour la gestion personnalisée des polices

Avant de charger réellement le document, nous pouvons indiquer à Aspose.Words où chercher les polices qui ne sont pas présentes sur le système. C’est là que `FontSettings` intervient.

```csharp
// Create a FontSettings instance.
FontSettings fontSettings = new FontSettings();

// Add a custom folder (e.g., a shared network location) where your application stores its fonts.
fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);

// Optional: If you have a specific font to use as a universal fallback, set it here.
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

**Pourquoi c’est important** – En indiquant à Aspose.Words un dossier contenant les polices manquantes, vous évitez souvent la substitution. Lorsque cela n’est pas possible, une valeur par défaut raisonnable (comme *Arial*) maintient la lisibilité du document.

---

## Étape 3 : Charger le document Word avec le rappel d’avertissement configuré

Nous rassemblons maintenant le tout : nous créons `LoadOptions`, y intégrons nos `FontSettings` et `FontWarningHandler`, puis chargeons enfin le document.

```csharp
// Prepare LoadOptions with both FontSettings and our warning handler.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = new FontWarningHandler()
};

// Load the Word document. Replace the path with your actual file location.
Document document = new Document(@"C:\Docs\input.docx", loadOptions);

// At this point the warning handler has already printed any font‑substitution messages.
Console.WriteLine("✅ Document loaded successfully.");
```

**Pourquoi c’est important** – `LoadOptions` est l’endroit unique où vous configurez *comment* un document est lu. En fournissant à la fois la configuration des polices et le rappel d’avertissement, nous nous assurons que toute police manquante est recherchée aux bons endroits **et** signalée immédiatement.

---

## Étape 4 : Vérifier la sortie – que devriez‑vous voir ?

Exécutez le programme depuis une console. Si `input.docx` utilise une police qui n’est pas installée et qui n’est pas non plus dans `C:\SharedFonts`, vous verrez quelque chose comme :

```
⚠️ Font substitution detected: Font 'Roboto' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
```

Si toutes les polices sont disponibles, la ligne d’avertissement n’apparaît tout simplement jamais. Cette boucle de rétroaction immédiate est inestimable dans les pipelines de traitement automatisé de documents où des substitutions de police silencieuses pourraient violer les directives de marque.

---

## Étape 5 : Pièges courants et conseils de bonnes pratiques

| Piège | Comment l’éviter |
|---------|-----------------|
| **Oubli d’inclure `Aspose.Words.Fonts`** | Assurez‑vous d’avoir `using Aspose.Words.Fonts;` en haut du fichier ; sinon le compilateur signalera des types manquants. |
| **Le chemin du dossier de polices est incorrect** | Vérifiez à nouveau le chemin et définissez `recursive: true` si vous avez des sous‑dossiers. Utilisez `Path.GetFullPath` pour déboguer. |
| **Multiples rappels d’avertissement** | Aspose.Words ne prend en compte que le dernier `WarningCallback` que vous assignez. Conservez un seul gestionnaire qui délègue si vous avez besoin d’une logique plus complexe. |
| **Exécution sur un serveur sans interface** | Les écritures console sont correctes, mais pour les applications web vous préférerez peut‑être consigner dans un fichier ou un système de surveillance plutôt que d’utiliser `Console.WriteLine`. |
| **Les gros documents entraînent une perte de performance** | Réutilisez une seule instance de `FontSettings` sur plusieurs chargements ; la créer à chaque fois peut être coûteux. |

**Astuce pro** : Si vous devez *collecter* les avertissements pour une analyse ultérieure, stockez‑les dans une `List<string>` à l’intérieur du gestionnaire au lieu de les imprimer directement.

```csharp
class CollectingWarningHandler : IWarningCallback
{
    public List<string> Messages { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Messages.Add(info.Description);
    }
}
```

Vous pouvez ensuite inspecter `handler.Messages` après le chargement du document.

---

## Étape 6 : Étendre la solution – que faire si je dois intégrer une police de secours ?

Parfois, vous souhaitez que la police manquante soit *intégrée* dans le PDF de sortie afin que les visionneuses en aval voient exactement le même rendu. Après le chargement du document, vous pouvez forcer l’intégration :

```csharp
// Ensure the fallback font is embedded when saving to PDF.
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    EmbedStandardPdfFonts = false,
    FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
};

document.Save(@"C:\Docs\output.pdf", pdfOptions);
Console.WriteLine("✅ PDF saved with embedded fonts.");
```

Cet extrait montre comment la même approche de **configuration des paramètres de police** peut être étendue au-delà du simple chargement.

---

## Exemple complet exécutable

Voici le programme complet que vous pouvez copier‑coller dans un nouveau projet d’application console. Il inclut tous les éléments abordés ci‑dessus.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    // Step 1 – Warning handler
    class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ Font substitution: {info.Description}");
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2 – Configure FontSettings
            FontSettings fontSettings = new FontSettings();
            fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);
            fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";

            // Step 3 – LoadOptions with warning callback
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontWarningHandler()
            };

            // Step 4 – Load the document
            string docPath = @"C:\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");

            // Optional: Save as PDF with embedded fonts
            var pdfOptions = new PdfSaveOptions
            {
                EmbedStandardPdfFonts = false,
                FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
            };
            doc.Save(@"C:\Docs\output.pdf", pdfOptions);
            Console.WriteLine("✅ PDF saved with embedded fonts.");
        }
    }
}
```

**Sortie attendue** (lorsqu’une police manquante est présente) :

```
⚠️ Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
✅ PDF saved with embedded fonts.
```

Si aucune substitution ne se produit, seules les messages de succès apparaissent.

---

## Conclusion

Nous venons de **créer un rappel d’avertissement** qui détecte de façon fiable les **polices manquantes** lors du **chargement d’un document Word** avec Aspose.Words, et nous avons montré comment **configurer les paramètres de police** pour contrôler où la bibliothèque recherche les polices et quel substitut utiliser. En combinant `FontSettings` et `LoadOptions`, vous obtenez une visibilité complète sur les problèmes liés aux polices — plus de glitches de mise en page silencieux.

Prochaines étapes ? Essayez de remplacer le `FontWarningHandler` par un logger qui écrit dans une base de données, ou expérimentez les **règles de substitution de police** pour mapper des polices manquantes spécifiques à des alternatives approuvées par la marque. Vous pouvez également explorer le **chargement dynamique de polices** depuis le stockage cloud si votre application s’exécute dans un environnement conteneurisé.

Des questions sur un cas particulier — par exemple la gestion des fonctionnalités OpenType ou des fichiers DOCX chiffrés ? Laissez un commentaire ci‑dessous, et bon codage !  

---

![Create warning callback diagram](https://example.com/images/create-warning-callback.png "Create warning callback diagram")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}