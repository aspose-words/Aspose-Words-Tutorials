---
category: general
date: 2026-11-22
description: Adicionar forma retangular em um documento Word com Java, definir o tamanho
  da forma, agrupar várias formas e anexar a forma ao grupo de forma eficiente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add rectangle shape
- set shape size
- group multiple shapes
- set shape dimensions
- append shape to group
language: pt
lastmod: 2026-11-22
og_description: Adicionar forma retangular em um documento Word usando Java, definir
  o tamanho da forma, agrupar várias formas e anexar a forma ao grupo em um único
  fluxo de trabalho.
og_image_alt: Screenshot showing a rectangle shape added and grouped in a Word document
  using Java
og_title: Adicionar forma de retângulo e agrupar formas em Java – guia completo
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  headline: Add rectangle shape and group shapes in Java
  type: TechArticle
- description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  name: Add rectangle shape and group shapes in Java
  steps:
  - name: Insert the rectangle shape
    text: The rectangle is the first visual element we want to place inside the document.
      By using the `Shape` constructor with `ShapeType.RECTANGLE`, you get a fully
      editable object.
  - name: Set shape size and dimensions
    text: Set shape size and dimensions
  - name: Create a group shape container
    text: '```java // Step 6: Create a group shape that will hold the rectangle and
      other shapes GroupShape groupShape = builder.insertGroupShape(); ```'
  - name: Append shape to group
    text: Append shape to group
  - name: Save the document
    text: '```java // Save the result to a new file doc.save("output.docx"); } } ```'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shape manipulation
title: Adicionar forma de retângulo e agrupar formas em Java
url: /pt/java/images-shapes/add-rectangle-shape-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Adicionar forma retangular e agrupar formas em Java

Se você precisa **add rectangle shape** a um documento Word com Java, este guia o conduzirá passo a passo. Você também aprenderá como **set shape size**, **group multiple shapes** e **append shape to group** sem sair da IDE.

Trabalhar com gráficos vetoriais dentro de um arquivo DOCX muitas vezes parece equilibrar APIs separadas. Ao final deste tutorial, você terá um programa único e autocontido que cria um retângulo, uma elipse e quaisquer formas adicionais que precisar, e então as agrupa para que se movimentem como um único objeto. Nenhuma ferramenta externa é necessária além do Aspose.Words for Java.

## Pré-requisitos

* Java 17 ou posterior instalado.
* Maven 3.8+ (ou Gradle) para gerenciar dependências.
* Uma licença válida do Aspose.Words for Java (avaliação funciona para testes).
* Uma IDE como IntelliJ IDEA ou VS Code, embora qualquer editor de texto sirva.

Esses requisitos permitem que o código seja compilado e executado em qualquer ambiente de desenvolvimento moderno.

## Etapa 1: Configurar o projeto Maven

Create a new Maven project or add the Aspose.Words dependency to an existing `pom.xml`:

```xml
<project>
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.example</groupId>
  <artifactId>shape‑demo</artifactId>
  <version>1.0.0</version>

  <dependencies>
    <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.12</version>
    </dependency>
  </dependencies>
</project>
```

The dependency pulls in all classes needed for document manipulation, including `Document`, `DocumentBuilder`, `Shape`, and `GroupShape`. Maven will download the JARs automatically when you run `mvn compile`.

## Etapa 2: Carregar o documento e criar um DocumentBuilder

A `DocumentBuilder` provides the fluent API for inserting content. Load an existing DOCX or start from a blank document:

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document or create a new one
        Document doc = new Document("input.docx");          // replace with your path
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Creating the builder early gives you a cursor positioned at the start of the document, ready for shape insertion.

## Adicionar forma retangular a um documento Word

### Etapa 3: Inserir a forma retangular

The rectangle is the first visual element we want to place inside the document. By using the `Shape` constructor with `ShapeType.RECTANGLE`, you get a fully editable object.

```java
        // Step 3: Insert a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        // The shape is not yet sized; we will set its dimensions next.
```

Adding the rectangle at this point does not affect layout until its size is defined and it is appended to a container.

### Definir tamanho e dimensões da forma

#### Etapa 4: Definir largura e altura

Setting the shape’s dimensions determines how it appears on the page. Width and height values are measured in points (1 pt = 1/72 in).

