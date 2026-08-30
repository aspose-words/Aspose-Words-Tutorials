---
category: general
date: 2026-07-29
description: Crie documento Word em Java usando Aspose.Words. Aprenda a inserir forma
  retangular, agrupar formas no Word e salvar o documento como docx rapidamente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert rectangle shape
- group shapes in word
- save document as docx
- add shapes to word
language: pt
lastmod: 2026-07-29
og_description: Crie um documento Word em Java com Aspose.Words. Insira uma forma
  retangular, agrupe formas no Word e salve o documento como docx em minutos.
og_image_alt: Screenshot showing how to create word document with grouped shapes using
  Java
og_title: Criar documento Word com formas – Tutorial Java Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Create word document in Java using Aspose.Words. Learn to insert rectangle
    shape, group shapes in Word, and save document as docx quickly.
  headline: Create Word Document with Shapes in Java – Complete Aspose.Words Guide
  type: TechArticle
- description: Create word document in Java using Aspose.Words. Learn to insert rectangle
    shape, group shapes in Word, and save document as docx quickly.
  name: Create Word Document with Shapes in Java – Complete Aspose.Words Guide
  steps:
  - name: '## Create Word Document with Shapes Using Aspose.Words'
    text: The first thing you need is an empty Word file to work with. Aspose.Words
      makes this a one‑liner.
  - name: '## Insert Rectangle Shape and Other Shapes'
    text: Now we’ll add a blue rectangle and a green ellipse. The rectangle demonstrates
      the **insert rectangle shape** keyword, while the ellipse shows that you can
      mix shape types freely.
  - name: '## Group Shapes in Word for Easy Manipulation'
    text: Having two separate objects is fine, but often you want to move them together.
      That’s where **group shapes in word** shines.
  - name: '## Save Document as DOCX and Verify Output'
    text: Finally, we persist the file. This step fulfills the **save document as
      docx** requirement.
  - name: '## Full Working Example and Common Pitfalls'
    text: Below is the complete, ready‑to‑run Java class. Copy‑paste it into your
      project, adjust the output folder, and hit *Run*.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: Criar documento Word com formas em Java – Guia completo do Aspose.Words
url: /pt/java/images-shapes/create-word-document-with-shapes-in-java-complete-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar Word Document com Formas em Java – Guia Completo do Aspose.Words

Já se perguntou como **create word document** programaticamente e encher de gráficos personalizados? Você não está sozinho. Seja para gerar um relatório com seções destacadas ou projetar um folheto rapidamente, dominar o manuseio de formas no Word pode economizar horas de trabalho manual.

Neste tutorial, percorreremos os passos exatos para **create word document** usando Aspose.Words for Java, **insert rectangle shape**, **group shapes in Word**, e finalmente **save document as docx**. Ao final, você terá um exemplo totalmente executável que pode inserir em qualquer projeto.

## O Que Você Vai Aprender

- Um novo arquivo Word gerado inteiramente a partir de código Java.  
- Duas formas distintas (um retângulo e uma elipse) adicionadas à página.  
- Essas formas agrupadas usando a API **group shapes in word**, fazendo com que se comportem como um único objeto.  
- O arquivo persistido no disco como um `.docx` padrão que abre no Microsoft Word sem problemas.

Sem ferramentas externas, sem truques complicados de XML — apenas Java tipado e limpo e Aspose.Words.

---

## Pré‑requisitos

Antes de mergulharmos, certifique‑se de que você tem:

1. **Java Development Kit (JDK) 8 ou mais recente** – o código tem como alvo Java 8+.  
2. **Aspose.Words for Java** JAR (você pode obter a versão mais recente do repositório Maven Central).  
3. Uma IDE modesta (IntelliJ IDEA, Eclipse ou até mesmo um editor de texto simples).

Se você tem isso, ótimo — vamos começar.

## Implementação Passo a Passo

A seguir, dividimos o processo em etapas pequenas. Cada etapa inclui um trecho de código, uma breve explicação e uma dica que você pode não encontrar na documentação oficial.

### ## Criar Word Document com Formas Usando Aspose.Words

A primeira coisa que você precisa é um arquivo Word vazio para trabalhar. Aspose.Words torna isso em uma única linha.

```java
// Step 1: Initialise a blank document and a DocumentBuilder
Document doc = new Document();                 // Represents the Word file
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Por que isso importa:**  
`Document` é o contêiner para tudo — texto, tabelas, imagens e formas. `DocumentBuilder` é o ajudante amigável que permite adicionar conteúdo sem lutar com objetos de baixo nível. Pense nele como uma caneta que escreve diretamente na página.

> **Dica profissional:** Se você planeja começar com um modelo (por exemplo, um cabeçalho de empresa), substitua `new Document()` por `new Document("template.docx")`.

### ## Inserir Forma Retangular e Outras Formas

Agora adicionaremos um retângulo azul e uma elipse verde. O retângulo demonstra a palavra‑chave **insert rectangle shape**, enquanto a elipse mostra que você pode misturar tipos de forma livremente.

```java
// Step 2: Insert a rectangle shape (100x50 points) and set its appearance
Shape rect = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
rect.setLeft(50);                               // X‑coordinate in points
rect.setTop(50);                                // Y‑coordinate in points
rect.getFill().setColor(java.awt.Color.BLUE);  // Fill color

