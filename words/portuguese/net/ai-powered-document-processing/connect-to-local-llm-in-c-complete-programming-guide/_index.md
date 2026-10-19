---
category: general
date: 2026-04-28
description: Conecte-se ao LLM local a partir de C# e solicite ao modelo de linguagem
  grande que carregue um documento Word, chame o LLM local e reescreva o texto automaticamente.
  Código passo a passo incluído.
draft: false
keywords:
- connect to local llm
- prompt large language model
- load word document
- call local llm
- rewrite text automatically
language: pt
og_description: Conecte-se ao LLM local a partir do C# e veja como interagir com um
  modelo de linguagem grande, carregar um documento Word, chamar o LLM local e reescrever
  o texto automaticamente em minutos.
og_title: Conecte-se ao LLM Local em C# – Guia Completo de Programação
tags:
- Aspose.Words
- C#
- LLM
- AI Automation
title: Conecte-se ao LLM local em C# – Guia completo de programação
url: /pt/net/ai-powered-document-processing/connect-to-local-llm-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Conectar a um LLM Local em C# – Guia Completo de Programação

Já precisou **conectar a um llm local** a partir de um aplicativo .NET e se perguntou como fazê‑lo conversar com um arquivo Word? Você não está sozinho. Neste guia percorreremos todo o processo — conectar ao llm local, **prompt large language model**, carregar um documento Word, **call local llm** e, por fim, **rewrite text automatically**. Ao final, você terá um exemplo executável que transforma qualquer parágrafo em um tom formal sem precisar de chaves de API externas.

## O Que Este Tutorial Abrange

Começaremos instalando os pacotes NuGet necessários, depois iniciaremos um endpoint simples de LLM local (pense no Ollama na porta 11434). Em seguida, carregaremos um arquivo `.docx` usando Aspose.Words, enviaremos um parágrafo ao LLM, receberemos a versão reescrita e a gravaremos de volta no mesmo documento. Você também verá como lidar com armadilhas comuns — parágrafos nulos, descarte assíncrono e peculiaridades de codificação — para que o código funcione em produção, não apenas em uma demonstração.

### Pré‑requisitos

- .NET 6.0 SDK ou posterior (você também pode usar .NET 8 se preferir)
- Visual Studio 2022 ou VS Code com extensão C#
- **Aspose.Words for .NET** (a versão de avaliação funciona)
- Um LLM hospedado localmente que siga o contrato `/api/generate` (ex.: Ollama, LMStudio)
- Familiaridade básica com async/await em C#

> **Pro tip:** Se ainda não instalou o Ollama, execute `ollama serve` e faça o download de um modelo com `ollama pull llama3`. O endpoint HTTP padrão será `http://localhost:11434/api/generate`.

---

## Etapa 1: Instalar os Pacotes Necessários

Primeiro, adicione os pacotes NuGet Aspose.Words e Aspose.Words.AI ao seu projeto.

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

Essas bibliotecas nos dão a capacidade de **load word document** e um wrapper leve para **call local llm** sem precisar criar requisições HTTP manualmente.

---

## Etapa 2: Conectar ao Endpoint do LLM Local

Conectar a um modelo hospedado localmente é tão simples quanto instanciar `LocalLargeLanguageModel`. O construtor espera a URL completa do endpoint de geração.

```csharp
using Aspose.Words.AI;
using Aspose.Words;
using System.Threading.Tasks;

// Create a client that talks to the LLM running on localhost
var localLlm = new LocalLargeLanguageModel("http://localhost:11434/api/generate");
```

Por que envolver o endpoint em uma classe? O `LocalLargeLanguageModel` cuida da serialização JSON, tentativas de nova conexão e respostas em streaming para você — assim você pode focar na lógica do prompt em vez de mexer com `HttpClient`.

---

## Etapa 3: Carregar o Documento Word de Origem

Em seguida, trazemos o documento para a memória. Aspose.Words suporta praticamente todos os formatos Word, então `Document` analisará `input.docx` sem precisar do Office instalado.

