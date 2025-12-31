---
category: general
date: 2025-12-31
description: Capturez les avertissements de police dans Aspose.Words pour détecter
  les polices manquantes et répertoriez les polices manquantes dans votre application
  .NET. Découvrez une solution C# étape par étape.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- list missing fonts
- Aspose.Words font warnings
- C# document loading
language: fr
og_description: Capturez les avertissements de police dans Aspose.Words pour détecter
  les polices manquantes et les répertorier. Guide complet C# avec code et astuces.
og_title: Capture des avertissements de police – détecter et lister les polices manquantes
tags:
- Aspose.Words
- C#
- .NET
- Font Substitution
title: Capturer les avertissements de police – Détecter et répertorier les polices
  manquantes
url: /fr/net/working-with-fonts/capture-font-warnings-detect-list-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Capturer les avertissements de police – Détecter & lister les polices manquantes

Vous avez déjà eu besoin de **capturer les avertissements de police** lors du chargement d’un document Word sans savoir comment exposer les détails des polices manquantes ? Vous n’êtes pas seul. Dans de nombreux projets réels, les polices manquantes provoquent des défauts de mise en page, et sans avertissements appropriés vous finissez par courir après des bugs fantômes.  

Dans ce tutoriel, nous allons vous montrer comment **détecter les polices manquantes** et **lister les polices manquantes** avec Aspose.Words for .NET. À la fin, vous disposerez d’un extrait C# prêt à l’emploi qui affiche chaque avertissement de substitution, afin que vous puissiez le consigner, le signaler ou même remplacer les polices automatiquement.

---

## Pourquoi capturer les avertissements de police est important

Lorsque Aspose.Words ouvre un DOCX qui référence une police non installée sur le serveur, il effectue silencieusement une substitution de secours. Le document semble correct, mais la fidélité visuelle est compromise — imaginez le logo d’une marque d’entreprise rendu avec une mauvaise typographie.  

Capturer ces avertissements vous permet de :

* **Maintenir la cohérence de la marque** – vous savez exactement quelles polices sont manquantes.  
* **Automatiser la remédiation** – remplacer les polices manquantes par programme.  
* **Auditer la conformité** – générer des rapports pour les revues juridiques ou de design.  

En bref, **capturer les avertissements de police** constitue la première ligne de défense contre la substitution silencieuse de polices.

---

## Configurer LoadOptions pour détecter les polices manquantes

Le point clé pour exposer les avertissements est la propriété `LoadOptions.FontSubstitutionWarning`. Par défaut, elle est réglée sur `None`, ce qui signifie qu’Aspose.Words absorbe les messages. La passer à `All` indique à la bibliothèque d’enregistrer chaque événement de substitution.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Configure LoadOptions so every font‑substitution warning is stored
LoadOptions loadOptions = new LoadOptions
{
    // Provide a fresh FontSettings instance – you can also pre‑load custom fonts here
    FontSettings = new FontSettings(),

    // This flag tells Aspose.Words to capture *all* font‑related warnings
    FontSubstitutionWarning = FontSubstitutionWarning.All
};
```

> **Astuce :** Si vous avez déjà un dossier de polices personnalisé, affectez‑le à `FontSettings.SetFontsFolder("path")` avant de charger le document. Ainsi vous pourrez **détecter les polices manquantes** qui ne se trouvent pas dans le répertoire système.

---

## Charger le document et lister les polices manquantes

Une fois les `LoadOptions` configurées, l’étape suivante consiste à charger le fichier Word. Le constructeur accepte l’objet d’options, et toute substitution sera enregistrée dans la `WarningInfoCollection` du document.

```csharp
// Path to the DOCX that may contain unknown fonts
string docPath = @"C:\Docs\UnknownFonts.docx";

// Load the document with the warning‑capture options
Document document = new Document(docPath, loadOptions);
```

Si le fichier référence des polices qui ne sont pas disponibles, chaque police manquante génère une entrée `WarningInfo`. Vous pouvez **lister les polices manquantes** en parcourant cette collection.

```csharp
// Iterate through the warnings and output them to the console
foreach (WarningInfo warning in document.WarningInfoCollection)
{
    // The warning.Type will be FontSubstitution, and Description contains details
    Console.WriteLine($"{warning.Type}: {warning.Description}");
}
```

Un résultat typique ressemble à :

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

Chaque ligne indique exactement quelle police était manquante, satisfaisant ainsi le besoin de **lister les polices manquantes**.

---

## Lire et interpréter la WarningInfoCollection

La `WarningInfoCollection` peut contenir différents types d’avertissements (par ex., `DocumentStructure`, `ImageLoading`). Pour se concentrer uniquement sur les problèmes de police, filtrez par `WarningType.FontSubstitution`.

```csharp
var fontWarnings = document.WarningInfoCollection
                           .Where(w => w.Type == WarningType.FontSubstitution);

