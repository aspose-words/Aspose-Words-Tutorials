---
category: general
date: 2026-10-23
description: Crie um documento Word em branco, adicione uma forma retangular e oculte
  a forma no Word usando Aspose.Words. Código passo a passo para desenvolvedores .NET.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- how to insert shape
- hide shape word
language: pt
lastmod: 2026-10-23
og_description: Crie um documento Word em branco, adicione uma forma retangular e
  oculte a forma no Word com Aspose.Words. Siga o exemplo completo em C#.
og_image_alt: Screenshot of a Word document containing a hidden rectangle shape
og_title: Crie um documento Word em branco e adicione uma forma de retângulo oculta
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Create a blank Word document, add a rectangle shape, and hide the shape
    in Word using Aspose.Words. Step‑by‑step code for .NET developers.
  headline: Create a blank Word document and add a rectangle shape
  type: TechArticle
tags:
- Aspose.Words
- .NET
- Word automation
title: Crie um documento Word em branco e adicione uma forma de retângulo
url: /pt/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar um documento Word em branco e adicionar uma forma retangular

Se você precisar **criar um documento Word em branco**, este guia mostra como fazer isso com Aspose.Words for .NET. Você também aprenderá **como inserir forma** — especificamente um retângulo — e **ocultar forma no Word** para que não afete o layout.

O tutorial percorre cada linha de código, explica por que cada etapa é importante e aborda armadilhas comuns, como a visibilidade de formas ocultas em diferentes modos de visualização do Word. Ao final, você terá um arquivo `.docx` totalmente funcional que contém uma forma retangular oculta que pode ser revelada ou manipulada programaticamente.

## Pré-requisitos

- .NET 6.0 ou posterior (o código também funciona com .NET Framework 4.6+)
- Pacote NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)
- Um ambiente de desenvolvimento como Visual Studio 2022 ou VS Code com extensões C#
- Familiaridade básica com a sintaxe C# e conceitos de documentos Word

Nenhuma instalação adicional do Office é necessária porque o Aspose.Words funciona completamente na memória.

## Criar um documento Word em branco

O primeiro passo é instanciar um objeto `Document` vazio. Esse objeto representa um arquivo Word que ainda não contém seções, parágrafos ou conteúdo ainda.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document
Document document = new Document();
```

**Por que isso importa:**  
Um `Document` em branco fornece uma tela limpa. Se você começar a partir de um modelo existente, formas ocultas podem herdar estilos indesejados. Começar do zero garante que a forma retangular que você adicionará posteriormente seja o único conteúdo que você controla.

## Adicionar uma forma retangular ao documento

Em seguida, precisamos de um `DocumentBuilder` para colocar conteúdo no documento. O método `InsertShape` do builder é a forma padrão **de inserir forma** objetos, como retângulos, círculos ou desenhos personalizados.

```csharp
// Step 2: Initialize a DocumentBuilder to add content
DocumentBuilder builder = new DocumentBuilder(document);

// Step 3: Insert a rectangle shape of size 200x100 points
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

**Por que isso importa:**  
`InsertShape` retorna um objeto `Shape` que você pode configurar ainda mais (cor, estilo de linha, etc.). As dimensões são fornecidas em pontos (1 ponto = 1/72 polegada), que corresponde ao sistema de medição interno do Word.

### Opcional: estilizar o retângulo (opcional)

Se você quiser que o retângulo tenha uma borda visível quando você o revelar posteriormente, pode definir sua espessura de linha e cor:

```csharp
rectangleShape.LineWeight = 0.5;               // Thin border
rectangleShape.LineColor = System.Drawing.Color.Blue;
```

Essas linhas são opcionais porque a forma será ocultada na próxima etapa.

## Ocultar a forma no Word

O Word permite que formas sejam ocultadas do layout enquanto ainda fazem parte do modelo de objetos do documento. Definir a propriedade `Hidden` como `true` torna a forma invisível na visualização normal, mas ainda selecionável via API.

```csharp
// Step 4: Hide the shape so it does not appear in the layout
rectangleShape.Hidden = true;
```

**Por que isso importa:**  
Uma forma oculta é útil para armazenar metadados, marcadores de posição para processamento posterior ou conteúdo condicional que você revela apenas sob certas circunstâncias (por exemplo, ao gerar um relatório final). A forma permanece no arquivo, de modo que você pode revelá‑la programaticamente mais tarde com `rectangleShape.Hidden = false;`.

## Salvar o documento

