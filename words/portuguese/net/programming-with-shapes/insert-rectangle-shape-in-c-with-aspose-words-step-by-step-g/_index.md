---
category: general
date: 2026-08-07
description: Inserir forma retangular em C# usando Aspose.Words e aprender como ocultar
  a forma, definir a cor de preenchimento e adicionar a forma retangular a um documento
  Word de forma eficiente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- how to insert shape
- how to set fill color
- add rectangle shape
language: pt
lastmod: 2026-08-07
og_description: Inserir forma retangular em um documento Word com C#. Aprenda a ocultar
  a forma, definir a cor de preenchimento e adicionar forma retangular usando Aspose.Words.
og_image_alt: Screenshot showing a hidden yellow rectangle shape inserted into a Word
  document
og_title: Inserir forma retangular em C# – tutorial completo do Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  headline: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  name: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  steps:
  - name: What each step does
    text: '| Step | Reason | |------|--------| | **Create a new document** | Provides
      a clean canvas; you can also load an existing .docx by passing a file path to
      `new Document(path)`. | | **Initialize DocumentBuilder** | `DocumentBuilder`
      is the high‑level helper that lets you insert text, tables, and shapes'
  - name: 1. Making the shape visible again
    text: 'If a later part of your workflow needs to reveal the hidden rectangle,
      you can toggle the flag:'
  - name: 2. Adding a border (stroke)
    text: 'A hidden shape can still have a visible border when you decide to show
      it. Set the `LineColor` and `LineWidth` properties:'
  - name: 3. Positioning the rectangle absolutely
    text: 'For precise layout control, switch the shape’s `WrapType` to `WrapType.Inline`
      (default) or `WrapType.TopBottom` and adjust `Left`/`Top` properties:'
  - name: 4. Using a different measurement unit
    text: 'Aspose.Words works in points (1 pt = 1/72 inch). If you prefer centimeters,
      convert first:'
  - name: Next steps
    text: '* Explore **how to insert shape** inside tables or headers/footers for
      watermarks. * Combine **add rectangle shape** with content controls to create
      dynamic placeholders. * Review Aspose.Words’ **shape manipulation** API for
      advanced features like rotation, gradient fills, and SVG import.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
- document generation
title: Inserir forma retangular em C# com Aspose.Words – guia passo a passo
url: /pt/net/programming-with-shapes/insert-rectangle-shape-in-c-with-aspose-words-step-by-step-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Inserir forma retangular em C# com Aspose.Words – guia passo a passo

Se você precisar **inserir forma retangular** em um documento Word a partir de C#, este guia mostra exatamente como fazer isso. Você verá como definir a cor de preenchimento, ocultar a forma para que ela não apareça no layout final e salvar o arquivo — tudo com apenas algumas linhas de código.

Nas seções a seguir, cobrimos tudo o que você precisa saber: pré‑requisitos, o código completo, explicações para cada passo e dicas para variações comuns, como tornar a forma visível novamente ou usar uma cor diferente. Ao final, você será capaz de **adicionar forma retangular** a qualquer arquivo .docx programaticamente.

## Pré-requisitos

Antes de começar, certifique‑se de que você tem:

* **Aspose.Words for .NET** (versão 23.10 ou posterior). Você pode instalá‑lo via NuGet:

  ```bash
  dotnet add package Aspose.Words
  ```

* .NET 6.0 SDK ou posterior instalado na sua máquina.
* Um entendimento básico de C# e Visual Studio (ou qualquer IDE de sua preferência).

Nenhuma biblioteca adicional é necessária — as APIs relacionadas a formas fazem parte do pacote central do Aspose.Words.

## Inserir forma retangular com Aspose.Words

O núcleo da solução é um programa curto e autocontido que cria um documento em branco, insere um retângulo, colore‑o, oculta‑o e, em seguida, salva o arquivo. Abaixo está o código‑fonte completo com comentários inline que explicam o *porquê* de cada linha.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Required for Color struct

