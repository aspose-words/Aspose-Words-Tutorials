---
category: general
date: 2026-07-16
description: como inserir forma de grupo em Java usando Aspose.Words – adicionar forma
  de retângulo, definir dimensões da forma e criar retângulo e círculo coloridos.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert group
- add rectangle shape
- set shape dimensions
- create colored rectangle
- create colored circle
language: pt
lastmod: 2026-07-16
og_description: 'como inserir forma de grupo em Java: um guia prático para adicionar
  forma retangular, definir dimensões da forma e criar retângulo e círculo coloridos
  com Aspose.Words.'
og_image_alt: Screenshot showing a grouped blue rectangle and red circle in a Java‑generated
  Word document
og_title: Inserir Forma de Grupo em Java – Tutorial Completo do Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  headline: how to insert group shape in Java – Complete Guide
  type: TechArticle
- description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  name: how to insert group shape in Java – Complete Guide
  steps:
  - name: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
    text: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
  - name: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
    text: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
  - name: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
    text: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
  - name: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
    text: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
  - name: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
    text: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shapes
- Document Automation
- Group Shapes
title: Como inserir forma de grupo no Java – Guia completo
url: /pt/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# como inserir group shape em Java – Guia Completo

Já se perguntou **how to insert group shape** em um documento Word usando Java? Você não é o único. Seja construindo um gerador de relatórios ou um criador de folhetos dinâmicos, agrupar formas mantém seu layout organizado e seu código gerenciável.

Neste tutorial, percorreremos os passos exatos para **add rectangle shape**, **set shape dimensions**, e **create colored rectangle** e **create colored circle** usando a biblioteca Aspose.Words. Ao final, você terá um programa executável que produz um .docx file com um retângulo azul e um círculo vermelho cuidadosamente envoltos dentro de um grupo.

## Pré-requisitos

- Java 17 (ou qualquer JDK recente) instalado e configurado.
- Maven ou Gradle para gerenciar dependências.
- Aspose.Words for Java 23.9 ou mais recente – você pode obtê-lo no Maven Central.
- Um entendimento básico da sintaxe Java – nada sofisticado é necessário.

Se você estiver faltando algum desses, baixe o JDK do site da Oracle e adicione a dependência Aspose.Words ao seu `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Agora que a base está pronta, vamos colocar a mão na massa.

## como inserir group shape – Visão geral

A ideia central é simples: criar um `Document`, abrir um `DocumentBuilder`, inserir uma **group shape**, e então colocar formas individuais (um retângulo e um círculo) dentro desse grupo. O grupo funciona como um contêiner, portanto movê‑lo depois deslocará tudo que está dentro – ideal para layouts complexos.

Abaixo está o código completo, pronto‑para‑executar. Sinta‑se à vontade para copiar‑colar em uma nova classe Java chamada `InsertGroupShapeDemo`.

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to insert a group shape, add a rectangle and a circle,
 * set their dimensions, and apply colors using Aspose.Words for Java.
 */
public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to work with it.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape that will contain other shapes.
        Shape group = builder.insertGroupShape();

        // Step 3: Create a blue rectangle, set its size and position, and add it to the group.
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);          // set shape dimensions – width
        rectangle.setHeight(50.0);          // set shape dimensions – height
        rectangle.setLeft(20.0);            // X‑coordinate inside the group
        rectangle.setTop(20.0);             // Y‑coordinate inside the group
        rectangle.getFill().setForeColor(Color.BLUE); // create colored rectangle
        group.appendChild(rectangle);       // add rectangle shape to the group

        // Step 4: Create a red circle, set its size and position, and add it to the same group.
        Shape circle = new Shape(doc, ShapeType.ELLIPSE);
        circle.setWidth(60.0);              // set shape dimensions – width (diameter)
        circle.setHeight(60.0);             // set shape dimensions – height (diameter)
        circle.setLeft(150.0);              // X‑coordinate inside the group
        circle.setTop(20.0);                // Y‑coordinate inside the group
        circle.getFill().setForeColor(Color.RED); // create colored circle
        group.appendChild(circle);          // add circle shape to the group

        // Step 5: Save the document with the grouped shapes.
        doc.save("GroupShapeDemo.docx");
        System.out.println("Document saved successfully.");
    }
}
```

