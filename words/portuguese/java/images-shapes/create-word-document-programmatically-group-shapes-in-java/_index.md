---
category: general
date: 2026-09-21
description: Criar documento Word programaticamente usando Java. Aprenda como agrupar
  formas no Word, inserir uma forma retangular, definir o tamanho da forma e adicionar
  formas a um documento Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- how to group shapes in word
- how to insert rectangle shape
- add shapes to word document
- set shape size word
language: pt
lastmod: 2026-09-21
og_description: 'Crie documento Word programaticamente com Java: este guia mostra
  como agrupar formas no Word, inserir formas retangulares, definir o tamanho das
  formas e adicionar formas a um documento Word.'
og_image_alt: Screenshot of a Java program creating a Word document with grouped shapes
og_title: Criar documento Word programaticamente, agrupar formas em Java
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically using Java. Learn how to group
    shapes in Word, insert a rectangle shape, set shape size, and add shapes to a
    Word document.
  headline: Create word document programmatically, group shapes in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Word automation
- Shapes
title: Criar documento Word programaticamente, agrupar formas em Java
url: /pt/java/images-shapes/create-word-document-programmatically-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar documento Word programaticamente, agrupar formas em Java

Se você precisa **criar documento Word programaticamente**, este guia o conduz por uma solução completa. Você verá como **agrupar formas no Word**, inserir um retângulo, definir seu tamanho e adicionar outras formas — tudo usando Java e a biblioteca Aspose.Words for Java.

O tutorial cobre cada passo, desde a configuração do projeto até a gravação do arquivo .docx final. Ao final, você será capaz de gerar um documento Word que contém um retângulo e uma imagem agrupados dentro de um único grupo, facilitando mover ou redimensionar ambos juntos. Não é necessário ter experiência prévia com a API Aspose.Words, mas você deve possuir um ambiente básico de desenvolvimento Java.

## Pré-requisitos

* Java Development Kit (JDK) 8 ou superior  
* Maven ou Gradle para gerenciamento de dependências  
* Aspose.Words for Java 23.9 (ou a versão mais recente) – a biblioteca é gratuita para avaliação  
* Um arquivo de imagem (por exemplo, `sample.jpg`) colocado em um diretório conhecido  

Ter esses itens prontos garante que o código seja executado sem configuração adicional.

## Etapa 1: Configurar o projeto e importar o Aspose.Words

Crie um projeto Maven (ou adicione a dependência ao seu `pom.xml` existente):

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Se preferir Gradle, adicione o seguinte ao `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:23.9'
```

Depois que a dependência for resolvida, importe as classes necessárias no seu arquivo fonte Java:

```java
import com.aspose.words.*;
import java.io.File;
```

## Etapa 2: Criar o documento Word programaticamente

A primeira operação em qualquer cenário de automação é instanciar um objeto `Document` e um `DocumentBuilder`. O builder simplifica a inserção de texto, imagens e formas.

```java
public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Neste ponto o documento existe apenas na memória. Agora você pode começar a adicionar formas.

## Etapa 3: Inserir uma forma retângulo – como inserir forma retângulo

Um retângulo é uma `Shape` básica com `ShapeType.RECTANGLE`. Você controla suas dimensões com `setWidth`, `setHeight` e a posiciona com `setTop` e `setLeft`.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);
        rectangle.setTop(10.0);
        rectangle.setLeft(10.0);

        // Optional: give the rectangle a visible fill and line color
        rectangle.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);
        rectangle.getStrokeColor().setColor(java.awt.Color.DARK_GRAY);
```

**Por que isso importa:** Definir o tamanho e a posição explicitamente (`set shape size word`) garante que o retângulo apareça exatamente onde você espera, independentemente do layout padrão do documento.

## Etapa 4: Inserir uma imagem – adicionar formas ao documento Word

O `DocumentBuilder` pode inserir uma imagem diretamente a partir de um caminho de arquivo. Após a inserção, você pode reposicionar a imagem como qualquer outra forma.

```java
        // Insert an image; replace the path with your own image location
        String imagePath = "YOUR_DIRECTORY/sample.jpg";
        if (!new File(imagePath).exists()) {
            throw new IllegalArgumentException("Image file not found: " + imagePath);
        }
        Shape picture = builder.insertImage(imagePath);
        picture.setTop(70.0);
        picture.setLeft(10.0);
```

Tanto o retângulo quanto a imagem agora são formas independentes dentro do documento.

## Etapa 5: Agrupar as formas – como agrupar formas no Word

Agrupar formas é útil quando você deseja mover ou redimensionar elas como uma única unidade. Aspose.Words fornece um contêiner `GroupShape` para esse propósito.

```java
        // Create a GroupShape that will contain the rectangle and the picture
        GroupShape group = builder.insertGroupShape();

        // Append the rectangle and picture to the group
        group.appendChild(rectangle);
        group.appendChild(picture);
```

Quando o grupo é salvo, o Word trata os dois filhos como um único objeto lógico. Você pode, posteriormente, selecionar o grupo e arrastá‑lo, e tanto o retângulo quanto a imagem seguirão.

## Etapa 6: Salvar o documento

Finalmente, grave o documento no disco. O caminho deve ser gravável pelo processo Java.

```java
        // Save the document with the grouped shapes
        String outputPath = "YOUR_DIRECTORY/GroupShapeExample.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Executar o método `main` produz um arquivo chamado **GroupShapeExample.docx**. Abra‑o no Microsoft Word para ver um retângulo e uma imagem bloqueados juntos dentro de um grupo. Selecionar o grupo permite mover ambos os objetos simultaneamente, confirmando que o agrupamento foi bem‑sucedido.

## Saída esperada

* Um arquivo Word (`GroupShapeExample.docx`) localizado no diretório que você especificou.  
* Dentro do arquivo, um retângulo (preenchimento cinza‑claro) aparece no canto superior‑esquerdo, e a imagem fica logo abaixo dele.  
* Ambos os objetos fazem parte de um único grupo, de modo que arrastar um move o outro.

## Variações comuns e casos de borda

| Situação | Recomendação |
|-----------|----------------|
| **Formatos de imagem diferentes** | Aspose.Words suporta PNG, BMP, GIF e TIFF. Use a extensão de arquivo apropriada em `insertImage`. |
| **Dimensões negativas** | A API lança `ArgumentException`. Sempre valide largura e altura antes de chamar `setWidth` / `setHeight`. |
| **Documentos grandes** | Agrupar muitas formas pode aumentar o tamanho do arquivo. Considere mesclar formas em uma única imagem quando o desempenho for importante. |
| **Compatibilidade de versão do Word** | GroupShape funciona com Word 2007 (`.docx`) e posteriores. Para arquivos `.doc` mais antigos, o grupo será achatado. |
| **Posicionamento dinâmico** | Use cálculos baseados no tamanho da página (`doc.getFirstSection().getPageSetup().getPageWidth()`) se precisar de posicionamento adaptativo. |

**Dica profissional:** Depois de criar o grupo, você pode alterar

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Criar documento Word Java – Adicionar forma retângulo com efeito de sombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Criar forma retângulo no Word com Java – Guia completo](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Criar forma de grupo em documento Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}