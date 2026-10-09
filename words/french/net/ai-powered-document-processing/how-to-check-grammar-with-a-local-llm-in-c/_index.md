---
category: general
date: 2026-03-19
description: Apprenez à vérifier la grammaire dans Word en utilisant un LLM local,
  à enregistrer le modèle et à sauvegarder les documents corrigés — le tout dans un
  seul tutoriel C#.
draft: false
keywords:
- how to check grammar
- set up local llm
- check grammar in word
- how to register llm
- how to save corrected
language: fr
og_description: Comment vérifier la grammaire dans Word en utilisant un LLM local,
  enregistrer le modèle et sauvegarder les documents corrigés — guide étape par étape.
og_title: Comment vérifier la grammaire avec un LLM local en C#
tags:
- Aspose.Words
- AI
- C#
title: Comment vérifier la grammaire avec un LLM local en C#
url: /fr/net/ai-powered-document-processing/how-to-check-grammar-with-a-local-llm-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment vérifier la grammaire avec un LLM local en C#

Vous vous êtes déjà demandé **comment vérifier la grammaire** dans un document Word sans envoyer votre texte vers le cloud ? Vous n'êtes pas seul. De nombreux développeurs souhaitent la confidentialité d’un modèle auto‑hébergé tout en bénéficiant de suggestions alimentées par l’IA. Dans ce guide, nous allons parcourir l’enregistrement d’un LLM personnalisé, la configuration d’Aspose.Words pour l’utiliser, et enfin **comment enregistrer les fichiers corrigés** — le tout en C# pur.

Nous couvrirons également les détails de **configuration d’un LLM local**, vous montrerons **comment enregistrer les points de terminaison LLM**, et démontrerons les étapes exactes pour **vérifier la grammaire dans des documents Word**. À la fin, vous disposerez d’un exemple exécutable que vous pourrez intégrer à n’importe quel projet .NET.

## Prérequis

- .NET 6+ SDK (le code fonctionne sur .NET Core et .NET Framework)
- Visual Studio 2022 ou VS Code avec les extensions C#
- Aspose.Words for .NET (v24.12 ou plus récent) – vous pouvez le récupérer sur NuGet
- Un LLM exécuté localement qui utilise l’API compatible OpenAI (par ex., Ollama sur le port 11434)

> **Astuce :** Si vous utilisez Ollama, la commande `ollama serve` démarrera automatiquement le point de terminaison `http://localhost:11434/api/generate`.

## Étape 1 – Comment enregistrer le LLM : Ajouter le modèle personnalisé à Aspose.Words

La première chose à faire est d’informer Aspose.Words de notre **LLM local**. Cela se fait une fois au démarrage de l’application.

```csharp
using Aspose.Words;
using Aspose.Words.AI;

// Register a custom LLM endpoint – no API key required for local servers
AiEngine.RegisterModel(
    modelName: "local-llm",                         // identifier we’ll reference later
    endpoint: new Uri("http://localhost:11434/api/generate"),
    apiKey: null,                                   // local server doesn’t need a key
    provider: AiProvider.Custom);
```

**Pourquoi c’est important :** En enregistrant le modèle, vous donnez à Aspose.Words une poignée nommée (`"local-llm"`). Plus tard, lorsque nous appelons `CheckGrammar`, la bibliothèque sait exactement quel point de terminaison atteindre. Ignorer cette étape force la bibliothèque à revenir à son service cloud intégré, ce qui annule l’objectif d’un LLM privé.

## Étape 2 – Charger le document Word à analyser

Nous chargeons maintenant le fichier en mémoire. Vous pouvez pointer vers n’importe quel fichier `.docx`, `.doc` ou même `.rtf`.

```csharp
// Replace YOUR_DIRECTORY with the actual folder path on your machine
Document sourceDocument = new Document("YOUR_DIRECTORY/input.docx");

// Quick sanity check – print the number of paragraphs we just loaded
Console.WriteLine($"Loaded document with {sourceDocument.GetChildNodes(NodeType.Paragraph, true).Count} paragraphs.");
```

**Ce qui se passe :** `Document` est le modèle d’objet principal d’Aspose.Words. Il analyse le fichier et construit un arbre de nœuds (paragraphes, tableaux, images, etc.). Cela permet au moteur d’IA de cibler des plages de texte spécifiques pour l’analyse grammaticale.

## Étape 3 – Configurer les options de vérification grammaticale (configuration d’un LLM local)

Ici, nous associons le modèle précédemment enregistré à l’opération de vérification grammaticale.

```csharp
AiGrammarCheckOptions grammarOptions = new AiGrammarCheckOptions
{
    Model = "local-llm",               // references the name we used in RegisterModel
    // Optional: you can tweak temperature, maxTokens, etc. if your LLM supports them
    // Temperature = 0.7,
    // MaxTokens = 512
};
```

