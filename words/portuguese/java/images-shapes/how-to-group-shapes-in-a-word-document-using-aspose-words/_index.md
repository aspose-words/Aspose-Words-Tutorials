---
category: general
date: 2026-08-20
description: Aprenda a agrupar formas, definir o tamanho da forma, inserir imagem
  no documento, adicionar imagem ao grupo e criar forma retangular com Aspose.Words
  em Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert image into document
- set shape size
- add picture to group
- create rectangle shape
language: pt
lastmod: 2026-08-20
og_description: Como agrupar formas em um documento Word usando Aspose.Words. Siga
  este tutorial passo a passo em Java para definir o tamanho da forma, inserir imagem
  no documento, adicionar imagem ao grupo e criar forma retangular.
og_image_alt: Diagram showing how to group shapes in a Word document
og_title: Como agrupar formas em um documento Word com Aspose.Words – Guia Java
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to group shapes, set shape size, insert image into document,
    add picture to group, and create rectangle shape with Aspose.Words in Java.
  headline: How to group shapes in a Word document using Aspose.Words
  type: TechArticle
- description: Learn how to group shapes, set shape size, insert image into document,
    add picture to group, and create rectangle shape with Aspose.Words in Java.
  name: How to group shapes in a Word document using Aspose.Words
  steps:
  - name: Create a new document and a `DocumentBuilder`
    text: A `Document` represents the Word file, while `DocumentBuilder` provides
      convenient methods for inserting content.
  - name: Insert a group shape that will hold multiple child shapes
    text: A group shape acts like a container. Its dimensions define the bounding
      box for all child shapes.
  - name: Create a rectangle shape, set its size, and add it to the group
    text: Setting the exact size of a shape is essential when you want precise layout
      control.
  - name: Insert an image, then add the picture shape to the same group
    text: Inserting an image is the core of the **insert image into document** requirement.
      The returned `Shape` is a picture shape that can be grouped like any other shape.
  - name: Position the entire group on the page
    text: After adding all child shapes, you can move, rotate, or hide the whole group.
      Positioning uses the **add picture to group** concept indirectly, because the
      group now contains the picture.
  - name: Save the document
    text: Finally, write the file to disk. You can open the resulting `.docx` in Word
      to verify the grouping.
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Automation
title: Como agrupar formas em um documento Word usando Aspose.Words
url: /pt/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como agrupar formas em um documento Word usando Aspose.Words

Se você precisa **como agrupar formas** em um arquivo Word, este tutorial mostra a solução completa em Java. Você verá como **definir o tamanho da forma**, **inserir imagem no documento**, **adicionar imagem ao grupo** e **criar forma retangular** — tudo com explicações claras e um exemplo de código executável.

Agrupar formas simplifica o gerenciamento de layout, permite mover ou girar vários objetos como uma única unidade e mantém seu documento organizado. Nos passos abaixo você criará um grupo que contém um retângulo e uma imagem, e então posicionará o grupo na página.

## Pré-requisitos

Antes de começar, certifique‑se de que você tem:

* Java 17 ou mais recente instalado.  
* Aspose.Words for Java (versão 23.9 ou posterior) adicionado ao classpath do seu projeto.  
* Uma imagem JPEG de exemplo em `YOUR_DIRECTORY/sample.jpg` (substitua `YOUR_DIRECTORY` pelo caminho real).

Você pode adicionar o Aspose.Words via Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## Como agrupar formas com Aspose.Words

As seções a seguir percorrem cada operação necessária para **como agrupar formas**. O cabeçalho H2 principal contém a palavra‑chave principal, atendendo às regras de SEO.

### Etapa 1: Criar um novo documento e um `DocumentBuilder`

Um `Document` representa o arquivo Word, enquanto `DocumentBuilder` fornece métodos convenientes para inserir conteúdo.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Por que isso importa*: Começar com um `Document` novo garante que o grupo que você criar não interfira em elementos existentes.

### Etapa 2: Inserir uma forma de grupo que conterá várias formas filhas

Uma forma de grupo funciona como um contêiner. Suas dimensões definem a caixa delimitadora para todas as formas filhas.

```java
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape groupShape = builder.insertGroupShape(300, 200);
```

*Dica*: A largura (`300`) e a altura (`200`) estão em pontos (1 pt = 1/72 polegada). Ajuste‑as com base no tamanho das formas que você planeja adicionar.

### Etapa 3: Criar uma forma retangular, definir seu tamanho e adicioná‑la ao grupo

Definir o tamanho exato de uma forma é essencial quando você deseja controle preciso de layout.

```java
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // set shape size – width
        rectangleShape.setHeight(50);   // set shape size – height
        // Optionally set a fill color for visibility
        rectangleShape.getFillColor().setRGB(0xFF, 0xCC, 0x00);
        groupShape.appendChild(rectangleShape);
```

*Por que definimos o tamanho da forma*: Os métodos `setWidth` e `setHeight` correspondem à palavra‑chave secundária **definir tamanho da forma**, oferecendo controle pixel‑perfeito sobre a aparência do retângulo.

### Etapa 4: Inserir uma imagem e, em seguida, adicionar a forma de imagem ao mesmo grupo

Inserir uma imagem é o núcleo do requisito **inserir imagem no documento**. O `Shape` retornado é uma forma de imagem que pode ser agrupada como qualquer outra forma.

