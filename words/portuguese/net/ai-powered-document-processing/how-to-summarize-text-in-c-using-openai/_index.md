---
category: general
date: 2026-09-11
description: Aprenda a resumir texto em C# lendo a chave da API, chamando a OpenAI
  e gerando um resumo conciso de um documento Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to summarize text
- summarize word document
- read api key
- how to create summary
- how to call openai
language: pt
lastmod: 2026-09-11
og_description: Como resumir texto em C#? Este tutorial mostra como ler a chave da
  API, chamar o OpenAI e criar um resumo de um documento Word.
og_image_alt: Diagram showing C# code flow that reads an API key, calls OpenAI, and
  outputs a document summary
og_title: Como resumir texto em C# com OpenAI – guia passo a passo
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
title: Como resumir texto em C# usando OpenAI
url: /pt/net/ai-powered-document-processing/how-to-summarize-text-in-c-using-openai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como resumir texto em C# usando OpenAI

Se você precisa **how to summarize text** em um arquivo .docx, este guia mostra uma solução completa, pronta‑para‑executar. Você aprenderá como ler a chave da API do seu ambiente, como chamar OpenAI (ou Google) a partir de C#, e como criar um resumo conciso de um documento Word.

Resumir um documento Word é uma necessidade comum para geração de relatórios, resumos de e‑mail ou extração de base de conhecimento. Ao final deste tutorial, você terá um programa de linha de comando que imprime um resumo de cinco frases de qualquer arquivo `.docx` que você fornecer.

## Pré-requisitos

- .NET 6.0 SDK ou posterior (download em [dotnet.microsoft.com](https://dotnet.microsoft.com/download))
- Uma chave de API OpenAI válida armazenada em uma variável de ambiente chamada `OPENAI_API_KEY` (você verá **read api key** em ação)
- O pacote NuGet `DocumentFormat.OpenXml` para leitura de arquivos `.docx`
- O pacote NuGet `OpenAI` (ou `Google.AI` se preferir o provedor Google)

## Etapa 1: Configurar o projeto e instalar dependências

Crie um novo projeto console e adicione os pacotes necessários:

```bash
dotnet new console -n SummarizerDemo
cd SummarizerDemo
dotnet add package DocumentFormat.OpenXml
dotnet add package OpenAI
# Optional: dotnet add package Google.AI
```

**Pro tip:** Mantenha seu `csproj` organizado agrupando pacotes relacionados sob um `<ItemGroup>` se você adicionar mais dependências posteriormente.

## Etapa 2: Ler a chave da API com segurança

Codificar segredos diretamente no código é inseguro. O tutorial demonstra a forma correta de **read api key** a partir de variáveis de ambiente.

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

## Etapa 3: Carregar o documento Word que você deseja resumir

O código abaixo mostra **how to summarize word document** o conteúdo extraindo texto simples da estrutura OpenXML.

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

## Etapa 4: Construir uma classe resumidora reutilizável

Esta classe encapsula **how to call openai** (ou Google) e implementa a lógica de **how to create summary**. Ela também permite trocar de provedor com um único valor enum.

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

### Por que esta estrutura importa

- **Separação de responsabilidades:** Carregar o documento, ler a chave da API e chamar o serviço de IA são isolados em seus próprios métodos. Isso torna o código mais fácil de testar e estender.
- **Flexibilidade de provedor:** Usando um enum, você pode alternar entre OpenAI e Google sem modificar o código de chamada, o que responde diretamente **how to call openai** e **how to create summary** de forma reutilizável.
- **Tratamento de erros:** Chaves de API ausentes lançam uma exceção clara, evitando falhas silenciosas.

## Etapa 5: Juntar tudo em `Program.cs`

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

### Saída esperada

Executando o programa com um documento de exemplo:

```bash
dotnet run -- "sample/input.docx"
```

pode produzir:

```
Summary:
The report outlines quarterly sales growth, highlighting a 12% increase in the North American market. 
Key challenges include supply‑chain delays and rising material costs. 
Customer feedback indicates higher satisfaction with the new product line. 
Recommendations focus on expanding the digital sales channel and optimizing inventory levels. 
Overall, the company is positioned for continued growth in the next fiscal year.
```

## Etapa 6: Variações comuns e casos de borda

| Situação | Ajuste recomendado |
|-----------|------------------------|
| **Documentos grandes** ( > 10 KB ) | Divida o texto em blocos e resuma cada bloco, depois combine os resultados. |
| **Conteúdo não‑inglês** | Passe a dica de idioma no prompt, por exemplo, “Summarize the following French text …”. |
| **Provedor Google** | Substitua a chamada `SummarizeWithOpenAIAsync` pelo cliente de API Google apropriado; mantenha a mesma interface enum. |
| **Comprimento de resumo personalizado** | Altere o argumento `maxSentences` ao chamar `SummarizeAsync`. |
| **Chave de API ausente** | O método `GetOpenAIApiKey` já lança uma exceção clara; capture-a em `Main` se desejar uma mensagem mais amigável. |

## Dicas profissionais para uso em produção

1. **Cache a chave da API** – ler a partir do ambiente a cada chamada adiciona uma sobrecarga insignificante, mas você pode armazená‑la em um campo static readonly se chamar o resumidor muitas vezes em um único processo.
2. **Limite a taxa de requisições** – o OpenAI impõe limites de requisição; implemente back‑off exponencial se receber `429 Too Many Requests`.
3. **Sanitize input** – remova informações pessoalmente identificáveis antes de enviar o texto a um serviço de IA externo.
4. **Teste unitário da lógica de extração** – simule `WordprocessingDocument` para verificar se `ExtractTextFromDocx` funciona com diferentes estruturas de documento.

## Conclusão

Agora você sabe **how to summarize text** em C# lendo a chave da API com segurança, chamando o OpenAI e gerando um resumo conciso de um documento Word. O mesmo padrão permite que você **how to call openai** com outros provedores, **how to create summary** para diferentes tipos de conteúdo, e leia **read api key** com segurança a partir do ambiente. Experimente documentos mais longos, diferentes provedores ou prompts personalizados para adaptar a sumarização ao seu domínio específico.

---


## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Resumir documento Word em C# com Aspose.Words API – Guia completo com IA](/words/english/net/ai-powered-document-processing/summarize-word-document-in-c-complete-ai-powered-guide/)
- [como criar pdf a partir de Word – Guia completo em C#](/words/english/net/basic-conversions/how-to-create-pdf-from-word-complete-c-guide/)
- [Documento Word - Como remover conteúdo](/words/english/net/remove-content/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}