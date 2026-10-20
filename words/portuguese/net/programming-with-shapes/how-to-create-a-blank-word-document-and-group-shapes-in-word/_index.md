---
category: general
date: 2026-10-20
description: Aprenda como criar um documento Word em branco, agrupar formas no Word,
  definir a cor de preenchimento da forma e usar o tipo de ajuste em linha com um
  exemplo completo em C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- how to group shapes
- set shape fill color
- wrap type inline
language: pt
lastmod: 2026-10-20
og_description: Crie um documento Word em branco, agrupe formas no Word e defina a
  cor de preenchimento da forma com tipo de ajuste inline usando Aspose.Words e C#.
  Siga o tutorial completo.
og_image_alt: Screenshot of a blank Word document containing a grouped rectangle and
  text box created with Aspose.Words
og_title: Crie um documento Word em branco e agrupe formas no Word – guia passo a
  passo
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Learn how to create a blank Word document, group shapes in Word, set
    shape fill color, and use wrap type inline with a complete C# example.
  headline: How to create a blank Word document and group shapes in Word using Aspose.Words
  type: TechArticle
- description: Learn how to create a blank Word document, group shapes in Word, set
    shape fill color, and use wrap type inline with a complete C# example.
  name: How to create a blank Word document and group shapes in Word using Aspose.Words
  steps:
  - name: Expected result
    text: '* A .docx file containing a single paragraph. * Inside the paragraph, an
      inline group that looks like a single composite object. * The rectangle is filled
      with light blue, and the text box displays “Grouped text”.'
  - name: What if I need the group to float rather than be inline?
    text: Replace `WrapType.Inline` with `WrapType.TopBottom` (or any other `WrapType`
      enum value). Floating groups can be positioned independently of paragraph flow,
      but they lose the automatic inline alignment.
  - name: Can I add more shapes, such as circles or images?
    text: Yes. Create additional `Shape` objects with `ShapeType.Ellipse` or `ShapeType.Image`,
      configure their properties, and call `group.AppendChild(newShape)`. The group
      will automatically expand to accommodate the new bounds if you update `group.Bounds`
      accordingly.
  - name: How do I change the group’s overall size after adding children?
    text: Adjust `group.Bounds` after all children are appended, or compute the union
      of child bounds programmatically. This ensures the group’s hit‑test area matches
      the visual content.
  - name: What if the output folder does not exist?
    text: 'Aspose.Words throws a `DirectoryNotFoundException`. Create the directory
      first:'
  - name: Does this work with .NET Framework instead of .NET Core?
    text: All APIs used (`Document`, `DocumentBuilder`, `GroupShape`, `Shape`) are
      available in the .NET Framework version of Aspose.Words, so the same code works
      unchanged.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Como criar um documento Word em branco e agrupar formas no Word usando Aspose.Words
url: /pt/net/programming-with-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar um documento Word em branco e agrupar formas no Word

Se você precisa **criar um documento Word em branco** que contém várias formas atuando como uma única unidade, este guia mostra exatamente como fazer. Você verá como **agrupar formas no Word**, definir a cor de preenchimento de uma forma e aplicar **wrap type inline** — tudo com um programa C# conciso e executável.

O tutorial percorre cada linha de código, explica por que cada passo é importante e destaca armadilhas comuns. Ao final, você terá um arquivo .docx que exibe um retângulo e uma caixa de texto agrupados, pronto para automação adicional.

## O que você aprenderá

* Como inicializar um arquivo Word vazio com Aspose.Words.  
* A maneira correta de criar um **GroupShape** e adicionar formas filhas.  
* Técnicas para **set shape fill color** e controle de posicionamento.  
* Uso de **wrap type inline** para que o grupo se comporte como um único objeto inline.  
* Como salvar e verificar o resultado.  

Nenhuma experiência prévia com Aspose.Words é necessária, mas você deve estar confortável com a sintaxe básica de C# e ter o Visual Studio (ou outra IDE) instalado.

