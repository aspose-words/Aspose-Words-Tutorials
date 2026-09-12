---
category: general
date: 2026-09-11
description: Aprenda a criar um documento Word, adicionar uma forma retangular e definir
  as dimensões da forma com Aspose.Words. Guia passo a passo em C# para dimensionamento
  preciso de formas.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- add rectangle shape
- set shape size
- create shapes in word
- set shape dimensions
language: pt
lastmod: 2026-09-11
og_description: Crie um documento Word com Aspose.Words em C#. Este guia mostra como
  adicionar uma forma retangular, definir o tamanho da forma e gerenciar as dimensões
  da forma programaticamente.
og_image_alt: Screenshot of a rectangle shape inside a grouped shape in a newly created
  Word document
og_title: Criar documento Word com formas – tutorial Aspose.Words C#
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document, add rectangle shape, and set shape
    dimensions with Aspose.Words. Step‑by‑step C# guide for precise shape sizing.
  headline: How to create word document with shapes using Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Como criar documento Word com formas usando Aspose.Words em C#
url: /pt/net/programming-with-shapes/how-to-create-word-document-with-shapes-using-aspose-words-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar documento Word com formas usando Aspose.Words em C#

Se você precisa **criar documento Word** que contenha gráficos personalizados, pode fazer isso totalmente por código. Este tutorial orienta você na criação de um arquivo Word, na adição de uma forma retangular e no controle de cada dimensão da forma. Ao final, você terá um trecho reutilizável que pode ser inserido em qualquer projeto .NET.

Você aprenderá como **adicionar forma retangular**, **definir o tamanho da forma** e **definir as dimensões da forma** dentro de um contêiner agrupado. O exemplo usa Aspose.Words 13.9, mas os conceitos se aplicam a versões posteriores também. Não é necessário ter experiência prévia com a API de desenho da Aspose — apenas conhecimentos básicos de C#.

## Pré-requisitos

