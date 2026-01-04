---
category: general
date: 2026-01-03
description: Comment détecter les polices dans Aspose.Words et gérer les avertissements
  à l'aide des paramètres de police Aspose – un guide étape par étape pour les développeurs.
draft: false
keywords:
- how to detect fonts
- how to handle warnings
- aspose font settings
- how to configure warnings
language: fr
og_description: Comment détecter les polices dans Aspose.Words et configurer les avertissements
  avec les paramètres de police Aspose. Apprenez le flux complet en quelques minutes.
og_title: Comment détecter les polices dans Aspose.Words – Gérer les avertissements
tags:
- Aspose.Words
- C#
- Document Processing
title: Comment détecter les polices dans Aspose.Words – Gérer les avertissements et
  les paramètres
url: /fr/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment détecter les polices dans Aspose.Words – Gérer les avertissements et les paramètres

Vous vous êtes déjà demandé **comment détecter les polices** dans un document Word avant qu’il ne passe en production ? Vous n’êtes pas seul. Des polices manquantes peuvent provoquer des cauchemars de mise en page, et sans avertissements appropriés vous pourriez livrer un PDF ou un DOCX défectueux sans même vous en rendre compte.  

Dans ce tutoriel, nous allons parcourir **comment détecter les polices** à l’aide d’Aspose.Words, montrer **comment gérer les avertissements**, et ajuster **les paramètres de police Aspose** afin que vous puissiez **configurer les avertissements** exactement comme vous le souhaitez. À la fin, vous disposerez d’un extrait prêt à l’emploi qui affiche chaque substitution effectuée par Aspose, et vous saurez comment l’adapter à vos propres projets.

## Prérequis

- .NET 6+ (ou .NET Framework 4.6+).  
- Aspose.Words pour .NET installé via NuGet (`Install-Package Aspose.Words`).  
- Un fichier Word qui référence intentionnellement une police manquante (par ex., *DocumentWithMissingFonts.docx*).  

Si vous avez déjà tout cela, super—plongeons‑y.

