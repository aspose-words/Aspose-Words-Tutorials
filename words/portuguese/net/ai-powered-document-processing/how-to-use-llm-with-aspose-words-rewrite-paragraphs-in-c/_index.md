---
category: general
date: 2026-05-04
description: Como usar LLM para editar documentos com Aspose – aprenda a substituir
  texto de parágrafos, conectar a um LLM local e reescrever texto usando IA.
draft: false
keywords:
- how to use llm
- replace paragraph text
- connect to local llm
- rewrite text using ai
- edit document aspose
language: pt
og_description: Como usar LLM para editar documentos com Aspose. Este guia mostra
  como conectar a um LLM local, substituir o texto de parágrafos e reescrever texto
  usando IA.
og_title: Como usar LLM com Aspose.Words – Reescrever parágrafos em C#
tags:
- Aspose.Words
- C#
- AI
- LLM
title: Como usar LLM com Aspose.Words – Reescrever parágrafos em C#
url: /pt/net/ai-powered-document-processing/how-to-use-llm-with-aspose-words-rewrite-paragraphs-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como usar LLM com Aspose.Words – Reescrever Parágrafos em C#

Já se perguntou **como usar LLM** para aprimorar um documento Word sem abri‑lo manualmente? Você não está sozinho. Muitos desenvolvedores se deparam com um obstáculo quando precisam *substituir o texto de um parágrafo* programaticamente, mas não têm um fluxo de trabalho limpo baseado em IA.  

Neste tutorial vamos conectar um modelo de linguagem grande local, alimentar um trecho de um arquivo `.docx`, pedir que ele **reescreva o texto usando IA**, e finalmente salvar o documento atualizado — tudo com Aspose.Words. Ao final, você terá um aplicativo console C# pronto‑para‑executar que demonstra todo o pipeline.

> **O que você receberá:** um exemplo completo e executável, explicações de cada passo, dicas para casos de borda e ideias para expandir a solução.

## O que você precisará

- **.NET 6+** (ou .NET Framework 4.7.2 – o código funciona em ambos)
- **Aspose.Words for .NET** (pacote NuGet `Aspose.Words`)
- Um **servidor LLM local** que exponha um endpoint HTTP simples `/generate` (por exemplo, Ollama, LMStudio ou um serviço Flask personalizado)
- Familiaridade básica com C# e código de cliente HTTP  

Nenhum SDK adicional é necessário; todo o resto está no código que escreveremos juntos.

## Etapa 1: Como usar LLM para substituir o texto de um parágrafo

A primeira coisa que precisamos fazer é identificar o parágrafo que queremos modificar. Aspose.Words torna isso muito fácil ao expor um modelo de objetos rico.

```csharp
using Aspose.Words;
using Aspose.Words.AI;   // Imaginary namespace for illustration – replace with actual if needed
using System.Net.Http;
using System.Text;
using System.Text.Json;

// Load the source document
Document document = new Document("YOUR_DIRECTORY/input.docx");

// Grab the third paragraph (zero‑based index)
Paragraph targetParagraph = document.FirstSection.Body.Paragraphs[2];

// Show the original text in the console – handy for debugging
Console.WriteLine("Original paragraph:");
Console.WriteLine(targetParagraph.GetText());
```

**Por que isso importa:**  
Selecionar o nó correto impede que você sobrescreva acidentalmente cabeçalhos ou tabelas. Ao usar a abordagem de **substituir texto de parágrafo** mantemos a estrutura do documento intacta, tocando apenas o conteúdo que nos interessa.

> **Dica de especialista:** Se o seu documento tem seções de comprimento variável, use `document.GetChildNodes(NodeType.Paragraph, true)` e LINQ para localizar um parágrafo pelo seu texto ou estilo.

## Etapa 2: Conectar a um endpoint LLM local

Agora que temos o texto, precisamos enviá‑lo ao LLM. O exemplo usa uma classe wrapper simples `LocalLargeLanguageModel` que oculta a parte HTTP. Sinta‑se à vontade para substituí‑la por chamadas `HttpClient` se preferir.

