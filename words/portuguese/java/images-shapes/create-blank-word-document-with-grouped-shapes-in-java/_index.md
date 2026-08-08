---
category: general
date: 2026-08-07
description: Crie um documento Word em branco com formas agrupadas em Java usando
  Aspose.Words. Aprenda como agrupar formas, definir o tamanho da forma e adicionar
  formas ao Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shape
- group shapes word
- set shape size
- add shapes to word
language: pt
lastmod: 2026-08-07
og_description: Crie um documento Word em branco com formas agrupadas em Java. Siga
  este guia para definir o tamanho das formas, adicionar formas ao Word e dominar
  como agrupar formas.
og_image_alt: Create blank Word document with grouped shapes using Aspose.Words for
  Java
og_title: Criar documento Word em branco com formas agrupadas – tutorial Java
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create blank Word document with grouped shapes in Java using Aspose.Words.
    Learn how to group shape, set shape size, and add shapes to Word.
  headline: Create blank Word document with grouped shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word Automation
- Shapes
title: Criar documento Word em branco com formas agrupadas em Java
url: /pt/java/images-shapes/create-blank-word-document-with-grouped-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar documento Word em branco com formas agrupadas em Java

Se você precisa **criar documento Word em branco** que contenha várias formas organizadas como uma única unidade, este tutorial mostra exatamente como fazer. Você verá um exemplo completo e executável que demonstra **como agrupar formas**, ajustar suas dimensões e **adicionar formas ao Word** usando Aspose.Words for Java.

O guia percorre cada etapa — desde a configuração do projeto até a gravação do arquivo .docx final — para que você possa copiar o código diretamente para sua própria aplicação. Nenhuma referência externa é necessária, e a solução funciona com Aspose.Words 23.9 ou posterior.

## Pré-requisitos

* Java 17 (ou qualquer JDK suportado)
* Maven ou Gradle para gerenciamento de dependências
* Uma licença Aspose.Words for Java (ou uma chave de avaliação temporária)
* Um arquivo de imagem de exemplo (por exemplo, `sample.jpg`) colocado em um diretório conhecido

Se algum desses itens estiver ausente, instale‑o primeiro; o restante do tutorial assume que o ambiente está pronto.

## Etapa 1: Adicionar Aspose.Words ao seu projeto

Adicione a dependência Aspose.Words ao seu `pom.xml` (Maven) ou `build.gradle` (Gradle). Esta biblioteca fornece as classes `Document`, `DocumentBuilder`, `GroupShape` e `Shape` usadas posteriormente.

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:23.9'
```

**Por que isso importa:** Sem a biblioteca, nenhuma das APIs de processamento de Word está disponível, e você não pode **criar documento Word em branco** programaticamente.

## Etapa 2: Criar um documento Word em branco

A primeira ação concreta é instanciar um objeto `Document`, que representa um **documento Word em branco** na memória.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new, empty document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*`Document()`* cria um **documento Word em branco** com configurações padrão (página A4, margens padrão). O `DocumentBuilder` associado permite inserir conteúdo na posição atual do cursor.

## Etapa 3: Inserir uma forma de grupo (como agrupar formas)

Uma *group shape* funciona como um contêiner para outras formas. Nesta etapa, você aprende **como agrupar formas** para que se movam juntas.

```java
        // Insert a group shape with a width of 300 points and height of 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

O método `insertGroupShape` coloca o contêiner na posição do cursor do builder. Agrupar é essencial quando você deseja tratar vários desenhos como uma única entidade — esse é o núcleo da funcionalidade de **group shapes word**.

## Etapa 4: Criar um retângulo e definir seu tamanho

Agora adicione um retângulo ao grupo. Isso demonstra **definir tamanho da forma**, que é necessário para um layout preciso.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // set shape width
        rectangle.setHeight(50.0);   // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Append rectangle to the group
        group.appendChild(rectangle);
