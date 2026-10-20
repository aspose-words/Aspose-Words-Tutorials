---
category: general
date: 2026-04-04
description: Apprenez à capturer les avertissements, à détecter les polices manquantes
  et à consigner les événements de substitution à l'aide de LoadOptions d'Aspose.Words
  en C#.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to log substitution
- Aspose.Words warning handling
- font substitution monitoring
language: fr
og_description: Comment capturer les avertissements, détecter les polices manquantes
  et consigner les événements de substitution à l’aide de LoadOptions d’Aspose.Words
  en C#.
og_title: Comment capturer les avertissements en C# – détecter les polices manquantes
  et consigner les substitutions
tags:
- C#
- Aspose.Words
- Document Loading
- Font Management
title: Comment capturer les avertissements en C# – détecter les polices manquantes
  et consigner les substitutions
url: /fr/net/programming-with-loadoptions/how-to-capture-warnings-in-c-detect-missing-fonts-log-substi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment capturer les avertissements en C# – Détecter les polices manquantes et consigner les substitutions

Vous vous êtes déjà demandé **comment capturer les avertissements** qui apparaissent lorsque vous chargez un document Word avec des polices manquantes ? Vous n'êtes pas seul. Dans de nombreux projets réels, les polices sont perdues lors de la migration, et le remplacement silencieux peut casser votre mise en page. Bonne nouvelle ? Aspose.Words vous offre un moyen propre d’écouter ces avertissements, de détecter les polices manquantes et même d’enregistrer chaque substitution afin de pouvoir corriger la source plus tard.

Dans ce tutoriel, nous parcourrons une solution complète, prête à l’exécution, qui montre **comment capturer les avertissements**, démontre **la détection des polices manquantes**, et explique **comment consigner les événements de substitution**. À la fin, vous disposerez d’un gestionnaire d’avertissements réutilisable, d’un objet `LoadOptions` entièrement configuré, et d’un exemple de sortie console que vous pourrez vérifier.

> **Prérequis :** Vous avez besoin d’Aspose.Words pour .NET (v24.x ou ultérieur) installé via NuGet et d’un environnement de développement C# de base (Visual Studio 2022 ou VS Code fonctionnent parfaitement).

---

## Comment capturer les avertissements lors du chargement de documents

Le cœur de la solution est une classe qui implémente `IWarningCallback`. Aspose.Words appelle automatiquement ce rappel pour chaque avertissement généré lors du chargement du document, y compris les avertissements de substitution de police.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

/// <summary>
/// Handles warning callbacks from Aspose.Words.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We're only interested in font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This line prints the warning to the console.
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

> **Pourquoi cette étape ?**  
> En filtrant sur `WarningType.FontSubstitution`, nous évitons l’encombrement des avertissements non liés (comme les fonctionnalités obsolètes). Cela rend le journal centré sur le problème exact qui vous intéresse — les polices manquantes.

---

## Détecter les polices manquantes avec Aspose.Words

Lorsqu’un document fait référence à une police qui n’est pas installée sur la machine, Aspose.Words substitue la police la plus proche et génère un avertissement. Notre gestionnaire ci‑dessus capturera chaque occurrence, détectant ainsi efficacement **les polices manquantes**.

Pour le voir en action, nous devons configurer `LoadOptions` et attacher le gestionnaire :

```csharp
// Configure load options and attach the warning callback.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

> **Astuce :** Si vous préférez collecter les avertissements pour un traitement ultérieur (par ex., écrire dans un fichier), remplacez `Console.WriteLine` par du code qui ajoute le message à une `List<string>`.

---

## Comment consigner les événements de substitution

La journalisation est aussi simple que de diriger la sortie d’avertissement vers un stockage persistant. Voici un exemple rapide qui écrit chaque avertissement de substitution dans un fichier texte nommé `font-warnings.log`.

```csharp
using System.IO;

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            // Append the message to the log file.
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

