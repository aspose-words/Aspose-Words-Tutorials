---
category: general
date: 2026-07-29
description: Desenhe retângulo no Word usando Aspose.Words. Aprenda como adicionar
  forma de retângulo, forma de linha e gerenciar várias formas em um único documento.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle word
- add rectangle shape
- add line shape
- how to add shapes
- multiple shapes word
language: pt
lastmod: 2026-07-29
og_description: Desenhe um retângulo no Word com Aspose.Words. Siga este guia passo
  a passo para adicionar forma de retângulo, forma de linha e trabalhar com várias
  formas no Word sem esforço.
og_image_alt: Screenshot showing a Word document with a grouped rectangle and line
  shape – draw rectangle word example
og_title: Desenhar retângulo no Word – Domine a adição de formas no Word
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: draw rectangle word using Aspose.Words. Learn how to add rectangle
    shape, add line shape, and manage multiple shapes word in a single document.
  headline: draw rectangle word – Add Shapes in Word with Aspose
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: Desenhar retângulo no Word – Adicionar formas no Word com Aspose
url: /pt/net/programming-with-shapes/draw-rectangle-word-add-shapes-in-word-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# draw rectangle word – Guia Completo para Adicionar Formas no Word

Já se perguntou como **draw rectangle word** documentos sem abrir a interface toda vez? Você não está sozinho. Muitos desenvolvedores precisam gerar arquivos Word dinamicamente, e a maneira mais fácil é deixar uma biblioteca fazer o trabalho pesado. Neste tutorial vamos mostrar exatamente **como adicionar formas** — especificamente um retângulo e uma linha — usando Aspose.Words para .NET, e vamos manter o foco na frase *draw rectangle word* para que você nunca se perca.

Pense nisso como um mini‑estúdio de arte que vive dentro do seu código. Ao final, você será capaz de **adicionar forma de retângulo**, **adicionar forma de linha**, e até combinar ambas em grupos **multiple shapes word**. Sem UI, sem ajustes manuais, apenas C# limpo e repetível.

## O que você vai aprender

- Configurar um novo documento Word com Aspose.Words.  
- Criar um **GroupShape** que pode conter vários objetos.  
- **Add rectangle shape** e **add line shape** dentro desse grupo.  
- Inserir as formas agrupadas no corpo do documento.  
- Salvar o arquivo e ver o resultado instantaneamente.  

Se você está confortável com C# básico e tem uma cópia do Aspose.Words, está pronto. Nenhum pacote NuGet extra além da biblioteca principal é necessário.

> **Dica profissional:** Aspose.Words funciona com .NET 6, .NET 7 e .NET Framework 4.6+. Escolha o runtime que corresponde ao seu projeto.

![exemplo de draw rectangle word](https://example.com/placeholder-image.png "draw rectangle word – formas agrupadas em um arquivo Word")

## draw rectangle word – Configurando o Documento

Antes de podermos **draw rectangle word** precisamos de uma tela limpa. A classe `Document` é essa tela; o `DocumentBuilder` é nosso pincel.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document doc = new Document();

// DocumentBuilder lets us insert nodes, paragraphs, tables, etc.
DocumentBuilder builder = new DocumentBuilder(doc);
```

As duas linhas acima nos dão um `.docx` fresco, em memória. Nada é gravado no disco ainda, o que significa que podemos experimentar sem poluir o sistema de arquivos.

## Como adicionar formas – Criando um contêiner GroupShape

Quando você quer que **multiple shapes word** se comportem como uma única unidade — mover juntas, girar juntas — você as envolve em um `GroupShape`. Pense em um grupo como uma pasta que contém outras formas.

```csharp
// Define a GroupShape that will act as a container for other shapes.
// Width = 300 pts, Height = 200 pts (roughly 4.2" x 2.8").
GroupShape group = new GroupShape(doc, 300, 200)
{
    Left = 100,   // Position from the left margin.
    Top  = 100    // Position from the top margin.
};
```

Por que um grupo? Porque mais tarde você pode querer **add rectangle shape** e **add line shape** e então movê‑las juntas. Sem um grupo, seria necessário reposicionar cada forma individualmente.

## add rectangle shape – Inserindo um retângulo dentro do grupo

Agora que o contêiner existe, vamos **add rectangle shape**. Um retângulo é um `Shape` cujo `ShapeType` é `Rectangle`.

```csharp
// Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width  = 120,   // 120 points ≈ 1.67 inches.
    Height = 80,    // 80 points ≈ 1.11 inches.
    Left   = 10,    // Offset inside the group.
    Top    = 10
};

