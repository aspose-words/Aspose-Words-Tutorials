---
category: general
date: 2026-11-15
description: Aprenda a traduzir texto com o Google em C#. Este tutorial mostra um
  exemplo do Google Translate, lidando com múltiplos idiomas e as melhores práticas.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to translate text
- translate text with google
- google translate example
- google translate tutorial
- translate multiple languages
language: pt
lastmod: 2026-11-15
og_description: Como traduzir texto com o Google em C# usando um exemplo completo
  do Google Translate. Siga este tutorial para traduzir vários idiomas com segurança.
og_image_alt: Console output showing translated text from English to French using
  Google Translate API
og_title: Como traduzir texto com a API do Google Translate em C# – tutorial rápido
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to translate text with Google in C#. This tutorial shows
    a Google Translate example, handling multiple languages and best practices.
  headline: How to translate text with Google Translate API in C# – step‑by‑step guide
  type: TechArticle
- description: Learn how to translate text with Google in C#. This tutorial shows
    a Google Translate example, handling multiple languages and best practices.
  name: How to translate text with Google Translate API in C# – step‑by‑step guide
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 SDK or later (the code compiles with .NET Core and .NET Framework).
      * A Google Cloud account with the **Cloud Translation API** enabled. * Basic
      familiarity with C# and console applications.'
  - name: Handling language detection
    text: 'If you need to know the source language, the response object contains `DetectedSourceLanguage`:'
  - name: Translating large documents
    text: The API supports up to 30 KB per request. For larger texts, split the content
      into chunks, translate each chunk, and then concatenate the results. Keep sentence
      boundaries intact to avoid awkward phrasing.
  - name: Rate‑limiting and quotas
    text: Google enforces per‑minute request limits. Implement a retry policy with
      exponential back‑off to respect quota limits and avoid `429 Too Many Requests`
      errors.
  type: HowTo
- questions:
  - answer: Yes. Use the `Format` parameter (`"text"` or `"html"`) when calling `TranslateText`.
      The SDK exposes this via the `TranslateText` overload that accepts a `TranslateTextRequest`.
    question: Can I translate a whole HTML page?
  - answer: The API returns an error. Validate language codes against the list returned
      by `client.ListSupportedLanguages()` before making a request.
    question: What if a language isn’t supported?
  - answer: 'Google bills per character translated. Estimate costs using the pricing
      page and consider caching frequent translations. --- ## Conclusion You now know
      **how to translate text** in C# using the official Google Translate API. The
      tutorial covered a **Google translate example**, demonstrated **transla'
    question: Does the API charge per character?
  type: FAQPage
tags:
- Google Cloud
- C#
- Translation API
title: Como traduzir texto com a API do Google Translate em C# – guia passo a passo
url: /pt/net/ai-powered-document-processing/how-to-translate-text-with-google-translate-api-in-c-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como traduzir texto com a API Google Translate em C# – guia passo a passo

Se você precisa **como traduzir texto** em uma aplicação .NET, a Google Cloud Translation API oferece uma solução confiável e independente de idioma. Neste tutorial você verá um **exemplo do Google Translate** que traduz uma string simples, expande para **traduzir múltiplos idiomas**, e segue as melhores práticas para chaves de API e tratamento de erros.

Você sairá com um programa de console C# pronto‑para‑executar, uma compreensão clara de **traduzir texto com o Google**, e a confiança para adaptar o código a projetos maiores.

## O que este tutorial cobre

* Configurar um projeto Google Cloud e obter uma chave de API.  
* Instalar o pacote NuGet `Google.Cloud.Translation.V2`.  
* Escrever código limpo e reutilizável que **como traduzir texto** usando o SDK oficial.  
* Estender a solução para **traduzir múltiplos idiomas** em uma única chamada.  
* Armadilhas comuns e dicas para implementações de nível produção.

### Pré-requisitos

* .NET 6.0 SDK ou posterior (o código compila com .NET Core e .NET Framework).  
* Uma conta Google Cloud com a **Cloud Translation API** habilitada.  
* Familiaridade básica com C# e aplicações de console.  

---

## Etapa 1: Instalar a biblioteca cliente Google Cloud Translation

