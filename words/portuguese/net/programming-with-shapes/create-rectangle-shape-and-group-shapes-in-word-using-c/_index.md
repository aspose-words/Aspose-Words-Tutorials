---
category: general
date: 2026-09-08
description: Crie uma forma retangular em um documento Word com C#. Aprenda a definir
  o tamanho da forma, agrupar várias formas e criar um documento Word em branco programaticamente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- set shape size
- group multiple shapes
- create blank word document
language: pt
lastmod: 2026-09-08
og_description: Crie uma forma retangular em um documento Word com C#. Este guia mostra
  como definir o tamanho da forma, agrupar várias formas e criar um documento Word
  em branco programaticamente.
og_image_alt: Screenshot showing how to create rectangle shape in a Word document
  using C#
og_title: Criar forma de retângulo e agrupar formas no Word usando C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Create rectangle shape in a Word document with C#. Learn to set shape
    size, group multiple shapes, and create blank Word document programmatically.
  headline: Create rectangle shape and group shapes in Word using C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Criar forma retangular e agrupar formas no Word usando C#
url: /pt/net/programming-with-shapes/create-rectangle-shape-and-group-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar forma de retângulo e agrupar formas no Word usando C#

Se você precisa **criar forma de retângulo** dentro de um arquivo Word, este tutorial oferece uma solução completa e pronta‑para‑executar. Você verá como definir o tamanho da forma, agrupar várias formas e criar um documento Word em branco do zero — tudo com a biblioteca Aspose.Words for .NET.

Trabalhar programaticamente com documentos Word costuma ser como equilibrar muitos detalhes pequenos. Ao final deste guia, você terá um único método que produz um arquivo `.docx` contendo um retângulo e uma elipse agrupados, prontos para edição ou impressão adicionais.

## Pré‑requisitos

Antes de começar, certifique‑se de que você tem:

* .NET 6.0 ou superior (o código também funciona com .NET Framework 4.6+)
* Uma cópia licenciada do **Aspose.Words for .NET** (você pode usar uma chave de avaliação gratuita)
* Uma IDE como Visual Studio 2022 ou Visual Studio Code
* Familiaridade básica com a sintaxe C#

Nenhum pacote NuGet adicional é necessário além de `Aspose.Words`.

## Etapa 1: Criar um documento Word em branco

A primeira etapa é criar um documento vazio que hospedará as formas. Isso atende ao requisito de *criar documento Word em branco*.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty Word document
Document doc = new Document();

// The document already contains one section and one empty paragraph
// You can add additional sections later if needed
```

Criar um documento em branco fornece uma tela limpa. O objeto `Document` representa todo o arquivo `.docx`, e seu `FirstSection.Body.FirstParagraph` é o ponto de inserção padrão para novos nós.

## Etapa 2: Criar forma de retângulo

Agora você pode adicionar o retângulo. É aqui que a operação **criar forma de retângulo** ocorre.

```csharp
// Initialize a DocumentBuilder to simplify node insertion
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape instance
Shape rectangle = new Shape(doc, ShapeType.Rectangle);

// Set the rectangle's size (width and height) and position
rectangle.Width  = 100;   // points; 1 point = 1/72 inch
rectangle.Height = 50;
rectangle.Left   = 10;    // distance from the left edge of the container
rectangle.Top    = 20;    // distance from the top edge of the container

// Optional: give the rectangle a visible border
rectangle.StrokeColor = Color.Blue;
rectangle.FillColor   = Color.LightGray;
```

Definir as dimensões diretamente responde à palavra‑chave **set shape size**. Todos os valores de tamanho são expressos em pontos, o que oferece controle preciso sobre como a forma aparece no documento final.

## Etapa 3: Criar uma forma adicional (elipse)

Um caso de uso típico é combinar várias formas. Aqui adicionamos uma elipse que mais tarde compartilhará o mesmo contêiner.

```csharp
// Create an ellipse shape instance
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width  = 80;
ellipse.Height = 80;
ellipse.Left   = 120;   // Position it to the right of the rectangle
ellipse.Top    = 30;