// Append the rectangle to the group.
group.AppendChild(rectangle);
```

Observe que os valores de `Left` e `Top` são relativos à origem do grupo, não à página. Isso facilita alinhar as formas com precisão. O retângulo aparecerá próximo ao canto superior‑esquerdo do grupo.

## add line shape – Adicionando uma linha ao mesmo grupo

Uma linha é apenas outro `Shape`, mas seu `ShapeType` é `Line`. Vamos posicioná‑la abaixo do retângulo.

```csharp
// Create a line shape.
Shape line = new Shape(doc, ShapeType.Line)
{
    Width  = 150,   // Length of the line.
    Height = 0,     // Height is zero for a straight line.
    Left   = 10,
    Top    = 110    // Position it a bit lower than the rectangle.
};

// Append the line to the group.
group.AppendChild(line);
```

Como a altura da linha é zero, a propriedade `Top` determina onde a linha fica verticalmente. A `Width` controla o comprimento horizontal da linha.

## multiple shapes word – Inserindo o grupo no corpo do documento

Temos um grupo que agora contém **add rectangle shape** e **add line shape**. O passo final é inserir tudo no documento.

```csharp
// Insert the completed group into the document body at the current cursor position.
builder.InsertNode(group);
```

`InsertNode` coloca o grupo exatamente onde o `DocumentBuilder` está posicionado no momento. Se precisar dele em um parágrafo específico, mova o builder com `builder.MoveToParagraph(index)` primeiro.

## Salvando o resultado – Visualizando a saída do draw rectangle word

```csharp
// Save the document to disk. Change the path to a location that exists on your machine.
doc.Save("C:/Temp/GroupShape.docx");
```

Abra o arquivo gerado no Microsoft Word e você verá um único grupo contendo um retângulo e uma linha. Você pode clicar no grupo, arrastá‑lo ou até redimensioná‑lo — todas as formas se movem juntas. Esse é o poder de **multiple shapes word**.

### Saída esperada

- Um arquivo `.docx` chamado `GroupShape.docx`.  
- Uma página com um retângulo agrupado (120 × 80 pt) próximo ao canto superior‑esquerdo.  
- Uma linha horizontal (150 pt de comprimento) posicionada logo abaixo do retângulo.  
- Ambas as formas são selecionáveis como um único objeto.

Se você der duplo‑clique no grupo, o Word permitirá editar cada forma individualmente — perfeito para ajustes finos.

## Perguntas comuns & casos de borda

**E se eu precisar de mais de duas formas?**  
Basta continuar chamando `group.AppendChild(yourShape)` para cada objeto adicional. O grupo pode conter qualquer número de formas, tornando‑o ideal para diagramas complexos.

**Posso mudar a cor de preenchimento do retângulo?**  
Claro. Depois de criar o retângulo, defina `rectangle.FillColor = System.Drawing.Color.LightBlue;`. Isso funciona para qualquer forma que suporte preenchimento.

**Preciso definir `Height = 0` para uma linha?**  
Sim, para uma linha horizontal reta a altura deve ser zero. Para uma linha vertical, defina `Width = 0` e atribua um valor positivo a `Height`.

**Isso funciona com arquivos .doc (Word 97‑2003)?**  
Aspose.Words pode salvar no formato antigo `.doc`, mas alguns recursos modernos de formas podem ser limitados. Use `.docx` para fidelidade total.

**Como giro todo o grupo?**  
Você pode definir `group.Rotation = 45;` (graus) antes de inseri‑lo. A rotação se aplica a todas as formas filhas.

## Recap – Como adicionar formas no Word programaticamente

- **draw rectangle word** começa criando um `Document` e um `DocumentBuilder`.  
- Construa um **GroupShape** para conter **multiple shapes word**.  
- **add rectangle shape** e **add line shape** são adicionados ao grupo.  
- Insira o grupo no corpo com `builder.InsertNode`.  
- Salve o arquivo e abra‑o para verificar o resultado visual.

Esse é todo o fluxo de trabalho, encapsulado em um único trecho de código fácil de ler.

## Próximos passos & tópicos relacionados

Agora que você sabe **como adicionar formas**, considere explorar:

- **add rectangle shape** com cantos arredondados (`ShapeType.Rectangle` + `CornerRadius`).  
- Estilizar linhas com diferentes padrões de traço (`line.LineFormat.DashStyle`).  
- Incorporar imagens ao lado das formas para relatórios mais ricos.  
- Usar **multiple shapes word** para construir fluxogramas ou diagramas UML simples.  

Cada um desses tópicos se baseia naturalmente na fundação que apresentamos aqui, e todos seguem o mesmo padrão de criar formas, configurá‑las e agrupá‑las quando necessário.

---

Feliz codificação! Se encontrar algum detalhe estranho ou tiver um caso de uso interessante para compartilhar, deixe um comentário abaixo. Seu feedback ajuda a todos a dominar a arte de **draw rectangle word** e muito mais.


## O que você deve aprender a seguir?


Os tutoriais a seguir cobrem tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}