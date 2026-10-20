---
category: general
date: 2026-08-07
description: Como agrupar formas no Word com Aspose.Words e adicionar formas ao documento
  Word usando C#. Siga este guia passo a passo para obter código limpo e reutilizável.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes in word
- add shapes to word document
language: pt
lastmod: 2026-08-07
og_description: Como agrupar formas no Word usando Aspose.Words para .NET. Este tutorial
  mostra como adicionar formas a um documento Word, agrupá‑las e salvar o arquivo
  com código C# claro.
og_image_alt: Screenshot of a rectangle and ellipse grouped in a Word document created
  with Aspose.Words
og_title: Como agrupar formas no Word – guia rápido de C#
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to group shapes in Word with Aspose.Words and add shapes to Word
    document using C#. Follow this step‑by‑step guide for clean, reusable code.
  headline: How to group shapes in Word and add shapes to Word document
  type: TechArticle
- description: How to group shapes in Word with Aspose.Words and add shapes to Word
    document using C#. Follow this step‑by‑step guide for clean, reusable code.
  name: How to group shapes in Word and add shapes to Word document
  steps:
  - name: Create a document and a builder
    text: A `Document` object represents the entire DOCX file. `DocumentBuilder` provides
      a convenient API for editing the document.
  - name: Add the rectangle shape
    text: A rectangle is created by specifying `ShapeType.Rectangle`. Width, height,
      and location are set in points (1 pt ≈ 1/72 in).
  - name: Add the ellipse shape
    text: The ellipse uses `ShapeType.Ellipse`. Its size and position are independent
      of the rectangle, which allows you to control the final layout of the group.
  - name: Group the two shapes
    text: '`GroupShape` acts as a container that treats its children as a single object.
      This is the essential operation for **how to group shapes in Word**.'
  - name: Insert the grouped shape into the document
    text: '`DocumentBuilder.InsertNode` places the `GroupShape` at the current cursor
      location. Because we have not moved the builder, the group appears at the start
      of the first page.'
  - name: Save the document
    text: Finally, write the DOCX file to disk. Use a full path that your application
      can write to.
  - name: Expected output
    text: Open `GroupShape.docx`. You will see a single visual object that contains
      a blue rectangle on the left and a green ellipse on the right. Selecting the
      object in Word highlights both shapes simultaneously—proof that **how to group
      shapes in Word** succeeded.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Como agrupar formas no Word e adicionar formas ao documento do Word
url: /pt/net/programming-with-shapes/how-to-group-shapes-in-word-and-add-shapes-to-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como agrupar formas no Word e adicionar formas ao documento Word

Se você precisa de **how to group shapes in Word**, este guia o conduz por todo o processo usando Aspose.Words for .NET. Você também aprenderá **add shapes to Word document** com algumas linhas de código C#, de modo que o resultado esteja pronto para qualquer cenário de relatórios ou modelagem.

O tutorial cobre tudo o que você precisa: pacotes NuGet necessários, um arquivo de código completo e uma explicação do porquê cada etapa é importante. Ao final, você poderá gerar um DOCX que contém um retângulo e uma elipse combinados em uma única forma de grupo.

## Pré-requisitos

* .NET 6.0 SDK ou posterior instalado  
* Visual Studio 2022 (ou qualquer IDE que suporte .NET)  
* Pacote NuGet Aspose.Words for .NET (`Aspose.Words`) – o teste gratuito funciona para testes, mas uma licença remove as marcas d'água de avaliação  

Estes itens são as únicas dependências externas para **add shapes to Word document**.

## Como agrupar formas no Word

O núcleo da solução consiste em criar formas individuais, posicioná‑las na página e, em seguida, agrupá‑las em um `GroupShape`. As etapas a seguir refletem a ordem lógica do código.

### Etapa 1: Criar um documento e um builder

Um objeto `Document` representa o arquivo DOCX completo. `DocumentBuilder` fornece uma API conveniente para editar o documento.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create an empty Word document
Document doc = new Document();

// DocumentBuilder lets you insert nodes, text, and shapes
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Por que isso importa*: O `Document` é o contêiner para todos os elementos do Word. O `DocumentBuilder` mantém o controle da posição atual do cursor, o que é necessário quando você inserir a forma agrupada posteriormente.

### Etapa 2: Adicionar a forma retângulo

Um retângulo é criado especificando `ShapeType.Rectangle`. Largura, altura e localização são definidas em pontos (1 pt ≈ 1/72 in).

```csharp
Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
rectangleShape.Width = 100;               // 100 pt wide
rectangleShape.Height = 50;               // 50 pt tall
rectangleShape.Left = 0;                  // X‑coordinate
rectangleShape.Top = 0;                   // Y‑coordinate
rectangleShape.StrokeColor = Color.Blue; // Outline color
```

*Por que isso importa*: Definir `StrokeColor` torna a forma visível quando o documento é aberto. Você também pode preencher a forma com `FillColor` se for necessário um interior sólido.