// Later, when creating LoadOptions:
var loadOptions = new LoadOptions
{
    WarningCallback = new FileLoggingWarningHandler()
};
```

> **Pourquoi consigner dans un fichier ?**  
> Les journaux persistants vous permettent d’auditer les problèmes de police sur plusieurs exécutions, d’automatiser les alertes, ou d’alimenter les vérifications d’une chaîne de construction.

---

## Exemple complet fonctionnel

En rassemblant tous les éléments, voici une application console autonome que vous pouvez copier, coller et exécuter. Elle montre **comment capturer les avertissements**, **détecter les polices manquantes**, et **comment consigner les substitutions** en une seule fois.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

class Program
{
    static void Main()
    {
        // Choose which handler you want:
        // var handler = new FontWarningHandler();          // console output
        var handler = new FileLoggingWarningHandler();    // file logging

        var loadOptions = new LoadOptions
        {
            WarningCallback = handler
        };

        // Path to the document that may contain missing fonts.
        string docPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

        try
        {
            // Load the document – warnings are raised automatically.
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
        }

        // If you used the file logger, show where the log lives.
        if (handler is FileLoggingWarningHandler)
        {
            Console.WriteLine($"Font warnings have been written to 'font-warnings.log'.");
        }
    }
}
```

### Sortie console attendue

Si `input.docx` fait référence à une police qui n’est pas installée, vous verrez quelque chose comme :

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document loaded successfully.
```

Si vous passez à `FileLoggingWarningHandler`, les mêmes lignes apparaîtront dans `font-warnings.log` avec des horodatages.

![sortie console de capture des avertissements](image-placeholder.png)

---

## Questions fréquentes et cas particuliers

### Et si je dois capturer *tous* les avertissements, pas seulement les substitutions de police ?

Il suffit de supprimer la vérification `if (info.Type == WarningType.FontSubstitution)`. Le rappel recevra chaque type d’avertissement (`WarningType.DegradedDocument`, `WarningType.UnexpectedContent`, etc.). Vous pourrez alors bifurquer sur `info.Type` pour gérer chaque cas différemment.

### Cela fonctionne‑t‑il avec les PDF ou uniquement avec les documents Word ?

`LoadOptions` et `IWarningCallback` font partie d’Aspose.Words, ils s’appliquent donc aux formats compatibles Word (`.docx`, `.doc`, `.rtf`, `.html`). Pour les PDF, vous utiliseriez les mécanismes d’avertissement propres à Aspose.PDF.

### Comment puis‑je supprimer les avertissements au lieu de les consigner ?

Définissez `LoadOptions.WarningCallback = null` ou implémentez le rappel mais laissez le corps de la méthode vide. La bibliothèque effectuera toujours la substitution silencieusement.

### Qu’en est‑il de la sécurité des threads ?

L’instance du rappel est invoquée sur le même thread qui charge le document, vous n’avez donc pas besoin de synchronisation supplémentaire sauf si vous partagez le gestionnaire entre des chargements parallèles. Dans ce cas, protégez les ressources partagées (par ex., le fichier de journal) avec un verrou ou utilisez des collections concurrentes.

---

## Conclusion

Nous avons couvert **comment capturer les avertissements** d’Aspose.Words, vous avons montré comment **détecter les polices manquantes**, et expliqué **comment consigner les événements de substitution** pour une analyse ultérieure. En branchant une implémentation simple de `IWarningCallback` dans `LoadOptions`, vous obtenez une visibilité complète sur les problèmes liés aux polices sans encombrer votre base de code.

Prochaines étapes ? Essayez d’étendre le journaliseur pour envoyer des e‑mails, l’intégrer à Azure Monitor, ou installer automatiquement les polices manquantes sur un serveur de construction. Vous pouvez également explorer d’autres types d’avertissements—`WarningType.DegradedDocument` peut vous alerter sur les fonctionnalités qui n’ont pas survécu au processus de conversion.

Vous avez d’autres questions sur la gestion des polices ou sur Aspose.Words en général ? Laissez un commentaire ou ouvrez un nouveau ticket sur les forums Aspose. Bon codage, et que vos documents s’affichent toujours avec la bonne police !

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}