---
category: general
date: 2026-10-23
description: Aprenda como inserir elipse e como adicionar forma de retângulo no Word
  usando Aspose.Words. Inclui mover o cursor para a forma e como criar forma de grupo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert ellipse
- how to add rectangle
- move cursor to shape
- insert rectangle shape word
- how to create group shape
language: pt
lastmod: 2026-10-23
og_description: Como inserir uma elipse e como adicionar uma forma de retângulo no
  Word com Aspose.Words. Siga o guia passo a passo para mover o cursor para a forma
  e criar um grupo de formas.
og_image_alt: Screenshot of a Word document showing a group shape containing a rectangle
  and an ellipse
og_title: Como inserir formas de elipse e retângulo em um grupo de formas no Word
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to insert ellipse and how to add rectangle shape in Word
    using Aspose.Words. Includes move cursor to shape and how to create group shape.
  headline: How to insert ellipse and rectangle shapes inside a group shape with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Como inserir formas de elipse e retângulo dentro de um grupo de formas com
  Aspose.Words
url: /pt/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como inserir formas de elipse e retângulo dentro de um grupo de formas com Aspose.Words

Se você precisa saber **como inserir elipse** em um documento Word programaticamente, este guia mostra o processo completo. Você também verá **como adicionar forma de retângulo**, aprenderá a **mover o cursor para a forma** e descobrirá **como criar um grupo de formas** que contém vários objetos de desenho.

A automação do Word frequentemente requer posicionamento preciso de objetos de desenho. Ao final deste tutorial você poderá gerar um arquivo `.docx` que contém um retângulo e uma elipse agrupados, pronto para estilização adicional ou exportação. Nenhuma ferramenta externa é necessária além da biblioteca Aspose.Words for .NET e um ambiente de desenvolvimento .NET.

## Pré-requisitos

* .NET 6.0 ou posterior instalado.
* Aspose.Words for .NET (pacote NuGet `Aspose.Words`) adicionado ao seu projeto.
* Conhecimento básico da sintaxe C# e Visual Studio (ou qualquer IDE).

Esses requisitos garantem que o código compile sem configuração adicional.

## Como criar um grupo de formas no Word

Um grupo de formas atua como um contêiner que permite mover, girar ou formatar várias formas como uma única unidade. O código a seguir cria um grupo com um tamanho específico (300 × 200 pontos) e prepara o documento para operações de desenho adicionais.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapeDemo
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a group shape that will act as a container for other shapes.
        GroupShape group = builder.InsertGroupShape(300, 200);
        
        // The group shape is now part of the document.
        // Subsequent shape insertions will be placed inside this group.
```

*Por que esta etapa é importante*: O grupo de formas define um sistema de coordenadas local. Todas as formas adicionadas após mover o cursor para dentro do grupo serão posicionadas em relação à origem do grupo, tornando os cálculos de layout simples.

## Como adicionar forma de retângulo no Word

Agora que o grupo existe, você pode **inserir forma de retângulo** dentro dele. O retângulo servirá como fundo ou como um marcador visual para outro conteúdo.

```csharp
        // Move the cursor into the group so that the next shape is added to it.
        builder.MoveTo(group);
        
        // Insert a rectangle of width 100 points and height 50 points.
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

*Explicação*: `MoveTo(group)` informa ao builder que o ponto de inserção ativo é o grupo de formas. Sem mover o cursor, `InsertShape` adicionaria o retângulo ao corpo principal do documento em vez do grupo.

## Como inserir elipse

Com o retângulo no lugar, você pode agora demonstrar **como inserir elipse**. A elipse será centralizada dentro do mesmo grupo, sobrepondo o retângulo se desejado.

