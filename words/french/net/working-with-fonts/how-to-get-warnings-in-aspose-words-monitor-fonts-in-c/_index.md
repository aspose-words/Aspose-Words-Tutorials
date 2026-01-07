---
category: general
date: 2026-01-06
description: Apprenez comment obtenir des avertissements lors du chargement de documents
  et comment surveiller les polices avec Aspose.Words. Ce guide couvre les rappels
  d’avertissement et le suivi de la substitution de polices.
draft: false
keywords:
- how to get warnings
- how to monitor fonts
- Aspose.Words warning callback
- font substitution detection
- document load options
language: fr
og_description: Comment obtenir des avertissements dans Aspose.Words ? Suivez ce tutoriel
  étape par étape pour surveiller les polices et capturer les messages de substitution
  lors du chargement des documents.
og_title: Comment obtenir des avertissements dans Aspose.Words – Surveiller les polices
tags:
- Aspose.Words
- C#
- Font Monitoring
title: Comment obtenir des avertissements dans Aspose.Words – surveiller les polices
  en C#
url: /fr/net/working-with-fonts/how-to-get-warnings-in-aspose-words-monitor-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment obtenir des avertissements dans Aspose.Words – Surveiller les polices en C#

Vous vous êtes déjà demandé **comment obtenir des avertissements** lorsqu’un document Word contient des polices que vous n’avez pas installées ? C’est un problème fréquent—votre application remplace silencieusement les polices manquantes, et vous ne savez jamais ce qui a changé. La bonne nouvelle, c’est que vous pouvez vous brancher sur le système d’avertissement d’Aspose.Words et **surveiller les polices** en temps réel.

Dans ce tutoriel, nous vous montrerons exactement comment capturer ces avertissements de substitution de police, pourquoi c’est important, et quoi faire avec l’information une fois que vous l’avez. Aucun document externe, juste un exemple complet et exécutable que vous pouvez coller dans Visual Studio dès maintenant.

> **Astuce :** Si vous construisez une chaîne de conversion de documents, consigner les polices manquantes dès le départ vous évite de mauvaises surprises de mise en page en aval.

---

## Ce dont vous avez besoin

- **Aspose.Words for .NET** (dernière version ; l’API n’a pas changé depuis v23.10)
- Un environnement de développement .NET (Visual Studio, Rider ou VS Code avec l’extension C#)
- Un fichier `.docx` d’exemple qui référence une police que vous n’avez pas installée (par ex., **« NonExistentFont »**)

C’est tout—aucun package NuGet supplémentaire en dehors d’Aspose.Words.

---

## Étape 1 – Configurer un collecteur d’avertissements (Mot‑clé principal dans l’en‑tête)

La première chose dont vous avez besoin est un endroit où stocker les avertissements au fur et à mesure qu’ils surviennent. Aspose.Words fournit la propriété `WarningCallback` sur `LoadOptions` exactement pour cela.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

// Create a collection that will receive every warning emitted during load.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Attach the collector to LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = warningCollector
};
```

**Pourquoi c’est important :**  
Lorsque la bibliothèque rencontre une police manquante, elle ne lève pas d’exception ; elle émet un objet `WarningInfo`. En branchant un collecteur, vous obtenez une visibilité complète sur chaque événement de substitution, vous permettant de **surveiller les polices** sans polluer votre console avec des messages non pertinents.

---

## Étape 2 – Charger le document avec les options d’avertissement activées

Nous allons maintenant réellement lire le fichier. Les `LoadOptions` que nous avons préparées à l’étape précédente garantissent que tous les avertissements liés aux polices sont capturés.

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\unknownFont.docx";

Document doc = new Document(docPath, loadOptions);
```

**Ce qui se passe en coulisses :**  
Aspose.Words analyse le fichier Word, résout les polices, et chaque fois qu’il ne trouve pas la police demandée, il revient à une police de substitution (généralement Arial). Ce recours déclenche un avertissement `WarningType.FontSubstitution`, qui se retrouve dans `warningCollector`.

---

## Étape 3 – Inspecter les avertissements collectés (Le mot‑clé principal apparaît à nouveau)

Une fois le document chargé, nous parcourons simplement le `warningCollector` et affichons les messages de substitution de police.

```csharp
foreach (WarningInfo warning in warningCollector)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        // The Description contains a readable message like:
        // "Font 'NonExistentFont' was not found. Substituted with 'Arial'."
        Console.WriteLine($"Substituted font: {warning.Description}");
    }
}
```

**Sortie attendue** (en supposant que la police manquante soit *« FancyScript »*) :

```
Substituted font: Font 'FancyScript' was not found. Substituted with 'Arial'.
```

Si le document contient plusieurs polices inconnues, vous verrez une ligne par substitution—parfait pour la journalisation ou les alertes.

---

## Étape 4 – Optionnel : consigner ou persister les informations d’avertissement

En production, vous voudrez probablement plus qu’un `Console.WriteLine`. Voici un exemple rapide qui écrit les avertissements dans un fichier JSON pour une analyse ultérieure.

