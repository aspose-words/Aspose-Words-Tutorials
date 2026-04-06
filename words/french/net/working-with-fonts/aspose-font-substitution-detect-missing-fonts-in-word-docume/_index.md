---
category: general
date: 2026-04-05
description: Guide de substitution de polices Aspose pour détecter les polices manquantes
  lors du chargement d’un document Word. Apprenez à configurer les paramètres de police
  et à gérer efficacement les polices manquantes.
draft: false
keywords:
- aspose font substitution
- detect missing fonts
- load word document
- configure font settings
- handle missing fonts
language: fr
og_description: Guide de substitution de polices Aspose pour détecter les polices
  manquantes lors du chargement d’un document Word. Apprenez à configurer les paramètres
  de police et à gérer les polices manquantes efficacement.
og_title: Substitution de polices Aspose – Détecter les polices manquantes dans les
  documents Word
tags:
- Aspose.Words
- C#
- Font Management
title: Substitution de polices Aspose – Détecter les polices manquantes dans les documents
  Word
url: /fr/net/working-with-fonts/aspose-font-substitution-detect-missing-fonts-in-word-docume/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Substitution de polices Aspose – Détecter les polices manquantes dans les documents Word

Vous êtes déjà tombé sur un fichier Word qui semble parfait sur une machine mais qui présente d’étranges changements de police sur une autre ? C’est le problème classique de **aspose font substitution**, qui signifie généralement que certaines polices sont absentes sur le système cible. Dans ce tutoriel, nous vous montrerons, étape par étape, comment **détecter les polices manquantes** lors du **chargement d’un document Word**, comment **configurer les paramètres de police**, et quoi faire pour **gérer les polices manquantes** de manière élégante.

Nous parcourrons un exemple complet et exécutable en C#, expliquerons pourquoi chaque ligne est importante, et vous montrerons même la sortie console attendue. À la fin, vous pourrez repérer les substitutions de police dès le chargement d’un document—sans aucune supposition.

## Ce que vous apprendrez

- Comment activer le collecteur de diagnostic d’Aspose.Words pour les avertissements de police.  
- Le code exact nécessaire pour **charger un document Word** avec des **paramètres de police** personnalisés.  
- Comment parcourir les objets `WarningInfo` pour lister chaque police substituée.  
- Conseils pour supprimer les avertissements indésirables ou fournir des polices de secours.  
- Un exemple prêt à l’emploi que vous pouvez copier‑coller dans Visual Studio.

### Prérequis

- .NET 6.0 ou version ultérieure (l’API fonctionne de la même façon sur .NET Framework).  
- Aspose.Words pour .NET (package NuGet `Aspose.Words`).  
- Un fichier Word qui référence une police que vous n’avez pas installée (par ex., `MissingFont.docx`).  

Si vous avez tout cela, plongeons‑y.

## Étape 1 – Activer le collecteur de diagnostic (Configurer les paramètres de police)

Première chose à faire : Aspose.Words n’enregistre les avertissements de substitution de police que si vous le lui indiquez. Cela se fait en créant un objet `FontSettings` et en l’assignant à une instance `LoadOptions`. Considérez cela comme l’allumage des « voyants de débogage » pour la gestion des polices.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Prepare load options with a fresh FontSettings instance.
LoadOptions loadOptions = new LoadOptions
{
    // The FontSettings object is the hub for all font‑related configuration.
    FontSettings = new FontSettings()
};
```

**Pourquoi ?**  
Sans objet `FontSettings`, le collecteur d’avertissements reste silencieux et vous ne saurez jamais quelles polices ont été remplacées. En l’initialisant vide, nous laissons Aspose utiliser les polices système par défaut *et* suivre toutes les substitutions.

> **Astuce :** Si vous savez qu’un dossier spécifique contient les polices de l’entreprise, indiquez‑le à `FontSettings` avec `SetFontsFolder("path")`. Cela peut réduire le nombre d’avertissements de polices manquantes.

## Étape 2 – Charger le document avec les options configurées (Charger le document Word)

Maintenant que le collecteur est actif, chargez votre fichier `.docx` en utilisant les mêmes `LoadOptions`. C’est le moment où Aspose analyse le document, recherche chaque référence de police, et décide si une substitution est nécessaire.

```csharp
// Step 2: Load the Word file while applying the previously defined load options.
Document document = new Document(@"C:\Docs\MissingFont.docx", loadOptions);
```

**Pourquoi est‑ce important ?**  
Si vous appelez simplement `new Document("MissingFont.docx")`, les paramètres par défaut s’appliqueraient *et* la liste des avertissements resterait vide. Passer `loadOptions` garantit que le collecteur de diagnostic est intégré au processus de chargement.

## Étape 3 – Récupérer et afficher les avertissements de substitution de police (Détecter les polices manquantes)

Après que le document soit en mémoire, Aspose stocke les avertissements dans `document.WarningCallback.Warnings`. Parcourez cette collection, filtrez sur `WarningType.FontSubstitution`, et affichez la description. Chaque description indique quelle police était manquante et laquelle a été utilisée à la place.

```csharp
// Step 3: Examine the warning list for any font substitution entries.
foreach (WarningInfo warningInfo in document.WarningCallback.Warnings)
{
    if (warningInfo.Type == WarningType.FontSubstitution)
    {
        // The Description contains a human‑readable message, e.g.,
        // "Font 'Comic Sans MS' was not found. Substituted with 'Arial'."
        Console.WriteLine($"Substituted font: {warningInfo.Description}");
    }
}
```

**Sortie console attendue**

```
Substituted font: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
Substituted font: Font 'Times New Roman' was not found. Substituted with 'Calibri'.
```

Cette sortie indique exactement quelles polices sont manquantes sur la machine exécutant le code. Vous pouvez maintenant décider d’installer les polices manquantes, de les incorporer dans le document, ou de conserver la substitution.

![Sortie console affichant les avertissements de substitution de police aspose](/images/aspose-font-substitution-console.png)

*Texte alternatif de l’image :* substitution de police aspose – sortie console listant les polices substituées

## Étape 4 – Optionnel : Personnaliser le comportement de substitution (Gérer les polices manquantes)

Parfois, vous ne voulez pas seulement savoir *qu*’une substitution a eu lieu—vous voulez contrôler *comment* elle se produit. Aspose.Words vous permet d’enregistrer une règle personnalisée `IFontSubstitutionRule`. Voici un exemple rapide qui force toute police manquante à revenir à `Tahoma`.

```csharp
// Optional Step 4 – Define a custom substitution rule.
class TahomaFallbackRule : IFontSubstitutionRule
{
    public FontInfo Substitute(FontInfo fontInfo, FontSubstitutionInfo substitutionInfo)
    {
        // Always return Tahoma regardless of the missing font.
        return new FontInfo("Tahoma");
    }
}

