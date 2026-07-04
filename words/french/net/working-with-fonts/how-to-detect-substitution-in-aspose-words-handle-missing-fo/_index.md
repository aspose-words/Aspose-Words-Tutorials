---
category: general
date: 2026-04-24
description: Comment détecter la substitution des polices manquantes dans Aspose.Words
  en C#. Ce guide vous montre comment gérer les polices manquantes de manière fiable
  avec les avertissements de FontSettings.
draft: false
keywords:
- how to detect substitution
- handle missing fonts
- Aspose.Words font warnings
- C# missing font detection
- FontSettings event handling
language: fr
og_description: Comment détecter la substitution des polices manquantes dans Aspose.Words
  avec C#. Apprenez à gérer les polices manquantes à l'aide des avertissements FontSettings.
og_title: Comment détecter la substitution dans Aspose.Words – Guide complet
tags:
- Aspose.Words
- C#
- Fonts
- .NET
title: Comment détecter la substitution dans Aspose.Words – Gérer les polices manquantes
url: /fr/net/working-with-fonts/how-to-detect-substitution-in-aspose-words-handle-missing-fo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment détecter la substitution dans Aspose.Words – Gérer les polices manquantes

Vous vous êtes déjà demandé **comment détecter la substitution** lorsqu’un document tente d’utiliser une police qui n’est pas installée sur votre serveur ? C’est un problème fréquent, surtout lorsque vous générez des PDF ou des fichiers Word dans un pipeline automatisé. La bonne nouvelle, c’est qu’Aspose.Words vous fournit un crochet intégré pour repérer exactement cette situation, et vous pouvez également **gérer les polices manquantes** de manière élégante.

Dans ce tutoriel, nous parcourrons un exemple concret qui montre **comment détecter la substitution** via l’événement `FontSettings.Warning`, et nous expliquerons comment **gérer les polices manquantes** sans interrompre votre flux de traitement. À la fin, vous disposerez d’un extrait prêt à l’emploi, d’une compréhension claire de l’importance de chaque ligne, et de quelques astuces pour éviter les pièges habituels.

## Prérequis

- .NET 6.0 ou version ultérieure (le code fonctionne également sur .NET Framework)
- Aspose.Words pour .NET (package NuGet `Aspose.Words`) – version 23.11 ou plus récente
- Un document d’exemple qui référence une police que vous n’avez pas installée (par ex., `MissingFont.docx`)
- Visual Studio, VS Code, ou tout IDE C# de votre choix  

Aucune configuration supplémentaire n’est requise au-delà de l’ajout du package NuGet.

---

## Comment détecter la substitution avec FontSettings

Le cœur de **comment détecter la substitution** réside dans l’événement `FontSettings.Warning`. Lorsque Aspose.Words ne trouve pas une police demandée, il déclenche un avertissement `WarningType.FontSubstitution`. En vous abonnant à cet événement, vous recevez une notification en temps réel, incluant le nom de la police d’origine et la police utilisée en remplacement.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create LoadOptions and enable a custom FontSettings instance.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};

// Step 2: Hook into the FontSettings warning event – this is where we detect substitution.
loadOptions.FontSettings.Warning += (sender, e) =>
{
    // We only care about font‑substitution warnings.
    if (e.WarningType == WarningType.FontSubstitution)
    {
        // Output the warning to the console – you could log it or collect it in a list.
        Console.WriteLine($"⚠️ Font substituted: {e.Message}");
    }
};

// Step 3: Load the document using the configured LoadOptions.
Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

**Pourquoi cela fonctionne :**
- `LoadOptions.FontSettings` indique à Aspose.Words d’utiliser l’objet `FontSettings` que vous venez de créer.
- S’abonner à `Warning` vous offre un point unique pour surveiller *tous* les problèmes liés aux polices, pas seulement les polices manquantes.
- Le filtre `WarningType.FontSubstitution` garantit que vous ne réagissez qu’au scénario exact qui vous intéresse – l’essence de **comment détecter la substitution**.

