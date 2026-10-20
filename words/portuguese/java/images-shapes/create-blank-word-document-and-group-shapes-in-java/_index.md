---
category: general
date: 2026-08-23
description: Crie um documento Word em branco com Aspose.Words para Java, aprenda
  a agrupar formas, colorir forma retangular e salvar o documento como docx em minutos.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- save document as docx
- how to group shapes
- color rectangle shape
language: pt
lastmod: 2026-08-23
og_description: Crie um documento Word em branco com Aspose.Words para Java, depois
  veja como agrupar formas, colorir forma retangular e salvar o documento como DOCX
  de forma eficiente.
og_image_alt: Screenshot of a blank Word document containing grouped colored rectangle
  shapes
og_title: Criar documento Word em branco e agrupar formas em Java – guia passo a passo
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Create blank Word document with Aspose.Words for Java, learn how to
    group shapes, color rectangle shape, and save document as docx in minutes.
  headline: Create blank Word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Criar documento Word em branco e agrupar formas em Java
url: /pt/java/images-shapes/create-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar documento Word em branco e agrupar formas em Java

Se você precisa **create blank Word document** programaticamente, Aspose.Words for Java torna isso simples. Este tutorial mostra exatamente como **create blank Word document**, inserir um **group shapes in Word**, aplicar **color rectangle shape**, e finalmente **save document as docx**. Ao final, você terá um trecho de código reutilizável que pode inserir em qualquer projeto Java.

Você aprenderá:

* A dependência necessária do Maven/Gradle para Aspose.Words.
* Como instanciar um documento em branco e um `DocumentBuilder`.
* Os passos exatos para **how to group shapes** dentro de um `GroupShape`.
* Como definir cores de preenchimento em formas retangulares.
* A melhor prática para **save document as docx** e onde encontrar o arquivo de saída.

Não se assume experiência prévia com Aspose.Words, mas você deve estar confortável com desenvolvimento Java básico e ter um JDK 8 ou mais recente instalado.

---

## Pré-requisitos

| Requisito | Versão / Detalhe |
|-----------|-------------------|
| Java Development Kit | 8 or higher |
| Build tool | Maven 3+ or Gradle 6+ |
| Aspose.Words for Java | 23.12 or later (the latest version at the time of writing) |
| IDE (optional) | IntelliJ IDEA, Eclipse, VS Code, or any Java‑compatible editor |

---

## Etapa 1: Adicionar Aspose.Words ao seu projeto

### Maven

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

### Gradle

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **Dica profissional:** Se você estiver usando um proxy corporativo, configure o Maven/Gradle para obter o pacote do repositório Aspose conforme descrito na documentação oficial.

---

## Etapa 2: **Create blank Word document** com um builder

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new blank document
        Document doc = new Document();               // <-- create blank Word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

O construtor `Document` cria um contêiner `.docx` vazio na memória. O `DocumentBuilder` fornece uma API fluente para adicionar conteúdo, incluindo formas.

---

## Etapa 3: Inserir um contêiner **group shapes in Word**

```java
        // Step 3.1: Insert a GroupShape that will hold individual shapes
        // Width = 300 points, Height = 200 points
        GroupShape groupShape = builder.insertGroupShape(300, 200);
```

Um `GroupShape` funciona como um mini‑canvas. Todas as formas adicionadas a ele se movem juntas, o que é exatamente **how to group shapes** para consistência de layout.

---

## Etapa 4: Adicionar a primeira **color rectangle shape** (vermelho)

```java
        // Step 4.1: Create the first rectangle and set its fill color to red
        Shape redRectangle = new Shape(doc, ShapeType.RECTANGLE);
        redRectangle.setWidth(120);
        redRectangle.setHeight(80);
        redRectangle.getFill().setForeColor(java.awt.Color.RED);
        // Append the rectangle to the group
        groupShape.appendChild(redRectangle);
```

A constante `ShapeType.RECTANGLE` cria um retângulo simples. Ao chamar `getFill().setForeColor(...)` você controla a **color rectangle shape**. Você pode substituir `java.awt.Color.RED` por qualquer constante `java.awt.Color` ou valor RGB personalizado.

---

## Etapa 5: Adicionar a segunda **color rectangle shape** (verde) e posicioná‑la

```java
        // Step 5.1: Create a second rectangle, color it green, and offset it inside the group
        Shape greenRectangle = new Shape(doc, ShapeType.RECTANGLE);
        greenRectangle.setWidth(120);
        greenRectangle.setHeight(80);
        greenRectangle.setLeft(130); // Horizontal offset inside the group
        greenRectangle.getFill().setForeColor(java.awt.Color.GREEN);
        groupShape.appendChild(greenRectangle);
```

