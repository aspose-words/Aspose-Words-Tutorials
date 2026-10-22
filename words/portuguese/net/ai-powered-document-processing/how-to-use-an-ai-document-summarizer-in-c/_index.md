---
category: general
date: 2026-09-21
description: Aprenda a criar um resumidor de documentos com IA em C# que gera resumos
  a partir de arquivos Word usando as APIs da OpenAI ou do Google.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- ai document summarizer
- ai powered summarization
- create summary from word
- summarize docx with ai
- summarize using google
language: pt
lastmod: 2026-09-21
og_description: O resumidor de documentos AI em C# permite criar resumos de arquivos
  Word rapidamente. Siga este guia para usar OpenAI ou Google para resumir com IA.
og_image_alt: Diagram showing the workflow of an ai document summarizer processing
  a Word file
og_title: Crie um resumidor de documentos AI em C# – guia passo a passo
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to build an ai document summarizer in C# that creates summary
    from Word files using OpenAI or Google APIs.
  headline: How to use an ai document summarizer in C#
  type: TechArticle
- description: Learn how to build an ai document summarizer in C# that creates summary
    from Word files using OpenAI or Google APIs.
  name: How to use an ai document summarizer in C#
  steps:
  - name: Provider implementation details
    text: '```csharp static class DocumentSummarizer { public static string Summarize(string
      text, SummarizerProvider provider, int maxSentences = 5) { return provider switch
      { SummarizerProvider.OpenAI => SummarizeWithOpenAI(text, maxSentences), SummarizerProvider.Google
      => SummarizeWithGoogle(text, maxSenten'
  - name: Handling token limits and large documents
    text: If the source document exceeds the model’s token quota, split it into paragraphs
      and summarize each chunk separately, then combine the chunk summaries. This
      ensures you never hit the 8 k‑token limit for most models.
  - name: Expected output
    text: '``` Summary: The report highlights a 12% revenue increase driven by new
      product launches. Customer churn dropped to 3% after the recent support improvements.
      Marketing spend rose by 8% but delivered a 15% ROI. The upcoming quarter will
      focus on expanding into APAC markets. Overall, the company is on'
  type: HowTo
tags:
- AI
- C#
- Document Processing
title: Como usar um resumidor de documentos de IA em C#
url: /pt/net/ai-powered-document-processing/how-to-use-an-ai-document-summarizer-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como usar um resumidor de documentos AI em C#

Se você precisa de um **resumidor de documentos AI** para arquivos .docx, este guia mostra como criar um resumo a partir do Word usando C#. Você verá um exemplo completo e executável que funciona tanto com OpenAI quanto com Google, oferecendo uma solução de **resumação alimentada por IA** em minutos.

O tutorial cobre tudo, desde a configuração do projeto até o tratamento de casos extremos, para que você possa **resumir docx com IA** em suas próprias aplicações com confiança. Nenhum script externo necessário — apenas alguns pacotes NuGet e um pequeno trecho de código.

## O que você precisará

- .NET 6.0 ou superior (o código também funciona em .NET Core 3.1+)
- Uma chave de API da OpenAI **ou** uma chave do Google Cloud Vertex AI
- O pacote NuGet `DocX` para leitura de arquivos Word
- O pacote NuGet `OpenAI` ou `Google.Cloud.AIPlatform.V1` para o provedor escolhido
- Um ambiente de desenvolvimento como Visual Studio 2022 ou VS Code

## Etapa 1: Configurar o ambiente do resumidor de documentos AI

Primeiro, crie um novo projeto de console e adicione os pacotes necessários:

```bash
dotnet new console -n AiSummarizerDemo
cd AiSummarizerDemo
dotnet add package DocX --version 1.0.0
dotnet add package OpenAI --version 2.5.0   # for OpenAI
dotnet add package Google.Cloud.AIPlatform.V1 --version 2.6.0   # for Google
```

> **Dica profissional:** Mantenha suas chaves de API em variáveis de ambiente (`OPENAI_API_KEY`, `GOOGLE_APPLICATION_CREDENTIALS`) em vez de codificá‑las diretamente.

## Etapa 2: Carregar um documento Word para **criar resumo a partir do Word**

A primeira linha funcional lê o arquivo `.docx` de origem. Usando `DocX` extraímos o texto puro, que o modelo de IA resumirá posteriormente.

```csharp
using System;
using System.IO;
using Xceed.Words.NET;   // DocX namespace

// Load the source document you want to summarize
Document document = Document.Load("input.docx");

// Extract raw text for the summarizer
string rawText = document.Text;
```

> **Por que esta etapa importa:** Modelos de IA funcionam melhor com texto limpo e linear. Remover a formatação evita surpresas com limites de tokens e melhora a relevância do resumo.

## Etapa 3: Escolher um provedor de **resumização alimentada por IA**

Você pode alternar entre o GPT‑4 da OpenAI ou o modelo PaLM do Google definindo o enum `SummarizerProvider`. O enum abstrai a lógica específica de cada provedor.

```csharp
enum SummarizerProvider
{
    OpenAI,
    Google
}

// Choose the provider (replace with your preference)
SummarizerProvider provider = SummarizerProvider.OpenAI; // or SummarizerProvider.Google
```

### Detalhes da implementação do provedor

```csharp
static class DocumentSummarizer
{
    public static string Summarize(string text, SummarizerProvider provider, int maxSentences = 5)
    {
        return provider switch
        {
            SummarizerProvider.OpenAI => SummarizeWithOpenAI(text, maxSentences),
            SummarizerProvider.Google => SummarizeWithGoogle(text, maxSentences),
            _ => throw new NotSupportedException("Unsupported summarizer provider.")
        };
    }

    private static string SummarizeWithOpenAI(string text, int maxSentences)
    {
        var apiKey = Environment.GetEnvironmentVariable("OPENAI_API_KEY")
                     ?? throw new InvalidOperationException("OpenAI API key missing.");
        var client = new OpenAIClient(apiKey);
        var request = new ChatRequest
        {
            Model = "gpt-4o-mini",
            Messages =
            {
                new ChatMessage(ChatMessageRole.System,
                    "You are a helpful assistant that creates concise summaries."),
                new ChatMessage(ChatMessageRole.User,
                    $"Summarize the following text in no more than {maxSentences} sentences:\n\n{text}")
            }
        };
        var response = client.ChatEndpoint.GetCompletionAsync(request).Result;
        return response.FirstChoice.Message.Content.Trim();
    }

    private static string SummarizeWithGoogle(string text, int maxSentences)
    {
        var client = new PredictionServiceClientBuilder
        {
            // Google credentials are read from GOOGLE_APPLICATION_CREDENTIALS env var
        }.Build();

        var request = new PredictRequest
        {
            // The model name depends on your Vertex AI deployment
            Endpoint = "projects/YOUR_PROJECT/locations/us-central1/publishers/google/models/text-bison",
            Instances = { new Value { StringValue = $"Summarize in {maxSentences} sentences: {text}" } }
        };

        var response = client.Predict(request);
        return response.Predictions[0].StringValue.Trim();
    }
}
```

> **Por que abstraímos o provedor:** Esse padrão permite que você **resuma usando Google** ou OpenAI sem mudar o código que faz a chamada — ótimo para testes ou troca de provedores futuramente.

## Etapa 4: Gerar um resumo conciso – **resumir docx com IA**

Agora chame o método auxiliar, limitando a saída a cinco frases (ajustável via `maxSentences`).

```csharp
// Generate a concise summary with a maximum of 5 sentences
string summary = DocumentSummarizer.Summarize(rawText, provider, maxSentences: 5);
```

### Lidando com limites de tokens e documentos grandes

Se o documento de origem exceder a cota de tokens do modelo, divida‑o em parágrafos e resuma cada trecho separadamente, depois combine os resumos dos trechos. Isso garante que você nunca atinja o limite de 8 k tokens na maioria dos modelos.

```csharp
static string SummarizeLargeText(string fullText, SummarizerProvider provider, int maxSentences)
{
    const int chunkSize = 2000; // approximate token count
    var chunks = fullText
        .Split(new[] { "\n\n" }, StringSplitOptions.RemoveEmptyEntries)
        .Select(p => p.Trim())
        .Where(p => p.Length > 0)
        .ToList();

    var partialSummaries = new List<string>();
    var sb = new System.Text.StringBuilder();

    foreach (var paragraph in chunks)
    {
        sb.Append(paragraph);
        if (sb.Length > chunkSize)
        {
            partialSummaries.Add(Summarize(sb.ToString(), provider, maxSentences));
            sb.Clear();
        }
    }

    if (sb.Length > 0)
        partialSummaries.Add(Summarize(sb.ToString(), provider, maxSentences));

    // Final pass to merge chunk summaries
    return Summarize(string.Join(" ", partialSummaries), provider, maxSentences);
}
```

## Etapa 5: Exibir o resumo resultante

Por fim, escreva o resumo no console ou armazene‑o onde precisar.

```csharp
// Display the resulting summary
Console.WriteLine("Summary:\n" + summary);
```

### Saída esperada

```
Summary:
The report highlights a 12% revenue increase driven by new product launches. Customer churn dropped to 3% after the recent support improvements. Marketing spend rose by 8% but delivered a 15% ROI. The upcoming quarter will focus on expanding into APAC markets. Overall, the company is on track to exceed its annual targets.
```

A formulação exata varia conforme o provedor de IA, mas a estrutura (≤ 5 frases) permanece consistente.

## Programa completo executável

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Xceed.Words.NET;               // DocX
using OpenAI;                       // OpenAI SDK
using OpenAI.Chat;                  // Chat classes
using Google.Cloud.AIPlatform.V1;   // Google Vertex AI SDK
using Google.Protobuf;              // Value type

enum SummarizerProvider { OpenAI, Google }

static class DocumentSummarizer
{
    public static string Summarize(string text, SummarizerProvider provider, int maxSentences = 5)
        => provider switch
        {
            SummarizerProvider.OpenAI => SummarizeWithOpenAI(text, maxSentences),
            SummarizerProvider.Google => SummarizeWithGoogle(text, maxSentences),
            _ => throw new NotSupportedException("Unsupported provider.")
        };

    private static string SummarizeWithOpenAI(string text, int maxSentences)
    {
        var apiKey = Environment.GetEnvironmentVariable("OPENAI_API_KEY")
                     ?? throw new InvalidOperationException("OpenAI API key missing.");
        var client = new OpenAIClient(apiKey);
        var request = new ChatRequest
        {
            Model = "gpt-4o-mini",
            Messages =
            {
                new ChatMessage(ChatMessageRole.System,
                    "You are a helpful assistant that creates concise summaries."),
                new ChatMessage(ChatMessageRole.User,
                    $"Summarize the following text in no more than {maxSentences} sentences:\n\n{text}")
            }
        };
        var response = client.ChatEndpoint.GetCompletionAsync(request).Result;
        return response.FirstChoice.Message.Content.Trim();
    }

    private static string SummarizeWithGoogle(string text, int maxSentences)
    {
        var client = new PredictionServiceClientBuilder().Build();
        var request = new PredictRequest
        {
            Endpoint = "projects/YOUR_PROJECT/locations/us-central1/publishers/google/models/text-bison",
            Instances = { new Value { StringValue = $"Summarize in {maxSentences} sentences: {text}" } }
        };
        var response = client.Predict(request);
        return response.Predictions[0].StringValue.Trim();
    }
}

class Program
{
    static void Main()
    {
        // Step 1: Load the source document you want to summarize
        var doc = Document.Load("input.docx");
        string rawText = doc.Text;

        // Step 2: Choose the AI provider for summarization (OpenAI or Google)
        SummarizerProvider provider = SummarizerProvider.OpenAI; // or SummarizerProvider.Google

        // Step 3: Generate a concise summary with a maximum of 5 sentences
        string summary = DocumentSummarizer.Summarize(rawText, provider, maxSentences: 5);

        // Step 4: Display the resulting summary
        Console.WriteLine("Summary:\n" + summary);
    }
}
```

Salve o arquivo como `Program.cs`, coloque um `


## O que você deve aprender a seguir?


Os tutoriais a seguir abordam tópicos intimamente relacionados que expandem as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código totalmente funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Resumir documento Word em C# com Aspose.Words API – Guia completo com IA](/words/english/net/ai-powered-document-processing/summarize-word-document-in-c-complete-ai-powered-guide/)
- [Criar novo documento Word](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Criar e estilizar um documento Word no Aspose.Words para .NET](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}