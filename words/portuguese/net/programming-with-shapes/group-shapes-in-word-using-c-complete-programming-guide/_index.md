---
category: general
date: 2026-10-13
description: Agrupar formas no Word com C# – aprenda como agrupar formas e adicionar
  formas ao grupo usando Aspose.Words em alguns passos simples.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- add shapes to group
language: pt
lastmod: 2026-10-13
og_description: Agrupe formas no Word usando C# e Aspose.Words. Siga este guia para
  aprender como agrupar formas e adicionar formas ao grupo em um documento do Word.
og_image_alt: Screenshot of a Word document showing two shapes combined into a single
  grouped shape
og_title: Agrupar formas no Word com C# – guia passo a passo
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: group shapes in Word with C# – learn how to group shapes and add shapes
    to group using Aspose.Words in a few easy steps.
  headline: Group shapes in Word using C# – complete programming guide
  type: TechArticle
- description: group shapes in Word with C# – learn how to group shapes and add shapes
    to group using Aspose.Words in a few easy steps.
  name: Group shapes in Word using C# – complete programming guide
  steps:
  - name: Load the Word document
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Retrieve the shapes you want to group
    text: '```csharp // Get the first shape (index 0) and second shape (index 1) from
      the whole document. Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0,
      true); Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true); ```'
  - name: Create a new `GroupShape` container
    text: '```csharp GroupShape groupShape = new GroupShape(doc); ```'
  - name: Add the individual shapes to the group
    text: '```csharp groupShape.AppendChild(firstShape); groupShape.AppendChild(secondShape);
      ```'
  - name: Insert the group shape into the document body
    text: '```csharp // Insert the group as the last child of the first paragraph.
      Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph; firstParagraph.AppendChild(groupShape);
      ```'
  - name: Save the modified document
    text: '```csharp string outputPath = @"YOUR_DIRECTORY\output.docx"; doc.Save(outputPath);
      ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Agrupar formas no Word usando C# – guia completo de programação
url: /pt/net/programming-with-shapes/group-shapes-in-word-using-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Agrupar formas no Word usando C# – guia completo de programação

Se você precisa **agrupar formas no Word** programaticamente, este guia mostra exatamente como fazer. Ao final das duas primeiras frases, você saberá o código necessário, o raciocínio por trás de cada passo e como **adicionar formas ao grupo** sem surpresas.

Cobriremos tudo, desde o carregamento de um arquivo `.docx` até a gravação do documento atualizado. O tutorial assume que você tem conhecimentos básicos de C# e uma referência à biblioteca Aspose.Words for .NET. Nenhuma documentação externa é necessária — basta copiar, colar e executar.

## Pré-requisitos

- .NET 6.0 ou posterior (o código também funciona com .NET Framework 4.7+)
- Pacote NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)
- Um documento Word (`input.docx`) que já contém pelo menos duas formas (por exemplo, imagens, AutoShapes)

> **Dica profissional:** Se você estiver testando, crie um arquivo Word simples com dois retângulos via a interface do Word. Salve-o como `input.docx` em uma pasta que você controla.

## Agrupar formas no Word – guia passo a passo

A seguir, dividimos o processo em cinco etapas lógicas. Cada etapa inclui o código C# exato, uma explicação do *porquê* da linha ser necessária e uma breve observação sobre armadilhas comuns.

### Etapa 1: Carregar o documento Word

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

string inputPath = @"YOUR_DIRECTORY\input.docx";
Document doc = new Document(inputPath);
```

**Por que:** `Document` é o ponto de entrada para qualquer manipulação de Word. Fornecer o caminho completo do arquivo carrega o documento na memória, permitindo que consultemos e modifiquemos sua árvore de nós.

**Armadilha:** Passar um caminho relativo pode falhar quando o diretório de trabalho for diferente. Use um caminho absoluto ou `Path.Combine` com `AppContext.BaseDirectory`.

### Etapa 2: Recuperar as formas que você deseja agrupar

```csharp
// Get the first shape (index 0) and second shape (index 1) from the whole document.
Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true);
```

**Por que:** `GetChild` percorre a árvore do documento e retorna o *n‑ésimo* nó do tipo solicitado. Definir `isDeep` como `true` busca em todo o documento, não apenas na seção atual.

**Caso de borda:** Se o documento contiver menos de duas formas, `firstShape` ou `secondShape` será `null` e uma exceção será lançada quando tentarmos fazer o cast. Proteja-se contra isso:

```csharp
if (firstShape == null || secondShape == null)
    throw new InvalidOperationException("The document must contain at least two shapes to group.");