// Give the ellipse a distinct border and fill
ellipse.StrokeColor = Color.DarkGreen;
ellipse.FillColor   = Color.LightYellow;
```

Ambas as formas ainda são independentes neste ponto. A próxima etapa mostra como **group multiple shapes** juntas.

## Etapa 4: Agrupar formas no Word

Agrupar formas permite mover, redimensionar ou formatar todas como uma única unidade. Isso satisfaz os requisitos **group shapes in word** e **group multiple shapes**.

```csharp
// Create a GroupShape container that will hold the rectangle and ellipse
GroupShape group = new GroupShape(doc);

// Define the container's bounding box – it must be large enough for all children
group.Bounds = new RectangleF(0, 0, 300, 200);

// Append the group to the document's first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(group);

// Add the rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

A propriedade `GroupShape.Bounds` determina o sistema de coordenadas para as formas filhas. Ao colocar o retângulo e a elipse dentro do mesmo `GroupShape`, você pode mover ou girá‑los juntos com uma única chamada.

## Etapa 5: Salvar o documento

Por fim, grave o documento no disco. O arquivo conterá as formas agrupadas que você acabou de criar.

```csharp
// Choose an output path – ensure the directory exists and you have write permission
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");

// Save the document in DOCX format
doc.Save(outputPath);
```

Depois de executar o programa, abra `GroupedShapes.docx` no Microsoft Word. Você deverá ver um retângulo e uma elipse agrupados; selecionar uma forma também seleciona a outra, confirmando que o agrupamento foi bem‑sucedido.

## Código‑fonte completo

Copie o programa completo abaixo para um novo projeto console‑app e execute‑o. Nenhum código adicional é necessário.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System;
using System.Drawing;
using System.IO;

class Program
{
    static void Main()
    {
        // Step 1: create a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: create rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width  = 100,
            Height = 50,
            Left   = 10,
            Top    = 20,
            StrokeColor = Color.Blue,
            FillColor   = Color.LightGray
        };

        // Step 3: create ellipse shape
        Shape ellipse = new Shape(doc, ShapeType.Ellipse)
        {
            Width  = 80,
            Height = 80,
            Left   = 120,
            Top    = 30,
            StrokeColor = Color.DarkGreen,
            FillColor   = Color.LightYellow
        };

        // Step 4: group the shapes
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new RectangleF(0, 0, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);
        group.AppendChild(rectangle);
        group.AppendChild(ellipse);

        // Step 5: save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### Saída esperada

A execução do programa produz `GroupedShapes.docx`. Ao abrir o arquivo no Word, você verá:

* Um **retângulo** (100 pt × 50 pt) com borda azul e preenchimento cinza‑claro.
* Uma **elipse** (80 pt × 80 pt) com borda verde‑escura e preenchimento amarelo‑claro.
* Ambas as formas estão dentro de um único grupo, de modo que mover uma move a outra.

## Perguntas comuns e casos de borda

| Pergunta | Resposta |
|----------|----------|
| **Posso adicionar mais de duas formas ao grupo?** | Sim. Crie objetos `Shape` adicionais e chame `group.AppendChild(suaForma)` para cada um. |
| **E se eu precisar girar o grupo?** | Defina `group.RotationAngle = 45;` (graus). Todas as formas filhas giram juntas. |
| **É possível agrupar formas depois que o documento foi salvo?** | Você deve modificar a estrutura do documento antes de salvar; caso contrário, seria necessário carregar o arquivo, localizar as formas e recriar o grupo. |
| **Preciso liberar algum objeto?** | Aspose.Words gerencia seus próprios recursos, mas você deve liberar objetos `FileStream` se abrir fluxos manualmente. |
| **O código funciona com o formato .doc (binário)?** | Sim, altere `doc.Save("output.doc")`. O comportamento de agrupamento é idêntico. |

## Conclusão

Agora você sabe como **criar forma de retângulo**, **set shape size** e **group multiple shapes** dentro de um arquivo Word usando C#. Essa abordagem permite construir programaticamente diagramas complexos, marcas d’água ou relatórios baseados em modelos sem edição manual.

### Próximos passos

* Explore **group shapes in word** adicionando caixas de texto ou imagens ao mesmo grupo.
* Use o padrão `SetShapeSize` para calcular dinamicamente as dimensões com base no layout da página.
* Combine esta técnica com campos de mala‑direta para gerar documentos personalizados em escala.

Sinta‑se à vontade para experimentar diferentes tipos de forma, cores e transformações de grupo. Boa codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas em seus próprios projetos.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create Word Document with a Shadowed Rectangle – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}