```csharp
using System.IO;
using System.Text.Json;

// Build a simple DTO.
var warnings = warningCollector
    .Where(w => w.WarningType == WarningType.FontSubstitution)
    .Select(w => new { FontMessage = w.Description })
    .ToList();

string json = JsonSerializer.Serialize(warnings, new JsonSerializerOptions { WriteIndented = true });
File.WriteAllText(@"C:\Logs\font-warnings.json", json);

Console.WriteLine("Font warnings saved to font-warnings.json");
```

Vous avez maintenant un enregistrement permanent que vous pouvez injecter dans un tableau de bord de surveillance, ou même déclencher une requête automatisée pour les fichiers de police manquants.

---

## Étape 5 – Vérifier le résultat et nettoyer

Exécutez le programme. Si vous voyez les messages de substitution, vous avez réussi à **obtenir des avertissements** et vous **surveillez activement les polices**. Si rien n’apparaît, vérifiez que le document de test référence réellement une police qui n’est pas installée sur la machine.

```csharp
// Quick sanity check – print the total number of warnings captured.
Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
```

Un compteur à zéro signifie généralement soit :

1. Toutes les polices ont été résolues (peut‑être que la police *est* installée localement), ou
2. Le document ne contenait aucune référence de police nécessitant une substitution.

---

## Pièges courants & comment les éviter

| Piège | Pourquoi cela se produit | Solution |
|-------|--------------------------|----------|
| **Aucun avertissement n’apparaît** | La police existe réellement sur le système, ou le document n’utilise que des polices intégrées. | Renommez la police dans le fichier source avec un nom impossible (par ex., `XYZ123`) et réessayez. |
| **Trop d’avertissements (bruit)** | Vous chargez de nombreux documents dans une boucle sans vider le collecteur. | Réinstanciez `WarningInfoCollection` pour chaque document, ou appelez `warningCollector.Clear()` après le traitement. |
| **Impact sur les performances** | Une journalisation excessive sur le disque peut ralentir le traitement par lots. | Mettez les avertissements en mémoire tampon et écrivez‑les en bloc, ou utilisez une I/O asynchrone. |
| **`using Aspose.Words.Loading;` manquant** | La classe `LoadOptions` se trouve dans cet espace de noms. | Ajoutez la directive `using` manquante, comme indiqué à l’étape 1. |

---

## Étendre la solution – Surveiller d’autres types d’avertissements

Bien que la substitution de police soit la plus visible, Aspose.Words peut émettre des avertissements pour :

- **Fonctionnalités obsolètes** (`WarningType.Deprecated`),
- **Perte de données potentielle** (`WarningType.DataLoss`),
- **Formats de fichier non pris en charge** (`WarningType.UnsupportedFileFormat`).

Vous pouvez élargir le filtre à l’étape 3 pour capturer ceux‑ci également :

```csharp
if (warning.WarningType != WarningType.None)
{
    Console.WriteLine($"{warning.WarningType}: {warning.Description}");
}
```

De cette façon, vous ne faites pas seulement **surveiller les polices**, mais aussi **obtenir des avertissements** pour tout scénario que votre application pourrait rencontrer.

---

## Exemple complet fonctionnel (prêt à copier‑coller)

```csharp
using System;
using System.IO;
using System.Linq;
using System.Text.Json;
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

class Program
{
    static void Main()
    {
        // Step 1 – Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();
        LoadOptions loadOptions = new LoadOptions { WarningCallback = warningCollector };

        // Step 2 – Load the document (adjust the path to your file).
        string docPath = @"C:\Docs\unknownFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // Step 3 – Output font substitution warnings.
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Substituted font: {warning.Description}");
            }
        }

        // Optional Step 4 – Persist warnings to JSON.
        var fontWarnings = warningCollector
            .Where(w => w.WarningType == WarningType.FontSubstitution)
            .Select(w => new { Message = w.Description })
            .ToList();

        string json = JsonSerializer.Serialize(fontWarnings, new JsonSerializerOptions { WriteIndented = true });
        File.WriteAllText(@"C:\Logs\font-warnings.json", json);
        Console.WriteLine("Font warnings saved to font-warnings.json");

        // Step 5 – Quick sanity check.
        Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
    }
}
```

**Exécutez‑le :** Compilez le projet, lancez‑le, et vous verrez les avertissements affichés et enregistrés. C’est la réponse complète à **comment obtenir des avertissements** et **comment surveiller les polices** avec Aspose.Words.

---

## Conclusion

Vous savez maintenant **comment obtenir des avertissements** d’Aspose.Words, spécifiquement pour les scénarios de substitution de police, et vous avez appris **comment surveiller les polices** tout au long du processus de chargement du document. En attachant un `WarningCallback`, en parcourant les objets `WarningInfo` collectés, et éventuellement en persistant les données, vous obtenez une transparence totale sur les événements de police manquante—une capacité essentielle pour toute chaîne de traitement de documents.

Prochaines étapes ? Essayez d’élargir le filtre d’avertissement pour couvrir les pertes de données ou les avertissements de fonctionnalités obsolètes, ou intégrez le journal JSON dans un tableau de bord de surveillance comme Grafana. Le même modèle fonctionne pour tous les types d’avertissements, vous serez donc bien équipé pour garder un œil sur tout problème qu’Aspose.Words pourrait générer.

Bon codage, et que vos documents s’affichent toujours exactement comme vous le souhaitez !

---

<img src="font-warnings.png" alt="comment obtenir des avertissements dans Aspose.Words" style="max-width:100%;">

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}