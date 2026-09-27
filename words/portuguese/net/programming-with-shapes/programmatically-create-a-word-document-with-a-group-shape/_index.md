---
category: general
date: 2026-09-27
description: Crie programaticamente um documento Word com um grupo de formas usando
  Aspose.Words em C#. Siga este guia passo a passo para gerar o arquivo e aprender
  dicas úteis.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically create word document
- how to create group shape word
- Aspose.Words group shape
- C# Word automation
- StructuredDocumentTag example
language: pt
lastmod: 2026-09-27
og_description: Crie programaticamente um documento Word com um grupo de formas usando
  Aspose.Words. Este tutorial guia você pelo código completo em C#, explica cada passo
  e mostra o resultado final.
og_image_alt: Screenshot of a Word document containing a group shape with a text placeholder
og_title: Criar programaticamente um documento Word com um grupo de formas – guia
  C#
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Programmatically create a Word document with a group shape using Aspose.Words
    in C#. Follow this step‑by‑step guide to generate the file and learn useful tips.
  headline: Programmatically create a Word document with a group shape
  type: TechArticle
- description: Programmatically create a Word document with a group shape using Aspose.Words
    in C#. Follow this step‑by‑step guide to generate the file and learn useful tips.
  name: Programmatically create a Word document with a group shape
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code also works with .NET Framework 4.7+). - Aspose.Words
      for .NET NuGet package (`Install-Package Aspose.Words`). - A C# IDE such as
      Visual Studio 2022 or VS Code with the C# extension.'
  - name: Expected output screenshot (conceptual)
    text: '``` +-----------------------------------------------------------+ | ┌───────────────────────────────────────────────┐
      | | │ [Enter text here] │ | | └───────────────────────────────────────────────┘
      | +-----------------------------------------------------------+ ```'
  - name: Adding more child shapes
    text: 'You can enrich the group by appending additional drawing objects, such
      as pictures or text boxes:'
  - name: Controlling wrapping style
    text: 'If you need the group shape to stay behind text or to have tight wrapping,
      set the `WrapType` property:'
  - name: 'Edge case: Empty group shape'
    text: A `GroupShape` without children renders as an invisible placeholder. Always
      verify that at least one child (e.g., an SDT or a picture) is added; otherwise
      Word may drop the group during saving.
  - name: Compatibility note
    text: Aspose.Words 23.10+ fully supports `GroupShape` and `StructuredDocumentTag`.
      If you target older versions, the `AppendChild` method may behave differently,
      and you might need to call `UpdatePageLayout` after saving.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Criar programaticamente um documento Word com um grupo de formas
url: /pt/net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar programaticamente um documento Word com um shape de grupo

Se você precisa **criar programaticamente um documento Word** que contenha um desenho agrupado, este guia mostra exatamente como fazer isso com Aspose.Words para .NET. Seja você quem está desenvolvendo um gerador de contratos, um criador de relatórios ou uma ferramenta de preenchimento de formulários, aprenderá o código C# completo, por que cada chamada de API é importante e como lidar com casos de borda comuns.

Criar um shape agrupado no Word pode parecer complicado porque o modelo de objetos do Word trata os group shapes como contêineres para outros objetos de desenho. Este tutorial não apenas responde **como criar documentos Word com group shape**, mas também demonstra como incorporar um StructuredDocumentTag (SDT) de texto simples dentro do grupo, permitindo que o shape contenha conteúdo editável.

## O que você irá alcançar

- Inicializar um novo documento Word em branco com `Document` e `DocumentBuilder`.
- Inserir um `GroupShape` na posição atual do cursor.
- Adicionar um `StructuredDocumentTag` (SDT) de texto simples ao shape de grupo.
- Salvar o arquivo como `.docx` que pode ser aberto no Microsoft Word.
- Compreender as principais propriedades de `GroupShape` e `StructuredDocumentTag` para extensões futuras.

### Pré-requisitos

- .NET 6.0 ou posterior (o código também funciona com .NET Framework 4.7+).
- Pacote NuGet Aspose.Words para .NET (`Install-Package Aspose.Words`).
- Uma IDE C# como Visual Studio 2022 ou VS Code com a extensão C#.

---

## Criar programaticamente um documento Word – configurar o projeto

1. **Criar um novo projeto de console**  
   ```bash
   dotnet new console -n WordGroupShapeDemo
   cd WordGroupShapeDemo
   dotnet add package Aspose.Words
   ```
2. **Abrir o projeto na sua IDE** e substituir o conteúdo de `Program.cs` pelo código mostrado nas próximas seções.

> **Dica profissional:** Mantenha a pasta do projeto limpa; o Aspose.Words grava o arquivo de saída no diretório de trabalho, a menos que você forneça um caminho absoluto.

## Etapa 1: Inicializar o documento e o builder

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;

// Create a new blank document.
Document doc = new Document();

// DocumentBuilder gives you a cursor to insert nodes.
DocumentBuilder builder = new DocumentBuilder(doc);

// Optional: set the page size or margins if your shape must fit a specific area.
builder.PageSetup.PageWidth = 595;   // A4 width in points
builder.PageSetup.PageHeight = 842;  // A4 height in points
```

