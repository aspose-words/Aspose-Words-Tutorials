---
category: general
date: 2026-09-18
description: Crie um documento Word em branco usando C# e defina um texto de espaço
  reservado, depois salve o documento como docx. Aprenda a inserir um controle de
  texto simples e adicionar o nome do espaço reservado.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set placeholder text
- save document as docx
- insert plain text control
- add placeholder name
language: pt
lastmod: 2026-09-18
og_description: Crie um documento Word em branco usando C#. Defina o texto do marcador
  de posição, insira um controle de texto simples, adicione o nome do marcador de
  posição e salve o documento como docx.
og_image_alt: Screenshot of a Word document showing a plain‑text content control with
  placeholder text
og_title: Criar documento Word em branco com texto de espaço reservado – Guia C#
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank Word document using C# and set placeholder text, then
    save document as docx. Learn to insert plain text control and add placeholder
    name.
  headline: Create blank Word document and insert a plain‑text control
  type: TechArticle
- description: Create blank Word document using C# and set placeholder text, then
    save document as docx. Learn to insert plain text control and add placeholder
    name.
  name: Create blank Word document and insert a plain‑text control
  steps:
  - name: An empty Word file (the **blank Word document** you created)
    text: An empty Word file (the **blank Word document** you created)
  - name: A plain‑text content control (the **insert plain text control** step)
    text: A plain‑text content control (the **insert plain text control** step)
  - name: Placeholder text that appears inside the control until the user types something
      (the **set placeholder text** step)
    text: Placeholder text that appears inside the control until the user types something
      (the **set placeholder text** step)
  - name: A placeholder name that can be used for programmatic access later (the **add
      placeholder name** step)
    text: A placeholder name that can be used for programmatic access later (the **add
      placeholder name** step)
  - name: A line of regular text after the control, demonstrating that normal content
      can follow
    text: A line of regular text after the control, demonstrating that normal content
      can follow
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Criar documento Word em branco e inserir um controle de texto simples
url: /pt/java/using-document-elements/create-blank-word-document-and-insert-a-plain-text-control/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar documento Word em branco e inserir um controle de texto simples

Se você precisar **criar documento Word em branco** programaticamente, este guia mostra como fazer isso com C#. Você aprenderá a **inserir controle de texto simples**, **definir texto de espaço reservado**, **adicionar nome do espaço reservado** e, finalmente, **salvar o documento como docx**. As etapas são totalmente autônomas, de modo que você pode copiar o código para qualquer projeto .NET e executá‑lo imediatamente.

Trabalhar com arquivos Word costuma exigir um ponto de partida limpo — um documento vazio que já contém os controles que seus usuários preencherão. Ao final deste tutorial você terá um arquivo `.docx` que contém um controle de conteúdo de texto simples com um espaço reservado útil, seguido por conteúdo regular.

## Pré‑requisitos

- .NET 6.0 ou posterior (o código também funciona com .NET Framework 4.6+)
- Uma referência à biblioteca **Aspose.Words for .NET** (disponível via NuGet `Install-Package Aspose.Words`)
- Familiaridade básica com aplicações console C#
- Permissão de gravação na pasta de saída que você especificar em `doc.save(...)`

## O que você vai construir

O documento final (`SDT.docx`) contém:

1. Um arquivo Word vazio (o **documento Word em branco** que você criou)
2. Um controle de conteúdo de texto simples (a etapa **inserir controle de texto simples**)
3. Texto de espaço reservado que aparece dentro do controle até o usuário digitar algo (a etapa **definir texto de espaço reservado**)
4. Um nome de espaço reservado que pode ser usado para acesso programático posterior (a etapa **adicionar nome do espaço reservado**)
5. Uma linha de texto regular após o controle, demonstrando que conteúdo normal pode seguir

## Etapa 1: Criar um documento Word em branco

A primeira operação é instanciar um objeto `Document` vazio. Esse objeto representa um **documento Word em branco** completamente novo na memória.

```csharp
using Aspose.Words;
using Aspose.Words.BuildingBlocks;

// Step 1: Create a new blank document
Document doc = new Document();
```

*Por que isso importa:* Um `Document` vazio lhe dá controle total sobre cada elemento que você adiciona, garantindo que nenhum estilo ou seção ocultos interfiram no controle de conteúdo que será inserido mais tarde.

## Etapa 2: Inicializar um DocumentBuilder

`DocumentBuilder` é a classe auxiliar que permite escrever no `Document`. Ela rastreia a posição atual do cursor e fornece métodos para inserir todos os tipos de objetos Word.

```csharp
// Step 2: Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Por que isso importa:* Usar um `DocumentBuilder` simplifica o processo de adicionar um **controle de texto simples** porque o builder conhece o ponto exato de inserção.

## Etapa 3: Inserir controle de texto simples

Agora adicionamos um **controle de conteúdo de texto simples** (também conhecido como Structured Document Tag, ou SDT). O tipo de controle `StructuredDocumentTagType.PLAIN_TEXT` indica ao Word que o conteúdo deve ser tratado como texto simples, não como formatação rica.

```csharp
// Step 3: Insert a plain‑text StructuredDocumentTag (SDT) with a tag ID
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");
```

*Por que isso importa:* O método `InsertStructuredDocumentTag` cria o controle e devolve uma referência (`sdt`) que você pode configurar ainda mais, como adicionar texto de espaço reservado ou um nome personalizado.

## Etapa 4: Definir texto de espaço reservado e adicionar nome do espaço reservado

O texto de espaço reservado oferece aos usuários uma pista visual sobre o que digitar. A etapa **adicionar nome do espaço reservado** atribui um identificador programático que você pode consultar depois com `doc.GetChildNodes` ou APIs semelhantes.

```csharp
// Step 4a: Set a placeholder text that appears when the SDT is empty
sdt.SetPlaceholderName("Enter text…");

