---
category: general
date: 2026-09-14
description: Aprenda como ocultar formas no Word usando C# — incluindo código para
  criar documento Word, inserir forma retangular no Word e ocultar a forma no Word
  programaticamente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape
- hide shape in word
- create word document code
- insert rectangle shape word
language: pt
lastmod: 2026-09-14
og_description: Como ocultar forma no Word usando C# — guia passo a passo que também
  mostra como criar código de documento Word e inserir forma retangular no Word.
og_image_alt: Word document preview with a visible rectangle shape and a hidden ellipse
  shape
og_title: Como ocultar forma em um documento Word com código C#
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Learn how to hide shape in Word using C#—including create word document
    code, insert rectangle shape word, and hide shape in word programmatically.
  headline: How to hide shape in a Word document with C# code
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Como ocultar forma em um documento do Word com código C#
url: /pt/net/programming-with-shapes/how-to-hide-shape-in-a-word-document-with-c-code/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como ocultar forma em um documento Word com código C#

Se você precisa **how to hide shape** em um arquivo Word, este tutorial mostra a solução completa. Você verá como criar um documento Word, inserir uma forma retangular, adicionar uma elipse e ocultar essa elipse para que apenas o retângulo apareça quando o arquivo for aberto.

O guia cobre tudo o que você precisa — sem referências externas, apenas o código e as explicações. Ao final, você será capaz de incorporar gráficos ocultos em qualquer documento Word que você gerar programaticamente.

## Pré-requisitos

- .NET 6.0 ou posterior (o código também funciona com .NET Framework 4.7+)
- Aspose.Words for .NET (versão de avaliação gratuita ou licenciada)  
  Instale via NuGet: `dotnet add package Aspose.Words`
- Familiaridade básica com C# e Visual Studio ou qualquer IDE de sua preferência

## Etapa 1: Configurar o projeto e importar namespaces

Inicie um novo aplicativo de console e adicione as declarações `using` necessárias. Essas importações dão acesso às classes `Document`, `DocumentBuilder` e de desenho necessárias para manipular formas.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The rest of the code follows in the next steps
        }
    }
}
```

**Por que isso importa** – Importar os namespaces corretos evita erros de compilação e torna a superfície da API disponível para criação de formas e controle de visibilidade.

## Etapa 2: Criar um novo documento Word e um builder

Um `Document` representa o arquivo, enquanto um `DocumentBuilder` fornece uma API fluente para adicionar conteúdo. Este é o primeiro local onde você aplica a lógica de **how to hide shape**: você precisa de um contexto de documento antes que qualquer forma possa existir.

```csharp
// Step 2: Create a new blank document and a builder to edit it
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);
```

**Explicação** – O objeto `Document` começa vazio. O `DocumentBuilder` está posicionado no início do primeiro parágrafo, pronto para inserir formas ou texto.

## Etapa 3: Inserir uma forma retangular visível

O retângulo será a forma que permanece visível quando o documento for aberto. Você pode controlar seu tamanho, posição e formatação diretamente através do objeto shape.

```csharp
// Step 3: Insert a visible rectangle shape and position it
Shape visibleRectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
visibleRectangle.Left = 50;                 // 50 points from the left margin
visibleRectangle.Top = 100;                 // 100 points from the top of the page
visibleRectangle.FillColor = System.Drawing.Color.LightBlue;
visibleRectangle.LineColor = System.Drawing.Color.DarkBlue;
```

**Por que esta etapa** – Adicionar um retângulo demonstra o requisito **insert rectangle shape word**. Definir `FillColor` e `LineColor` torna a forma fácil de identificar no documento final.

## Etapa 4: Inserir uma forma elipse e ocultá‑la

Agora você adiciona a forma que pretende ocultar. A propriedade `Hidden` indica ao Word que não renderize a forma na interface, embora ela continue fazendo parte da estrutura do documento.

```csharp
// Step 4: Insert an ellipse shape, position it, and hide it from view
Shape hiddenEllipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
hiddenEllipse.Left = 200;      // Position away from the rectangle
hiddenEllipse.Top = 100;
hiddenEllipse.Hidden = true;   // This flag implements how to hide shape
```

**Explicação** – Definir `Hidden = true` é o núcleo de **hide shape in word**. O Word respeita essa flag durante a visualização e impressão normais, mas a forma ainda pode ser acessada programaticamente, se necessário.

## Etapa 5: Salvar o documento

Finalmente, grave o documento no disco. Escolha uma pasta na qual você tenha permissão de escrita e dê ao arquivo um nome claro que reflita o objetivo do tutorial.

```csharp
// Step 5: Save the document with both shapes
string outputPath = @"C:\Temp\ShapeVisibility.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

