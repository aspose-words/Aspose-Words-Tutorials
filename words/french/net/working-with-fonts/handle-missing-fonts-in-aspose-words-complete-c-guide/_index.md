---
category: general
date: 2026-03-14
description: Gérez rapidement les polices manquantes avec Aspose.Words. Apprenez comment
  capturer les avertissements de substitution de police, configurer LoadOptions et
  éviter les problèmes de rendu.
draft: false
keywords:
- handle missing fonts
- Aspose.Words
- font substitution
- LoadOptions
- DocumentWarnings
- C# document loading
language: fr
og_description: Gérez les polices manquantes dans Aspose.Words à l'aide d'un collecteur
  d'avertissements. Ce tutoriel montre étape par étape comment détecter et consigner
  les substitutions de polices.
og_title: Gérer les polices manquantes dans Aspose.Words – Guide complet C#
tags:
- Aspose
- C#
- Fonts
- DocumentProcessing
title: Gérer les polices manquantes dans Aspose.Words – Guide complet C#
url: /fr/net/working-with-fonts/handle-missing-fonts-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Gérer les polices manquantes dans Aspose.Words – Guide complet C#

Vous avez déjà eu besoin de **gérer les polices manquantes** lors du chargement d'un document Word et vous vous êtes demandé pourquoi votre sortie PDF ou image était déformée ? Vous n'êtes pas le seul. Les fichiers de polices manquants sont un troubleur silencieux qui peut transformer un rapport parfaitement conçu en un désordre illisible.  

Bonne nouvelle ? Aspose.Words vous offre un moyen simple de capturer ces événements de substitution de police, de les consigner, et même de remplacer par une police de secours si vous le souhaitez. Dans ce tutoriel, nous parcourrons un exemple complet, prêt à l'exécution, qui montre exactement comment configurer un collecteur d'avertissements, le brancher à `LoadOptions`, et charger un document pouvant contenir des polices manquantes.

À la fin de ce guide, vous serez capable de :

* Détecter chaque substitution de police qui se produit lors du chargement du document.  
* Afficher un message convivial dans la console (ou le diriger vers un logger) pour chaque police manquante.  
* Étendre la solution pour remplacer les polices, si nécessaire.  

**Prérequis** – vous aurez besoin de :

* .NET 6.0 ou ultérieur (le code fonctionne également avec .NET Core et .NET Framework).  
* Le package NuGet Aspose.Words pour .NET (version actuelle 23.11).  
* Un fichier Word qui référence délibérément une police que vous n'avez pas installée – nous l'appellerons `doc-with-missing-font.docx`.  

Si vous êtes déjà à l'aise avec C# et avez un projet configuré, vous pouvez passer directement au code. Sinon, continuez à lire ; nous couvrirons d'abord les petites étapes de configuration.

---

## Pourquoi la gestion des polices manquantes est importante

Lorsque Aspose.Words charge un document, il tente d'associer chaque glyphe à une police installée sur la machine. S'il ne trouve pas la police exacte, il substitue silencieusement la police la plus proche. Cette substitution peut modifier la hauteur des lignes, le crénage, et même faire disparaître des caractères. En capturant l'événement `WarningType.FontSubstitution`, vous obtenez une vue transparente de **ce qui** a été remplacé et **pourquoi**, ce qui est essentiel pour :

* Maintenir la cohérence de la marque (votre police d'entreprise doit apparaître exactement comme conçue).  
* Déboguer les problèmes de conversion PDF — souvent le coupable est une police manquante.  
* Construire des pipelines de documents automatisés où vous devez signaler les fichiers problématiques pour une révision manuelle.  

Maintenant que le « pourquoi » est clair, plongeons dans le **comment**.

## Étape 1 – Configurer le collecteur d'avertissements

Ce dont nous avons besoin en premier est un objet capable d'écouter les avertissements d'Aspose.Words. `DocumentWarnings` implémente `IWarningCallback`, nous permettant de réagir chaque fois que la bibliothèque émet un avertissement.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Create a collector that will receive warning events.
DocumentWarnings fontWarnings = new DocumentWarnings();

// Subscribe to the Warning event.
fontWarnings.Warning += (sender, e) =>
{
    // We only care about font substitution warnings.
    if (e.WarningType == WarningType.FontSubstitution)
    {
        // Log the original font name that was missing.
        Console.WriteLine($"Font '{e.WarningInfo}' was substituted.");
    }
};
```

**Ce qui se passe ?**  
* `DocumentWarnings` est un léger wrapper autour de l'interface de rappel.  
* Le lambda vérifie `e.WarningType` afin d'ignorer les avertissements non pertinents (comme les fonctionnalités obsolètes).  
* `e.WarningInfo` contient le nom de la police manquante, que nous affichons dans la console.  

*Astuce pro* : Remplacez `Console.WriteLine` par un logger structuré (Serilog, NLog) en production — ainsi vous obtenez des horodatages et des niveaux de log gratuitement.

## Étape 2 – Brancher le collecteur à LoadOptions

`LoadOptions` est le gardien de chaque document que vous ouvrez avec Aspose.Words. En assignant notre instance `fontWarnings` à sa propriété `WarningCallback`, nous nous assurons que le collecteur est actif pendant le processus de chargement.

```csharp
// Configure load options to use our warning callback.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = fontWarnings
};
```

**Pourquoi utiliser LoadOptions ?**  
En plus des avertissements, `LoadOptions` vous permet de gérer les mots de passe, l'encodage, et même le chargement de ressources personnalisées. Ici nous nous concentrons sur les avertissements, mais le même schéma fonctionne pour d'autres rappels.

## Étape 3 – Charger le document avec les options configurées

Nous chargeons enfin le document en mémoire. Si une police est manquante, notre collecteur se déclenchera et vous verrez une ligne dans la console pour chaque substitution.

```csharp
// Path to the document that may reference missing fonts.
string docPath = Path.Combine(
    Environment.CurrentDirectory,
    "doc-with-missing-font.docx");

