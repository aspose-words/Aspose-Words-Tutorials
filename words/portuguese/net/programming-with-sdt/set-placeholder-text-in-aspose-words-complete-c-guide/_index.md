---
category: general
date: 2026-07-19
description: Defina o texto de espaço reservado em um StructuredDocumentTag com Aspose.Words.
  Aprenda como adicionar controle, mover para o controle e definir o atributo da tag
  em C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set placeholder text
- move to control
- how to add control
- how to create sdt
- set tag attribute
language: pt
lastmod: 2026-07-19
og_description: Defina texto de espaço reservado em um StructuredDocumentTag usando
  Aspose.Words. Siga este guia passo a passo para adicionar controle, mover para o
  controle e definir o atributo da tag.
og_image_alt: Screenshot showing a Word document with placeholder text inside a content
  control created by Aspose.Words
og_title: Definir Texto de Espaço Reservado no Aspose.Words – Tutorial Rápido de C#
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Set placeholder text in a StructuredDocumentTag with Aspose.Words.
    Learn how to add control, move to control and set tag attribute in C#.
  headline: Set Placeholder Text in Aspose.Words – Complete C# Guide
  type: TechArticle
- description: Set placeholder text in a StructuredDocumentTag with Aspose.Words.
    Learn how to add control, move to control and set tag attribute in C#.
  name: Set Placeholder Text in Aspose.Words – Complete C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6+ (or .NET Framework 4.7.2) – the code works on any recent runtime.
      - Aspose.Words for .NET (NuGet package `Aspose.Words` version 23.12 or later).
      - A basic understanding of C# and Visual Studio (or your favorite IDE).'
  - name: Expected Result
    text: 'Open `SDTExample.docx` in Microsoft Word:'
  - name: What if I need a **dropdown** instead of plain text?
    text: Replace `SdtType.PlainText` with `SdtType.DropDownList` and populate the
      `ListItems` collection. The rest of the workflow—`InsertNode`, `MoveTo`, `SetTagAttribute`—remains
      the same.
  - name: Can I **set the tag attribute** after insertion?
    text: 'Absolutely. The `Tag` property can be modified at any time:'
  - name: How do I **find a control later** in a large document?
    text: Use the `Document.GetChildNodes(NodeType.StructuredDocumentTag, true)` method
      and filter by `Tag` or `Title`. This is handy when you need to replace placeholder
      text in bulk.
  - name: What if I want the placeholder to appear in **all languages**?
    text: Aspose.Words supports localized placeholder text via the `PlaceholderName`
      property. Set it to a resource string that varies per culture.
  type: HowTo
tags:
- Aspose.Words
- C#
- ContentControl
title: Definir Texto de Espaço Reservado no Aspose.Words – Guia Completo de C#
url: /pt/net/programming-with-sdt/set-placeholder-text-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Definir Texto de Espaço Reservado no Aspose.Words – Guia Completo em C#

Já se perguntou como **definir texto de espaço reservado** dentro de um controle de conteúdo do Word usando Aspose.Words? Você não está sozinho. Seja construindo um mecanismo de geração de documentos ou apenas precisando de um modelo reutilizável, saber como adicionar controle, mover para o controle e definir o atributo de tag é essencial.

Neste tutorial percorreremos um exemplo real que mostra exatamente como criar um SDT (StructuredDocumentTag), atribuir uma tag, definir texto de espaço reservado e escrever conteúdo padrão — tudo em C# puro. Ao final, você terá um trecho pronto‑para‑executar que pode ser inserido em qualquer projeto .NET.

## O que você aprenderá

- Como **criar SDT** (StructuredDocumentTag) programaticamente.  
- A forma correta de **definir texto de espaço reservado** para que os usuários vejam sugestões úteis.  
- Usar **move to control** para posicionar o cursor dentro do controle recém‑adicionado.  
- Atribuir um **atributo de tag** para identificação posterior.  
- Salvar o documento e verificar o resultado.