```

### Etapa 3: Criar um novo contêiner `GroupShape`

```csharp
GroupShape groupShape = new GroupShape(doc);
```

**Por que:** `GroupShape` funciona como um nó pai que pode conter múltiplos objetos `Shape`. Ele herda de `Shape`, portanto pode ser inserido onde uma forma regular é permitida (por exemplo, dentro de um parágrafo).

### Etapa 4: Adicionar as formas individuais ao grupo

```csharp
groupShape.AppendChild(firstShape);
groupShape.AppendChild(secondShape);
```

**Por que:** `AppendChild` move as formas de suas localizações originais para o novo grupo. Após esta chamada, as formas originais não existem mais como nós independentes; elas passam a fazer parte de `groupShape`.

**Dica:** O agrupamento ajusta automaticamente as posições relativas das formas filhas. Se precisar de um layout específico, defina a propriedade `GroupShape.Bounds` *antes* de anexar os filhos.

```csharp
// Example: set the group to start at (100, 100) points and be 300x200 points large.
groupShape.Bounds = new System.Drawing.RectangleF(100, 100, 300, 200);
```

### Etapa 5: Inserir o grupo de formas no corpo do documento

```csharp
// Insert the group as the last child of the first paragraph.
Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
firstParagraph.AppendChild(groupShape);
```

**Por que:** Um `GroupShape` deve ser colocado dentro de um parágrafo (ou de uma célula de tabela) para ser renderizado. Ao anexá‑lo ao primeiro parágrafo garantimos uma colocação visível sem interromper o layout existente.

### Etapa 6: Salvar o documento modificado

```csharp
string outputPath = @"YOUR_DIRECTORY\output.docx";
doc.Save(outputPath);
```

**Por que:** `Save` grava as alterações em memória de volta a um arquivo `.docx`. Você também pode salvar em um stream ou em PDF alterando a sobrecarga.

**Verificação do resultado:** Abra `output.docx` no Microsoft Word. Você deverá ver as duas formas originais agora combinadas em um único objeto agrupado. Selecionar o grupo exibirá as alças padrão de agrupamento do Word.

## Como agrupar formas programaticamente – insights mais profundos

- **Propriedade do nó:** Quando você chama `AppendChild`, a referência `ParentNode` da forma é alterada automaticamente. Isso impede nós “órfãos” que poderiam corromper o documento.
- **Preservação de formatação:** O agrupamento **não** perde nenhuma formatação da forma (cor de preenchimento, estilo de linha, etc.). Todas as formas filhas mantêm suas propriedades originais.
- **Grupos aninhados:** `GroupShape` pode conter outros objetos `GroupShape`, permitindo hierarquias de múltiplos níveis. Basta tratar o grupo interno como qualquer outra forma.

## Adicionar formas ao grupo e gerenciá‑las posteriormente

Se você precisar adicionar mais formas após o grupo inicial ser criado, pode reutilizar a mesma instância `GroupShape`:

```csharp
// Assume we have a third shape somewhere in the document.
Shape thirdShape = (Shape)doc.GetChild(NodeType.Shape, 2, true);
groupShape.AppendChild(thirdShape);
```

Quando precisar desagrupar mais tarde, itere sobre `groupShape.GetChildNodes(NodeType.Shape, true)` e reinsira cada filho onde desejar.

```csharp
foreach (Shape child in groupShape.GetChildNodes(NodeType.Shape, true))
{
    // Example: move each child back to the original paragraph.
    firstParagraph.AppendChild(child);
}
firstParagraph.RemoveChild(groupShape); // Remove the empty group container.
```

**Por que isso importa:** Alguns fluxos de trabalho exigem agrupamento temporário (por exemplo, alinhar múltiplos objetos) seguido de desagrupamento para edições individuais posteriores.

## Exemplo completo executável

Abaixo está um programa autocontido que você pode compilar e executar tal como está. Substitua `YOUR_DIRECTORY` por um caminho de pasta real em sua máquina.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Load the document.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath);

        // 2. Retrieve the first two shapes.
        Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true);

        if (firstShape == null || secondShape == null)
        {
            Console.WriteLine("Document must contain at least two shapes.");
            return;
        }

        // 3. Create a GroupShape container.
        GroupShape groupShape = new GroupShape(doc);

        // Optional: define the group’s bounding box.
        groupShape.Bounds = new System.Drawing.RectangleF(100, 100, 300, 200);

        // 4. Add the shapes to the group.
        groupShape.AppendChild(firstShape);
        groupShape.AppendChild(secondShape);

        // 5. Insert the group into the first paragraph.
        Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(groupShape);

        // 6. Save the result.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Grouped shapes saved to {outputPath}");
    }
}
```

**Saída esperada:** Quando você abrir `output.docx`, as duas formas originais aparecerão como um único objeto agrupado. Selecionar o grupo mostra as conhecidas alças de agrupamento do Word, permitindo mover, redimensionar ou girar todo o conjunto junto.

## Conclusão

Agora você sabe como **agrupar formas no Word** usando C# e Aspose.Words, e viu os passos exatos para **adicionar formas ao grupo** e posteriormente manipulá‑las ou desagrupá‑las. Esta técnica é ideal para automatizar layouts de relatórios, criar diagramas compostos ou preparar modelos Word que exigem posicionamento preciso de múltiplos objetos.

Em seguida, explore tópicos relacionados como **como agrupar formas** com diferentes tipos de âncora, aplicar **formatação avançada** a objetos agrupados ou exportar o resultado agrupado para PDF. Experimente aninhar grupos para construir gráficos complexos programaticamente.

Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Inserir Formas em Documentos Word Usando Aspose.Words para .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Criar Forma de Grupo em Documento Word Usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Adicionar Efeito de Sombra a Formas Word – Guia Completo em C#](/words/english/net/programming-with-shapes/add-shadow-effect-to-word-shapes-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}