foreach (var fw in fontWarnings)
{
    Console.WriteLine($"Missing font detected: {fw.Description}");
}
```

Pourquoi filtrer ? Parce qu’un gros document peut également générer des avertissements concernant des images corrompues ou des fonctionnalités non prises en charge. En affinant la collection, vous évitez le bruit et gardez la sortie **capturer les avertissements de police** claire.

---

## Exemple complet – Capturer les avertissements de police en action

Voici le programme complet, autonome, que vous pouvez intégrer à n’importe quel projet console .NET. Il montre chaque étape, de la configuration de `LoadOptions` à l’impression d’une liste propre des polices manquantes.

```csharp
// ------------------------------------------------------------
// Complete C# example: Capture Font Warnings, Detect & List Missing Fonts
// ------------------------------------------------------------
using System;
using System.Linq;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare LoadOptions to capture all font‑substitution warnings
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings(),
            FontSubstitutionWarning = FontSubstitutionWarning.All
        };

        // OPTIONAL: If you have a custom font folder, point Aspose.Words to it
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyFonts", true);

        // 2️⃣ Load the document with the configured options
        string docPath = @"C:\Docs\UnknownFonts.docx";
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Filter only font‑substitution warnings
        var fontWarnings = doc.WarningInfoCollection
                               .Where(w => w.Type == WarningType.FontSubstitution);

        // 4️⃣ Output the missing‑font details
        Console.WriteLine("=== Missing Font Report ===");
        foreach (var warning in fontWarnings)
        {
            Console.WriteLine(warning.Description);
        }

        // 5️⃣ If no warnings were found, let the user know
        if (!fontWarnings.Any())
            Console.WriteLine("All referenced fonts are available – no warnings captured.");
    }
}
```

**Sortie console attendue**

```
=== Missing Font Report ===
Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

Si le document ne contient aucune police manquante, vous verrez :

```
All referenced fonts are available – no warnings captured.
```

---

## Cas limites courants & comment les gérer

| Situation | Pourquoi cela se produit | Solution recommandée |
|-----------|--------------------------|----------------------|
| **Le document utilise une police OpenType intégrée** | Aspose.Words peut lire les polices intégrées, mais uniquement si le fichier n’est pas corrompu. | Vérifiez le DOCX dans Word d’abord ; ré‑intégrez la police si nécessaire. |
| **Grand nombre d’avertissements** (ex., 200 + polices manquantes) | Les importations massives depuis des systèmes hérités référencent souvent une large palette de polices. | Traitez les avertissements par lots : stockez‑les dans une base de données, puis exécutez un script d’installation de polices. |
| **WarningInfoCollection est vide** | Soit le document possède toutes les polices, soit `FontSubstitutionWarning` est resté sur `None`. | Revérifiez la configuration de vos `LoadOptions` et assurez‑vous de charger le bon chemin de fichier. |
| **Polices personnalisées situées sur un partage réseau** | La latence réseau peut provoquer des dépassements de délai lors de la recherche de police. | Pré‑chargez les polices dans `FontSettings` avec `SetFontsFolder` et activez `CacheFontData = true`. |

Ces conseils vous aident à **détecter les polices manquantes** de façon fiable, même dans des environnements complexes.

---

## Illustration

![exemple de capture d'avertissements de police](https://example.com/images/capture-font-warnings.png "exemple de capture d'avertissements de police")

*La capture d’écran montre une exécution console où deux polices manquantes sont signalées.*

---

## Prochaines étapes – Aller au-delà du simple reporting

Maintenant que vous pouvez **capturer les avertissements de police**, envisagez d’automatiser la remédiation :

1. **Substitution automatique de police** – Remplacez les polices manquantes par une alternative approuvée par l’entreprise en modifiant `FontSettings.SubstitutionSettings`.  
2. **Journalisation vers un système de monitoring** – Redirigez les messages d’avertissement vers Serilog, ELK ou Azure Application Insights.  
3. **Rapports destinés aux utilisateurs** – Générez un résumé HTML ou PDF pour que les designers puissent examiner quelles polices doivent être installées.

Toutes ces extensions s’appuient sur la même base que nous avons couverte : configurer `LoadOptions`, charger le document et lire `WarningInfoCollection`.

---

## Conclusion

Vous venez d’apprendre comment **capturer les avertissements de police** avec Aspose.Words, **détecter les polices manquantes** et **lister les polices manquantes** avec une sortie console claire. L’approche est simple, ne nécessite que quelques lignes de C# et fonctionne avec n’importe quelle version .NET supportant Aspose.Words 23.x ou ultérieure.  

Essayez-le sur un DOCX d’exemple qui référence une police que vous avez délibérément désinstallée — vous verrez les avertissements apparaître immédiatement. Vous pourrez alors décider d’installer les caractères manquants, de les substituer par programme, ou simplement de consigner le problème pour une révision ultérieure.

Bon codage, et que vos documents s’affichent toujours avec les bonnes polices !

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}