---
category: general
date: 2026-11-25
description: Como agrupar formas no Word usando Java e como definir as dimensões das
  formas em um arquivo DOCX com Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes in word
- how to set shape dimensions
- set shape size word
language: pt
lastmod: 2026-11-25
og_description: Como agrupar formas no Word com a API Aspose.Words Java e definir
  rapidamente o tamanho da forma no Word. Siga a solução completa passo a passo.
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: Como agrupar formas no Word e definir suas dimensões – Guia Java
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  headline: How to group shapes in Word and set their dimensions programmatically
  type: TechArticle
- description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  name: How to group shapes in Word and set their dimensions programmatically
  steps:
  - name: Expected output
    text: '* A Word document (`GroupShape.docx`) with one page. * A `GroupShape` containing
      a 100 × 50 pt rectangle and an 80 × 80 pt ellipse. * Selecting either shape
      selects the whole group.'
  - name: How to change the position of the grouped shapes?
    text: 'After creating the `GroupShape`, you can set its `left` and `top` properties:'
  - name: What if I need to add more than two shapes?
    text: '`GroupShape` works like any other container node. Call `groupShape.appendChild(yourShape)`
      for each additional shape. The API does not limit the number of children.'
  - name: Can I apply style (fill color, line weight) to individual shapes?
    text: 'Yes. Each `Shape` object exposes formatting properties:'
  - name: Does the code work with older Aspose.Words versions?
    text: The `insertGroupShape` method was introduced in version 24.9. If you are
      on an earlier version, you’ll need to create a `GroupShape` manually via the
      node tree, which is more involved. Upgrading is the recommended path.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- shapes
title: Como agrupar formas no Word e definir suas dimensões programaticamente
url: /pt/java/images-shapes/how-to-group-shapes-in-word-and-set-their-dimensions-program/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como agrupar formas no Word e definir suas dimensões programaticamente

Se você precisa **como agrupar formas no Word** e controlar seu tamanho exato, este guia mostra uma solução completa e executável. Usando Aspose.Words for Java você pode criar um retângulo, uma elipse, adicioná-los a um `GroupShape` e então **como definir dimensões da forma** como largura e altura em um único arquivo DOCX.

Você aprenderá a:

* Criar um novo documento Word do zero.  
* Inserir um `GroupShape` (nova API na versão 24.9).  
* Adicionar um retângulo e uma elipse ao grupo.  
* **Definir tamanho da forma no Word** precisamente com `setWidth` e `setHeight`.  
* Salvar o documento no disco.

Nenhuma ferramenta externa é necessária — apenas Java 17+, Maven e a biblioteca Aspose.Words for Java.

## Pré-requisitos

* Java Development Kit 17 ou superior.  
* Maven (ou Gradle) para gerenciamento de dependências.  
* Aspose.Words for Java 24.9 ou posterior (a API `GroupShape` foi introduzida na 24.9).  
* Familiaridade básica com a sintaxe Java e conceitos orientados a objetos.

Se você ainda não adicionou o Aspose.Words ao seu projeto, inclua a seguinte dependência Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## Etapa 1: Criar um novo documento e um DocumentBuilder

A classe `Document` representa o arquivo Word completo, enquanto `DocumentBuilder` fornece uma maneira conveniente de adicionar conteúdo.

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Por que esta etapa?*  
Criar um `Document` novo fornece uma tela limpa. `DocumentBuilder` é o ajudante de alto nível que permite inserir parágrafos, tabelas e, neste caso, formas.

## Etapa 2: Inserir um GroupShape (nova API na versão 24.9)

Um `GroupShape` funciona como um contêiner; qualquer forma que você adicionar passa a fazer parte do mesmo grupo visual.

```java
        // Step 2: Insert a GroupShape (new API in version 24.9)
        GroupShape groupShape = builder.insertGroupShape();
```

*Por que usar `GroupShape`?*  
Agrupar formas simplifica mover, girar ou aplicar formatação a vários objetos simultaneamente. A API foi adicionada na 24.9, portanto versões mais antigas não compilarão esta linha.

## Etapa 3: Criar um retângulo, definir seu tamanho e adicioná-lo ao grupo

Aqui demonstramos **como definir dimensões da forma** para um retângulo.

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);   // height in points
        groupShape.appendChild(rectangle);
