---
category: general
date: 2026-11-25
description: Aprenda a criar um documento Word, adicionar forma de retângulo, resumir
  o documento com IA, traduzir texto usando IA e salvar o documento como DOCX usando
  Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- add rectangle shape
- summarize document with ai
- save document as docx
- translate text using ai
language: pt
lastmod: 2026-11-25
og_description: Crie um documento Word, adicione uma forma de retângulo, resuma o
  documento com IA, traduza o texto usando IA e salve o documento como DOCX — tudo
  em um único tutorial de C#.
og_image_alt: Screenshot showing a generated Word document with a rectangle shape
  and AI‑generated summary
og_title: Criar um documento Word com formas, resumo de IA e tradução em C#
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to create a Word document, add rectangle shape, summarize
    document with AI, translate text using AI, and save document as DOCX using Aspose.Words.
  headline: How to create a Word document with shapes, AI summarization, and translation
    in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- AI integration
title: Como criar um documento Word com formas, resumo por IA e tradução em C#
url: /pt/net/ai-powered-document-processing/how-to-create-a-word-document-with-shapes-ai-summarization-a/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar um documento Word com formas, resumo por IA e tradução em C#

Se você precisa **criar um documento Word** programaticamente, este guia mostra exatamente como fazer. Usando Aspose.Words para .NET, você aprenderá a **adicionar forma retangular**, invocar um serviço de IA para **resumir documento com IA**, traduzir um parágrafo com **traduzir texto usando IA**, e finalmente **salvar o documento como DOCX**.

Muitos desenvolvedores têm dificuldade em combinar automação de documentos com recursos modernos de IA. Ao final deste tutorial, você terá um único projeto C# auto‑contido que gera um arquivo *.docx* totalmente formatado, completo com uma forma visual, resumo gerado por IA e conteúdo multilíngue.

## Pré-requisitos

