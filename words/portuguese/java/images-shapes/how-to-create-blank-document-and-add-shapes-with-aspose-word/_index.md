---
category: general
date: 2026-09-30
description: Crie um documento em branco e insira uma forma retangular, elipse e agrupe
  várias formas em C# usando Aspose.Words. Aprenda como inserir formas e como criar
  um grupo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- insert rectangle shape
- group multiple shapes
- how to insert shapes
- how to create group
language: pt
lastmod: 2026-09-30
og_description: Crie um documento em branco em C# e aprenda como inserir formas e
  agrupar várias formas com Aspose.Words. Siga o tutorial passo a passo.
og_image_alt: Screenshot of a C# program that creates a blank document, inserts a
  rectangle and ellipse, and groups them together.
og_title: Crie um documento em branco e agrupe formas em C# – Guia Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Create blank document and insert rectangle shape, ellipse, and group
    multiple shapes in C# using Aspose.Words. Learn how to insert shapes and how to
    create group.
  headline: How to create blank document and add shapes with Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- document automation
- shapes
title: Como criar um documento em branco e adicionar formas com Aspose.Words em C#
url: /pt/java/images-shapes/how-to-create-blank-document-and-add-shapes-with-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar um documento em branco e adicionar formas com Aspose.Words em C#

Se você precisa **criar um documento em branco** e preenchê‑lo com gráficos, este guia mostra exatamente como fazer. Você verá como **inserir uma forma retangular**, adicionar outros objetos de desenho e, em seguida, **agrupar várias formas** para que elas se comportem como uma única unidade.

Trabalhar com formas é uma necessidade comum ao gerar contratos, certificados ou relatórios personalizados. Neste tutorial você aprenderá o fluxo de trabalho completo, desde a inicialização do documento até a gravação do arquivo final, usando a API Aspose.Words para .NET.

## Pré‑requisitos

Antes de começar, certifique‑se de que você tem:

* SDK .NET 6.0 (ou posterior) instalado  
* Uma licença válida do Aspose.Words para .NET (a versão de avaliação gratuita funciona para este exemplo)  
* Uma IDE como Visual Studio 2022 ou Visual Studio Code  

Nenhum pacote NuGet adicional é necessário além do `Aspose.Words`.

## Como criar um documento em branco e trabalhar com formas

A primeira etapa é instanciar um objeto `Document`. Esse objeto representa o arquivo Word em memória e fornece acesso ao `DocumentBuilder`, que é a ferramenta principal para inserir conteúdo.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Por que isso importa:** Um documento em branco oferece uma tela limpa. O `DocumentBuilder` mantém o ponto de inserção atual, de modo que cada forma que você adiciona é posicionada automaticamente na página apropriada.

## Inserir forma retangular e outras formas

Em seguida, adicionamos um retângulo e uma elipse. Ambas as chamadas utilizam o mesmo método `InsertShape`, que é a forma recomendada **de inserir formas** no Aspose.Words.

```csharp
        // Step 2: Insert a rectangle shape (100 × 50 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;   // optional styling
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Insert an ellipse shape (80 × 80 points)
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;
```

*O método `InsertShape` posiciona automaticamente a forma na localização atual do cursor.* Se precisar de posicionamento preciso, você pode ajustar `Shape.Left` e `Shape.Top` após a inserção.

## Agrupar várias formas em um único objeto

Agora combinamos o retângulo e a elipse em uma entidade lógica única. Agrupar é útil quando você deseja mover ou redimensionar várias formas juntas.

```csharp
        // Step 4: Create a group shape that will hold multiple shapes
        GroupShape groupShape = builder.InsertGroupShape();

        // Step 5: Add the rectangle and ellipse to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional: Apply a border to the whole group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;
```

**Como isso funciona:** `InsertGroupShape` cria um contêiner que se comporta como qualquer outra `Shape`. Ao chamar `AppendChild`, você move as formas existentes para dentro do contêiner, que atualiza automaticamente suas coordenadas relativas.

### Dica prática

Se mais tarde precisar **criar um grupo** programaticamente para mais de duas formas, basta repetir `AppendChild` para cada instância adicional de `Shape`. O grupo pode conter qualquer número de objetos de desenho, incluindo imagens, caixas de texto ou até mesmo outros grupos.

## Exemplo completo – como inserir formas e salvar o documento

Abaixo está o programa completo e executável que demonstra cada passo discutido até agora. Executar o código gera um arquivo `ShapesDemo.docx` contendo um retângulo, uma elipse e uma forma agrupada.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Insert rectangle shape
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // 3. Insert ellipse shape
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;

        // 4. Create a group shape
        GroupShape groupShape = builder.InsertGroupShape();

        // 5. Add shapes to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional styling for the group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;

        // 6. Save the document
        string outputPath = "ShapesDemo.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Saída esperada:** Ao abrir `ShapesDemo.docx` no Microsoft Word, você verá uma única página com um retângulo azul, uma elipse verde e uma borda cinza ao redor que representa o grupo. Mover o grupo desloca ambas as formas simultaneamente, confirmando que a operação **agrupar várias formas** foi bem‑sucedida.

## Perguntas comuns e tratamento de casos extremos

| Pergunta | Resposta |
|----------|----------|
| *E se eu precisar das formas em uma página específica?* | Chame `builder.MoveToDocumentEnd();` antes de inserir as formas, ou use `builder.MoveToSection(sectionIndex);` para direcionar uma seção específica. |
| *Posso adicionar texto dentro de uma forma agrupada?* | Sim. Crie uma `Shape` do tipo `ShapeType.TextBox`, configure seu texto e então `AppendChild` ao `GroupShape`. |
| *As dimensões das formas usam pontos ou pixels?* | Aspose.Words usa **pontos** (1 pt = 1/72 polegada). Isso garante dimensionamento consistente em impressoras e telas. |
| *Como alterar a rotação do grupo?* | Defina `groupShape.RotationAngle = 45;` (graus). Todas as formas filhas giram em torno da origem do grupo. |

## Conclusão

Agora você sabe como **criar um documento em branco**, **inserir forma retangular**, **como inserir formas** como elipses e **agrupar várias formas** em um único objeto usando Aspose.Words para .NET. O exemplo de código completo demonstra a abordagem recomendada, e as dicas acima ajudam a adaptar a solução a cenários mais complexos, como adicionar caixas de texto ou girar grupos.

Pronto para explorar mais? Experimente adicionar uma forma de imagem ao grupo, teste diferentes cores de preenchimento ou gere um relatório de várias páginas onde cada página contém seu próprio diagrama agrupado. Os mesmos princípios se aplicam, permitindo escalar esse padrão para qualquer projeto de automação de documentos.

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código totalmente funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}