Finalmente, grave o documento no disco. A extensão do arquivo determina o formato Word; `.docx` é o formato Open XML moderno.

```csharp
// Step 5: Save the document with the hidden shape
string outputPath = @"C:\Temp\HiddenShape.docx";
document.Save(outputPath);
```

**Resultado:**  
Abrir `HiddenShape.docx` no Microsoft Word mostra uma página vazia. O retângulo não é visível, mas se você for em **Início → Selecionar → Painel de Seleção**, verá a forma listada e poderá alternar sua visibilidade.

## Exemplo completo em funcionamento

Abaixo está o programa completo que você pode copiar, colar e executar. Ele inclui todas as declarações `using` necessárias e comentários.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document
        Document document = new Document();

        // Initialize a DocumentBuilder for content insertion
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a rectangle shape (200x100 points)
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // Optional styling (comment out if not needed)
        rectangleShape.LineWeight = 0.5;
        rectangleShape.LineColor = System.Drawing.Color.Blue;

        // Hide the shape so it does not appear in the layout
        rectangleShape.Hidden = true;

        // Save the document
        string outputPath = @"C:\Temp\HiddenShape.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Saída esperada:**  

- O console imprime o caminho de salvamento.  
- `HiddenShape.docx` abre como uma página em branco no Word.  
- A forma retangular existe, mas está oculta; você pode verificá‑la via *Painel de Seleção* ou definindo programaticamente `Hidden = false` e reabrindo o arquivo.

## Perguntas comuns e casos extremos

| Pergunta | Resposta |
|----------|----------|
| **Posso ocultar outros tipos de forma?** | Sim. Qualquer `Shape` (por exemplo, `ShapeType.Ellipse`, `ShapeType.Picture`) suporta a propriedade `Hidden`. |
| **A forma oculta aumentará o tamanho do arquivo?** | O aumento é insignificante (alguns kilobytes) porque os dados da forma são armazenados como XML no pacote `.docx`. |
| **E se eu precisar que a forma apareça apenas na visualização de impressão?** | Use a propriedade `Shape.IsPrint` em vez de `Hidden`. Definir `IsPrint = false` oculta a forma da saída impressa, mas mantém‑a visível na tela. |
| **Como revelar a forma mais tarde?** | Carregue o documento, localize a forma (por exemplo, por `Shape.Name`), então defina `shape.Hidden = false;` e salve. |
| **Isso funciona com o formato .doc (binário)?** | Sim, o Aspose.Words pode salvar em `.doc` usando `document.Save("file.doc");`. O sinalizador oculto é preservado. |

## Dicas profissionais

- **Nomeie suas formas**: `rectangleShape.Name = "PlaceholderRectangle";` facilita encontrá‑las mais tarde via `document.GetChildNodes(NodeType.Shape, true).Cast<Shape>().FirstOrDefault(s => s.Name == "PlaceholderRectangle")`.
- **Processamento em lote**: Se precisar adicionar formas ocultas a muitos documentos, encapsule o código em um método e reutilize a instância `DocumentBuilder`.
- **Desempenho**: Criar uma forma é barato, mas salvar documentos grandes com frequência pode ser limitado por I/O. Considere usar `MemoryStream` para processamento intermediário.

## Conclusão

Agora você sabe como **criar um documento Word em branco**, **adicionar uma forma retangular** e **ocultar forma no Word** usando Aspose.Words for .NET. Essa técnica permite incorporar marcadores de posição invisíveis que podem ser revelados ou manipulados posteriormente, um padrão útil para geração dinâmica de relatórios, conteúdo condicional e modelagem de documentos.

Próximos passos que você pode explorar:

- Substituir o retângulo por uma imagem ou gráfico usando `ShapeType.Picture`.
- Usar **como inserir forma** nas seções de cabeçalho/rodapé para marcadores de posição estilo marca d'água.
- Combinar formas ocultas com validação de dados baseada em **adicionar forma retangular** (por exemplo, armazenando JSON na propriedade `AlternativeText` de uma forma).

Feliz codificação, e sinta-se à vontade para experimentar outros tipos de forma e opções de visibilidade para atender às suas necessidades de automação de documentos!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Criar documento Word – Como adicionar forma retangular e sombra](/words/english/net/programming-with-shapes/create-word-document-how-to-add-rectangle-shape-and-shadow/)
- [Criar forma de grupo em documento Word usando Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Criar um documento Word em branco com forma elipse oculta – Guia completo em C#](/words/english/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}