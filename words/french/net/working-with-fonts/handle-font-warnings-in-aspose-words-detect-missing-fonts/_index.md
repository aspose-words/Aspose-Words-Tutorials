---
category: general
date: 2026-02-28
description: Apprenez à gérer les avertissements de police et à détecter les polices
  manquantes dans Aspose.Words avec C#. Guide complet étape par étape avec le code
  complet.
draft: false
keywords:
- handle font warnings
- detect missing fonts
language: fr
og_description: Gérez les avertissements de police dans Aspose.Words et détectez les
  polices manquantes avec un exemple C# prêt à l'emploi. Suivez les étapes et voyez
  le résultat.
og_title: Gérer les avertissements de police dans Aspose.Words – Guide complet
tags:
- Aspose.Words
- C#
- Document Loading
title: Gérer les avertissements de police dans Aspose.Words – Détecter les polices
  manquantes
url: /fr/net/working-with-fonts/handle-font-warnings-in-aspose-words-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Gérer les avertissements de police dans Aspose.Words – Détecter les polices manquantes

Vous avez déjà eu besoin de **gérer les avertissements de police** lors du chargement d’un document Word et vous vous êtes demandé pourquoi certains textes apparaissent étranges ? Vous n’êtes pas seul. Les polices manquantes déclenchent des avertissements de substitution qui peuvent corrompre silencieusement la mise en page visuelle, et si vous ne **détectez pas les polices manquantes** vous ne saurez jamais ce qui s’est passé.

Dans ce tutoriel, nous vous montrons une façon pratique de **gérer les avertissements de police** en utilisant `IWarningCallback` d’Aspose.Words. À la fin du guide, vous serez capable d’identifier chaque événement de substitution de police, de l’enregistrer, et même de décider d’interrompre le chargement. Aucun document externe, juste un exemple prêt à copier‑coller.

## Ce que vous allez apprendre

- Configurer un gestionnaire d’avertissement personnalisé qui ne réagit qu’aux alertes de substitution de police.  
- Attacher ce gestionnaire à `LoadOptions` afin que chaque chargement de document le traverse.  
- Vérifier la sortie dans la console et comprendre la signification de chaque avertissement.  

**Prérequis**

- .NET 6.0 ou supérieur (le code fonctionne également avec .NET Framework 4.6+).  
- Aspose.Words for .NET installé via NuGet (`Install-Package Aspose.Words`).  
- Un fichier Word qui référence une police non installée sur votre machine (par ex., une police d’entreprise personnalisée).  

Si l’un de ces éléments vous manque, procurez‑le‑vous maintenant—sinon, passons à l’action.

## Comment gérer les avertissements de police dans Aspose.Words

Voici le programme complet, exécutable. Il comprend tout, des déclarations `using` à la méthode `Main`, de sorte que vous pouvez le coller dans une application console et appuyer sur **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

/// <summary>
/// Custom warning handler that reacts only to font‑substitution warnings.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We’re only interested in font substitution events.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write a clear message to the console – this is how we **detect missing fonts**.
            Console.WriteLine($"⚠️ Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Step 1: Create LoadOptions and attach the custom warning callback.
        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        // Step 2: Load the document. Any missing font will trigger our handler.
        // Replace the path with the actual location of your test document.
        string docPath = @"C:\Docs\MissingFont.docx";

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
        }

        // Keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

> **Sortie console attendue** (en supposant que le document utilise une police que vous n’avez pas installée) :  
> ```
> ⚠️ Font substituted: Font 'MyCustomFont' was substituted with 'Arial'.
> ✅ Document loaded successfully.
> 
> Press any key to exit...
> ```

Si le document ne contient **aucune police manquante**, la ligne d’avertissement n’apparaît jamais—vous avez donc **détecté les polices manquantes** uniquement lorsque c’est nécessaire.

### Pourquoi cela fonctionne

Aspose.Words génère un `WarningInfo` pour chaque problème non critique rencontré lors de l’analyse d’un fichier. En implémentant `IWarningCallback`, vous obtenez un point d’accroche dans ce pipeline. Le drapeau `WarningType.FontSubstitution` vous indique précisément quand la bibliothèque a dû remplacer une police demandée par une police de secours. C’est la méthode la plus fiable pour **gérer les avertissements de police** car elle s’exécute *pendant* le chargement, avant même que vous n’interagissiez avec le modèle d’objet du document.

