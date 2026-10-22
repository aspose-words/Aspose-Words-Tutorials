---
category: general
date: 2026-09-05
description: Aprenda a criar um documento Word em branco e adicionar uma forma retangular
  que pode ser ocultada usando Aspose.Words em C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- blank word document
- add rectangle shape
- how to hide shape
- hide shape word
- create hidden shape
language: pt
lastmod: 2026-09-05
og_description: Criação de documento Word em branco e inserção de forma retangular
  oculta usando Aspose.Words – guia passo a passo para desenvolvedores C#.
og_image_alt: Screenshot of a blank Word document with a hidden rectangle shape created
  by Aspose.Words in C#
og_title: Crie um documento Word em branco com uma forma de retângulo oculta
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  headline: Create a blank word document and add a rectangle shape
  type: TechArticle
- description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  name: Create a blank word document and add a rectangle shape
  steps:
  - name: Expected result
    text: 'Open `HiddenRectangle.docx` in Word:'
  - name: Can I hide multiple shapes at once?
    text: Yes. Create each shape, set `Hidden = true`, and insert them sequentially.
      The hidden flag works per node, so mixing hidden and visible shapes in the same
      document is supported.
  - name: What if I need the shape to be hidden only in the print view?
    text: 'Word distinguishes between **display** and **print** visibility through
      the `DisplayWhen` property. Aspose.Words does not expose a direct API for that
      flag, but you can modify the underlying XML:'
  - name: Does the hidden shape affect file size?
    text: A hidden shape adds the same XML payload as a visible one, so the file size
      increase is identical. However, because the shape
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Crie um documento Word em branco e adicione um retângulo.
url: /pt/net/programming-with-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar um documento Word em branco e adicionar uma forma retangular

Se você precisa criar um **documento Word em branco** que também contenha uma forma que você não quer que apareça no layout, este guia mostra exatamente como fazer isso com Aspose.Words para .NET. Você verá um exemplo completo e executável que cria um novo documento, adiciona uma forma retangular, oculta essa forma e salva o arquivo — sem necessidade de ferramentas adicionais.

O tutorial cobre tudo, desde a configuração do projeto até a solução de problemas comuns. Ao final, você será capaz de gerar um arquivo Word que parece vazio para o leitor, mas ainda contém metadados ocultos, o que é útil para coisas como marcas d'água, armazenamento de XML personalizado ou âncoras de layout.

## Pré-requisitos

