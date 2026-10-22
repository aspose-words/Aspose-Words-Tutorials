---
category: general
date: 2026-08-04
description: Salvar arquivo docx programaticamente enquanto adiciona forma retangular
  e agrupa formas no Word. Aprenda a definir dimensões da forma e criar caixa de texto
  programaticamente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save docx file
- add rectangle shape
- group shapes word
- set shape dimensions
- create textbox programmatically
language: pt
lastmod: 2026-08-04
og_description: Salvar arquivo docx usando C# adicionando forma retangular, agrupando
  formas no Word, definindo dimensões da forma e criando caixa de texto programaticamente.
og_image_alt: Screenshot of a saved docx file that contains a grouped rectangle and
  textbox
og_title: Salvar arquivo docx com formas agrupadas no Word – Guia passo a passo em
  C#
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  headline: Save docx file with grouped shapes in Word using C#
  type: TechArticle
- description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  name: Save docx file with grouped shapes in Word using C#
  steps:
  - name: 1. Create a new document and a builder
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing; using Aspose.Words.Drawing.Shapes;'
  - name: 2. Add rectangle shape to a group
    text: '```csharp // Create a group container that will hold all shapes. GroupShape
      group = new GroupShape(doc) { Width = 400, // Set shape dimensions for the group.
      Height = 200 };'
  - name: 3. Group shapes in Word document
    text: The `GroupShape` class aggregates multiple drawing objects. Grouping is
      useful when you want to treat several objects as a single unit (e.g., moving,
      rotating, or copying them together).
  - name: 4. Set shape dimensions for precise layout
    text: Both the group and its child shapes need explicit dimensions; otherwise
      Word applies default sizes that may not match your design.
  - name: 5. Create textbox programmatically inside the group
    text: '```csharp // Add a textbox shape with custom text. Shape textBox = new
      Shape(doc, ShapeType.TextBox) { Width = 180, Height = 100, Left = 210, // Position
      relative to the group’s coordinate system. Top = 10 };'
  - name: 6. Insert group shape and **save docx file**
    text: '```csharp // Insert the completed group into the document at the current
      cursor position. builder.InsertNode(group);'
  - name: Expected output
    text: '* A file named **GroupShape.docx** appears in the output directory. * Opening
      the file shows a rectangular shape on the left and a textbox containing “Grouped
      text” on the right, both locked together. * Selecting either shape moves the
      entire group, confirming that **group shapes word** functionalit'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Salvar arquivo docx com formas agrupadas no Word usando C#
url: /pt/net/programming-with-shapes/save-docx-file-with-grouped-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Salvar arquivo docx com formas agrupadas no Word usando C#

Se você precisa **save docx file** que contém várias formas organizadas juntas, este guia mostra como fazer isso com C#. Você aprenderá como **add rectangle shape**, agrupar várias formas em um documento Word, **set shape dimensions**, e **create textbox programmatically**. A solução funciona com a versão mais recente do Aspose.Words para .NET e roda em .NET 6 ou superior.

O tutorial percorre cada passo, desde a configuração do projeto até a chamada final `doc.Save`. Ao final, você terá um trecho de código reutilizável que pode colar em qualquer projeto console ou ASP.NET. Nenhum script externo ou edição manual do arquivo DOCX é necessário.

## Pré-requisitos

* .NET 6 SDK (ou mais recente) instalado.
* Uma licença válida para **Aspose.Words for .NET** (a versão de avaliação gratuita funciona para testes).
* Visual Studio 2022, VS Code, ou qualquer IDE que possa compilar projetos .NET.

O código usa apenas o namespace Aspose.Words, portanto nenhum pacote NuGet adicional é necessário.

## Salvar arquivo docx com formas agrupadas no Word

O núcleo da solução consiste em criar um `GroupShape` que contém um retângulo e uma caixa de texto, inserir o grupo no documento e chamar `doc.Save`. As seções a seguir dividem o processo em partes manejáveis.

### 1. Criar um novo documento e um builder

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // Initialize a blank document.
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for editing the document.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Por que este passo importa* – Um novo objeto `Document` representa um arquivo *.docx* vazio. `DocumentBuilder` fornece métodos de alto nível como `InsertNode`, que usaremos para posicionar a forma de grupo.

### 2. Adicionar forma retangular a um grupo

```csharp
        // Create a group container that will hold all shapes.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,   // Set shape dimensions for the group.
            Height = 200
        };

        // Add a rectangle shape that will be part of the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,   // Set shape dimensions for the rectangle.
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);
```

*Por que este passo importa* – A operação **add rectangle shape** demonstra como definir um elemento visual com tamanho e posição exatos. O retângulo está dentro de `group`, então mover o grupo posteriormente move o retângulo automaticamente.

### 3. Agrupar formas no documento Word

