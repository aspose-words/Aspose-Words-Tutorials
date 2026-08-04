---
category: general
date: 2026-08-04
description: Crie um documento Word programaticamente usando C#. Aprenda como adicionar
  controle de conteúdo ao Word e definir texto de espaço reservado para modelos dinâmicos.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add content control to word
- set placeholder text word
- Aspose.Words content control
- dynamic Word template C#
language: pt
lastmod: 2026-08-04
og_description: Crie um documento Word programaticamente com C#. Este guia mostra
  como adicionar controle de conteúdo ao Word e definir texto de espaço reservado
  para modelos reutilizáveis.
og_image_alt: Screenshot of a Word document with a highlighted content control placeholder
og_title: Criar documento Word programaticamente – adicionar controle de conteúdo
  e marcador de posição
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create word document programmatically using C#. Learn how to add content
    control to word and set placeholder text word for dynamic templates.
  headline: Create word document programmatically – add content control and placeholder
  type: TechArticle
tags:
- C#
- Aspose.Words
- Word automation
title: Criar documento Word programaticamente – adicionar controle de conteúdo e marcador
  de posição
url: /pt/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar documento Word programaticamente – adicionar controle de conteúdo e placeholder

Se você precisa **create word document programmatically**, este tutorial mostra uma solução completa, pronta‑para‑executar. Você verá como **add content control to word**, dar-lhe um título significativo e **set placeholder text word** para que os usuários finais possam preencher os dados mais tarde.

O guia percorre cada linha de código, explica por que cada etapa é importante e destaca armadilhas comuns. Ao final, você terá um arquivo .docx reutilizável que pode servir como modelo para faturas, contratos ou qualquer documento baseado em formulário.

## Pré-requisitos

* .NET 6.0 (ou posterior) instalado – o código usa os recursos mais recentes da linguagem C#.
* Uma licença do Aspose.Words for .NET (a avaliação gratuita funciona para desenvolvimento).
* Visual Studio 2022 ou qualquer IDE que possa compilar projetos .NET.
* Familiaridade básica com C# e o conceito de Structured Document Tags (SDTs).

> **Pro tip:** Se você executar o exemplo sem uma licença, o Aspose.Words adiciona uma pequena marca d'água ao arquivo salvo. Aplique sua licença logo no início do programa para evitá‑la.

## Etapa 1: Configurar o projeto e importar namespaces

Crie um novo projeto de console e adicione o pacote NuGet Aspose.Words.

```bash
dotnet new console -n WordTemplateDemo
cd WordTemplateDemo
dotnet add package Aspose.Words
```

Agora importe os namespaces necessários em `Program.cs`:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
```

Esses namespaces dão acesso às classes `Document`, `DocumentBuilder` e `StructuredDocumentTag`, que são essenciais para **create word document programmatically**.

## Etapa 2: Inicializar um documento em branco e um builder

A classe `Document` representa todo o arquivo .docx, enquanto `DocumentBuilder` permite inserir conteúdo em uma localização específica do cursor.

```csharp
// Step 2: Create an empty Word document
Document document = new Document();

// Step 2b: Initialize a DocumentBuilder for editing the document
DocumentBuilder builder = new DocumentBuilder(document);
```

*Por que isso importa*: Começar com um `Document` vazio garante que você tenha controle total sobre cada elemento inserido. O `DocumentBuilder` mantém um cursor interno, permitindo inserir nós exatamente onde você precisar.

## Etapa 3: Criar um Structured Document Tag (SDT) de texto simples

Um Structured Document Tag é o nome técnico para um **content control** no Word. Criaremos uma tag inline de texto simples que se comporta como um campo placeholder.

```csharp
// Step 3: Create a plain‑text Structured Document Tag (content control)
StructuredDocumentTag plainTextTag = new StructuredDocumentTag(
    document,
    StructuredDocumentTagType.PlainText,   // plain‑text content control
    MarkupLevel.Inline);                    // appears inside a paragraph
