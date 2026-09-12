---
category: general
date: 2026-09-11
description: Apprenez à résumer du texte en C# en lisant la clé API, en appelant OpenAI
  et en générant un résumé concis d'un document Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to summarize text
- summarize word document
- read api key
- how to create summary
- how to call openai
language: fr
lastmod: 2026-09-11
og_description: Comment résumer du texte en C# ? Ce tutoriel vous montre comment lire
  la clé API, appeler OpenAI et créer un résumé d’un document Word.
og_image_alt: Diagram showing C# code flow that reads an API key, calls OpenAI, and
  outputs a document summary
og_title: Comment résumer du texte en C# avec OpenAI – guide étape par étape
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to summarize text in C# by reading the API key, calling OpenAI,
    and generating a concise summary of a Word document.
  headline: How to summarize text in C# using OpenAI
  type: TechArticle
- description: Learn how to summarize text in C# by reading the API key, calling OpenAI,
    and generating a concise summary of a Word document.
  name: How to summarize text in C# using OpenAI
  steps:
  - name: '**Cache the API key** – reading from the environment each call adds negligible
      overhead, but you can store it in a static readonly field if you call the summarizer
      many times in one process.'
    text: '**Cache the API key** – reading from the environment each call adds negligible
      overhead, but you can store it in a static readonly field if you call the summarizer
      many times in one process.'
  - name: '**Rate‑limit requests** – OpenAI enforces request limits; implement exponential
      back‑off if you hit `429 Too Many Requests`.'
    text: '**Rate‑limit requests** – OpenAI enforces request limits; implement exponential
      back‑off if you hit `429 Too Many Requests`.'
  - name: '**Sanitize input** – remove personally identifiable information before
      sending text to an external AI service.'
    text: '**Sanitize input** – remove personally identifiable information before
      sending text to an external AI service.'
  - name: '**Unit test the extraction logic** – mock `WordprocessingDocument` to verify
      `ExtractTextFromDocx` works with different document structures.'
    text: '**Unit test the extraction logic** – mock `WordprocessingDocument` to verify
      `ExtractTextFromDocx` works with different document structures.'
  type: HowTo
tags:
- C#
- OpenAI
- Document processing
- AI summarization
title: Comment résumer du texte en C# avec OpenAI
url: /fr/net/ai-powered-document-processing/how-to-summarize-text-in-c-using-openai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment résumer du texte en C# avec OpenAI

Si vous avez besoin de **comment résumer du texte** dans un fichier .docx, ce guide vous montre une solution complète, prête à l’emploi. Vous apprendrez comment lire la clé API depuis votre environnement, comment appeler OpenAI (ou Google) depuis C#, et comment créer un résumé concis d’un document Word.

Résumer un document Word est une exigence courante pour la génération de rapports, les résumés d’e‑mail ou l’extraction de bases de connaissances. À la fin de ce tutoriel, vous disposerez d’un programme en ligne de commande qui affiche un résumé de cinq phrases de n’importe quel fichier `.docx` que vous fournissez.

## Prérequis