// Step 4b: Add a placeholder name (tag ID) for later retrieval
sdt.Tag = "MyTag";
```

*Por que isso importa:* `SetPlaceholderName` controla o texto de dica cinza exibido dentro do controle de conteúdo. Definir `Tag` (a ação **adicionar nome do espaço reservado**) permite localizar o controle na árvore do documento sem precisar escanear todo o arquivo.

## Etapa 5: Adicionar conteúdo regular após o controle

Para provar que o documento continua normalmente após o controle, escrevemos uma linha simples de texto.

```csharp
// Step 5: Add regular content after the SDT
builder.Writeln("After the tag.");
```

## Etapa 6: Salvar documento como docx

Finalmente, persistimos o documento em memória no disco. Esta é a operação **salvar documento como docx** que produz o arquivo que você pode abrir no Microsoft Word.

```csharp
// Step 6: Save the document as a .docx file
string outputPath = @"YOUR_DIRECTORY/SDT.docx";
doc.Save(outputPath);
```

*Por que isso importa:* Usar o formato `.docx` garante a máxima compatibilidade com versões modernas do Word, Google Docs e outras ferramentas compatíveis com Office.

## Exemplo completo e executável

Abaixo está o programa completo que você pode copiar para um projeto console‑app. Substitua `YOUR_DIRECTORY` por um caminho de pasta real na sua máquina.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.BuildingBlocks;

namespace WordSdtExample
{
    class Program
    {
        static void Main()
        {
            // Create a new blank Word document
            Document doc = new Document();

            // Initialize a DocumentBuilder to work with the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a plain‑text StructuredDocumentTag (SDT) with a tag ID
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");

            // Set a placeholder text that appears when the SDT is empty
            sdt.SetPlaceholderName("Enter text…");

            // Add a placeholder name (tag) for later retrieval
            sdt.Tag = "MyTag";

            // Add regular content after the SDT
            builder.Writeln("After the tag.");

            // Save the document as a .docx file
            string outputPath = @"C:\Temp\SDT.docx"; // change to your folder
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

### Resultado esperado

- Ao abrir `SDT.docx` no Word, aparece uma caixa cinza vazia com o texto **Enter text…** dentro.
- A caixa é um controle de conteúdo de texto simples; você pode digitar diretamente nela.
- Abaixo da caixa, a linha **After the tag.** aparece como texto de parágrafo regular.

Se o espaço reservado não aparecer, verifique se você está usando uma versão recente do Aspose.Words (v23.1 ou posterior) e se o documento está aberto em uma versão do Word que suporte controles de conteúdo (Word 2007+).

## Variações comuns e casos de borda

| Cenário | Como adaptar o código |
|----------|-----------------------|
| **Multiple placeholders** | Call `InsertStructuredDocumentTag` again with a different tag ID and placeholder name. |
| **Rich‑text control** | Use `StructuredDocumentTagType.RichText` instead of `PlainText`. |
| **Setting default text** | After insertion, assign `sdt.Text = "Default value";` – this text replaces the placeholder when the document loads. |
| **Saving to a stream** | Replace `doc.Save(outputPath);` with `doc.Save(stream, SaveFormat.Docx);` to send the file over HTTP. |
| **Changing placeholder color** | Use `sdt.PlaceholderTextColor = System.Drawing.Color.Gray;` (requires `using System.Drawing`). |

## Dicas profissionais

- **Reuse the tag ID**: Keeping the tag (`MyTag`) consistent across documents lets you automate data population later with `doc.Range.Replace` or the `StructuredDocumentTagCollection`.
- **Avoid hard‑coded paths**: Use `Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), "SDT.docx")` for a portable output location.
- **Performance**: If you need to generate thousands of documents, create a single `Document` template with the SDT already present, then clone it with `doc.Clone()` for each iteration.

## Conclusão

Agora você sabe como **criar documento Word em branco**, **inserir controle de texto simples**, **definir texto de espaço reservado**, **adicionar nome do espaço reservado** e **salvar documento como docx** usando Aspose.Words for .NET. Esse padrão forma a base para construir modelos Word preenchidos por formulários, relatórios automatizados ou qualquer solução que exija espaços reservados editáveis pelo usuário.

Sinta‑se à vontade para experimentar outros tipos de controle, combinar múltiplos espaços reservados ou integrar este código em uma API web que devolva o arquivo `.docx` gerado diretamente aos chamadores. Para o próximo passo, explore **preencher um controle de conteúdo com dados programaticamente** ou **converter o arquivo Word gerado para PDF** usando os recursos de conversão nativos do Aspose.Words. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Inserir campo de formulário de entrada de texto em documento Word](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)
- [Criar um documento Word com tabela usando Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Criar documento Word com cabeçalho e rodapé usando Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}