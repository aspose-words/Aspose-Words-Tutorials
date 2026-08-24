---
category: general
date: 2026-08-23
description: Aprenda a agrupar formas em C# usando Aspose.Words. O guia também aborda
  como inserir uma forma retangular e adicionar formas ao Word para documentos complexos.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- add shapes word
- group multiple shapes
- how to start group
language: pt
lastmod: 2026-08-23
og_description: Como agrupar formas em C# com Aspose.Words. Siga este tutorial completo
  para inserir forma de retângulo, adicionar formas ao Word e agrupar várias formas
  de forma eficiente.
og_image_alt: How to group shapes in C# using Aspose.Words
og_title: Como agrupar formas em C# – guia passo a passo
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Learn how to group shapes in C# using Aspose.Words. The guide also
    covers how to insert rectangle shape and add shapes word for complex documents.
  headline: How to group shapes in C# with Aspose.Words
  type: TechArticle
- description: Learn how to group shapes in C# using Aspose.Words. The guide also
    covers how to insert rectangle shape and add shapes word for complex documents.
  name: How to group shapes in C# with Aspose.Words
  steps:
  - name: '**Nested groups** – Aspose.Words allows groups within groups. To create
      a nested group, call `StartGroupShape` again before calling `EndGroupShape`
      for the inner group.'
    text: '**Nested groups** – Aspose.Words allows groups within groups. To create
      a nested group, call `StartGroupShape` again before calling `EndGroupShape`
      for the inner group.'
  - name: '**Empty groups** – If you start a group but never insert a shape, `EndGroupShape`
      will still create an empty container. This is harmless but may increase file
      size slightly.'
    text: '**Empty groups** – If you start a group but never insert a shape, `EndGroupShape`
      will still create an empty container. This is harmless but may increase file
      size slightly.'
  - name: '**Compatibility** – The generated DOCX works with Word 2010 and later.
      Older versions may ignore grouping metadata, so always test with the target
      Word version.'
    text: '**Compatibility** – The generated DOCX works with Word 2010 and later.
      Older versions may ignore grouping metadata, so always test with the target
      Word version.'
  type: HowTo
- questions:
  - answer: Yes. Retrieve the existing `Shape` objects, call `builder.StartGroupShape()`,
      re‑insert them with `builder.InsertShape(existingShape)`, then call `EndGroupShape()`.
    question: Can I group shapes that already exist in the document?
  - answer: Aspose.Words adds a `<w:grpSp>` element that contains each shape’s `<w:sp>`
      node. This is fully compliant with the Office Open XML specification.
    question: Does grouping affect the underlying XML?
  - answer: 'There is no direct “ungroup” API, but you can iterate through the child
      shapes of the group (`group.GroupShape.Children`) and copy them out to the document
      body. ## Next steps Now that you know **how to group shapes**, consider exploring
      these related topics: - **Apply complex formatting to grouped '
    question: What if I need to ungroup later?
  type: FAQPage
tags:
- Aspose.Words
- C#
- shapes
- document automation
title: Como agrupar formas em C# com Aspose.Words
url: /pt/net/programming-with-shapes/how-to-group-shapes-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como agrupar formas em C# com Aspose.Words

Se você precisa **how to group shapes** em um documento Word programaticamente, este tutorial mostra os passos exatos usando Aspose.Words para .NET. Seja construindo um gerador de relatórios, um motor de templates ou uma ferramenta de diagramas, você aprenderá como iniciar um grupo, inserir uma forma retangular e adicionar conteúdo de nível Word às formas sem sair do seu código.

Você também verá como **group multiple shapes** juntos, o que é essencial quando você deseja mover, girar ou estilizar uma coleção de objetos como uma única entidade. O exemplo abaixo funciona com a versão mais recente do Aspose.Words 24.x e requer apenas .NET 6 ou posterior.

## Pré-requisitos

- .NET 6 SDK (ou qualquer versão .NET suportada pelo Aspose.Words)
- Visual Studio 2022 ou VS Code
- Pacote NuGet Aspose.Words para .NET (`Install-Package Aspose.Words`)
- Familiaridade básica com C# e o modelo de objetos Aspose.Words

