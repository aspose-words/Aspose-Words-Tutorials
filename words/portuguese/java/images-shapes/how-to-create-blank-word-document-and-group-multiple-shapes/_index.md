---
category: general
date: 2026-10-26
description: Crie um documento Word em branco em C# e aprenda a inserir um grupo de
  formas, depois adicione uma forma retangular ao grupo. Este guia aborda como agrupar
  várias formas passo a passo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group multiple shapes
- insert rectangle shape
- how to insert group
- how to add rectangle
language: pt
lastmod: 2026-10-26
og_description: Crie um documento Word em branco em C# e veja como inserir um grupo,
  depois adicione uma forma de retângulo. Domine o agrupamento de múltiplas formas
  com um exemplo de código completo.
og_image_alt: Screenshot showing a blank Word document with a grouped rectangle shape
og_title: Criar documento Word em branco e agrupar várias formas – tutorial C#
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Create a blank Word document in C# and learn how to insert a group
    shape, then add a rectangle shape to the group. This guide covers group multiple
    shapes step‑by‑step.
  headline: How to create blank Word document and group multiple shapes
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Como criar um documento Word em branco e agrupar várias formas
url: /pt/java/images-shapes/how-to-create-blank-word-document-and-group-multiple-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar um documento Word em branco e agrupar várias formas

Se você precisa **criar um documento Word em branco** programaticamente, este tutorial mostra exatamente como fazer. Você verá como inserir uma forma de grupo e, em seguida, **adicionar um retângulo** a esse grupo, cobrindo todo o fluxo de trabalho desde um documento vazio até um desenho agrupado.

Trabalhar com arquivos Word costuma significar organizar vários desenhos juntos — pense em um diagrama composto por múltiplas formas. Ao final deste guia, você será capaz de **agrupar várias formas**, inserir uma **forma retângulo** e entender **como inserir grupo** e **como adicionar retângulo** de maneira limpa e reutilizável.

## O que você precisará

* .NET 6.0 ou superior (o código também funciona com .NET Framework 4.6+)
* Pacote NuGet **Aspose.Words for .NET** (`Install-Package Aspose.Words`)
* Um entendimento básico de C# e do IDE Visual Studio (qualquer IDE serve)

> **Dica profissional:** Aspose.Words funciona totalmente offline; você não precisa de conexão com a internet após o pacote ser instalado.

## Etapa 1: Criar um documento Word em branco

A primeira operação é instanciar um objeto `Document` vazio. Esse objeto representa o **documento Word em branco** que você irá enriquecer posteriormente com formas.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1 – create a new blank Word document
        Document doc = new Document();               // <-- blank document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Por que isso importa:* Um `Document` sem seções ou parágrafos ainda é um arquivo .docx válido. Começar a partir de uma página limpa garante que nenhuma formatação oculta interfira nas formas que você adicionará depois.

## Etapa 2: Inserir uma forma de grupo (como inserir grupo)

Uma **forma de grupo** funciona como um contêiner que pode conter outros objetos de desenho. No Aspose.Words você a cria com `InsertGroupShape`.

```csharp
        // Step 2 – insert a group shape that will hold other shapes
        GroupShape group = builder.InsertGroupShape();   // <-- container for shapes
```

*Por que usar um grupo?* Agrupar permite mover, girar ou redimensionar várias formas como uma única unidade. Isso é essencial para diagramas onde os elementos precisam permanecer alinhados.

## Etapa 3: Inserir uma forma retângulo (inserir forma retângulo)

Agora adicione um retângulo ao documento. O método `InsertShape` devolve um objeto `Shape` que você pode anexar ao grupo posteriormente.

```csharp
        // Step 3 – create a rectangle shape with specific dimensions
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50); // width=100pt, height=50pt
```

*Por que um retângulo?* Retângulos são o bloco de construção mais comum para fluxogramas, maquetes de UI e gráficos de espaço reservado. As dimensões são expressas em pontos (1 pt ≈ 1/72 polegada).