**Resultado** – Ao abrir `ShapeVisibility.docx` no Microsoft Word, apenas o retângulo azul‑claro é exibido. A elipse oculta não aparece, confirmando que você dominou com sucesso **how to hide shape** em um arquivo Word.

## Exemplo completo em funcionamento

Juntando todos os trechos, você obtém um único programa executável:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a new document and builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert a visible rectangle
            Shape visibleRectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            visibleRectangle.Left = 50;
            visibleRectangle.Top = 100;
            visibleRectangle.FillColor = System.Drawing.Color.LightBlue;
            visibleRectangle.LineColor = System.Drawing.Color.DarkBlue;

            // Insert a hidden ellipse
            Shape hiddenEllipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
            hiddenEllipse.Left = 200;
            hiddenEllipse.Top = 100;
            hiddenEllipse.Hidden = true; // hides the shape

            // Save the document
            string outputPath = @"C:\Temp\ShapeVisibility.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Saída esperada

- **Visual**: Ao abrir `ShapeVisibility.docx`, você vê um retângulo azul‑claro posicionado próximo à margem esquerda. Nenhuma elipse é visível.
- **Programático**: A elipse oculta permanece no XML do documento (elemento `<w:drawing>`) com o atributo `w:hidden` definido, o que pode ser verificado ao abrir o arquivo como zip e inspecionar `document.xml`.

## Perguntas comuns e casos extremos

| Pergunta | Resposta |
|----------|----------|
| *Posso ocultar várias formas?* | Sim. Defina `Hidden = true` em cada forma que você deseja ocultar. |
| *Formas ocultas são impressas?* | Por padrão, o Word não imprime objetos ocultos. Se precisar que sejam impressos, limpe a flag `Hidden` antes da impressão. |
| *A propriedade hidden é suportada em versões mais antigas do Word?* | O atributo `Hidden` faz parte do padrão Office Open XML e funciona no Word 2007 e posteriores. |
| *E se eu precisar alternar a visibilidade em tempo de execução?* | Recupere a forma via `document.GetChildNodes(NodeType.Shape, true)` e altere a propriedade `Hidden` de acordo com sua lógica. |

## Dicas profissionais

- **Desempenho**: Se você gerar muitos documentos, reutilize uma única instância de `DocumentBuilder` ao invés de criar uma nova para cada arquivo.
- **Controle de versão**: Armazene os arquivos `.docx` gerados em uma pasta controlada por versionamento; formas ocultas podem atuar como marcadores de metadados para processamento posterior.
- **Teste**: Automatize um teste visual rápido convertendo o DOCX para PDF com Aspose.Words (`document.Save("out.pdf")`). O PDF também ocultará a elipse, confirmando que a flag hidden se propaga nas conversões de formato.

## Conclusão

Agora você sabe **how to hide shape** em um documento Word usando C#. O tutorial percorreu a criação de um documento, **insert rectangle shape word**, a adição de uma elipse e a aplicação da flag `Hidden` para alcançar o comportamento **hide shape in word**. Com o código completo e executável, você pode integrar gráficos ocultos em qualquer fluxo de trabalho de relatórios ou modelagem automatizada.

### Próximos passos

- Explore outras propriedades de forma, como rotação, sombra e ajuste de texto.  
- Combine formas ocultas com propriedades de documento personalizadas para incorporar dados legíveis por máquina.  
- Investigue padrões de **create word document code** para tabelas, gráficos e controles de conteúdo para expandir seu conjunto de ferramentas de automação.

Sinta‑se à vontade para experimentar diferentes tipos de forma e configurações de visibilidade — seu próximo projeto de automação Word está a apenas algumas linhas de código!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Criar forma retangular no Word usando C# – Guia passo a passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Criar documento Word em branco com forma retangular sombreada – Guia passo a passo](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Tutorial de sombra de forma Aspose.Words – Adicionar sombra a forma Word em C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}