### Sortie attendue

Exécuter le code ci‑dessus avec un document qui référence une police inexistante affichera quelque chose comme :

```
⚠️ Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Si le document n’utilise que des polices installées, la console reste silencieuse – un signal clair que **comment détecter la substitution** a réussi sans fausses alertes.

---

## Gérer les polices manquantes de manière élégante

Détecter une substitution n’est que la moitié du combat ; vous avez également besoin d’une stratégie pour **gérer les polices manquantes** afin que le rendu final corresponde à vos attentes. Voici trois approches pratiques que vous pouvez combiner.

### 1. Fournir un dossier de polices de secours

Aspose.Words peut rechercher des polices dans des répertoires supplémentaires. En le pointant vers un dossier contenant les polices les plus courantes que vous attendez, vous réduisez complètement le risque de substitution.

```csharp
// Assume you have a folder "FallbackFonts" with Arial, Times New Roman, etc.
loadOptions.FontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);
```

**Pourquoi :** Lorsque la police d’origine est manquante, Aspose.Words dispose maintenant d’un ensemble connu d’alternatives, ce qui donne souvent un résultat visuel plus prévisible.

### 2. Remplacer les polices manquantes par programme

Si vous souhaitez un contrôle total, vous pouvez remplacer la police manquante par une police spécifique après détection.

```csharp
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes("Comic Sans MS", new[] { "Arial", "Helvetica" });
```

**Pourquoi :** Cela indique au moteur exactement quelles polices essayer, vous permettant d’appliquer la charte graphique de l’entreprise ou les normes d’accessibilité.

### 3. Journaliser et interrompre (lorsque la substitution est inacceptable)

Parfois, une police manquante signifie que le document est invalide pour votre cas d’utilisation (par ex., des formulaires juridiques). Dans ce scénario, vous pouvez lever une exception dès qu’une substitution se produit.

```csharp
loadOptions.FontSettings.Warning += (sender, e) =>
{
    if (e.WarningType == WarningType.FontSubstitution)
        throw new InvalidOperationException($"Critical font missing: {e.Message}");
};
```

**Pourquoi :** Un échec immédiat empêche les erreurs en aval, comme des tableaux mal alignés ou des signatures corrompues.

---

## Exemple complet fonctionnel – Toutes les étapes combinées

Ci‑dessous se trouve un programme unique, prêt à copier‑coller, qui démontre **comment détecter la substitution** *et* plusieurs façons de **gérer les polices manquantes**. N’hésitez pas à commenter les sections dont vous n’avez pas besoin.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // 1️⃣ Set up LoadOptions with a fresh FontSettings.
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // 2️⃣ OPTIONAL: Add a fallback folder with extra fonts.
        // -------------------------------------------------
        // loadOptions.FontSettings.SetFontsFolder(@"C:\FallbackFonts", true);

        // -------------------------------------------------
        // 3️⃣ OPTIONAL: Define explicit substitution rules.
        // -------------------------------------------------
        // loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
        //     "Comic Sans MS", new[] { "Arial", "Helvetica" });

        // -------------------------------------------------
        // 4️⃣ Subscribe to the warning event – the heart of how to detect substitution.
        // -------------------------------------------------
        loadOptions.FontSettings.Warning += (sender, e) =>
        {
            if (e.WarningType == WarningType.FontSubstitution)
            {
                // Log the warning – you could also collect it in a list for later analysis.
                Console.WriteLine($"⚠️ Font substituted: {e.Message}");

                // Uncomment to abort on any substitution.
                // throw new InvalidOperationException($"Missing font detected: {e.Message}");
            }
        };

        // -------------------------------------------------
        // 5️⃣ Load the document; the warning handler fires automatically.
        // -------------------------------------------------
        string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // -------------------------------------------------
        // 6️⃣ Save the result – you’ll see the substituted font in the output file.
        // -------------------------------------------------
        string outPath = @"YOUR_DIRECTORY/Processed.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**Ce à quoi s’attendre :**
- Si `MissingFont.docx` référence une police qui n’est pas présente sur la machine, la console affiche l’avertissement de substitution.
- Le fichier `Processed.docx` enregistré utilise la police de secours que vous avez configurée (ou la police par défaut de la bibliothèque).
- Aucune exception non gérée n’apparaît, sauf si vous interrompez délibérément en cas de substitution.

---

## Questions fréquentes & cas limites

| Question | Réponse |
|----------|--------|
| *Et si le document contient de nombreuses polices manquantes ?* | L’événement d’avertissement se déclenche pour **chaque** substitution, vous verrez donc plusieurs lignes. Vous pouvez les regrouper dans une liste pour un rapport récapitulatif. |
| *Cela fonctionne‑t‑il avec la conversion PDF ?* | Absolument. Les mêmes `FontSettings` sont respectés lorsque vous appelez `doc.Save("out.pdf")`. L’avertissement de substitution se déclenche toujours, vous permettant de vérifier la fidélité visuelle du PDF. |
| *Puis‑je détecter la substitution après que le document soit déjà chargé ?* | Pas directement. L’avertissement est déclenché **pendant** le chargement ou l’enregistrement. Si vous avez besoin d’une analyse post‑chargement, capturez les avertissements dans une collection pendant la phase de chargement. |
| *Qu’en est‑il des polices personnalisées intégrées dans le DOCX ?* | Les polices intégrées sont considérées comme présentes, donc aucune substitution ne se produit. Si la police intégrée est corrompue, Aspose.Words déclenche toujours un avertissement, que vous pouvez intercepter de la même manière. |
| *Y a‑t‑il un impact sur les performances ?* | Minimal. La vérification des avertissements est légère ; le vrai coût provient du chargement du document lui‑-même. Ajouter un dossier de polices peut augmenter légèrement le temps de recherche, mais seulement lors du premier chargement. |

---

## Astuces pro & pièges à éviter

- **Astuce pro :** Toujours définir `recursive: true` lorsqu’on pointe vers un dossier contenant de nombreuses polices ; sinon les sous‑dossiers sont ignorés.  
- **Attention :** Sensibilité à la casse sous Linux. Les noms de polices sont insensibles à la casse sous Windows mais pas sous Linux, donc utilisez le nom exact ou ajoutez les deux variantes.  
- **Rappel :** Si vous exécutez dans un environnement conteneurisé, assurez‑vous que le dossier de polices fait partie de l’image ou est monté au moment de l’exécution.  
- **Conseil :** Stockez les avertissements dans une `List<string>` si vous devez présenter un résumé aux utilisateurs finaux ou les consigner dans un système de surveillance.  

---

## Conclusion

Nous avons couvert **comment détecter la substitution** des polices manquantes dans Aspose.Words, vous avons montré plusieurs façons de **gérer les polices manquantes**, et fourni un exemple complet et exécutable que vous pouvez intégrer à n’importe quel projet .NET. En vous appuyant sur l’événement `FontSettings.Warning`, vous obtenez une visibilité en temps réel sur les problèmes de polices, et avec des dossiers de secours ou des règles de substitution explicites, vous maintenez votre rendu exactement comme vous le souhaitez.

Prêt pour l’étape suivante ? Essayez d’étendre la solution pour intégrer automatiquement la police de secours dans le PDF généré, ou de connecter le gestionnaire d’avertissement à un service de journalisation centralisé pour des pipelines de documents à grande échelle. Les modèles que nous avons abordés aujourd’hui—détection basée sur les événements, secours élégant et gestion explicite des erreurs—s’appliquent à de nombreuses autres API Aspose, vous êtes donc maintenant équipé pour relever les défis liés aux polices.

Vous avez d’autres questions sur la gestion des polices, la conversion PDF ou les astuces Aspose.Words ? Laissez un commentaire ci‑dessous, et bon codage !

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}