## Etapa 4: Adicionar o retângulo ao grupo (como adicionar retângulo)

Uma forma criada com `InsertShape` reside diretamente no corpo do documento. Para torná‑la parte do grupo, chame `AppendChild` no `GroupShape`.

```csharp
        // Step 4 – add the rectangle to the previously created group
        group.AppendChild(rectangle);   // <-- rectangle now belongs to the group
```

*O que acontece nos bastidores?* `AppendChild` move o nó do retângulo da história principal do documento para a coleção interna do grupo, preservando seu tamanho e posição em relação à origem do grupo.

## Etapa 5: Salvar o documento

Finalmente, grave o arquivo no disco. Você pode abrir o `.docx` resultante no Microsoft Word para ver o retângulo agrupado.

```csharp
        // Step 5 – save the document to a file
        doc.Save("GroupedShapeExample.docx");
    }
}
```

> **Caso especial:** Se você pretende adicionar mais formas (por exemplo, círculos, linhas) ao mesmo grupo, repita **Etapa 3** e **Etapa 4** para cada nova forma antes de salvar. O grupo ajustará automaticamente sua caixa delimitadora para abranger todos os filhos.

## Como agrupar várias formas – estendendo o exemplo

Abaixo está um trecho rápido que adiciona uma segunda forma (uma elipse) ao mesmo grupo, demonstrando **agrupar várias formas** em um único documento.

```csharp
        // Additional shape: an ellipse
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 40);
        group.AppendChild(ellipse);   // now the group contains rectangle + ellipse
```

Ao abrir `GroupedShapeExample.docx`, você verá o retângulo e a elipse mover‑se juntos quando selecionar o grupo no Word.

## Perguntas frequentes e solução de problemas

| Pergunta | Resposta |
|----------|----------|
| **Preciso de licença para Aspose.Words?** | Uma avaliação gratuita funciona sem licença, mas adiciona uma marca d'água. Para produção, aplique uma licença para remover a marca d'água e desbloquear o desempenho total. |
| **Posso posicionar as formas com precisão?** | Sim. Após inserir uma forma, você pode definir as propriedades `Shape.Left`, `Shape.Top`, `Shape.Width` e `Shape.Height`. |
| **E se o retângulo desaparecer após salvar?** | Certifique‑se de chamar `group.AppendChild(rectangle)` *depois* de inserir o retângulo. É necessário adicionar a forma ao corpo do documento primeiro e depois movê‑la para o grupo. |
| **É possível agrupar formas em diferentes seções?** | Não. Todas as formas em um grupo devem pertencer à mesma história (seção). Crie grupos separados por seção, se necessário. |

## Recapitulação

Agora você sabe como **criar um documento Word em branco**, **inserir grupo**, **adicionar retângulo** e **agrupar várias formas** usando Aspose.Words para .NET. O exemplo completo e executável acima pode ser copiado para um aplicativo console e executado imediatamente.

## Próximos passos

* Experimente diferentes tamanhos e cores da **forma retângulo** (`rectangle.FillColor = Color.LightBlue;`).  
* Explore outros tipos de forma (`ShapeType.Polygon`, `ShapeType.Line`) para enriquecer seus diagramas.  
* Aprenda a converter o `.docx` final em PDF (`doc.Save("output.pdf");`) para distribuição.  
* Mergulhe em **como adicionar retângulo** a documentos existentes que já contêm texto — use `DocumentBuilder.MoveTo` para posicionar o grupo onde precisar.

Sinta‑se à vontade para adaptar o código às suas próprias necessidades de relatórios ou geração de diagramas. Boa codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas em seus próprios projetos.

- [Como criar um documento Word em branco e agrupar formas em C#](/words/english/net/programming-with-shapes/how-to-create-blank-word-document-and-group-shapes-in-c/)
- [Como agrupar formas no Word e adicionar formas ao documento Word](/words/english/net/programming-with-shapes/how-to-group-shapes-in-word-and-add-shapes-to-word-document/)
- [Como criar forma retângulo e agrupar formas no Word com Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}