// 1️⃣ Create a new, empty Word document.
Document document = new Document();

// 2️⃣ Obtain a DocumentBuilder – the primary API for editing the document.
DocumentBuilder builder = new DocumentBuilder(document);

// 3️⃣ Insert a rectangle shape of 100 × 50 points.
//    ShapeType.Rectangle tells Aspose.Words to create a simple rectangular drawing object.
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Set the shape's fill color to yellow.
//    The FillColor property accepts a System.Drawing.Color value.
rectangleShape.FillColor = Color.Yellow;

// 5️⃣ Hide the shape so it does not appear in the rendered document.
//    When Hidden = true, the shape is stored in the file but omitted from layout.
//    This is useful for placeholders, bookmarks, or metadata.
rectangleShape.Hidden = true;

// 6️⃣ Save the document to disk.
//    Change the path to a folder you have write access to.
document.Save(@"C:\Temp\HiddenRectangleShape.docx");
```

### O que cada passo faz

| Etapa | Motivo |
|------|--------|
| **Create a new document** | Fornece uma tela limpa; você também pode carregar um .docx existente passando um caminho de arquivo para `new Document(path)`. |
| **Initialize DocumentBuilder** | `DocumentBuilder` é o auxiliar de alto nível que permite inserir texto, tabelas e formas sem lidar com árvores de nós de baixo nível. |
| **Insert rectangle shape** | O método `InsertShape` retorna um objeto `Shape` que pode ser personalizado ainda mais (tamanho, posição, bordas, etc.). |
| **Set fill color** | A propriedade `FillColor` controla a cor interna; você pode usar qualquer valor `Color` (`Color.Red`, `Color.FromArgb(255, 0, 255, 0)`, etc.). |
| **Hide the shape** | `Hidden = true` indica ao Word que ignore a forma durante o layout, mantendo‑a ainda no XML do documento. Esta é a forma padrão de armazenar objetos invisíveis. |
| **Save the document** | Persiste as alterações em um arquivo .docx. O arquivo salvo conterá a forma retangular oculta. |

## Como definir a cor de preenchimento de uma forma

Alterar a cor de preenchimento é tão simples quanto atribuir um `System.Drawing.Color` à propriedade `FillColor`. Se precisar de um tom personalizado, use `Color.FromArgb`:

```csharp
// Example: set a semi‑transparent teal fill
rectangleShape.FillColor = Color.FromArgb(128, 0, 128, 128);
```

*Por que isso importa*: A cor de preenchimento é armazenada no XML da forma (`<w:fill>`). Quando a forma está oculta, a cor ainda existe, o que pode ser útil para processamento posterior (por exemplo, extração de metadados com base em códigos de cor).

## Como ocultar a forma no documento final

A bandeira `Hidden` é uma propriedade booleana da classe `Shape`. Defini‑la como `true` garante que a forma seja ignorada pelo mecanismo de layout do Word.

```csharp
rectangleShape.Hidden = true;
```

**Problemas comuns**

* **Hidden vs. Visible** – Se mais tarde precisar que a forma apareça, basta definir `Hidden = false`.
* **Compatibility** – Versões mais antigas do Word (pré‑2007) podem tratar objetos de desenho ocultos de forma diferente. O Aspose.Words mantém a compatibilidade armazenando a bandeira no elemento OOXML apropriado.

## Como inserir forma programaticamente

Embora o exemplo use um retângulo, o mesmo método `InsertShape` funciona para muitas outras formas (elipse, triângulo, linha, etc.). O primeiro argumento é um valor do enum `ShapeType`:

```csharp
// Insert an ellipse with the same dimensions
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
ellipse.FillColor = Color.LightBlue;
```

**Dica**: Se precisar posicionar a forma em um local específico da página, use `builder.MoveTo` para definir o ponto de inserção antes de chamar `InsertShape`.

## Adicionar forma retangular a um documento existente

Frequentemente você estará aprimorando um modelo em vez de começar do zero. Substitua o passo 1 por:

```csharp
// Load an existing .docx file
Document document = new Document(@"C:\Templates\ReportTemplate.docx");
```

Todas as etapas subsequentes permanecem idênticas, e o retângulo será adicionado onde o cursor do builder estiver posicionado (geralmente no final do documento por padrão).

## Tratando casos de borda e variações

### 1. Tornar a forma visível novamente

Se uma parte posterior do seu fluxo de trabalho precisar revelar o retângulo oculto, você pode alternar a bandeira:

```csharp
rectangleShape.Hidden = false;   // Shape will now be rendered
```

### 2. Adicionar uma borda (traço)

Uma forma oculta ainda pode ter uma borda visível quando você decidir mostrá‑la. Defina as propriedades `LineColor` e `LineWidth`:

```csharp
rectangleShape.LineColor = Color.Black;
rectangleShape.LineWeight = 1.5; // points
```

### 3. Posicionar o retângulo absolutamente

Para controle preciso de layout, altere o `WrapType` da forma para `WrapType.Inline` (padrão) ou `WrapType.TopBottom` e ajuste as propriedades `Left`/`Top`:

```csharp
rectangleShape.WrapType = WrapType.TopBottom;
rectangleShape.Left = 72;   // 1 inch from the left margin
rectangleShape.Top = 144;   // 2 inches from the top margin
```

### 4. Usando uma unidade de medida diferente

O Aspose.Words trabalha em pontos (1 pt = 1/72 polegada). Se preferir centímetros, converta primeiro:

```csharp
float cmToPoints = 28.3465f; // 1 cm ≈ 28.3465 pt
float width = 5 * cmToPoints;   // 5 cm wide
float height = 2 * cmToPoints;  // 2 cm tall
Shape cmRectangle = builder.InsertShape(ShapeType.Rectangle, width, height);
```

## Exemplo completo executável

Abaixo está o programa *completo* que você pode copiar, colar e executar. Ele inclui todas as diretivas `using` necessárias e usa caminhos absolutos que você deve ajustar ao seu ambiente.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class InsertRectangleShapeDemo
{
    static void Main()
    {
        // Create a blank document.
        Document doc = new Document();

        // Use DocumentBuilder to edit the document.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 100 × 50 pt rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // Set the fill color to yellow.
        rect.FillColor = Color.Yellow;

        // Hide the shape so it does not affect layout.
        rect.Hidden = true;

        // Save the result.
        string outputPath = @"C:\Temp\HiddenRectangleShape.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Resultado esperado**: O arquivo `HiddenRectangleShape.docx` abre no Microsoft Word sem nenhuma forma visível, mas o retângulo oculto está presente no XML do documento. Você pode verificar sua existência abrindo o .docx como um arquivo zip e inspecionando `word/document.xml` para um elemento `<w:shape>` com os atributos `w:fill="yellow"` e `w:hidden="true"`.

## Conclusão

Agora você sabe como **inserir forma retangular** em um documento Word usando C# e Aspose.Words, como **definir a cor de preenchimento** e como **ocultar a forma** para que ela permaneça invisível no layout final. O mesmo padrão funciona para outros tipos de forma, cores personalizadas e modelos existentes. Experimente bordas, posicionamento absoluto e diferentes unidades de medida para adaptar a forma aos seus requisitos exatos.

### Próximos passos

* Explore **como inserir forma** dentro de tabelas ou cabeçalhos/rodapés para marcas d'água.
* Combine **adicionar forma retangular** com controles de conteúdo para criar espaços reservados dinâmicos.
* Revise a API de **manipulação de formas** do Aspose.Words para recursos avançados como rotação, preenchimentos gradientes e importação de SVG.

Sinta‑se à vontade para adaptar o código ao seu próprio projeto e nos informe nos comentários qual desafio relacionado a formas você resolveu a seguir!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Criar forma retangular no Word usando C# – Guia passo a passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Tutorial de Sombra de Forma Aspose.Words – Adicionar sombra a forma Word em C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Criar Forma de Grupo em Documento Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}