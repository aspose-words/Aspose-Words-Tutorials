---
category: general
date: 2026-04-02
description: Comment détecter les polices dans les documents C# en utilisant Aspose.Words.
  Apprenez à configurer les paramètres de police et à gérer efficacement les polices
  manquantes.
draft: false
keywords:
- how to detect fonts
- configure font settings
- handle missing fonts
- font substitution warning
- Aspose.Words font handling
language: fr
og_description: Comment détecter les polices dans les documents C# à l'aide d'Aspose.Words.
  Ce guide vous montre comment configurer les paramètres de police et gérer les polices
  manquantes.
og_title: Comment détecter les polices en C# – Guide complet
tags:
- C#
- Aspose.Words
- Document Processing
title: Comment détecter les polices dans C# – Guide complet
url: /fr/net/working-with-fonts/how-to-detect-fonts-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment détecter les polices en C# – Guide complet

Vous vous êtes déjà demandé **comment détecter les polices** manquantes ou substituées lors du chargement d’un document Word en .NET ? Vous n’êtes pas seul — les développeurs se heurtent souvent à ce problème lorsqu’un document fait référence à une police qui n’est pas installée sur le serveur. La bonne nouvelle, c’est qu’Aspose.Words vous offre une méthode propre et programmatique pour repérer ces lacunes.

Dans ce tutoriel, nous passerons en revue un exemple pratique qui montre non seulement **comment détecter les polices**, mais aussi comment **configurer les paramètres de police** et **gérer les polices manquantes** de façon élégante. À la fin, vous disposerez d’un extrait prêt à l’emploi qui affiche chaque avertissement de substitution de police, afin que vous puissiez le consigner, alerter ou remplacer les polices selon vos besoins.

---

## Ce dont vous avez besoin

- **Aspose.Words for .NET** (la dernière version est recommandée ; le code ci‑dessous cible .NET 6+)
- Un environnement de développement .NET (Visual Studio, Rider ou VS Code)
- Un fichier `.docx` d’exemple qui fait référence à une police que vous n’avez pas installée (idéal pour les tests)

Aucun package NuGet supplémentaire n’est requis au‑delà d’Aspose.Words, et la solution fonctionne sous Windows, Linux et macOS.

---

## Étape 1 : Installer et référencer Aspose.Words

Tout d’abord, ajoutez la bibliothèque à votre projet. La commande NuGet est simple :

```bash
dotnet add package Aspose.Words
```

> **Astuce :** Si vous travaillez sur un serveur d’intégration continue, épinglez la version du package pour éviter des changements inattendus.

---

## Étape 2 : Configurer les paramètres de police (et préparer les options de chargement)

Avant d’ouvrir un document, vous pouvez indiquer à Aspose.Words où chercher les polices de secours. C’est la partie **configurer les paramètres de police** qui empêche le moteur de remplacer silencieusement des polices que vous ne souhaitez pas.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 2: Create a FontSettings object and point it to a folder with fallback fonts
var fontSettings = new FontSettings();

// Example: add a custom folder that contains common Windows fonts
fontSettings.SetFontsFolder(@"C:\Windows\Fonts", recursive: true);

// You can also embed a default font to use when nothing matches
fontSettings.SubstitutionSettings.DefaultFontName = "Arial";

