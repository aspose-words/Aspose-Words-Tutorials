---
category: general
date: 2026-10-20
description: Ocultar/Exibir uma forma com a nova propriedade `Hidden` usando Aspose.Words
  para C#. Aprenda a alternar a visibilidade da forma, lidar com casos extremos e
  salvar o resultado.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- Hide/Show a Shape with the new `Hidden` prop
- Aspose.Words hide shape
- C# shape hidden property
- Word document shape visibility
- programmatically hide shape
language: pt
lastmod: 2026-10-20
og_description: Ocultar/Exibir uma Forma com a nova propriedade `Hidden` usando Aspose.Words
  para C#. Domine a alternância de visibilidade de formas e evite armadilhas comuns.
og_image_alt: Screenshot of a Word document where a shape is hidden using the Hidden
  property
og_title: Ocultar/Exibir uma Forma com a nova propriedade `Hidden` no Aspose.Words
  (C#)
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Hide/Show a Shape with the new `Hidden` prop using Aspose.Words for
    C#. Learn how to toggle shape visibility, handle edge cases, and save the result.
  headline: Hide/Show a Shape with the new `Hidden` prop in Aspose.Words for C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Ocultar/Exibir uma Forma com a nova propriedade `Hidden` no Aspose.Words para
  C#
url: /pt/net/programming-with-shapes/hide-show-a-shape-with-the-new-hidden-prop-in-aspose-words-f/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ocultar/Exibir uma Forma com a nova propriedade `Hidden` no Aspose.Words para C#

Se você precisa **Ocultar/Exibir uma Forma com a nova propriedade `Hidden`** em um documento Word, este guia mostra exatamente como fazer isso com Aspose.Words para .NET. Seja gerando relatórios, criando modelos ou limpando documentos importados, controlar a visibilidade de formas programaticamente evita edições manuais.

Neste tutorial você aprenderá como carregar um documento, localizar uma forma, alternar a propriedade `Hidden` e salvar o arquivo modificado. As etapas também cobrem variações comuns, como manipular múltiplas formas e lidar com gráficos inline versus flutuantes.

## Pré-requisitos

Antes de começar, certifique-se de que você tem:

* .NET 6.0 (ou posterior) instalado – Aspose.Words suporta .NET Standard 2.0 e .NET Core.  
* Uma cópia licenciada do **Aspose.Words for .NET** (a versão de avaliação gratuita funciona para exploração).  
* Uma IDE como Visual Studio 2022 ou Visual Studio Code.  
* Um documento Word (`input.docx`) que contenha ao menos uma forma (por exemplo, uma imagem, SmartArt ou uma tela de desenho).

## Etapa 1: Carregar o documento Word

A primeira operação é criar um objeto `Document` que representa o arquivo .docx no disco.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Por que esta etapa é importante*: `Document` é o ponto de entrada para todas as operações do Aspose.Words. Carregar o arquivo na memória fornece acesso total à sua árvore de nós, incluindo formas.

## Etapa 2: Recuperar a forma alvo

Para alternar a visibilidade, você deve obter uma referência ao nó da forma. O exemplo abaixo obtém a primeira forma no documento, mas você pode adaptar a lógica para localizar formas por nome, tipo ou índice.

```csharp
// Get the first Shape node in the document tree
Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

if (shape == null)
{
    throw new InvalidOperationException("No shape was found in the document.");
}
```

*Por que esta etapa é importante*: `GetChild` com `true` realiza uma busca profunda, garantindo que você encontre formas mesmo quando elas estão aninhadas dentro de tabelas ou cabeçalhos. Verificar se o resultado é `null` evita um `NullReferenceException` quando o documento não contém formas.

## Etapa 3: Ocultar a forma com a propriedade `Hidden`

Aspose.Words introduziu a propriedade `Hidden` para controlar se uma forma é renderizada ou impressa. Definir como `true` oculta a forma; definir como `false` a torna visível novamente.

```csharp
// Hide the shape so it will not appear in the rendered document
shape.Hidden = true;
```

Se você precisar **exibir** uma forma previamente oculta, basta atribuir `false`:

```csharp
// Show the shape again
shape.Hidden = false;
```

*Por que esta etapa é importante*: A propriedade `Hidden` funciona tanto para formas flutuantes quanto inline, e integra‑se com a formatação nativa “Hidden” do Word. Essa abordagem é mais confiável que remover a forma, pois o nó permanece na árvore do documento, preservando o layout e as referências.

## Etapa 4: Salvar o documento modificado

Depois de ajustar a visibilidade, grave as alterações em um novo arquivo (ou sobrescreva o original, se desejar).

```csharp
// Save the document with the updated shape visibility
doc.Save("YOUR_DIRECTORY/ShapeHidden.docx");
```

*Por que esta etapa é importante*: `Save` serializa a árvore de nós em memória em um pacote .docx que o Word pode abrir. A flag oculta é persistida, de modo que ao abrir o arquivo no Microsoft Word a forma será exibida de acordo com a configuração `Hidden`.

## Exemplo completo, executável

Juntando todas as etapas, você obtém um programa autocontido que pode copiar, compilar e executar.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HideShowShapeExample
{
    static void Main()
    {
        // 1. Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first shape in the document
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found. Exiting.");
            return;
        }

        // 3. Toggle the Hidden property
        // Hide the shape
        shape.Hidden = true;
        // To show the shape again, uncomment the following line:
        // shape.Hidden = false;

        // 4. Save the modified document
        doc.Save("YOUR_DIRECTORY/ShapeHidden.docx");

        Console.WriteLine("Document saved. Shape hidden = " + shape.Hidden);
    }
}
```

**Saída esperada** ao executar o programa:

```
Document saved. Shape hidden = True
```

Abrir `ShapeHidden.docx` no Microsoft Word mostra o documento sem a forma alvo. Se você definir `shape.Hidden = false;` antes de salvar, a forma reaparece.

## Manipulando múltiplas formas

O exemplo acima funciona para uma única forma. Documentos reais costumam conter muitas imagens. Use um loop para ocultar ou exibir todas as formas que atendam a uma condição (por exemplo, um nome ou tipo específico).

```csharp
// Hide every picture shape in the document
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.ShapeType == ShapeType.Image)
    {
        s.Hidden = true; // hide picture
    }
}
doc.Save("YOUR_DIRECTORY/AllPicturesHidden.docx");
```

*Dica*: Filtrar por `ShapeType` evita ocultar acidentalmente elementos decorativos como caixas de texto ou SmartArt.

## Casos extremos e boas práticas

| Situação | Manipulação recomendada |
|-----------|----------------------|
| **A forma está dentro de um cabeçalho/rodapé** | Recupere primeiro o nó de cabeçalho/rodapé, então chame `GetChild(NodeType.Shape, …)` nesse sub‑documento. |
| **O documento não contém formas** | Sempre verifique se é `null` após `GetChild` ou confirme `doc.GetChildNodes(NodeType.Shape, true).Count`. |
| **Você precisa preservar a flag hidden em diferentes versões do Word** | A propriedade `Hidden` é armazenada no XML da forma como `<w:hidden/>`, que é suportado pelo Word 2007 e posteriores. |
| **Desempenho com documentos grandes** | Use `doc.GetChildNodes(NodeType.Shape, true)` uma única vez e reutilize a coleção ao invés de chamar `GetChild` repetidamente. |

## Dica profissional: Combine `Hidden` com `WrapType`

Quando uma forma está oculta, o Word ainda reserva o espaço que ela ocuparia, a menos que você também altere seu comportamento de quebra. Definir `WrapType = WrapType.None` remove a área de espaço reservado.

```csharp
shape.Hidden = true;
shape.WrapType = WrapType.None;
```

Isso faz com que o layout colapse como se a forma nunca tivesse existido, o que é útil para gerar relatórios limpos.

## Conclusão

Agora você sabe como **Ocultar/Exibir uma Forma com a nova propriedade `Hidden`** usando Aspose.Words para C#. A solução cobre carregamento do documento, localização da forma, alternância da propriedade `Hidden` e persistência da alteração. Seguindo as dicas de boas práticas — verificação de `null`, manipulação de múltiplas formas e ajuste das configurações de quebra — você pode controlar a visibilidade de formas de forma confiável em qualquer cenário de automação do Word.

Pronto para explorar mais? Considere os próximos passos:

* **Ocultar/Exibir múltiplas formas** com base em metadados personalizados (usa a técnica “ocultar forma programaticamente”).  
* **Combinar `Hidden` com conteúdo condicional** usando campos do Aspose.Words para geração dinâmica de relatórios.  
* **Explorar outras propriedades de nós**, como `Visible` para objetos de gráfico ou `IsDeleted` para controle ao nível de parágrafo.

Feliz codificação, e aproveite o controle granular que o Aspose.Words oferece para a visibilidade de formas em documentos Word!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [como ocultar forma no Word usando C# – guia passo a passo](/words/english/net/programming-with-shapes/how-to-hide-shape-in-word-using-c-step-by-step-guide/)
- [Como ocultar forma no Word com C# – Guia passo a passo](/words/english/net/programming-with-shapes/how-to-hide-shape-in-word-with-c-step-by-step-guide/)
- [Criar um documento Word em branco com uma forma elipse oculta – Guia completo em C#](/words/english/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}