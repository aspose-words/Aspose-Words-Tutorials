---
category: general
date: 2026-10-04
description: Aprenda como agrupar formas no Word usando C#. Este guia mostra como
  inserir uma forma de retângulo, agrupar várias formas e criar um arquivo Word em
  branco programaticamente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- insert rectangle shape
- group multiple shapes
- append child to group
- create blank word file
language: pt
lastmod: 2026-10-04
og_description: Agrupe formas no Word usando C#. Siga este guia passo a passo para
  inserir uma forma retangular, agrupar várias formas e criar um arquivo Word em branco
  com DocumentBuilder.
og_image_alt: Screenshot of grouped rectangle and ellipse shapes inside a Word document
og_title: Agrupar formas no Word com C# – tutorial completo do DocumentBuilder
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to group shapes in Word using C#. This guide shows how to
    insert rectangle shape, group multiple shapes, and create a blank Word file programmatically.
  headline: How to group shapes in Word with C# and DocumentBuilder
  type: TechArticle
- description: Learn how to group shapes in Word using C#. This guide shows how to
    insert rectangle shape, group multiple shapes, and create a blank Word file programmatically.
  name: How to group shapes in Word with C# and DocumentBuilder
  steps:
  - name: '**Create a blank Word file** – Starting with a clean document guarantees
      that no hidden formatting interferes with shape positioning.'
    text: '**Create a blank Word file** – Starting with a clean document guarantees
      that no hidden formatting interferes with shape positioning.'
  - name: '**Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level
      node manipulation, letting you focus on layout.'
    text: '**Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level
      node manipulation, letting you focus on layout.'
  - name: '**Insert individual shapes** – You first need separate objects (`insert
      rectangle shape` and an ellipse) before you can group them. Adjusting `Left`
      and `Top` ensures they appear side‑by‑side.'
    text: '**Insert individual shapes** – You first need separate objects (`insert
      rectangle shape` and an ellipse) before you can group them. Adjusting `Left`
      and `Top` ensures they appear side‑by‑side.'
  - name: '**Group multiple shapes** – By creating a `GroupShape` and using **append
      child to group**, you turn two independent drawings into a single logical unit.
      Moving or resizing the group will affect both children simultaneously.'
    text: '**Group multiple shapes** – By creating a `GroupShape` and using **append
      child to group**, you turn two independent drawings into a single logical unit.
      Moving or resizing the group will affect both children simultaneously.'
  - name: '**Save the document** – The final file, `GroupedShapes.docx`, can be opened
      in Microsoft Word to verify that the rectangle and ellipse are indeed grouped
      (select one, and both move together).'
    text: '**Save the document** – The final file, `GroupedShapes.docx`, can be opened
      in Microsoft Word to verify that the rectangle and ellipse are indeed grouped
      (select one, and both move together).'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shape handling
- DocumentBuilder
title: Como agrupar formas no Word com C# e DocumentBuilder
url: /pt/java/images-shapes/how-to-group-shapes-in-word-with-c-and-documentbuilder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como agrupar formas no Word com C# e DocumentBuilder

Se você precisa **agrupar formas no Word** a partir de uma aplicação C#, este tutorial mostra exatamente como fazer isso. Você verá como *inserir uma forma retangular*, combinar vários desenhos em um único grupo e, finalmente, **criar um arquivo Word em branco** que contém os objetos agrupados.

Trabalhar com formas é uma necessidade comum ao gerar relatórios, faturas ou modelos personalizados programaticamente. Ao final deste guia, você terá um trecho de código reutilizável que pode ser inserido em qualquer projeto .NET que faça referência ao Aspose.Words.

## O que você vai aprender

- Criar um documento Word em branco do zero.  
- Inserir uma forma retangular e uma elipse usando `DocumentBuilder`.  
- **Agrupar múltiplas formas** em um `GroupShape`.  
- Usar **append child to group** para construir a hierarquia.  
- Salvar o arquivo no disco e verificar o resultado.

Nenhuma experiência prévia com Aspose.Words é necessária, mas você deve ter um entendimento básico de C# e desenvolvimento .NET.

## Pré‑requisitos

| Requisito | Motivo |
|-----------|--------|
| .NET 6.0 ou superior | Fornece o runtime para o código C#. |
| Aspose.Words for .NET (versão mais recente) | Disponibiliza as classes `Document`, `DocumentBuilder` e de forma. |
| Uma IDE como Visual Studio 2022 (ou VS Code) | Facilita a compilação e execução do exemplo. |
| Permissão de gravação em uma pasta da sua máquina | Necessária para a chamada `doc.save`. |

Instale o Aspose.Words via NuGet:

```bash
dotnet add package Aspose.Words
```

---

## Agrupar formas no Word – guia passo a passo

Abaixo está o programa completo e executável. Cada seção é explicada em detalhes para que você entenda **por que** o código foi escrito dessa forma, não apenas **o que** ele faz.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

namespace WordShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // -------------------------------------------------
            // Step 1: create a blank Word file
            // -------------------------------------------------
            // The Document constructor creates an empty .docx container.
            Document doc = new Document();

            // -------------------------------------------------
            // Step 2: initialize DocumentBuilder to add content
            // -------------------------------------------------
            // DocumentBuilder is the high‑level API for inserting text,
            // images, tables, and shapes into the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // -------------------------------------------------
            // Step 3: insert individual shapes
            // -------------------------------------------------
            // Insert a rectangle shape – this demonstrates the
            // "insert rectangle shape" keyword in practice.
            Shape rectangle = builder.InsertShape(
                ShapeType.Rectangle,   // shape type
                100,                  // width in points
                50);                  // height in points

            // Position the rectangle a little away from the left margin.
            rectangle.Left = 100;   // points from the left edge
            rectangle.Top = 100;    // points from the top of the page

            // Insert an ellipse shape to accompany the rectangle.
            Shape ellipse = builder.InsertShape(
                ShapeType.Ellipse,
                80,
                80);
            ellipse.Left = rectangle.Left + rectangle.Width + 20; // place right of rectangle
            ellipse.Top = rectangle.Top; // align tops

            // -------------------------------------------------
            // Step 4: create a GroupShape and append children
            // -------------------------------------------------
            // A GroupShape acts like a container; any shape added to it
            // moves together with the group. This fulfills the
            // "group multiple shapes" requirement.
            GroupShape group = builder.InsertGroupShape();

            // The "append child to group" operation builds the hierarchy.
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Optional: give the group a name for later reference.
            group.Name = "MyShapeGroup";

            // -------------------------------------------------
            // Step 5: save the document containing the grouped shapes
            // -------------------------------------------------
            string outputPath = @"GroupedShapes.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Por que cada passo importa

1. **Criar um arquivo Word em branco** – Começar com um documento limpo garante que nenhuma formatação oculta interfira no posicionamento das formas.  
2. **Inicializar DocumentBuilder** – `DocumentBuilder` abstrai a manipulação de nós de baixo nível, permitindo que você se concentre no layout.  
3. **Inserir formas individuais** – Primeiro você precisa de objetos separados (`insert rectangle shape` e uma elipse) antes de poder agrupá‑los. Ajustar `Left` e `Top` garante que eles apareçam lado a lado.  
4. **Agrupar múltiplas formas** – Ao criar um `GroupShape` e usar **append child to group**, você transforma dois desenhos independentes em uma única unidade lógica. Mover ou redimensionar o grupo afetará ambos os filhos simultaneamente.  
5. **Salvar o documento** – O arquivo final, `GroupedShapes.docx`, pode ser aberto no Microsoft Word para verificar que o retângulo e a elipse estão realmente agrupados (selecione um e ambos se moverão juntos).

### Saída esperada

Abra `GroupedShapes.docx` no Microsoft Word:

- Você verá um retângulo e uma elipse posicionados um ao lado do outro.  
- Selecionar qualquer forma destaca ambas, confirmando que pertencem ao mesmo grupo.  
- O grupo pode ser arrastado, redimensionado ou formatado como um único objeto.

![Diagram of grouped rectangle and ellipse inside a Word document](https://example.com/grouped-shapes.png){: .center-image alt="Diagrama de retângulo e elipse agrupados dentro de um documento Word"}

*A captura de tela ilustra as formas agrupadas finais.*

---

## Inserir forma retangular – personalizando tamanho e estilo

Se você precisar de um retângulo com uma cor de preenchimento ou borda específica, modifique o objeto `Shape` após a inserção:

```csharp
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.LineWidth = 2.0; // points
```

Essas propriedades fazem parte da classe `Shape` e funcionam para qualquer tipo de forma, não apenas retângulos. Ajustar o estilo antes de **append child to group** garante que o grupo herde as propriedades visuais que você definiu.

---

## Agrupar múltiplas formas – manipulando mais de dois objetos

O exemplo agrupa um retângulo e uma elipse, mas você pode adicionar qualquer número de formas:

```csharp
// Create additional shapes as needed
Shape triangle = builder.InsertShape(ShapeType.Triangle, 60, 60);
triangle.Left = ellipse.Left + ellipse.Width + 20;
triangle.Top = ellipse.Top;

