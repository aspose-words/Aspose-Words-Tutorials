---
category: general
date: 2026-02-26
description: Gérez les polices manquantes en C# avec Aspose.Words. Apprenez à capturer
  les avertissements de substitution de police, à implémenter IWarningCallback et
  à maintenir l’apparence correcte de vos documents.
draft: false
keywords:
- handle missing fonts
- Aspose.Words font warning
- C# LoadOptions
- IWarningCallback implementation
- document loading with missing fonts
- font substitution handling
language: fr
og_description: Gérez rapidement les polices manquantes en C#. Ce guide montre comment
  capturer les avertissements de substitution de police avec Aspose.Words, implémenter
  IWarningCallback et vérifier les résultats.
og_title: Gérer les polices manquantes en C# – Tutoriel Aspose.Words étape par étape
tags:
- Aspose.Words
- C#
- Document Processing
title: Gérer les polices manquantes en C# avec Aspose.Words – Guide complet
url: /fr/net/working-with-fonts/handle-missing-fonts-in-c-with-aspose-words-complete-guide/
---

Now produce final output with everything.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Gérer les polices manquantes en C# avec Aspose.Words – Guide complet

Vous avez déjà eu besoin de **gérer les polices manquantes** lors du chargement d’un document Word en C# et vous vous êtes demandé pourquoi le rendu était étrange ? Vous n’êtes pas le seul. Lorsqu’un fichier source fait référence à une police qui n’est pas installée sur la machine, Aspose.Words la remplace silencieusement par une autre, ce qui peut casser votre mise en page ou votre identité visuelle.  

La bonne nouvelle ? En branchant un **callback d’avertissement**, vous pouvez intercepter chaque événement de substitution de police, le consigner, et décider de fournir un remplacement. Dans ce tutoriel, nous parcourrons l’ensemble du processus—de la configuration du projet à la vérification de la sortie console—afin que vous ne soyez plus jamais surpris par une police invisible.

> **Ce que vous obtiendrez** : Une application console C# prête à l’emploi qui signale chaque police manquante, explique pourquoi l’avertissement se produit, et vous montre comment étendre le gestionnaire pour une logique personnalisée.

---

## Prérequis

- .NET 6.0 ou ultérieur (le code fonctionne aussi bien sur .NET Core que sur .NET Framework)
- Visual Studio 2022 (ou tout IDE C# de votre choix)
- Une **licence** pour Aspose.Words for .NET (l’essai gratuit suffit pour les tests)
- Un document Word qui fait référence à une police que vous n’avez pas installée (par ex., *Comic Sans MS* sur une machine Linux)

Si vous avez tout cela, plongeons‑y.

---

## Étape 1 : Créez un nouveau projet console et ajoutez Aspose.Words

Pour garder les choses ordonnées, commencez avec un nouveau projet console.

```bash
dotnet new console -n FontWarningDemo
cd FontWarningDemo
dotnet add package Aspose.Words
```

> **Astuce** : Utilisez le drapeau `--framework net6.0` si vous souhaitez cibler un runtime spécifique.

Cela récupère le dernier package NuGet Aspose.Words, qui contient les types `LoadOptions` et `IWarningCallback` dont nous aurons besoin.

## Étape 2 : Implémentez un gestionnaire d’avertissement (IWarningCallback)

Aspose.Words génère un objet `WarningInfo` pour chaque problème non critique rencontré lors du chargement d’un document. En implémentant `IWarningCallback`, vous décidez quoi faire de ces avertissements.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

public class FontWarningHandler : IWarningCallback
{
    // This method is called automatically by Aspose.Words whenever a warning occurs.
    public void Warning(WarningInfo info)
    {
        // We’re only interested in font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // The Description property contains the name of the missing font and the substitute used.
            Console.WriteLine($"⚠️ Missing font detected: {info.Description}");
        }
        // You could also log other warning types here if you wish.
    }
}
```

**Pourquoi c’est important** : Sans gestionnaire, les avertissements de substitution de police sont ignorés silencieusement. En les affichant, vous obtenez une visibilité immédiate sur les polices manquantes et sur ce qu’Aspose.Words a utilisé à la place.

## Étape 3 : Configurez LoadOptions avec le callback d’avertissement

Nous allons maintenant lier le gestionnaire au processus de chargement du document. `LoadOptions` vous permet d’insérer le callback avant que le fichier ne soit analysé.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // 1️⃣ Tell Aspose.Words to use our FontWarningHandler.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        // 2️⃣ Path to the Word file that contains missing fonts.
        string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFont.docx";

        // 3️⃣ Load the document with the custom options.
        Document doc = new Document(docPath, loadOptions);

        // At this point, any font‑substitution warning has already been printed.
        Console.WriteLine("✅ Document loaded successfully.");
    }
}
```