**Por que isso importa:**  
`Document` representa todo o arquivo Word, enquanto `DocumentBuilder` permite posicionar novos elementos sem navegar manualmente pela árvore de nós. Definir as dimensões da página antecipadamente garante que o group shape não ultrapasse a página.

## Etapa 2: Inserir um GroupShape na posição atual do cursor

```csharp
// Create an empty GroupShape container.
GroupShape groupShape = new GroupShape(doc)
{
    // Give the group a size that comfortably holds its children.
    Width = 300,
    Height = 150,

    // Position the group relative to the page (you can also use RelativeHorizontalPosition).
    Left = 100,
    Top = 100
};

// Insert the group shape into the document where the builder is currently positioned.
builder.InsertNode(groupShape);
```

**Explicação:**  
Um `GroupShape` é um objeto de desenho que pode conter outras formas, imagens ou caixas de texto. Ao definir `Width`, `Height`, `Left` e `Top`, você controla sua posição exata na página. O método `InsertNode` coloca o shape no fluxo principal do documento, comportando‑se como um objeto flutuante.

## Etapa 3: Adicionar um StructuredDocumentTag (SDT) de texto simples dentro do grupo

```csharp
// Create a plain‑text SDT that will act as a content placeholder.
StructuredDocumentTag sdtTag = new StructuredDocumentTag(doc, SdtType.PlainText, true)
{
    // Provide a helpful tag title that appears as a tooltip in Word.
    Title = "GroupShapeText",
    // Set default placeholder text.
    PlaceholderName = "Enter text here"
};

// Append the SDT to the group shape's child collection.
groupShape.AppendChild(sdtTag);
```

**Por que usar um SDT?**  
StructuredDocumentTags são os controles de conteúdo nativos do Word. Eles permitem que os usuários editem o texto diretamente no documento salvo e podem ser acessados programaticamente mais tarde para extração de dados. Inserir um SDT dentro de um group shape permite combinar agrupamento visual com conteúdo editável.

## Etapa 4: Salvar o documento

```csharp
// Define the output path – replace with your desired directory.
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShapeDemo.docx");

// Save the document in DOCX format.
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved to: {outputPath}");
```

**Resultado:**  
Abrir `GroupShapeDemo.docx` no Microsoft Word exibe um retângulo flutuante (o group shape) contendo um placeholder de texto que diz “Enter text here”. Os usuários podem clicar dentro do shape e digitar diretamente.

### Captura de tela esperada (conceitual)

```
+-----------------------------------------------------------+
|   ┌───────────────────────────────────────────────┐   |
|   │  [Enter text here]                               │   |
|   └───────────────────────────────────────────────┘   |
+-----------------------------------------------------------+
```

A caixa externa é o `GroupShape`; a área cinza interna é o `StructuredDocumentTag`.

---

## Como criar group shape word – considerações adicionais

### Adicionando mais shapes filhos

Você pode enriquecer o grupo anexando objetos de desenho adicionais, como imagens ou caixas de texto:

```csharp
// Example: add a picture inside the same group.
Shape picture = new Shape(doc, ShapeType.Image)
{
    ImageData = ImageData.FromFile("logo.png"),
    Width = 100,
    Height = 50,
    Left = 10,
    Top = 80
};
groupShape.AppendChild(picture);
```

### Controlando o estilo de quebra de texto

Se precisar que o group shape fique atrás do texto ou tenha quebra apertada, defina a propriedade `WrapType`:

```csharp
groupShape.WrapType = WrapType.Inline; // Makes the shape behave like a paragraph.
```

### Caso de borda: GroupShape vazio

Um `GroupShape` sem filhos é renderizado como um placeholder invisível. Sempre verifique se ao menos um filho (por exemplo, um SDT ou uma imagem) foi adicionado; caso contrário, o Word pode remover o grupo ao salvar.

### Nota de compatibilidade

Aspose.Words 23.10+ oferece suporte total a `GroupShape` e `StructuredDocumentTag`. Se você direcionar versões mais antigas, o método `AppendChild` pode se comportar de forma diferente, e talvez seja necessário chamar `UpdatePageLayout` após a gravação.

---

## Exemplo completo executável

Copie o trecho completo abaixo para `Program.cs` e execute o projeto. O código inclui todas as etapas acima em um único programa autônomo.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.PageSetup.PageWidth = 595;
        builder.PageSetup.PageHeight = 842;

        // 2️⃣ Create and insert a GroupShape.
        GroupShape groupShape = new GroupShape(doc)
        {
            Width = 300,
            Height = 150,
            Left = 100,
            Top = 100
        };
        builder.InsertNode(groupShape);

        // 3️⃣ Add a plain‑text StructuredDocumentTag (SDT) inside the group.
        StructuredDocumentTag sdtTag = new StructuredDocumentTag(doc, SdtType.PlainText, true)
        {
            Title = "GroupShapeText",
            PlaceholderName = "Enter text here"
        };
        groupShape.AppendChild(sdtTag);

        // 4️⃣ Optional: add a picture to demonstrate multiple children.
        // Uncomment and adjust the path if you want to test this.
        /*
        Shape picture = new Shape(doc, ShapeType.Image)
        {
            ImageData = ImageData.FromFile("logo.png"),
            Width = 100,
            Height = 50,
            Left


## O que você deve aprender a seguir?


Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}