- .NET 6.0 SDK ou version ultérieure (téléchargez‑le depuis [dotnet.microsoft.com](https://dotnet.microsoft.com/download))
- Une clé API OpenAI valide stockée dans une variable d’environnement nommée `OPENAI_API_KEY` (vous verrez **lire la clé API** en action)
- Le package NuGet `DocumentFormat.OpenXml` pour lire les fichiers `.docx`
- Le package NuGet `OpenAI` (ou `Google.AI` si vous préférez le fournisseur Google)

## Étape 1 : Configurer le projet et installer les dépendances

Créez un nouveau projet console et ajoutez les packages requis :

```bash
dotnet new console -n SummarizerDemo
cd SummarizerDemo
dotnet add package DocumentFormat.OpenXml
dotnet add package OpenAI
# Optional: dotnet add package Google.AI
```

> **Astuce pro :** Gardez votre `csproj` propre en regroupant les packages liés sous un `<ItemGroup>` si vous ajoutez plus tard d’autres dépendances.

## Étape 2 : Lire la clé API de façon sécurisée

Coder les secrets en dur est dangereux. Le tutoriel montre la bonne façon de **lire la clé API** depuis les variables d’environnement.

```csharp
using System;

/// <summary>
/// Retrieves the OpenAI API key from the environment.
/// Throws an exception if the variable is missing.
/// </summary>
static string GetOpenAIApiKey()
{
    var key = Environment.GetEnvironmentVariable("OPENAI_API_KEY");
    if (string.IsNullOrWhiteSpace(key))
    {
        throw new InvalidOperationException(
            "OPENAI_API_KEY environment variable not set. " +
            "Set it before running the program.");
    }
    return key;
}
```

## Étape 3 : Charger le document Word que vous souhaitez résumer

Le code ci‑dessous montre **comment résumer le contenu d’un document Word** en extrayant le texte brut de la structure OpenXML.

```csharp
using DocumentFormat.OpenXml.Packaging;
using DocumentFormat.OpenXml.Wordprocessing;

/// <summary>
/// Extracts raw text from a .docx file.
/// </summary>
static string ExtractTextFromDocx(string path)
{
    using var wordDoc = WordprocessingDocument.Open(path, false);
    var body = wordDoc.MainDocumentPart.Document.Body;
    return body.InnerText;
}
```

## Étape 4 : Construire une classe de résumé réutilisable

Cette classe encapsule **comment appeler openai** (ou Google) et implémente la logique **comment créer un résumé**. Elle vous permet également de changer de fournisseur avec une seule valeur d’énumération.

```csharp
using System.Threading.Tasks;
using OpenAI;
using OpenAI.Chat;

/// <summary>
/// Supported AI providers for summarization.
/// </summary>
enum SummarizerProvider { OpenAI, Google }

/// <summary>
/// Provides a method to summarize a document using the selected provider.
/// </summary>
static class DocumentSummarizer
{
    public static async Task<string> SummarizeAsync(
        string text,
        SummarizerProvider provider,
        int maxSentences = 5)
    {
        return provider switch
        {
            SummarizerProvider.OpenAI => await SummarizeWithOpenAIAsync(text, maxSentences),
            SummarizerProvider.Google => await SummarizeWithGoogleAsync(text, maxSentences),
            _ => throw new NotSupportedException($"Provider {provider} is not supported.")
        };
    }

    // ---------- OpenAI implementation ----------
    private static async Task<string> SummarizeWithOpenAIAsync(string text, int maxSentences)
    {
        var apiKey = GetOpenAIApiKey(); // re‑use the method from Step 2
        var client = new OpenAIClient(new OpenAIAuthentication(apiKey));

        var prompt = $"Summarize the following text in no more than {maxSentences} sentences:\n\n{text}";
        var chatRequest = new ChatRequest(new[] { new ChatMessage(ChatMessageRole.System, prompt) });

        var response = await client.ChatEndpoint.GetCompletionAsync(chatRequest);
        return response.FirstChoice.Message.Content.Trim();
    }

    // ---------- Google implementation (optional) ----------
    private static async Task<string> SummarizeWithGoogleAsync(string text, int maxSentences)
    {
        // Placeholder for Google AI call.
        // Replace with actual Google client code if you have the package.
        await Task.Yield();
        return "Google summarization not implemented in this demo.";
    }
}
```

### Pourquoi cette structure est importante

- **Séparation des responsabilités :** le chargement du document, la lecture de la clé API et l’appel au service d’IA sont isolés dans leurs propres méthodes. Cela rend le code plus facile à tester et à étendre.
- **Flexibilité du fournisseur :** en utilisant une énumération, vous pouvez basculer entre OpenAI et Google sans toucher au code appelant, répondant ainsi directement à **comment appeler openai** et **comment créer un résumé** de façon réutilisable.
- **Gestion des erreurs :** l’absence de clé API déclenche une exception claire, évitant les échecs silencieux.

## Étape 5 : Assembler le tout dans `Program.cs`

```csharp
using System;
using System.Threading.Tasks;

class Program
{
    static async Task Main(string[] args)
    {
        if (args.Length != 1)
        {
            Console.WriteLine("Usage: SummarizerDemo <path-to-docx>");
            return;
        }

        string docPath = args[0];

        // 1️⃣ Load the source document
        string rawText = ExtractTextFromDocx(docPath);

        // 2️⃣ Summarize the document using OpenAI (you can switch to Google)
        string summary = await DocumentSummarizer.SummarizeAsync(
            rawText,
            SummarizerProvider.OpenAI, // change to SummarizerProvider.Google if needed
            maxSentences: 5);

        // 3️⃣ Output the generated summary
        Console.WriteLine("Summary:");
        Console.WriteLine(summary);
    }

    // Include the helper methods from Steps 2‑4 here
    // (GetOpenAIApiKey, ExtractTextFromDocx, DocumentSummarizer, etc.)
}
```

### Sortie attendue

Exécution du programme avec un document d’exemple :

```bash
dotnet run -- "sample/input.docx"
```

pourrait produire :

```
Summary:
The report outlines quarterly sales growth, highlighting a 12% increase in the North American market. 
Key challenges include supply‑chain delays and rising material costs. 
Customer feedback indicates higher satisfaction with the new product line. 
Recommendations focus on expanding the digital sales channel and optimizing inventory levels. 
Overall, the company is positioned for continued growth in the next fiscal year.
```

## Étape 6 : Variations courantes et cas limites

| Situation | Ajustement recommandé |
|-----------|-----------------------|
| **Documents volumineux** ( > 10 KB ) | Divisez le texte en fragments, résumez chaque fragment, puis combinez les résultats. |
| **Contenu non‑anglais** | Indiquez la langue dans l’invite, par ex. : « Summarize the following French text … ». |
| **Fournisseur Google** | Remplacez l’appel `SummarizeWithOpenAIAsync` par le client API Google approprié ; conservez la même interface d’énumération. |
| **Longueur de résumé personnalisée** | Modifiez l’argument `maxSentences` lors de l’appel à `SummarizeAsync`. |
| **Clé API manquante** | La méthode `GetOpenAIApiKey` lève déjà une exception claire ; capturez‑la dans `Main` si vous souhaitez un message plus convivial. |

## Astuces pro pour la production

1. **Mettre en cache la clé API** – lire la variable d’environnement à chaque appel ajoute un surcoût négligeable, mais vous pouvez la stocker dans un champ `static readonly` si vous appelez le résumeur plusieurs fois dans le même processus.  
2. **Limiter le débit des requêtes** – OpenAI impose des limites ; implémentez un back‑off exponentiel si vous recevez `429 Too Many Requests`.  
3. **Assainir l’entrée** – supprimez les informations personnellement identifiables avant d’envoyer le texte à un service d’IA externe.  
4. **Tester l’extraction** – moquez `WordprocessingDocument` pour vérifier que `ExtractTextFromDocx` fonctionne avec différentes structures de documents.

## Conclusion

Vous savez maintenant **comment résumer du texte** en C# en lisant la clé API de façon sécurisée, en appelant OpenAI, et en générant un résumé concis d’un document Word. Le même modèle vous permet **comment appeler openai** avec d’autres fournisseurs, **comment créer un résumé** pour différents types de contenu, et de lire en toute sécurité les valeurs **lire la clé API** depuis l’environnement. Expérimentez avec des documents plus longs, d’autres fournisseurs ou des invites personnalisées pour adapter le résumé à votre domaine spécifique.

---


## Que devriez‑vous apprendre ensuite ?


Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications pas à pas pour vous aider à maîtriser des fonctionnalités d’API supplémentaires et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Résumer un document Word en C# avec l'API Aspose.Words – Guide complet alimenté par l'IA](/words/english/net/ai-powered-document-processing/summarize-word-document-in-c-complete-ai-powered-guide/)
- [comment créer un PDF à partir de Word – Guide complet C#](/words/english/net/basic-conversions/how-to-create-pdf-from-word-complete-c-guide/)
- [Document Word – Comment supprimer du contenu](/words/english/net/remove-content/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}