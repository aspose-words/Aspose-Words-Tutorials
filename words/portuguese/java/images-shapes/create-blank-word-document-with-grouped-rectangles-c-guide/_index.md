---
category: general
date: 2026-07-23
description: Crie um documento Word em branco e adicione uma forma retangular em C#.
  Aprenda como inserir formas e agrupar formas no Word usando Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- group shapes word
- how to insert shapes
- how to group shapes
language: pt
lastmod: 2026-07-23
og_description: Crie um documento Word em branco em C# e aprenda como inserir formas,
  adicionar forma de retângulo e agrupar formas no Word com Aspose.Words.
og_image_alt: Screenshot showing a blank Word document with two rectangle shapes grouped
  together
og_title: Criar documento Word em branco com retângulos agrupados – tutorial C#
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: Create blank word document and add rectangle shape in C#. Learn how
    to insert shapes and group shapes word using Aspose.Words.
  headline: Create blank word document with grouped rectangles – C# guide
  type: TechArticle
- description: Create blank word document and add rectangle shape in C#. Learn how
    to insert shapes and group shapes word using Aspose.Words.
  name: Create blank word document with grouped rectangles – C# guide
  steps:
  - name: What if I need more than two shapes?
    text: Just keep calling `builder.InsertShape(...)` and `group.AppendChild(...)`
      for each new shape. The group can hold any number of children.
  - name: Can I set fill colour or border on the rectangles?
    text: 'Absolutely. After creating a rectangle you can tweak its `FillColor`, `OutlineColor`,
      and `LineWidth`:'
  - name: How do I move the whole group after it’s been created?
    text: 'Use the group''s `Left` and `Top` properties, measured in points:'
  - name: What about scaling the group?
    text: Set `group.Width` and `group.Height` or use `group.ScaleX` / `group.ScaleY`.
      The child rectangles retain their proportions relative to the group.
  - name: Does this work with older .doc files?
    text: Aspose.Words abstracts the file format, so the same code works for `.doc`
      and `.docx`. The only limitation is that some newer shape features may be down‑sampled
      when saving to the older binary format.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Criar documento Word em branco com retângulos agrupados – Guia C#
url: /pt/java/images-shapes/create-blank-word-document-with-grouped-rectangles-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar documento Word em branco com retângulos agrupados – Guia C# 

Já precisou **criar documento Word em branco** que já contenha um conjunto de formas, mas não sabia como agrupá‑las adequadamente? Você não está sozinho. Em muitos cenários de relatórios ou geração de modelos, você quer uma tela limpa com alguns retângulos atuando como marcadores de posição, e gostaria que eles se movessem juntos como uma única unidade.

Neste tutorial, percorreremos os passos exatos para **criar documento Word em branco**, **adicionar forma de retângulo**, e então **agrupar formas Word** usando a biblioteca Aspose.Words. Ao final, você terá um arquivo `.docx` pronto para uso onde os dois retângulos fazem parte de um grupo, de modo que qualquer posicionamento ou redimensionamento posterior afete ambos simultaneamente.

Também responderemos às perguntas comuns “**como inserir formas**” e “**como agrupar formas**” que surgem em fóruns e no Stack Overflow. Nenhuma documentação externa necessária — tudo o que você precisa está aqui.

---

## Prerequisites

- .NET 6 ou posterior (o código também compila com .NET Core)  
- Aspose.Words for .NET (pacote NuGet `Aspose.Words`)  
- Um entendimento básico da sintaxe C# (se você já escreveu um “Hello World”, está pronto)  

If you haven’t installed Aspose.Words yet, run:

```bash
dotnet add package Aspose.Words
```

É isso — sem DLLs extras, sem interop COM, apenas uma referência NuGet limpa.

---

## Step 1: Create blank word document and initialize the builder

A primeira coisa que fazemos é criar um objeto `Document` vazio. Pense nele como uma folha em branco. Em seguida, anexamos um `DocumentBuilder`, que é a ferramenta prática que a Aspose fornece para inserir conteúdo.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document doc = new Document();               // <-- create blank word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Por que isso importa:** Sem um `DocumentBuilder` você teria que manipular a árvore de nós de baixo nível manualmente, o que é propenso a erros. O builder abstrai as complexidades XML de um arquivo `.docx`.

---

## Step 2: How to insert shapes – add a group container first

A Aspose permite inserir uma *group shape* que pode posteriormente conter outras formas. Esta é a base para **group shapes word**.  

```csharp
        // Step 2: Insert a group shape that will act as a container
        Shape group = builder.InsertGroupShape();
```

> **Dica profissional:** O grupo em si é invisível até que você adicione formas filhas, portanto você não verá nenhum artefato no documento resultante até a próxima etapa.

---

## Step 3: Add rectangle shape – the actual visible objects

Agora vamos **adicionar forma de retângulo** duas vezes, cada uma com seu próprio tamanho. O método `InsertShape` recebe um `ShapeType` e dimensões em pontos (1 pt ≈ 1/72 polegada).

