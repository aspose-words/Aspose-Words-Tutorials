---
category: general
date: 2026-09-21
description: Crie um documento Word em branco usando Aspose.Words, defina o tamanho
  da forma, defina a posição da forma, defina a cor da forma e salve o arquivo docx
  em um único passo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set shape size
- save docx file
- set shape position
- set shape color
language: pt
lastmod: 2026-09-21
og_description: Crie um documento Word em branco, defina o tamanho da forma, defina
  a posição da forma, defina a cor da forma e salve o arquivo docx com Aspose.Words
  em minutos.
og_image_alt: Screenshot of a blank Word document containing two colored rectangles
  grouped together
og_title: Crie um documento Word em branco e adicione formas coloridas – Guia Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create a blank Word document using Aspose.Words, set shape size, set
    shape position, set shape color, and save the docx file in a single walkthrough.
  headline: Create a blank Word document and add colored shapes with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Crie um documento Word em branco e adicione formas coloridas com Aspose.Words
url: /pt/net/programming-with-shapes/create-a-blank-word-document-and-add-colored-shapes-with-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crie um documento Word em branco e adicione formas coloridas com Aspose.Words

Se você precisa **criar um documento Word em branco** programaticamente, este guia mostra como fazer isso com Aspose.Words. Você aprenderá a **definir o tamanho da forma**, **definir a posição da forma**, **definir a cor da forma** e, finalmente, **salvar o arquivo docx** sem sair do seu IDE.

Trabalhar com arquivos Word em C# costuma envolver chamadas de baixo nível ao OpenXML, mas o Aspose.Words abstrai essa complexidade. Ao final deste tutorial você terá um `.docx` totalmente funcional que contém um grupo de formas composto por dois retângulos coloridos — perfeito para relatórios, certificados ou modelos personalizados.

## Pré‑requisitos

- .NET 6.0 ou superior (o código também funciona com .NET Framework 4.7+)
- Aspose.Words for .NET 23.9 ou mais recente (instale via NuGet: `Install-Package Aspose.Words`)
- Familiaridade básica com C# e Visual Studio (ou qualquer editor C#)

Nenhum arquivo Word existente é necessário; o tutorial começa **criando um documento Word em branco** do zero.

## Crie um documento Word em branco com Aspose.Words

A primeira etapa é instanciar um objeto `Document`. Esse objeto representa um arquivo Word vazio na memória.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty document.
Document document = new Document();

// DocumentBuilder gives you a cursor to add content.
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` começa vazio, que é exatamente o que você precisa ao **criar um documento Word em branco**. O `builder` será usado posteriormente para inserir o grupo de formas na posição atual do cursor.

## Defina o tamanho da forma e crie um GroupShape

Um `GroupShape` funciona como um contêiner que pode conter várias formas individuais. Primeiro, defina as dimensões gerais do contêiner.

```csharp
// Create a GroupShape that will hold multiple shapes.
// Width = 300 points, Height = 200 points.
GroupShape groupShape = new GroupShape(document, 300, 200);

// Position the group on the page: 100 points from the left, 100 points from the top.
groupShape.Left = 100;
groupShape.Top  = 100;
```

Aqui nós **definimos o tamanho da forma** para o próprio grupo (300 × 200). Os mesmos nomes de propriedades (`Width`, `Height`) são usados para cada forma filha, oferecendo controle detalhado sobre cada elemento.

## Adicione o primeiro retângulo e defina a cor da forma

Agora adicione um retângulo ao grupo e atribua-lhe uma cor de fundo.

```csharp
// First rectangle – light blue background.
Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 0,          // Position relative to the group’s left edge.
    Top = 0,           // Position relative to the group’s top edge.
    FillColor = Color.LightBlue
};

// Append the rectangle to the group.
groupShape.AppendChild(rectangle1);
```

A propriedade `FillColor` **define a cor da forma**. Usar `System.Drawing.Color` permite escolher qualquer valor ARGB predefinido ou personalizado.

## Adicione um segundo retângulo, defina seu tamanho, posição e cor

Um segundo retângulo demonstra como **definir a posição da forma** em relação ao grupo e como alterar sua cor.

```csharp
// Second rectangle – light coral background.
Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 150,               // 150 points to the right of the group’s left edge.
    Top = 0,                  // Same vertical alignment as the first rectangle.
    FillColor = Color.LightCoral
};

