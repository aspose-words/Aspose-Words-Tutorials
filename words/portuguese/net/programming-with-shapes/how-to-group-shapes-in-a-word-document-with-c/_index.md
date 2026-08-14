---
category: general
date: 2026-08-14
description: Como agrupar formas em um documento Word usando C#. Aprenda a criar um
  documento Word, inserir uma forma retangular, agrupar formas no Word e salvar o
  documento como docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- create word document
- insert rectangle shape
- group shapes in word
- save document as docx
language: pt
lastmod: 2026-08-14
og_description: Como agrupar formas em um documento Word usando C#. Siga este tutorial
  completo para criar um arquivo Word, inserir uma forma retangular, agrupar formas
  no Word e salvar o resultado como docx.
og_image_alt: Screenshot showing how to group shapes in a Word document using C#
og_title: Como agrupar formas em um documento Word com C# – guia passo a passo
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to group shapes in a Word document using C#. Learn to create Word
    document, insert rectangle shape, group shapes in Word, and save document as docx.
  headline: How to group shapes in a Word document with C#
  type: TechArticle
- description: How to group shapes in a Word document using C#. Learn to create Word
    document, insert rectangle shape, group shapes in Word, and save document as docx.
  name: How to group shapes in a Word document with C#
  steps:
  - name: Create a new blank document
    text: The first thing you do when you want to **create Word document** programmatically
      is instantiate a `Document` object. This object represents the entire .docx
      file in memory.
  - name: Insert a rectangle shape
    text: To demonstrate **insert rectangle shape**, we use the `InsertShape` method.
      The rectangle will act as the first member of the group.
  - name: Insert an ellipse shape
    text: Next, we **insert ellipse shape** (the API calls it `Ellipse`). This will
      be the second member of the group.
  - name: Group the rectangle and ellipse
    text: Now we answer the central question **how to group shapes** in a Word document.
      Aspose.Words provides `AppendGroupShape` to create a group container, and then
      you call `Group()` on that container.
  - name: Save the document as a DOCX file
    text: The final step is to **save document as docx**. You can choose any path
      you like; the example uses a placeholder `"YOUR_DIRECTORY"` that you should
      replace with a real folder.
  - name: Expected output
    text: When you open `groupedShapes.docx` in Microsoft Word, you will see a light‑blue
      rectangle and a light‑coral ellipse locked together. Clicking either shape selects
      both, allowing you to move or resize them as a single unit.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Como agrupar formas em um documento do Word com C#
url: /pt/net/programming-with-shapes/how-to-group-shapes-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como agrupar formas em um documento Word com C#

Se você precisa **como agrupar formas** em um documento Word, este guia mostra os passos exatos usando C# e a biblioteca Aspose.Words. Você verá como criar um documento Word, inserir uma forma retangular, agrupar formas no Word e, finalmente, **salvar documento como docx** — tudo em um único programa executável.

Criar e manipular formas é uma necessidade comum ao gerar relatórios, contratos ou brochuras de marketing programaticamente. Ao final deste tutorial você terá um trecho de código reutilizável que pode ser inserido em qualquer projeto .NET.

## Pré-requisitos

Antes de começar, certifique‑se de que você tem:

- .NET 6.0 ou posterior instalado  
- Visual Studio 2022 (ou qualquer IDE que suporte .NET)  
- Uma licença do Aspose.Words para .NET (ou uma avaliação gratuita)  
- Familiaridade básica com a sintaxe C#  

Nenhum pacote NuGet adicional é necessário além de `Aspose.Words`.

## Como agrupar formas em um documento Word

O núcleo da solução é um processo de cinco etapas. Cada etapa é explicada em detalhes, e o código‑fonte completo é fornecido ao final do artigo.

### Etapa 1: Criar um novo documento em branco

A primeira coisa que você faz quando quer **criar documento Word** programaticamente é instanciar um objeto `Document`. Esse objeto representa todo o arquivo .docx na memória.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document doc = new Document();

// Obtain a DocumentBuilder to add content
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Por que isso importa:** `DocumentBuilder` é um auxiliar de alto nível que permite inserir texto, tabelas e formas sem precisar manipular manualmente a árvore de nós subjacente.

### Etapa 2: Inserir uma forma retangular

Para demonstrar **inserir forma retangular**, usamos o método `InsertShape`. O retângulo atuará como o primeiro membro do grupo.

```csharp
// Insert a rectangle (100x50 points) at the current cursor position
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// Optional: set a fill color so the shape is visible
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
```

**Por que isso importa:** As formas são posicionadas em relação ao ponto de inserção. Definir uma cor de preenchimento ajuda a visualizar a forma ao abrir o documento resultante.

### Etapa 3: Inserir uma forma elíptica

Em seguida, **inserimos forma elíptica** (a API a chama de `Ellipse`). Esta será o segundo membro do grupo.

```csharp
// Insert an ellipse (80x40 points) right after the rectangle
Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 40);
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```

**Por que isso importa:** Ao inserir a elipse imediatamente após o retângulo, ambas as formas ficam no mesmo parágrafo, o que simplifica o agrupamento posterior.

### Etapa 4: Agrupar o retângulo e a elipse

Agora respondemos à pergunta central **como agrupar formas** em um documento Word. Aspose.Words fornece `AppendGroupShape` para criar um contêiner de grupo e, em seguida, você chama `Group()` nesse contêiner.