### Pré‑requisitos

- .NET 6+ (ou .NET Framework 4.7.2) – o código funciona em qualquer runtime recente.  
- Aspose.Words for .NET (pacote NuGet `Aspose.Words` versão 23.12 ou superior).  
- Noções básicas de C# e Visual Studio (ou sua IDE favorita).

Nenhuma outra biblioteca externa é necessária.

## Etapa 1: Inicializar o Document e o Builder

Primeiro de tudo — crie um `Document` vazio e um `DocumentBuilder`. O builder é seu pincel; o documento é a tela.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

// Create a brand‑new blank document.
Document document = new Document();

// DocumentBuilder lets us insert text, tables, and controls.
DocumentBuilder docBuilder = new DocumentBuilder(document);
```

> **Por que isso importa:** Começar com um `Document` limpo garante que o espaço reservado que definiremos depois não entre em conflito com conteúdo existente.

## Etapa 2: Criar o StructuredDocumentTag (SDT)

Agora vamos **como criar sdt** – um controle de conteúdo que pode conter texto simples, datas, listas suspensas etc. Neste caso precisamos de um controle de texto simples.

```csharp
// Create a plain‑text StructuredDocumentTag (content control).
StructuredDocumentTag plainTextSdt = new StructuredDocumentTag(
    document, SdtType.PlainText, true);

// Give the control a friendly name and a tag for later lookup.
plainTextSdt.Title = "CustomerName";
plainTextSdt.Tag   = "CustomerNameTag";

