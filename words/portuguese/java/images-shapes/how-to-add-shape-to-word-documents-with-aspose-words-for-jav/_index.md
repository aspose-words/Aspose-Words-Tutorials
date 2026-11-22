---
category: general
date: 2026-11-22
description: Aprenda como adicionar forma ao Word usando Aspose.Words para Java –
  insira um retângulo e oculte‑o programaticamente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shape to word
- how to insert shape
- how to hide shape
- hide shape in word
language: pt
lastmod: 2026-11-22
og_description: Adicione forma ao Word usando Aspose.Words para Java. Este tutorial
  mostra como inserir um retângulo, ocultar a forma e salvar o documento.
og_image_alt: Screenshot of Java code that adds and hides a shape in a Word document
og_title: Adicionar forma ao Word com Aspose.Words – Guia Java
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  headline: How to add shape to Word documents with Aspose.Words for Java
  type: TechArticle
- description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  name: How to add shape to Word documents with Aspose.Words for Java
  steps:
  - name: Expected output
    text: '* The file `output.docx` opens without any visible shapes. * If you inspect
      the document with Aspose.Words (e.g., `doc.getChildNodes(NodeType.SHAPE, true).size()`),
      the shape count will be **1**, confirming that the shape exists but is hidden.'
  - name: 1. Creating a shape in a fresh document
    text: 'If you start from scratch, replace the load line with:'
  - name: 2. Positioning the shape precisely
    text: 'By default, `insertShape` places the shape at the current cursor location.
      To position it absolutely:'
  - name: 3. Controlling visibility per output format
    text: 'If you need the shape visible in the Word UI but hidden when exporting
      to PDF, use `Shape.setWrapType(WrapType.NONE)` together with `Hidden`:'
  - name: 4. Adding text inside the shape
    text: 'A rectangle can contain a text frame:'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Shape handling
title: Como adicionar forma a documentos Word com Aspose.Words para Java
url: /pt/java/images-shapes/how-to-add-shape-to-word-documents-with-aspose-words-for-jav/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como adicionar forma a documentos Word com Aspose.Words para Java

Se você precisar **adicionar forma a documentos Word** programaticamente, o Aspose.Words para Java torna isso simples. Neste guia você aprenderá **como inserir forma**, controlar sua visibilidade e **como ocultar forma** para que o arquivo final fique exatamente como esperado.

Você percorrerá um exemplo completo e executável que carrega um `.docx` existente, insere um retângulo, o oculta e salva o resultado. Nenhum script externo ou etapas manuais são necessários, e o tutorial cobre variações comuns, como criar um novo documento do zero ou ocultar uma forma apenas ao imprimir.

## Pré‑requisitos

Antes de começar, certifique‑se de que você tem:

* Java 17 (ou superior) instalado – versões anteriores funcionam, mas a LTS mais recente oferece melhor desempenho.  
* Maven 3.8+ para gerenciamento de dependências.  
* Uma licença válida do Aspose.Words para Java (a avaliação gratuita serve para aprendizado).  
* Uma IDE ou editor de texto de sua preferência (por exemplo, IntelliJ IDEA, VS Code).

## Etapa 1: Adicionar Aspose.Words ao seu projeto Maven

Adicione a dependência a seguir ao seu `pom.xml`. Isso traz a versão estável mais recente (a partir de novembro 2026).

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

> **Dica profissional:** Use uma cláusula `<scope>provided</scope>` se você planeja distribuir o JAR com sua própria lógica de licenciamento.

## Adicionar forma ao Word – inicializando o documento

O primeiro passo funcional é obter um objeto `Document`. Você pode carregar um arquivo existente ou criar um novo.

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document (or create a new one)
        Document doc = new Document("input.docx");   // <-- replace with your path
        // If you prefer a blank document, use:
        // Document doc = new Document();
```

*Por que isso importa*: A classe `Document` é o ponto de entrada para todas as manipulações de Word. Carregar um arquivo existente preserva estilos, cabeçalhos e rodapés, enquanto um documento novo oferece uma página em branco.

## Como inserir forma em um documento Word

Em seguida, crie um `DocumentBuilder` para modificar o conteúdo do documento. O builder fornece métodos para inserir texto, tabelas e **formas**.

```java
        // Create a builder attached to the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a rectangle shape with a width of 100 points and height of 50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
```

A chamada `insertShape` devolve um objeto `Shape` que pode ser configurado adicionalmente (cor, borda, texto etc.). As dimensões são expressas em pontos (1 pt = 1/72 in).

*Por que você pode usar um retângulo*: Retângulos são o contêiner mais comum para anotações, marcas d'água ou marcadores de posição. Você pode substituir `ShapeType.RECTANGLE` por `ShapeType.ELLIPSE`, `ShapeType.LINE` etc., para atender a diferentes necessidades visuais.

## Como ocultar forma no Word

Às vezes, você precisa que uma forma exista para cálculos de layout, mas não apareça na renderização final. O Aspose.Words fornece o método `setHidden(true)` para isso.

```java
        // Hide the shape so it does not appear when the document is opened
        rectangle.setHidden(true);