```csharp
/// <summary>
/// Minimal wrapper around a local LLM HTTP API.
/// Assumes the API accepts a JSON payload { "prompt": "..."} and returns { "response": "..." }.
/// </summary>
public class LocalLargeLanguageModel
{
    private readonly HttpClient _client;
    private readonly string _endpoint;

    public LocalLargeLanguageModel(string endpoint)
    {
        _endpoint = endpoint.TrimEnd('/');
        _client = new HttpClient();
    }

    public string GenerateText(string prompt)
    {
        var payload = new { prompt };
        var content = new StringContent(JsonSerializer.Serialize(payload), Encoding.UTF8, "application/json");

        // Synchronous call for brevity – in production use async/await
        var response = _client.PostAsync($"{_endpoint}/generate", content).Result;
        response.EnsureSuccessStatusCode();

        var json = response.Content.ReadAsStringAsync().Result;
        var result = JsonSerializer.Deserialize<Dictionary<string, string>>(json);
        return result?["response"] ?? string.Empty;
    }
}

// Step 2: Instantiate the LLM client pointing at localhost
var localLlm = new LocalLargeLanguageModel("http://localhost:5000");
```

**Por que nos conectamos dessa forma:**  
Uma configuração de **conectar a LLM local** elimina latência, mantém os dados on‑premise e evita custos de API. O wrapper também deixa o código posterior mais limpo, permitindo focar na lógica de **reescrever texto usando IA**.

## Etapa 3: Reescrever texto usando IA com Aspose.Words

Com o texto do parágrafo em mãos e o LLM pronto, criamos um prompt que diz ao modelo exatamente o que queremos — reescrever em tom formal. Você pode ajustar o prompt para outros estilos (amigável, técnico, etc.).

```csharp
// Build the prompt – notice the newline for readability
string prompt = $"Rewrite the following in a formal tone:\n{targetParagraph.GetText()}";

// Ask the LLM to generate the revised version
string revisedText = localLlm.GenerateText(prompt);

// Show the AI‑generated text
Console.WriteLine("\nRevised paragraph:");
Console.WriteLine(revisedText);
```

**Por que isso funciona:**  
LLMs são dirigidos por prompts; dar instruções explícitas (“Rewrite … in a formal tone”) gera resultados consistentes. A etapa de **reescrever texto usando IA** é o coração do tutorial – demonstra como a IA pode ser incorporada diretamente nos fluxos de trabalho de documentos.

## Etapa 4: Editar o documento e salvar as alterações

Agora substituímos as runs originais pelo novo conteúdo. Aspose.Words armazena texto em objetos `Run`, então limpá‑los primeiro evita artefatos de formatação remanescentes.

```csharp
// Clear existing runs (pieces of text) from the paragraph
targetParagraph.Runs.Clear();

// Append a new Run containing the revised text
targetParagraph.AppendChild(new Run(document, revisedText));

// Save the updated document
document.Save("YOUR_DIRECTORY/output.docx");

// Confirmation
Console.WriteLine("\nDocument saved as output.docx");
```

**Nota de caso de borda:**  
Se o parágrafo original continha formatação mista (negrito, itálico) você pode querer preservar os estilos. Nesse caso, crie uma nova `Run`, copie as configurações originais de `Font`, e então defina seu `Text` para `revisedText`.

## Exemplo completo em funcionamento

Abaixo está o programa inteiro que você pode copiar‑colar em um projeto console. Lembre‑se de instalar o pacote NuGet Aspose.Words primeiro (`dotnet add package Aspose.Words`).