### Etapa 3: Adicionar a forma elipse

A elipse usa `ShapeType.Ellipse`. Seu tamanho e posição são independentes do retângulo, o que permite controlar o layout final do grupo.

```csharp
Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
ellipseShape.Width = 80;
ellipseShape.Height = 80;
ellipseShape.Left = 120;                  // Placed to the right of the rectangle
ellipseShape.Top = 0;
ellipseShape.StrokeColor = Color.Green;
```

*Por que isso importa*: Ao posicionar a elipse em `Left = 120`, ela não se sobrepõe ao retângulo, tornando o grupo visualmente distinto.

### Etapa 4: Agrupar as duas formas

`GroupShape` atua como um contêiner que trata seus filhos como um único objeto. Esta é a operação essencial para **how to group shapes in Word**.

```csharp
GroupShape groupShape = new GroupShape(doc);
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);
```

*Por que isso importa*: Agrupar permite mover, redimensionar ou girar ambas as formas juntas. Qualquer transformação aplicada ao `groupShape` se propaga para seus filhos.

### Etapa 5: Inserir a forma agrupada no documento

`DocumentBuilder.InsertNode` coloca o `GroupShape` na posição atual do cursor. Como não movemos o builder, o grupo aparece no início da primeira página.

```csharp
builder.InsertNode(groupShape);
```

*Por que isso importa*: Inserir o nó diretamente evita a necessidade de um parágrafo ou célula de tabela separados. O grupo torna‑se parte do fluxo do documento.

### Etapa 6: Salvar o documento

Finalmente, grave o arquivo DOCX no disco. Use um caminho completo ao qual sua aplicação tenha permissão de gravação.

```csharp
doc.Save(@"C:\Temp\GroupShape.docx");
```

*Por que isso importa*: `doc.Save` finaliza todas as alterações. O arquivo resultante pode ser aberto no Microsoft Word, LibreOffice ou qualquer visualizador que suporte DOCX.

## Arquivo de código completo

Copie o código abaixo para um novo projeto de console (`dotnet new console`) e execute‑o. O programa cria um arquivo chamado `GroupShape.docx` contendo um retângulo e uma elipse agrupados.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordShapeGrouping
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new document and a builder to edit it
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Define a rectangle shape
            Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
            rectangleShape.Width = 100;
            rectangleShape.Height = 50;
            rectangleShape.Left = 0;
            rectangleShape.Top = 0;
            rectangleShape.StrokeColor = Color.Blue;

            // Step 3: Define an ellipse shape
            Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
            ellipseShape.Width = 80;
            ellipseShape.Height = 80;
            ellipseShape.Left = 120;
            ellipseShape.Top = 0;
            ellipseShape.StrokeColor = Color.Green;

            // Step 4: Group the two shapes together
            GroupShape groupShape = new GroupShape(doc);
            groupShape.AppendChild(rectangleShape);
            groupShape.AppendChild(ellipseShape);

            // Step 5: Insert the grouped shape into the document
            builder.InsertNode(groupShape);

            // Step 6: Save the document
            doc.Save(@"C:\Temp\GroupShape.docx");
        }
    }
}
```

### Saída esperada

Abra `GroupShape.docx`. Você verá um único objeto visual que contém um retângulo azul à esquerda e uma elipse verde à direita. Selecionar o objeto no Word destaca ambas as formas simultaneamente — prova de que **how to group shapes in Word** foi bem‑sucedido.

## Perguntas comuns e casos de borda

* **Posso adicionar mais de duas formas?**  
  Sim. Chame `groupShape.AppendChild` para cada `Shape` adicional antes de inserir o grupo.

* **E se eu precisar girar o grupo?**  
  Defina `groupShape.RotationAngle = 45;` (ângulo em graus) após o grupo ser construído.

* **Preciso chamar `doc.UpdatePageLayout()`?**  
  Não para este cenário. O layout é atualizado automaticamente quando o documento é salvo.

* **Como a licença afeta o código?**  
  Com uma licença válida do Aspose.Words (`License license = new License(); license.SetLicense("Aspose.Words.lic");`) o documento gerado não contém marca d'água de avaliação.

## Conclusão

Agora você sabe **how to group shapes in Word** e **add shapes to Word document** usando Aspose.Words for .NET. O tutorial abordou a criação de um documento, a definição de formas individuais, o agrupamento delas, a inserção do grupo e a gravação do arquivo.  

A partir daqui você pode experimentar com:

* Adicionar caixas de texto ou imagens ao grupo  
* Alterar cores de preenchimento, estilos de linha ou efeitos de sombra  
* Agrupar formas dentro de tabelas ou cabeçalhos  

Essas extensões permitem construir modelos Word sofisticados programaticamente, mantendo o código limpo e sustentável. Boa codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Criar forma de grupo em documento Word usando Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Inserir formas em documentos Word usando Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Criar documento Word com Aspose.Words – Guia passo a passo](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}