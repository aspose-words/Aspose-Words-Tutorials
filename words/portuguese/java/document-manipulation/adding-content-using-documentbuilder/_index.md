---
"description": "Domine a criação de documentos com o Aspose.Words para Java. Um guia passo a passo para adicionar texto, tabelas, imagens e muito mais. Crie documentos Word impressionantes sem esforço."
"linktitle": "Adicionando conteúdo usando o DocumentBuilder"
"second_title": "API de processamento de documentos Java Aspose.Words"
"title": "Adicionando conteúdo usando DocumentBuilder no Aspose.Words para Java"
"url": "/pt/java/document-manipulation/adding-content-using-documentbuilder/"
"weight": 26
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Adicionando conteúdo usando DocumentBuilder no Aspose.Words para Java


## Introdução à adição de conteúdo usando DocumentBuilder no Aspose.Words para Java

Neste guia passo a passo, exploraremos como usar o DocumentBuilder do Aspose.Words para Java para adicionar vários tipos de conteúdo a um documento do Word. Abordaremos a inserção de texto, tabelas, linhas horizontais, campos de formulário, HTML, hiperlinks, sumário, imagens embutidas e flutuantes, parágrafos e muito mais. Vamos começar!

## Pré-requisitos

Antes de começar, certifique-se de ter a biblioteca Aspose.Words para Java configurada em seu projeto. Você pode baixá-la em [aqui](https://releases.aspose.com/words/java/).

## Adicionando texto

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Inserir um parágrafo de texto simples
builder.write("This is a simple text paragraph.");

// Salvar o documento
doc.save("path/to/your/document.docx");
```

## Adicionando tabelas

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Iniciar uma tabela
Table table = builder.startTable();

// Inserir células e conteúdo
builder.insertCell();
builder.write("Cell 1");

builder.insertCell();
builder.write("Cell 2");

// Acabar com a mesa
builder.endTable();

// Salvar o documento
doc.save("path/to/your/document.docx");
```

## Adicionando régua horizontal

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Inserir uma régua horizontal
builder.insertHorizontalRule();

// Salvar o documento
doc.save("path/to/your/document.docx");
```

## Adicionando campos de formulário

### Campo de formulário de entrada de texto

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Inserir um campo de formulário de entrada de texto
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// Salvar o documento
doc.save("path/to/your/document.docx");
```

### Campo de formulário de caixa de seleção

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Inserir um campo de formulário de caixa de seleção
builder.insertCheckBox("CheckBox", true, true, 0);

// Salvar o documento
doc.save("path/to/your/document.docx");
```

### Campo de formulário de caixa de combinação

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Definir itens para a caixa de combinação
String[] items = { "Option 1", "Option 2", "Option 3" };

// Inserir um campo de formulário de caixa de combinação
builder.insertComboBox("DropDown", items, 0);

// Salvar o documento
doc.save("path/to/your/document.docx");
```

## Adicionando HTML

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Inserir conteúdo HTML
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// Salvar o documento
doc.save("path/to/your/document.docx");
```

## Adicionando hiperlinks

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Inserir um hiperlink
builder.write("Visit ");
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Aspose Website", "http://www.aspose.com", falso);
builder.getFont().clearFormatting();
builder.write(" for more information.");

// Salvar o documento
doc.save("path/to/your/document.docx");
```

## Adicionando um Índice

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Inserir um índice
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Adicionar conteúdo do documento
// ...

// Atualizar o índice
doc.updateFields();

// Salvar o documento
doc.save("path/to/your/document.docx");
```

## Adicionando Imagens

### Imagem embutida

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Inserir uma imagem em linha
builder.insertImage("path/to/your/image.png");

// Salvar o documento
doc.save("path/to/your/document.docx");
```

### Imagem Flutuante

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Inserir uma imagem flutuante
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// Salvar o documento
doc.save("path/to/your/document.docx");
```

## Adicionando parágrafos

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Definir formatação de parágrafo
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

// Inserir um parágrafo
builder.writeln("This is a formatted paragraph.");

// Salvar o documento
doc.save("path/to/your/document.docx");
```

## Etapa 10: Movendo o cursor

Você pode controlar a posição do cursor dentro do documento usando vários métodos como `moveToParagraph`, `moveToCell`, e muito mais. Aqui está um exemplo:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Mova o cursor para um parágrafo específico
builder.moveToParagraph(2, 0);

// Adicionar conteúdo na nova posição do cursor
builder.writeln("This is the 3rd paragraph.");
```

Estas são algumas operações comuns que você pode realizar usando o DocumentBuilder do Aspose.Words para Java. Explore a documentação da biblioteca para recursos mais avançados e opções de personalização. Boa criação de documentos!


## Conclusão

Neste guia abrangente, exploramos os recursos do DocumentBuilder do Aspose.Words para Java para adicionar vários tipos de conteúdo a documentos do Word. Abordamos texto, tabelas, linhas horizontais, campos de formulário, HTML, hiperlinks, sumário, imagens, parágrafos e movimentação do cursor.

## Perguntas frequentes

### P: O que é Aspose.Words para Java?

R: Aspose.Words para Java é uma biblioteca Java que permite aos desenvolvedores criar, modificar e manipular documentos do Microsoft Word programaticamente. Ela oferece uma ampla gama de recursos para geração, formatação e inserção de conteúdo de documentos.

### P: Como posso adicionar um índice ao meu documento?

R: Para adicionar um índice, use o `DocumentBuilder` Para inserir um campo de índice no seu documento. Certifique-se de atualizar os campos no documento após adicionar conteúdo para preencher o índice. Veja um exemplo:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Inserir um campo de índice
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Adicionar conteúdo do documento
// ...

// Atualizar o índice
doc.updateFields();
```

### P: Como faço para inserir imagens em um documento usando o Aspose.Words para Java?

R: Você pode inserir imagens, tanto em linha quanto flutuantes, usando o `DocumentBuilder`. Aqui estão alguns exemplos de ambos:

#### Imagem embutida:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Inserir uma imagem em linha
builder.insertImage("path/to/your/image.png");
```

#### Imagem flutuante:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Inserir uma imagem flutuante
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### P: Posso formatar texto e parágrafos ao adicionar conteúdo?

R: Sim, você pode formatar texto e parágrafos usando o `DocumentBuilder`Você pode definir propriedades de fonte, alinhamento de parágrafo, recuo e muito mais. Veja um exemplo:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Definir fonte e formatação de parágrafo
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

// Inserir um parágrafo formatado
builder.writeln("This is a formatted paragraph.");
```

### P: Como posso mover o cursor para um local específico dentro do documento?

R: Você pode controlar a posição do cursor usando métodos como `moveToParagraph`, `moveToCell`, e muito mais. Aqui está um exemplo:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Mova o cursor para um parágrafo específico
builder.moveToParagraph(2, 0);

// Adicionar conteúdo na nova posição do cursor
builder.writeln("This is the 3rd paragraph.");
```

Estas são algumas perguntas e respostas comuns para ajudar você a começar a usar o DocumentBuilder do Aspose.Words para Java. Se tiver mais dúvidas ou precisar de mais ajuda, consulte o [documentação da biblioteca](https://reference.aspose.com/words/java/) ou busque ajuda na comunidade e nos recursos de suporte do Aspose.Words.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}