// Step 3: Insert an ellipse shape (80x80 points) and configure it
Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 80, 80);
ellipse.setLeft(180);
ellipse.setTop(30);
ellipse.getFill().setColor(java.awt.Color.GREEN);
```

**O que está acontecendo nos bastidores?**  
Cada chamada a `insertShape` cria um objeto `Shape` e o adiciona automaticamente ao parágrafo atual. Os métodos `setLeft`/`setTop` posicionam a forma em relação às margens da página, medidos em pontos (1 pt = 1/72 in). Ajustando esses números, você pode colocar as formas onde quiser.

> **Pergunta comum:** *Posso adicionar uma imagem em vez de uma cor sólida?*  
> Absolutamente — basta substituir a cor de preenchimento por uma imagem usando `shape.getFill().setImage("path/to/image.png")`.

### ## Agrupar Formas no Word para Manipulação Fácil

Ter dois objetos separados está ok, mas frequentemente você quer movê‑los juntos. É aí que **group shapes in word** se destaca.

```java
// Step 4: Create a GroupShape container and add the two shapes
GroupShape group = builder.insertGroupShape(); // Starts an empty group
group.appendChild(rect);
group.appendChild(ellipse);

// Step 5: Reposition the whole group as a single entity
group.setLeft(100);
group.setTop(150);
```

**Por que agrupar?**  
Quando as formas são agrupadas, qualquer transformação — mover, girar, redimensionar — aplica‑se a toda a coleção. Isso espelha o comportamento que você obtém ao selecionar manualmente múltiplas formas na interface do Word e pressionar *Group*. Também simplifica o código posterior, pois você precisa ajustar apenas um objeto em vez de vários.

> **Caso extremo:** Se você precisar desagrupar mais tarde, chame `group.getParentNode().removeChild(group)` e reinsira os filhos individualmente.

### ## Salvar Documento como DOCX e Verificar a Saída

Finalmente, persistimos o arquivo. Esta etapa cumpre o requisito **save document as docx**.

```java
// Step 6: Write the document to disk as a .docx file
String outputPath = "output/GroupShapeExample.docx";
doc.save(outputPath, SaveFormat.DOCX);
System.out.println("Document saved successfully to " + outputPath);
```

**O que esperar:**  
Abra o `GroupShapeExample.docx` gerado no Microsoft Word. Você verá um retângulo azul e uma elipse verde, agrupados de forma ordenada. Arraste o grupo — ambas as formas se moverão juntas, exatamente como esperado na interface.

> **Dica:** Use `SaveFormat.PDF` se precisar de uma versão PDF; o mesmo código funciona sem alterações.

### ## Exemplo Completo e Armadilhas Comuns

Abaixo está a classe Java completa, pronta para execução. Copie‑e‑cole no seu projeto, ajuste a pasta de saída e pressione *Run*.

```java
import com.aspose.words.*;

public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert the first rectangle shape and set its position and fill color
        Shape rect = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rect.setLeft(50);
        rect.setTop(50);
        rect.getFill().setColor(java.awt.Color.BLUE);

        // Step 3: Insert a second ellipse shape and configure its position and fill color
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 80, 80);
        ellipse.setLeft(180);
        ellipse.setTop(30);
        ellipse.getFill().setColor(java.awt.Color.GREEN);

        // Step 4: Group the two shapes together using the new GroupShape API
        GroupShape group = builder.insertGroupShape();
        group.appendChild(rect);
        group.appendChild(ellipse);

        // Step 5: Optionally reposition the entire group as a single object
        group.setLeft(100);
        group.setTop(150);

        // Step 6: Save the document containing the grouped shapes
        String outPath = "output/GroupShapeExample.docx";
        doc.save(outPath, SaveFormat.DOCX);
        System.out.println("Document saved successfully to " + outPath);
    }
}
```

#### Armadilhas Comuns & Como Evitá‑las

| Issue | Why It Happens | Fix |
|-------|----------------|-----|
| **`NullPointerException` on `builder`** | Esquecer de instanciar `DocumentBuilder` após criar `Document`. | Certifique‑se de que `new DocumentBuilder(doc)` seja executado antes de inserir qualquer forma. |
| **Shapes appear off‑page** | Usar valores em pixels em vez de pontos, ou não considerar as margens. | Lembre‑se de que Aspose.Words espera pontos; 72 pt = 1 in. Ajuste `setLeft`/`setTop` adequadamente. |
| **Group disappears after save** | Adicionar formas ao grupo *depois* que o grupo foi salvo. | Sempre agrupe antes de chamar `doc.save()`. |
| **File not found on save** | O diretório de saída não existe. | Crie o diretório programaticamente (`new File("output").mkdirs();`) ou use um caminho existente. |

---

## Conclusão

Acabamos de **create word document** do zero, **add shapes to word**, **insert rectangle shape**, **group shapes in word**, e finalmente **save document as docx** — tudo com algumas linhas de Java. O poder do Aspose.Words reside em seu modelo de objetos claro; você pode tratar um arquivo Word como uma tela, pintar nele com formas e depois exportá‑lo onde precisar.

Sentindo-se aventureiro? Experimente substituir o retângulo por uma estrela, adicionar texto dentro das formas usando `Shape.getTextBox()`, ou experimentar rotação (`shape.setRotationAngle(45)`). A API é rica, e as possibilidades são praticamente infinitas.

Tem perguntas sobre cenários mais avançados — como vincular formas a marcadores ou exportar para PDF com fontes incorporadas? Deixe um comentário abaixo, e exploraremos mais a fundo juntos. Feliz codificação!

## O Que Você Deve Aprender a Seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Criar Word Document Java – Adicionar Forma Retangular com Efeito de Sombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Criar Forma de Grupo em Documento Word Usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Criar forma retangular no Word com Aspose.Words – Guia passo a passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}