## Pré‑requisitos

| Requisito | Motivo |
|-----------|--------|
| .NET 6.0 ou superior | Fornece o runtime para o projeto C#. |
| Aspose.Words for .NET (versão mais recente) | Disponibiliza as classes `Document`, `DocumentBuilder` e de formas usadas no exemplo. |
| Um caminho de pasta gravável | A chamada `doc.Save` precisa de um diretório válido para gravar o arquivo de saída. |
| Conhecimento básico de C# | Permite que você siga o código e o modifique para seus próprios cenários. |

Instale o Aspose.Words via NuGet:

```bash
dotnet add package Aspose.Words
```

---

## Etapa 1: Criar um documento Word em branco

A primeira operação é **criar um documento Word em branco**. A classe `Document` do Aspose.Words representa um arquivo Word em memória, e `DocumentBuilder` fornece uma API conveniente para editá‑lo.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Initialize a new empty document.
Document doc = new Document();

// Attach a builder to the document for easy content insertion.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Por que isso importa*: Começar com um documento limpo garante que a forma de grupo que você adicionar será o único conteúdo, facilitando a verificação.

## Etapa 2: Definir um GroupShape com wrap type inline

Um **GroupShape** funciona como um contêiner para outras formas. Definir seu `WrapType` como `Inline` assegura que o grupo se comporte como um único objeto inline no fluxo do parágrafo.

```csharp
// Create a group shape that will hold the rectangle and text box.
GroupShape group = new GroupShape(doc, WrapType.Inline);

// Define the bounding rectangle of the group (x, y, width, height).
group.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
```

*Por que isso importa*: Usar **wrap type inline** impede que o grupo flutue longe do texto ao redor, o que é essencial quando você deseja que o grupo se mova como uma unidade.

## Etapa 3: Adicionar um retângulo e definir a cor de preenchimento da forma

Um retângulo é um elemento visual comum. O construtor `Shape` recebe um `ShapeType`; em seguida, especificamos dimensões e cor de preenchimento.

```csharp
// Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width = 150,
    Height = 100,
    FillColor = System.Drawing.Color.LightBlue
};

// Append the rectangle to the group.
group.AppendChild(rectangle);
```

*Por que isso importa*: A propriedade `FillColor` demonstra **set shape fill color** na prática, dando ao retângulo um fundo azul‑claro que se destaca no documento final.

## Etapa 4: Adicionar uma caixa de texto – como agrupar formas efetivamente

Uma caixa de texto fornece texto editável dentro do grupo. Posicione‑a em relação ao sistema de coordenadas do grupo ajustando a propriedade `Top`.

```csharp
// Create a text box shape.
Shape textBox = new Shape(doc, ShapeType.TextBox)
{
    Width = 120,
    Height = 60,
    TextBoxText = "Grouped text",
    Top = 110 // Position below the rectangle inside the group.
};

// Append the text box to the group.
group.AppendChild(textBox);
```

*Por que isso importa*: Esta etapa responde **how to group shapes** — adicionando cada forma filha à mesma instância de `GroupShape`. O deslocamento `Top` garante que a caixa de texto apareça abaixo do retângulo, demonstrando controle preciso de layout.

## Etapa 5: Inserir o GroupShape concluído no documento

Agora que o grupo contém ambas as formas filhas, insira‑o na posição atual do builder.

```csharp
// Insert the group shape at the builder’s cursor location.
builder.InsertNode(group);
```

*Por que isso importa*: Inserir o grupo como um único nó garante que o Word trate o retângulo e a caixa de texto como um objeto lógico único, preservando suas posições relativas durante a edição.

## Etapa 6: Salvar o documento e verificar a saída

Finalmente, grave o documento no disco. Substitua `YOUR_DIRECTORY` por um caminho real na sua máquina.

