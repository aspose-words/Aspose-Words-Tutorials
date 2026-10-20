---
category: general
date: 2026-06-24
description: Tutoriel LLM local qui montre comment appeler un LLM local, charger un
  document Word et effectuer une vérification grammaticale à l'aide d'une vérification
  grammaticale IA en C#.
draft: false
keywords:
- local llm tutorial
- run grammar check
- ai grammar check
- call local llm
- load word document
language: fr
og_description: Le tutoriel LLM local explique étape par étape comment appeler un
  LLM local, charger un document Word et effectuer une vérification grammaticale IA
  en C#.
og_title: Tutoriel LLM local – Appeler un LLM local et lancer une vérification grammaticale
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: Local LLM tutorial that shows you how to call a local LLM, load a Word
    document and run grammar check using AI grammar check in C#.
  headline: Local LLM Tutorial – How to Call a Local LLM and Run Grammar Check
  type: TechArticle
- description: Local LLM tutorial that shows you how to call a local LLM, load a Word
    document and run grammar check using AI grammar check in C#.
  name: Local LLM Tutorial – How to Call a Local LLM and Run Grammar Check
  steps:
  - name: How to Run
    text: 1. Open a terminal in the project folder. 2. Run `dotnet run`. 3. Watch
      the console print the corrected text.
  - name: Can I use a different LLM brand?
    text: Absolutely. As long as the server respects the OpenAI v1 API schema, just
      change `Endpoint` and pick the corresponding `AiModelType` enum value (e.g.,
      `AiModelType.Llama2`). The rest of the code stays identical.
  - name: What if my document is huge (10 MB+)?
    text: Large payloads can exceed the default request size of many servers. Split
      the document into sections and call `CheckGrammar` per section, then concatenate
      the results. This also reduces the chance of a timeout.
  - name: How do I write the corrected output back to a `.docx` file?
    text: 'The `Document` class usually provides a `Save(string path, string content)`
      method. After you get `result.CorrectedText`, call:'
  - name: Is the dummy API key a security risk?
    text: No. The key is ignored by self‑hosted endpoints, but some SDKs enforce a
      non‑null string. Using a placeholder like `"dummy"` satisfies the SDK without
      exposing any secrets.
  type: HowTo
tags:
- LLM
- C#
- GrammarCheck
- AI
title: Tutoriel LLM local – Comment appeler un LLM local et effectuer une vérification
  grammaticale
url: /fr/net/ai-powered-document-processing/local-llm-tutorial-how-to-call-a-local-llm-and-run-grammar-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tutoriel LLM local – Appeler un LLM local et effectuer une vérification grammaticale

Vous êtes‑vous déjà demandé comment **exécuter une vérification grammaticale** sur un fichier Word sans rien envoyer dans le cloud ? Dans ce **tutoriel llm local**, nous allons connecter un modèle de langage de grande taille auto‑hébergé, charger un fichier `.docx`, et laisser l'IA nettoyer le texte. Pas de clés API, pas de trafic externe—juste votre propre machine qui fait le travail lourd.

Nous passerons en revue chaque ligne de code, expliquerons pourquoi chaque élément est important, et même vous montrerons comment gérer les pièges habituels (comme les fichiers manquants ou un point de terminaison inaccessible). À la fin, vous disposerez d’une application console C# prête à l’emploi qui effectue une **vérification grammaticale IA** en utilisant un modèle hébergé localement.

> **Ce que vous obtiendrez :** un programme complet et exécutable, une explication claire de chaque étape, et des conseils pour faire évoluer la solution vers des documents plus volumineux ou différents fournisseurs de LLM.

