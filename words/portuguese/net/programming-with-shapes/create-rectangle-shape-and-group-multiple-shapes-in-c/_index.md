---
category: general
date: 2026-09-18
description: Crie uma forma retangular em um documento Word usando C#. Aprenda como
  adicionar várias formas, adicionar formas a um grupo e inserir um grupo de formas
  com Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add multiple shapes
- add shapes to group
- insert group shape
language: pt
lastmod: 2026-09-18
og_description: Criar forma de retângulo em um arquivo Word com C#. Este guia mostra
  como adicionar várias formas, adicionar formas a um grupo e inserir forma de grupo
  usando Aspose.Words.
og_image_alt: Grouped rectangle and ellipse shapes displayed in a Word document
og_title: Criar forma de retângulo e agrupar formas em C#
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create rectangle shape in a Word document using C#. Learn how to add
    multiple shapes, add shapes to a group, and insert group shape with Aspose.Words.
  headline: Create rectangle shape and group multiple shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Shape
- GroupShape
title: Criar forma de retângulo e agrupar múltiplas formas em C#
url: /pt/net/programming-with-shapes/create-rectangle-shape-and-group-multiple-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar forma retangular e agrupar várias formas em C#

Se você precisa **criar forma retangular** em um documento Word, este tutorial mostra uma solução completa. Você verá como **adicionar várias formas**, **adicionar formas a um grupo** e **inserir forma de grupo** usando a API Aspose.Words para .NET.

Trabalhar com formas é uma necessidade comum ao gerar relatórios, contratos ou materiais de marketing programaticamente. Ao final deste guia você terá uma aplicação console C# executável que produz um arquivo `.docx` contendo um retângulo, uma elipse e um grupo que contém ambas as formas.

Os únicos pré-requisitos são um SDK .NET recente (6.0 ou superior) e uma cópia licenciada do Aspose.Words para .NET. Nenhuma ferramenta adicional é necessária.

## Pré-requisitos

- .NET 6.0 SDK ou mais recente  
- Aspose.Words para .NET (pacote NuGet `Aspose.Words`)  
- Familiaridade básica com a sintaxe C#  

Você pode instalar o pacote com o seguinte comando:

```bash
dotnet add package Aspose.Words
```

## Etapa 1: Criar forma retangular com Aspose.Words

O primeiro passo é criar um objeto `Shape` do tipo `Rectangle`. Esse objeto representa o retângulo visual que aparecerá no documento.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty document
Document doc = new Document();

// Initialize a DocumentBuilder for editing the document
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape: width = 100 points, height = 50 points
Shape rectangle = new Shape(doc, ShapeType.Rectangle);
rectangle.Width = 100;
rectangle.Height = 50;

// Optional: give the rectangle a fill color and a border
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.StrokeWeight = 1.0;

// Insert the rectangle at the current builder position
builder.InsertNode(rectangle);
```

**Por que isso importa:** `ShapeType.Rectangle` indica ao Aspose.Words que deve renderizar um retângulo geométrico. Definir `Width` e `Height` determina seu tamanho em pontos (1 ponto = 1/72 polegada). Adicionar cores de preenchimento e contorno torna a forma visível sem necessidade de estilos adicionais.

## Etapa 2: Adicionar várias formas ao documento

Depois do retângulo, você pode criar quantas formas adicionais quiser. Neste exemplo, adicionamos uma elipse para demonstrar como funciona **adicionar várias formas**.

```csharp
// Create an ellipse shape: width = 80 points, height = 80 points
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width = 80;
ellipse.Height = 80;

// Style the ellipse
ellipse.FillColor = System.Drawing.Color.LightCoral;
ellipse.StrokeColor = System.Drawing.Color.Maroon;
ellipse.StrokeWeight = 1.0;

// Insert the ellipse after the rectangle
builder.InsertNode(ellipse);
```

**Por que isso importa:** Cada chamada a `new Shape` cria um objeto de desenho independente. Ao inseri‑los sequencialmente, você constrói uma coleção de formas que podem ser agrupadas ou posicionadas individualmente mais tarde.

## Etapa 3: Adicionar formas ao grupo

Agrupar formas simplifica o gerenciamento de layout porque o grupo se comporta como um único nó. Esta etapa mostra como **adicionar formas ao grupo** usando `GroupShape`.

```csharp
// Create a GroupShape with a bounding box of 200x200 points
GroupShape group = new GroupShape(doc, 200, 200);

// Move the builder's cursor back to the start of the document
builder.MoveToDocumentStart();

// Insert the empty group into the document
builder.InsertNode(group);