```

*Por que definir dimensões?* Chamar explicitamente `setWidth` e `setHeight` garante que o retângulo apareça exatamente como desejado, independentemente dos estilos de forma padrão do documento.

## Etapa 5: Inserir uma imagem e adicioná‑la ao grupo

Adicionar uma imagem mostra outro caso de uso comum para **add shapes to word**. A imagem torna‑se parte do mesmo grupo, movendo‑se junto com o retângulo.

```java
        // Insert an image at the current cursor position
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        picture.setLeft(150.0);   // position inside the group
        picture.setTop(30.0);     // position inside the group

        // Append picture to the group
        group.appendChild(picture);
```

Se o arquivo de imagem estiver ausente, Aspose.Words lança uma exceção. Uma dica prática é verificar o caminho antecipadamente:

```java
        File imgFile = new File("YOUR_DIRECTORY/sample.jpg");
        if (!imgFile.exists()) {
            throw new IllegalArgumentException("Image file not found: " + imgFile.getAbsolutePath());
        }
```

## Etapa 6: Salvar o documento contendo as formas agrupadas

Finalmente, persista o **documento Word em branco** (agora preenchido com uma forma agrupada) no disco.

```java
        // Save the document as a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

Ao abrir `GroupShapeDemo.docx` no Microsoft Word, você verá um único objeto agrupado que contém um retângulo e uma imagem. Selecionar qualquer parte do grupo move todo o contêiner, confirmando que as formas foram corretamente **agrupadas**.

### Saída esperada

* Um arquivo chamado `GroupShapeDemo.docx` no diretório especificado.
* Ao abrir o arquivo, mostra um contêiner de 300 × 200 pontos com:
  * Um retângulo de 100 × 50 pontos posicionado em (20, 20).
  * Uma imagem posicionada em (150, 30) dentro do mesmo contêiner.

## Casos de borda e variações

| Situação | Como lidar |
|----------|------------|
| **Tamanho de página diferente** | Chame `doc.getFirstSection().getPageSetup().setPaperSize(PaperSize.A5);` antes de inserir o grupo. |
| **Múltiplos grupos** | Repita as etapas 3‑5 com uma nova instância `GroupShape`; cada grupo pode ser posicionado independentemente. |
| **Rotacionar formas** | Use `shape.setRotationAngle(45.0);` para girar um retângulo ou imagem antes de adicioná‑lo ao grupo. |
| **Formas não‑imagem** | Crie objetos `Shape` do tipo `ShapeType.ELLIPSE`, `ShapeType.LINE`, etc., e adicione‑os como o retângulo. |
| **Imagens grandes** | Redimensione a imagem com `picture.setWidth(80.0); picture.setHeight(60.0);` para manter o grupo dentro de seus limites originais. |

## Dicas práticas da experiência

* **Dica profissional:** Defina `RelativeHorizontalPosition` e `RelativeVerticalPosition` do grupo para `RelativeHorizontalPosition.PAGE` e `RelativeVerticalPosition.PAGE` se desejar que o grupo permaneça ancorado à página em vez do cursor.
* **Cuidado com:** Adicionar uma forma que exceda as dimensões do grupo; a forma será recortada no Word. Ajuste o tamanho do grupo com `group.setWidth()` e `group.setHeight()` conforme necessário.
* **Nota de desempenho:** Se você gerar muitos documentos em um loop, reutilize uma única instância `DocumentBuilder` e chame `doc.clone()` para reduzir a sobrecarga de criação de objetos.

## Conclusão

Agora você sabe como **criar documento Word em branco** que contém uma coleção agrupada de formas usando Aspose.Words for Java. O tutorial cobriu todo o fluxo de trabalho: configurar a biblioteca, criar o documento, inserir um grupo, **definir tamanho da forma**, **adicionar formas ao word**, e salvar o resultado.

A partir daqui, você pode explorar recursos mais avançados, como agrupar gráficos, aplicar estilos a formas individuais ou exportar o documento para PDF. Cada um desses tópicos se baseia nos mesmos princípios demonstrados neste guia.

---

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}