```

A bandeira hidden funciona como a opção de formatação **Hidden** no Microsoft Word: a forma é omitida do layout visual, mas ainda participa do modelo de objetos do documento. Isso é útil para:

* Armazenar metadados ou marcadores que sua aplicação lê posteriormente.  
* Criar marcadores de posição que são removidos logo antes da publicação.  
* Controlar a visibilidade para diferentes formatos de saída (por exemplo, ocultar no HTML mas manter no PDF).

> **Observação:** Formas ocultas ainda são exportadas para PDF por padrão. Se precisar que sejam omitidas do PDF também, defina `rectangle.getWrapType( ) = WrapType.NONE` e ajuste a propriedade `Hidden` conforme necessário.

## Etapa 4: Salvar o documento modificado

Por fim, persista as alterações em um novo arquivo.

```java
        // Save the document with the hidden rectangle
        doc.save("output.docx");   // <-- replace with your desired output path
    }
}
```

Ao abrir `output.docx` no Microsoft Word, o retângulo não será visível, mas permanecerá parte da árvore do documento. Você pode verificar sua presença programaticamente recarregando o arquivo e checando `Shape.isHidden()`.

### Saída esperada

* O arquivo `output.docx` abre sem nenhuma forma visível.  
* Se você inspecionar o documento com Aspose.Words (por exemplo, `doc.getChildNodes(NodeType.SHAPE, true).size()`), a contagem de formas será **1**, confirmando que a forma existe, porém está oculta.

## Variações avançadas e casos de borda

### 1. Criando uma forma em um documento novo

Se você começar do zero, substitua a linha de carregamento por:

```java
Document doc = new Document();          // creates an empty Word file
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Report Title");        // add a title before the shape
```

### 2. Posicionando a forma com precisão

Por padrão, `insertShape` coloca a forma na posição atual do cursor. Para posicioná‑la absolutamente:

```java
rectangle.setLeft(72);   // 1 inch from the left margin
rectangle.setTop(144);   // 2 inches from the top of the page
rectangle.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangle.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
```

### 3. Controlando a visibilidade por formato de saída

Se precisar que a forma seja visível na UI do Word, mas oculta ao exportar para PDF, use `Shape.setWrapType(WrapType.NONE)` junto com `Hidden`:

```java
rectangle.setHidden(false);                 // visible in Word
rectangle.getParagraph().getParagraphFormat()
        .setPageBreakBefore(true);          // ensure it stays on its own line
// When converting to PDF, hide it programmatically:
if (exportingToPdf) {
    rectangle.setHidden(true);
}
```

### 4. Adicionando texto dentro da forma

Um retângulo pode conter uma caixa de texto:

```java
Shape textBox = builder.insertShape(ShapeType.TEXT_BOX, 200, 50);
textBox.getTextBox().setInternalMarginLeft(5);
textBox.getTextBox().setInternalMarginTop(5);
builder.moveTo(textBox.getFirstParagraph());
builder.write("Confidential");
```

Você pode então ocultar a caixa de texto com a mesma chamada `setHidden(true)`.

## Armadilhas comuns e como evitá‑las

| Sintoma | Causa | Solução |
|---------|-------|---------|
| A forma aparece mesmo após `setHidden(true)` | O documento foi salvo antes da bandeira hidden ser definida. | Certifique‑se de chamar `setHidden(true)` **antes** de `doc.save()`. |
| O tamanho da forma parece distorcido | Confusão entre pontos e pixels em telas de alta DPI. | Use pontos (72 pt = 1 in) para dimensionamento consistente em todas as plataformas. |
| Forma oculta ainda imprime | Algumas impressoras ignoram a bandeira hidden. | Defina `Shape.setWrapType(WrapType.NONE)` e também limpe `Shape.getParagraph().getParagraphFormat().setPageBreakBefore(false)`. |

## Conclusão

Agora você sabe como **adicionar forma a documentos Word** usando Aspose.Words para Java, **como inserir forma** e **como ocultar forma** para que ela permaneça invisível ao usuário final, mas ainda faça parte da estrutura do documento. O exemplo completo acima carrega um arquivo, insere um retângulo, o oculta e salva o resultado, cobrindo tanto casos típicos quanto vários casos de borda.

A partir daqui, você pode explorar tópicos relacionados, como **como inserir forma** com cores de preenchimento personalizadas, **como ocultar forma no Word** para impressão condicional, ou automatizar o processamento em massa de documentos com Aspose.Words. Experimente diferentes valores de `ShapeType`, opções de posicionamento e bandeiras de visibilidade para adequar ao seu fluxo de trabalho específico.

Feliz codificação e aproveite a flexibilidade que a manipulação programática de Word traz para suas aplicações Java!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Create a Word document programmatically, add and hide a shape in Java using Aspose.Words](/words/english/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/)
- [How to hide shape in a Word document using Java](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Create a blank .docx Word document and add a hidden rectangle shape with Aspose.Words](/words/english/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}