groupShape.AppendChild(rectangle2);
```

Como a largura do grupo é 300 pontos, os dois retângulos de 120 pontos cabem confortavelmente com um espaçamento de 30 pontos. Ajuste `Left` e `Top` se precisar de um layout diferente.

## Insira o GroupShape no documento

Com o grupo totalmente configurado, posicione‑o na posição atual do cursor.

```csharp
// Insert the completed group shape at the builder’s current location.
builder.InsertNode(groupShape);
```

`InsertNode` grava a forma diretamente no corpo do documento, preservando a **posição da forma** exata que você definiu anteriormente.

## Salve o arquivo docx

A etapa final é persistir o documento no disco. Isso demonstra a operação de **salvar arquivo docx**.

```csharp
// Define the output path (ensure the directory exists).
string outputPath = @"C:\Temp\GroupShape.docx";

// Save the document in DOCX format.
document.Save(outputPath);
```

Depois de executar o programa, abra `GroupShape.docx` no Microsoft Word. Você deverá ver uma página em branco com um grupo de formas contendo dois retângulos coloridos posicionados lado a lado.

### Saída esperada

- Um arquivo `.docx` de página única.  
- A página contém um grupo de formas localizado a 100 pts das margens esquerda e superior.  
- Dentro do grupo, um retângulo azul‑claro fica à esquerda e um retângulo coral‑claro à direita, cada um com 120 × 80 pts.

## Exemplo completo, executável

Abaixo está o programa completo que você pode copiar‑colar em uma aplicação console. Nenhum arquivo adicional é necessário.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Define a GroupShape and set its size and position.
        GroupShape groupShape = new GroupShape(document, 300, 200)
        {
            Left = 100,
            Top = 100
        };

        // 3️⃣ First rectangle – set size, position, and color.
        Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 0,
            Top = 0,
            FillColor = Color.LightBlue
        };
        groupShape.AppendChild(rectangle1);

        // 4️⃣ Second rectangle – set size, position, and color.
        Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 150,
            Top = 0,
            FillColor = Color.LightCoral
        };
        groupShape.AppendChild(rectangle2);

        // 5️⃣ Insert the grouped shape into the document.
        builder.InsertNode(groupShape);

        // 6️⃣ Save the docx file.
        string outputPath = @"C:\Temp\GroupShape.docx";
        document.Save(outputPath);

        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Executar este programa cria exatamente o documento descrito anteriormente, atendendo aos quatro objetivos: **criar documento Word em branco**, **definir tamanho da forma**, **definir posição da forma**, **definir cor da forma** e **salvar arquivo docx**.

## Variações comuns e casos de borda

| Cenário | O que mudar | Por que importa |
|----------|----------------|----------------|
| **Tipos de forma diferentes** | Substitua `ShapeType.Rectangle` por `ShapeType.Ellipse`, `ShapeType.Triangle`, etc. | Permite criar gráficos mais complexos sem imagens externas. |
| **Dimensões dinâmicas** | Calcule `Width` e `Height` a partir de entrada do usuário ou arquivos de configuração. | Torna a solução reutilizável em múltiplos modelos de documento. |
| **Salvar como PDF** | Chame `document.Save("output.pdf", SaveFormat.Pdf);` | Se os destinatários precisarem de um formato não editável, PDF é uma escolha segura. |
| **Adicionar texto dentro de uma forma** | Crie uma forma `TextBox` e defina `TextBox.Text`. | Útil para criar crachás rotulados ou balões de chamada. |
| **Múltiplos grupos em uma página** | Repita as etapas 2‑5 com valores diferentes de `Left`/`Top`. | Permite construir dashboards ou layouts de múltiplas seções. |

### Dica profissional

Quando precisar alinhar formas com precisão, use a propriedade `ShapeBase.WrapType = WrapType.Inline` antes de inserir o grupo. Isso faz com que o grupo se comporte como um parágrafo, evitando fluxo de texto inesperado ao seu redor.

## Conclusão

Agora você sabe como **criar um documento Word em branco** com Aspose.Words, **definir o tamanho da forma**, **definir a posição da forma**, **definir a cor da forma** e **salvar o arquivo docx**. O exemplo completo demonstra um padrão limpo e reutilizável para adicionar gráficos agrupados a qualquer projeto de automação Word.

A partir daqui, você pode explorar:

- Adicionar mais formas ou imagens ao mesmo `GroupShape` (variações de **definir tamanho da forma**, **definir cor da forma**).  
- Usar `ShapeBase.Rotation` para girar retângulos e criar efeitos decorativos.  
- Exportar o mesmo documento como PDF ou HTML para ampliar a distribuição (alternativa ao **salvar arquivo docx**).

Sinta‑se à vontade para experimentar diferentes cores, tamanhos e lógicas de layout para atender às suas necessidades específicas de relatórios ou modelagem. Boa codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que expandem as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}