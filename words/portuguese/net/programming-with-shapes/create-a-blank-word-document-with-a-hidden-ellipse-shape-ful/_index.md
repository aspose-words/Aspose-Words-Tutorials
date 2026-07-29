---
category: general
date: 2026-07-29
description: Crie um documento Word em branco e aprenda como ocultar forma, criar
  objeto oculto e criar forma de elipse usando Aspose.Words em C#. Código passo a
  passo incluído.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- blank word document
- how to hide shape
- create hidden object
- create ellipse shape
language: pt
lastmod: 2026-07-29
og_description: Crie um documento Word em branco e oculte a forma instantaneamente.
  Aprenda a criar um objeto oculto e desenhar uma forma elíptica usando Aspose.Words
  em C#.
og_image_alt: Hidden ellipse shape inserted into a blank Word document
og_title: Criar um documento Word em branco com uma forma de elipse oculta – Tutorial
  C#
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Create a blank word document and learn how to hide shape, create hidden
    object, and create ellipse shape using Aspose.Words in C#. Step‑by‑step code included.
  headline: Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide
  type: TechArticle
- description: Create a blank word document and learn how to hide shape, create hidden
    object, and create ellipse shape using Aspose.Words in C#. Step‑by‑step code included.
  name: Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide
  steps:
  - name: What if the target Word version doesn’t support hidden shapes?
    text: The `Hidden` flag is part of the Office Open XML spec and is respected by
      Word 2007+ and LibreOffice. Older formats (e.g., `.doc`) ignore the flag, so
      always save as `.docx` when you need reliable hiding.
  - name: Can I hide other types of objects (pictures, tables)?
    text: Yes. Any node derived from `Shape`—including pictures, text boxes, and even
      SmartArt—exposes the `Hidden` property. Just set it to `true` before insertion.
  - name: Does hiding a shape affect document performance?
    text: Negligibly. The shape is stored as XML markup, and Word skips rendering
      hidden objects during layout. If you embed many hidden objects, the file size
      grows, but rendering stays fast.
  - name: How does this differ from using a bookmark or comment as a marker?
    text: Bookmarks are invisible by design, but they’re meant for navigation, not
      visual placeholders. Comments appear in the margin. A hidden shape gives you
      a visual object (size, position) that you can later reveal or manipulate, which
      is handy for templating scenarios.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
- Shapes
title: Criar um Documento Word em Branco com uma Forma de Elipse Oculta – Guia Completo
  de C#
url: /pt/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar um Documento Word em Branco com uma Forma de Elipse Oculta – Guia Completo em C#

Já precisou criar um **documento Word em branco** e depois ocultar uma forma dentro dele? Talvez você esteja gerando um modelo onde certos marcadores precisam permanecer invisíveis até uma etapa posterior. Neste tutorial vamos percorrer exatamente **como ocultar forma**, como **criar objeto oculto**, e até como **criar forma de elipse** usando Aspose.Words para .NET. Ao final, você terá um trecho de C# pronto‑para‑executar que produz um arquivo DOCX contendo uma elipse invisível.

## O que você aprenderá

- Inicializar um novo documento Word em branco com Aspose.Words.  
- Criar uma forma de elipse, definir suas dimensões e posicioná‑la na página.  
- Marcar a forma como oculta para que nunca apareça na tela ou na impressão.  
- Salvar o resultado no disco e verificar se o objeto oculto está realmente invisível.  

Nenhuma biblioteca externa além do Aspose.Words é necessária, e o código funciona com a versão 24.10 ou superior (a propriedade `Hidden` foi introduzida nessa versão). Vamos começar.