> **Dica profissional:** Use a licença de avaliação gratuita da Aspose para evitar limitações de marca d'água durante os testes.

## Como agrupar formas com Aspose.Words

Abaixo está um programa completo e executável que demonstra **how to start group**, adiciona um retângulo e finaliza o grupo. O código segue o mesmo fluxo lógico do trecho que você forneceu, mas adiciona contexto, tratamento de erros e comentários para clareza.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank document.
            Document doc = new Document();

            // 2️⃣ Get a DocumentBuilder to insert content.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Start a group shape – all shapes added after this call belong to the group.
            // This is the “how to start group” step.
            Shape group = builder.StartGroupShape();

            // 4️⃣ Insert individual shapes inside the group.
            //    a) Insert a rectangle shape (demonstrates “insert rectangle shape”).
            builder.InsertShape(ShapeType.Rectangle, 150, 80);
            //    b) Insert a simple ellipse for visual variety.
            builder.InsertShape(ShapeType.Ellipse, 100, 60);
            //    c) Add a WordArt‑style text shape – shows “add shapes word”.
            builder.InsertShape(ShapeType.TextPlainText, 200, 40);
            builder.Writeln("Grouped Text"); // adds text inside the last shape

            // 5️⃣ Close the group shape to finalize the grouping.
            builder.EndGroupShape();

            // Optional: Save the document to verify the result.
            string outPath = "GroupedShapes.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Por que cada passo importa

| Etapa | Propósito | Como se relaciona com as palavras‑chave |
|------|-----------|----------------------------------------|
| **Create a new blank document** | Fornece uma tela limpa para operações de forma. | Prepara o cenário para **add shapes word** posteriormente. |
| **Initialize DocumentBuilder** | O builder é a API principal para inserção de objetos. | Necessário antes de você poder **how to start group**. |
| **StartGroupShape** | Inicia um contêiner lógico; todas as formas subsequentes tornam‑se membros deste grupo. | Responde diretamente a **how to start group**. |
| **InsertShape** (rectangle, ellipse, text) | Coloca formas individuais dentro do grupo. A chamada de retângulo satisfaz **insert rectangle shape**; a forma de texto satisfaz **add shapes word**. | Demonstra **group multiple shapes**. |
| **EndGroupShape** | Finaliza o grupo para que você possa mover ou estilizar como uma unidade. | Completa o fluxo de trabalho **how to group shapes**. |

## Inserindo uma forma retangular – mergulho profundo

O método `InsertShape` aceita um enum `ShapeType`, largura e altura. Para **insert rectangle shape** com estilo personalizado, você pode estender o exemplo:

```csharp
// Insert a styled rectangle
Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rect.FillColor = System.Drawing.Color.LightBlue;
rect.StrokeColor = System.Drawing.Color.DarkBlue;
rect.LineWidth = 2.0;
```

> **Por que estilizar?** A estilização garante que o retângulo se destaque quando o grupo for reposicionado posteriormente. Também demonstra que as propriedades da forma podem ser definidas *antes* do grupo ser fechado.

## Adicionando formas em nível Word (add shapes word)

Se você precisar incorporar texto diretamente dentro de uma forma — comumente chamada de “WordArt” ou “caixa de texto” — use `ShapeType.TextPlainText`. Após inserir, você pode escrever texto na forma com `DocumentBuilder.Writeln` ou acessando a propriedade `TextBox` da forma:

```csharp
Shape textBox = builder.InsertShape(ShapeType.TextPlainText, 250, 50);
textBox.TextBox.Text = "Hello, grouped world!";
```

Isso satisfaz a palavra‑chave **add shapes word** e mostra como o texto pode viajar com o grupo.

## Agrupando várias formas – cenários práticos

Quando você **group multiple shapes**, pode tratá‑las como um único objeto para posicionamento, rotação ou dimensionamento. Por exemplo, após o grupo ser fechado, você pode mover todo o grupo:

```csharp
// Move the entire group 100 points to the right and 50 points down.
group.Left += 100;
group.Top += 50;
```