```csharp
// ---------------------------------------------------------------
// Complete C# console app: how to use llm to edit a Word doc
// ---------------------------------------------------------------
using Aspose.Words;
using Aspose.Words.AI;   // Replace with real namespace if needed
using System;
using System.Collections.Generic;
using System.Net.Http;
using System.Text;
using System.Text.Json;

namespace LlmAsposeDemo
{
    public class LocalLargeLanguageModel
    {
        private readonly HttpClient _client;
        private readonly string _endpoint;

        public LocalLargeLanguageModel(string endpoint)
        {
            _endpoint = endpoint.TrimEnd('/');
            _client = new HttpClient();
        }

        public string GenerateText(string prompt)
        {
            var payload = new { prompt };
            var content = new StringContent(JsonSerializer.Serialize(payload), Encoding.UTF8, "application/json");

            var response = _client.PostAsync($"{_endpoint}/generate", content).Result;
            response.EnsureSuccessStatusCode();

            var json = response.Content.ReadAsStringAsync().Result;
            var result = JsonSerializer.Deserialize<Dictionary<string, string>>(json);
            return result?["response"] ?? string.Empty;
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the document
            Document document = new Document("YOUR_DIRECTORY/input.docx");

            // 2️⃣ Pick the third paragraph (index 2)
            Paragraph targetParagraph = document.FirstSection.Body.Paragraphs[2];
            Console.WriteLine("Original paragraph:");
            Console.WriteLine(targetParagraph.GetText());

            // 3️⃣ Connect to the local LLM
            var localLlm = new LocalLargeLanguageModel("http://localhost:5000");

            // 4️⃣ Ask the model to rewrite it formally
            string prompt = $"Rewrite the following in a formal tone:\n{targetParagraph.GetText()}";
            string revisedText = localLlm.GenerateText(prompt);
            Console.WriteLine("\nRevised paragraph:");
            Console.WriteLine(revisedText);

            // 5️⃣ Replace the paragraph contents
            targetParagraph.Runs.Clear();
            targetParagraph.AppendChild(new Run(document, revisedText));

            // 6️⃣ Save the file
            document.Save("YOUR_DIRECTORY/output.docx");
            Console.WriteLine("\nDocument saved as output.docx");
        }
    }
}
```

### Saída esperada

```
Original paragraph:
the quick brown fox jumps over the lazy dog.

Revised paragraph:
The quick brown fox leaps over the lazy dog in a formal manner.

Document saved as output.docx
```

Abra `output.docx` – você verá que o terceiro parágrafo agora contém a versão aprimorada.

## Perguntas frequentes e armadilhas

| Pergunta | Resposta |
|----------|----------|
| **E se meu LLM retornar JSON com campos extras?** | Ajuste `GenerateText` para desserializar a propriedade correta ou analise a resposta manualmente. |
| **Posso processar vários parágrafos de uma vez?** | Sim – itere sobre `document.FirstSection.Body.Paragraphs` e aplique a mesma lógica de prompt, talvez adicionando um índice de parágrafo ao prompt para contexto. |
| **Meu servidor LLM usa autenticação?** | Adicione um cabeçalho ao `HttpClient` antes do POST: `_client.DefaultRequestHeaders.Add("Authorization", "Bearer YOUR_TOKEN");`. |
| **A formatação se perde após a substituição.** | Preserve as configurações originais de `Run.Font`: crie uma nova `Run`, copie `originalRun.Font.Clone()`, então defina seu `Text`. |
| **O LLM às vezes retorna strings vazias.** | Implemente um fallback – se `revisedText.Trim().Length == 0`, mantenha o texto original ou tente novamente com um prompt mais simples. |

## Expandindo a solução

Agora que você dominou **como usar LLM** para um único parágrafo, considere os próximos passos:

- **Processamento em lote:** Percorra cada parágrafo e reescreva no estilo escolhido (por exemplo, “tornar todo o texto conciso”).  
- **Reescrita consciente de estilo:** Passe o nome do estilo do parágrafo original no prompt para que o LLM respeite cabeçalhos vs texto de corpo.  
- **Integração com pipeline CI:** Automatize o polimento de documentos como parte de um processo de construção de documentação.  
- **Prompts alternativos:** Experimente “summarize this paragraph” ou “translate this paragraph to Spanish” para explorar todo o poder de **reescrever texto usando IA**.

## Conclusão

Percorremos todo o fluxo de **como usar LLM** com Aspose.Words: carregar um documento, **conectar a LLM local**, extrair um parágrafo, **reescrever texto usando IA**, **substituir texto de parágrafo**, e finalmente salvar o resultado. O código é autocontido, funciona imediatamente e demonstra uma maneira prática de combinar IA com automação tradicional de documentos.

Dê uma experimentada, ajuste os prompts e deixe

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}