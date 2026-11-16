---
category: general
date: 2026-11-15
description: Aprenda a inserir formas em um documento Word e agrupar várias formas
  com o Aspose.Words DocumentBuilder. Inclui exemplos de inserção de forma retangular
  e inserção de múltiplas formas.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert shape
- group multiple shapes
- insert multiple shapes
- insert rectangle shape
language: pt
lastmod: 2026-11-15
og_description: Como inserir forma em um arquivo Word usando Aspose.Words. Este guia
  aborda agrupar várias formas, inserir forma de retângulo e adicionar várias formas
  de forma eficiente.
og_image_alt: Screenshot showing how to insert shape and group multiple shapes in
  a Word document using DocumentBuilder
og_title: Como inserir forma e agrupar várias formas com DocumentBuilder
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  headline: How to insert shape and group multiple shapes using DocumentBuilder in
    C#
  type: TechArticle
- description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  name: How to insert shape and group multiple shapes using DocumentBuilder in C#
  steps:
  - name: Why use a group?
    text: '* **Single‑point transformation** – rotate or resize the whole group with
      one call. * **Logical organization** – the Word document tree reflects the grouping,
      making later edits easier. * **Consistent layout** – moving the group keeps
      the relative positions of its children intact.'
  - name: Adding more shapes – extending **insert multiple shapes** inside the group
    text: 'You can keep calling `InsertShape` while the cursor remains inside the
      `GroupShape`. For example, to add a triangle:'
  - name: Expected output
    text: '* **First two shapes** – a rectangle and an ellipse placed independently
      on the page. * **Grouped block** – a rectangle, an ellipse, and a triangle that
      move together when you click any of them in Word.'
  type: HowTo
tags:
- Aspose.Words
- C#
- DocumentBuilder
- Shape handling
title: Como inserir forma e agrupar várias formas usando DocumentBuilder em C#
url: /pt/net/add-content-using-document-builder/how-to-insert-shape-and-group-multiple-shapes-using-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como inserir forma e agrupar várias formas usando DocumentBuilder em C#

Se você precisa saber **como inserir forma** em um documento Word com Aspose.Words, este guia mostra os passos exatos. Você também aprenderá como **agrupar várias formas** para que se comportem como um único objeto, e como **inserir forma retangular** ao lado de outros gráficos.

A automação de documentos frequentemente requer a adição de vários gráficos—gráficos, logotipos, chamadas—mantendo-os organizados. Ao final deste tutorial, você será capaz de **inserir várias formas**, colocá‑las dentro de um grupo e salvar um layout limpo e reutilizável.

## Pré-requisitos

Antes de começar, certifique‑se de que você tem:

* .NET 6.0 ou posterior instalado  
* Visual Studio 2022 (ou qualquer IDE C#)  
* Uma licença do Aspose.Words para .NET ou uma chave de avaliação gratuita  
* Familiaridade básica com C# e a classe Aspose.Words `DocumentBuilder`  

Você **não** precisa de nenhuma outra biblioteca de terceiros; tudo o que é necessário faz parte do Aspose.Words.

## Etapa 1: Instalar Aspose.Words via NuGet

Abra seu projeto no Visual Studio e execute o seguinte comando no Package Manager Console:

```powershell
Install-Package Aspose.Words
```

O pacote inclui as classes `DocumentBuilder`, `Shape` e `GroupShape` usadas ao longo deste tutorial.

## Etapa 2: Criar uma instância de DocumentBuilder – a base para **como inserir forma**

A primeira linha de código executável é a criação de um `DocumentBuilder`. Este objeto fornece acesso direto à árvore do documento, permitindo que você posicione formas exatamente onde desejar.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Initialise a new blank document
        Document doc = new Document();
        // Create a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // The rest of the tutorial inserts and groups shapes here …
    }
}
```

*Por que isso importa*: `DocumentBuilder` mantém um cursor (o “ponto de inserção”). Cada chamada subsequente de `Insert...` usa esse cursor, razão pela qual mais tarde o movemos para dentro de um `GroupShape` para manter todas as formas juntas.

## Etapa 3: **Inserir forma retangular** – o primeiro gráfico que você adicionará

Um retângulo é um placeholder comum para tabelas, imagens ou chamadas. Use `InsertShape` com `ShapeType.Rectangle` e especifique a largura e altura em pontos (1 pt ≈ 1/72 pol).

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

O retângulo aparece na posição atual do cursor. Você pode personalizar seu preenchimento, estilo de linha ou texto posteriormente, se necessário.

## Etapa 4: Inserir outra forma – uma elipse para variedade visual

Adicionar mais de uma forma demonstra **inserir várias formas**. A elipse ficará após o retângulo no fluxo do documento.

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

Neste ponto, o documento contém duas formas independentes. Se você mover o cursor ou adicionar texto, as formas permanecem onde foram inseridas.

## Etapa 5: **Agrupar várias formas** para que atuem como uma única unidade

Agrupar é essencial quando você precisa mover, girar ou formatar vários gráficos juntos. O código a seguir cria um `GroupShape`, move o cursor do builder para dentro dele e, em seguida, insere as mesmas formas novamente—desta vez elas se tornam filhas do grupo.

```csharp
// 1️⃣ Create a GroupShape and add it to the document tree
GroupShape group = new GroupShape(builder.Document);
builder.InsertNode(group);