- .NET 6.0 ou superior instalado  
- Pacote NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)  
- Uma IDE como Visual Studio 2022 (qualquer editor que suporte C# funciona)  

Ter essas ferramentas prontas permite que você execute o código imediatamente, sem configuração adicional.

## Etapa 1: Inicializar o documento e o builder – criar os fundamentos do documento Word

A primeira operação é instanciar um objeto `Document` e um `DocumentBuilder`. O `Document` representa o próprio arquivo, enquanto o `DocumentBuilder` fornece uma API fluente para inserção de conteúdo.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Create a new, empty Word document
        Document doc = new Document();

        // DocumentBuilder gives us a cursor to insert nodes
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Por que isso importa:**  
Criar o documento antecipadamente fornece uma tela limpa. O cursor do builder começa no primeiro parágrafo, que é onde mais tarde **criaremos formas no Word**.

## Etapa 2: Construir um GroupShape para conter múltiplos gráficos

Um `GroupShape` funciona como um contêiner; você pode mover, girar ou redimensionar todo o grupo como uma única unidade. Aqui definimos a largura e a altura do contêiner em pontos (1 pt ≈ 1/72 in).

```csharp
        // Define a group that is 300 pt wide and 200 pt high
        GroupShape group = new GroupShape(doc, 300, 200);

        // Position the group 50 pt from the left and top margins
        group.Left = 50;
        group.Top  = 50;
```

**Por que isso importa:**  
Agrupar formas simplifica o gerenciamento de layout. Se mais tarde precisar adicionar outras formas (por exemplo, círculos ou caixas de texto), elas herdarão a posição e a escala do grupo.

## Etapa 3: Criar uma forma retangular e configurar suas dimensões

Agora adicionamos o retângulo propriamente dito. O construtor `Shape` requer a referência ao documento e o tipo da forma. Após a criação, definimos explicitamente **o tamanho da forma** e **as dimensões da forma**.

```csharp
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);

        // Set the rectangle’s width to 100 pt and height to 50 pt
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height

        // Position the rectangle 10 pt from the group’s left/top edges
        rectangle.Left = 10;
        rectangle.Top  = 10;
```

**Por que isso importa:**  
Especificar largura, altura, esquerda e topo fornece controle pixel‑perfect sobre a forma. Isso é essencial quando o documento deve corresponder a uma especificação de design ou a um formulário impresso.

## Etapa 4: Montar o grupo anexando o retângulo

Anexar o retângulo ao `GroupShape` o torna um nó filho. Você pode adicionar quantos filhos precisar antes de inserir o grupo no documento.

```csharp
        // Add the rectangle to the group
        group.AppendChild(rectangle);
```

**Dica:** Se planeja adicionar uma segunda forma, crie-a da mesma maneira e chame `group.AppendChild(secondShape)`. Todos os filhos compartilham o sistema de coordenadas do grupo.

## Etapa 5: Inserir a forma agrupada no documento e salvar

Com o grupo totalmente construído, colocamos ele no parágrafo atual. A propriedade `CurrentParagraph` do builder fornece acesso direto à árvore de nós subjacente.

```csharp
        // Insert the group into the first paragraph of the document
        builder.CurrentParagraph.AppendChild(group);

        // Save the document to disk (adjust the path as needed)
        doc.Save("GroupShape.docx");

        // Optional: open the file automatically (Windows only)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**Por que isso importa:**  
Anexar o grupo a um parágrafo garante que a forma apareça em linha com o fluxo de texto. Salvar o documento finaliza a operação de **criar documento Word**.

## Variações comuns e casos de borda

| Cenário | Ajuste |
|----------|------------|
| **Orientação de página diferente** | Defina `doc.FirstSection.PageSetup.Orientation = Orientation.Landscape;` antes de criar o grupo. |
| **Múltiplos retângulos** | Crie objetos `Shape` adicionais e chame `group.AppendChild(newRect)` para cada um. |
| **Tamanho dinâmico baseado no conteúdo** | Calcule largura/altura a partir das dimensões da imagem ou métricas de texto, então atribua a `rectangle.Width` / `rectangle.Height`. |
| **Exportar para PDF** | Após `doc.Save`, chame `doc.Save("GroupShape.pdf", SaveFormat.Pdf);`. |
| **Compatibilidade com versões antigas do Word** | Salve usando `SaveFormat.Doc` em vez de `Docx` para compatibilidade com Word 97‑2003. |

Essas variações ilustram como a mesma lógica central pode ser adaptada a diversas necessidades do mundo real.

## Exemplo completo, executável

Abaixo está o programa completo que você pode copiar, colar e executar. Ele inclui todas as diretivas `using`, um ponto de entrada `Main` e comentários que explicam cada linha.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Define a group shape (300 pt × 200 pt) positioned at (50, 50)
        GroupShape group = new GroupShape(doc, 300, 200);
        group.Left = 50;
        group.Top  = 50;

        // 3️⃣ Create a rectangle (100 pt × 50 pt) positioned at (10, 10) inside the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height
        rectangle.Left = 10;
        rectangle.Top  = 10;

        // 4️⃣ Add the rectangle to the group
        group.AppendChild(rectangle);

        // 5️⃣ Insert the group into the first paragraph and save the file
        builder.CurrentParagraph.AppendChild(group);
        doc.Save("GroupShape.docx");

        // Open the resulting file automatically (optional)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**Saída esperada:**  
Ao abrir *GroupShape.docx*, a primeira página mostra um retângulo com borda cinza posicionado 50 pt da margem esquerda/superior, com o próprio retângulo deslocado 10 pt dentro do grupo. As dimensões correspondem aos valores definidos no código.

## Conclusão

Agora você sabe como **criar documento Word**, **adicionar forma retangular** e definir com precisão **o tamanho da forma** e **as dimensões da forma** usando Aspose.Words. A abordagem de forma agrupada mantém seu layout flexível e pronto para extensões futuras, como gráficos adicionais ou caixas de texto.

Em seguida, explore tópicos relacionados como **criar formas no Word** para círculos, setas ou caminhos SVG personalizados, e aprenda a **definir a cor de preenchimento da forma** ou **aplicar rotação**. Experimente diferentes unidades de medida para ver como o Word renderiza pontos versus centímetros, e integre o código em pipelines maiores de geração de documentos.

Feliz codificação, e sinta-se à vontade para adaptar este padrão a qualquer cenário de geração automática de relatórios ou preenchimento de formulários que encontrar!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}