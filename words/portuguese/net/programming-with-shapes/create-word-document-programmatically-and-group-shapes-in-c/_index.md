---
category: general
date: 2026-08-10
description: Criar documento Word programaticamente usando Aspose.Words, aprender
  como agrupar múltiplas formas no Word, adicionar retângulo ao Word e criar um grupo
  de formas em C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- group multiple shapes word
- add rectangle to word
- how to create group shape
language: pt
lastmod: 2026-08-10
og_description: Crie documentos Word programaticamente com Aspose.Words. Este guia
  mostra como agrupar várias formas no Word, adicionar um retângulo ao Word e incorporar
  um controle de conteúdo de texto simples, tudo em C#.
og_image_alt: Screenshot of a Word file showing a grouped rectangle and ellipse with
  a plain‑text content control
og_title: Criar documento Word programaticamente – agrupar formas em C#
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  headline: Create word document programmatically and group shapes in C#
  type: TechArticle
- description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  name: Create word document programmatically and group shapes in C#
  steps:
  - name: – Initialize the document and builder
    text: The `Document` object represents the entire DOCX file, while `DocumentBuilder`
      provides a convenient API to add content. Initializing them is the first requirement
      whenever you **create word document programmatically**.
  - name: – Create a group shape container
    text: A `Shape` with `ShapeType.Group` acts as a canvas that can hold other shapes.
      Setting `Width` and `Height` defines the bounding box for the group. This is
      the core of **how to create group shape** in Aspose.Words.
  - name: – Add a rectangle to word
    text: A rectangle is created with `ShapeType.Rectangle`. Its `Left` and `Top`
      properties position it relative to the group’s origin. This step demonstrates
      **add rectangle to word** and shows how you can control exact placement.
  - name: – Add an ellipse (circle) to the group
    text: An ellipse is added the same way as the rectangle, but with `ShapeType.Ellipse`.
      The `Left = 210` moves it to the right of the rectangle, creating a visually
      distinct pair of shapes inside the same group.
  - name: – Insert the completed group shape into the document
    text: '`builder.InsertNode(groupShape)` places the whole group at the current
      cursor location. Because the group already contains its children, you do not
      need additional insert calls for the rectangle or ellipse.'
  - name: – Create a plain‑text StructuredDocumentTag (SDT)
    text: A StructuredDocumentTag is a content control that end users can fill in
      when the document is opened in Word. Setting `Title = "CustomerName"` gives
      the control a meaningful identifier, which is useful for later data extraction.
  - name: – Save the document
    text: '`doc.Save("GroupAndSDT.docx")` writes the file to disk. The resulting DOCX
      contains the grouped shapes and the SDT. Opening the file in Microsoft Word
      will show a rectangle next to a circle, both selectable as a single object,
      followed by a placeholder “Enter name here …”.'
  - name: Using different shape types
    text: You can replace `ShapeType.Rectangle` or `ShapeType.Ellipse` with any other
      `ShapeType` (e.g., `ShapeType.Polygon`, `ShapeType.Line`). The grouping logic
      remains identical.
  - name: Setting fill color and borders
    text: '```csharp rectangleShape.FillColor = System.Drawing.Color.LightBlue; rectangleShape.StrokeColor
      = System.Drawing.Color.DarkBlue; ellipseShape.FillColor = System.Drawing.Color.LightCoral;
      ``` Adding fill and stroke improves visual distinction, especially when the
      document is shared with non‑technical'
  - name: Rotating the entire group
    text: '```csharp groupShape.Rotation = 45; // rotates both shapes together ```
      Rotating the group is more efficient than rotating each child individually.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Criar documento Word programaticamente e agrupar formas em C#
url: /pt/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar documento Word programaticamente e agrupar formas em C#

Se você precisar **create word document programmatically**, este tutorial mostra como criar um arquivo DOCX com Aspose.Words e **group multiple shapes word** juntos. Também abordaremos **add rectangle to word** e **how to create group shape** que contém tanto um retângulo quanto uma elipse, além de um StructuredDocumentTag de texto simples para entrada do usuário.

Você terminará com um arquivo Word pronto‑para‑uso que contém uma forma agrupada de retângulo‑elipse e um controle de conteúdo onde o usuário pode digitar um nome. Nenhuma edição manual no Word é necessária após a execução do código.

## O que você precisará

- .NET 6.0 ou posterior (o exemplo tem como alvo .NET 6, mas qualquer versão recente do .NET funciona)
- Uma licença do Aspose.Words for .NET (o teste gratuito funciona para testes)
- Visual Studio 2022 ou qualquer IDE C# que você prefira
- Familiaridade básica com a sintaxe C#

## Criar documento Word programaticamente – fluxo de trabalho geral

O processo consiste em três fases lógicas:

1. **Initialize** um `Document` e um `DocumentBuilder` – a base para qualquer arquivo Word que você gerar.
2. **Build a group shape** que contém um retângulo e uma elipse – demonstra **group multiple shapes word** e **how to create group shape**.
3. **Insert a StructuredDocumentTag (SDT)** – um controle de conteúdo de texto simples que permite que os usuários finais preencham dados, ilustrando **add rectangle to word** como parte do layout geral do documento.

