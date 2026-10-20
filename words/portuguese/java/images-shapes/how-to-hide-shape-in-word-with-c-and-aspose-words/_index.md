---
category: general
date: 2026-09-11
description: Aprenda como ocultar formas no Word usando C#. Este guia também mostra
  como inserir uma forma retangular e inserir forma em um documento Word com Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape in word
- insert rectangle shape
- insert shape into word document
language: pt
lastmod: 2026-09-11
og_description: Como ocultar forma no Word usando C# e Aspose.Words. Siga o tutorial
  passo a passo para inserir forma retangular e gerenciar formas em um documento Word.
og_image_alt: Screenshot showing how to hide shape in Word document using C#
og_title: Como ocultar forma no Word – guia completo de C#
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  headline: How to hide shape in Word with C# and Aspose.Words
  type: TechArticle
- description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  name: How to hide shape in Word with C# and Aspose.Words
  steps:
  - name: Explanation of each step
    text: 1. **Create a new document** – `Document` represents the Word file in memory.
      `DocumentBuilder` provides a fluent API for inserting content. 2. **Insert rectangle
      shape** – `InsertShape` creates a drawing object of type `Rectangle`. The dimensions
      are expressed in points (1 pt ≈ 1/72 in). This satis
  - name: Expected result
    text: 'Open `output.docx` in Microsoft Word:'
  - name: Manually adding the hidden attribute (fallback)
    text: '```csharp // Fallback for Aspose.Words versions prior to 24.10 Shape shape
      = builder.InsertShape(ShapeType.Rectangle, 100, 50); shape.FillColor = System.Drawing.Color.LightGray;'
  type: HowTo
- questions:
  - answer: No. Hidden shapes are ignored by the layout engine, so they do not consume
      space. This is useful for placeholder content that should not affect page breaks.
    question: Does hiding a shape affect pagination?
  - answer: Yes. The same `Hidden` property works on shapes located anywhere in the
      document tree, including headers, footers, and even inside tables.
    question: Can I hide a shape that is part of a header or footer?
  - answer: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` for each target shape. ```csharp foreach (Shape s in
      doc.GetChildNodes(NodeType.Shape, true)) { if (s.ShapeType == ShapeType.Rectangle)
      s.Hidden = true; } ```
    question: What if I need to hide multiple shapes at once?
  - answer: 'When converting to PDF, hidden shapes are omitted by default, matching
      Word’s rendering behavior. If you need them in the PDF, you must unhide them
      before conversion. ## Tips and pitfalls * **Pro tip:** Set `shape.WrapType =
      WrapType.None` before hiding if you later plan to unhide the shape without '
    question: Is the hidden attribute preserved when converting to PDF?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Word automation
title: Como ocultar forma no Word com C# e Aspose.Words
url: /pt/java/images-shapes/how-to-hide-shape-in-word-with-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como ocultar forma no Word com C# e Aspose.Words

Se você precisa ocultar uma forma no Word mantendo-a na estrutura do documento, este tutorial mostra exatamente como fazer isso. Usando Aspose.Words para .NET, você pode inserir uma forma retangular, ocultá‑la e ainda manter sua posição para processamento posterior.

A automação do Word costuma exigir controle fino sobre as formas — seja ao gerar modelos, preparar relatórios ou construir um serviço de edição de documentos. Ao final deste guia você será capaz de:

* Inserir uma forma retangular em um documento Word (`insert rectangle shape`).
* Ocultar qualquer forma sem excluí‑la (`how to hide shape in word`).
* Salvar o resultado e verificar que a forma oculta não aparece na visualização renderizada (`insert shape into word document`).

O exemplo funciona com Aspose.Words 24.10 ou posterior e tem como alvo .NET 6.0+, mas os conceitos se aplicam a versões anteriores também.

## Pré‑requisitos

* **Aspose.Words para .NET** ≥ 24.10. Você pode obter uma licença temporária gratuita no site da Aspose.
* **.NET SDK** 6.0 ou mais recente instalado na sua máquina.
* Um ambiente de desenvolvimento como Visual Studio 2022, VS Code ou Rider.
* Familiaridade básica com C# e o conceito Word Open XML (opcional, mas útil).

## Como ocultar forma no Word com Aspose.Words

A seguir, um programa completo e executável que demonstra todo o fluxo — desde a criação do documento até a inserção de uma forma retangular e, finalmente, sua ocultação.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HideShapeDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a rectangle shape (100 × 50 points) at the current cursor position.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        // Optional: give the shape a visible fill so you can see it before hiding.
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Hide the shape without removing it from the document.
        // The Hidden property is available starting with Aspose.Words 24.10.
        rectangle.Hidden = true;

        // Step 4: Save the document to disk.
        string outputPath = "output.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}. The rectangle shape is hidden.");
    }
}
```