- .NET 6.0 SDK ou versão posterior instalado  
- Visual Studio 2022 (ou qualquer IDE C#)  
- Uma licença do Aspose.Words para .NET (ou uma chave de avaliação gratuita)  
- Acesso à internet para as chamadas de resumo e tradução por IA  

Nenhum pacote NuGet adicional é necessário além de `Aspose.Words` e `Aspose.Words.AI`.

## Etapa 1: Configurar o projeto e adicionar os pacotes necessários

Crie um novo projeto de console e inclua as bibliotecas Aspose.Words.

```bash
dotnet new console -n WordAiDemo
cd WordAiDemo
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

> **Dica profissional:** Se você pretende usar o modo de avaliação, chame `Aspose.Words.License.SetLicense("Aspose.Words.lic");` logo no início do `Main` para evitar marcas d'água.

## Etapa 2: Inicializar o documento – o núcleo de **criar documento word**

A primeira linha de código executável cria um novo objeto **Word document**. Esse objeto é a tela para todas as operações subsequentes.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.AI;          // AI‑powered features
using Aspose.Words.Charts;     // chart‑related properties
using System;

class Program
{
    static void Main()
    {
        // Create a new, empty Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

O `DocumentBuilder` simplifica a inserção de texto, formas e controles sem a necessidade de manipular manualmente árvores de nós de baixo nível.

## Etapa 3: **Adicionar forma retangular** ao documento

Uma forma retangular pode ser usada como um placeholder visual, fundo de rótulo ou um gráfico simples. Primeiro criamos um `GroupShape` e, em seguida, inserimos um `Rectangle` dentro dele.

```csharp
        // Step 3: Insert a group shape and add a rectangle inside it
        GroupShape groupShape = new GroupShape(document);
        builder.InsertNode(groupShape);
        builder.MoveTo(groupShape);
        builder.InsertShape(ShapeType.Rectangle, 100, 50); // width=100pt, height=50pt
```

O retângulo tem 100 pontos de largura e 50 pontos de altura. Como ele está dentro de um `GroupShape`, você pode adicionar mais elementos posteriormente (por exemplo, caixas de texto) sem se preocupar com colisões de layout.

## Etapa 4: Inserir um StructuredDocumentTag (SDT) de texto simples

Objetos StructuredDocumentTag são úteis para controles de conteúdo que podem ser vinculados a fontes de dados posteriormente.

```csharp
        // Step 4: Add a plain‑text StructuredDocumentTag (SDT) to the document
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(document, SdtType.PlainText, true);
        builder.InsertNode(plainTextTag);
```

O sinalizador `true` marca a tag como um controle **repetitivo**, o que é útil para modelos.

## Etapa 5: Adicionar um controle ActiveX CommandButton (UI opcional)

Se o documento gerado for usado em um ambiente que suporte ActiveX, você pode incorporar um botão.

```csharp
        // Step 5: Insert an ActiveX CommandButton control (Forms2 OLE control)
        builder.InsertForms2OleControl(OleControlType.CommandButton);
```

Esta etapa é opcional; você pode removê‑la se seu público‑alvo nunca interagir com o documento em um ambiente Windows.

## Etapa 6: **Resumir documento com IA**

Aspose.Words.AI fornece um wrapper conveniente em torno de serviços de grandes modelos de linguagem. Aqui chamamos `DocumentSummarizer.Summarize` com o backend OpenAI.

```csharp
        // Step 6: Summarize the document content using an AI service
        string summary = DocumentSummarizer.Summarize(document, SummarizerOptions.OpenAI);
        Console.WriteLine("Document summary:");
        Console.WriteLine(summary);
```

O método analisa a árvore de nós atual, extrai as frases mais relevantes e retorna um parágrafo conciso. Este é o núcleo da funcionalidade **resumir documento com IA**.

## Etapa 7: **Traduzir texto usando IA**

Em seguida, demonstramos como traduzir uma string de exemplo do inglês para o francês. O método `Translator.Translate` chama internamente um modelo de IA do Google.

```csharp
        // Step 7: Translate a sample paragraph to French using Google AI
        string translatedParagraph = Translator.Translate("Hello world", Language.French);
        Console.WriteLine("\nTranslated paragraph (English → French):");
        Console.WriteLine(translatedParagraph);
```

Você pode substituir `Language.French` por qualquer valor enum de idioma suportado, permitindo a geração multilíngue de documentos em tempo real.

## Etapa 8: **Salvar documento como DOCX**

Finalmente, persista o documento editado no disco. O método `Save` grava automaticamente um arquivo *.docx* quando você especifica a extensão `.docx`.

```csharp
        // Step 8: Save the modified document
        document.Save("Result.docx"); // **save document as docx**
        Console.WriteLine("\nDocument saved as Result.docx");
    }
}
```

O arquivo `Result.docx` agora contém:

- Uma forma retangular dentro de um group shape  
- Um controle de conteúdo de texto simples (SDT)  
- Um ActiveX CommandButton (se você manteve a Etapa 5)  
- Um parágrafo de resumo gerado por IA  
- Uma tradução em francês de “Hello world”

Você pode abrir o arquivo no Microsoft Word para verificar cada elemento.

## Código-fonte completo

Abaixo está o programa completo, pronto para execução. Copie‑o para `Program.cs` e execute `dotnet run`.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.AI;          // AI‑powered features
using Aspose.Words.Charts;     // chart‑related properties
using System;

class Program
{
    static void Main()
    {
        // 1. Create a new Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Insert a group shape and add a rectangle inside it
        GroupShape groupShape = new GroupShape(document);
        builder.InsertNode(groupShape);
        builder.MoveTo(groupShape);
        builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // 3. Add a plain‑text StructuredDocumentTag (SDT)
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(document, SdtType.PlainText, true);
        builder.InsertNode(plainTextTag);

        // 4. Insert an ActiveX CommandButton (optional)
        builder.InsertForms2OleControl(OleControlType.CommandButton);

        // 5. Summarize the document using AI
        string summary = DocumentSummarizer.Summarize(document, SummarizerOptions.OpenAI);
        Console.WriteLine("Document summary:");
        Console.WriteLine(summary);

        // 6. Translate a paragraph to French using AI
        string translatedParagraph = Translator.Translate("Hello world", Language.French);
        Console.WriteLine("\nTranslated paragraph (English → French):");
        Console.WriteLine(translatedParagraph);

        // 7. Save the document as DOCX
        document.Save("Result.docx");
        Console.WriteLine("\nDocument saved as Result.docx");
    }
}
```

### Saída esperada

```
Document summary:
[AI‑generated concise summary of the document’s current content]

Translated paragraph (English → French):
Bonjour le monde

Document saved as Result.docx
```

Ao abrir `Result.docx`, você verá a forma retangular próximo ao topo, o placeholder SDT, o botão, o parágrafo de resumo e a tradução em francês inserida como texto simples.

## Conclusão

Agora você sabe como **criar um documento Word** do zero, **adicionar forma retangular**, **resumir documento com IA**, **traduzir texto usando IA**, e **salvar documento como DOCX** — tudo com algumas linhas concisas de C#. Esse padrão escala: você pode substituir as strings codificadas por dados dinâmicos, adicionar mais formas ou gráficos, e trocar o provedor de IA ajustando os parâmetros `SummarizerOptions` ou `Translator`.

### O que vem a seguir?

- Explore variações de **add rectangle shape**: altere a cor de preenchimento, o estilo da linha ou adicione texto dentro da forma.  
- Use **summarize document with AI** em documentos maiores para gerar resumos executivos automaticamente.  
- Amplie **translate text using AI** para processar em lote parágrafos ou tabelas inteiras para relatórios multilíngues.  
- Combine as APIs de gráficos do Aspose.Words para incorporar visualizações de dados ao lado de insights gerados por IA.  

Sinta‑se à vontade para experimentar e compartilhar seus resultados nos comentários ou no GitHub. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Criar um documento Word em branco e adicionar uma forma retangular](/words/english/net/programming-with-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)
- [Criar Group Shape em documento Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Adicionar marca d'água de texto em documento Word usando Aspose.Words para .NET](/words/english/net/working-with-watermark/add-text-watermark/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}