// Append the new shape to the existing group
group.AppendChild(triangle);
```

**Dica profissional:** Depois de construir um grupo complexo, você pode bloquear seu layout para evitar alterações acidentais:

```csharp
group.LockAspectRatio = true;
group.RelativeHorizontalPosition = RelativeHorizontalPosition.Margin;
group.RelativeVerticalPosition = RelativeVerticalPosition.Margin;
```

---

## Append child to group – a ordem importa

A ordem em que você chama `AppendChild` define a ordem Z (qual forma aparece acima). No exemplo, o retângulo é adicionado primeiro, depois a elipse, de modo que a elipse sobrepõe o retângulo se eles se cruzarem. Reordenar é tão simples quanto chamar `RemoveChild` e adicionar novamente:

```csharp
group.RemoveChild(ellipse);
group.AppendChild(ellipse); // now ellipse is on top
```

---

## Criar arquivo Word em branco – método auxiliar reutilizável

Se sua aplicação frequentemente precisar de um documento novo, encapsule a lógica de criação:

```csharp
/// <summary>
/// Returns a new empty Document with a single section.
/// </summary>
static Document CreateBlankWordFile()
{
    Document emptyDoc = new Document();
    // Optionally set default page size, margins, etc.
    emptyDoc.FirstSection.PageSetup.PageWidth = 595;  // A4 width in points
    emptyDoc.FirstSection.PageSetup.PageHeight = 842; // A4 height in points
    return emptyDoc;
}
```

Você pode então substituir a linha `new Document()` no programa principal por `CreateBlankWordFile()`. Isso demonstra o conceito de **create blank word file** de forma reutilizável.

---

## Armadilhas comuns e como evitá‑las

| Problema | Por que acontece | Solução |
|----------|------------------|---------|
| Formas aparecem fora da página | Valores padrão de `Left`/`Top` são 0, posicionando a forma na margem. | Defina explicitamente `Left` e `Top` após a inserção. |
| O grupo perde formatação | Alterar uma forma filha depois de adicioná‑la ao grupo pode quebrar o layout do grupo. | Aplique todas as propriedades visuais **antes** de chamar `AppendChild`. |
| Arquivo salvo está vazio | `DocumentBuilder` nunca foi usado para adicionar um nó, ou `doc.Save` foi chamado em uma instância diferente de `Document`. | Verifique se está salvando o mesmo `Document` que você construiu. |
| Avisos de compatibilidade no Word | Uso de recursos de forma mais recentes que não são suportados |

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}