// 2️⃣ Position the cursor inside the group so new inserts go into it
builder.MoveTo(group);

// 3️⃣ Insert a rectangle shape inside the group
builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Insert an ellipse shape inside the same group
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

### Por que usar um grupo?

* **Transformação de ponto único** – rotacione ou redimensione todo o grupo com uma única chamada.  
* **Organização lógica** – a árvore do documento Word reflete o agrupamento, facilitando edições posteriores.  
* **Layout consistente** – mover o grupo mantém as posições relativas de seus filhos intactas.

### Adicionando mais formas – estendendo **inserir várias formas** dentro do grupo

Você pode continuar chamando `InsertShape` enquanto o cursor permanece dentro do `GroupShape`. Por exemplo, para adicionar um triângulo:

```csharp
builder.InsertShape(ShapeType.Triangle, 60, 60);
```

Cada chamada respeita o contexto do grupo, portanto o triângulo se torna automaticamente parte do mesmo conjunto agrupado.

## Etapa 6: Salvar o documento e verificar o resultado

Depois que todas as formas forem posicionadas, persista o documento em um arquivo `.docx`. Abrir o arquivo no Microsoft Word (ou em qualquer visualizador compatível) deve mostrar duas formas separadas seguidas por um conjunto agrupado contendo o mesmo retângulo, elipse e triângulo.

```csharp
// Save the document
doc.Save("GroupedShapesDemo.docx");
```

### Saída esperada

* **Primeiras duas formas** – um retângulo e uma elipse posicionados independentemente na página.  
* **Bloco agrupado** – um retângulo, uma elipse e um triângulo que se movem juntos quando você clica em qualquer um deles no Word.

Você pode testar o agrupamento selecionando qualquer forma dentro do grupo; o Word destacará toda a coleção, confirmando que a operação **agrupar várias formas** foi bem‑sucedida.

## Armadilhas comuns e dicas profissionais

| Problema | Por que acontece | Solução |
|----------|------------------|---------|
| Formas aparecem fora da página pretendida | O cursor do builder não foi movido para dentro do `GroupShape` antes da inserção. | Sempre chame `builder.MoveTo(group)` **antes** de qualquer chamada `InsertShape` que pertença ao grupo. |
| Grupo desaparece após salvar | O grupo foi inserido sem ser adicionado à coleção de nós do documento. | Use `builder.InsertNode(group)` imediatamente após criar o `GroupShape`. |
| Tamanho inesperado devido ao DPI do documento | Aspose.Words usa pontos; se você pensar em pixels pode obter dimensões incompatíveis. | Converta pixels para pontos (`points = pixels * 72 / 96`) ou trabalhe diretamente em pontos. |
| Formas se sobrepõem inadvertidamente | Nenhum posicionamento explícito foi definido; o Word as coloca sequencialmente. | Defina `Shape.Left` e `Shape.Top` após a inserção para controlar a posição exata. |

**Dica profissional:** Após agrupar, você pode recuperar a coleção `Shapes` do grupo (`group.Shapes`) para iterar, renomear ou aplicar formatação em massa.

## Etapa 7: Estendendo o exemplo – o que vem a seguir?

Agora que você sabe **como inserir forma**, **inserir forma retangular** e **agrupar várias formas**, pode explorar:

* **Animando formas agrupadas** – defina propriedades de rotação ou inversão no grupo.  
* **Aplicando estilos** – use `Shape.FillColor`, `Shape.LineFormat` ou `Shape.TextBox` para adicionar rótulos.  
* **Exportando para PDF** – o mesmo layout agrupado é renderizado corretamente ao chamar `doc.Save("output.pdf")`.  

Todas essas extensões reutilizam o mesmo fluxo de trabalho `DocumentBuilder`, mantendo seu código limpo e fácil de manter.

## Conclusão

Este tutorial demonstrou **como inserir forma** em um documento Word com Aspose.Words, como **inserir forma retangular**, e como **agrupar várias formas** para que se comportem como um único objeto. Seguindo o código passo a passo, você pode inserir **várias formas** de forma confiável, organizá‑las em grupos e produzir documentos de nível profissional programaticamente.

Sinta‑se à vontade para experimentar diferentes tipos de forma, cores e transformações de grupo. Quando estiver pronto, integre o padrão em soluções maiores de relatórios ou modelagem para automatizar layouts de documentos complexos. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Inserir formas em documentos Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Como criar e inserir formas elipse e retângulo dentro de um group shape em um documento Word usando Aspose.Words](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [Como agrupar formas em um documento Word usando Aspose.Words](/words/english/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}