Ou girar o grupo:

```csharp
group.Rotation = 45; // degrees
```

Essas operações só são possíveis porque as formas compartilham o mesmo grupo pai.

## Tratamento de casos extremos

1. **Nested groups** – Aspose.Words permite grupos dentro de grupos. Para criar um grupo aninhado, chame `StartGroupShape` novamente antes de chamar `EndGroupShape` para o grupo interno.  
2. **Empty groups** – Se você iniciar um grupo mas nunca inserir uma forma, `EndGroupShape` ainda criará um contêiner vazio. Isso não causa problemas, mas pode aumentar o tamanho do arquivo ligeiramente.  
3. **Compatibility** – O DOCX gerado funciona com Word 2010 e posteriores. Versões mais antigas podem ignorar os metadados de agrupamento, portanto sempre teste com a versão alvo do Word.

## Arquivo fonte completo para referência

Salve o seguinte como `Program.cs` em um projeto console .NET. O código compila e executa sem modificações.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document.
            Document doc = new Document();

            // Step 2: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Start the group – “how to start group”.
            Shape group = builder.StartGroupShape();

            // Step 4a: Insert a rectangle – “insert rectangle shape”.
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 150, 80);
            rect.FillColor = System.Drawing.Color.LightCoral;
            rect.StrokeColor = System.Drawing.Color.DarkRed;
            rect.LineWidth = 1.5;

            // Step 4b: Insert an ellipse (additional shape for grouping).
            builder.InsertShape(ShapeType.Ellipse, 100, 60);

            // Step 4c: Add a text box – “add shapes word”.
            Shape txt = builder.InsertShape(ShapeType.TextPlainText, 200, 40);
            txt.TextBox.Text = "Grouped Text";

            // Step 5: End the group – completes “how to group shapes”.
            builder.EndGroupShape();

            // Optional: Adjust group position.
            group.Left += 50;
            group.Top += 30;

            // Save the result.
            string outPath = "GroupedShapes.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Saída esperada

Abrir `GroupedShapes.docx` no Microsoft Word mostrará:

- Um retângulo coral‑claro, uma elipse e uma caixa de texto — todos visualmente ligados juntos.  
- Selecionar qualquer parte do grupo também seleciona todo o grupo (aparece uma única caixa delimitadora).  
- Mover ou girar o grupo move todas as três formas juntas.

## Perguntas frequentes

**Q: Posso agrupar formas que já existem no documento?**  
A: Sim. Recupere os objetos `Shape` existentes, chame `builder.StartGroupShape()`, reinsira‑os com `builder.InsertShape(existingShape)`, então chame `EndGroupShape()`.

**Q: O agrupamento afeta o XML subjacente?**  
A: Aspose.Words adiciona um elemento `<w:grpSp>` que contém o nó `<w:sp>` de cada forma. Isso está totalmente em conformidade com a especificação Office Open XML.

**Q: E se eu precisar desagrupar mais tarde?**  
A: Não há uma API direta de “ungroup”, mas você pode iterar sobre as formas filhas do grupo (`group.GroupShape.Children`) e copiá‑las para o corpo do documento.

## Próximos passos

Agora que você sabe **how to group shapes**, considere explorar estes tópicos relacionados:

- **Apply complex formatting to grouped shapes** – aprenda como definir preenchimentos em gradiente, efeitos de sombra e estilos de linha.  
- **Export grouped shapes as images** – use `Shape.GetShapeRenderer().Save(...)` para rasterizar um grupo.  
- **Create dynamic diagrams** – combine posicionamento orientado a dados com agrupamento para gerar fluxogramas automaticamente.

Cada um desses se baseia na fundação abordada aqui e ajudará você a criar documentos Word mais ricos e interativos.

*Feliz codificação! Se você achou este guia útil, compartilhe com colegas ou dê uma estrela ao repositório que contém o projeto de exemplo.*

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Inserir formas em documentos Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Criar forma de grupo em documento Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Criar forma retangular no Word com Aspose.Words – Guia passo a passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}