```csharp
        // Keep the cursor inside the same group.
        builder.MoveTo(group);
        
        // Insert an ellipse of width 80 points and height 80 points.
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

*Por que o cursor deve ser movido*: Cada chamada a `InsertShape` respeita a localização atual do cursor. Re‑chamar `MoveTo(group)` garante que a elipse também seja filha do grupo, preservando a hierarquia pretendida.

## Mover o cursor para a forma antes de inserir objetos adicionais

Se precisar adicionar mais formas posteriormente, sempre **mova o cursor para a forma** antes de cada inserção. Esse padrão evita posicionamento acidental fora do grupo.

```csharp
        // Example: add a third shape, such as a line.
        builder.MoveTo(group);
        builder.InsertShape(ShapeType.Line, 150, 0);
```

*Dica*: Reutilizar `MoveTo(group)` é barato e melhora a legibilidade do código. Também facilita a manutenção futura porque o contexto de inserção fica explícito.

## Salvar o documento

Finalmente, persista o documento no disco. O exemplo salva o arquivo como `GroupShape.docx` em uma pasta que você especificar.

```csharp
        // Save the document to the desired location.
        document.Save(@"C:\Temp\GroupShape.docx");
    }
}
```

Ao abrir o arquivo salvo no Microsoft Word, você verá um único grupo contendo um retângulo e uma elipse, ambos posicionados corretamente.

### Saída esperada

* Um arquivo `.docx` chamado `GroupShape.docx`.
* Dentro do documento, um objeto de desenho agrupado com tamanho de 300 × 200 pontos.
* Dentro do grupo:
  * Um retângulo (100 × 50 pontos) localizado na origem do grupo.
  * Uma elipse (80 × 80 pontos) sobrepondo o retângulo.
  * Quaisquer formas adicionais que você adicionou após mover o cursor.

## Variações comuns e casos extremos

| Situação | Abordagem recomendada |
|-----------|----------------------|
| **Tamanhos de unidade diferentes** | Aspose.Words usa pontos (1 pt = 1/72 in). Converta centímetros ou polegadas para pontos antes de chamar `InsertShape`. |
| **Rotacionar formas dentro do grupo** | Após inserir uma forma, recupere seu objeto `ShapeBase` e defina `ShapeBase.RotationAngle`. |
| **Adicionar texto dentro de uma forma** | Use `ShapeBase.AppendChild(new Paragraph(document))` e então adicione um `Run` com o texto desejado. |
| **Salvar como PDF em vez de DOCX** | Chame `document.Save("GroupShape.pdf", SaveFormat.Pdf);` – a hierarquia do grupo é preservada na saída PDF. |

## Dicas profissionais

* **Reutilize a mesma instância de `DocumentBuilder`** – isso reduz o consumo de memória e mantém o estado do documento consistente.
* **Valide as dimensões das formas** – larguras ou alturas extremamente grandes podem causar problemas de renderização em versões mais antigas do Word.
* **Agrupe antes de estilizar** – aplicar cores de preenchimento ou estilos de linha ao grupo depois que todos os filhos forem adicionados garante uma aparência uniforme.

## Conclusão

Agora você entende **como inserir elipse** e **como adicionar forma de retângulo** dentro de um contêiner agrupado em um documento Word usando Aspose.Words. Ao mover consistentemente o **cursor para a forma** antes de cada inserção, você mantém uma hierarquia limpa e evita posicionamento acidental. O exemplo completo compila, executa e produz uma forma agrupada que pode ser personalizada ou exportada adicionalmente.

Pronto para explorar mais? Tente combinar esta técnica com **como criar um grupo de formas** para diagramas complexos, ou experimente **inserir forma de retângulo no Word** junto com caixas de texto para geração de relatórios avançados. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá-lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Como criar forma de retângulo e grupos de formas no Word com Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)
- [Como criar documento Word em branco e adicionar uma forma de elipse oculta em C#](/words/english/java/images-shapes/how-to-create-blank-word-document-and-add-a-hidden-ellipse-s/)
- [Como criar docx de grupo de formas e adicionar controles interativos em C#](/words/english/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}