---
date: 2026-01-01
description: Aprenda a criar campos de formulário e adicionar texto, tabelas, imagens,
  hyperlinks e muito mais usando o DocumentBuilder do Aspose.Words for Java. Um guia
  passo a passo para desenvolvedores.
linktitle: Adding Content using DocumentBuilder
second_title: Aspose.Words Java Document Processing API
title: Como criar campos de formulário e adicionar conteúdo usando DocumentBuilder
  no Aspose.Words para Java
url: /pt/java/document-manipulation/adding-content-using-documentbuilder/
weight: 26
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Adicionando Conteúdo usando DocumentBuilder no Aspose.Words para Java

## Introdução à Adição de Conteúdo usando DocumentBuilder no Aspose.Words para Java

Neste guia passo a passo, você **criará campos de formulário** e adicionará uma variedade de conteúdo — texto, tabelas, linhas horizontais, HTML, hyperlinks, imagens e muito mais — em um documento Word com Aspose.Words para Java. Seja construindo um relatório, um modelo de contrato ou um formulário interativo, a classe `DocumentBuilder` oferece controle detalhado sobre cada elemento. Vamos mergulhar!

## Respostas Rápidas
- **Como criar campos de formulário?** Use `insertTextInput`, `insertCheckBox` ou `insertComboBox` em um `DocumentBuilder`.
- **Qual método adiciona texto simples?** Chame `builder.write("Your text")` ou `builder.writeln("Your text")`.
- **Posso inserir uma linha horizontal?** Sim — `builder.insertHorizontalRule()` adiciona um separador de linha.
- **Como incorporar HTML?** Use `builder.insertHtml("<p>HTML content</p>")`.
- **Como adicionar uma imagem inline?** `builder.insertImage("path/to/image.png")` coloca a imagem dentro do fluxo de texto.

## O que é DocumentBuilder e por que usá-lo para criar campos de formulário?

`DocumentBuilder` é a API fluente do Aspose.Words para construir e editar documentos Word programaticamente. Ela abstrai a estrutura OpenXML de baixo nível, permitindo que você se concentre no *que* deseja adicionar — como **campos de formulário** — em vez de *como* o XML se apresenta. Isso a torna ideal para gerar formulários dinâmicos, contratos ou qualquer documento que exija interação do usuário.

## Pré-requisitos

