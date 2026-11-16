---
category: general
date: 2026-11-15
description: Crie uma forma retangular no Word com Java e aprenda como adicionar formas
  ao Word, definir as dimensões da forma e salvar o documento do Word de forma eficiente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add shapes to word
- save word document
- set shape dimensions
- define shape size
language: pt
lastmod: 2026-11-15
og_description: Crie uma forma retangular em um documento Word usando Java. Aprenda
  a adicionar formas ao Word, definir as dimensões da forma e salvar o documento Word
  em minutos.
og_image_alt: Screenshot showing a rectangle shape inside a group shape in a Word
  document
og_title: Criar forma de retângulo no Word com Java – guia passo a passo
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  headline: Create rectangle shape in a Word document using Java
  type: TechArticle
- description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  name: Create rectangle shape in a Word document using Java
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well). * Aspose.Words
      for Java 23.10 or newer – you can obtain it from Maven Central. * A basic understanding
      of Java syntax and object‑oriented concepts.'
  - name: Expected output
    text: '* A Word file named `RectangleShapeDemo.docx`. * Inside the first paragraph,
      a group shape containing a 100 pt × 50 pt rectangle. * No text is added, so
      the rectangle appears on a blank page.'
  - name: What’s next?
    text: '* Explore **add shapes to Word** by inserting circles, arrows, or text
      boxes. * Combine multiple shapes into a single `GroupShape` and apply transformations
      (rotate, flip). * Generate reports that embed charts as shapes, then **save
      Word document** as PDF for sharing.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Criar forma de retângulo em um documento Word usando Java
url: /pt/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar forma retangular em um documento Word usando Java

Se você precisa **criar forma retangular** dentro de um arquivo Word, este guia mostra exatamente como fazer isso com Java. Você verá como **adicionar formas ao Word**, controlar o **definir dimensões da forma**, e finalmente **salvar documento Word** sem sair do seu IDE.

Nas seções a seguir você obterá um exemplo completo e executável, uma explicação de cada linha e dicas para armadilhas comuns, como problemas de dimensionamento e compatibilidade de documentos. Nenhuma referência externa é necessária — apenas a biblioteca Aspose.Words for Java.

## What you’ll learn

* Como inicializar um `Document` e um `DocumentBuilder`.
* Como inserir um **group shape** e colocar um retângulo dentro dele.
* Como **definir o tamanho da forma** usando `setWidth` e `setHeight`.
* Como **salvar documento Word** no formato `.docx`.
* Tratamento de casos extremos para diferentes tamanhos de página e configurações de DPI.

### Prerequisites

* Java 17 ou superior (o código também compila com Java 8).
* Aspose.Words for Java 23.10 ou mais recente – você pode obtê-lo no Maven Central.
* Um entendimento básico da sintaxe Java e dos conceitos orientados a objetos.

> **Pro tip:** Se você planeja adicionar mais formas depois (por exemplo, círculos ou caixas de texto), mantenha‑as dentro do mesmo `GroupShape`. Isso facilita mover, rotacionar ou formatar toda a coleção.

## Step 1: Initialise the document and builder

O primeiro passo é criar um arquivo Word em branco e um `DocumentBuilder` que permite escrever conteúdo.  

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Why this matters:* Um `Document` representa o arquivo inteiro, enquanto `DocumentBuilder` fornece métodos de alto nível para inserir texto, tabelas e **shapes**. Sem o builder você teria que manipular nós de baixo nível manualmente.

## Step 2: Insert a group shape to hold multiple shapes

Um **group shape** funciona como um contêiner; você pode adicionar várias formas e tratá‑las como um único objeto depois (por exemplo, mover ou rotacionar juntas).

```java
        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();
```

*Why use a group shape?* Se mais tarde você decidir adicionar setas, círculos ou rótulos ao redor do retângulo, o grupo mantém tudo alinhado. Também simplifica o fluxo de **add shapes to Word**, pois você precisa de apenas uma chamada a `appendChild` para cada nova forma.

## Step 3: Create the rectangle shape

Agora criamos o retângulo real que viverá dentro do grupo. O construtor `Shape` precisa do `Document` proprietário e do tipo de forma desejado.

```java
        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
```

*Why a rectangle?* `ShapeType.RECTANGLE` é a primitiva mais comum para destacar seções, criar marcadores de posição ou desenhar mock‑ups de UI simples diretamente dentro do Word.

## Step 4: Define the rectangle’s size

Definir as dimensões é onde **set shape dimensions** se torna importante. Você pode usar qualquer unidade de medida suportada pelo Aspose.Words; o padrão são pontos (1 pt = 1/72 inch).