**Pourquoi nous exposons ces options :** Les différents LLM ont des comportements différents. En exposant `Model`, Aspose.Words vous permet de basculer entre un modèle local et un modèle cloud sans modifier le reste du code. Cette flexibilité est essentielle lors de la **configuration d’un LLM local** pour des environnements de conformité ou hors ligne.

## Étape 4 – Exécuter la vérification grammaticale pilotée par l’IA (vérifier la grammaire dans Word)

Une fois tout connecté, la vérification grammaticale réelle ne nécessite qu’une seule ligne.

```csharp
// This mutates sourceDocument in place, inserting suggestions and corrections
sourceDocument.CheckGrammar(grammarOptions);
Console.WriteLine("Grammar check completed.");
```

**En interne :** Aspose.Words extrait chaque phrase, l’envoie au point de terminaison du LLM, reçoit une charge JSON avec les suggestions de modifications, puis applique ces modifications à l’arbre du document. Le processus s’exécute ici de manière synchrone pour plus de simplicité ; vous pouvez également appeler la surcharge asynchrone `CheckGrammarAsync` si vous préférez une I/O non bloquante.

## Étape 5 – Comment enregistrer les documents corrigés

Après que l’IA a fait sa magie, vous voudrez persister les modifications.

```csharp
// Save the corrected file – you can change the format to PDF, HTML, etc.
sourceDocument.Save("YOUR_DIRECTORY/checked.docx");
Console.WriteLine("Corrected document saved as checked.docx");
```

**Ce à quoi vous attendre :** Ouvrez `checked.docx` dans Word et vous verrez les problèmes de grammaire soulignés (ou automatiquement corrigés, selon vos `AiGrammarCheckOptions`). Si le suivi est activé, vous verrez également les marques de révision.

## Exemple complet fonctionnel

En assemblant tout, voici une application console prête à l’exécution :

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.AI;

class Program
{
    static void Main()
    {
        // 1️⃣ Register the local LLM
        AiEngine.RegisterModel(
            modelName: "local-llm",
            endpoint: new Uri("http://localhost:11434/api/generate"),
            apiKey: null,
            provider: AiProvider.Custom);

        // 2️⃣ Load the source document
        string inputPath = "YOUR_DIRECTORY/input.docx";
        Document sourceDocument = new Document(inputPath);
        Console.WriteLine($"Loaded: {inputPath}");

        // 3️⃣ Set up grammar‑check options (using the local model)
        AiGrammarCheckOptions grammarOptions = new AiGrammarCheckOptions
        {
            Model = "local-llm"
        };

        // 4️⃣ Perform the AI‑driven grammar check
        sourceDocument.CheckGrammar(grammarOptions);
        Console.WriteLine("Grammar analysis finished.");

        // 5️⃣ Save the corrected document
        string outputPath = "YOUR_DIRECTORY/checked.docx";
        sourceDocument.Save(outputPath);
        Console.WriteLine($"Corrected file saved to: {outputPath}");
    }
}
```

**Sortie attendue dans la console :**

```
Loaded: YOUR_DIRECTORY/input.docx
Grammar analysis finished.
Corrected file saved to: YOUR_DIRECTORY/checked.docx
```

Ouvrez `checked.docx` et vous devriez voir les améliorations grammaticales appliquées automatiquement.

## Questions fréquentes & cas limites

| Question | Réponse |
|----------|--------|
| *Et si mon LLM nécessite une clé API ?* | Passez la clé à `apiKey` dans `RegisterModel`. Le même code fonctionne pour les services avec ou sans clé. |
| *Puis-je utiliser un autre format de fichier ?* | Absolument. `Document.Save` accepte les formats `.pdf`, `.html`, `.txt`, etc. Il suffit de changer l’extension. |
| *Et si le LLM renvoie une erreur ?* | Enveloppez `CheckGrammar` dans un try/catch ; inspectez `AiException` pour les détails. Souvent il s’agit d’un timeout—envisagez d’augmenter `grammarOptions.Timeout`. |
| *L’opération est‑elle thread‑safe ?* | L’étape d’enregistrement est globale et doit être effectuée une seule fois au démarrage. Les appels ultérieurs à `CheckGrammar` peuvent être exécutés en parallèle tant que chaque appel utilise sa propre instance de `Document`. |

## Prochaines étapes

Maintenant que vous savez **comment vérifier la grammaire** en utilisant un **LLM local**, vous pouvez explorer :

- **Traitement par lots** : Parcourir un dossier de documents et exécuter le même pipeline.  
- **Invites personnalisées** : Ajustez la charge de la requête en définissant `grammarOptions.PromptTemplate` pour des vérifications spécifiques de style.  
- **Intégration avec ASP.NET Core** : Exposez un point de terminaison API qui accepte des fichiers `.docx` téléchargés, exécute la vérification grammaticale et renvoie le fichier corrigé.  

Ces extensions vous permettent de créer une plateforme complète « grammaire‑en‑tant‑que‑service » sans jamais quitter vos locaux.

---

*Bon codage ! Si vous rencontrez des problèmes, laissez un commentaire ci‑dessous—je suis heureux de vous aider à peaufiner la configuration.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}