// Wrap the settings into LoadOptions so Aspose.Words uses them when loading
var loadOptions = new LoadOptions { FontSettings = fontSettings };
```

Pourquoi faire cela ? Si le document référence *Comic Sans* mais que votre serveur ne possède que *Calibri*, Aspose.Words substituera *Calibri* et générera un avertissement. En configurant le chemin de recherche, vous réduisez les surprises indésirables.

---

## Étape 3 : Charger le document avec les options préparées

Nous ouvrons maintenant le fichier. Les `LoadOptions` créées à l’étape précédente sont passées directement au constructeur `Document`.

```csharp
// Step 3: Load the Word file using the configured FontSettings
var docPath = @"C:\Docs\input.docx";
var document = new Document(docPath, loadOptions);
```

Si le fichier est introuvable ou corrompu, une exception est levée — il est donc conseillé d’envelopper cet appel dans un try/catch en production.

---

## Étape 4 : Parcourir les avertissements du document pour les substitutions de police

Aspose.Words collecte une liste d’avertissements pendant l’analyse. Parmi eux, `FontSubstitutionWarning` indique exactement quelle police a été remplacée.

```csharp
// Step 4: Iterate over warnings and look for FontSubstitutionWarning instances
foreach (WarningInfo warning in document.Warnings)
{
    if (warning is FontSubstitutionWarning fontWarning)
    {
        Console.WriteLine(
            $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
    }
}
```

La collection `Warnings` peut également contenir d’autres éléments (par ex., `DocumentStructureWarning`). Filtrer sur `FontSubstitutionWarning` garantit que nous ne signalons que le scénario **gérer les polices manquantes** qui nous intéresse.

---

## Étape 5 : Assembler le tout – Exemple complet et exécutable

Voici le programme complet. Copiez‑collez‑le dans une nouvelle application console et exécutez‑le ; chaque police manquante sera affichée dans la console.

```csharp
// Full example: Detect font substitutions in a Word document
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare font settings (configure font settings)
        var fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\Windows\Fonts", recursive: true);
        fontSettings.SubstitutionSettings.DefaultFontName = "Arial";

        // 2️⃣ Build load options with those settings
        var loadOptions = new LoadOptions { FontSettings = fontSettings };

        // 3️⃣ Load the document (handle missing fonts gracefully)
        var docPath = @"C:\Docs\input.docx";
        Document document;
        try
        {
            document = new Document(docPath, loadOptions);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
            return;
        }

        // 4️⃣ Scan warnings for font substitution events
        bool anySubstitutions = false;
        foreach (WarningInfo warning in document.Warnings)
        {
            if (warning is FontSubstitutionWarning fontWarning)
            {
                anySubstitutions = true;
                Console.WriteLine(
                    $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
            }
        }

        // 5️⃣ Inform the user if everything was fine
        if (!anySubstitutions)
        {
            Console.WriteLine("No font substitutions detected – all fonts were found.");
        }
    }
}
```

**Sortie attendue** (exemple) :

```
Font 'Times New Roman' was substituted with 'Arial'.
Font 'Comic Sans MS' was substituted with 'Arial'.
```

Si le document n’utilise que des polices présentes sur la machine, vous verrez la ligne « No font substitutions detected » à la place.

---

## Cas limites et questions fréquentes

### Et si le document ne contient **aucun avertissement** ?

Cela signifie simplement que chaque police référencée a été trouvée dans les dossiers de recherche que vous avez configurés. Le drapeau `anySubstitutions` de l’exemple couvre ce cas.

### Puis‑je **consigner** les avertissements dans un fichier au lieu de la console ?

Absolument. Remplacez les appels `Console.WriteLine` par le logger de votre choix (Serilog, NLog, etc.). L’objet `WarningInfo` expose également `WarningType` et `WarningMessage` si vous avez besoin de plus de détails.

### Comment **ignorer** certaines polices, par exemple une police de marque d’entreprise qui ne doit jamais être remplacée ?

Vous pouvez ajouter une règle de substitution personnalisée :

```csharp
fontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes("MyBrandFont", new[] { "Arial", "Helvetica" });
```

Désormais, Aspose.Words ne remplacera que *MyBrandFont* par les alternatives listées, et vous continuerez à recevoir un avertissement que vous pourrez traiter.

### Cela fonctionne‑t‑il dans des conteneurs **Linux** ?

Oui—assurez‑vous simplement de monter un dossier contenant les fichiers `.ttf`/`.otf` requis et de pointer `SetFontsFolder` vers ce répertoire. Aspose.Words ne dépend pas des polices installées par le système d’exploitation.

---

## Vue d’ensemble visuelle

![diagramme de détection des polices](detect-fonts.png "Diagramme montrant les étapes de détection des polices dans un document")

*Texte alternatif de l’image :* **diagramme de détection des polices** illustrant la configuration, le chargement et l’inspection des avertissements.

---

## Récapitulatif – Ce que nous avons appris

- **Comment détecter les polices** manquantes ou substituées à l’aide des avertissements d’Aspose.Words.  
- Comment **configurer les paramètres de police** pour pointer vers des dossiers de polices personnalisés et définir une police de secours par défaut.  
- Stratégies pour **gérer les polices manquantes**, de la consignation aux règles de substitution personnalisées.

Tout cela tient dans une petite application console autonome que vous pouvez intégrer à n’importe quelle solution .NET.

---

## Prochaines étapes et sujets associés

- **Incorporer les polices** directement dans le document de sortie pour éviter les futures substitutions (`SaveOptions` avec `EmbedFullFonts`).  
- **Remplacement programmatique de polices** — remplacer les polices manquantes par une alternative spécifique avant l’enregistrement.  
- **Optimisation des performances** — mettre en cache `FontSettings` lors du traitement de nombreux documents en lot.  

Si ces sujets vous intéressent, recherchez *configure font settings* et *handle missing fonts* — ils vous mèneront à des approfondissements sur la gestion des polices avec Aspose.Words.

---

Bon codage ! Vous avez un cas particulier de police ? Laissez un commentaire, et nous résoudrons le problème ensemble.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}