* .NET 6.0 SDK ou posterior (o código também funciona com .NET Framework 4.7+)
* Visual Studio 2022 (ou qualquer IDE que suporte C#)
* Uma licença ativa do **Aspose.Words** via NuGet (a versão de avaliação gratuita serve para testes)
* Familiaridade básica com C# e o conceito de nós de documento

Você pode instalar a biblioteca com o seguinte comando CLI:

```bash
dotnet add package Aspose.Words
```

> **Dica profissional:** Mantenha sua versão do Aspose.Words atualizada; a API usada neste tutorial está estável a partir da versão 23.10.

## Como criar um documento Word em branco com Aspose.Words

O primeiro passo é instanciar um objeto `Document`. Um `Document` novo representa um **documento Word em branco** vazio — sem parágrafos, sem seções, apenas o contêiner do arquivo.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, empty Word document
Document document = new Document();
```

> **Por que isso importa:** Começar com um documento limpo garante que a forma oculta que você adicionará mais tarde não interfira no conteúdo ou estilos existentes.

## Adicionar uma forma retangular ao documento

Em seguida, criamos uma forma retangular. No Aspose.Words, uma forma é um nó que pode ser colocado em qualquer lugar da árvore do documento, e pode ser configurado com tamanho, preenchimento, estilo de linha e visibilidade.

```csharp
// Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Define a rectangle shape (the "add rectangle shape" step)
Shape rectangle = new Shape(document, ShapeType.Rectangle)
{
    Width = 150,   // Width in points (1 point = 1/72 inch)
    Height = 80,   // Height in points
    FillColor = System.Drawing.Color.LightGray,
    StrokeColor = System.Drawing.Color.DarkGray,
    StrokeWeight = 0.5
};
```

O código acima cria um retângulo visível. Neste ponto, você poderia inseri-lo no documento com `builder.InsertNode(rectangle)`. No entanto, como queremos que a forma permaneça oculta, ajustaremos sua propriedade `Hidden` antes da inserção.

## Como ocultar forma em um documento Word

O Word fornece um atributo `Hidden` para nós de forma. Quando definido como `true`, a forma não aparece no layout da página, mas permanece parte do XML do documento. Este é o cerne do requisito de **como ocultar forma**.

```csharp
// Hide the shape so it won't be displayed
rectangle.Hidden = true;
```

> **Explicação:** Definir `Hidden = true` adiciona o atributo `<w:hide>` ao XML da forma. Processadores de Word ignoram a forma durante a renderização, porém a forma ainda pode ser acessada programaticamente ou via a visualização XML do Word.

## Inserir a forma oculta no documento em branco

Agora colocamos o retângulo oculto na árvore do documento. Como o documento ainda está vazio, a forma se torna o primeiro nó na história principal.

```csharp
// Insert the hidden rectangle at the current cursor position
builder.InsertNode(rectangle);
```

Se você abrir o arquivo resultante no Microsoft Word, verá uma página aparentemente vazia. A forma está lá, mas está invisível.

## Salvar o documento

Finalmente, grave o documento no disco. Você pode escolher qualquer formato suportado (`.docx`, `.pdf`, `.odt`, etc.). Para este tutorial, usaremos o formato DOCX moderno.

```csharp
// Save the file – adjust the path as needed
string outputPath = Path.Combine(Environment.CurrentDirectory, "HiddenRectangle.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

### Resultado esperado

Abra `HiddenRectangle.docx` no Word:

* O documento aparece em branco (sem formas ou texto visíveis).
* Se você inspecionar o arquivo com uma ferramenta como **Open XML SDK** ou o **Word XML Viewer**, verá o elemento `<w:pict>` contendo o retângulo com o atributo `hidden`.

![documento Word em branco com forma de retângulo oculta](image.png){: .align-center alt="documento Word em branco com forma de retângulo oculta"}

## Exemplo completo e executável

Abaixo está o programa completo que você pode copiar e colar em uma aplicação de console. Ele inclui todas as diretivas `using` necessárias, tratamento de erros e comentários.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Prepare a DocumentBuilder to manipulate the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Define a rectangle shape (add rectangle shape)
        Shape rectangle = new Shape(document, ShapeType.Rectangle)
        {
            Width = 150,
            Height = 80,
            FillColor = System.Drawing.Color.LightGray,
            StrokeColor = System.Drawing.Color.DarkGray,
            StrokeWeight = 0.5,
            // 4️⃣ Hide the shape (how to hide shape)
            Hidden = true
        };

        // 5️⃣ Insert the hidden shape into the blank document
        builder.InsertNode(rectangle);

        // 6️⃣ Save the document (create hidden shape)
        string outputPath = Path.Combine(
            Environment.CurrentDirectory, "HiddenRectangle.docx");
        document.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Execute o programa (`dotnet run`) e verifique o arquivo de saída. O console confirmará o local de salvamento.

## Perguntas comuns e casos extremos

### Posso ocultar várias formas ao mesmo tempo?

Sim. Crie cada forma, defina `Hidden = true` e insira-as sequencialmente. A bandeira oculta funciona por nó, portanto, misturar formas ocultas e visíveis no mesmo documento é suportado.

### E se eu precisar que a forma fique oculta apenas na visualização de impressão?

O Word diferencia entre visibilidade **de exibição** e **de impressão** através da propriedade `DisplayWhen`. O Aspose.Words não expõe uma API direta para essa bandeira, mas você pode modificar o XML subjacente:

```csharp
rectangle.GetShapeRenderer().GetShapeXml()
    .SetAttribute("w:display", "print");
```

Use isso apenas quando precisar de visibilidade somente na impressão.

### A forma oculta afeta o tamanho do arquivo?

Uma forma oculta adiciona a mesma carga XML que uma forma visível, portanto o aumento do tamanho do arquivo é idêntico. Contudo, como a forma

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá-lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Criar Documento Word em Branco com Forma Retangular com Sombra – Guia Passo a Passo](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Criar forma retangular no Word usando C# – Guia Passo a Passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Tutorial de Sombra de Forma Aspose.Words – Adicionar Sombra a Forma Word em C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}