// Here’s the crucial part: set the placeholder text that the user sees.
plainTextSdt.PlaceholderText = "Enter name here";
```

> **Dica profissional:** A propriedade `PlaceholderText` é o que o usuário vê antes de digitar qualquer coisa. Ela difere do texto padrão que você pode escrever posteriormente.

## Etapa 3: Inserir o Controle no Documento

Com o SDT pronto, precisamos **como adicionar controle** ao documento. O método `InsertNode` faz exatamente isso.

```csharp
// Insert the content control at the current cursor position.
docBuilder.InsertNode(plainTextSdt);
```

> **O que acontece nos bastidores?** `InsertNode` coloca o SDT como filho do parágrafo atual, preservando qualquer formatação ao redor.

## Etapa 4: Mover para o Controle e Escrever Conteúdo Padrão (Opcional)

Se quiser pré‑popular o controle com um valor (por exemplo, um nome de cliente padrão), primeiro **move to control** e então escreva.

```csharp
// Optionally clear the placeholder and write a default name.
plainTextSdt.RemoveAllChildren();          // Remove the placeholder node.
docBuilder.MoveTo(plainTextSdt);           // Move cursor inside the SDT.
docBuilder.Write("John Doe");              // Write default text.
```

> **Por que removemos o espaço reservado:** O espaço reservado é uma pista visual, não conteúdo real do documento. Removê‑lo antes de escrever garante que o documento final contenha apenas o texto real.

## Etapa 5: Salvar o Documento

Por fim, persista o arquivo no disco. Você também pode transmiti‑lo como resposta em um aplicativo web — basta substituir a chamada `Save`.

```csharp
// Save the Word document to the desired location.
document.Save("C:/Temp/SDTExample.docx");
```

### Resultado Esperado

Abra `SDTExample.docx` no Microsoft Word:

- Você verá um controle de conteúdo de texto simples intitulado **CustomerName**.  
- O controle exibe “Enter name here” como texto de espaço reservado em tom claro (se você não escreveu conteúdo padrão).  
- Se manteve a linha `Write("John Doe")`, “John Doe” aparecerá dentro do controle e o espaço reservado desaparecerá.

## Exemplo Completo Funcional

A seguir está o programa completo, pronto para copiar e colar. Ele inclui todas as etapas acima, além de algumas verificações defensivas.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialise document and builder.
        Document document = new Document();
        DocumentBuilder docBuilder = new DocumentBuilder(document);

        // 2️⃣ Create a plain‑text SDT (content control).
        StructuredDocumentTag plainTextSdt = new StructuredDocumentTag(
            document, SdtType.PlainText, true);
        plainTextSdt.Title = "CustomerName";
        plainTextSdt.Tag   = "CustomerNameTag";
        plainTextSdt.PlaceholderText = "Enter name here";

        // 3️⃣ Insert the control into the document.
        docBuilder.InsertNode(plainTextSdt);

        // 4️⃣ (Optional) Move to the control and set default text.
        plainTextSdt.RemoveAllChildren();   // Clear placeholder.
        docBuilder.MoveTo(plainTextSdt);    // Move cursor inside.
        docBuilder.Write("John Doe");       // Write default value.

        // 5️⃣ Save the file.
        string outputPath = @"C:\Temp\SDTExample.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Execute o programa, abra o arquivo gerado e você verá tudo funcionando exatamente como descrito.

## Perguntas Frequentes & Casos de Borda

### E se eu precisar de um **dropdown** em vez de texto simples?

Substitua `SdtType.PlainText` por `SdtType.DropDownList` e preencha a coleção `ListItems`. O restante do fluxo — `InsertNode`, `MoveTo`, `SetTagAttribute` — permanece o mesmo.

### Posso **definir o atributo de tag** após a inserção?

Com certeza. A propriedade `Tag` pode ser modificada a qualquer momento:

```csharp
plainTextSdt.Tag = "NewTagValue";
```

Apenas lembre‑se de salvar o documento novamente para que a alteração persista.

### Como **encontrar um controle** mais tarde em um documento grande?

Use o método `Document.GetChildNodes(NodeType.StructuredDocumentTag, true)` e filtre por `Tag` ou `Title`. Isso é útil quando você precisa substituir textos de espaço reservado em massa.

```csharp
foreach (StructuredDocumentTag sdt in document.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
    if (sdt.Tag == "CustomerNameTag")
    {
        // Do something with this control.
    }
}
```

### E se eu quiser que o espaço reservado apareça em **todos os idiomas**?

Aspose.Words suporta texto de espaço reservado localizado via a propriedade `PlaceholderName`. Defina‑a para uma string de recurso que varia conforme a cultura.

## Dicas & Truques (Pro Tips)

- **Reutilize o mesmo SDT** em vários documentos clonando‑o (`plainTextSdt.Clone(true)`), e então inserindo a cópia onde for necessário.  
- **Evite tags duplicadas**; elas tornam a busca posterior ambígua. Mantenha as tags únicas por documento.  
- **Dica de desempenho:** Se estiver gerando milhares de documentos, reutilize uma única instância de `Document` como modelo e apenas substitua o texto de espaço reservado. Isso reduz a sobrecarga de criação de objetos.

## Conclusão

Cobremos tudo o que você precisa para **definir texto de espaço reservado** em um StructuredDocumentTag do Aspose.Words, desde a criação do controle até mover‑se até ele, escrever conteúdo padrão e atribuir um atributo de tag. Com esse conhecimento, você pode construir modelos Word dinâmicos que orientam os usuários, impõem regras de entrada de dados e permanecem fáceis de manter.

Pronto para o próximo desafio? Experimente trocar o SDT de texto simples por um **date picker** ou um **combo box**, ou explore como vincular SDTs a fontes de dados XML para uma automação de documentos ainda mais avançada.

Boa codificação, e que seus documentos estejam sempre perfeitamente modelados!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Definir estilo de controle de conteúdo](/words/hindi/net/programming-with-sdt/set-content-control-style/)
- [Definir cor de controle de conteúdo](/words/hindi/net/programming-with-sdt/set-content-control-color/)
- [Como criar campos de formulário e adicionar conteúdo usando DocumentBuilder no Aspose.Words para Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}