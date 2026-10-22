---
category: general
date: 2026-09-05
description: Crie uma forma de retângulo em um documento Word usando Aspose.Words,
  depois aprenda como inserir uma elipse e agrupar formas no Word para layouts mais
  ricos.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- how to insert rectangle word
- how to insert ellipse word
- aspose.words create shapes
language: pt
lastmod: 2026-09-05
og_description: Crie uma forma retangular em um documento Word com Aspose.Words, depois
  veja como inserir uma elipse e agrupar formas no Word para layouts complexos.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with Aspose.Words
og_title: Criar forma de retângulo e agrupar formas no Word – Guia Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create rectangle shape in a Word document using Aspose.Words, then
    learn how to insert ellipse word and group shapes in Word for richer layouts.
  headline: How to create rectangle shape and group shapes in Word with Aspose.Words
  type: TechArticle
- description: Create rectangle shape in a Word document using Aspose.Words, then
    learn how to insert ellipse word and group shapes in Word for richer layouts.
  name: How to create rectangle shape and group shapes in Word with Aspose.Words
  steps:
  - name: Pro tip
    text: Always add shapes **before** you group them. If you try to group a shape
      that is already part of another group, Aspose.Words throws an `ArgumentException`.
      Building the group in a single method prevents this runtime error.
  - name: Watch out for
    text: '* **Coordinate system** – `Left` and `Top` are measured from the page’s
      left and top margins, not from the document edge. Misunderstanding this can
      place shapes off‑page. * **Licensing** – Without a valid license, the saved
      document will contain a watermark that says “Aspose.Words for .NET Evaluatio'
  - name: What’s next?
    text: '* Explore **aspose.words create shapes** for more complex geometry such
      as `Polygon` or `Freeform`. * Combine grouped shapes with **content controls**
      to build dynamic templates. * Convert the DOCX to PDF or HTML to see how vector
      shapes are rendered across formats.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Como criar forma retangular e agrupar formas no Word com Aspose.Words
url: /pt/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar forma retangular e agrupar formas no Word com Aspose.Words

Se você precisa **criar forma retangular** em um documento Word, este guia mostra os passos exatos com Aspose.Words para .NET. Você também verá como inserir elipse, agrupar formas no Word e salvar o resultado como um arquivo DOCX. A solução funciona em qualquer projeto .NET 6+ e não requer o Microsoft Office instalado no servidor.

O tutorial cobre tudo, desde a configuração do projeto até o tratamento de armadilhas comuns de layout, para que você possa copiar o código e executá‑lo imediatamente.

## Pré-requisitos

* .NET 6 SDK ou posterior instalado  
* Uma IDE compatível com NuGet (Visual Studio, Rider ou VS Code)  
* Uma licença do Aspose.Words para .NET (ou uma chave de avaliação temporária)  
* Conhecimento básico de C# e da estrutura de documentos Word  

Esses itens permitem que o código compile e que as formas sejam renderizadas corretamente.

## Etapa 1: Configurar o projeto e adicionar Aspose.Words

Crie um novo projeto de console e adicione o pacote Aspose.Words:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

O pacote fornece as classes `Document`, `DocumentBuilder`, `Shape` e `GroupShape` usadas ao longo deste tutorial.

## Etapa 2: Inicializar um documento em branco e um builder

O objeto `Document` representa todo o arquivo Word, enquanto `DocumentBuilder` permite inserir conteúdo programaticamente.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

Document doc = new Document();                 // creates an empty .docx container
DocumentBuilder builder = new DocumentBuilder(doc);
```

Criar o documento primeiro garante que todas as operações subsequentes de forma tenham um contêiner válido.

## Etapa 3: **Criar forma retangular** e definir suas dimensões

Um retângulo é o contêiner mais comum para texto ou imagens. Você define seu tamanho em pontos (1 pt ≈ 1/72 polegada).

```csharp
// create a rectangle shape
Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
rectangleShape.Width = 100;      // 100 pt ≈ 1.39 in
rectangleShape.Height = 50;      // 50 pt ≈ 0.69 in

// optional: give the rectangle a light fill and a thin border
rectangleShape.FillColor = System.Drawing.Color.LightGray;
rectangleShape.Line.Width = 0.5;

// insert the rectangle into the document at the current cursor position
builder.InsertNode(rectangleShape);
```

Por que esta etapa é importante: a classe `Shape` encapsula geometria, preenchimento e propriedades de linha. Definir `Width` e `Height` antes da inserção garante que a forma apareça com o tamanho esperado.

## Etapa 4: **Como inserir elipse** – adicionar uma forma elíptica

Uma elipse pode ser usada para ícones, marcadores ou elementos decorativos. O código espelha a criação do retângulo, apenas o `ShapeType` muda.

```csharp
// create an ellipse shape
Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
ellipseShape.Width = 80;      // 80 pt ≈ 1.11 in
ellipseShape.Height = 80;     // a perfect circle because width = height

// style the ellipse
ellipseShape.FillColor = System.Drawing.Color.CornflowerBlue;
ellipseShape.Line.Color = System.Drawing.Color.DarkBlue;