A biblioteca cliente oficial abstrai chamadas HTTP e gerencia a autenticação para você.

```bash
dotnet add package Google.Cloud.Translation.V2
```

Executar o comando adiciona o pacote `Google.Cloud.Translation.V2` ao seu projeto, fornecendo acesso à classe `TranslationClient` usada ao longo deste guia.

> **Por que esta etapa importa** – Usar o SDK evita a construção manual de requisições, reduz bugs e garante que você esteja alinhado com a versão mais recente da API do Google.

## Etapa 2: Criar um helper de tradução reutilizável

Encapsular a lógica de tradução em uma classe estática torna o código reutilizável e isola o manuseio da chave de API.

```csharp
using Google.Cloud.Translation.V2;
using System;

namespace GoogleTranslateDemo
{
    /// <summary>
    /// Provides simple methods to translate text using the Google Cloud Translation API.
    /// </summary>
    public static class Translator
    {
        /// <summary>
        /// Translates a single string into the specified target language.
        /// </summary>
        /// <param name="sourceText">The text you want to translate.</param>
        /// <param name="targetLanguage">ISO‑639‑1 language code (e.g., "fr" for French).</param>
        /// <param name="apiKey">Your Google Cloud API key.</param>
        /// <returns>The translated text.</returns>
        public static string Translate(string sourceText, string targetLanguage, string apiKey)
        {
            // Initialise the client with the provided API key.
            var client = TranslationClient.CreateFromApiKey(apiKey);

            // Perform the translation. The API automatically detects the source language.
            var response = client.TranslateText(sourceText, targetLanguage);
            return response.TranslatedText;
        }

        /// <summary>
        /// Translates a collection of texts into several languages at once.
        /// </summary>
        /// <param name="sourceTexts">Array of strings to translate.</param>
        /// <param name="targetLanguages">Array of ISO‑639‑1 codes (e.g., "es", "de").</param>
        /// <param name="apiKey">Your Google Cloud API key.</param>
        /// <returns>A dictionary keyed by language code containing the translated results.</returns>
        public static Dictionary<string, string[]> TranslateMultiple(string[] sourceTexts,
                                                                    string[] targetLanguages,
                                                                    string apiKey)
        {
            var client = TranslationClient.CreateFromApiKey(apiKey);
            var result = new Dictionary<string, string[]>();

            foreach (var lang in targetLanguages)
            {
                var translations = client.TranslateTexts(sourceTexts, lang);
                result[lang] = translations.Select(t => t.TranslatedText).ToArray();
            }

            return result;
        }
    }
}
```

> **Por que retornamos um dicionário** – Quando você precisa **traduzir múltiplos idiomas**, organizar os resultados por código de idioma torna o processamento subsequente mais simples.

## Etapa 3: Construir a aplicação de console que usa o helper

Abaixo está um `Program.cs` completo que demonstra tanto a tradução de um único texto quanto a tradução em lote.

```csharp
using System;
using GoogleTranslateDemo; // Namespace from the helper class

class Program
{
    static void Main()
    {
        // ---- Single translation (Google Translate example) ----
        string sourceText = "Hello, world!";
        string targetLanguage = "fr"; // French
        string apiKey = "YOUR_GOOGLE_API_KEY"; // Replace with your actual key

        try
        {
            string translated = Translator.Translate(sourceText, targetLanguage, apiKey);
            Console.WriteLine($"[Single] English → French: {translated}");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"Translation failed: {ex.Message}");
        }

        // ---- Translate multiple languages (translate multiple languages) ----
        string[] texts = { "Good morning", "How are you?" };
        string[] languages = { "es", "de", "ja" }; // Spanish, German, Japanese

        try
        {
            var batchResult = Translator.TranslateMultiple(texts, languages, apiKey);
            foreach (var kvp in batchResult)
            {
                Console.WriteLine($"\n[Batch] Language: {kvp.Key}");
                for (int i = 0; i < texts.Length; i++)
                {
                    Console.WriteLine($"  {texts[i]} → {kvp.Value[i]}");
                }
            }
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"Batch translation failed: {ex.Message}");
        }
    }
}
```

**Saída esperada no console**

