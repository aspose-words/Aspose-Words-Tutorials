---
category: general
date: 2026-09-21
description: Aprenda a agrupar formas no Word usando Aspose.Words para C#. Este guia
  passo a passo aborda a criação, o posicionamento e a gravação de formas agrupadas.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in Word
- Aspose.Words shape grouping
- C# Word shape manipulation
- DocumentBuilder insert shape
- GroupShape container
language: pt
lastmod: 2026-09-21
og_description: Agrupe formas no Word usando Aspose.Words para C#. Siga este tutorial
  conciso para criar, posicionar e salvar formas agrupadas programaticamente.
og_image_alt: Screenshot of grouped shapes in Word document created with Aspose.Words
og_title: Agrupar formas no Word com Aspose.Words – guia completo em C#
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  headline: How to group shapes in Word with Aspose.Words for C#
  type: TechArticle
- description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  name: How to group shapes in Word with Aspose.Words for C#
  steps:
  - name: Create a blank document and a `DocumentBuilder`
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert the first rectangle shape
    text: '```csharp // Insert a rectangle that is 100 points wide and 50 points tall.
      Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50); ```'
  - name: Insert the second rectangle and offset it
    text: '```csharp // Insert the second rectangle with the same dimensions. Shape
      shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);'
  - name: Create a `GroupShape` large enough for both rectangles
    text: '```csharp // The group must be wide enough to contain both shapes (100
      pt + 120 pt + 100 pt = 320 pt). // We give a little extra margin, so the group
      width is set to 300 pt and height to 100 pt. GroupShape group = new GroupShape(doc,
      300, 100); ```'
  - name: Append the individual shapes to the group
    text: '```csharp group.AppendChild(shape1); group.AppendChild(shape2); ```'
  - name: Insert the grouped shape back into the document
    text: '```csharp // Insert the GroupShape at the current builder position. builder.InsertNode(group);
      ```'
  - name: Save the document
    text: '```csharp // Replace YOUR_DIRECTORY with an absolute or relative path where
      you have write permission. doc.Save("YOUR_DIRECTORY/GroupedShapes.docx"); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Como agrupar formas no Word com Aspose.Words para C#
url: /pt/net/programming-with-shapes/how-to-group-shapes-in-word-with-aspose-words-for-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como agrupar formas no Word com Aspose.Words para C#

Se você precisa **agrupar formas no Word** programaticamente, o Aspose.Words torna isso simples. Este tutorial mostra como criar duas formas retangulares, posicioná‑las lado a lado, combiná‑las em um `GroupShape` e salvar o resultado como um arquivo DOCX.

Você verá um exemplo completo e executável, explicações sobre a importância de cada etapa e dicas para lidar com casos comuns, como formas sobrepostas ou dimensionamento dinâmico. Ao final deste guia, você poderá integrar o agrupamento de formas em qualquer projeto de automação do Word.

## Pré‑requisitos

Antes de começar, certifique‑se de que você tem:

* .NET 6.0 (ou superior) instalado – o Aspose.Words oferece suporte a .NET Standard 2.0+, .NET Core e .NET Framework.  
* Uma licença válida do Aspose.Words for .NET (ou uma chave de avaliação temporária) – a biblioteca funciona sem licença, mas adiciona uma marca d’água.  
* Visual Studio 2022 (ou qualquer IDE C#) para compilar e executar o exemplo.

Nenhum pacote NuGet adicional é necessário além do `Aspose.Words`.

## Como agrupar formas no Word usando Aspose.Words

O núcleo da solução é um objeto **`GroupShape`** que atua como contêiner para as formas individuais. A seguir, dividimos o processo em etapas claras.

### Etapa 1: Criar um documento em branco e um `DocumentBuilder`

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty Word document.
Document doc = new Document();

// DocumentBuilder provides convenient methods for inserting content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Por que esta etapa?*  
`Document` representa todo o arquivo DOCX, enquanto `DocumentBuilder` fornece métodos fluentes (por exemplo, `InsertShape`) que inserem automaticamente novos elementos na posição atual do cursor.

### Etapa 2: Inserir a primeira forma retangular

```csharp
// Insert a rectangle that is 100 points wide and 50 points tall.
Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

A chamada `InsertShape` adiciona a forma ao documento e devolve um objeto `Shape` que pode ser configurado (cor, borda etc.). O tamanho é expresso em pontos (1 pt ≈ 1/72 pol).

### Etapa 3: Inserir o segundo retângulo e deslocá‑lo

```csharp
// Insert the second rectangle with the same dimensions.
Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// Move the second shape 120 points to the right so the two rectangles do not overlap.
shape2.Left = 120; // Horizontal offset from the left edge of the page.
```

Definir `Left` posiciona a forma em relação à margem da página. O deslocamento deve ser maior que a largura da primeira forma (100 pt) para evitar sobreposição; usamos 120 pt para deixar um pequeno espaço.

### Etapa 4: Criar um `GroupShape` grande o suficiente para ambos os retângulos

```csharp
// The group must be wide enough to contain both shapes (100 pt + 120 pt + 100 pt = 320 pt).
// We give a little extra margin, so the group width is set to 300 pt and height to 100 pt.
GroupShape group = new GroupShape(doc, 300, 100);
```

`GroupShape` recebe o `Document` proprietário e as dimensões do contêiner. A largura do contêiner deve exceder a borda direita da forma mais distante; caso contrário, a segunda forma seria recortada.

### Etapa 5: Anexar as formas individuais ao grupo

```csharp
group.AppendChild(shape1);
group.AppendChild(shape2);
```

Anexar move as formas para a coleção interna do grupo. Após esta chamada, as formas não são mais objetos independentes na árvore do documento – elas pertencem ao grupo.

### Etapa 6: Inserir a forma agrupada de volta no documento

```csharp
// Insert the GroupShape at the current builder position.
builder.InsertNode(group);
```

`InsertNode` coloca todo o `GroupShape` onde o cursor está no momento. Se precisar do grupo em um parágrafo específico, mova o builder para esse parágrafo primeiro.

### Etapa 7: Salvar o documento

```csharp
// Replace YOUR_DIRECTORY with an absolute or relative path where you have write permission.
doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
```

O arquivo resultante contém dois retângulos que se comportam como um único objeto – você pode mover, redimensionar ou excluir ambos juntos no Microsoft Word.

## Código‑fonte completo

Juntando todas as etapas, obtém‑se um programa autônomo:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first rectangle (100 pt × 50 pt).
        Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // 3️⃣ Insert the second rectangle and offset it horizontally.
        Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        shape2.Left = 120; // Prevent overlap.

        // 4️⃣ Create a GroupShape container large enough for both.
        GroupShape group = new GroupShape(doc, 300, 100);

        // 5️⃣ Add both rectangles to the group.
        group.AppendChild(shape1);
        group.AppendChild(shape2);

        // 6️⃣ Insert the grouped shape back into the document.
        builder.InsertNode(group);

        // 7️⃣ Save the document.
        doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
    }
}
```

**Saída esperada:** Ao abrir *GroupedShapes.docx* no Microsoft Word, você verá dois retângulos lado a lado, tratados como um único objeto selecionável. Arrastar o grupo move ambos os retângulos simultaneamente.

## Variações comuns e casos de borda

| Situação | Ajuste recomendado |
|-----------|------------------------|
| **Mais de duas formas** | Crie objetos `Shape` adicionais, posicione‑os adequadamente e anexe cada um ao mesmo `GroupShape`. |
| **Tamanho dinâmico** | Calcule a largura/altura do grupo com base nos valores máximos de `Right` e `Bottom` das formas filhas. |
| **Tipos de forma diferentes** | `ShapeType.Ellipse`, `ShapeType.Triangle`, etc., podem ser inseridos da mesma forma; o contêiner do grupo não se importa com o tipo. |
| **Formas rotacionadas** | Defina `shape.Rotation = 45;` antes de anexar; a rotação é preservada dentro do grupo. |
| **Salvar como PDF** | Chame `doc.Save("GroupedShapes.pdf");` – o grupo é mantido na renderização PDF. |

**Dica profissional:** Após agrupar, ainda é possível modificar formas individuais acessando `group.GetChildNodes(NodeType.Shape, true)`. Isso é útil quando você precisa mudar a cor de preenchimento de um retângulo sem quebrar o grupo.

## Como verificar o agrupamento programaticamente

Se precisar confirmar que as formas foram agrupadas corretamente (por exemplo, em testes unitários), examine a hierarquia de nós do documento:

```csharp
NodeCollection groups = doc.GetChildNodes(NodeType.GroupShape, true);
Console.WriteLine($"Number of groups: {groups.Count}");
Console.WriteLine($"Children in first group: {groups[0].GetChildNodes(NodeType.Shape, true).Count}");
```

A saída deve ser:

```
Number of groups: 1
Children in first group: 2
```

Isso confirma que **agrupamento de formas no Word** foi criado conforme o esperado.

## Conclusão

Agora você sabe como **agrupar formas no Word** com Aspose.Words para C#. O processo envolve criar formas individuais, posicioná‑las, encapsulá‑las em um `GroupShape` e inserir o grupo de volta no documento. Com o exemplo completo acima, você pode estender a técnica para qualquer número de formas, tipos diferentes ou até combinar com caixas de texto e imagens.

Em seguida, explore tópicos relacionados como **agrupamento de formas no Aspose.Words**, **manipulação de formas Word em C#** e **DocumentBuilder insert shape** para cenários mais avançados de automação de documentos. Experimente dimensionamento dinâmico, agrupamento condicional e exportação para PDF para aproveitar ao máximo o poder do Aspose.Words.

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas em seus próprios projetos.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}