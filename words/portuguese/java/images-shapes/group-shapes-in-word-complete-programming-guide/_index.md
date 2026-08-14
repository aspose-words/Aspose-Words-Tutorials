---
category: general
date: 2026-08-14
description: Agrupe formas no Word com Java usando Aspose.Words. Aprenda como criar
  uma forma retangular, definir as dimensões da forma e agrupar várias formas em um
  documento Word em branco.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create rectangle shape
- set shape dimensions
- group multiple shapes
- build blank word document
language: pt
lastmod: 2026-08-14
og_description: Agrupe formas no Word usando Aspose.Words para Java. Crie um documento
  Word em branco, crie uma forma retangular, defina as dimensões da forma e agrupe
  várias formas em minutos.
og_image_alt: Screenshot showing grouped rectangle shapes in a Word document created
  with Java
og_title: Agrupar formas no Word – exemplo Java para desenvolvedores
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Group shapes in Word with Java using Aspose.Words. Learn how to create
    rectangle shape, set shape dimensions, and group multiple shapes in a blank Word
    document.
  headline: Group shapes in Word – complete programming guide
  type: TechArticle
- questions:
  - answer: Overlap is allowed; Word will render them in the order they were added.
      Use `setZOrder` if you need explicit stacking.
    question: What if the shapes overlap?
  - answer: No. A `GroupShape` is confined to a single page because its coordinate
      system is page‑relative.
    question: Can I group shapes across different pages?
  - answer: Each child keeps its own formatting (fill color, line style). To apply
      a uniform style, iterate over `groupShape.getChildNodes()` and set properties
      programmatically.
    question: Do grouped shapes inherit formatting?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: Agrupar formas no Word – guia completo de programação
url: /pt/java/images-shapes/group-shapes-in-word-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Agrupar formas no Word – guia completo de programação

Se você precisa **agrupar formas no Word**, este tutorial o guiará por todo o processo com Java e Aspose.Words. Você aprenderá como **criar um documento Word em branco**, **criar forma retangular**, **definir dimensões da forma** e, finalmente, **agrupar várias formas** para que se comportem como um único objeto.

Trabalhar com formas em um arquivo Word muitas vezes parece desenhar em uma tela sem pincel. Ao final deste guia, você terá um trecho de código reutilizável que pode inserir em qualquer projeto Java, seja gerando relatórios, faturas ou modelos personalizados.

## O que você precisará

- Java 8 ou superior
- Aspose.Words for Java (a versão mais recente, por exemplo, 24.9)
- Uma IDE como IntelliJ IDEA ou Eclipse
- Familiaridade básica com programação orientada a objetos

Todos esses pré-requisitos são gratuitos para instalar, e o código abaixo compila com uma única dependência Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

## Etapa 1: Criar documento Word em branco e inicializar o builder

A primeira coisa que você deve fazer é **criar um documento Word em branco**. Isso fornece uma tela limpa na qual você pode inserir formas posteriormente.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder lets you add content programmatically
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` representa o arquivo *.docx* completo, enquanto `DocumentBuilder` é o auxiliar que insere parágrafos, tabelas e formas. Inicializar ambos os objetos é a base para qualquer tarefa de automação do Word.

## Etapa 2: Inserir um contêiner de forma de grupo

Uma **group shape** funciona como uma pasta que pode conter outras formas. Primeiro criamos o contêiner com um tamanho fixo de 400 pt × 200 pt.

```java
        // Insert a group shape that will hold other shapes (400 pt × 200 pt)
        GroupShape groupShape = builder.insertGroupShape(400, 200);
```

O método `insertGroupShape` retorna um objeto `GroupShape`. Todas as formas subsequentes que você deseja tratar como uma única unidade devem ser adicionadas a esse objeto.

## Etapa 3: Criar formas retangulares e definir dimensões da forma

Agora nós **criamos objetos de forma retangular**, configuramos seu tamanho e os posicionamos dentro do grupo. Esta etapa também demonstra como **definir dimensões da forma** com precisão.

```java
        // ---- First rectangle -------------------------------------------------
        Shape rectangle1 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle1.setWidth(150);   // set shape dimensions: width = 150 pt
        rectangle1.setHeight(100);  // set shape dimensions: height = 100 pt
        rectangle1.setTop(20);      // vertical offset inside the group
        rectangle1.setLeft(20);     // horizontal offset inside the group
        groupShape.appendChild(rectangle1); // add to the group

        // ---- Second rectangle ------------------------------------------------
        Shape rectangle2 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle2.setWidth(150);
        rectangle2.setHeight(100);
        rectangle2.setTop(20);
        rectangle2.setLeft(200);    // place it beside the first rectangle
        groupShape.appendChild(rectangle2);