// Append the previously created rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

**Por que isso importa:** `GroupShape` funciona como um contêiner. Quando você move, gira ou redimensiona o grupo, todas as formas filhas seguem automaticamente. A caixa delimitadora (200 × 200 pontos) define o espaço de coordenadas para as formas filhas.

## Etapa 4: Inserir forma de grupo no documento

Agora que o grupo contém o retângulo e a elipse, você precisa **inserir a forma de grupo** no local desejado. O builder já posicionou o grupo vazio, mas você também pode inseri‑lo em outro lugar, se necessário.

```csharp
// Position the group at a specific location (optional)
group.Left = 50;   // 50 points from the left margin
group.Top = 100;   // 100 points from the top margin

// Save the document with the grouped shapes
doc.Save("GroupShapeExample.docx");
```

**Por que isso importa:** Ajustar `Left` e `Top` move todo o grupo dentro da página. Salvar o documento grava a hierarquia de formas em um arquivo `.docx` que pode ser aberto no Microsoft Word, LibreOffice ou qualquer visualizador compatível.

## Exemplo completo executável

Abaixo está o programa completo que combina todas as etapas. Copie o código para um novo projeto console e execute‑lo para gerar `GroupShapeExample.docx`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document
            Document doc = new Document();

            // Step 2: Initialize a DocumentBuilder for editing the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle);
            rectangle.Width = 100;
            rectangle.Height = 50;
            rectangle.FillColor = Color.LightBlue;
            rectangle.StrokeColor = Color.DarkBlue;
            rectangle.StrokeWeight = 1.0;

            // Step 4: Create an ellipse shape
            Shape ellipse = new Shape(doc, ShapeType.Ellipse);
            ellipse.Width = 80;
            ellipse.Height = 80;
            ellipse.FillColor = Color.LightCoral;
            ellipse.StrokeColor = Color.Maroon;
            ellipse.StrokeWeight = 1.0;

            // Step 5: Create a GroupShape that will hold both shapes
            GroupShape group = new GroupShape(doc, 200, 200);
            group.Left = 50;   // optional positioning
            group.Top = 100;   // optional positioning

            // Add the rectangle and ellipse to the group
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Insert the group into the document at the current builder position
            builder.InsertNode(group);

            // Step 6: Save the document containing the grouped shapes
            doc.Save("GroupShapeExample.docx");

            Console.WriteLine("Document saved successfully.");
        }
    }
}
```

**Saída esperada:**  
Abrir `GroupShapeExample.docx` mostra um único grupo contendo um retângulo azul‑claro e uma elipse coral‑clara, ambos posicionados dentro de um contêiner de 200 × 200 pontos. O grupo pode ser selecionado como um único objeto no Word, confirmando que **adicionar formas ao grupo** foi bem‑sucedido.

## Variações comuns e casos de borda

| Situação | Ajuste recomendado |
|-----------|------------------------|
| Tipos diferentes de forma (por exemplo, `ShapeType.Line`) | Crie a forma com o `ShapeType` desejado e defina sua geometria de acordo. |
| Necessidade de girar uma forma | Use `shape.Rotation = 45;` (graus) antes de adicioná‑la ao grupo. |
| Documentos maiores com muitos grupos | Reutilize uma única instância de `DocumentBuilder`; evite criar um novo builder para cada grupo para reduzir o consumo de memória. |
| Salvar em PDF ao invés de DOCX | Chame `doc.Save("output.pdf", SaveFormat.Pdf);` após inserir o grupo. |

**Dica profissional:** Sempre defina valores explícitos de `Left` e `Top` para o grupo quando precisar de posicionamento preciso. Se você os omitir, o grupo herdará a posição atual do cursor do builder, o que pode gerar resultados de layout inesperados.

## Conclusão

Agora você sabe como **criar forma retangular**, **adicionar várias formas**, **adicionar formas ao grupo** e **inserir forma de grupo** em um documento Word usando C#. O exemplo completo demonstra todo o fluxo de trabalho, desde a criação do documento até a gravação do arquivo final.  

Em seguida, explore tópicos relacionados, como **posicionar formas em relação ao texto**, **aplicar quebra de texto** e **exportar formas agrupadas para PDF**. Essas extensões permitem criar layouts de documentos sofisticados e programáticos com Aspose.Words.

## O que Você Deve Aprender a Seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Criar forma retangular no Word usando C# – Guia passo a passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Criar Forma de Grupo em Documento Word Usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Criar Documento Word em Branco com Forma Retangular Sombreada – Guia passo a passo](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}