```
[Single] English → French: Bonjour le monde!

[Batch] Language: es
  Good morning → Buenos días
  How are you? → ¿Cómo estás?

[Batch] Language: de
  Good morning → Guten Morgen
  How are you? → Wie geht es Ihnen?

[Batch] Language: ja
  Good morning → おはようございます
  How are you? → お元気ですか？
```

> **Por que os blocos try/catch?** – Erros de rede, limites de cota ou uma chave de API inválida geram exceções. Tratá‑las de forma elegante melhora a experiência do usuário e mantém sua aplicação estável.

## Etapa 4: Proteger sua chave de API

Inserir a chave de API diretamente no código, como mostrado acima, é aceitável para uma demonstração rápida, mas não para produção. Siga estas práticas:

* Armazene a chave em uma variável de ambiente (`GOOGLE_API_KEY`) e leia‑a em tempo de execução:
  ```csharp
  string apiKey = Environment.GetEnvironmentVariable("GOOGLE_API_KEY");
  ```
* Use **Google Application Default Credentials** em vez de uma chave de API ao executar no Google Cloud (App Engine, Cloud Run, etc.).
* Restrinja a chave à Translation API no console do Google Cloud e limite o uso a endereços IP ou referenciadores específicos.

## Etapa 5: Estender a solução para cenários reais

### Detectando o idioma

Se você precisar saber o idioma de origem, o objeto de resposta contém `DetectedSourceLanguage`:

```csharp
var response = client.TranslateText(sourceText, targetLanguage);
Console.WriteLine($"Detected source: {response.DetectedSourceLanguage}");
```

### Traduzindo documentos grandes

A API suporta até 30 KB por requisição. Para textos maiores, divida o conteúdo em blocos, traduza cada bloco e depois concatene os resultados. Mantenha os limites de frases intactos para evitar construções estranhas.

### Limitação de taxa e cotas

O Google impõe limites de requisições por minuto. Implemente uma política de retry com back‑off exponencial para respeitar os limites de cota e evitar erros `429 Too Many Requests`.

```csharp
// Example using Polly (install Polly via NuGet)
var policy = Policy
    .Handle<Google.Api.Gax.Rpc.ResourceExhaustedException>()
    .WaitAndRetryAsync(3, attempt => TimeSpan.FromSeconds(Math.Pow(2, attempt)));

await policy.ExecuteAsync(() => client.TranslateTextAsync(...));
```

---

## Perguntas comuns e casos extremos

**Q: Posso traduzir uma página HTML inteira?**  
A: Sim. Use o parâmetro `Format` (`"text"` ou `"html"`) ao chamar `TranslateText`. O SDK expõe isso via a sobrecarga de `TranslateText` que aceita um `TranslateTextRequest`.

**Q: E se um idioma não for suportado?**  
A: A API retorna um erro. Valide os códigos de idioma contra a lista retornada por `client.ListSupportedLanguages()` antes de fazer a requisição.

**Q: A API cobra por caractere?**  
A: O Google cobra por caractere traduzido. Estime os custos usando a página de preços e considere armazenar em cache traduções frequentes.

---

## Conclusão

Agora você sabe **como traduzir texto** em C# usando a API oficial do Google Translate. O tutorial abordou um **exemplo do Google translate**, demonstrou **traduzir múltiplos idiomas**, e destacou práticas prontas para produção, como segurança da chave de API e tratamento de erros. Reutilizando o helper `Translator`, você pode integrar tradução em qualquer serviço .NET, aplicativo desktop ou microsserviço.

**Próximos passos**

* Explore o **tutorial do Google Translate** para recursos avançados como glossários e modelos personalizados.  
* Combine este código com ASP.NET Core para criar uma API web multilíngue.  
* Experimente a tradução em lote de arquivos CSV para automatizar pipelines de localização.

Boa codificação, e aproveite para criar aplicações acessíveis globalmente!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [traduzir docx para francês com Aspose.Words e Google API](/words/english/net/ai-powered-document-processing/translate-docx-to-french-with-aspose-words-and-google-api/)
- [Como salvar documento Word traduzido em C# com Google AI](/words/english/net/ai-powered-document-processing/how-to-save-translated-word-document-in-c-with-google-ai/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}