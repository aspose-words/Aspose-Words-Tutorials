---
category: general
date: 2026-09-08
description: Aprenda a criar um documento Word em branco, inserir uma forma retangular
  e agrupar várias formas usando C#. Siga este guia passo a passo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert rectangle shape
- group multiple shapes
- add shapes to group
language: pt
lastmod: 2026-09-08
og_description: Crie um documento Word em branco, insira uma forma retangular e agrupe
  várias formas em C#. Este tutorial orienta você por todo o processo.
og_image_alt: Screenshot showing a blank Word document with a grouped rectangle and
  ellipse shape
og_title: Criar documento Word em branco com formas agrupadas em C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to create blank Word document, insert rectangle shape and
    group multiple shapes using C#. Follow this step‑by‑step guide.
  headline: How to create blank Word document with grouped shapes
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Como criar um documento Word em branco com formas agrupadas
url: /pt/java/images-shapes/how-to-create-blank-word-document-with-grouped-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar documento Word em branco com formas agrupadas

Se você precisa **criar um documento Word em branco** que contenha gráficos personalizados, este guia mostra exatamente como fazer. Você aprenderá a **inserir forma retangular**, **agrupar múltiplas formas** e **adicionar formas ao grupo** usando Aspose.Words for .NET.

Um documento em branco fornece uma tela limpa, e agrupar formas permite mover, redimensionar ou girar como uma única unidade. Este tutorial cobre cada passo — desde a inicialização do documento até a gravação do arquivo final — para que você possa copiar o código para seu próprio projeto e ver resultados imediatos.

## O que você precisará

* .NET 6.0 ou posterior (o código também funciona com .NET Framework 4.6+)
* Uma licença válida do Aspose.Words for .NET (a avaliação gratuita funciona para testes)
* Uma IDE como Visual Studio 2022 ou Visual Studio Code
* Familiaridade básica com a sintaxe C#

Nenhum pacote NuGet adicional é necessário além de `Aspose.Words`.

## Como criar documento Word em branco

O primeiro passo é instanciar um objeto `Document`. Este objeto representa um arquivo `.docx` vazio que você pode editar com um `DocumentBuilder`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document and a builder to edit it.
            Document doc = new Document();               // Blank Word document
            DocumentBuilder builder = new DocumentBuilder(doc);
```

O construtor `Document` cria um **documento Word em branco** na memória. O `DocumentBuilder` fornece uma API fluente para inserir texto, imagens e objetos de desenho.

## Inserir forma retangular no documento

Em seguida, adicione uma forma retangular. O retângulo será o primeiro filho do grupo que criaremos mais tarde.

```csharp
            // Step 2: Insert a rectangle shape (100 pt wide, 50 pt high).
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            // Optional: give the rectangle a fill color for visibility.
            rectangle.FillColor = System.Drawing.Color.LightBlue;
```

Chamar `InsertShape` com `ShapeType.Rectangle` **insere uma forma retangular** na posição atual do cursor. A largura e a altura são expressas em pontos (1 pt ≈ 1/72 in).

## Agrupar múltiplas formas juntas

Um `GroupShape` funciona como um contêiner. Todas as formas filhas dentro do grupo movem‑se e transformam‑se juntas. Primeiro, crie o grupo, depois adicione o retângulo que acabamos de criar.

```csharp
            // Step 3: Create a group shape that will hold multiple child shapes.
            GroupShape group = builder.InsertGroupShape();
            // Append the rectangle as the first child of the group.
            group.AppendChild(rectangle);
```

O método `InsertGroupShape` coloca um grupo vazio no cursor do builder. Ao anexar o retângulo, nós **agrupamos múltiplas formas** — o retângulo passa a fazer parte da coleção interna de nós do grupo.

## Adicionar formas ao grupo e salvar o arquivo

Agora adicione uma segunda forma — uma elipse — para demonstrar como múltiplos objetos compartilham o mesmo contêiner. Em seguida, salve o documento.

```csharp
            // Step 4: Insert an ellipse shape (80 pt wide, 80 pt high).
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;

            // Append the ellipse to the same group.
            group.AppendChild(ellipse);

            // Step 5: Save the document containing the grouped shapes.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

