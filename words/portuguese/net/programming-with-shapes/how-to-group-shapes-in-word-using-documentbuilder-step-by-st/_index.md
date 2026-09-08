---
category: general
date: 2026-09-08
description: Aprenda a agrupar formas no Word com um DocumentBuilder, criar um documento
  Word em branco e inserir uma forma retangular em apenas algumas linhas de código
  C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create blank word doc
- insert rectangle shape word
- how to use documentbuilder
language: pt
lastmod: 2026-09-08
og_description: Agrupe formas no Word usando DocumentBuilder. Este tutorial mostra
  como criar um documento Word em branco, inserir uma forma retangular e combinar
  formas em um GroupShape.
og_image_alt: Screenshot of a Word document showing grouped shapes – group shapes
  in Word example
og_title: Agrupar formas no Word com DocumentBuilder – exemplo completo em C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to group shapes in Word with a DocumentBuilder, create a
    blank Word doc, and insert a rectangle shape in just a few lines of C# code.
  headline: How to group shapes in Word using DocumentBuilder – step‑by‑step guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Como agrupar formas no Word usando DocumentBuilder – guia passo a passo
url: /pt/net/programming-with-shapes/how-to-group-shapes-in-word-using-documentbuilder-step-by-st/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como agrupar formas no Word usando DocumentBuilder – guia passo a passo

Se você precisar **agrupar formas no Word** programaticamente, este tutorial mostra uma solução completa em C#. Você verá como **criar um documento Word em branco**, usar **DocumentBuilder** e **inserir uma forma retangular** antes de agrupá‑la com uma elipse. O resultado é um único `GroupShape` que você pode mover, redimensionar ou estilizar como um único objeto.

Este guia cobre tudo o que você precisa saber para gerar um documento Word com gráficos agrupados usando a biblioteca Aspose.Words for .NET. Ao final do artigo, você terá um projeto executável que produz `GroupedShapes.docx` contendo um retângulo e uma elipse combinados em uma única forma.

## Pré-requisitos

- .NET 6.0 ou posterior (o código também funciona com .NET Framework 4.7.2+)
- Pacote NuGet Aspose.Words for .NET (`Aspose.Words`) – versão 23.12 ou mais recente
- Uma IDE C# como Visual Studio 2022 ou Visual Studio Code
- Familiaridade básica com a sintaxe C# e programação orientada a objetos

> **Dica profissional:** Instale o pacote NuGet pela linha de comando para manter seu projeto organizado:  
> `dotnet add package Aspose.Words --version 23.12.0`

## Etapa 1: Criar um documento Word em branco

A primeira operação é instanciar um objeto `Document`, que representa um arquivo Word vazio, e um `DocumentBuilder` que permite adicionar conteúdo.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Step 1: Create a blank Word document and a DocumentBuilder
        Document document = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Por que isso importa:** `Document` fornece o contêiner do arquivo, enquanto `DocumentBuilder` oferece uma API fluente para inserir texto, imagens e formas. Sem um `DocumentBuilder` você teria que manipular a árvore de nós do documento manualmente, o que é propenso a erros.

## Etapa 2: Inserir uma forma retangular

Um retângulo é um bloco de construção comum para diagramas. Use `InsertShape` com `ShapeType.Rectangle` e especifique a largura e altura em pontos (1 pt ≈ 1/72 in).

```csharp
        // Step 2: Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;   // distance from the left margin (points)
        rectangleShape.Top = 50;    // distance from the top margin (points)
```

**Por que isso importa:** Definir `Left` e `Top` posiciona o retângulo precisamente na página, o que é essencial quando você posteriormente o agrupa com outras formas. O método `InsertShape` adiciona automaticamente a forma ao parágrafo atual.

## Etapa 3: Inserir uma forma elíptica

Em seguida, adicione uma elipse que ficará ao lado do retângulo.

```csharp
        // Step 3: Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;
```

**Por que isso importa:** Usar um `ShapeType` diferente demonstra como a mesma API `DocumentBuilder` pode criar gráficos variados. Posicionar a elipse de modo que ela se sobreponha ao retângulo torna o efeito de agrupamento evidente.

## Etapa 4: Agrupar as duas formas

Um `GroupShape` funciona como um contêiner. Ao anexar o retângulo e a elipse como filhos, eles se comportam como um único objeto.

```csharp
        // Step 4: Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        // Define the bounding rectangle that encloses all child shapes
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Insert the group into the document body
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);
```

**Por que isso importa:** A propriedade `Bounds` indica ao Word onde o grupo está localizado na página. Ao anexar as formas filhas, você preserva a formatação individual delas enquanto permite transformações coletivas (mover, girar, redimensionar).

## Etapa 5: Salvar o documento

Finalmente, grave o documento no disco. Você pode alterar o caminho para qualquer pasta que preferir.

```csharp
        // Step 5: Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Ao abrir `GroupedShapes.docx` no Microsoft Word, você verá um retângulo e uma elipse agrupados. Selecionar o grupo destacará ambas as formas, permitindo arrastá‑las ou redimensioná‑las como uma única unidade.

### Saída esperada

- Um arquivo Word chamado **GroupedShapes.docx**
- A primeira página contém um **retângulo** (100 pt × 50 pt) na posição (50, 50)
- Uma **elipse** (80 pt × 80 pt) na posição (200, 70)
- Ambas as formas fazem parte de um **GroupShape** com uma caixa delimitadora de 300 pt × 200 pt

## Variações comuns e casos de borda

| Cenário | Ajuste |
|----------|------------|
| **Different page size** | Set `document.Sections[0].PageSetup.PageWidth` and `PageHeight` before inserting shapes. |
| **More than two shapes** | Create additional `Shape` objects and call `groupShape.AppendChild(newShape)` for each. |
| **Apply fill color** | `rectangleShape.FillColor = System.Drawing.Color.LightBlue;` |
| **Rotate the group** | `groupShape.Rotation = 45;` (degrees) |
| **Export to PDF** | After saving the DOCX, call `document.Save("GroupedShapes.pdf");` |

## Código-fonte completo (pronto para executar)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Create a blank Word document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;
        rectangleShape.Top = 50;

        // Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;

        // Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);

        // Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Copie o código para um novo projeto de console, restaure o pacote NuGet Aspose.Words e execute. O console confirmará o local do arquivo, e ao abrir o arquivo você verá os gráficos agrupados.

## Conclusão

Agora você sabe **como agrupar formas no Word** com o `DocumentBuilder` da Aspose.Words. O tutorial percorreu a criação de um **documento Word em branco**, **inserção de uma forma retangular**, adição de uma elipse e a combinação delas em um `GroupShape`. Com essa base, você pode criar diagramas mais ricos, fluxogramas ou gráficos personalizados diretamente em C#.

### O que vem a seguir?

- Explore **como usar DocumentBuilder** para tabelas, cabeçalhos e rodapés.
- Combine técnicas de **inserir forma retangular Word** com caixas de texto para diagramas anotados.
- Use **criar documento word em branco** como modelo para geração automática de relatórios.

Sinta‑se à vontade para experimentar cores, gradientes e formas adicionais. Boa codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que expandem as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Criar Forma de Grupo em Documento Word Usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Inserir Formas em Documentos Word Usando Aspose.Words para .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Criar forma retangular no Word usando C# – Guia passo a passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}