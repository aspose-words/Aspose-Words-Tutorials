---
category: general
date: 2026-10-07
description: Criar um documento Word em branco em C# e aprender a adicionar forma
  de retângulo, inserir forma de imagem e agrupar várias formas para relatórios dinâmicos.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- insert image shape
- group multiple shapes
- add image to word
language: pt
lastmod: 2026-10-07
og_description: Crie um documento Word em branco em C# com Aspose.Words. Aprenda a
  adicionar forma retangular, inserir forma de imagem e agrupar várias formas para
  documentos profissionais.
og_image_alt: Screenshot of a Word file showing a grouped rectangle and logo created
  with C#
og_title: Criar documento Word em branco e agrupar formas em C# – guia passo a passo
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create blank Word document in C# and learn to add rectangle shape,
    insert image shape, and group multiple shapes for dynamic reports.
  headline: How to create blank Word document and group shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Como criar um documento Word em branco e agrupar formas em C#
url: /pt/net/programming-with-shapes/how-to-create-blank-word-document-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar documento Word em branco e agrupar formas em C#

Se você precisar **criar documento Word em branco** programaticamente, este guia mostra exatamente como. Você verá como **adicionar forma de retângulo**, **inserir forma de imagem** e **agrupar várias formas** para que elas se comportem como um único objeto quando você **adicionar imagem ao Word** mais tarde.

Trabalhar com arquivos Word a partir do código pode parecer intimidante, mas o Aspose.Words torna o processo simples. Ao final deste tutorial você terá um trecho de código C# reutilizável que gera um arquivo Word limpo e vazio contendo um retângulo agrupado e um logotipo. Você pode incorporar o resultado em faturas, relatórios ou qualquer fluxo de trabalho de documentos automatizado.

## Pré-requisitos

* .NET 6.0 ou posterior (o código também funciona com .NET Framework 4.7+).  
* Uma licença válida do Aspose.Words for .NET ou uma chave de avaliação gratuita.  
* Um arquivo de imagem (por exemplo, `logo.png`) colocado em uma pasta que você pode referenciar no código.  
* Visual Studio 2022 ou qualquer IDE compatível com C#.

Nenhum pacote NuGet adicional é necessário além de `Aspose.Words`.

## Como criar documento Word em branco com Aspose.Words

O primeiro passo é sempre **criar documento Word em branco**. Este objeto hospedará todas as formas subsequentes.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// 1️⃣ Initialize a new empty document.
Document doc = new Document();

// 2️⃣ Prepare a DocumentBuilder – it simplifies adding content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` representa o arquivo `.docx` completo. Neste ponto o arquivo está vazio, o que atende ao requisito de *criar documento Word em branco*.

## Criar um contêiner para agrupar várias formas

Agrupar formas permite mover, girar ou redimensionar todas juntas. O Aspose.Words fornece a classe `GroupShape` para esse propósito.

```csharp
// 3️⃣ Create a GroupShape that will hold our drawing objects.
GroupShape group = new GroupShape(doc)
{
    // Define the container’s position and size on the page.
    Bounds = new Rectangle(50, 50, 300, 200)
};

// Append the group to the first paragraph of the first section.
doc.FirstSection.Body.FirstParagraph.AppendChild(group);
```

O retângulo `Bounds` determina onde o grupo aparece na página. Ao colocar o grupo no primeiro parágrafo, você garante que o **criar documento Word em branco** conterá imediatamente um contêiner visual.

## Como adicionar forma de retângulo dentro do grupo

Um requisito comum é **adicionar forma de retângulo** como fundo ou borda. O código a seguir cria um retângulo e o adiciona ao grupo definido anteriormente.

```csharp
// 4️⃣ Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width = 100,
    Height = 80,
    Left = 20,
    Top = 20,
    // Optional: give the rectangle a light gray fill.
    FillColor = Color.LightGray
};

// Add the rectangle to the group.
group.AppendChild(rectangle);
```

Como o retângulo está dentro do `GroupShape`, ele se moverá junto com quaisquer outras formas que você adicionar posteriormente. Este é o núcleo da funcionalidade de **group multiple shapes**.

## Como inserir forma de imagem dentro do grupo

Em seguida, você **inserirá forma de imagem** (o logotipo) e a posicionará ao lado do retângulo. Isso demonstra o fluxo de trabalho de **adicionar imagem ao Word**.