```java
        // Step 4: Set shape size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

You can adjust these numbers to match your design requirements. The same methods apply to any `Shape` instance, so you can reuse them for circles, arrows, or custom drawings.

#### Etapa 5: Inserir o retângulo no documento

Now that the rectangle has a size, place it on the page. The `insertShape` method of `DocumentBuilder` adds the shape at the current cursor position.

```java
        // Insert the rectangle at the builder’s current position
        builder.insertShape(rectangle);
```

At this stage the rectangle appears alone on the page. The next steps show how to combine it with other shapes.

## Agrupar várias formas juntas

Grouping shapes lets you move, rotate, or resize them as a single unit. This is especially useful for creating complex diagrams.

### Etapa 6: Criar um contêiner de group shape

```java
        // Step 6: Create a group shape that will hold the rectangle and other shapes
        GroupShape groupShape = builder.insertGroupShape();
```

The `insertGroupShape` call adds an empty container to the document. Any shapes appended to this container become part of the group.

### Anexar forma ao grupo

#### Etapa 7: Adicionar o retângulo ao grupo

```java
        // Append the previously created rectangle to the group
        groupShape.appendChild(rectangle);
```

Appending moves the rectangle from the document body into the group’s internal collection. The rectangle now respects the group’s transformations.

#### Etapa 8: Adicionar uma elipse para demonstração

```java
        // Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(80);
        ellipse.setHeight(80);
        groupShape.appendChild(ellipse);
```

The ellipse shares the same coordinate space as the rectangle, so you can align them visually by adjusting their `setLeft` and `setTop` properties if needed.

### Etapa 9: Salvar o documento

```java
        // Save the result to a new file
        doc.save("output.docx");
    }
}
```

Running the program generates `output.docx`. Open the file in Microsoft Word or LibreOffice; you’ll see a rectangle and an ellipse grouped together. Selecting either shape highlights the entire group, confirming that **append shape to group** succeeded.

![Add rectangle shape example in Java](image.png){alt="Exemplo de adição de forma retangular em Java"}

*The screenshot shows the rectangle and ellipse inside a single group, ready for joint manipulation.*  
*A captura de tela mostra o retângulo e a elipse dentro de um único grupo, pronta para manipulação conjunta.*

## Por que esta abordagem é importante

* **Single source of truth** – Todas as propriedades da forma são definidas antes da criação do grupo, evitando falhas de layout.
* **Reusability** – Os mesmos métodos `setWidth`/`setHeight` funcionam para qualquer forma, permitindo estender o exemplo para setas, estrelas ou SVGs personalizados.
* **Performance** – Agrupar reduz o número de objetos de desenho que o renderizador do Word precisa manipular, melhorando a velocidade de abertura de documentos grandes.
* **Maintainability** – Ao manter a criação e a lógica de agrupamento das formas juntas, desenvolvedores futuros podem modificar dimensões ou adicionar novas formas sem procurar em código não relacionado.

## Variações comuns e casos de borda

| Cenário | Ajuste |
|----------|------------|
| **Unidades diferentes** | Use a conversão `PointsToPixels` ou defina `Shape.setWrapType(WrapType.INLINE)` para posicionamento inline. |
| **Rotacionar o grupo** | Chame `groupShape.setRotation(45);` para girar todas as formas filhas em 45°. |
| **Adicionar texto a uma forma** | Use `Shape.setText("Label");` após definir o tamanho. |
| **Dimensionamento dinâmico** | Recupere as dimensões da página via `doc.getFirstSection().getPageSetup().getPageWidth()` e calcule os tamanhos das formas proporcionalmente. |

These variations illustrate how the core pattern—**add rectangle shape**, **set shape size**, **group multiple shapes**, **append shape to group**—adapts to many real‑world requirements.

## Conclusão

You now know how to **add rectangle shape** to a Word document using Java, **set shape size**, **group multiple shapes**, and **append shape to group** in a clean, maintainable way. The complete example compiles into a single runnable class, and the resulting DOCX file demonstrates the expected output.

From here you can explore:

* Adicionar rótulos de texto ou hyperlinks a cada forma.
* Aninhar grupos para construir diagramas hierárquicos.
* Exportar o documento para PDF mantendo os grupos de formas.

Feel free to experiment with different dimensions, colors, and additional shape types. Mastering shape manipulation opens the door to automated report generation, dynamic diagrams, and rich document experiences—all directly from Java code.

## O que você deve aprender a seguir?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Inserir Forma Retangular em Java – Agrupar e Posicionar Formas](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [Como criar e inserir formas de elipse e retângulo dentro de um group shape em um documento Word usando Aspose.Words](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [Criar forma retangular em um documento Word usando Java](/words/english/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}