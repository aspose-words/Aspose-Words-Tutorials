---
category: general
date: 2026-07-19
description: Agrupar formas no Word usando Aspose.Words. Aprenda como adicionar forma
  retangular, definir forma elíptica e inserir forma em documentos do Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- how to group shapes
- insert shape into word
- define ellipse shape
language: pt
lastmod: 2026-07-19
og_description: Agrupe formas no Word com Aspose.Words. Domine a adição de forma retangular,
  a definição de forma elíptica e a inserção de formas em documentos do Word.
og_image_alt: Screenshot of grouped shapes in a Word document created with Aspose.Words
og_title: Agrupar formas no Word – Tutorial passo a passo em C#
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Group shapes in Word using Aspose.Words. Learn how to add rectangle
    shape, define ellipse shape, and insert shape into Word documents.
  headline: Group Shapes in Word with Aspose.Words – Complete C# Guide
  type: TechArticle
- description: Group shapes in Word using Aspose.Words. Learn how to add rectangle
    shape, define ellipse shape, and insert shape into Word documents.
  name: Group Shapes in Word with Aspose.Words – Complete C# Guide
  steps:
  - name: Set Up the Document and Builder
    text: We start by creating an empty `Document` and a `DocumentBuilder`. The builder
      is our “pen” that lets us insert content wherever we need it.
  - name: Add Rectangle Shape (add rectangle shape)
    text: Now we **add rectangle shape** to the document. We set its size, position,
      and fill colour to make it stand out.
  - name: Define Ellipse Shape (define ellipse shape)
    text: Next, we **define ellipse shape**. Notice the different `ShapeType` and
      the offset (`Left = 120`) so the ellipse sits beside the rectangle.
  - name: (Optional) Insert Individual Shapes for Preview
    text: If you want to see each shape before grouping, you can **insert shape into
      Word** individually. This step is optional but handy for debugging.
  - name: How to Group Shapes – Create a GroupShape
    text: 'Here’s the core of the tutorial: **how to group shapes**. We create a `GroupShape`,
      attach our rectangle and ellipse, and decide how the group behaves with surrounding
      text.'
  - name: Insert the Grouped Shape into the Document (insert shape into word)
    text: Now we **insert shape into Word**—but this time it’s the grouped container,
      not the individual pieces.
  - name: Save the Document
    text: Finally, write the file to disk. You can change the path to suit your project
      layout.
  - name: What if I need more than two shapes?
    text: Just keep calling `groupShape.AppendChild(yourNewShape);` before inserting
      the group. The API imposes no limit on the number of child shapes.
  - name: Can I rotate or resize the whole group?
    text: Absolutely. `GroupShape` inherits from `Shape`, so you can set properties
      like `RotationAngle`, `Width`, or `Height` on the group itself, and all child
      shapes will follow.
  - name: How do I change the group’s background colour?
    text: Use `groupShape.FillColor`. This fills the invisible bounding box; it can
      be handy for highlighting.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
title: Formas em Grupo no Word com Aspose.Words – Guia Completo em C#
url: /pt/net/programming-with-shapes/group-shapes-in-word-with-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Agrupar Formas no Word – Guia Completo em C#

Já se perguntou como **agrupar formas no Word** sem ficar mexendo na interface? Você não está sozinho. Seja gerando contratos, flyers ou diagramas programaticamente, poder **adicionar forma retangular**, **definir forma elíptica** e então **agrupar formas no Word** pode economizar horas de trabalho manual.

Neste tutorial vamos percorrer um exemplo real usando **Aspose.Words for .NET**. Ao final, você saberá exatamente como **inserir forma no Word**, combiná‑las e produzir um documento polido que pode ser enviado a clientes ou colegas de equipe.

---

## O Que Você Precisa

Antes de mergulharmos, certifique‑se de que tem o seguinte:

- **Aspose.Words for .NET** (última versão, por exemplo, 24.9). Você pode obtê‑lo via NuGet com `Install-Package Aspose.Words`.
- Um ambiente de desenvolvimento .NET (Visual Studio 2022 ou VS Code com a extensão C# funciona bem).
- Familiaridade básica com a sintaxe C# — nada sofisticado, apenas as declarações `using` habituais e a criação de objetos.

É só isso. Nenhuma biblioteca extra, sem interop COM, apenas código gerenciado puro.

---

## Como Agrupar Formas no Word Usando Aspose.Words

A seguir, um passo‑a‑passo que espelha o código que você já tem. Cada etapa explica **por que** a fazemos, não apenas **o que** a linha faz, para que você possa adaptar o padrão a qualquer forma que desejar.

### Etapa 1: Configurar o Documento e o Builder

Começamos criando um `Document` vazio e um `DocumentBuilder`. O builder é a nossa “caneta” que permite inserir conteúdo onde for necessário.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();
// The builder will help us place shapes and text
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Por quê?** O objeto `Document` representa todo o arquivo .docx, enquanto o `DocumentBuilder` fornece uma API conveniente para inserir nós (como formas) sem precisar lidar diretamente com a árvore de nós subjacente.

### Etapa 2: Adicionar Forma Retangular (add rectangle shape)

Agora **adicionamos uma forma retangular** ao documento. Definimos seu tamanho, posição e cor de preenchimento para que se destaque.

```csharp
// Create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 100;                     // Width in points
rectangleShape.Height = 50;                      // Height in points
rectangleShape.Left   = 0;                       // X‑coordinate
rectangleShape.Top    = 0;                       // Y‑coordinate
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
```

> **Dica:** Você pode mudar `FillColor` para qualquer `System.Drawing.Color` que preferir. Isso é útil quando precisar de seções codificadas por cores em um relatório.

### Etapa 3: Definir Forma Elíptica (define ellipse shape)

Em seguida, **definimos a forma elíptica**. Observe o `ShapeType` diferente e o deslocamento (`Left = 120`) para que a elipse fique ao lado do retângulo.

```csharp
// Create an ellipse shape
Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
ellipseShape.Width  = 80;
ellipseShape.Height = 40;
ellipseShape.Left   = 120;   // Position it to the right of the rectangle
ellipseShape.Top    = 0;
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```

> **Por que isso importa:** Posicionando as formas explicitamente, você controla como elas aparecem antes de agrupá‑las. Se confiar no layout automático, o agrupamento pode ficar desalinhado.

### Etapa 4: (Opcional) Inserir Formas Individuais para Pré‑visualização

Se quiser ver cada forma antes de agrupar, pode **inserir forma no Word** individualmente. Esta etapa é opcional, mas prática para depuração.

```csharp
// Insert the rectangle and ellipse separately (useful for preview)
builder.InsertNode(rectangleShape);
builder.InsertNode(ellipseShape);
```

> **Pro dica:** Comente estas duas linhas assim que estiver confiante de que as formas estão corretas; caso contrário, você acabará com visuais duplicados após o agrupamento.

### Etapa 5: Como Agrupar Formas – Criar um GroupShape

Aqui está o núcleo do tutorial: **como agrupar formas**. Criamos um `GroupShape`, anexamos nosso retângulo e elipse, e definimos como o grupo se comporta em relação ao texto ao redor.

```csharp
// Create a container for the group
GroupShape groupShape = new GroupShape(document);

// Add the rectangle and ellipse to the group
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);

// Set wrapping – Inline makes the group act like a character in the text flow
groupShape.WrapType = WrapType.Inline;
```

> **Explicação:** `GroupShape` é essencialmente uma mini‑tela que contém outras formas. Ao definir `WrapType` como `Inline`, todo o grupo se move como uma única unidade quando você adiciona ou remove texto.

### Etapa 6: Inserir a Forma Agrupada no Documento (insert shape into word)

Agora **inserimos a forma no Word** — mas desta vez é o contêiner agrupado, não as peças individuais.

```csharp
// Insert the grouped shape at the current cursor position
builder.InsertNode(groupShape);
```

> **O que acontece nos bastidores?** A chamada `InsertNode` adiciona o `GroupShape` à coleção de nós do documento. Como o grupo já contém o retângulo e a elipse, eles aparecem juntos como um único objeto.

### Etapa 7: Salvar o Documento

Por fim, gravamos o arquivo no disco. Você pode mudar o caminho para se adequar à estrutura do seu projeto.

```csharp
// Save the resulting .docx file
document.Save("YOUR_DIRECTORY/GroupShape.docx");
```

> **Resultado:** Abra `GroupShape.docx` no Microsoft Word e você verá um retângulo azul‑claro e uma elipse coral bloqueados juntos. Arrastar um move o outro — exatamente o que “agrupar formas no Word” promete.

---

## Confirmação Visual

Abaixo está uma simulação de como as formas agrupadas ficam dentro do arquivo Word.  

![Captura de tela das formas agrupadas em um documento Word criado com Aspose.Words](grouped_shapes_placeholder.png "agrupar formas no word")

*O texto alternativo da imagem contém a palavra‑chave principal para acessibilidade e SEO.*

---

## Perguntas Frequentes & Casos Limite

### E se eu precisar de mais de duas formas?

Basta continuar chamando `groupShape.AppendChild(suaNovaForma);` antes de inserir o grupo. A API não impõe limite ao número de formas filhas.

### Posso girar ou redimensionar todo o grupo?

Com certeza. `GroupShape` herda de `Shape`, então você pode definir propriedades como `RotationAngle`, `Width` ou `Height` no próprio grupo, e todas as formas filhas seguirão.

```csharp
groupShape.RotationAngle = 15;   // Rotate the entire group 15 degrees
groupShape.Width = 250;          // Stretch the group uniformly
```

### Como mudar a cor de fundo do grupo?

Use `groupShape.FillColor`. Isso preenche a caixa delimitadora invisível; pode ser útil para realçar.

```csharp
groupShape.FillColor = System.Drawing.Color.LightGray;
```

### Isso funciona com formatos Word mais antigos (.doc)?

`Aspose.Words` também pode salvar em `.doc` — basta substituir a extensão do arquivo em `Save`. Contudo, alguns recursos avançados de forma (como agrupamento) são totalmente suportados apenas no formato OOXML `.docx`.

---

## Exemplo Completo Funcional

Copie‑e‑cole o bloco a seguir em um novo aplicativo console para ver todo o processo em ação. Nenhum trecho está faltando; este é um **exemplo completo e executável**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing; // For Color

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Add rectangle shape
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width  = 100;
        rectangleShape.Height = 50;
        rectangleShape.Left   = 0;
        rectangleShape.Top    = 0;
        rectangleShape.FillColor = Color.LightBlue;

        // 3️⃣ Define ellipse shape
        Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
        ellipseShape.Width  = 80;
        ellipseShape.Height = 40;
        ellipseShape.Left   = 120;
        ellipseShape.Top    = 0;
        ellipseShape.FillColor = Color.LightCoral;

        // 4️⃣ (Optional) Preview individual shapes
        // builder.InsertNode(rectangleShape);
        // builder.InsertNode(ellipseShape);

        // 5️⃣ Group the shapes together
        GroupShape groupShape = new GroupShape(document);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        groupShape.WrapType = WrapType.Inline;

        // 6️⃣ Insert the grouped shape into the document
        builder.InsertNode(groupShape);

        // 7️⃣ Save the file
        document.Save("GroupShape.docx");

        System.Console.WriteLine("Document created successfully!");
    }
}
```

**Saída esperada:** Ao abrir `GroupShape.docx`, você verá um único objeto agrupado composto por um retângulo azul‑claro e uma elipse coral‑clara, perfeitamente alinhados lado a lado.

---

## Recapitulação

Acabamos de cobrir tudo o que você precisa para **agrupar formas no Word** com Aspose.Words:

1. Crie um documento e um builder.  
2. **Adicione forma retangular** e **defina forma elíptica** com dimensões explícitas.  
3. (Opcional) **insira forma no Word** para uma pré‑visualização rápida.  
4. Use `GroupShape` para **como agrupar formas** — anexe cada filho, defina o contorno e insira.  
5. Salve o arquivo e verifique o

## O Que Você Deve Aprender a Seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas em seus próprios projetos.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}