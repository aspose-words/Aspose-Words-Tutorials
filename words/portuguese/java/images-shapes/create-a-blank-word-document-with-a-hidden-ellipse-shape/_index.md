---
category: general
date: 2026-09-18
description: Crie um documento Word em branco e oculte uma forma elíptica usando Aspose.Words.
  Aprenda como ocultar formas no Word, como inserir uma elipse e criar uma forma oculta
  rapidamente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to hide shape
- how to insert ellipse
- hide shape in word
- create hidden shape
language: pt
lastmod: 2026-09-18
og_description: Crie um documento Word em branco e oculte uma forma de elipse no Word.
  Este guia mostra passo a passo como inserir a elipse, ocultar a forma no Word e
  criar uma forma oculta com Aspose.Words.
og_image_alt: Screenshot of a blank Word document containing a hidden ellipse shape
  created with Aspose.Words
og_title: Criar um documento Word em branco com uma forma de elipse oculta
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create a blank Word document and hide an ellipse shape using Aspose.Words.
    Learn how to hide shape in Word, how to insert ellipse, and create hidden shape
    quickly.
  headline: Create a blank Word document with a hidden ellipse shape
  type: TechArticle
- description: Create a blank Word document and hide an ellipse shape using Aspose.Words.
    Learn how to hide shape in Word, how to insert ellipse, and create hidden shape
    quickly.
  name: Create a blank Word document with a hidden ellipse shape
  steps:
  - name: Pro tip
    text: If you later need to make the shape visible again, simply set `ellipse.Hidden
      = false;` and save the document.
  - name: What if the shape still appears?
    text: '* Ensure you are using Aspose.Words 23.9 or later – older versions had
      a bug where `Hidden` was ignored for some shape types. * Verify that you are
      not applying any additional formatting (e.g., `WrapType`) that forces the shape
      to occupy layout space.'
  - name: Can I hide other shape types?
    text: Yes. The same `Hidden` property works for `ShapeType.Rectangle`, `ShapeType.Picture`,
      etc. Just replace `ShapeType.Ellipse` with the desired type.
  - name: How to list hidden shapes later?
    text: '```csharp foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
      { if (shape.Hidden) Console.WriteLine($"Hidden shape: {shape.ShapeType}"); }
      ```'
  - name: Next steps
    text: '* Explore **how to hide shape** conditionally based on document content.
      * Learn **how to unhide shape** when generating a final version of the document.
      * Combine hidden shapes with **custom document properties** to embed machine‑readable
      data.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Criar um documento Word em branco com uma forma de elipse oculta
url: /pt/java/images-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar um documento Word em branco com uma forma de elipse oculta

Se você precisar **criar um documento Word em branco** que contenha uma forma que você não deseja que apareça no layout, este guia mostra exatamente como fazer isso. Usando Aspose.Words for .NET, você pode inserir programaticamente uma elipse e então ocultar a forma para que o documento permaneça visualmente vazio, mas ainda contenha os dados da forma.

Neste tutorial você aprenderá:

* como **criar objetos de documento Word em branco**,
* como **inserir elipse** usando `DocumentBuilder`,
* como **ocultar forma no Word** para que não afete a página,
* como **criar objetos de forma oculta** para processamento posterior.

As etapas funcionam com .NET 6+ e a versão mais recente do Aspose.Words (23.9 no momento da escrita). Nenhuma instalação adicional do Office é necessária.

## Pré-requisitos

* Visual Studio 2022 (ou qualquer IDE C#)
* .NET 6 SDK ou posterior
* Pacote NuGet Aspose.Words for .NET  
  ```bash
  dotnet add package Aspose.Words
  ```
* Conhecimento básico de C# e conceitos de documentos Word

## Etapa 1: Criar um documento Word em branco

A primeira coisa que você deve fazer é instanciar um objeto `Document`. Esse objeto representa um arquivo `.docx` vazio e é a base para todas as operações subsequentes.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document
Document doc = new Document();   // <-- creates a blank Word document in memory
```

Criar um **documento Word em branco** fornece uma tela limpa – sem parágrafos, sem seções, apenas a estrutura subjacente do pacote. Este é o ponto de partida ideal quando você precisa apenas de uma forma oculta e nada mais.

## Etapa 2: Inicializar um DocumentBuilder

`DocumentBuilder` fornece uma API conveniente para adicionar conteúdo a um `Document`. Ele funciona como um cursor que você move pelo documento.