Abaixo está o código completo e executável seguido de uma explicação passo a passo.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1 – Initialize the document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2 – Create a group shape container
            Shape groupShape = new Shape(doc, ShapeType.Group)
            {
                Width = 400,
                Height = 200
            };

            // Step 3 – Add a rectangle to the group
            Shape rectangleShape = new Shape(doc, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100,
                Left = 0,
                Top = 0
            };
            groupShape.GroupShape.AddChild(rectangleShape);

            // Step 4 – Add an ellipse (circle) to the group
            Shape ellipseShape = new Shape(doc, ShapeType.Ellipse)
            {
                Width = 100,
                Height = 100,
                Left = 210, // Position next to the rectangle
                Top = 0
            };
            groupShape.GroupShape.AddChild(ellipseShape);

            // Step 5 – Insert the completed group shape into the document
            builder.InsertNode(groupShape);

            // Step 6 – Create a plain‑text StructuredDocumentTag for user input
            StructuredDocumentTag sdtTag = new StructuredDocumentTag(
                doc,
                SdtType.PlainText,
                MarkupLevel.Block)
            {
                Title = "CustomerName"
            };
            builder.InsertNode(sdtTag);
            builder.Writeln("Enter name here …");

            // Step 7 – Save the document
            doc.Save("GroupAndSDT.docx");
            Console.WriteLine("Document created successfully.");
        }
    }
}
```

### Etapa 1 – Inicializar o documento e o builder
O objeto `Document` representa o arquivo DOCX inteiro, enquanto `DocumentBuilder` fornece uma API conveniente para adicionar conteúdo. Inicializá‑los é o primeiro requisito sempre que você **create word document programmatically**.

> **Dica profissional:** Se você planeja reutilizar o mesmo documento em várias operações, mantenha uma única instância de `DocumentBuilder` para evitar a criação desnecessária de objetos.

### Etapa 2 – Criar um contêiner de forma agrupada
Um `Shape` com `ShapeType.Group` funciona como uma tela que pode conter outras formas. Definir `Width` e `Height` estabelece a caixa delimitadora para o grupo. Isso é o núcleo de **how to create group shape** no Aspose.Words.

> **Caso limite:** Se a largura do grupo for menor que a largura combinada de seus filhos, os filhos serão recortados. Sempre faça o grupo grande o suficiente para conter todas as formas filhas.

### Etapa 3 – Adicionar um retângulo ao Word
Um retângulo é criado com `ShapeType.Rectangle`. Suas propriedades `Left` e `Top` posicionam‑no em relação à origem do grupo. Esta etapa demonstra **add rectangle to word** e mostra como você pode controlar a posição exata.

> **Erro comum:** Esquecer de definir `Left`/`Top` faz com que o retângulo apareça na origem padrão do grupo (0,0), o que pode sobrepor outros filhos.

### Etapa 4 – Adicionar uma elipse (círculo) ao grupo
Uma elipse é adicionada da mesma forma que o retângulo, mas com `ShapeType.Ellipse`. O `Left = 210` move‑a para a direita do retângulo, criando um par de formas visualmente distinto dentro do mesmo grupo.

> **Por que usar um grupo?** Agrupar permite mover, girar ou redimensionar ambas as formas juntas com uma única operação posteriormente, preservando seu layout relativo.

### Etapa 5 – Inserir a forma agrupada concluída no documento
`builder.InsertNode(groupShape)` coloca todo o grupo na posição atual do cursor. Como o grupo já contém seus filhos, você não precisa de chamadas de inserção adicionais para o retângulo ou a elipse.

### Etapa 6 – Criar um StructuredDocumentTag (SDT) de texto simples
Um StructuredDocumentTag é um controle de conteúdo que os usuários finais podem preencher quando o documento é aberto no Word. Definir `Title = "CustomerName"` fornece ao controle um identificador significativo, útil para extração de dados posterior.

> **Por que um SDT de texto simples?** Ele restringe a entrada a texto simples, evitando formatação acidental que poderia quebrar o processamento subsequente.

### Etapa 7 – Salvar o documento
`doc.Save("GroupAndSDT.docx")` grava o arquivo no disco. O DOCX resultante contém as formas agrupadas e o SDT. Ao abrir o arquivo no Microsoft Word, será exibido um retângulo ao lado de um círculo, ambos selecionáveis como um único objeto, seguido de um placeholder “Enter name here …”.

#### Saída esperada
- Um arquivo chamado **GroupAndSDT.docx** na pasta de execução.
- No Word: uma forma agrupada (retângulo + elipse) que você pode mover como uma única unidade.
- Diretamente abaixo do grupo, um controle de conteúdo sombreado em cinza solicitando que o usuário digite um nome.

## Variações adicionais e boas práticas

### Usando diferentes tipos de forma
Você pode substituir `ShapeType.Rectangle` ou `ShapeType.Ellipse` por qualquer outro `ShapeType` (por exemplo, `ShapeType.Polygon`, `ShapeType.Line`). A lógica de agrupamento permanece idêntica.

### Definindo cor de preenchimento e bordas
```csharp
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```
Adicionar preenchimento e contorno melhora a distinção visual, especialmente quando o documento é compartilhado com partes interessadas não técnicas.

### Rotacionando todo o grupo
```csharp
groupShape.Rotation = 45; // rotates both shapes together
```
Rotacionar o grupo é mais eficiente do que rotacionar cada filho individualmente.

### Exportando para PDF
Se você precisar de uma versão PDF, basta chamar:
```csharp
doc.Save("GroupAndSDT.pdf", SaveFormat.Pdf);
```
Todas as formas agrupadas e o SDT (renderizado como um campo de texto) aparecerão no PDF.

## Armadilhas comuns e como evitá‑las

| Symptom | Cause | Fix |
|---------|-------|


## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}