Antes de começar, certifique‑se de que a biblioteca Aspose.Words para Java esteja instalada em seu projeto. Você pode baixá‑la [aqui](https://releases.aspose.com/words/java/).

## Adicionando Texto (como adicionar texto)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a simple text paragraph
builder.write("This is a simple text paragraph.");

// Save the document
doc.save("path/to/your/document.docx");
```

## Adicionando Tabelas

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Start a table
Table table = builder.startTable();

// Insert cells and content
builder.insertCell();
builder.write("Cell 1");

builder.insertCell();
builder.write("Cell 2");

// End the table
builder.endTable();

// Save the document
doc.save("path/to/your/document.docx");
```

## Adicionando uma Linha Horizontal (adicionar linha horizontal)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a horizontal rule
builder.insertHorizontalRule();

// Save the document
doc.save("path/to/your/document.docx");
```

## Adicionando Campos de Formulário (criar campos de formulário)

### Campo de Formulário de Entrada de Texto

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a text input form field
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### Campo de Formulário de Caixa de Seleção

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a check box form field
builder.insertCheckBox("CheckBox", true, true, 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### Campo de Formulário de Caixa de Combinação

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Define items for the combo box
String[] items = { "Option 1", "Option 2", "Option 3" };

// Insert a combo box form field
builder.insertComboBox("DropDown", items, 0);

// Save the document
doc.save("path/to/your/document.docx");
```

## Adicionando HTML (inserir palavra html)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert HTML content
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// Save the document
doc.save("path/to/your/document.docx");
```

## Adicionando Hyperlinks (como adicionar hyperlink)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a hyperlink
builder.write("Visit ");
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Aspose Website", "http://www.aspose.com", false);
builder.getFont().clearFormatting();
builder.write(" for more information.");

// Save the document
doc.save("path/to/your/document.docx");
```

## Adicionando um Sumário

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table of contents
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Add document content
// ...

// Update the table of contents
doc.updateFields();

// Save the document
doc.save("path/to/your/document.docx");
```

## Adicionando Imagens

### Imagem Inline (inserir imagem inline)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");

// Save the document
doc.save("path/to/your/document.docx");
```

### Imagem Flutuante

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// Save the document
doc.save("path/to/your/document.docx");
```

## Adicionando Parágrafos

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Set paragraph formatting
Font font = builder.getFont();
font.setSize(16.0);
font.setBold(true);
font.setColor(Color.BLUE);
font.setName("Arial");
font.setUnderline(Underline.DASH);

ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setFirstLineIndent(8.0);
paragraphFormat.setAlignment(ParagraphAlignment.JUSTIFY);
paragraphFormat.setKeepTogether(true);

// Insert a paragraph
builder.writeln("This is a formatted paragraph.");

// Save the document
doc.save("path/to/your/document.docx");
```

## Movendo o Cursor (Etapa 10)

Você pode controlar a posição do cursor dentro do documento usando métodos como `moveToParagraph`, `moveToCell`, etc.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

Estas são algumas operações comuns que você pode executar usando o `DocumentBuilder` do Aspose.Words para Java. Explore a documentação da biblioteca para recursos avançados e opções de personalização. Boa criação de documentos!

## Conclusão

Neste guia abrangente, mostramos como **criar campos de formulário** e adicionar vários tipos de conteúdo — texto, tabelas, linhas horizontais, HTML, hyperlinks, um sumário, imagens, parágrafos formatados e navegação de cursor — usando o `DocumentBuilder` do Aspose.Words para Java. Agora você tem uma base sólida para gerar documentos Word dinâmicos e interativos programaticamente.

## Perguntas Frequentes

### Q: O que é Aspose.Words para Java?

R: Aspose.Words para Java é uma biblioteca Java que permite aos desenvolvedores criar, modificar e manipular documentos Microsoft Word programaticamente. Ela oferece uma ampla gama de recursos para geração de documentos, formatação e inserção de conteúdo.

### Q: Como posso adicionar um sumário ao meu documento?

R: Para adicionar um sumário, use o `DocumentBuilder` para inserir um campo TOC e então chame `doc.updateFields()` após adicionar seu conteúdo.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table of contents field
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Add document content
// ...

// Update the table of contents
doc.updateFields();
```

### Q: Como insiro imagens em um documento usando Aspose.Words para Java?

R: Você pode inserir imagens, tanto inline quanto flutuantes, usando o `DocumentBuilder`.

#### Imagem Inline:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");
```

#### Imagem Flutuante:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### Q: Posso formatar texto e parágrafos ao adicionar conteúdo?

R: Sim, você pode formatar texto e parágrafos usando o `DocumentBuilder`. Defina propriedades de fonte, alinhamento de parágrafo, recuo e mais antes de escrever o conteúdo.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Set font and paragraph formatting
Font font = builder.getFont();
font.setSize(16.0);
font.setBold(true);
font.setColor(Color.BLUE);
font.setName("Arial");
font.setUnderline(Underline.DASH);

ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setFirstLineIndent(8.0);
paragraphFormat.setAlignment(ParagraphAlignment.JUSTIFY);
paragraphFormat.setKeepTogether(true);

// Insert a formatted paragraph
builder.writeln("This is a formatted paragraph.");
```

### Q: Como posso mover o cursor para um local específico dentro do documento?

R: Use métodos como `moveToParagraph`, `moveToCell`, etc., para posicionar o cursor antes de inserir novo conteúdo.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

Estas respostas cobrem os cenários mais comuns ao trabalhar com o `DocumentBuilder` do Aspose.Words para Java. Para detalhes mais aprofundados, consulte a [documentação da biblioteca](https://reference.aspose.com/words/java/) ou participe da comunidade Aspose.Words para suporte.

---

**Última Atualização:** 2026-01-01  
**Testado com:** Aspose.Words for Java 24.12  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}