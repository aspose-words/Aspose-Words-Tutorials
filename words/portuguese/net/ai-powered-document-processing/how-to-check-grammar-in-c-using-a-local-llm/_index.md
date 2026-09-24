---
category: general
date: 2026-02-21
description: Como verificar gramática em C# carregando um DOCX, enviando seu texto
  para um LLM local e gravando de volta a versão corrigida. Inclui como usar o LLM
  e ler o texto de documentos Word.
draft: false
keywords:
- how to check grammar
- how to use llm
- read word document text
- load docx in c#
language: pt
og_description: Como verificar a gramática em C# carregando um DOCX, enviando seu
  texto para um LLM local e gravando de volta a versão corrigida. Aprenda a usar LLM
  e ler o texto de documentos Word.
og_title: Como Verificar Gramática em C# Usando um LLM Local
tags:
- C#
- LLM
- Aspose.Words
title: Como Verificar Gramática em C# Usando um LLM Local
url: /pt/net/ai-powered-document-processing/how-to-check-grammar-in-c-using-a-local-llm/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como Verificar Gramática em C# Usando um LLM Local

Já se perguntou **como verificar gramática** em um documento Word sem sair do seu projeto C#? Você não está sozinho—desenvolvedores perguntam constantemente: “Posso automatizar a revisão de texto com o mesmo código que alimenta chatbots?” A resposta curta é sim. Carregando um DOCX, extraindo seu texto e enviando‑o para um modelo de linguagem grande (LLM) hospedado localmente, você obtém correções de gramática instantâneas e grava o resultado polido diretamente no arquivo.

Neste tutorial vamos percorrer todo o processo: ler um `.docx` com **load docx in c#**, chamar **how to use llm** para correção gramatical e, finalmente, salvar o documento limpo. Ao final, você terá um aplicativo console pronto‑para‑executar que faz exatamente o que precisa—sem copiar‑colar manual, sem APIs externas, apenas C# puro e um endpoint LLM local.