A chamada `InsertShape` **adiciona formas ao grupo** quando você anexa o `Shape` retornado ao `GroupShape`. Salvar o `Document` grava um arquivo `.docx` que pode ser aberto no Microsoft Word, LibreOffice ou qualquer visualizador compatível.

### Resultado esperado

Ao abrir *GroupShapeDemo.docx*, você verá uma página em branco com um objeto agrupado que contém um retângulo azul‑claro e uma elipse rosa. Selecionar o grupo permite mover ambas as formas juntas, confirmando que **agrupar múltiplas formas** funcionou como esperado.

## Por que usar um GroupShape?

* **Transformações atômicas** – Redimensionar, girar ou mover o grupo afeta todos os filhos uniformemente.
* **Organização lógica** – Mantém gráficos relacionados juntos, facilitando a manutenção da estrutura do documento.
* **Desempenho** – Renderizar um único contêiner costuma ser mais rápido do que lidar com muitas formas independentes.

Se precisar modificar um filho único mais tarde, você pode recuperá‑lo de `group.ChildNodes` por índice ou pela propriedade `Name`.

## Variações comuns e casos extremos

| Cenário                                 | Como adaptar o código                                                            |
|------------------------------------------|----------------------------------------------------------------------------------|
| **Tipos diferentes de forma**            | Substitua `ShapeType.Rectangle` ou `ShapeType.Ellipse` por qualquer outro `ShapeType` |
| **Adicionar texto dentro de uma forma** | Use `Shape.TextPath.Text = \"Hello\"` após inserir a forma                    |
| **Definir um ângulo de rotação**         | `group.Rotation = 45;` (graus)                                                 |
| **Salvar como PDF em vez de DOCX**      | `doc.Save("GroupShapeDemo.pdf");`                                                |
| **Aplicar borda ao grupo**               | `group.LineStyle = LineStyle.Single;`<br>`group.LineWidth = 1.5;`               |

## Dicas profissionais

* **Nomeie suas formas** – `rectangle.Name = "MyRect";` facilita localizá‑las mais tarde.
* **Use posicionamento relativo** – Defina `group.RelativeHorizontalPosition` para `RelativeHorizontalPosition.Page` se quiser que o grupo permaneça ancorado às margens da página.
* **Libere recursos** – Envolva o `Document` em um bloco `using` ao trabalhar em aplicações maiores para liberar a memória não gerenciada prontamente.

## Código-fonte completo para copiar‑colar rápido

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document and a builder to edit it.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a rectangle shape (100 pt × 50 pt) and give it a light‑blue fill.
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // Create a group shape and add the rectangle as its first child.
            GroupShape group = builder.InsertGroupShape();
            group.AppendChild(rectangle);

            // Insert an ellipse shape (80 pt × 80 pt) with a pink fill.
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;
            group.AppendChild(ellipse);

            // Save the document. The file will contain the grouped rectangle and ellipse.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Copie o código para um novo projeto de console, restaure o pacote NuGet `Aspose.Words` e execute. O arquivo de saída aparece na pasta `bin/Debug/net6.0` do projeto (ou equivalente).

## Próximos passos

Agora que você pode **criar documento Word em branco**, **inserir forma retangular** e **agrupar múltiplas formas**, você pode explorar:

* Adicionar **caixas de texto** dentro de um grupo para criar diagramas rotulados.
* Exportar o gráfico agrupado para uma imagem com `doc.Save("image.png", SaveFormat.Png)`.
* Combinar grupos com tabelas para relatórios ricamente formatados.

Experimente diferentes propriedades de forma, hierarquias de grupos e formatos de exportação para aproveitar ao máximo os recursos de desenho do Aspose.Words.

--- 

*Lembre‑se*: agrupar formas é uma maneira poderosa de manter seus documentos Word organizados e seu código sustentável. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Criar forma retangular no Word usando C# – Guia passo a passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Inserir formas em documentos Word usando Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Criar Group Shape em documento Word usando Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}