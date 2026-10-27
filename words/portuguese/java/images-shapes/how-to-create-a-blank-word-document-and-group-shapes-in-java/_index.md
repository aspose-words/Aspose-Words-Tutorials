---
category: general
date: 2026-09-24
description: Aprenda a criar um documento Word em branco em Java e agrupar formas
  como retângulos e linhas usando Aspose.Words. Inclui código passo a passo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shapes
- add rectangle shape
- group shapes in word
- set shape size
language: pt
lastmod: 2026-09-24
og_description: Crie um documento Word em branco em Java e aprenda como agrupar formas,
  adicionar uma forma retangular e definir o tamanho da forma com Aspose.Words.
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: Crie um documento Word em branco e agrupe formas em Java – guia passo a
  passo
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Learn how to create a blank Word document in Java and group shapes
    like rectangles and lines using Aspose.Words. Includes step‑by‑step code.
  headline: How to create a blank Word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Como criar um documento Word em branco e agrupar formas em Java
url: /pt/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar um documento Word em branco e agrupar formas em Java

Se você precisa **criar um documento Word em branco** e então organizar vários objetos de desenho, este guia mostra exatamente como fazer. Usando Aspose.Words for Java você pode inserir uma forma de grupo, adicionar uma forma retangular, desenhar uma linha e controlar o tamanho e a posição de cada forma — tudo em um único programa executável.

Você percorrerá cada passo, desde a inicialização do documento até a gravação do `.docx` final. Ao final, você entenderá **como agrupar formas**, **adicionar forma retangular** e **definir o tamanho da forma** para que seus arquivos Word fiquem exatamente como desejado.

## Pré-requisitos