> **Note** : Remplacez `YOUR_DIRECTORY` par le dossier réel contenant votre fichier `.docx` de test. L’instance `LoadOptions` doit être passée au constructeur `Document` ; sinon le comportement silencieux par défaut s’appliquera.

## Étape 4 : Exécutez l’application et vérifiez la sortie

Compilez et exécutez :

```bash
dotnet run
```

Si le document fait référence à une police qui n’est pas présente sur votre machine (par ex., *Papyrus*), vous verrez quelque chose comme :

```
⚠️ Missing font detected: The font 'Papyrus' was not found. Using 'Times New Roman' as a substitute.
✅ Document loaded successfully.
```

Cette ligne unique vous indique exactement quelle police est manquante et quel substitut Aspose.Words a choisi. Vous pouvez maintenant décider d’incorporer la police manquante, de modifier le document source, ou d’accepter la substitution.

## Étape 5 : Avancé – Collecter les avertissements pour une utilisation ultérieure

Parfois vous souhaitez stocker les avertissements au lieu de les afficher immédiatement. Voici une petite modification du gestionnaire qui agrège les messages dans une liste.

```csharp
using System.Collections.Generic;

public class FontWarningCollector : IWarningCallback
{
    public List<string> Messages { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string msg = $"Missing font: {info.Description}";
            Messages.Add(msg);
        }
    }
}
```

Et mettez à jour `Main` en conséquence :

```csharp
static void Main()
{
    var collector = new FontWarningCollector();

    LoadOptions lo = new LoadOptions { WarningCallback = collector };
    Document doc = new Document(@"YOUR_DIRECTORY\DocumentWithMissingFont.docx", lo);

    Console.WriteLine("✅ Document loaded.");
    if (collector.Messages.Count > 0)
    {
        Console.WriteLine("\n--- Font Substitution Report ---");
        foreach (var m in collector.Messages)
            Console.WriteLine(m);
    }
}
```

Vous disposez maintenant d’une liste réutilisable que vous pouvez écrire dans un fichier de log, envoyer à un service de surveillance, ou afficher dans une interface utilisateur.

## Étape 6 : Pièges courants et comment les éviter

| Problème | Pourquoi cela se produit | Solution |
|----------|--------------------------|----------|
| **Aucun avertissement n’apparaît** | Le callback n’a pas été attaché, ou le document a été chargé sans `LoadOptions`. | Assurez‑vous que `LoadOptions.WarningCallback` est défini **avant** d’appeler le constructeur `Document`. |
| **Nom de police incorrect dans le message** | Certaines polices sont incorporées dans le document ; Aspose.Words indique le nom *original*, pas celui incorporé. | Vérifiez les références de police du fichier source ; incorporer les polices élimine complètement l’avertissement. |
| **Impact sur les performances** | Collecter les avertissements pour des milliers de documents peut ajouter une surcharge. | Utilisez un simple `Console.WriteLine` pour un débogage rapide ; passez à un collecteur uniquement lorsque vous avez besoin des données. |

## Résumé visuel

![Illustration de la gestion des polices manquantes montrant le flux du callback d’avertissement](/images/handle-missing-fonts.png "Diagramme de la gestion des polices manquantes avec Aspose.Words")

*Le diagramme (le texte alternatif inclut le mot‑clé principal) visualise comment le callback d’avertissement intercepte les événements de substitution de police lors du chargement du document.*

## Conclusion

Vous savez maintenant **comment gérer les polices manquantes** en C# avec Aspose.Words. En branchant un `IWarningCallback` dans `LoadOptions`, vous obtenez une visibilité complète sur chaque événement de substitution de police, pouvez le consigner ou agir en conséquence, et assurez en fin de compte que vos documents générés conservent l’apparence et le rendu prévus.

> **Récapitulatif rapide** :  
> 1. Ajoutez Aspose.Words à une application console.  
> 2. Implémentez `FontWarningHandler` (ou un collecteur).  
> 3. Transmettez‑le via `LoadOptions` lors du chargement du document.  
> 4. Vérifiez la sortie console ou les avertissements stockés.  

À partir d’ici, vous pourriez explorer **l’incorporation des polices manquantes** (`FontSettings.SubstitutionSettings`) ou **le téléchargement automatique depuis un serveur de polices d’entreprise**—deux extensions naturelles du modèle que nous venons de créer.

Vous avez d’autres questions sur **l’avertissement de police Aspose.Words**, **C# LoadOptions**, ou **le chargement de documents avec des polices manquantes** ? Laissez un commentaire, et bon codage !

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}