```csharp
// 5️⃣ Create an image shape.
Shape picture = new Shape(doc, ShapeType.Image)
{
    Width = 80,
    Height = 80,
    Left = 150,
    Top = 30
};

// Load the image from disk. Replace the path with your actual image location.
picture.ImageData.SetImage(Image.FromFile(@"YOUR_DIRECTORY/logo.png"));

// Add the image shape to the same group.
group.AppendChild(picture);
```

O método `SetImage` lê o arquivo e o incorpora diretamente ao documento Word, garantindo que a imagem persista mesmo quando o arquivo de origem for movido. Isso conclui a etapa de **inserir forma de imagem** e finaliza o requisito de **adicionar imagem ao Word**.

## Salvar o documento

Finalmente, persista o arquivo no disco. O arquivo salvo contém o documento em branco, o retângulo agrupado e o logotipo incorporado.

```csharp
// 6️⃣ Save the document with the grouped shapes.
doc.Save(@"YOUR_DIRECTORY/GroupShape.docx");
```

Ao abrir `GroupShape.docx` no Microsoft Word, você verá um único grupo que inclui um retângulo cinza‑claro e o logotipo posicionados lado a lado. Selecionar qualquer parte do grupo permite mover ou redimensionar toda a coleção, provando que as formas realmente **group multiple shapes**.

## Exemplo completo e executável

Abaixo está o programa completo que você pode copiar, colar e executar. Substitua `YOUR_DIRECTORY` por um caminho absoluto ou relativo que exista na sua máquina.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank Word document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Create a GroupShape to hold the rectangle and image.
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new Rectangle(50, 50, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);

        // Step 3: Add a rectangle shape inside the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 100,
            Height = 80,
            Left = 20,
            Top = 20,
            FillColor = Color.LightGray
        };
        group.AppendChild(rectangle);

        // Step 4: Insert an image shape inside the group.
        Shape picture = new Shape(doc, ShapeType.Image)
        {
            Width = 80,
            Height = 80,
            Left = 150,
            Top = 30
        };
        picture.ImageData.SetImage(Image.FromFile(@"YOUR_DIRECTORY/logo.png"));
        group.AppendChild(picture);

        // Step 5: Save the document.
        doc.Save(@"YOUR_DIRECTORY/GroupShape.docx");
    }
}
```

### Saída esperada

* Um arquivo chamado `GroupShape.docx` localizado em `YOUR_DIRECTORY`.  
* Ao abrir o arquivo no Word, ele mostra um único grupo visual contendo um retângulo cinza à esquerda e o `logo.png` à direita.  
* Selecionar qualquer parte do grupo visual permite mover ou redimensionar toda a coleção, confirmando que as formas estão corretamente **group multiple shapes**.

## Perguntas comuns e tratamento de casos extremos

| Pergunta | Resposta |
|---|---|
| **Posso adicionar mais de duas formas ao mesmo grupo?** | Sim. Chame `group.AppendChild(yourShape)` para cada `Shape` adicional. O grupo pode conter qualquer número de objetos de desenho. |
| **E se o arquivo de imagem estiver ausente?** | `SetImage` lançará uma `FileNotFoundException`. Envolva a chamada em um bloco try‑catch e forneça uma alternativa (por exemplo, uma forma de espaço reservado). |
| **Preciso definir `WrapType` para as formas?** | Por padrão, as formas são inline. Se precisar de comportamento flutuante, defina `picture.WrapType = WrapType.Inline;` ou outro modo de ajuste antes de adicionar ao grupo. |
| **Como o tamanho do documento afeta os limites do grupo?** | O retângulo `Bounds` é definido em pontos (1 pt ≈ 1/72 pol). Ajuste o tamanho se colocar o grupo em um layout de página diferente (por exemplo, A4 vs. Letter). |
| **Posso reutilizar o mesmo grupo em outro documento?** | Sim. Clone o grupo com `GroupShape cloned = (GroupShape)group.Clone(true);` e insira‑o em um `Document` diferente. |

## Dicas profissionais

* **Reuse the `DocumentBuilder`** para adicionar texto antes ou depois do grupo. Ele respeita automaticamente a posição atual do cursor.  
* **Set `Shape.StrokeColor`** se precisar de uma borda visível ao redor do retângulo.  
* **Use PNGs de alta resolução** para o logotipo a fim de evitar pixelização quando

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá-lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Criar forma de grupo em documento Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Criar forma de retângulo em Word usando C# – Guia passo a passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Inserir imagem inline em documento Word usando Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}