## Détecter les polices manquantes sans casser votre application

Parfois, vous voudrez peut‑être traiter une police manquante comme une erreur fatale—peut‑être que vos directives de marque interdisent toute substitution. Vous pouvez modifier le gestionnaire pour lever une exception au lieu de simplement consigner :

```csharp
public void Warning(WarningInfo info)
{
    if (info.WarningType == WarningType.FontSubstitution)
    {
        // Throwing stops the load process; you can catch it higher up.
        throw new InvalidOperationException($"Missing font detected: {info.Description}");
    }
}
```

Désormais, le bloc `try…catch` autour de `new Document(...)` capturera le problème, vous laissant décider d’interrompre, de recourir à une alternative, ou d’informer l’utilisateur.

## Bonus : visualiser les avertissements dans une application UI

Si vous développez une application WinForms ou WPF, remplacez `Console.WriteLine` par un appel compatible UI :

```csharp
MessageBox.Show($"Font substituted: {info.Description}", "Font Warning",
                MessageBoxButtons.OK, MessageBoxIcon.Warning);
```

Ainsi, les utilisateurs finaux voient immédiatement l’avertissement, et vous continuez à **gérer les avertissements de police** de façon cohérente sur toutes les plateformes.

## Pièges courants & astuces professionnelles

- **Piège :** Oublier de définir `WarningCallback`. Le comportement par défaut est d’ignorer les avertissements de police, vous ne les verrez donc jamais.  
  **Astuce :** Créez toujours une instance de `LoadOptions` même si vous n’avez besoin que du gestionnaire d’avertissement. C’est peu coûteux et explicite.  

- **Piège :** Utiliser le mauvais séparateur de chemin sur un OS non Windows.  
  **Astuce :** Utilisez `Path.Combine` ou une chaîne brute (`@"C:\Docs\MissingFont.docx"` fonctionne sous Windows ; sous Linux utilisez `"/home/user/docs/MissingFont.docx"`).  

- **Piège :** Supposer que l’avertissement se déclenchera pour les polices incorporées.  
  **Astuce :** Les polices incorporées sont considérées comme présentes, donc aucun avertissement de substitution n’apparaît. Testez avec de vraies polices *manquantes* pour voir le gestionnaire en action.  

- **Piège :** Surcharger le journal avec chaque type d’avertissement.  
  **Astuce :** Filtrez par `WarningType.FontSubstitution` comme montré—cela garde la console propre et se concentre sur le scénario de **détection des polices manquantes**.

## Récapitulatif de l’exemple complet

Voici à nouveau le programme entier, cette fois sans commentaires pour ceux qui préfèrent une vue épurée :

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
            Console.WriteLine($"⚠️ Font substituted: {info.Description}");
    }
}

class Program
{
    static void Main()
    {
        var loadOptions = new LoadOptions { WarningCallback = new FontWarningHandler() };
        string docPath = @"C:\Docs\MissingFont.docx";

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
        }

        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

Copiez, collez, exécutez—votre console **gérera désormais les avertissements de police** et **détectera automatiquement les polices manquantes**.

## Prochaines étapes

- **Journaliser dans un fichier :** Remplacez `Console.WriteLine` par un logger (par ex., NLog) pour un suivi de niveau production.  
- **Traitement par lots :** Parcourez un dossier de documents, collectez tous les événements de substitution de police dans un rapport CSV.  
- **Installation automatique de polices :** Reliez le gestionnaire d’avertissement pour télécharger les polices manquantes depuis un dépôt d’entreprise avant de poursuivre le chargement.  

Chacune de ces extensions s’appuie sur l’idée centrale de **gérer les avertissements de police** de manière propre et réutilisable.

---

*Bon codage ! Si vous rencontrez des particularités en essayant de **détecter les polices manquantes**, laissez un commentaire ci‑dessous. Je serai ravi de vous aider à résoudre le problème.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}