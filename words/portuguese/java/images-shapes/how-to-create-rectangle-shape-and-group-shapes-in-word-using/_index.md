---
category: general
date: 2026-11-18
description: Aprenda como criar uma forma retangular em um documento do Word com C#.
  O guia também aborda como definir o tamanho da forma, definir a posição da forma
  e agrupar formas no Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- set shape size
- group shapes in word
- set shape dimensions
- set shape position
language: pt
lastmod: 2026-11-18
og_description: Crie uma forma retangular em um arquivo Word usando C# e aprenda a
  definir as dimensões da forma, definir a posição da forma e agrupar formas no Word.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape created with C#
og_title: Criar forma de retângulo e agrupar formas no Word com C#
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  headline: How to create rectangle shape and group shapes in Word using C#
  type: TechArticle
- description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  name: How to create rectangle shape and group shapes in Word using C#
  steps:
  - name: Initialize the document and builder
    text: '```csharp using System; using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert a group shape
    text: '```csharp // Step 2: Insert a group shape that will hold multiple child
      shapes GroupShape group = builder.InsertGroupShape(); ```'
  - name: Create the rectangle and set its size
    text: '```csharp // Step 3: Create a rectangle shape, set its size, and add it
      to the group Shape rectangle = new Shape(doc, ShapeType.Rectangle); rectangle.Width
      = 100; // set shape size (width) in points rectangle.Height = 50; // set shape
      size (height) in points group.AppendChild(rectangle); ```'
  - name: Create the ellipse, set dimensions, and position it
    text: '```csharp // Step 4: Create an ellipse shape, set its size and position,
      and add it to the group Shape ellipse = new Shape(doc, ShapeType.Ellipse); ellipse.Width
      = 80; // set shape dimensions (width) ellipse.Height = 80; // set shape dimensions
      (height) ellipse.Left = 120; // set shape position rela'
  - name: Save the document
    text: '```csharp // Step 5: Save the document containing the grouped shapes doc.Save("GroupShape.docx");
      Console.WriteLine("Document saved successfully."); } } ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Como criar forma retangular e agrupar formas no Word usando C#
url: /pt/java/images-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-using/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar forma retangular e agrupar formas no Word usando C#

Se você precisa **criar forma retangular** em um documento Word, este tutorial mostra uma solução completa e pronta‑para‑executar. Você verá como definir o tamanho da forma, definir a posição da forma e agrupar formas no Word para que elas se comportem como um único objeto.

Trabalhar com formas é uma necessidade comum ao gerar relatórios, faturas ou diagramas programaticamente. Ao final deste guia, você será capaz de gerar um arquivo `.docx` que contém um retângulo, uma elipse e um contêiner agrupado — tudo criado com Aspose.Words for .NET.

## Pré-requisitos

- .NET 6.0 SDK ou posterior (o código também funciona com .NET Framework 4.7+)
- Pacote NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)
- Um editor de código ou IDE (Visual Studio, VS Code, Rider, etc.)

Nenhuma biblioteca adicional é necessária.

## Como criar forma retangular e agrupar formas no Word

Os passos principais são:

1. **Criar um documento em branco** e um `DocumentBuilder`.
2. **Inserir um `GroupShape`** que conterá as formas individuais.
3. **Criar uma forma retangular**, definir suas dimensões e adicioná‑la ao grupo.
4. **Criar uma forma elíptica**, definir seu tamanho e posição, e adicioná‑la ao grupo.
5. **Salvar** o documento.

Cada passo é explicado abaixo, e o código‑fonte completo segue a explicação.

### Passo 1: Inicializar o documento e o construtor

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` representa todo o arquivo Word, enquanto `DocumentBuilder` fornece uma API fluente para inserir conteúdo. Inicializá‑los é obrigatório antes de poder adicionar quaisquer formas.

### Passo 2: Inserir uma forma de grupo

```csharp
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape group = builder.InsertGroupShape();
```

Um `GroupShape` funciona como um contêiner; todas as formas filhas se movem juntas. Esta é a forma recomendada de **agrupar formas no Word** quando você precisa de transformações coletivas (por exemplo, mover, girar ou excluir).

### Passo 3: Criar o retângulo e definir seu tamanho

```csharp
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle);
```

Aqui nós **criamos a forma retangular** e **definimos o tamanho da forma** atribuindo `Width` e `Height`. No Aspose.Words, os tamanhos são expressos em pontos (1 pt ≈ 1/72 in). Definir as dimensões explicitamente garante que o retângulo apareça exatamente como desejado.

### Passo 4: Criar a elipse, definir dimensões e posicioná‑la

```csharp
        // Step 4: Create an ellipse shape, set its size and position, and add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position relative to the group
        group.AppendChild(ellipse);