A classe `GroupShape` agrega múltiplos objetos de desenho. Agrupar é útil quando você deseja tratar vários objetos como uma única unidade (por exemplo, mover, girar ou copiar todos juntos).

```csharp
        // The group now contains the rectangle; we will add more shapes next.
```

*Por que agrupamos* – Agrupar reduz a complexidade do layout. Em vez de posicionar cada forma individualmente na página, você ajusta `Left`, `Top`, `Width` e `Height` do grupo uma única vez.

### 4. Definir dimensões da forma para layout preciso

Tanto o grupo quanto suas formas filhas precisam de dimensões explícitas; caso contrário, o Word aplica tamanhos padrão que podem não corresponder ao seu design.

```csharp
        // Example of adjusting the group’s overall size.
        group.Width = 400;   // Overall width of the grouped area.
        group.Height = 200;  // Overall height of the grouped area.
```

*Por que definimos dimensões* – Medidas precisas garantem que o retângulo e a caixa de texto não se sobreponham inadvertidamente e que o **save docx file** final corresponda ao layout pretendido.

### 5. Criar caixa de texto programaticamente dentro do grupo

```csharp
        // Add a textbox shape with custom text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,   // Position relative to the group’s coordinate system.
            Top = 10
        };

        // Populate the textbox with a paragraph containing a run.
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);

        // Append the textbox to the same group.
        group.AppendChild(textBox);
```

*Por que este passo importa* – O segmento **create textbox programmatically** mostra como incorporar texto rico dentro de uma forma. Usar um `Paragraph` e `Run` lhe dá controle total sobre a formatação posteriormente.

### 6. Inserir forma de grupo e **save docx file**

```csharp
        // Insert the completed group into the document at the current cursor position.
        builder.InsertNode(group);

        // Save the document to the file system.
        doc.Save("GroupShape.docx");   // The file now contains a rectangle and a textbox grouped together.
    }
}
```

*Por que este passo final importa* – A chamada `InsertNode` coloca as formas agrupadas exatamente onde o cursor do builder está. O método `doc.Save` realiza a operação **save docx file**, gravando um documento Word totalmente funcional no disco.

> **Resultado:** Abrir *GroupShape.docx* no Microsoft Word exibe um retângulo à esquerda e uma caixa de texto à direita, ambos travados juntos dentro de um único grupo. Você pode mover o grupo como uma unidade, redimensioná‑lo ou aplicar formatação adicional.

## Exemplo completo e executável

Copie o código abaixo para um novo projeto console (`dotnet new console`) e execute `dotnet run`. O programa cria `GroupShape.docx` na pasta de saída do projeto.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // 1. Initialize document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Create a group shape container.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,
            Height = 200
        };

        // 3. Add rectangle shape.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);

        // 4. Add textbox shape with text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,
            Top = 10
        };
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);
        group.AppendChild(textBox);

        // 5. Insert the group into the document.
        builder.InsertNode(group);

        // 6. Save the document.
        doc.Save("GroupShape.docx");
    }
}
```

### Saída esperada

* Um arquivo chamado **GroupShape.docx** aparece no diretório de saída.
* Abrir o arquivo mostra uma forma retangular à esquerda e uma caixa de texto contendo “Grouped text” à direita, ambos travados juntos.
* Selecionar qualquer forma move todo o grupo, confirmando que a funcionalidade **group shapes word** funciona como esperado.

## Variações comuns e casos de borda

| Situação | Recomendação |
|-----------|----------------|
| Precisa de mais de duas formas | Anexe objetos `Shape` adicionais ao `group` antes de chamar `builder.InsertNode`. |
| Deseja que o grupo apareça em uma página específica | Mova o cursor do builder com `builder.MoveToDocumentEnd()` ou `builder.MoveToPage(pageNumber)`. |
| Requer unidades diferentes (por exemplo, centímetros) | Use `ConvertUtil.InchToPoint(1.0)` para converter polegadas em pontos, a unidade que o Word espera. |
| Deseja que a caixa de texto ajuste o texto | Defina `textBox.TextBoxWrap = TextBoxWrapType.Square` após criar a caixa de texto. |
| Trabalhando com versões mais antigas do .NET Framework | A mesma API funciona com .NET Framework 4.7+, mas certifique‑se de referenciar a versão correta do Aspose.Words. |

**Dica profissional:** Sempre defina `Width` e `Height` do grupo *depois* de adicionar todas as formas filhas. Isso garante que o grupo envolva totalmente seu conteúdo, evitando cortes quando o documento for aberto no Word.

## Conclusão

Agora você sabe como **save docx file** enquanto **add rectangle shape**, **group shapes word**, **set shape dimensions**, e **create textbox programmatically** usando Aspose.Words para .NET. O exemplo completo demonstra um padrão limpo e repetível que você pode adaptar a layouts mais complexos, como gráficos, imagens,

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}