---
category: general
date: 2026-10-13
description: Aprenda como criar formas agrupadas no Word com Java. Este guia mostra
  como inserir forma de grupo, adicionar linha ao grupo e agrupar várias formas em
  todo o documento.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create grouped shapes
- add line to group
- group multiple shapes word
- insert group shape
language: pt
lastmod: 2026-10-13
og_description: Crie formas agrupadas no Word com Java. Siga este tutorial completo
  para inserir forma de grupo, adicionar linha ao grupo e agrupar várias formas em
  documentos do Word.
og_image_alt: Screenshot of a Word document showing created grouped shapes
og_title: Criar formas agrupadas no Word com Java – guia passo a passo
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to create grouped shapes in Word with Java. This guide shows
    you how to insert group shape, add line to group, and group multiple shapes word‑wide.
  headline: How to create grouped shapes in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Como criar formas agrupadas em um documento Word usando Java
url: /pt/java/images-shapes/how-to-create-grouped-shapes-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar formas agrupadas em um documento Word usando Java

Se você precisa **criar formas agrupadas** em um arquivo Microsoft Word a partir do Java, este tutorial o guiará por todo o processo. Você verá como **inserir forma de grupo**, colocar um retângulo e uma linha dentro do mesmo contêiner e, finalmente, salvar o documento com os gráficos agrupados.

Agrupar formas facilita mover, redimensionar ou estilizar vários objetos de desenho como uma única unidade — perfeito para diagramas, fluxogramas ou decorações personalizadas de página. Ao final deste guia você será capaz de **adicionar linha ao grupo**, **agrupaar múltiplas formas word** documentos e reutilizar a mesma técnica para qualquer número de formas.

## Pré-requisitos

- Java 17 ou superior instalado na sua máquina de desenvolvimento.  
- Uma licença do Aspose.Words for Java (ou uma avaliação gratuita).  
- Um projeto Maven ou Gradle onde você possa adicionar a dependência do Aspose.Words:

```xml
<!-- Maven example -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

Nenhuma biblioteca adicional é necessária.

## Etapa 1: Inserir o contêiner de forma de grupo

O primeiro passo é **inserir forma de grupo** no documento. Este contêiner armazenará todas as formas subsequentes.

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // The rest of the code will add shapes to this group
```

`builder.insertGroupShape()` cria um objeto `Shape` vazio do tipo `GROUPSHAPE`. Pense nele como uma tela transparente que pode conter outros objetos de desenho.

## Etapa 2: Adicionar um retângulo ao grupo

Um retângulo costuma servir como plano de fundo visual para um conjunto de formas.

```java
        // Create a rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // width in points
        rectangleShape.setHeight(50);   // height in points
        rectangleShape.setLeft(0);      // X‑coordinate inside the group
        rectangleShape.setTop(0);       // Y‑coordinate inside the group

        // Append the rectangle to the group container
        groupShape.appendChild(rectangleShape);
```

Definir `Left` e `Top` como `0` posiciona o retângulo no canto superior‑esquerdo do grupo. Você pode alterar esses valores para deslocar a forma dentro do grupo.

## Etapa 3: **Adicionar linha ao grupo** – criar uma forma de linha

Agora **adicionamos linha ao grupo**. A linha aparecerá abaixo do retângulo.

```java
        // Create a line shape
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);   // length of the line
        lineShape.setTop(60);      // vertical position (60 points down)

        // Append the line to the same group
        groupShape.appendChild(lineShape);
```

A propriedade `Top` move a linha 60 pontos abaixo do retângulo, criando um layout simples empilhado. Você também pode definir `Left` caso precise de deslocamento horizontal.

## Etapa 4: Salvar o documento com as formas agrupadas

```java
        // Save the document to a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

Ao abrir `GroupShapeDemo.docx` no Microsoft Word, você verá um único grupo que contém tanto o retângulo quanto a linha. Selecionar o grupo permite mover ambas as formas juntas, demonstrando que você **agrupou múltiplas formas word** com sucesso.

## Exemplo completo e executável

Abaixo está o programa completo com todas as importações e tratamento de erros. Copie-o para sua IDE, substitua `YOUR_DIRECTORY` por um caminho de pasta existente e execute.

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // Step 3: Add a rectangle to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);
        rectangleShape.setHeight(50);
        rectangleShape.setLeft(0);
        rectangleShape.setTop(0);
        groupShape.appendChild(rectangleShape);

        // Step 4: Add a line to the group
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);
        lineShape.setTop(60);
        groupShape.appendChild(lineShape);

        // Step 5: Save the document
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

### Saída esperada

- Um arquivo chamado `GroupShapeDemo.docx` aparece na pasta de destino.  
- Abrindo o arquivo no Word, vê‑se um único objeto agrupado contendo um retângulo na parte superior e uma linha abaixo dele.  
- Arrastar o grupo move ambas as formas simultaneamente, confirmando que você **criou formas agrupadas** com sucesso.

## Dicas e armadilhas comuns

- **Dica profissional:** Se precisar girar ou estilizar formas individuais dentro do grupo, chame os respectivos setters (`setRotation`, `getFill().setForeColor`, etc.) antes de adicioná‑las ao grupo. O grupo preservará essas propriedades visuais.  
- **Cuidado com:** Esquecer de definir a propriedade `Top` para a linha pode fazer com que ela se sobreponha ao retângulo, deixando o grupo desordenado.  
- **Caso extremo:** Quando você adiciona mais de duas formas, lembre‑se de que as coordenadas de cada filho são relativas à origem do grupo (0,0). Planeje o layout adequadamente.  
- **Observação de desempenho:** Agrupar um grande número de formas (centenas) pode aumentar ligeiramente o tamanho do arquivo, mas simplifica a edição posterior no Word.

## Como **group multiple shapes word** documentos programaticamente

O padrão mostrado acima — criar um contêiner de grupo, configurar cada forma filha e anexar — funciona para qualquer número de formas: círculos, imagens, caixas de texto, etc. Basta repetir os passos “criar forma → definir propriedades → anexar” antes de chamar `doc.save()`.

Se precisar **adicionar linha ao grupo** depois que o grupo já contém outras formas, você pode recuperar o grupo existente com:

```java
Shape existingGroup = (Shape) doc.getChildNodes(NodeType.SHAPE, true)
                                 .stream()
                                 .filter(s -> ((Shape) s).getShapeType() == ShapeType.GROUPSHAPE)
                                 .findFirst()
                                 .orElseThrow(() -> new IllegalStateException("No group found"));
existingGroup.appendChild(lineShape);
```

Isso demonstra que você pode modificar um grupo em qualquer ponto do ciclo de vida do documento.

## Conclusão

Agora você sabe como **criar formas agrupadas** em um documento Word usando Java e Aspose.Words. Ao **inserir forma de grupo**, **adicionar linha ao grupo** e **agrupaar múltiplas formas word**, você pode construir desenhos complexos que se comportam como um único objeto — ideal para diagramas, modelos e geração automática de relatórios.

Em seguida, explore estes tópicos relacionados:

- **Aplicando estilos a formas agrupadas** – aprenda a definir cores de preenchimento, bordas e efeitos para todos os filhos de uma vez.  
- **Exportando formas agrupadas para PDF** – veja como o mesmo grupo persiste ao converter o documento.  
- **Animando formas com VBA** – combine grupos gerados em Java com macros do Word para documentos interativos.

Sinta‑se à vontade para experimentar diferentes tipos, tamanhos e posições de formas. O agrupamento oferece a flexibilidade de tratar muitos objetos como um só, simplificando tanto o código quanto a interação do usuário. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}