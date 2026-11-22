---
category: general
date: 2026-11-22
description: Defina texto de espaço reservado em um controle de conteúdo do Word com
  C#. Aprenda como criar uma tag personalizada, inserir um controle de texto simples
  e adicionar um espaço reservado à tag usando Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set placeholder text
- create custom tag
- how to insert content control
- add placeholder to tag
- insert plain text control
language: pt
lastmod: 2026-11-22
og_description: Defina texto de espaço reservado em um controle de conteúdo do Word
  com C#. Este tutorial mostra como criar uma tag personalizada, inserir um controle
  de texto simples e adicionar um espaço reservado à tag para melhorar a interatividade
  do documento.
og_image_alt: Screenshot showing a Word document with a content control placeholder
  text set using C#
og_title: Definir texto de espaço reservado em um controle de conteúdo do Word – Guia
  C#
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Set placeholder text in a Word content control with C#. Learn how to
    create a custom tag, insert a plain text control, and add placeholder to tag using
    Aspose.Words.
  headline: Set placeholder text in a Word content control with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Content Control
- Word Automation
title: Definir texto de espaço reservado em um controle de conteúdo do Word com C#
url: /pt/java/using-document-elements/set-placeholder-text-in-a-word-content-control-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Definir texto de espaço reservado em um controle de conteúdo do Word com C#

Se você precisar **definir texto de espaço reservado** em um documento Word programaticamente, este guia mostra exatamente como fazer isso. Usando Aspose.Words for .NET, você pode criar uma tag personalizada, inserir um controle de texto simples e adicionar espaço reservado à tag para que o documento esteja pronto para a entrada do usuário.

Neste tutorial você aprenderá como **criar tag personalizada**, **como inserir controle de conteúdo** e **adicionar espaço reservado à tag** mantendo o código conciso e pronto para produção. Nenhuma ferramenta externa é necessária — apenas um projeto .NET e a biblioteca Aspose.Words.

## Pré-requisitos

* .NET 6.0 SDK ou posterior instalado  
* Uma licença válida do Aspose.Words for .NET (ou uma chave de avaliação gratuita)  
* Familiaridade básica com C# e Visual Studio (ou qualquer IDE de sua preferência)  

As seções a seguir presumem que você criou um projeto de console chamado `WordPlaceholderDemo`.

## Etapa 1: Instalar Aspose.Words

Adicione o pacote NuGet ao seu projeto:

```bash
dotnet add package Aspose.Words
```

> **Dica profissional:** Use a flag `--version` para fixar o pacote na versão estável mais recente (por exemplo, `Aspose.Words.NET 24.9`).

## Etapa 2: Carregar o documento fonte e criar um `DocumentBuilder`

A primeira coisa que você faz é carregar um arquivo `.docx` existente (ou criar um novo documento vazio) e instanciar um `DocumentBuilder`. O builder fornece uma API fluente para inserir controles e texto.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Building;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // Load an existing Word file or create a new one
            Document doc = new Document("input.docx");   // <-- replace with your path
            DocumentBuilder builder = new DocumentBuilder(doc);
```

Este código **prepara o cenário** para inserir um controle de conteúdo. O `DocumentBuilder` trabalha diretamente no objeto `doc`, portanto quaisquer alterações que você fizer são refletidas automaticamente.

## Etapa 3: Criar uma tag personalizada (StructuredDocumentTag)

Uma *tag personalizada* no Word é chamada de **StructuredDocumentTag (SDT)**. Você pode considerá-la como um controle de conteúdo que carrega um identificador único. Criar uma é o núcleo da etapa **criar tag personalizada**.

```csharp
            // Insert a plain‑text StructuredDocumentTag (SDT) with a tag identifier
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");
```

O método `InsertStructuredDocumentTag` aceita dois argumentos:

1. O tipo de controle (`PlainText` neste caso).  
2. Uma string que identifica de forma única a tag (`"MyTag"`).  

Ao usar uma **tag personalizada**, você pode localizar ou manipular o controle programaticamente mais tarde.

## Etapa 4: Definir um título para acessibilidade

Um título melhora a acessibilidade e facilita a localização do controle na interface do Word.

```csharp
            // Set a descriptive title (used by screen readers)
            sdt.Title = "CustomerName";
```

A propriedade `Title` é opcional, mas adicioná‑la é uma prática recomendada ao **adicionar espaço reservado à tag** para melhorar a experiência do usuário.

## Etapa 5: Adicionar texto de espaço reservado à tag

Agora vem o objetivo principal: **definir texto de espaço reservado**. Esse texto aparece quando o controle está vazio, orientando o usuário sobre o que digitar.

```csharp
            // Provide placeholder text that shows when the tag is empty
            sdt.PlaceholderText = "Enter name…";