```csharp
// Path to the source file – adjust as needed
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document; throws if the file is missing or corrupted
Document sourceDocument = new Document(inputPath);
```

Se precisar trabalhar com um stream (por exemplo, um arquivo enviado via ASP.NET), basta substituir o caminho do arquivo por um `MemoryStream` e passá‑lo ao construtor `Document`.

---

## Etapa 4: Extrair o Texto do Parágrafo Atual

Usaremos `DocumentBuilder` para navegar no documento. Neste exemplo reescrevemos **o primeiro parágrafo**, mas você pode iterar sobre `sourceDocument.GetChildNodes(NodeType.Paragraph, true)` para processar vários.

```csharp
// Builder gives us a cursor inside the document
DocumentBuilder docBuilder = new DocumentBuilder(sourceDocument);

// Grab the text of the paragraph where the builder is currently positioned
string originalParagraph = docBuilder.CurrentParagraph?.GetText() ?? string.Empty;

// Safety check – avoid sending empty strings to the LLM
if (string.IsNullOrWhiteSpace(originalParagraph))
{
    Console.WriteLine("No paragraph found at the current cursor position.");
    return;
}
```

O operador `?.` evita um `NullReferenceException` caso o documento esteja vazio. Esse é um daqueles **edge cases** que pegam iniciantes.

---

## Etapa 5: Prompt the LLM to Rewrite the Paragraph

Agora realmente **prompt large language model**. O prompt está em inglês simples; o wrapper o enviará como JSON ao endpoint local.

```csharp
// Build a friendly instruction for the model
string prompt = $"Rewrite the following sentence in a more formal tone:\n{originalParagraph}";

// Await the model's response – this is an async call
string rewrittenParagraph = await localLlm.PromptAsync(prompt);
```

Por que formular a solicitação dessa maneira? LLMs respondem melhor a instruções claras e de tarefa única. Inserir uma nova linha após os dois‑pontos separa a instrução do conteúdo, reduzindo a chance de o modelo ecoar o prompt de volta.

**Saída esperada** – Se `originalParagraph` fosse `"Hey, what's up?"`, o LLM poderia retornar:

> “Good day, how may I assist you?”

Você pode verificar o resultado imprimindo‑o:

```csharp
Console.WriteLine("Original:  " + originalParagraph);
Console.WriteLine("Rewritten: " + rewrittenParagraph);
```

---

## Etapa 6: Inserir o Texto Reescrito de Volta no Documento

Com o novo texto em mãos, substituímos o parágrafo antigo. `DocumentBuilder.Writeln` grava uma nova linha e avança o cursor, o que é perfeito para acrescentar. Se precisar *substituir* exatamente o mesmo parágrafo, use `docBuilder.CurrentParagraph.RemoveAllChildren()` antes de escrever.

```csharp
// Option A – Append a new paragraph (keeps the original)
docBuilder.Writeln(rewrittenParagraph);

// Option B – Replace the existing paragraph (uncomment to use)
// docBuilder.CurrentParagraph.RemoveAllChildren();
// docBuilder.CurrentParagraph.AppendChild(new Run(docBuilder.Document, rewrittenParagraph));
```

Ambas as abordagens são mostradas para que você escolha a que melhor se adapta ao seu fluxo de trabalho.

---

## Etapa 7: Salvar o Documento Atualizado

Por fim, persistimos as alterações em um novo arquivo. Aspose.Words escolhe automaticamente o formato com base na extensão do arquivo.

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
sourceDocument.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Abra `output.docx` no Word e verá que o parágrafo agora está em tom formal.

---

## Exemplo Completo Funcional

Abaixo está o **programa completo e autocontido**. Copie‑e cole em um projeto de console, restaure os pacotes NuGet e execute — nenhuma configuração extra é necessária além de um LLM local em execução.