// Load the document using the previously configured LoadOptions.
Document document = new Document(docPath, loadOptions);
```

Si vous exécutez cet extrait avec un document qui référence, par exemple, *Calibri Light* alors que votre machine de test ne possède que *Calibri*, vous obtiendrez une sortie similaire à :

```
Font 'Calibri Light' was substituted.
```

C’est toute la boucle de détection — simple, mais puissante.

## Étape 4 – (Optionnel) Remplacer les polices manquantes par un substitut connu

Parfois, vous ne voulez pas seulement consigner le problème ; vous souhaitez imposer une police de secours afin que le rendu soit cohérent. Aspose.Words vous permet de fournir un objet `FontSettings` personnalisé qui associe les polices manquantes à un remplacement.

```csharp
// Create FontSettings and map any missing font to Arial.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
    "*", // wildcard – applies to any missing font
    new[] { "Arial" } // fallback font(s)
);

// Apply the FontSettings to the document.
document.FontSettings = fontSettings;

// Now re-save the document; all missing fonts will render as Arial.
document.Save("output-with-fallback.pdf");
Console.WriteLine("Document saved with fallback font applied.");
```

**Explication**  
* Le caractère générique `"*"` indique à Aspose.Words de traiter *toute* police manquante de la même manière.  
* Vous pouvez également mapper des polices spécifiques individuellement si vous avez besoin d'un contrôle fin.  
* Après avoir défini `document.FontSettings`, tout rendu ultérieur (PDF, image, HTML) respecte la substitution.

## Exemple complet fonctionnel

Voici le programme complet que vous pouvez copier‑coller dans une application console. Il inclut toutes les instructions `using` requises, la gestion des erreurs, et des commentaires pour plus de clarté.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        try
        {
            // -------------------------------------------------
            // Step 1: Create a warnings collector.
            // -------------------------------------------------
            DocumentWarnings fontWarnings = new DocumentWarnings();
            fontWarnings.Warning += (sender, e) =>
            {
                if (e.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font '{e.WarningInfo}' was substituted.");
                }
            };

            // -------------------------------------------------
            // Step 2: Attach the collector to LoadOptions.
            // -------------------------------------------------
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = fontWarnings
            };

            // -------------------------------------------------
            // Step 3: Load the document (may contain missing fonts).
            // -------------------------------------------------
            string docPath = Path.Combine(
                Environment.CurrentDirectory,
                "doc-with-missing-font.docx");

            Document doc = new Document(docPath, loadOptions);

            // -------------------------------------------------
            // Step 4 (optional): Apply a fallback font.
            // -------------------------------------------------
            FontSettings fontSettings = new FontSettings();
            fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
                "*", new[] { "Arial" });

            doc.FontSettings = fontSettings;

            // Save the result to verify the substitution.
            string outPath = Path.Combine(
                Environment.CurrentDirectory,
                "output-with-fallback.pdf");

            doc.Save(outPath);
            Console.WriteLine($"Document saved to '{outPath}'.");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"Error: {ex.Message}");
        }
    }
}
```

**Sortie attendue** (lorsqu'une police manquante est détectée) :

```
Font 'Times New Roman PS' was substituted.
Document saved to 'C:\MyProject\output-with-fallback.pdf'.
```

Si le document source contient déjà toutes les polices requises, la ligne d'avertissement n'apparaîtra tout simplement pas — rien à craindre.

## Questions fréquentes & cas particuliers

| Question | Réponse |
|----------|--------|
| **Et si je veux seulement consigner, pas remplacer les polices ?** | Ignorez complètement le bloc `FontSettings` ; le collecteur d'avertissements seul suffit. |
| **Puis-je rediriger les avertissements vers un fichier ?** | Oui — remplacez `Console.WriteLine` par `File.AppendAllText("font-warnings.log", …)`. |
| **Cela fonctionne-t-il pour DOC, DOCX et ODT ?** | Absolument. `LoadOptions` s'applique à tous les formats pris en charge par Aspose.Words. |
| **Qu'en est-il des polices personnalisées incorporées dans le document ?** | Les polices incorporées contournent le mécanisme de substitution ; elles sont utilisées telles quelles. |
| **Y a-t-il un impact sur les performances ?** | Le surcoût est minime — un seul rappel par police manquante. Pour de gros lots, envisagez d'agréger les avertissements au lieu d'écrire à chaque événement. |

## Conclusion

Nous avons montré **comment gérer les polices manquantes** dans Aspose.Words en branchant un collecteur `DocumentWarnings` à `LoadOptions`, en remplaçant éventuellement par une police de secours, et en enregistrant le résultat. Ce modèle vous offre une visibilité complète sur les événements de substitution de police, vous aidant à maintenir la fidélité visuelle lors des conversions PDF, image ou HTML.

Prochaines étapes que vous pourriez explorer :

* Intégrer le collecteur d'avertissements à un framework de journalisation centralisé.  
* Créer un tableau de bord UI qui répertorie les documents avec des polices manquantes pour un traitement par lots.  
* Combiner cette approche avec Aspose.PDF pour vérifier que les PDF générés utilisent réellement la police de secours.  

N'hésitez pas à expérimenter — remplacez `"Arial"` par `"Tahoma"` ou chargez un autre jeu de documents. L'idée principale reste la même : capturer l'avertissement, agir en conséquence, et garder vos documents exactement comme prévu.

Bon codage ! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}