```

A propriedade `PlaceholderText` é exatamente o que você precisa para **adicionar espaço reservado à tag**. Ela se comporta como a dica cinza que você vê em campos de formulário modernos.

## Etapa 6: Salvar o documento modificado

Depois de configurar o controle, grave o documento de volta no disco.

```csharp
            // Save the document with the new content control
            doc.Save("output.docx");   // <-- replace with your desired path
        }
    }
}
```

Ao abrir `output.docx` no Microsoft Word, você verá um controle de conteúdo de texto simples rotulado “CustomerName” com o espaço reservado “Enter name…”. Clicar dentro do controle remove o espaço reservado, permitindo que o usuário digite.

### Saída esperada

* Um arquivo Word (`output.docx`) contendo um único controle de conteúdo de texto simples.  
* O controle exibe o espaço reservado “Enter name…” até que o usuário digite algo.  
* O identificador da tag do controle é `MyTag`, que você pode consultar posteriormente com `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`.

## Etapa 7: Como inserir controle de conteúdo em outro lugar (avançado)

Se você precisar **como inserir controle de conteúdo** em um local específico — por exemplo, após um determinado parágrafo — use o método `MoveTo` antes de inserir a tag:

```csharp
            // Move the cursor to the end of the first paragraph
            builder.MoveTo(doc.FirstSection.Body.Paragraphs[0].End);
            // Insert another plain‑text control with a different tag
            StructuredDocumentTag addressTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "AddressTag");
            addressTag.Title = "CustomerAddress";
            addressTag.PlaceholderText = "Enter address…";
```

Este trecho demonstra **inserir controle de texto simples** várias vezes dentro do mesmo documento.

## Armadilhas comuns e como evitá‑las

| Problema | Por que acontece | Correção |
|----------|------------------|----------|
| Espaço reservado não visível | O controle já contém texto (mesmo que um espaço) | Garanta que `sdt.Text` esteja vazio antes de definir `PlaceholderText`. |
| Colisão de identificador de tag | Reutilizar o mesmo nome de tag (`MyTag`) no mesmo documento | Use identificadores únicos para cada `StructuredDocumentTag`. |
| Exceção de licença | Executar sem uma licença válida do Aspose.Words | Aplique um arquivo de licença (`license.SetLicense("Aspose.Words.lic")`) no início do `Main`. |
| Documento não salvo | Esquecer de chamar `doc.Save` ou usar um caminho somente leitura | Verifique se o caminho de saída é gravável e chame `doc.Save`. |

## Exemplo completo em funcionamento

Abaixo está o programa completo que você pode copiar‑colar em `Program.cs`. Ele inclui todas as etapas — **criar tag personalizada**, **como inserir controle de conteúdo**, **adicionar espaço reservado à tag** e **inserir controle de texto simples** — em um fluxo coeso.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Building;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // Optional: apply your Aspose.Words license here
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // Load the source document (or create a new one)
            Document doc = new Document("input.docx");
            DocumentBuilder builder = new DocumentBuilder(doc);

            // --------- Create custom tag ----------
            StructuredDocumentTag nameTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");
            nameTag.Title = "CustomerName";
            nameTag.PlaceholderText = "Enter name…";

            // Insert a second control after the first paragraph
            builder.MoveTo(doc.FirstSection.Body.Paragraphs[0].End);
            StructuredDocumentTag addressTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "AddressTag");
            addressTag.Title = "CustomerAddress";
            addressTag.PlaceholderText = "Enter address…";

            // Save the result
            doc.Save("output.docx");
            Console.WriteLine("Document saved with placeholder text set.");
        }
    }
}
```

Execute o programa com `dotnet run`. Após a execução, abra `output.docx` para verificar que ambos os controles exibem seus respectivos espaços reservados.

## Próximos passos

* **Personalizar aparência** – Use `sdt.Font` para alterar o tamanho, cor ou estilo da fonte dentro do controle.  
* **Vincular a dados XML** – Explore `sdt.XmlMapping` se precisar que o controle faça mapeamento 

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Criar documento Word programaticamente – adicionar controle de conteúdo e espaço reservado](/words/english/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/)
- [Definir Texto de Espaço Reservado no Aspose.Words – Guia Completo em C#](/words/english/net/programming-with-sdt/set-placeholder-text-in-aspose-words-complete-c-guide/)
- [Criar novo documento Word e inserir controle de conteúdo em C#](/words/english/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}