Definir `setLeft` (ou `setTop`) move a forma em relação ao canto superior esquerdo do contêiner **group shapes in Word**. Isso demonstra **how to group shapes** com posicionamento preciso.

---

## Etapa 6: **Save document as docx** e verifique o resultado

```java
        // Step 6.1: Persist the document to the file system
        String outputPath = "output/GroupShapeDemo.docx";
        doc.save(outputPath);          // <-- save document as docx
        System.out.println("Document saved to: " + outputPath);
    }
}
```

O método `save` grava automaticamente um arquivo `.docx` porque a extensão do arquivo é `.docx`. Se você precisar de um formato diferente (por exemplo, PDF), passe o enum `SaveFormat` apropriado.

> **Dica:** Certifique‑se de que o diretório de destino (`output/` neste exemplo) exista ou crie‑o programaticamente com `new File("output").mkdirs();`.

---

## Código-fonte completo para copiar‑colar rapidamente

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document
        Document doc = new Document();               // create blank Word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a GroupShape (the container for grouped shapes)
        GroupShape groupShape = builder.insertGroupShape(300, 200);

        // 3️⃣ First rectangle – red
        Shape redRectangle = new Shape(doc, ShapeType.RECTANGLE);
        redRectangle.setWidth(120);
        redRectangle.setHeight(80);
        redRectangle.getFill().setForeColor(java.awt.Color.RED);
        groupShape.appendChild(redRectangle);

        // 4️⃣ Second rectangle – green, positioned next to the red one
        Shape greenRectangle = new Shape(doc, ShapeType.RECTANGLE);
        greenRectangle.setWidth(120);
        greenRectangle.setHeight(80);
        greenRectangle.setLeft(130); // offset inside the group
        greenRectangle.getFill().setForeColor(java.awt.Color.GREEN);
        groupShape.appendChild(greenRectangle);

        // 5️⃣ Save the file as DOCX
        String outPath = "output/GroupShapeDemo.docx";
        doc.save(outPath);          // save document as docx
        System.out.println("Document saved to: " + outPath);
    }
}
```

**Saída esperada:** Ao abrir `GroupShapeDemo.docx` no Microsoft Word, você verá uma única página contendo dois retângulos coloridos (vermelho à esquerda, verde à direita) que se movem juntos quando você seleciona o grupo.

---

## Perguntas comuns e tratamento de casos extremos

| Pergunta | Resposta |
|----------|----------|
| *Posso adicionar mais de duas formas ao mesmo grupo?* | Sim. Chame `groupShape.appendChild(yourShape)` para cada forma adicional. O grupo redimensionará automaticamente para caber nas extensões mais distantes, ou você pode ajustar manualmente sua largura/altura. |
| *E se eu precisar de um tipo de forma diferente (por exemplo, elipse)?* | Substitua `ShapeType.RECTANGLE` por `ShapeType.ELLIPSE`. A mesma lógica de preenchimento de cor se aplica. |
| *Preciso descartar o objeto `Document`?* | Aspose.Words gerencia recursos nativos internamente. Quando a JVM termina, os recursos são liberados. Para aplicações de longa duração, chame `doc.dispose();` se você usar a versão **Aspose.Words for Java (Native)**. |
| *Como altero a ordem Z para que um retângulo apareça acima?* | Use `groupShape.insertAfter(shape, referenceShape);` ou `groupShape.insertBefore(shape, referenceShape);` para reordenar os filhos dentro do grupo. |
| *Posso agrupar formas em diferentes seções?* | Não. Um `GroupShape` deve residir dentro de um único parágrafo ou contêiner de forma. Para agrupar entre seções, crie grupos separados em cada seção. |

---

## Conclusão

Agora você sabe como **create blank Word document** com Aspose.Words for Java, **group shapes in Word**, aplicar estilização de **color rectangle shape**, e **save document as docx**. Esse padrão escala para layouts mais complexos — basta adicionar formas adicionais, ajustar deslocamentos e, opcionalmente, definir texto, imagens ou hyperlinks dentro do grupo.

**Próximas etapas** que você pode explorar:

* Use **group shapes in Word** para criar fluxogramas ou maquetes de UI.  
* Experimente **save document as docx** combinado com conversão para PDF (`doc.save("out.pdf")`).  
* Aplique gradientes ou padrões à **color rectangle shape** para um design visual mais rico.  
* Combine formas agrupadas com tabelas ou gráficos para documentos de relatório avançados.

Sinta‑se à vontade para modificar as dimensões, cores ou tipos de forma para combinar com a identidade visual do seu projeto. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Criar Documento Word Java – Adicionar Forma Retangular com Efeito de Sombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Como salvar documento como pdf com Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Usando Formas de Documento no Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}