```csharp
// Save the document to the specified folder.
doc.Save("YOUR_DIRECTORY/GroupShape.docx");
```

Ao abrir `GroupShape.docx` no Microsoft Word, você deverá ver um retângulo azul‑claro com uma caixa de texto rotulada “Grouped text” posicionada diretamente abaixo dele. Selecionar qualquer uma das formas selecionará todo o grupo, confirmando que **group shapes in Word** funciona como esperado.

### Resultado esperado

* Um arquivo .docx contendo um único parágrafo.  
* Dentro do parágrafo, um grupo inline que parece um único objeto composto.  
* O retângulo está preenchido com azul‑claro, e a caixa de texto exibe “Grouped text”.  

![Screenshot of the generated Word document](grouped_shapes.png){.center width=600 alt="Captura de tela de um documento Word em branco com retângulo agrupado e caixa de texto criada usando Aspose.Words"}

## Perguntas comuns e tratamento de casos limites

### E se eu precisar que o grupo flutue em vez de ser inline?

Substitua `WrapType.Inline` por `WrapType.TopBottom` (ou qualquer outro valor do enum `WrapType`). Grupos flutuantes podem ser posicionados independentemente do fluxo do parágrafo, mas perdem o alinhamento automático inline.

### Posso adicionar mais formas, como círculos ou imagens?

Sim. Crie objetos `Shape` adicionais com `ShapeType.Ellipse` ou `ShapeType.Image`, configure suas propriedades e chame `group.AppendChild(newShape)`. O grupo expandirá automaticamente para acomodar os novos limites se você atualizar `group.Bounds` adequadamente.

### Como altero o tamanho geral do grupo após adicionar as filhas?

Ajuste `group.Bounds` depois que todas as filhas forem adicionadas, ou calcule a união dos limites das filhas programaticamente. Isso garante que a área de teste de clique do grupo corresponda ao conteúdo visual.

### E se a pasta de saída não existir?

Aspose.Words lança uma `DirectoryNotFoundException`. Crie a pasta primeiro:

```csharp
string outputPath = "YOUR_DIRECTORY";
Directory.CreateDirectory(outputPath);
doc.Save(Path.Combine(outputPath, "GroupShape.docx"));
```

### Isso funciona com .NET Framework em vez de .NET Core?

Todas as APIs usadas (`Document`, `DocumentBuilder`, `GroupShape`, `Shape`) estão disponíveis na versão .NET Framework do Aspose.Words, portanto o mesmo código funciona sem alterações.

## Dicas profissionais

* **Dica de desempenho** – Reuse uma única instância de `DocumentBuilder` ao inserir muitos grupos; criar um novo builder por grupo adiciona sobrecarga.  
* **Consistência visual** – Defina `rectangle.StrokeColor` para combinar com `FillColor` para um visual uniforme, ou ajuste `rectangle.LineWidth = 0` para ocultar a borda.  
* **Depuração** – Chame `doc.UpdatePageLayout()` antes de salvar se você modificar muitas formas; isso força o Word a recalcular o layout e pode evitar recortes inesperados.  

## Conclusão

Agora você sabe como **criar um documento Word em branco**, **agrupar formas no Word**, **definir a cor de preenchimento da forma** e aplicar **wrap type inline** usando Aspose.Words para .NET. O exemplo completo demonstra a abordagem padrão para construir gráficos compostos que se comportam como um único objeto no Word.

A partir daqui, você pode explorar:

* Adicionar formas adicionais, como imagens ou gráficos.  
* Experimentar diferentes valores de `WrapType` para grupos flutuantes.  
* Automatizar a geração em lote de diagramas agrupados em vários documentos.  

Sinta‑se à vontade para adaptar o código aos seus próprios cenários de automação e compartilhar seus resultados nos comentários!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [How to Save PDF from Word with Inline Shapes – Complete Guide](/words/english/java/document-conversion-and-export/how-to-save-pdf-from-word-with-inline-shapes-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}