---
category: general
date: 2026-08-04
description: Inserir forma retangular em um documento Word com C#. Aprenda como agrupar
  formas no Word, salvar o documento como docx e usar DocumentBuilder para layouts
  avançados.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to group shapes
- group shapes in word
- save document as docx
- how to use builder
language: pt
lastmod: 2026-08-04
og_description: Inserir forma retangular em um arquivo Word usando C# e, em seguida,
  agrupar formas para layouts avançados. Este tutorial também aborda salvar o documento
  como docx e usar o DocumentBuilder de forma eficiente.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with C# DocumentBuilder
og_title: Inserir forma retangular no Word – Guia passo a passo em C#
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Insert rectangle shape in a Word document with C#. Learn how to group
    shapes in Word, save document as docx, and use DocumentBuilder for advanced layouts.
  headline: Insert rectangle shape in Word using C# – complete guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Inserir forma de retângulo no Word usando C# – guia completo
url: /pt/java/images-shapes/insert-rectangle-shape-in-word-using-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Inserir forma retangular no Word usando C# – guia completo

Se você precisa **inserir forma retangular** em um documento Word usando C#, este tutorial mostra exatamente como fazer. Você também aprenderá **como agrupar formas** no Word, **salvar documento como docx** e **como usar Builder** para um código limpo e de fácil manutenção.

Trabalhar com formas é uma necessidade comum ao gerar relatórios, certificados ou layouts personalizados programaticamente. Ao final deste guia você terá um exemplo totalmente executável que cria um retângulo, adiciona uma elipse, os agrupa e salva o resultado como um arquivo DOCX.

## Pré-requisitos

* .NET 6.0 ou posterior instalado  
* Visual Studio 2022 (ou qualquer IDE que suporte C#)  
* A biblioteca **Aspose.Words for .NET** (disponível via NuGet)  

Você pode adicionar a biblioteca com o seguinte comando:

```bash
dotnet add package Aspose.Words
```

## Inserir forma retangular com DocumentBuilder

O primeiro passo é criar um novo `Document` e um `DocumentBuilder`. O builder fornece uma API fluente para inserir conteúdo, incluindo formas.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document.
        Document document = new Document();

        // Initialize the builder that will edit the document.
        DocumentBuilder builder = new DocumentBuilder(document);
```

A instância `DocumentBuilder` é o objeto principal que você usará para **inserir forma retangular** e outros elementos. Ela rastreia a posição atual do cursor dentro do documento, de modo que qualquer inserção ocorre exatamente onde você precisa.

## Como inserir uma forma retangular

Com o builder pronto, chame `InsertShape`. Você especifica o `ShapeType`, a largura e a altura em pontos (1 pt ≈ 1/72 in).

```csharp
        // Insert a rectangle of 100 pt width and 50 pt height.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
```

*Por que isso importa*: Definir `FillColor` e `StrokeColor` torna o retângulo visualmente distinto, o que ajuda quando você posteriormente o agrupa com outras formas.

## Como agrupar formas no Word

Agrupar formas permite mover, girar ou formatar vários objetos como uma única entidade. Após inserir o retângulo, adicione outra forma (uma elipse neste exemplo) e então crie um `GroupShape`.

```csharp
        // Insert an ellipse of 80 pt diameter.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // Insert an empty group container.
        GroupShape groupShape = builder.InsertGroupShape();

        // Add the rectangle and ellipse to the group.
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
```

A chamada `InsertGroupShape` cria um placeholder que pode conter qualquer número de formas filhas. Ao anexar o retângulo e a elipse, você efetivamente **agrupa formas no Word**. O grupo se comporta como uma única forma — você pode reposicioná-lo, aplicar uma borda ou redimensioná-lo sem afetar o layout interno de cada filho.

### Dica profissional

Após agrupar, você pode alterar a posição do grupo em relação à página:

```csharp
        // Move the whole group 150 pt right and 100 pt down.
        groupShape.Left = 150;
        groupShape.Top = 100;
```

## Salvar documento como docx

Depois que as formas são organizadas, você precisa persistir o arquivo. O método `Document.Save` determina automaticamente o formato a partir da extensão do arquivo. Para **salvar documento como docx**, passe um caminho que termine com `.docx`.

```csharp
        // Save the document to the output folder.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

Executar o programa cria `output.docx`. Abra o arquivo no Microsoft Word e você verá um retângulo azul‑claro e uma elipse coral‑claro agrupados. Você pode clicar no grupo e movê‑lo como um único objeto.

## Como usar o DocumentBuilder de forma eficaz

`DocumentBuilder` é mais do que um inseridor de formas; ele também lida com texto, tabelas, cabeçalhos e rodapés. Quando você combina a criação de formas com texto, lembre‑se de redefinir o cursor se precisar inserir conteúdo em outro lugar:

```csharp
        // Move the cursor to a new paragraph after the group.
        builder.Writeln(); // Inserts a line break.
        builder.Font.Size = 12;
        builder.Writeln("Shapes have been added and grouped successfully.");
```

Manter o estado do builder explícito evita sobrescritas acidentais e torna o código mais fácil de manter.

## Casos de borda e variações

| Situação | Abordagem recomendada |
|-----------|----------------------|
| **Mais de duas formas** | Insira cada forma, então chame `AppendChild` para cada forma antes de salvar. |
| **Grupos aninhados** | Crie um grupo, adicione formas e, em seguida, insira esse grupo em outro `GroupShape`. |
| **Unidades de medida diferentes** | Use `builder.ConvertPixelsToPoints` se você tem dimensões em pixels. |
| **Compatibilidade com versões mais antigas do Word** | Salve como `.doc` alterando a extensão; a maioria dos recursos de forma ainda funciona. |

## Exemplo completo em funcionamento

Abaixo está o programa completo que você pode copiar‑colar em um novo projeto de console. Nenhum snippet adicional é necessário.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;

        // 3️⃣ Insert an ellipse shape.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // 4️⃣ Create a group shape and add both shapes.
        GroupShape groupShape = builder.InsertGroupShape();
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Optional: reposition the group.
        groupShape.Left = 150;
        groupShape.Top = 100;

        // 5️⃣ Add a caption below the group.
        builder.Writeln();
        builder.Font.Size = 12;
        builder.Writeln("Grouped rectangle and ellipse created with DocumentBuilder.");

        // 6️⃣ Save the document as DOCX.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

**Resultado esperado**: Ao abrir `output.docx` mostra um retângulo azul‑claro e uma elipse coral‑claro agrupados, posicionados a 150 pt da margem esquerda e 100 pt do topo. A legenda aparece abaixo do grupo.

## Conclusão

Agora você sabe como **inserir forma retangular** em um arquivo Word usando C#, **como agrupar formas no Word** e **como salvar documento como docx** com o `DocumentBuilder` da Aspose.Words. Ao dominar essas etapas, você pode criar layouts complexos — certificados, relatórios ou formulários personalizados — totalmente por código.

Em seguida, explore tópicos relacionados como **adicionar caixas de texto**, **trabalhar com tabelas** ou **exportar para PDF**. Cada um desses se baseia nos mesmos fundamentos do `DocumentBuilder` que você acabou de praticar.

Pronto para automatizar seus documentos Word? Experimente estender o exemplo com mais formas, aplicar gradientes ou percorrer dados para gerar um relatório completo em uma única execução. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Criar Forma de Grupo em Documento Word Usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Inserir Formas em Documentos Word Usando Aspose.Words para .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Criar forma retangular no Word com Aspose.Words – Guia passo a passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}