```

*Por que isso importa*: Usar `StructuredDocumentTagType.PlainText` indica ao Word que o controle aceitará apenas texto simples. `MarkupLevel.Inline` faz o controle se comportar como uma palavra regular dentro de um parágrafo, o que é ideal para campos de formulário.

## Etapa 4: Atribuir um título e texto placeholder

O **title** é o identificador interno que sua aplicação pode consultar posteriormente. O **placeholder** é a dica em cinza exibida ao usuário antes de digitar algo.

```csharp
// Step 4: Set a title and placeholder text for the content control
plainTextTag.Title = "CustomerName";          // internal name used by code
plainTextTag.PlaceholderName = "Enter name here"; // visible hint in the UI
```

Aqui definimos **set placeholder text word** para “Enter name here”. Quando o documento for aberto no Microsoft Word, o placeholder aparecerá em cinza claro até que o usuário digite um valor.

## Etapa 5: Inserir o content control na posição atual do cursor

`DocumentBuilder.InsertNode` coloca o SDT exatamente onde o cursor do builder está localizado. Por padrão, o cursor está no início do primeiro parágrafo.

```csharp
// Step 5: Insert the content control into the document at the builder's current position
builder.InsertNode(plainTextTag);
```

Se você precisar do controle dentro de um parágrafo específico, mova o cursor primeiro:

```csharp
builder.Writeln("Please provide the customer name:");
builder.InsertNode(plainTextTag);
```

Este exemplo demonstra como **add content control to word** preservando o texto ao redor.

## Etapa 6: Salvar o documento

Finalmente, persista o arquivo no disco. Você pode escolher qualquer pasta; apenas certifique‑se de que a aplicação tem permissão de escrita.

```csharp
// Step 6: Save the document with the content control
string outputPath = @"YOUR_DIRECTORY\SDT.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Ao abrir `SDT.docx` no Microsoft Word, você verá o placeholder “Enter name here” dentro de uma caixa cinza‑clara. Os usuários podem clicar na caixa e substituir a dica pelo nome real do cliente.

## Exemplo completo e executável

Abaixo está o programa completo que você pode copiar, colar e executar sem modificações (exceto o caminho de saída).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Optional: apply your Aspose.Words license here
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create a new empty document
        Document document = new Document();

        // 2. Initialize a DocumentBuilder for editing the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3. Write a brief instruction line (optional)
        builder.Writeln("Please enter the customer's name below:");

        // 4. Create a plain‑text Structured Document Tag (content control)
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(
            document,
            StructuredDocumentTagType.PlainText,
            MarkupLevel.Inline);

        // 5. Set a title and placeholder text for the content control
        plainTextTag.Title = "CustomerName";
        plainTextTag.PlaceholderName = "Enter name here";

        // 6. Insert the content control at the current cursor position
        builder.InsertNode(plainTextTag);

        // 7. Save the document
        string outputPath = @"C:\Temp\SDT.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Saída esperada** – Quando você executar o programa, o console imprime o caminho do arquivo, e o arquivo Word gerado contém uma única linha de texto seguida por um placeholder cinza que exibe “Enter name here”.

## Variações comuns e casos de borda

| Cenário | Como adaptar o código |
|----------|-----------------------|
| **Multi‑line placeholder** | Use `StructuredDocumentTagType.RichText` em vez de `PlainText` e defina `plainTextTag.MultipleLines = true;`. |
| **Repeating the same control** | Clone a tag com `plainTextTag.Clone(true)` e insira o clone onde for necessário. |
| **Binding to data source** | Depois que o usuário preencher o documento, recupere o valor com `document.GetChildNodes(NodeType.StructuredDocumentTag, true).Cast<StructuredDocumentTag>().First(t => t.Title == "CustomerName").GetText();`. |
| **Locking the control** | Defina `plainTextTag.LockContentControl = true;` para impedir que os usuários excluam o controle. |
| **Changing placeholder color** | O Word não expõe a estilização do placeholder através do SDK; você precisa editar o modelo manualmente ou usar uma macro do Word. |

## Boas práticas e solução de problemas

* **Always set a title** – Sem um título, localizar o controle mais tarde torna‑se complicado.
* **Avoid empty placeholders** – O Word oculta um placeholder vazio se a propriedade `ShowPlaceholderText` do controle for falsa. Mantenha‑a verdadeira para melhor UX.
* **Validate the output path** – Se `document.Save` lançar uma `UnauthorizedAccessException`, verifique se a pasta existe e se seu processo tem direitos de escrita.
* **License early** – Coloque o código da licença antes de qualquer objeto Aspose.Words ser instanciado para evitar a marca d'água da avaliação.

## Conclusão

Agora você sabe como **create word document programmatically**, **add content control to word** e **set placeholder text word** usando Aspose.Words para .NET. O exemplo completo demonstra cada passo necessário, desde a inicialização do documento até a persistência de um modelo que os usuários finais podem preencher.

Em seguida, você pode explorar:

* Adicionar **repeating content controls** para tabelas (palavra‑chave secundária: add content control to word).
* Preencher os placeholders com dados de um banco de dados (palavra‑chave secundária: set placeholder text word).
* Converter o .docx gerado para PDF ou HTML para processamento posterior.

Sinta‑se à vontade para experimentar diferentes tipos de tags, estilos e técnicas de vinculação de dados. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Criar novo documento Word](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Criar documento Word com cabeçalho e rodapé usando Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Criar um documento Word com tabela usando Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}