```csharp
        // Step 3: Insert two rectangle shapes with desired dimensions
        Shape rect1 = builder.InsertShape(ShapeType.Rectangle, 100, 50); // 100 pt × 50 pt
        Shape rect2 = builder.InsertShape(ShapeType.Rectangle, 80, 40);  // 80 pt × 40 pt
```

> **Por que retângulos?** Eles são a forma geométrica mais simples, perfeitos para marcadores de posição, simulações de UI semelhantes a botões ou elementos gráficos simples.

---

## Step 4: How to group shapes – attach rectangles to the group

Com os retângulos criados, agora **como agrupar formas** anexando‑os como filhos da group shape que inserimos anteriormente.

```csharp
        // Step 4: Append the rectangles to the group shape
        group.AppendChild(rect1);
        group.AppendChild(rect2);
```

> **O que acontece nos bastidores?** A group shape torna‑se o nó pai na árvore XML do documento. Mover o grupo move ambos os retângulos juntos, preservando suas posições relativas.

---

## Step 5: Save the document – you now have a grouped‑shape Word file

Finalmente, persistimos o documento no disco. Altere o caminho para um local que exista na sua máquina.

```csharp
        // Step 5: Save the document with the grouped shapes
        doc.Save("GroupShape.docx");   // Creates a blank word document with grouped rectangles
    }
}
```

Esse é o programa completo. Execute‑o, abra `GroupShape.docx` e você verá dois retângulos juntos. Se você selecionar um, todo o grupo será destacado — exatamente o que **group shapes word** deve fazer.

---

## Full source code in one place

Para conveniência, aqui está o exemplo completo, pronto para copiar e colar:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a group shape that will contain other shapes
        Shape group = builder.InsertGroupShape();

        // Insert two rectangle shapes with desired dimensions
        Shape rect1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        Shape rect2 = builder.InsertShape(ShapeType.Rectangle, 80, 40);

        // Add the rectangles to the group shape
        group.AppendChild(rect1);
        group.AppendChild(rect2);

        // Save the document
        doc.Save("GroupShape.docx");
    }
}
```

**Saída esperada:** Ao abrir `GroupShape.docx` você verá uma página em branco com dois retângulos agrupados. Selecionar um retângulo seleciona automaticamente o outro, confirmando que o agrupamento foi bem‑sucedido.

---

## Common questions & edge‑case handling

### What if I need more than two shapes?

Basta continuar chamando `builder.InsertShape(...)` e `group.AppendChild(...)` para cada nova forma. O grupo pode conter qualquer número de filhos.

### Can I set fill colour or border on the rectangles?

Com certeza. Após criar um retângulo, você pode ajustar seu `FillColor`, `OutlineColor` e `LineWidth`:

```csharp
rect1.FillColor = System.Drawing.Color.LightBlue;
rect1.OutlineColor = System.Drawing.Color.DarkBlue;
rect1.LineWidth = 1.5;
```

### How do I move the whole group after it’s been created?

Use as propriedades `Left` e `Top` do grupo, medidas em pontos:

```csharp
group.Left = 150;   // move 150 pt from the left margin
group.Top  = 200;   // move 200 pt from the top of the page
```

### What about scaling the group?

Defina `group.Width` e `group.Height` ou use `group.ScaleX` / `group.ScaleY`. Os retângulos filhos mantêm suas proporções relativas ao grupo.

### Does this work with older .doc files?

Aspose.Words abstrai o formato de arquivo, portanto o mesmo código funciona para `.doc` e `.docx`. A única limitação é que alguns recursos de forma mais recentes podem ser reduzidos ao salvar no formato binário mais antigo.

---

## Pro tips for production‑ready code

- **Liberar recursos** – Envolva `Document` em um bloco `using` se estiver lidando com arquivos grandes para liberar memória rapidamente.  
- **Tratamento de erros** – Capture `Aspose.Words.Fonts.FontSettingsException` se você planeja incorporar fontes personalizadas.  
- **Desempenho** – Ao inserir muitas formas, desative temporariamente as atualizações de layout com `doc.LayoutOptions = new LayoutOptions { UpdateFields = false };` e reative depois.

---

## Conclusion

Agora você sabe **como criar documento Word em branco**, **adicionar forma de retângulo** e **agrupar formas Word** usando Aspose.Words em C#. O exemplo cobre as etapas essenciais de “**como inserir formas**” e “**como agrupar formas**”, explica por que cada linha existe e ainda aborda personalização, casos extremos e boas práticas.

Em seguida, você pode explorar **como inserir imagens**, **adicionar texto dentro de formas agrupadas**, ou **exportar o documento para PDF** — tudo isso segue o mesmo padrão de uso do `DocumentBuilder` e manipulação de formas. Continue experimentando; a API da Aspose é suficientemente robusta para lidar com quase qualquer cenário de automação Word que você imaginar.

Feliz codificação, e sinta‑se à vontade para deixar um comentário se encontrar algum problema!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Inserir formas em documentos Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Criar Group Shape em documento Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Criar forma de retângulo no Word usando C# – Guia passo a passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}