```java
        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

> **Note:** Se preferir milímetros, chame `rectangle.setWidth(ConversionUtil.inchesToPoints(1.39));` onde `1.39 in ≈ 35 mm`. Isso demonstra a flexibilidade de **define shape size**.

## Step 5: Add the rectangle to the group shape

Adicionar o retângulo ao grupo criado anteriormente faz com que ele apareça no documento.

```java
        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);
```

Neste ponto o retângulo está posicionado no canto superior‑esquerdo do grupo. Você pode movê‑lo depois com `rectangle.setLeft(...)` e `rectangle.setTop(...)` se precisar de posicionamento preciso.

## Step 6: (Optional) Save the document to see the result

Finalmente, escreva o documento no disco. Esta é a etapa de **save Word document** que produz um arquivo `.docx` que pode ser aberto no Microsoft Word, LibreOffice ou Google Docs.

```java
        // Step 6: Save the document (optional but recommended for verification)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

Executar o programa cria `RectangleShapeDemo.docx` contendo um único retângulo dentro de um group shape. Abrir o arquivo mostra um retângulo branco simples — exatamente do tamanho que você definiu.

### Expected output

* Um arquivo Word chamado `RectangleShapeDemo.docx`.
* Dentro do primeiro parágrafo, um group shape contendo um retângulo de 100 pt × 50 pt.
* Nenhum texto é adicionado, portanto o retângulo aparece em uma página em branco.

## Common variations and edge cases

| Situação | Como adaptar o código |
|-----------|-----------------------|
| **Tamanho de página diferente** (ex.: A4) | Chame `document.getFirstSection().getPageSetup().setPaperSize(PaperSize.A4);` antes de inserir a forma. |
| **DPI mais alto para impressão** | Multiplique largura/altura pelo fator DPI desejado, por exemplo, `rectangle.setWidth(200 * 2);` para resolução dupla. |
| **Adicionar um rótulo de texto dentro do retângulo** | Crie um `Shape` do tipo `TEXT_BOX`, defina seu `setWidth`/`setHeight` para corresponder ao retângulo e, em seguida, adicione‑o ao mesmo `GroupShape`. |
| **Rotacionar o retângulo** | Use `rectangle.setRotationAngle(45);` para rotacionar 45 graus no sentido horário. |
| **Salvar como PDF em vez de DOCX** | Substitua `document.save("output.docx");` por `document.save("output.pdf");` – a mesma API funciona para PDF, preservando o retângulo. |

## Pro tips for a robust implementation

1. **Reuse the builder** – após inserir o group shape, você pode continuar adicionando parágrafos ou tabelas sem criar uma nova instância do builder.
2. **Dispose resources** – embora o coletor de lixo do Java trate a maioria dos objetos, chamar explicitamente `document.close();` (se usar streams) evita vazamentos de manipuladores de arquivo.
3. **Validate dimensions** – antes de chamar `setWidth`/`setHeight`, assegure‑se de que os valores são positivos; valores negativos lançam `IllegalArgumentException`.
4. **Version compatibility** – o código funciona com Aspose.Words 23.x e posteriores. Versões anteriores podem exigir `Shape.setSize(width, height)` em vez dos setters separados.

## Full, runnable example

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();

        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);

        // Optional: set a light gray fill to make it visible in Word
        rectangle.getFillColor() .setRGB(200, 200, 200);

        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);

        // Step 6: Save the document (you can also save as PDF)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

> **Result verification:** Abra `output/RectangleShapeDemo.docx` no Microsoft Word. Você deverá ver um retângulo do tamanho especificado centralizado no topo da primeira página. Se o retângulo aparecer muito pequeno, ajuste os valores passados para `setWidth` e `setHeight`.

## Conclusion

Agora você sabe como **criar forma retangular** em um arquivo Word usando Java, como **adicionar formas ao Word** via um `GroupShape`, como **definir dimensões da forma** e **definir o tamanho da forma**, e finalmente como **salvar documento Word** para distribuição. O mesmo padrão funciona para outros tipos de forma, permitindo construir diagramas complexos programaticamente.

### What’s next?

* Explore **adicionar formas ao Word** inserindo círculos, setas ou caixas de texto.
* Combine várias formas em um único `GroupShape` e aplique transformações (rotacionar, espelhar).
* Gere relatórios que incorporam gráficos como formas, então **salve documento Word** como PDF para compartilhamento.

Sinta‑se à vontade para experimentar as dimensões, cores e posicionamento para adequar ao seu cenário específico. Feliz codificação!

## What Should You Learn Next?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Criar Documento Word Java – Adicionar Forma Retangular com Efeito de Sombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Criar Forma Retangular em Documento Word Java – Guia Completo Passo a Passo](/words/english/java/images-shapes/create-rectangle-shape-in-java-word-document-full-step-by-st/)
- [Criar documento Word java – ocultar forma e definir cor de preenchimento](/words/english/java/images-shapes/create-word-document-java-hide-shape-and-set-fill-color/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}