- Java 17 ou posterior (o código compila com qualquer JDK recente)
- Biblioteca Aspose.Words for Java (download do [Aspose website](https://products.aspose.com/words/java))
- Uma IDE ou ferramenta de build (Maven/Gradle) que possa adicionar o JAR Aspose.Words ao classpath
- Conhecimento básico de sintaxe Java

> **Dica profissional:** Use Maven para gerenciamento de dependências; adicione `com.aspose:aspose-words:23.12` (ou a versão mais recente) ao seu `pom.xml`.

## Etapa 1: Criar um documento Word em branco

A primeira tarefa é **criar um documento Word em branco**. Isso fornece uma tela limpa na qual você pode inserir formas posteriormente.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document
        Document document = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Por que isso importa:* Um objeto `Document` representa o arquivo `.docx` completo. Começar com um documento em branco garante que nenhuma formatação oculta interfira nas formas que você adicionará.

## Etapa 2: Inserir uma forma de grupo – o contêiner para vários objetos

Uma **forma de grupo** funciona como um contêiner que permite mover, redimensionar ou girar várias formas juntas. Isso é o núcleo de **como agrupar formas** no Word.

```java
        // Insert a group shape of width 300 points and height 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

*Explicação:* O método `insertGroupShape` cria um objeto `GroupShape` e o posiciona na localização atual do cursor. Todas as formas subsequentes que você `appendChild` a esse grupo serão tratadas como uma única unidade.

## Etapa 3: Adicionar uma forma retangular e definir seu tamanho

Agora nós **adicionamos uma forma retangular** ao grupo e **definimos o tamanho da forma** com precisão.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);   // set shape width
        rectangle.setHeight(100.0);  // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Add the rectangle to the group
        group.appendChild(rectangle);
```

*Por que você precisa definir o tamanho da forma:* Largura e altura controlam como o retângulo aparece na página. Os métodos `setLeft` e `setTop` posicionam o retângulo em relação à origem do grupo, proporcionando controle de layout pixel‑perfect.

## Etapa 4: Adicionar uma forma de linha e configurar suas dimensões

Uma linha é outro objeto de desenho comum. Vamos aplicar a lógica de **adicionar forma retangular** a uma linha, mostrando que os mesmos princípios de dimensionamento se aplicam.

```java
        // Create a line shape
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);   // line length
        line.setHeight(0.0);    // height is zero for a horizontal line
        line.setLeft(20.0);
        line.setTop(130.0);

        // Add the line to the same group
        group.appendChild(line);
```

*Ponto chave:* Mesmo que uma linha não tenha altura, você ainda usa `setWidth` para definir seu comprimento. O posicionamento (`setLeft`, `setTop`) segue o mesmo sistema de coordenadas das outras formas.

## Etapa 5: Salvar o documento com formas agrupadas

Finalmente, persista as alterações salvando o documento. Isso gera um arquivo `.docx` que você pode abrir no Microsoft Word para verificar o resultado.

```java
        // Save the document to disk
        document.save("GroupShapeDemo.docx");
    }
}
```

**Saída esperada:** Ao abrir `GroupShapeDemo.docx` você verá uma página em branco contendo um retângulo e uma linha agrupados. Selecionar qualquer forma seleciona todo o grupo, permitindo mover ambos juntos.

## Perguntas comuns e tratamento de casos extremos

| Pergunta | Resposta |
|----------|----------|
| *Posso adicionar mais de duas formas ao grupo?* | Sim. Chame `group.appendChild(yourShape)` para cada forma adicional. |
| *E se eu precisar de uma unidade diferente (ex.: centímetros) para o tamanho?* | Aspose.Words usa pontos (1 ponto = 1/72 polegada). Converta usando `Points = centimeters * 28.3465`. |
| *O grupo manterá seu layout quando o documento for aberto em outra máquina?* | Absolutamente. Todos os dados de tamanho e posição são armazenados no arquivo `.docx`, tornando o layout portátil. |
| *Como desagrupar formas posteriormente?* | Recupere o objeto `GroupShape`, então itere sobre `group.getChildNodes(NodeType.SHAPE, true)` e mova cada filho para fora do grupo. |
| *E se eu precisar girar todo o grupo?* | Use `group.setRotationAngle(double angleInDegrees)` antes de salvar. |

## Exemplo completo e executável

Abaixo está o programa completo que você pode copiar‑colar em sua IDE. Ele inclui todas as importações necessárias e comentários.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape (container)
        GroupShape group = builder.insertGroupShape(300.0, 200.0);

        // Step 3: Add a rectangle shape and set its size
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);
        rectangle.setHeight(100.0);
        rectangle.setLeft(20.0);
        rectangle.setTop(20.0);
        group.appendChild(rectangle);

        // Step 4: Add a line shape and configure its dimensions
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);
        line.setHeight(0.0);
        line.setLeft(20.0);
        line.setTop(130.0);
        group.appendChild(line);

        // Step 5: Save the document with the grouped shapes
        document.save("GroupShapeDemo.docx");
    }
}
```

Execute o programa, abra `GroupShapeDemo.docx` no Microsoft Word, e você verá as formas agrupadas exatamente como descrito.

## Conclusão

Agora você sabe como **criar um documento Word em branco**, **agrupar formas no Word**, **adicionar forma retangular** e **definir o tamanho da forma** usando Aspose.Words for Java. Ao colocar formas dentro de um `GroupShape`, você obtém controle total sobre posicionamento coletivo, dimensionamento e rotação — perfeito para diagramas, fluxogramas ou gráficos personalizados incorporados em relatórios automatizados.

**Próximos passos:**  
- Explore **como agrupar formas** com objetos mais complexos como imagens ou caixas de texto.  
- Experimente `setRotationAngle` para girar todo o grupo.  
- Combine esta técnica com mala‑direta para gerar documentos personalizados que incluam gráficos de marca.

Sinta-se à vontade para adaptar o código aos seus próprios projetos e compartilhar seus resultados nos comentários!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá-lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Criar forma retangular no Word com Java – Guia Completo](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Criar Documento Word Java – Adicionar Forma Retangular com Efeito de Sombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Criar Forma de Grupo em Documento Word Usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}