### Explicação de cada etapa

1. **Criar um novo documento** – `Document` representa o arquivo Word na memória. `DocumentBuilder` fornece uma API fluente para inserção de conteúdo.  
2. **Inserir forma retangular** – `InsertShape` cria um objeto de desenho do tipo `Rectangle`. As dimensões são expressas em pontos (1 pt ≈ 1/72 in). Isso satisfaz o requisito `insert rectangle shape`.  
3. **Ocultar a forma** – Definir `Shape.Hidden = true` marca a forma como oculta na marcação Word (`<w:hidden/>`). A forma permanece parte da árvore do documento, podendo ser revelada depois ou referenciada programaticamente. Este é o núcleo de `how to hide shape in word`.  
4. **Salvar o arquivo** – O documento é gravado em `output.docx`. Ao ser aberto no Microsoft Word, o retângulo não será visível, mas ainda existirá no XML e pode ser inspecionado com um visualizador ZIP ou o Open XML SDK.

### Resultado esperado

Abra `output.docx` no Microsoft Word:

* O documento aparece vazio — nenhuma forma visível.  
* Se você inspecionar o XML subjacente (`word/document.xml`) encontrará um elemento `<w:pict>` com o atributo `<w:hidden/>`, confirmando que a forma está presente, porém oculta.

```xml
<w:pict>
  <v:shape id="Shape0" style="position:absolute; ...">
    <v:fillcolor>#ADD8E6</v:fillcolor>
    <w:hidden/>
  </v:shape>
</w:pict>
```

A forma oculta pode ser tornada visível novamente definindo `Hidden = false` e salvando o documento novamente.

## Inserir forma retangular em um documento Word

Embora o objetivo principal seja ocultar uma forma, muitos cenários começam inserindo a forma primeiro. O método `InsertShape` aceita diversos valores de `ShapeType`, incluindo `Rectangle`, `Ellipse`, `Line` e imagens personalizadas.

```csharp
// Example: Insert an ellipse shape and keep it visible.
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
ellipse.FillColor = System.Drawing.Color.Pink;
```

**Por que usar um retângulo?**  
Um retângulo fornece um contêiner limpo, alinhado aos eixos, que pode conter texto, imagens ou outras formas aninhadas. Ele costuma ser usado como placeholder para conteúdo dinâmico, como tabelas ou gráficos. Ao inserir o retângulo primeiro, você preserva a consistência do layout mesmo depois de ocultá‑lo.

## Inserir forma em documento Word — boas práticas

Ao `insert shape into word document`, considere o seguinte:

* **Defina dimensões explícitas** – Evite depender de dimensionamento automático; especifique largura e altura em pontos para garantir layout consistente em todas as plataformas.  
* **Defina o posicionamento** – Por padrão, a forma é ancorada ao parágrafo atual. Use `builder.MoveTo` ou `builder.StartBookmark` para posicioná‑la com precisão.  
* **Aplique estilos cedo** – Cor de preenchimento, estilo de linha e quebra de texto afetam a aparência final. Mesmo formas ocultas se beneficiam de um estilo adequado, pois a marcação permanece inalterada.  
* **Compatibilidade de versão** – A propriedade `Hidden` está disponível apenas a partir do Aspose.Words 24.10. Se você direcionar uma versão mais antiga, pode adicionar manualmente o atributo `<w:hidden/>` usando a API `Node`.