```csharp
using Aspose.Words.AI;
using Aspose.Words;
using System;
using System.IO;
using System.Threading.Tasks;

class Program
{
    static async Task Main()
    {
        // -------------------------------------------------
        // Step 1: Connect to the locally hosted LLM endpoint
        // -------------------------------------------------
        var localLlm = new LocalLargeLanguageModel("http://localhost:11434/api/generate");

        // -------------------------------------------------
        // Step 2: Load the source Word document
        // -------------------------------------------------
        string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        Document sourceDocument = new Document(inputPath);

        // -------------------------------------------------
        // Step 3: Retrieve the text of the current paragraph
        // -------------------------------------------------
        DocumentBuilder docBuilder = new DocumentBuilder(sourceDocument);
        string originalParagraph = docBuilder.CurrentParagraph?.GetText() ?? string.Empty;

        if (string.IsNullOrWhiteSpace(originalParagraph))
        {
            Console.WriteLine("No paragraph found at the current cursor position.");
            return;
        }

        // -------------------------------------------------
        // Step 4: Ask the LLM to rewrite the paragraph in a formal tone
        // -------------------------------------------------
        string prompt = $"Rewrite the following sentence in a more formal tone:\n{originalParagraph}";
        string rewrittenParagraph = await localLlm.PromptAsync(prompt);

        // -------------------------------------------------
        // Step 5: Insert the rewritten text back into the document
        // -------------------------------------------------
        docBuilder.Writeln(rewrittenParagraph);

        // -------------------------------------------------
        // Step 6: Save the updated document
        // -------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
        sourceDocument.Save(outputPath);

        Console.WriteLine("Original paragraph:");
        Console.WriteLine(originalParagraph);
        Console.WriteLine("\nRewritten paragraph:");
        Console.WriteLine(rewrittenParagraph);
        Console.WriteLine($"\nDocument saved to {outputPath}");
    }
}
```

### O Que Esperar ao Executar

1. O console imprime os parágrafos original e reescrito.  
2. `output.docx` aparece ao lado de `input.docx`.  
3. Ao abrir o arquivo, o novo parágrafo formal está inserido após o original (ou substituído, se você usou o código alternativo).

---

## Lidando com Casos de Borda Comuns

| Situação | Solução |
|-----------|----------|
| **Parágrafo vazio ou contendo apenas espaços** | Verifique `string.IsNullOrWhiteSpace` antes de fazer o prompt (veja a Etapa 3). |
| **LLM devolve erro ou string vazia** | Envolva `PromptAsync` em um `try/catch` e retorne o texto original como fallback. |
| **Vários parágrafos precisam ser reescritos** | Percorra `sourceDocument.GetChildNodes(NodeType.Paragraph, true)` e aplique a mesma lógica de prompt. |
| **Documentos grandes causam latência** | Agrupe parágrafos e envie‑os em uma única requisição (prompt de até 4 KB por chamada). |
| **Caracteres não‑ASCII ficam corrompidos** | Garanta que o endpoint do LLM use UTF‑8 (a maioria dos modelos modernos já faz). |

---

## Próximos Passos & Tópicos Relacionados

- **Prompt large language model** com instruções mais ricas (ex.: guias de estilo, limites de tamanho).  
- Use **call local llm** em uma Web API para expor a automação de documentos como serviço.  
- Explore **load word document** em streams paralelos para cenários de alta taxa de transferência.  
- Combine esta abordagem com **rewrite text automatically** para geração em massa de e‑mails ou padronização de relatórios.  

Se quiser aprofundar, consulte a documentação da Aspose sobre **document merging** e a referência da API do Ollama para parâmetros de amostragem personalizados.

---

## Conclusão

Acabamos de mostrar como **connect to local llm** a partir de C#, **prompt large language model**, **load word document**, **call local llm** e **rewrite text automatically** — tudo em um único aplicativo console executável. O padrão escala: troque o prompt, itere sobre parágrafos ou exponha a lógica via endpoint ASP.NET. O ponto principal é que modelos de IA locais podem ser integrados estreitamente com bibliotecas clássicas de processamento de documentos, proporcionando automação poderosa sem jamais sair do seu ambiente on‑prem confiável.

Tem dúvidas sobre threading,

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}