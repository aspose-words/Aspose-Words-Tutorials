---
category: general
date: 2026-11-22
description: Criar programaticamente um documento Word em C# e inserir forma retangular,
  inserir múltiplas formas e escrever as formas no Word usando Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically create word document
- insert rectangle shape
- insert multiple shapes
- write shapes to word
language: pt
lastmod: 2026-11-22
og_description: Criar programaticamente um documento Word em C# inserindo forma retangular,
  inserindo múltiplas formas e gravando as formas no Word usando Aspose.Words.
og_image_alt: Screenshot of a Word document showing a rectangle and an ellipse grouped
  together
og_title: Criar programaticamente um documento Word com formas em C#
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  headline: Programmatically create Word document with shapes in C#
  type: TechArticle
- description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  name: Programmatically create Word document with shapes in C#
  steps:
  - name: '**Initialize** a new `Document` and a `DocumentBuilder`.'
    text: '**Initialize** a new `Document` and a `DocumentBuilder`.'
  - name: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
    text: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
  - name: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
    text: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Criar programaticamente um documento Word com formas em C#
url: /pt/net/programming-with-shapes/programmatically-create-word-document-with-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar documento Word programaticamente com formas em C#

Se você precisa **criar um documento Word programaticamente** que contenha gráficos personalizados, este guia mostra como fazer isso com Aspose.Words para .NET. Você aprenderá a inserir uma forma retangular, adicionar formas adicionais, agrupá‑las e, finalmente, gravar as formas no Word — tudo em poucas linhas de C#.

Criar um arquivo Word com gráficos não requer mais edição manual ou scripts de macro. Ao final deste tutorial você terá um método reutilizável que produz um arquivo `.docx` contendo um retângulo e uma elipse agrupados, pronto para processamento posterior ou geração de relatórios.

## O que você precisará

- .NET 6.0 ou posterior (o código também funciona com .NET Framework 4.6+)
- Aspose.Words para .NET (pacote NuGet `Aspose.Words`)
- Uma IDE como Visual Studio 2022 (qualquer editor que compile C# serve)

> **Dica profissional:** Instale o pacote com o comando CLI `dotnet add package Aspose.Words` antes de começar a codificar.

## Criar documento Word programaticamente – visão geral

O fluxo geral consiste em três fases lógicas:

1. **Inicializar** um novo `Document` e um `DocumentBuilder`.  
2. **Inserir várias formas** (um retângulo e uma elipse) e colocá‑las dentro de um `GroupShape`.  
3. **Gravar as formas no Word** salvando o `Document` em um arquivo `.docx`.

Cada fase está encapsulada em uma etapa dedicada abaixo, para que você possa copiar‑colar o código diretamente no seu projeto.

![Programmatically create Word document with grouped shapes](grouped-shapes.png){: .align-center alt="Criar documento Word programaticamente com formas agrupadas"}

## Etapa 1: Inicializar o documento e o DocumentBuilder

A classe `Document` representa todo o arquivo Word, enquanto `DocumentBuilder` fornece uma API fluente para adicionar conteúdo.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document document = new Document();

// Initialize a DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(document);
```

*Por que isso importa:* Criar o `Document` primeiro fornece uma tela limpa. O `DocumentBuilder` rastreia o ponto de inserção atual, o que é essencial quando você posteriormente anexa formas a uma hierarquia de parágrafos.

## Etapa 2: Inserir um contêiner de forma de grupo

Um `GroupShape` permite tratar várias formas individuais como uma única unidade. Isso é útil quando você deseja mover ou redimensionar todas juntas.

```csharp
// Insert a group shape container at the current cursor position
GroupShape groupShape = builder.InsertGroupShape();
```

*Explicação:* `InsertGroupShape` insere um contêiner vazio e o define automaticamente como a forma atual. Todas as inserções de forma subsequentes serão adicionadas a esse contêiner até que você feche o grupo.

## Inserir forma retangular

Agora adicionamos o primeiro gráfico — um retângulo. Isso satisfaz o requisito de **inserir forma retangular**.

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

O retângulo herda o contexto de formatação do grupo, portanto aparece dentro do `GroupShape`. Você também pode definir cor da linha, preenchimento ou texto posteriormente, se necessário.

## Inserir várias formas

Para demonstrar a capacidade de **inserir várias formas**, adicionamos uma elipse logo após o retângulo. Você pode continuar adicionando quantas formas quiser (por exemplo, triângulos, estrelas) antes de fechar o grupo.

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

Neste ponto o grupo contém duas formas distintas: um retângulo e uma elipse. Como elas compartilham o mesmo pai, você pode movê‑las como uma única unidade.

## Etapa 3: Anexar a forma de grupo à hierarquia de parágrafos

Documentos Word armazenam o conteúdo em uma árvore de parágrafos. Para que o grupo fique visível no arquivo final, precisamos anexá‑lo ao parágrafo atual.

```csharp
// Append the group shape to the current paragraph so it becomes part of the document flow
groupShape.AppendChild(builder.CurrentParagraph);
```

*Por que esta etapa é necessária:* Sem anexar o grupo a um parágrafo, as formas existem apenas na memória e são omitidas quando o documento é salvo.

## Etapa 4: Salvar o documento – escrever formas no Word

Finalmente, persistimos o `Document` em memória no disco. Isso cumpre o objetivo de **gravar formas no Word**.

```csharp
// Define the output path (adjust the folder as needed)
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");

// Save the document in DOCX format
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Ao abrir `GroupShape.docx` no Microsoft Word, você verá um retângulo e uma elipse agrupados, exatamente como o código inseriu.

### Saída esperada

- Um arquivo chamado **GroupShape.docx** localizado na pasta de saída do projeto.  
- Dentro do arquivo Word: um único parágrafo contendo um retângulo agrupado (100 pt × 50 pt) e uma elipse (80 pt × 40 pt). Selecionar qualquer forma seleciona todo o grupo.

## Lidando com casos de borda comuns

| Situação | Recomendação |
|-----------|----------------|
| **DPI ou tamanho de página diferentes** | Defina explicitamente `builder.PageSetup.PaperSize` antes de inserir as formas para evitar dimensionamento inesperado. |
| **Precisa posicionar as formas com precisão** | Use `builder.MoveTo` para mover o ponto de inserção, então ajuste as propriedades `groupShape.Left` e `groupShape.Top` (os valores são em pontos). |


## O que você deve aprender a seguir?


Os tutoriais a seguir abordam tópicos estreitamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Create Word Document – Insert Rectangle Shape & Shadow in C#](/words/english/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/)
- [Create word document programmatically and group shapes in C#](/words/english/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/)
- [Programmatically create a Word document with a group shape](/words/english/net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}