### Adicionando manualmente o atributo hidden (fallback)

```csharp
// Fallback for Aspose.Words versions prior to 24.10
Shape shape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
shape.FillColor = System.Drawing.Color.LightGray;

// Access the underlying OpenXml node.
var shapeNode = shape.GetChildNodes(NodeType.Any, true)[0];
shapeNode.GetAttributes().Add("w:hidden", "true");
```

## Exemplo completo de ponta a ponta

Juntando tudo, segue um programa único que:

1. Insere uma forma retangular.  
2. Oculta a forma.  
3. Insere uma elipse visível como contraste.  
4. Salva o documento.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class FullDemo
{
    static void Main()
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert and hide a rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 120, 60);
        rect.FillColor = System.Drawing.Color.LightGreen;
        rect.Hidden = true; // core of how to hide shape in word

        // Insert a visible ellipse to show the difference.
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.FillColor = System.Drawing.Color.Coral;

        // Save the output.
        string filePath = "demo_output.docx";
        doc.Save(filePath);
        Console.WriteLine($"Demo document saved to {filePath}");
    }
}
```

Executar o programa gera `demo_output.docx`. Ao abrir, você verá apenas a elipse coral; o retângulo verde está presente no XML, porém oculto na visualização.

## Perguntas frequentes e casos de borda

**P: Ocultar uma forma afeta a paginação?**  
R: Não. Formas ocultas são ignoradas pelo motor de layout, portanto não consomem espaço. Isso é útil para conteúdo placeholder que não deve influenciar quebras de página.

**P: Posso ocultar uma forma que faça parte do cabeçalho ou rodapé?**  
R: Sim. A mesma propriedade `Hidden` funciona em formas localizadas em qualquer ponto da árvore do documento, incluindo cabeçalhos, rodapés e até dentro de tabelas.

**P: E se eu precisar ocultar várias formas de uma vez?**  
R: Percorra a coleção `Document.GetChildNodes(NodeType.Shape, true)` e defina `Hidden = true` para cada forma alvo.

```csharp
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.ShapeType == ShapeType.Rectangle)
        s.Hidden = true;
}
```

**P: O atributo hidden é preservado ao converter para PDF?**  
R: Ao converter para PDF, formas ocultas são omitidas por padrão, reproduzindo o comportamento de renderização do Word. Se precisar delas no PDF, desoculte‑as antes da conversão.

## Dicas e armadilhas

* **Dica profissional:** Defina `shape.WrapType = WrapType.None` antes de ocultar se pretender revelar a forma depois sem perturbar o texto ao redor.  
* **Cuidado com versões antigas do Aspose.Words:** A propriedade `Hidden` lança `NotSupportedException` antes da 24.10. Use a abordagem manual de XML nesses casos.  
* **Testes:** Sempre abra o `.docx` gerado no Word e use “Show XML markup” (aba Desenvolvedor) para confirmar que o atributo `<w:hidden/>` está presente.

## Conclusão

Agora você sabe como ocultar forma no Word usando C# e Aspose.Words, além de como inserir forma retangular e inserir forma em documento Word com controle total sobre a visibilidade. Ao aproveitar a propriedade `Hidden`, você pode manter formas no modelo de documento para processamento posterior, apresentando uma visualização limpa ao usuário final.

Em seguida, explore tópicos relacionados como **atualizar propriedades de forma em tempo de execução**, **converter formas ocultas em imagens**, ou **usar o Open XML SDK para manipular elementos ocultos diretamente**. Essas extensões aprofundarão seu domínio.

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas em seus próprios projetos.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}