// Apply the rule to the FontSettings we created earlier.
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRules.Add(new TahomaFallbackRule());
```

**Dans quel cas utiliseriez‑vous cela ?**  
Si vous générez des PDF pour un service web et que vous savez que chaque client peut rendre `Tahoma`, forcer le repli garantit une cohérence visuelle sans avoir à distribuer des dizaines de fichiers de polices.

## Exemple complet fonctionnel (Toutes les étapes combinées)

Voici le programme complet que vous pouvez coller dans un nouveau projet console. Il se compile tel quel, en supposant que vous avez installé le package NuGet Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1 – Enable diagnostic collector (configure font settings)
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // Optional: Force all missing fonts to Tahoma
        // -------------------------------------------------
        loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRules.Add(
            new TahomaFallbackRule());

        // -------------------------------------------------
        // Step 2 – Load the document (load word document)
        // -------------------------------------------------
        Document doc = new Document(@"C:\Docs\MissingFont.docx", loadOptions);

        // -------------------------------------------------
        // Step 3 – List any font substitutions (detect missing fonts)
        // -------------------------------------------------
        foreach (WarningInfo warning in doc.WarningCallback.Warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
                Console.WriteLine($"Substituted font: {warning.Description}");
        }
    }
}

// -------------------------------------------------
// Optional custom rule class (handle missing fonts)
// -------------------------------------------------
class TahomaFallbackRule : IFontSubstitutionRule
{
    public FontInfo Substitute(FontInfo fontInfo, FontSubstitutionInfo substitutionInfo)
    {
        return new FontInfo("Tahoma");
    }
}
```

Exécutez le programme, observez la console, et vous verrez chaque événement de police manquante affiché. À partir de là, vous pouvez décider d’installer les polices manquantes, de les incorporer, ou de conserver le repli.

## Questions fréquemment posées

**Q : Cette méthode fonctionne‑t‑elle avec la conversion PDF ?**  
Oui. Lorsque vous appelez plus tard `doc.Save("output.pdf")`, les polices qui ont été substituées lors du chargement seront celles incorporées dans le PDF. Ainsi, intercepter les avertissements tôt vous aide à éviter des changements de police inattendus dans le PDF final.

**Q : Et si j’ai de nombreux documents à traiter ?**  
Enveloppez la logique de chargement dans un bloc try‑catch et réutilisez une seule instance `FontSettings` pour tous les documents. Cela réduit la surcharge et maintient le collecteur d’avertissements actif pour chaque fichier.

**Q : Puis‑je supprimer complètement les avertissements ?**  
Vous pouvez définir `loadOptions.WarningCallback = null;` avant le chargement, mais vous perdrez la capacité de **détecter les polices manquantes**—ce qui n’est généralement pas souhaitable.

## Conclusion

Nous avons couvert tout ce dont vous avez besoin pour maîtriser **aspose font substitution** : activer le collecteur de diagnostic, charger un fichier Word avec des **paramètres de police** personnalisés, extraire la liste des polices manquantes, et même remplacer la règle de substitution par défaut pour **gérer les polices manquantes** à votre façon. Avec seulement quelques lignes de C#, vous obtenez une visibilité complète sur les problèmes de police qui autrement seraient cachés derrière des changements de mise en page subtils.

Prochaines étapes ? Essayez d’incorporer les polices originales dans le document avec `FontSettings.SetFontsFolder` ou explorez `FontSourceBase` pour charger des polices depuis une base de données. Vous pouvez également expérimenter avec la collection `Document.BuiltInStyle` pour voir comment les changements de police au niveau du style se propagent.

Vous avez d’autres questions sur Aspose.Words ou la gestion des polices ? Laissez un commentaire, explorez la documentation officielle d’Aspose, ou lancez un nouveau projet et testez le code ci‑dessus. Bon codage, et que vos documents s’affichent toujours exactement comme prévu !

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}