```csharp
// Step 2: Initialise a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

O builder cria automaticamente uma primeira seção e parágrafo padrão, para que você possa começar a inserir formas sem precisar adicionar seções manualmente.

## Etapa 3: Inserir uma forma de elipse

Agora nós **inserimos elipse** usando o método `InsertShape`. O método recebe uma enumeração `ShapeType`, a largura e a altura (em pontos).

```csharp
// Step 3: Insert an ellipse shape with a width of 100 points and a height of 50 points
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
```

Por que uma elipse? Uma elipse é uma forma vetorial que pode ser ocultada sem afetar o fluxo de texto ao redor. A largura de 100 pt e a altura de 50 pt são arbitrárias; você pode ajustá‑las conforme suas necessidades de processamento posterior.

## Etapa 4: Ocultar a forma para que não apareça no layout

Para **ocultar forma no Word**, defina a propriedade `Hidden` no objeto `Shape` como `true`. Quando o documento for aberto no Microsoft Word, a forma ficará invisível e não ocupará espaço no layout.

```csharp
// Step 4: Hide the shape so it does not appear in the layout
ellipse.Hidden = true;   // <-- this hides the shape in Word
```

A flag `Hidden` é armazenada no XML da forma (`<w:hidden/>`). O Word respeita esse atributo durante a renderização, por isso o documento parece completamente em branco, embora a forma exista.

### Dica profissional

Se mais tarde precisar tornar a forma visível novamente, basta definir `ellipse.Hidden = false;` e salvar o documento.

## Etapa 5: Salvar o documento com a forma oculta

Por fim, persista o documento no disco. O arquivo será um `.docx` regular que qualquer processador de Word pode abrir.

```csharp
// Step 5: Save the document with the hidden shape
doc.Save(@"C:\Temp\HiddenEllipse.docx");
```

O arquivo salvo, `HiddenEllipse.docx`, é um **documento Word em branco** que contém uma elipse oculta. Ao abri‑lo no Microsoft Word, será exibida uma página vazia, mas a forma ainda está presente na estrutura Open XML.

## Exemplo completo em funcionamento

Abaixo está o programa completo e autocontido que você pode copiar, colar e executar.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace HiddenShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a blank Word document
            Document doc = new Document();

            // 2️⃣ Initialise DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert an ellipse shape (width: 100pt, height: 50pt)
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

            // 4️⃣ Hide the shape so it does not affect layout
            ellipse.Hidden = true;

            // 5️⃣ Save the result
            string outputPath = @"C:\Temp\HiddenEllipse.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Saída esperada**

* Um arquivo chamado `HiddenEllipse.docx` aparece em `C:\Temp`.
* Ao abrir o arquivo no Microsoft Word, uma página completamente em branco é exibida.
* Se você inspecionar o documento com o Open XML SDK ou um visualizador de zip, encontrará o elemento `<w:shape>` com `<w:hidden/>` dentro da parte do documento.

## Perguntas comuns e casos de borda

### E se a forma ainda aparecer?

* Certifique‑se de que está usando Aspose.Words 23.9 ou posterior – versões mais antigas tinham um bug onde `Hidden` era ignorado para alguns tipos de forma.
* Verifique se não está aplicando nenhuma formatação adicional (por exemplo, `WrapType`) que force a forma a ocupar espaço no layout.

### Posso ocultar outros tipos de forma?

Sim. A mesma propriedade `Hidden` funciona para `ShapeType.Rectangle`, `ShapeType.Picture`, etc. Basta substituir `ShapeType.Ellipse` pelo tipo desejado.

### Como listar formas ocultas posteriormente?

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.Hidden)
        Console.WriteLine($"Hidden shape: {shape.ShapeType}");
}
```

Este trecho itera sobre todas as formas e imprime aquelas que estão ocultas, o que é útil para fluxos de trabalho de **criar forma oculta** onde você precisa processá‑las ou revelá‑las mais tarde.

## Conclusão

Agora você sabe como **criar um documento Word em branco**, **inserir elipse** e **ocultar forma no Word** para produzir uma **forma oculta** que permanece invisível ao leitor. Essa técnica é útil para armazenar metadados, marcadores ou XML personalizado dentro de um documento sem alterar sua aparência visual.

### Próximos passos

* Explore **como ocultar forma** condicionalmente com base no conteúdo do documento.
* Aprenda **como revelar forma** ao gerar a versão final do documento.
* Combine formas ocultas com **propriedades de documento personalizadas** para incorporar dados legíveis por máquina.

Sinta‑se à vontade para experimentar diferentes tipos de forma, tamanhos e lógica de estado oculto para adequar ao seu cenário de automação. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que expandem as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}