![Diagrama de uma elipse oculta dentro de um documento Word em branco](https://example.com/hidden-ellipse.png "Forma de elipse oculta inserida em um documento Word em branco")

## Criar um Documento Word em Branco e Inserir uma Forma de Elipse Oculta

O primeiro passo é iniciar um documento totalmente novo. Pense em `Document` como uma tela vazia; `DocumentBuilder` é seu pincel.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document and a DocumentBuilder to edit it.
Document document = new Document();               // This is your blank word document.
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Por que começar com um documento em branco?**  
> Uma página limpa garante que nenhum conteúdo pré‑existente interfira na forma oculta que você está prestes a adicionar. Também torna o exemplo mais fácil de copiar‑colar em qualquer projeto.

## Como ocultar a forma: Definindo a propriedade Hidden

O Aspose.Words 24.10 introduziu a bandeira `Hidden` em `Shape`. Quando definida como `true`, o Word trata a forma como um comentário — completamente invisível na interface e ao imprimir.

```csharp
// Step 2: Create an ellipse shape and set its size and position.
Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
ellipseShape.Width = 100;   // Width in points
ellipseShape.Height = 80;   // Height in points
ellipseShape.Left = 150;    // Horizontal offset from the left margin
ellipseShape.Top = 150;     // Vertical offset from the top margin

// Step 3: Hide the shape so it does not appear when the document is viewed or printed.
ellipseShape.Hidden = true;   // This is the key to "how to hide shape"
```

> **Dica profissional:** Se mais tarde precisar revelar a forma programaticamente, basta alternar `ellipseShape.Hidden = false;` e salvar o documento novamente.

## Criar Objeto Oculto: Inserindo a Forma no Documento

Agora que a elipse está preparada e oculta, inserimos ela na posição atual do cursor do builder. A posição do builder por padrão é o início do primeiro parágrafo, o que é perfeito para um documento em branco.

```csharp
// Step 4: Insert the hidden shape into the document at the current builder position.
builder.InsertNode(ellipseShape);
```

> **E se você precisar da forma em uma página específica?**  
> Mova o builder para a página desejada primeiro (`builder.MoveToDocumentEnd();` ou `builder.MoveToPage(pageNumber);`) antes de chamar `InsertNode`.

## Salvar o Documento contendo a Forma Oculta

Finalmente, grave o arquivo no disco. A saída será um DOCX padrão que qualquer processador de texto pode abrir — exceto que a elipse permanecerá invisível.

```csharp
// Step 5: Save the document containing the hidden shape.
document.Save("YOUR_DIRECTORY/HiddenShape.docx");
```

> **Saída esperada:** Abra `HiddenShape.docx` no Microsoft Word. Você não verá nenhum gráfico, mas o tamanho do arquivo será ligeiramente maior que um documento realmente vazio porque a elipse oculta está armazenada no XML.

## Verificar a Elipse Oculta Programaticamente (Opcional)

Se quiser confirmar que a forma está realmente oculta, você pode carregar o arquivo salvo e inspecionar a propriedade `Hidden` da forma:

```csharp
Document loaded = new Document("YOUR_DIRECTORY/HiddenShape.docx");
Shape loadedShape = (Shape)loaded.GetChild(NodeType.Shape, 0, true);
Console.WriteLine($"Is shape hidden? {loadedShape.Hidden}"); // Should print True
```

Executar este trecho imprime `True`, confirmando que o objeto oculto sobreviveu ao ciclo de salvar‑carregar.

## Casos Limites e Perguntas Frequentes

### E se a versão alvo do Word não suportar formas ocultas?

A bandeira `Hidden` faz parte da especificação Office Open XML e é respeitada pelo Word 2007+ e LibreOffice. Formatos mais antigos (por exemplo, `.doc`) ignoram a bandeira, portanto sempre salve como `.docx` quando precisar de ocultação confiável.

### Posso ocultar outros tipos de objetos (imagens, tabelas)?

Sim. Qualquer nó derivado de `Shape` — incluindo imagens, caixas de texto e até SmartArt — expõe a propriedade `Hidden`. Basta defini‑la como `true` antes da inserção.

### Ocultar uma forma afeta o desempenho do documento?

Negligivelmente. A forma é armazenada como marcação XML, e o Word ignora a renderização de objetos ocultos durante o layout. Se você incorporar muitas formas ocultas, o tamanho do arquivo aumenta, mas a renderização permanece rápida.

### Como isso difere de usar um marcador ou comentário como indicador?

Marcadores são invisíveis por design, mas destinam‑se à navegação, não a marcadores visuais. Comentários aparecem na margem. Uma forma oculta fornece um objeto visual (tamanho, posição) que você pode revelar ou manipular posteriormente, o que é útil em cenários de modelagem de templates.

## Exemplo Completo Funcional

Abaixo está o programa completo, pronto para copiar‑e‑colar. Ele inclui todas as diretivas using, a criação da elipse oculta e uma etapa de verificação.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HiddenEllipseDemo
{
    static void Main()
    {
        // 1️⃣ Create a blank word document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Build the ellipse shape.
        Shape ellipse = new Shape(doc, ShapeType.Ellipse)
        {
            Width = 100,
            Height = 80,
            Left = 150,
            Top = 150,
            Hidden = true               // ← how to hide shape
        };

        // 3️⃣ Insert the hidden shape.
        builder.InsertNode(ellipse);

        // 4️⃣ Save the file.
        string outPath = "HiddenEllipse.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");

        // 5️⃣ Optional: Verify that the shape is hidden.
        Document loaded = new Document(outPath);
        Shape loadedEllipse = (Shape)loaded.GetChild(NodeType.Shape, 0, true);
        Console.WriteLine($"Is the ellipse hidden? {loadedEllipse.Hidden}");
    }
}
```

Executar o programa cria `HiddenEllipse.docx` na pasta de execução. Abra‑o — você verá uma página em branco perfeitamente normal, porém a elipse oculta permanece silenciosamente dentro.

## Recapitulação

Cobrimos como **criar um documento Word em branco**, **ocultar uma forma**, **criar objeto oculto**, e **criar forma de elipse** tudo com algumas linhas de C#. O ponto principal é a propriedade `Hidden` em `Shape`, que transforma qualquer elemento visual em um marcador invisível sem quebrar a compatibilidade com o Word.

## O que vem a seguir?

- **Estilizar a forma oculta** (cor de preenchimento, estilo de linha) para que, quando você revelá‑la mais tarde, ela apareça exatamente como desejado.  
- **Combinar formas ocultas com marcadores** para construir templates dinâmicos que podem ser ativados ou desativados.  
- **Explorar outros tipos de forma** — retângulos, setas ou até caminhos SVG personalizados — trocando `ShapeType.Ellipse`.  

Sinta‑se à vontade para experimentar: altere o tamanho, mova a posição ou insira múltiplas elipses ocultas. O mesmo padrão funciona para qualquer forma do Aspose.Words que você precise manter fora de vista.

Se encontrar algum problema ou tiver ideias para expandir esse padrão, deixe um comentário abaixo. Boa codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Criar Documento Word em Branco com Forma de Retângulo Sombreada – Guia Passo a Passo](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Criar Forma de Grupo em Documento Word Usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Criar forma de retângulo no Word com Aspose.Words – Guia passo a passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}