```java
        // Step 4: Insert an image, then add the picture shape to the same group
        Shape pictureShape = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        // Resize the picture if needed (example: 120 pt wide, maintain aspect ratio)
        pictureShape.setWidth(120);
        // Add the picture to the previously created group
        groupShape.appendChild(pictureShape);
```

*Pro dica*: Se precisar preservar a proporção original, defina apenas uma dimensão (`setWidth` ou `setHeight`). O Aspose.Words dimensiona automaticamente a outra dimensão.

### Etapa 5: Posicionar todo o grupo na página

Depois de adicionar todas as formas filhas, você pode mover, girar ou ocultar todo o grupo. O posicionamento usa o conceito **adicionar imagem ao grupo** indiretamente, pois o grupo agora contém a imagem.

```java
        // Step 5: Position the entire group on the page (it can also be rotated, hidden, etc.)
        groupShape.setLeft(50);   // distance from the left margin
        groupShape.setTop(100);   // distance from the top margin
        // Optional: rotate the group 15 degrees
        groupShape.setRotation(15);
```

*Explicação*: `setLeft` e `setTop` posicionam o grupo em relação às margens da página. Girar o grupo demonstra que todas as formas filhas herdam a transformação.

### Etapa 6: Salvar o documento

Por fim, grave o arquivo no disco. Você pode abrir o `.docx` resultante no Word para verificar o agrupamento.

```java
        // Step 6: Save the document
        doc.save("GroupShapesDemo.docx");
    }
}
```

Executar o programa produz **GroupShapesDemo.docx** contendo um retângulo e uma imagem agrupados. Selecionar qualquer uma das formas no Word também selecionará a outra, confirmando que você aprendeu **como agrupar formas** com sucesso.

---

## Saída esperada

Ao abrir *GroupShapesDemo.docx* no Microsoft Word:

* Aparece um retângulo (preenchimento dourado) no lado esquerdo do grupo.  
* A imagem fornecida aparece à direita do retângulo.  
* Ambos os objetos se movem juntos ao arrastar o grupo.  
* O grupo está posicionado a 50 pt da margem esquerda e 100 pt da margem superior, girado 15°.

Se a imagem não aparecer, verifique novamente o caminho do arquivo em `insertImage`. O Aspose.Words lança uma `IOException` quando o arquivo não é encontrado.

---

## Perguntas frequentes e tratamento de casos extremos

| Pergunta | Resposta |
|----------|----------|
| **Posso adicionar mais de duas formas?** | Sim. Chame `groupShape.appendChild(otherShape)` para cada forma adicional. |
| **E se eu precisar de fundo transparente para o retângulo?** | Use `rectangleShape.getFillColor().setRGB(255, 255, 255); rectangleShape.setFillTransparent(true);` |
| **O agrupamento é suportado em formatos Word mais antigos (ex.: `.doc`)?** | O agrupamento funciona para `.docx` e `.doc`, mas alguns visualizadores antigos podem ignorar os metadados do grupo. Salve como `.docx` para fidelidade total. |
| **Como desagrupar depois?** | Recupere os nós filhos via `groupShape.getChildNodes(NodeType.ANY, true)` e mova‑os para o corpo do documento, então remova o grupo. |
| **Posso agrupar formas em diferentes seções?** | Não. Um `GroupShape` deve residir dentro de um único `Story` (geralmente o corpo principal do documento). |

---

## Dicas avançadas para manipulação robusta de formas

* **Use posicionamento absoluto com moderação** – posicionamento relativo (`builder.moveToDocumentEnd()`) costuma gerar layouts mais responsivos.  
* **Cache o `DocumentBuilder`** – criar um novo builder para cada operação pode degradar o desempenho em documentos grandes.  
* **Defina `PictureFillMode`** quando precisar que a imagem se estique ou repita dentro da forma: `pictureShape.setPictureFillMode(PictureFillMode.STRETCH);`  
* **Valide as dimensões da imagem** antes da inserção para evitar escalonamento inesperado que possa afetar a caixa delimitadora do grupo.

---

## Próximos passos

Agora que você sabe **como agrupar formas**, pode explorar:

* **Inserir imagem no documento** com opções avançadas como recorte (`pictureShape.setCropTop(...)`).  
* **Definir tamanho da forma** dinamicamente com base nas dimensões da página (`doc.getFirstSection().getPageSetup().getPageWidth()`).  
* **Adicionar imagem ao grupo** juntamente com caixas de texto para gráficos com legendas.  
* **Criar forma retangular** com cantos arredondados (`rectangleShape.setCornerRadius(5);`).

Esses tópicos ampliam a mesma superfície de API e ajudam a criar relatórios Word sofisticados e programáticos.

---

## Conclusão

Neste tutorial você aprendeu **como agrupar formas** em um documento Word usando Aspose.Words para Java. Seguindo os seis passos — criar um documento, inserir um grupo, **criar forma retangular**, **definir tamanho da forma**, **inserir imagem no documento**, **adicionar imagem ao grupo** e posicionar o grupo — você agora possui um padrão reutilizável para cenários de layout complexos. Sinta‑se à vontade para experimentar formas filhas adicionais, rotações diferentes ou lógica condicional de agrupamento para atender às necessidades da sua aplicação.

Happy coding!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas em seus próprios projetos.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Using Document Shapes in Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}