> **O que você precisará**
> - .NET 6.0 ou superior (o código também funciona no .NET Framework, mas .NET 6 é o ponto ideal)
> - A biblioteca [Aspose.Words for .NET](https://products.aspose.com/words/net/) (versão de avaliação gratuita serve para testes)
> - Um servidor LLM em execução que exponha um endpoint simples `CheckGrammar(string)` (ex.: Ollama, LM Studio ou um wrapper FastAPI customizado)
> - Familiaridade básica com async/await (opcional, mas recomendado)

Se você está se perguntando **por que isso importa**, pense no tempo que você gasta corrigindo manualmente erros de digitação em relatórios gerados. Automatizar essa etapa não só acelera os pipelines, como também garante consistência em dezenas de documentos. Vamos mergulhar.

---

## Como Verificar Gramática – Visão Geral

Antes de sujarmos as mãos, aqui está um roteiro rápido:

1. **Create a client** que converse com o endpoint LLM local.  
2. **Read the Word document** usando Aspose.Words—esta é a forma clássica de **read word document text** em C#.  
3. **Send the raw text** ao LLM e receba uma versão corrigida.  
4. **Replace the original content** no documento pelo texto corrigido.  
5. **Save** o arquivo atualizado (opcional, mas geralmente necessário).

Cada passo está encapsulado em seu próprio método para que você possa reutilizar ou substituir partes mais tarde. O código‑fonte completo aparece ao final do artigo.

---

## Passo 1: Configurar o Cliente LLM (Como Usar LLM)

Para manter as coisas organizadas, vamos encapsular a chamada HTTP em uma pequena classe wrapper. Essa classe supõe que o serviço LLM aceita uma requisição POST com um payload JSON `{ "prompt": "..."} ` e devolve `{ "response": "..." }`. Ajuste a serialização se o seu serviço for diferente.

```csharp
using System.Net.Http;
using System.Text;
using System.Text.Json;
using System.Threading.Tasks;

/// <summary>
/// Minimal client for a local LLM that offers a grammar‑checking endpoint.
/// </summary>
public class LocalLargeLanguageModel
{
    private readonly HttpClient _http;
    private readonly string _baseUrl;

    public LocalLargeLanguageModel(string baseUrl)
    {
        _baseUrl = baseUrl.TrimEnd('/');
        _http = new HttpClient();
    }

    /// <summary>
    /// Sends the input text to the LLM and returns the corrected version.
    /// </summary>
    public async Task<string> CheckGrammarAsync(string input)
    {
        var payload = new { prompt = $"Correct the grammar and punctuation:\n\n{input}" };
        var content = new StringContent(JsonSerializer.Serialize(payload), Encoding.UTF8, "application/json");

        // The endpoint is assumed to be /grammar
        var response = await _http.PostAsync($"{_baseUrl}/grammar", content);
        response.EnsureSuccessStatusCode();

        var json = await response.Content.ReadAsStringAsync();
        var result = JsonSerializer.Deserialize<Dictionary<string, string>>(json);
        return result != null && result.TryGetValue("response", out var corrected) ? corrected : input;
    }
}
```

**Why this matters:**  
- **Decoupling** – Se você mudar de Ollama para LM Studio, só precisará alterar a URL ou o formato do payload.  
- **Async‑friendly** – I/O de rede não bloqueará sua UI ou worker em background.  
- **Error handling** – `EnsureSuccessStatusCode` lança uma exceção clara se o LLM estiver indisponível, que capturaremos mais adiante.

> **Pro tip:** Se o seu LLM roda em GPU, mantenha o tamanho da requisição abaixo de ~4 KB para evitar picos de latência.

---

## Passo 2: Carregar o DOCX e Extrair Texto (Ler Texto de Documento Word)

Aspose.Words facilita a leitura de arquivos Word. O método `Document.GetText()` devolve todo o texto visível, preservando quebras de linha. Se precisar de formatação mais rica (tabelas, notas de rodapé), será necessário percorrer a árvore de nós, mas para verificação gramatical pura o texto simples é suficiente.

```csharp
using Aspose.Words;

/// <summary>
/// Loads a .docx file and returns its raw textual content.
/// </summary>
public static string ReadDocumentText(string filePath)
{
    if (!File.Exists(filePath))
        throw new FileNotFoundException($"Document not found: {filePath}");

    var doc = new Document(filePath);
    return doc.GetText(); // Returns text with line breaks
}
```

**Edge case note:**  
Se o documento contiver caracteres não‑ingleses ou símbolos especiais, certifique‑se de que o modelo LLM que você está usando suporte Unicode. A maioria dos modelos modernos suporta, mas modelos mais antigos podem truncar ou interpretar erroneamente esses caracteres.

---

## Passo 3: Substituir o Conteúdo pelo Texto Corrigido

Aspose.Words não possui um método de “substituir todo o corpo” em uma linha, mas limpar a árvore de nós e inserir um único parágrafo funciona muito bem. Isso também garante que qualquer marcação oculta (como alterações rastreadas) seja removida.

```csharp
/// <summary>
/// Overwrites the document with the supplied corrected text.
/// </summary>
public static void WriteCorrectedText(string filePath, string correctedText)
{
    var doc = new Document(filePath);
    doc.RemoveAllChildren(); // Clears sections, paragraphs, tables, etc.

    var builder = new DocumentBuilder(doc);
    builder.Writeln(correctedText); // Writes as a single paragraph; you can split by "\n" if you want multiple paragraphs.

    doc.Save(filePath); // Overwrites the original file
}
```

**Why we remove all children:**  
- Garante um ponto de partida limpo, impedindo que formatações residuais interfiram no novo conteúdo.  
- Simplifica o código—não é necessário procurar nós específicos para substituir.

Se preferir preservar os títulos originais, você poderia analisar a árvore de nós original, substituir apenas nós `Run`, mas isso adiciona complexidade além do escopo deste tutorial.

---

## Passo 4: Conectar Tudo – Exemplo Completo Funcional

A seguir está o programa console completo. Ele demonstra **how to check grammar** do início ao fim, incluindo tratamento básico de erros e argumentos de linha de comando opcionais.

```csharp
using System;
using System.IO;
using System.Threading.Tasks;
using Aspose.Words;

// Ensure you have a license or are okay with the evaluation watermark.
class Program
{
    // Adjust these paths to match your environment.
    private const string InputPath = @"YOUR_DIRECTORY\input.docx";
    private const string OutputPath = @"YOUR_DIRECTORY\output.docx";
    private const string LlmEndpoint = "http://localhost:5000";

    static async Task Main(string[] args)
    {
        try
        {
            // 1️⃣ Create the LLM client.
            var llm = new LocalLargeLanguageModel(LlmEndpoint);

            // 2️⃣ Load the DOCX and read its text.
            Console.WriteLine("Reading document...");
            string originalText = ReadDocumentText(InputPath);

            // 3️⃣ Send text to the LLM for grammar correction.
            Console.WriteLine("Sending text to LLM for grammar check...");
            string correctedText = await llm.CheckGrammarAsync(originalText);

            // 4️⃣ Write the corrected text back into a new file.
            Console.WriteLine("Writing corrected text to new document...");
            // We copy the original file first so the original remains untouched.
            File.Copy(InputPath, OutputPath, overwrite: true);
            WriteCorrectedText(OutputPath, correctedText);

            Console.WriteLine($"✅ Grammar check complete! Updated file saved to: {OutputPath}");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"❌ An error occurred: {ex.Message}");
            // For real‑world apps, consider logging the stack trace.
        }
    }

    // --- Helper methods from earlier steps ---
    public static string ReadDocumentText(string filePath)
    {
        if (!File.Exists(filePath))
            throw new FileNotFoundException($"Document not found: {filePath}");

        var doc = new Document(filePath);
        return doc.GetText();
    }

    public static void WriteCorrectedText(string filePath, string correctedText)
    {
        var doc = new Document(filePath);
        doc.RemoveAllChildren();

        var builder = new DocumentBuilder(doc);
        // Preserve line breaks by splitting and writing each line.
        foreach (var line in correctedText.Split(new[] { "\r\n", "\n" }, StringSplitOptions.None))
        {
            builder.Writeln(line);
        }

        doc.Save(filePath);
    }
}
```

### Saída Esperada

Ao executar o programa (`dotnet run`), o console exibirá algo como:

```
Reading document...
Sending text to LLM for grammar check...
Writing corrected text to new document...
✅ Grammar check complete! Updated file saved to: YOUR_DIRECTORY\output.docx
```

Abra `output.docx` no Word—você verá o mesmo conteúdo, porém com pontuação corrigida, concordância sujeito‑verbo ajustada e quaisquer erros óbvios de digitação corrigidos pelo LLM.

---

## Perguntas Frequentes & Casos de Borda

### E se o LLM retornar `null` ou uma string vazia?

O método `CheckGrammarAsync` recorre ao input original se o payload de resposta não contiver o campo `response`. Isso impede que você apague acidentalmente o documento.

### Qual o tamanho máximo de um documento antes que a requisição expire?

A maioria dos servidores LLM locais lida confortavelmente com alguns milhares de caracteres. Para arquivos maiores (ex.: 100 KB+), considere dividir o texto em parágrafos, enviar cada bloco separadamente e, depois, re‑montar as partes corrigidas. Um tamanho de bloco de ~2 KB é um bom ponto de partida.

### Isso preserva imagens, tabelas ou notas de rodapé?

Não. Ao limpar todos os filhos perdemos quaisquer elementos não‑textuais. Se precisar manter esses itens, será necessário percorrer a árvore de nós, substituir apenas nós `Run` (os fragmentos de texto) e deixar os demais nós intactos. Esse é um cenário mais avançado—sinta‑se à vontade para explorar a API Aspose.Words para manipulação de `NodeCollection`.

### Posso usar um LLM na nuvem em vez de um local?

Com certeza. Basta substituir a URL do endpoint e o formato do payload em `LocalLargeLanguageModel`. Tenha em mente que serviços na nuvem costumam ter limites de taxa e custos associados, enquanto um modelo local funciona offline e é gratuito após a configuração inicial de GPU/CPU.

---

## Dicas Profissionais & Melhores Práticas

- **Cache o cliente**: Re‑usar a mesma instância `HttpClient` evita

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}