```

Ambos os retângulos compartilham as mesmas dimensões, mas suas propriedades `left` diferem, de modo que aparecem lado a lado. Você pode alterar `setTop` e `setLeft` para organizar qualquer layout que precisar.

## Etapa 4: Salvar o documento contendo os retângulos agrupados

Depois que as formas estão dentro do grupo, basta salvar o `Document`. O arquivo resultante mostrará dois retângulos que se movem juntos quando selecionados.

```java
        // Save the document to disk
        String outputPath = "GroupShape.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Executar o programa cria `GroupShape.docx` no diretório de trabalho. Abra-o no Microsoft Word, selecione um retângulo e você perceberá que todo o grupo se move como uma unidade — exatamente o que **agrupar formas no Word** pretende fazer.

![Group shapes in Word example](group-shapes.png){alt="Exemplo de formas agrupadas no Word"}

*Figura: Duas formas retangulares agrupadas em um documento Word.*

## Dica profissional: Reutilizar a mesma forma de grupo

Se precisar adicionar mais formas posteriormente (por exemplo, círculos, caixas de texto), mantenha uma referência a `groupShape` e continue chamando `appendChild`. Isso evita recriar o contêiner e garante que todos os membros permaneçam sincronizados.

```java
        // Example: add a third shape later
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(120);
        ellipse.setHeight(80);
        ellipse.setTop(130);
        ellipse.setLeft(140);
        groupShape.appendChild(ellipse);
```

## Casos limites e perguntas comuns

- **E se as formas se sobrepuserem?** Sobreposição é permitida; o Word as renderiza na ordem em que foram adicionadas. Use `setZOrder` se precisar de empilhamento explícito.
- **Posso agrupar formas em páginas diferentes?** Não. Um `GroupShape` está confinado a uma única página porque seu sistema de coordenadas é relativo à página.
- **Formas agrupadas herdam formatação?** Cada filho mantém sua própria formatação (cor de preenchimento, estilo de linha). Para aplicar um estilo uniforme, itere sobre `groupShape.getChildNodes()` e defina as propriedades programaticamente.

## Código-fonte completo para referência

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // 1. Build blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert group shape container (400 pt × 200 pt)
        GroupShape groupShape = builder.insertGroupShape(400, 200);

        // 3. Create first rectangle and set shape dimensions
        Shape rectangle1 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle1.setWidth(150);
        rectangle1.setHeight(100);
        rectangle1.setTop(20);
        rectangle1.setLeft(20);
        groupShape.appendChild(rectangle1);

        // 4. Create second rectangle and set shape dimensions
        Shape rectangle2 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle2.setWidth(150);
        rectangle2.setHeight(100);
        rectangle2.setTop(20);
        rectangle2.setLeft(200);
        groupShape.appendChild(rectangle2);

        // 5. Save the document containing the grouped rectangles
        String outputPath = "GroupShape.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Executar o programa produz um arquivo DOCX onde os dois retângulos estão **agrupados**. Selecionar qualquer retângulo move ambos, confirmando que você agrupou com sucesso **várias formas**.

## Conclusão

Agora você sabe como **agrupar formas no Word** usando Java, desde **criar um documento Word em branco** até **criar forma retangular**, **definir dimensões da forma**, e finalmente **agrupar várias formas** em um único objeto móvel. Esse padrão escala para qualquer número de formas e pode ser combinado com texto, imagens ou gráficos para criar documentos ricos e programáticos.

### O que vem a seguir?

- Explore **agrupar várias formas** com diferentes tipos (elipses, setas, caixas de texto).
- Aplique cores de preenchimento ou bordas chamando `shape.getFillColor()` e `shape.getLine().setColor()`.
- Insira a forma agrupada em uma célula de tabela para relatórios estruturados.
- Combine esta abordagem com mesclagem de correspondência para gerar contratos personalizados que incluam gráficos de marca.

Sinta-se à vontade para experimentar, adaptar as dimensões ou incorporar conteúdo adicional. Quando você dominar o agrupamento, seus scripts de automação do Word se tornarão muito mais flexíveis e fáceis de manter. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá-lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Usando formas de documento no Aspose.Words para Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Criar documento Word Java – Adicionar forma retangular com efeito de sombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Criar forma de grupo em documento Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}