// place the ellipse after the rectangle
builder.InsertNode(ellipseShape);
```

As propriedades `FillColor` e `Line.Color` ilustram como personalizar a aparência sem imagens externas.

## Etapa 5: **Agrupar formas no Word** – combinar retângulo e elipse

Agrupar permite mover, redimensionar ou girar várias formas como uma única unidade. Isso é essencial quando você precisa de um gráfico composto (por exemplo, um ícone rotulado).

```csharp
// create a group shape container
GroupShape groupShape = new GroupShape(doc);

// add the previously created shapes to the group
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);

// optional: set the group's position on the page
groupShape.Left = 150;   // distance from the left margin in points
groupShape.Top = 100;    // distance from the top margin in points

// insert the grouped shape into the document
builder.InsertNode(groupShape);
```

Ao chamar `AppendChild`, as formas originais são removidas do fluxo principal do documento e se tornam filhas do `GroupShape`. O grupo se comporta como uma única forma, o que simplifica ajustes de layout posteriores.

## Etapa 6: Salvar o documento

Finalmente, grave o documento no disco. Você pode escolher qualquer formato suportado (`.docx`, `.pdf`, `.html`, etc.). Para este tutorial, mantemos o formato Word nativo.

```csharp
// replace "YOUR_DIRECTORY" with an absolute or relative path you control
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Depois de executar o programa, abra *GroupShape.docx* no Microsoft Word. Você verá um retângulo e uma elipse agrupados, posicionados nas coordenadas que você especificou.

## Variações comuns e casos de borda

| Situação | O que mudar | Motivo |
|-----------|----------------|--------|
| **Unidades de tamanho diferentes** | Use `ConvertUtil.InchToPoint(2.5)` para polegadas ou `ConvertUtil.MillimeterToPoint(30)` para milímetros. | Mantém o código legível quando você trabalha com medidas que não são em pontos. |
| **Adicionar texto dentro do retângulo** | Crie um nó `Paragraph`, defina sua propriedade `Text` e adicione‑o ao `rectangleShape` via `AppendChild`. | Permite rotular a forma sem caixas de texto separadas. |
| **Rotacionar o grupo** | Defina `groupShape.Rotation = 45;` (graus). | Útil para criar emblemas ou marcas d'água diagonais. |
| **Salvar como PDF** | Chame `doc.Save("GroupShape.pdf");`. | Aspose.Words rasteriza automaticamente formas vetoriais para saída em PDF. |
| **Múltiplos grupos** | Crie instâncias adicionais de `GroupShape` e repita as etapas de append/insert. | Permite layouts de página complexos com vários compostos independentes. |

### Dica profissional

Sempre adicione formas **antes** de agrupá‑las. Se você tentar agrupar uma forma que já faz parte de outro grupo, Aspose.Words lança um `ArgumentException`. Construir o grupo em um único método impede esse erro em tempo de execução.

### Atenção a

* **Sistema de coordenadas** – `Left` e `Top` são medidos a partir das margens esquerda e superior da página, não da borda do documento. Um entendimento incorreto pode posicionar as formas fora da página.  
* **Licenciamento** – Sem uma licença válida, o documento salvo conterá uma marca d'água que diz “Aspose.Words for .NET Evaluation”. Aplique sua licença cedo no código (`License license = new License(); license.SetLicense("Aspose.Words.lic");`) para evitá‑la.

## Código-fonte completo (executável)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Create rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
        rectangleShape.Width = 100;
        rectangleShape.Height = 50;
        rectangleShape.FillColor = System.Drawing.Color.LightGray;
        rectangleShape.Line.Width = 0.5;
        builder.InsertNode(rectangleShape);

        // 3️⃣ Create ellipse shape
        Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
        ellipseShape.Width = 80;
        ellipseShape.Height = 80;
        ellipseShape.FillColor = System.Drawing.Color.CornflowerBlue;
        ellipseShape.Line.Color = System.Drawing.Color.DarkBlue;
        builder.InsertNode(ellipseShape);

        // 4️⃣ Group rectangle and ellipse
        GroupShape groupShape = new GroupShape(doc);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        groupShape.Left = 150;
        groupShape.Top = 100;
        builder.InsertNode(groupShape);

        // 5️⃣ Save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Executar este programa produz *GroupShape.docx* com as formas agrupadas exatamente como descrito.

## Conclusão

Agora você sabe como **criar forma retangular**, **como inserir elipse** e **agrupar formas no Word** usando Aspose.Words. O exemplo completo demonstra o fluxo de trabalho completo — desde a inicialização de um documento até a gravação do arquivo final — para que você possa integrar o manuseio de formas em qualquer solução automatizada de relatórios ou geração de documentos.

### O que vem a seguir?

* Explore **aspose.words create shapes** para geometria mais complexa, como `Polygon` ou `Freeform`.  
* Combine formas agrupadas com **content controls** para criar modelos dinâmicos.  
* Converta o DOCX para PDF ou HTML para ver como as formas vetoriais são renderizadas em diferentes formatos.  

Sinta‑se à vontade para experimentar diferentes tamanhos, cores e rotações. Quando você dominar o agrupamento de formas, poderá criar diagramas sofisticados, emblemas e elementos de UI personalizados diretamente dentro de documentos Word.

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Criar Forma de Grupo em Documento Word Usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Inserir Formas em Documentos Word Usando Aspose.Words para .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Criar forma retangular no Word usando C# – Guia passo a passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}