![capture d’écran de la détection des polices](https://example.com/detect-fonts.png "exemple de sortie de la détection des polices")

## Comment détecter les polices avec Aspose.Words

La première étape consiste à dire à Aspose.Words que vous vous souciez des événements de substitution de police. Cela se fait en fournissant un rappel d’avertissement personnalisé via **les paramètres de police Aspose**. Le rappel reçoit un objet `WarningInfo` pour chaque substitution, vous permettant de **détecter les polices** à l’exécution.

### Étape 1 : Créer une classe de rappel d’avertissement

Implémentez l’interface `IWarningCallback`. Dans la méthode `Warning`, filtrez sur `WarningType.FontSubstitution` et consignez les détails.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Receives warnings from Aspose.Words during document loading.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Only act on font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This is where we **detect fonts** that were missing.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

> **Astuce :** La chaîne `info.Description` contient à la fois le nom de la police manquante et la police de substitution choisie par Aspose. Vous pouvez l’analyser si vous avez besoin d’un rapport structuré.

### Étape 2 : Configurer LoadOptions avec les paramètres de police Aspose

Créez une instance de `LoadOptions`, attachez un nouvel objet `FontSettings`, et pointez `WarningCallback` vers le gestionnaire que nous venons de créer. Cela indique à Aspose **comment configurer les avertissements**.

```csharp
// Prepare load options – this is where we **configure warnings**.
LoadOptions loadOptions = new LoadOptions
{
    // FontSettings can be further customized (e.g., add a custom folder).
    FontSettings = new FontSettings(),
    WarningCallback = new FontSubstitutionWarningHandler()
};
```

Si vous avez un dossier de polices privées, vous pouvez l’ajouter ainsi :

```csharp
loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", false);
```

Cette ligne montre un autre aspect des **paramètres de police Aspose**—vous contrôlez exactement où Aspose recherche les polices avant de décider de les substituer.

### Étape 3 : Charger le document et déclencher le rappel

Chargez maintenant le document cible avec les `loadOptions`. Au fur et à mesure qu’Aspose analyse le fichier, toute police manquante déclenche le gestionnaire d’avertissement, détectant ainsi **les polices** à la volée.

```csharp
// The document contains missing fonts, which will fire our warning handler.
Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFonts.docx", loadOptions);
```

Lorsque vous exécutez le programme, vous verrez une sortie similaire à :

```
Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Font substituted: Font 'Times New Roman' was not found. Substituted with 'Calibri'.
```

### Étape 4 : (Facultatif) Collecter les avertissements pour une utilisation ultérieure

Si vous devez stocker les données de substitution pour un rapport, modifiez le gestionnaire afin d’accumuler les messages dans une liste.

```csharp
class FontSubstitutionWarningHandler : IWarningCallback
{
    public List<string> Substitutions { get; } = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Substitutions.Add(info.Description);
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

Vous pourrez ensuite écrire `handler.Substitutions` dans un fichier JSON, l’envoyer à un service de journalisation, ou l’afficher dans une interface utilisateur.

### Étape 5 : Vérifier le résultat de façon programmatique

Parfois, vous voulez vous assurer qu’*aucune* substitution n’a eu lieu (par ex., dans une construction CI). Voici une vérification rapide :

```csharp
var handler = new FontSubstitutionWarningHandler();
loadOptions.WarningCallback = handler;

Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFonts.docx", loadOptions);

if (handler.Substitutions.Count == 0)
{
    Console.WriteLine("All fonts were found – no substitutions.");
}
else
{
    Console.WriteLine($"Detected {handler.Substitutions.Count} missing fonts.");
}
```

Cet extrait montre **comment gérer les avertissements** de manière déterministe, vous donnant un contrôle total sur le pipeline de construction.

## Questions fréquentes (et cas particuliers)

**Que faire si je dois ignorer certaines substitutions ?**  
Vous pouvez ajouter une logique conditionnelle à l’intérieur de `Warning` et simplement retourner sans consigner les polices que vous considérez acceptables.

**Puis‑je supprimer tous les avertissements et obtenir uniquement un résultat booléen ?**  
Oui—définissez `loadOptions.WarningCallback = null` puis inspectez `doc.FontInfo` après le chargement (bien que vous perdiez le journal détaillé).

**Cela fonctionne‑t‑il avec la conversion PDF ?**  
Absolument. Le même mécanisme d’avertissement se déclenche lorsque vous appelez `doc.Save("out.pdf")`. Le rappel capturera toutes les substitutions de police effectuées pendant l’étape de conversion.

**Y a‑t‑il un impact sur les performances ?**  
Le surcoût est minime—seulement quelques appels de méthode supplémentaires par police manquante. Pour de gros lots, vous pourriez vouloir mettre en cache les résultats.

## Récapitulatif : Ce que nous avons couvert

- **Comment détecter les polices** en implémentant un `IWarningCallback` personnalisé.  
- **Comment gérer les avertissements** via `LoadOptions.WarningCallback`.  
- Ajustement des **paramètres de police Aspose** (ajout de dossiers de polices personnalisés, activation/désactivation des avertissements).  
- **Comment configurer les avertissements** pour une sortie console immédiate et une analyse ultérieure.  

Avec ces éléments en place, vous pouvez traiter les documents Word en toute confiance, garantir que les polices manquantes sont signalées, et maintenir une sortie cohérente entre les environnements.

## Prochaines étapes

- Explorez `FontSettings.SubstitutionSettings` pour un contrôle plus granulaire (par ex., mapper des polices manquantes spécifiques à des substituts choisis).  
- Combinez cette approche avec Aspose.PDF pour générer des PDF qui conservent une typographie exacte.  
- Automatisez la vérification des avertissements dans un pipeline CI/CD afin de bloquer les versions contenant des problèmes de police—parfait pour les équipes qui **gèrent les avertissements** comme partie des portes de qualité.

Vous avez d’autres questions sur les **paramètres de police Aspose** ou besoin d’aide pour intégrer cela dans un service plus vaste ? Laissez un commentaire ci‑dessous, et bon codage !

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}