```

As **dimensões da forma** para a elipse são idênticas para largura e altura, produzindo um círculo perfeito. A propriedade `Left` demonstra **definir a posição da forma**: a elipse começa 120 pt à direita da origem do grupo, de modo que não sobrepõe o retângulo.

### Passo 5: Salvar o documento

```csharp
        // Step 5: Save the document containing the grouped shapes
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document saved successfully.");
    }
}
```

Salvar grava o arquivo Word no disco. Você pode abrir `GroupShape.docx` no Microsoft Word para verificar que o retângulo e a elipse estão agrupados e posicionados corretamente.

## Definindo dimensões e tamanho da forma – análise aprofundada

- **Pontos vs. polegadas**: 72 pt = 1 in. Se preferir polegadas, multiplique por 72 (por exemplo, `2.5 * 72` para 2,5 in).
- **Dimensionamento automático**: Se você omitir `Width` ou `Height`, a forma usará seu tamanho padrão. Defina explicitamente **o tamanho da forma** para evitar surpresas de layout.
- **Proporção**: Para formas como `Ellipse`, manter `Width` e `Height` iguais mantém a aparência circular.

## Posicionamento de uma forma no Word

As propriedades `Left` e `Top` controlam o deslocamento da forma dentro de seu contêiner (o grupo ou a página). Valores positivos movem a forma para a direita/para baixo; valores negativos deslocam‑na para a esquerda/para cima. Ao agrupar, as posições são relativas à origem do grupo, o que simplifica os cálculos de layout.

## Agrupando formas no Word usando Aspose.Words

Agrupar é essencial quando você deseja que várias formas atuem como uma única unidade. O objeto `GroupShape`:

- Suporta `AppendChild` para adicionar qualquer `Shape` (retângulo, elipse, imagem, etc.).
- Permite mover, girar ou excluir todo o grupo com uma única chamada.
- Mantém as posições das formas filhas relativas ao grupo, facilitando o gerenciamento de diagramas complexos.

**Dica profissional:** Após adicionar todas as formas filhas, você pode ajustar `Width`, `Height`, `Left` e `Top` do grupo para reposicionar toda a coleção em um único passo.

## Exemplo completo executável

Abaixo está o programa completo que você pode copiar, colar e executar. Ele inclui todas as diretivas `using`, um método `Main` e comentários que explicam cada linha.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a GroupShape to hold child shapes
        GroupShape group = builder.InsertGroupShape();

        // 3️⃣ Create a rectangle, set its dimensions, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle); // add rectangle to the group

        // 4️⃣ Create an ellipse, set size and position, then add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position inside the group
        group.AppendChild(ellipse); // add ellipse to the group

        // 5️⃣ Save the document
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document 'GroupShape.docx' created with a rectangle and an ellipse grouped together.");
    }
}
```

**Saída esperada:** Após executar o programa, `GroupShape.docx` aparece na pasta de execução. Ao abri‑lo no Word, mostra um retângulo (100 pt × 50 pt) à esquerda e uma elipse (80 pt × 80 pt) posicionada 120 pt à direita, ambos dentro de um único objeto agrupado.

![Word document with grouped rectangle and ellipse](grouped_shapes.png){: .center alt="Captura de tela de um documento Word mostrando um retângulo e uma elipse agrupados criados com C#" }

*A imagem acima ilustra o resultado final; o retângulo e a elipse são selecionáveis como um único grupo.*

## Perguntas frequentes e casos de borda

| Pergunta | Resposta |
|----------|----------|
| **Posso adicionar mais de duas formas?** | Sim. Chame `group.AppendChild(yourShape)` para cada forma adicional. |
| **E se eu precisar girar o grupo?** | Use `group.RotationAngle = 45;` (graus) após adicionar todos os filhos. |
| **Como altero a cor de fundo do grupo?** | Defina `group.FillColor = System.Drawing.Color.LightGray;`. |
| **Isso funciona com arquivos .doc?** | Aspose.Words suporta `.doc` e `.docx`. O mesmo código funciona; basta mudar a extensão do arquivo em `Save`. |
| **Há impacto de memória ao agrupar muitas formas?** | Agrupar em si adiciona sobrecarga mínima. A principal preocupação é o número total de formas; mantenha‑o razoável para documentos grandes. |

## Conclusão

Neste tutorial você aprendeu como **criar forma retangular** em um arquivo Word usando C#, como **definir o tamanho da forma**, **definir as dimensões da forma**, **definir a posição da forma**, e finalmente como **agrupar formas no Word** com Aspose.Words. O exemplo completo demonstra uma abordagem limpa e sustentável que você pode estender para diagramas, gráficos ou gráficos personalizados mais complexos.

Em seguida, você pode explorar:

- Adicionar texto dentro das formas (`Shape.TextPath.Text = "Hello"`).
- Inserir imagens em um `GroupShape`.
- Exportar as formas agrupadas para PDF com `doc.Save("output.pdf")`.

Sinta‑se à vontade para experimentar diferentes tamanhos, posições e tipos adicionais de formas para atender às necessidades do seu projeto. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Como criar forma retangular e agrupar formas no Word com Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)
- [Criar Forma de Grupo em Documento Word Usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Criar forma retangular no Word usando C# – Guia passo a passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}