```

*Por que definir largura e altura explicitamente?*  
O Word armazena o tamanho da forma em pontos. Ao chamar `setWidth` e `setHeight` você controla a área visual exata, o que é essencial quando você precisa de layout preciso ou ao exportar para PDF.

## Etapa 4: Criar uma elipse, definir seu tamanho e adicioná-la ao mesmo grupo

A mesma técnica de **definir tamanho da forma no Word** funciona para qualquer tipo de forma.

```java
        // Step 4: Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(document, ShapeType.ELLIPSE);
        ellipse.setWidth(80.0);
        ellipse.setHeight(80.0);
        groupShape.appendChild(ellipse);
```

*Por que adicionar a elipse ao mesmo `GroupShape`?*  
Ambas as formas se moverão juntas como uma única unidade. Isso é útil para criar ícones, logotipos ou diagramas complexos que precisam permanecer alinhados.

## Etapa 5: Salvar o documento com as formas agrupadas

Finalmente, persista o arquivo DOCX no disco.

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShape.docx");
    }
}
```

Executar este programa produz um arquivo chamado **GroupShape.docx** que contém um retângulo e uma elipse agrupados. Ao abrir o arquivo no Microsoft Word, você verá as duas formas comportarem‑se como um único objeto — você pode arrastar, redimensionar ou girá‑las juntas.

### Saída esperada

* Um documento Word (`GroupShape.docx`) com uma página.  
* Um `GroupShape` contendo um retângulo de 100 × 50 pt e uma elipse de 80 × 80 pt.  
* Selecionar qualquer forma seleciona todo o grupo.

## Perguntas comuns e casos de borda

### Como alterar a posição das formas agrupadas?

Depois de criar o `GroupShape`, você pode definir suas propriedades `left` e `top`:

```java
groupShape.setLeft(150.0);
groupShape.setTop(200.0);
```

Essas coordenadas também são medidas em pontos.

### E se eu precisar adicionar mais de duas formas?

`GroupShape` funciona como qualquer outro nó contêiner. Chame `groupShape.appendChild(yourShape)` para cada forma adicional. A API não limita o número de filhos.

### Posso aplicar estilo (cor de preenchimento, espessura da linha) a formas individuais?

Sim. Cada objeto `Shape` expõe propriedades de formatação:

```java
rectangle.getFillColor().setColor(Color.BLUE);
ellipse.getStroke().setWeight(2.0);
```

### O código funciona com versões mais antigas do Aspose.Words?

O método `insertGroupShape` foi introduzido na versão 24.9. Se você estiver em uma versão anterior, precisará criar um `GroupShape` manualmente via a árvore de nós, o que é mais complexo. Atualizar é o caminho recomendado.

## Dicas profissionais

* **Use points for consistency** – A unidade interna do Word é o ponto (1/72 polegada). Converter de pixels ou centímetros pode gerar tamanhos inesperados.  
* **Group before positioning** – Posicione o `GroupShape` depois de adicionar todos os seus filhos; caso contrário, pode ser necessário recalcular os deslocamentos.  
* **Reuse the DocumentBuilder** – Você pode inserir múltiplos grupos no mesmo documento movendo o cursor do builder (`builder.moveTo`) antes de cada chamada `insertGroupShape`.

## Conclusão

Agora você tem um exemplo completo, de ponta a ponta, de **como agrupar formas no Word** e **como definir dimensões da forma** usando Aspose.Words for Java. O tutorial abordou a criação de um documento, inserção de um `GroupShape`, adição de um retângulo e uma elipse, definição de seu tamanho exato e salvamento do resultado.  

A partir daqui você pode explorar:

* Adicionar caixas de texto ou imagens ao mesmo grupo.  
* Animar formas agrupadas com os recursos de SmartArt do Word (via a API).  
* Exportar as formas agrupadas para PDF ou SVG para uso na web.

Sinta‑se à vontade para experimentar diferentes tipos de formas, tamanhos e posições — o agrupamento oferece controle poderoso sobre layouts complexos em documentos Word.

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Como criar um documento Word em branco e agrupar formas em Java](/words/english/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/)
- [Como agrupar formas no Word com Java – guia completo](/words/english/java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}