```csharp
// Get the first paragraph of the document (where the shapes live)
Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;

// Create a group shape that contains the rectangle and ellipse
Shape groupedShape = firstParagraph.AppendGroupShape(new[] { rectangleShape, ellipseShape });

// Turn the container into a true group – the shapes will move and scale together
groupedShape.Group();
```

**Por que isso importa:** Uma vez agrupadas, qualquer transformação (mover, redimensionar, girar) aplicada a `groupedShape` afeta automaticamente tanto o retângulo quanto a elipse. Isso é essencial para manter a consistência do layout em documentos gerados.

### Etapa 5: Salvar o documento como arquivo DOCX

A etapa final é **salvar documento como docx**. Você pode escolher qualquer caminho; o exemplo usa o placeholder `"YOUR_DIRECTORY"` que deve ser substituído por uma pasta real.

```csharp
// Define the output path (ensure the directory exists)
string outputPath = @"C:\Temp\groupedShapes.docx";

// Save the document in DOCX format
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved successfully to {outputPath}");
```

**Por que isso importa:** Salvar como DOCX preserva os metadados de agrupamento, de modo que ao abrir o arquivo no Microsoft Word você verá o retângulo e a elipse atuando como um único objeto.

## Exemplo completo e executável

Abaixo está o programa completo que combina as cinco etapas. Copie-o para um novo projeto de console, restaure o pacote NuGet Aspose.Words e execute.

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
            // Step 1: Create a new blank document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Insert a rectangle shape (100x50 points)
            Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            rectangleShape.FillColor = System.Drawing.Color.LightBlue;

            // Step 3: Insert an ellipse shape (80x40 points)
            Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 40);
            ellipseShape.FillColor = System.Drawing.Color.LightCoral;

            // Step 4: Group the rectangle and ellipse
            Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
            Shape groupedShape = firstParagraph.AppendGroupShape(new[] { rectangleShape, ellipseShape });
            groupedShape.Group();

            // Step 5: Save the document as DOCX
            string outputPath = @"C:\Temp\groupedShapes.docx";
            doc.Save(outputPath, SaveFormat.Docx);

            Console.WriteLine($"Document saved successfully to {outputPath}");
        }
    }
}
```

### Saída esperada

Ao abrir `groupedShapes.docx` no Microsoft Word, você verá um retângulo azul‑claro e uma elipse coral‑clara bloqueados juntos. Clicar em qualquer uma das formas seleciona ambas, permitindo mover ou redimensioná‑las como uma única unidade.

## Perguntas comuns e casos de borda

| Pergunta | Resposta |
|----------|----------|
| **Posso agrupar mais de duas formas?** | Sim. Passe qualquer número de objetos `Shape` para `AppendGroupShape`. O método aceita um array, permitindo construir a coleção dinamicamente. |
| **E se eu precisar que o grupo esteja ancorado a uma célula de tabela?** | Insira as formas dentro do parágrafo da célula e, em seguida, chame `AppendGroupShape` nesse parágrafo. O grupo herda o ancoramento da célula. |
| **O agrupamento afeta o XML subjacente?** | Aspose.Words grava um elemento `<w:grpSp>` que contém as formas filhas. O Word reconhece isso como um grupo, preservando o posicionamento relativo. |
| **Como desagrupar mais tarde?** | Chame `groupedShape.Ungroup()`; o método devolve as formas individuais para que você possa manipulá‑las separadamente. |
| **Existe impacto de desempenho ao agrupar muitas formas?** | O próprio agrupamento é pouco custoso, mas renderizar grupos muito grandes (centenas de formas) pode aumentar o tamanho do arquivo. Considere achatar imagens se o tamanho se tornar um problema. |

## Dicas profissionais

- **Defina posições explícitas** (`Left`, `Top`) se precisar de alinhamento preciso antes de agrupar.  
- **Use `Shape.WrapType = WrapType.Inline`** quando quiser que o grupo se comporte como um elemento de parágrafo, em vez de um objeto flutuante.  
- **Aplique um estilo de linha** ao grupo (`groupedShape.LineFormat`) para dar à coleção inteira uma borda.  
- **Reutilize o grupo**: após chamar `Group()`, você pode clonar `groupedShape` e inserir o clone em outro local do documento.

## Próximos passos

Agora que você sabe **como agrupar formas** em um documento Word, pode explorar tópicos relacionados, como:

- **Inserir forma retangular** com texto ou imagens personalizadas dentro da forma.  
- **Criar diagramas complexos** aninhando grupos (grupo dentro de outro grupo).  
- **Exportar o documento como PDF** preservando o agrupamento de formas (`doc.Save("output.pdf", SaveFormat.Pdf)`).  

Cada um desses itens se baseia nos mesmos fundamentos abordados aqui, de modo que você está bem posicionado para expandir seu conjunto de ferramentas de automação Word.

## Conclusão

Este tutorial demonstrou **como agrupar formas** em um documento Word usando C#. Você aprendeu a **criar documento Word**, **inserir forma retangular**, **agrupar formas no Word** e, finalmente, **salvar documento como docx**. Com o exemplo completo e as dicas práticas fornecidas, você pode integrar o agrupamento de formas em qualquer fluxo de geração de documentos. Boa codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas em seus próprios projetos.

- [Criar forma de grupo em documento Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Inserir formas em documentos Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Criar forma retangular no Word usando C# – Guia passo a passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}