![diagramme du tutoriel llm local](https://example.com/local-llm-tutorial-diagram.png "Diagramme illustrant le flux du tutoriel llm local")

## Prérequis

- .NET 6.0 SDK ou version ultérieure (vous pouvez le télécharger depuis le site de Microsoft)
- Un serveur LLM fonctionnant localement exposant un point de terminaison compatible OpenAI (par ex., Ollama, LM Studio, ou un wrapper FastAPI personnalisé)
- Le package NuGet `AiGrammar` (ou toute bibliothèque fournissant les classes `LocalLargeLanguageModel`, `Document` et `AiModelType`)
- Un document Word d’exemple (`input.docx`) placé dans un dossier que vous référencerez plus tard

C’est tout—aucune information d’identification cloud supplémentaire requise.

## Étape 1 : Tutoriel LLM local – Configurer le point de terminaison

La première chose dont nous avons besoin est un objet **call local llm** qui sait où envoyer ses requêtes. Pensez‑y comme le numéro de téléphone que vous composez avant de pouvoir parler.

```csharp
using System;
using AiGrammar;   // Hypothetical library containing the LLM helpers

// Step 1: Configure a local large language model (LLM) endpoint
var llm = new LocalLargeLanguageModel
{
    Endpoint = "http://localhost:8000/v1",
    ApiKey = "dummy"   // Not required for self‑hosted models, but the property is mandatory
};
```

**Pourquoi c’est important :**  
La plupart des SDK LLM attendent un point de terminaison HTTP qui respecte le contrat de l’API OpenAI. En pointant `Endpoint` vers `http://localhost:8000/v1`, nous indiquons à la bibliothèque d’**appeler le LLM local** au lieu de contacter les serveurs d’OpenAI. La clé API factice n’est qu’un espace réservé—certains clients refusent une valeur nulle, donc nous lui fournissons quelque chose d’inoffensif.

> **Astuce :** Si vous exécutez le LLM derrière un reverse proxy, définissez `Endpoint` sur l’URL du proxy et laissez le proxy gérer la terminaison TLS. Cela garde votre application console simple et sécurisée.

## Étape 2 : Charger le document Word pour la vérification grammaticale

Maintenant que le modèle est accessible, nous devons **charger le document Word** en mémoire. La classe `Document` abstrait le parsing du `.docx` pour nous.

```csharp
// Step 2: Load the document you want to check
var docPath = @"C:\Projects\GrammarDemo\YOUR_DIRECTORY\input.docx";
if (!System.IO.File.Exists(docPath))
{
    Console.Error.WriteLine($"Error: The file '{docPath}' does not exist.");
    return;
}

var doc = new Document(docPath);
```

**Pourquoi c’est important :**  
Alimenter directement un fichier binaire `.docx` à un LLM le perturberait. L’assistant `Document` extrait le texte brut tout en préservant les sauts de paragraphe, ce qui fournit à la **vérification grammaticale IA** une entrée propre. La vérification d’existence empêche une `FileNotFoundException` désagréable qui ferait planter l’application autrement.

## Étape 3 : Exécuter la vérification grammaticale avec le LLM

Voici le cœur du tutoriel : nous demandons au modèle local de relire le texte. La méthode `CheckGrammar` masque la plomberie HTTP et renvoie un objet résultat.

```csharp
// Step 3: Run the grammar‑check operation using the LLM
var result = doc.CheckGrammar(
    llm,
    AiModelType.Gpt4   // You can swap this for any model supported by AiModelType
);
```

**Pourquoi c’est important :**  
`AiModelType.Gpt4` n’est qu’une étiquette qui indique au service distant quel modèle de prompt utiliser. Si vous avez un modèle plus petit (par ex., `Llama2`), remplacez‑le en conséquence. La bibliothèque sérialise le texte du document, l’envoie à `http://localhost:8000/v1/completions`, et analyse la sortie corrigée.

> **Cas limite :** Si le LLM dépasse le délai, `CheckGrammar` lève une `TimeoutException`. Enveloppez l’appel dans un bloc `try/catch` si vous prévoyez de gros documents ou un serveur chargé.

## Étape 4 : Afficher le texte corrigé

Enfin, nous affichons la version nettoyée. Dans une application réelle, vous pourriez l’écrire dans un nouveau fichier `.docx`, mais pour ce tutoriel un affichage console suffit.

```csharp
// Step 4: Output the corrected text
Console.WriteLine("=== Corrected Text ===");
Console.WriteLine(result.CorrectedText);
```

**Sortie attendue** (en supposant que le fichier original contenait quelques erreurs délibérées) :

```
=== Corrected Text ===
The quick brown fox jumps over the lazy dog. 
She doesn't like apples, but she loves oranges.
```

Si le LLM ne trouve aucune erreur, la sortie sera identique à l’entrée, ce qui reste un signal utile.

## Exemple complet fonctionnel

En rassemblant tout, voici le programme complet que vous pouvez copier‑coller dans un nouveau projet console :

```csharp
using System;
using AiGrammar;   // Replace with the actual namespace of your grammar library

namespace LocalLlmGrammarDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Configure the local LLM endpoint
            var llm = new LocalLargeLanguageModel
            {
                Endpoint = "http://localhost:8000/v1",
                ApiKey = "dummy"
            };

            // Path to the Word document you want to check
            var docPath = @"C:\Projects\GrammarDemo\YOUR_DIRECTORY\input.docx";

            // Verify the file exists before proceeding
            if (!System.IO.File.Exists(docPath))
            {
                Console.Error.WriteLine($"Error: The file '{docPath}' does not exist.");
                return;
            }

            // Load the document (this also extracts plain text)
            var doc = new Document(docPath);

            // Perform the AI grammar check using the local LLM
            GrammarCheckResult result;
            try
            {
                result = doc.CheckGrammar(llm, AiModelType.Gpt4);
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Grammar check failed: {ex.Message}");
                return;
            }

            // Show the corrected text
            Console.WriteLine("=== Corrected Text ===");
            Console.WriteLine(result.CorrectedText);
        }
    }
}
```

### Comment exécuter

1. Ouvrez un terminal dans le dossier du projet.  
2. Exécutez `dotnet run`.  
3. Regardez la console afficher le texte corrigé.

C’est l’ensemble du **tutoriel llm local** en moins de 100 lignes de code.

## Questions fréquemment posées (FAQ)

### Puis‑je utiliser une autre marque de LLM ?

Absolument. Tant que le serveur respecte le schéma de l’API OpenAI v1, il suffit de changer `Endpoint` et de choisir la valeur d’énumération `AiModelType` correspondante (par ex., `AiModelType.Llama2`). Le reste du code reste identique.

### Que faire si mon document est énorme (10 Mo+) ?

Les charges utiles importantes peuvent dépasser la taille de requête par défaut de nombreux serveurs. Divisez le document en sections et appelez `CheckGrammar` par section, puis concaténez les résultats. Cela réduit également le risque de dépassement de délai.

### Comment écrire la sortie corrigée dans un fichier `.docx` ?

La classe `Document` fournit généralement une méthode `Save(string path, string content)`. Après avoir obtenu `result.CorrectedText`, appelez :

```csharp
doc.Save(@"C:\Projects\GrammarDemo\output_corrected.docx", result.CorrectedText);
```

Vérifiez la documentation de la bibliothèque pour la signature exacte.

### La clé API factice représente‑t‑elle un risque de sécurité ?

Non. La clé est ignorée par les points de terminaison auto‑hébergés, mais certains SDK imposent une chaîne non nulle. Utiliser un espace réservé comme `"dummy"` satisfait le SDK sans exposer de secrets.

## Prochaines étapes et sujets connexes

- **Affinez votre LLM local** pour la grammaire spécifique à un domaine (par ex., rédaction juridique ou médicale).  
- **Exécutez un job batch** qui traite un dossier complet de fichiers Word—idéal pour les pipelines de publication.  
- Explorez les **réponses en streaming** si vous souhaitez des suggestions en temps réel pendant que l’utilisateur tape.  
- Combinez cela avec des **bibliothèques de vérification orthographique** pour une porte de qualité à double niveau.

Chacune de ces idées s’appuie sur les concepts de base abordés dans ce **tutoriel llm local**, vous retrouverez donc les mêmes schémas—**call local llm**, **load word document**, **run grammar check**, et **handle results**—qui se répètent tout au long.

*Bon codage ! Si vous rencontrez un problème, laissez un commentaire ci‑dessous et nous le résoudrons ensemble.*

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code fonctionnels complets avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités d’API supplémentaires et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Charger avec encodage dans un document Word](/words/english/net/programming-with-loadoptions/load-with-encoding/)
- [Charger un document Word chiffré](/words/english/net/programming-with-loadoptions/load-encrypted-document/)
- [Récupérer un DOCX corrompu – Ouvrir & charger un document Word](/words/english/python-net/document-operations/recover-corrupted-docx-open-load-word-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}