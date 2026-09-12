---
category: general
date: 2026-09-11
description: Impara a riassumere il testo in C# leggendo la chiave API, chiamando
  OpenAI e generando un riassunto conciso di un documento Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to summarize text
- summarize word document
- read api key
- how to create summary
- how to call openai
language: it
lastmod: 2026-09-11
og_description: Come riassumere il testo in C#? Questo tutorial ti mostra come leggere
  la chiave API, chiamare OpenAI e creare un riassunto di un documento Word.
og_image_alt: Diagram showing C# code flow that reads an API key, calls OpenAI, and
  outputs a document summary
og_title: Come riassumere il testo in C# con OpenAI – guida passo passo
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
title: Come riassumere il testo in C# usando OpenAI
url: /it/net/ai-powered-document-processing/how-to-summarize-text-in-c-using-openai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come riassumere testo in C# usando OpenAI

Se hai bisogno di **come riassumere testo** in un file .docx, questa guida ti mostra una soluzione completa, pronta all'uso. Imparerai come leggere la chiave API dall'ambiente, come chiamare OpenAI (o Google) da C#, e come creare un riassunto conciso di un documento Word.

Riassumere un documento Word è una necessità comune per la generazione di report, digest email o estrazione di conoscenza da basi dati. Alla fine di questo tutorial avrai un programma da riga di comando che stampa un riassunto di cinque frasi di qualsiasi file `.docx` fornito.

## Prerequisiti

- .NET 6.0 SDK o successivo (scaricabile da [dotnet.microsoft.com](https://dotnet.microsoft.com/download))
- Una chiave API OpenAI valida memorizzata in una variabile d'ambiente chiamata `OPENAI_API_KEY` (vedrai **leggere la chiave API** in azione)
- Il pacchetto NuGet `DocumentFormat.OpenXml` per leggere file `.docx`
- Il pacchetto NuGet `OpenAI` (o `Google.AI` se preferisci il provider Google)

## Passo 1: Configurare il progetto e installare le dipendenze

Crea un nuovo progetto console e aggiungi i pacchetti richiesti:

```bash
dotnet new console -n SummarizerDemo
cd SummarizerDemo
dotnet add package DocumentFormat.OpenXml
dotnet add package OpenAI
# Optional: dotnet add package Google.AI
```

> **Suggerimento professionale:** Mantieni il tuo `csproj` ordinato raggruppando i pacchetti correlati sotto un `<ItemGroup>` se in seguito aggiungerai altre dipendenze.

## Passo 2: Leggere la chiave API in modo sicuro

Hard‑coding di segreti è pericoloso. Il tutorial dimostra il modo corretto per **leggere la chiave API** dalle variabili d'ambiente.

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

## Passo 3: Caricare il documento Word da riassumere

Il codice qui sotto mostra **come riassumere il contenuto di un documento Word** estraendo il testo semplice dalla struttura OpenXML.

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

## Passo 4: Costruire una classe riassuntore riutilizzabile

Questa classe incapsula **come chiamare openai** (o Google) e implementa la logica di **come creare un riassunto**. Consente inoltre di cambiare provider con un singolo valore enum.

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

### Perché questa struttura è importante

- **Separazione delle responsabilità:** il caricamento del documento, la lettura della chiave API e la chiamata al servizio AI sono isolate in metodi propri. Questo rende il codice più facile da testare ed estendere.
- **Flessibilità del provider:** usando un enum puoi passare da OpenAI a Google senza modificare il codice chiamante, rispondendo direttamente a **come chiamare openai** e **come creare un riassunto** in modo riutilizzabile.
- **Gestione degli errori:** le chiavi API mancanti generano un'eccezione chiara, evitando fallimenti silenziosi.

## Passo 5: Mettere tutto insieme in `Program.cs`

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

### Output previsto

Eseguendo il programma con un documento di esempio:

```bash
dotnet run -- "sample/input.docx"
```

potrebbe produrre:

```
Summary:
The report outlines quarterly sales growth, highlighting a 12% increase in the North American market. 
Key challenges include supply‑chain delays and rising material costs. 
Customer feedback indicates higher satisfaction with the new product line. 
Recommendations focus on expanding the digital sales channel and optimizing inventory levels. 
Overall, the company is positioned for continued growth in the next fiscal year.
```

## Passo 6: Variazioni comuni e casi limite

| Situazione | Adeguamento consigliato |
|------------|--------------------------|
| **Documenti grandi** ( > 10 KB ) | Dividi il testo in blocchi e riassumi ciascun blocco, poi combina i risultati. |
| **Contenuto non‑inglese** | Inserisci l'indicazione della lingua nel prompt, ad es. “Riassumi il seguente testo francese …”. |
| **Provider Google** | Sostituisci la chiamata `SummarizeWithOpenAIAsync` con il client API Google appropriato; mantieni la stessa interfaccia enum. |
| **Lunghezza del riassunto personalizzata** | Modifica l'argomento `maxSentences` quando chiami `SummarizeAsync`. |
| **Chiave API mancante** | Il metodo `GetOpenAIApiKey` genera già un'eccezione chiara; catturala in `Main` se desideri un messaggio più amichevole. |

## Suggerimenti professionali per l'uso in produzione

1. **Cache della chiave API** – leggere dalla variabile d'ambiente ad ogni chiamata aggiunge un overhead trascurabile, ma puoi memorizzarla in un campo static readonly se chiami il riassuntore più volte nello stesso processo.
2. **Rate‑limit delle richieste** – OpenAI impone limiti di richiesta; implementa un back‑off esponenziale se ricevi `429 Too Many Requests`.
3. **Sanitizzare l'input** – rimuovi informazioni personali identificabili prima di inviare il testo a un servizio AI esterno.
4. **Test unitari della logica di estrazione** – simula `WordprocessingDocument` per verificare che `ExtractTextFromDocx` funzioni con diverse strutture di documento.

## Conclusione

Ora sai **come riassumere testo** in C# leggendo in modo sicuro la chiave API, chiamando OpenAI e generando un riassunto conciso di un documento Word. Lo stesso schema ti permette di **come chiamare openai** con altri provider, **come creare un riassunto** per diversi tipi di contenuto, e di leggere in sicurezza valori **leggere la chiave API** dall'ambiente. Sperimenta con documenti più lunghi, provider diversi o prompt personalizzati per adattare il riassunto al tuo dominio specifico.

---


## Cosa dovresti imparare dopo?


I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Riassumere documento Word in C# con Aspose.Words API – Guida completa AI‑Powered](/words/english/net/ai-powered-document-processing/summarize-word-document-in-c-complete-ai-powered-guide/)
- [come creare pdf da Word – Guida completa C#](/words/english/net/basic-conversions/how-to-create-pdf-from-word-complete-c-guide/)
- [Documento Word - Come rimuovere contenuto](/words/english/net/remove-content/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}