> **Dica profissional:** Os valores `setLeft` e `setTop` são relativos à origem do grupo, não à página. Isso facilita o reposicionamento de todo o grupo posteriormente.

### O que acabou de acontecer?

1. **Document & Builder** – Criamos um arquivo Word vazio e um `DocumentBuilder` que nos permite inserir conteúdo.
2. **Group Shape** – `builder.insertGroupShape()` cria um contêiner. Pense nele como uma pasta para objetos de desenho.
3. **Blue Rectangle** – Instanciamos um `Shape` do tipo `RECTANGLE`, definimos seu tamanho, posição e o preenchemos com azul – este é o passo **create colored rectangle**.
4. **Red Circle** – Mesmo padrão, mas usando `ELLIPSE` para um círculo perfeito, então preenchendo‑o de vermelho – esta é a parte **create colored circle**.
5. **Saving** – Finalmente persistimos tudo em `GroupShapeDemo.docx`.

Execute o programa (`mvn compile exec:java -Dexec.mainClass=InsertGroupShapeDemo`) e abra o arquivo resultante. Você deverá ver um retângulo azul à esquerda e um círculo vermelho à direita, ambos presos dentro de uma única caixa de grupo.

## Adicionando uma Forma de Retângulo

Se você precisar apenas de um retângulo sem agrupar, pode pular a chamada `insertGroupShape()` e anexar o retângulo diretamente ao corpo do documento. Contudo, o agrupamento oferece flexibilidade para mover, girar ou excluir várias formas de uma só vez.

```java
Shape rect = new Shape(doc, ShapeType.RECTANGLE);
rect.setWidth(120);
rect.setHeight(70);
rect.getFill().setForeColor(Color.GREEN);
builder.insertNode(rect);
```

Observe como usamos a lógica **add rectangle shape** aqui. O retângulo aparece na página como um objeto independente. Na maioria dos cenários reais, você desejará o grupo, pois ele preserva o posicionamento relativo.

## Definindo Dimensões da Forma

Quando você vê métodos como `setWidth` e `setHeight`, lembre‑se de que eles aceitam **points** (1/72 inch). Se preferir milímetros, converta primeiro:

```java
double mmToPoints = 72.0 / 25.4;
double widthInMm = 50; // 50 mm
rectangle.setWidth(widthInMm * mmToPoints);
rectangle.setHeight(30 * mmToPoints);
```

Este trecho demonstra **set shape dimensions** com conversão de unidade – útil quando as especificações de design vêm de um mockup de UI que usa unidades métricas.

## Criando um Retângulo Colorido

Colorir uma forma é tão simples quanto chamar `getFill().setForeColor()`. Você pode passar qualquer `java.awt.Color`. Quer um gradiente? Use `setForeColor` para a cor inicial e `setBackColor` para a final.

```java
rectangle.getFill().setForeColor(Color.MAGENTA);
rectangle.getFill().setBackColor(Color.YELLOW);
rectangle.getFill().setFillType(FillType.GRADIENT);
```

Essa é uma maneira rápida de **create colored rectangle** com preenchimento em gradiente ao invés de uma cor sólida.

## Criando um Círculo Colorido

Círculos são apenas elipses com largura e altura iguais. A mesma lógica de cor se aplica:

```java
circle.getFill().setForeColor(new Color(255, 165, 0)); // orange
```

Se precisar de preenchimento transparente, ajuste o canal alfa:

```java
circle.getFill().setForeColor(new Color(0, 0, 255, 128)); // semi‑transparent blue
```

Agora você dominou a técnica **create colored circle**.

## Salvando o Documento

Aspose.Words permite exportar para vários formatos: DOCX, PDF, HTML, PNG, o que quiser. Para esta demonstração, usamos DOCX porque preserva as formas vetoriais perfeitamente.

```java
doc.save("GroupShapeDemo.pdf", SaveFormat.PDF);
```

Alterar o `SaveFormat` é tudo o que precisa para gerar uma versão PDF da mesma arte agrupada.

## Armadilhas Comuns & Como Evitá‑las

- **Esqueceu de adicionar a forma ao grupo?** A forma aparecerá na página, mas não se moverá com o grupo. Sempre chame `group.appendChild(yourShape)`.

## O que Você Deve Aprender a Seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}