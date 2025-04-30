---
"description": "Aprenda a usar Tags de Documento Estruturadas (SDT) no Aspose.Words para Java com este guia completo. Crie, modifique e vincule SDTs a dados XML personalizados."
"linktitle": "Usando tags de documentos estruturados (SDT)"
"second_title": "API de processamento de documentos Java Aspose.Words"
"title": "Usando tags de documentos estruturados (SDT) no Aspose.Words para Java"
"url": "/pt/java/document-manipulation/using-structured-document-tags/"
"weight": 19
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Usando tags de documentos estruturados (SDT) no Aspose.Words para Java


## Introdução ao uso de tags de documentos estruturados (SDT) no Aspose.Words para Java

As Tags de Documento Estruturadas (SDT) são um recurso poderoso do Aspose.Words para Java que permite criar e manipular conteúdo estruturado em seus documentos. Neste guia completo, mostraremos os vários aspectos do uso de SDTs no Aspose.Words para Java. Seja você um desenvolvedor iniciante ou experiente, encontrará insights valiosos e exemplos práticos neste artigo.

## Começando

Antes de entrarmos em detalhes, vamos configurar nosso ambiente e criar um SDT básico. Nesta seção, abordaremos os seguintes tópicos:

- Criando um novo documento
- Adicionando uma tag de documento estruturado
- Salvando o documento

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Crie uma tag de documento estruturado do tipo CHECKBOX
StructuredDocumentTag sdtCheckBox = new StructuredDocumentTag(doc, SdtType.CHECKBOX, MarkupLevel.INLINE);
builder.insertNode(sdtCheckBox);

// Salvar o documento
doc.save("WorkingWithSDT.docx");
```

## Verificando o estado atual de uma caixa de seleção SDT

Depois de adicionar uma caixa de seleção SDT ao seu documento, você pode querer verificar seu estado atual programaticamente. Isso pode ser útil quando você precisa validar a entrada do usuário ou executar ações específicas com base no estado da caixa de seleção.

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtCheckBox = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtCheckBox.getSdtType() == SdtType.CHECKBOX) {
    // A caixa de seleção está marcada
    sdtCheckBox.setChecked(true);
}

doc.save("UpdatedDocument.docx");
```

## Modificando controles de conteúdo

Nesta seção, exploraremos como modificar os controles de conteúdo no seu documento. Abordaremos três tipos de controles de conteúdo: Texto Simples, Lista Suspensa e Imagem.

### Modificando o controle de conteúdo de texto simples

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtPlainText = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtPlainText.getSdtType() == SdtType.PLAIN_TEXT) {
    // Limpar o conteúdo existente
    sdtPlainText.removeAllChildren();

    // Adicionar novo texto
    Paragraph para = (Paragraph) sdtPlainText.appendChild(new Paragraph(doc));
    Run run = new Run(doc, "New text goes here");
    para.appendChild(run);
}

doc.save("ModifiedDocument.docx");
```

### Modificando o controle de conteúdo da lista suspensa

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtDropDown = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtDropDown.getSdtType() == SdtType.DROP_DOWN_LIST) {
    // Selecione o segundo item da lista
    SdtListItem secondItem = sdtDropDown.getListItems().get(2);
    sdtDropDown.getListItems().setSelectedValue(secondItem);
}

doc.save("ModifiedDocument.docx");
```

### Modificando o controle de conteúdo da imagem

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtPicture = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);
Shape shape = (Shape) sdtPicture.getChild(NodeType.SHAPE, 0, true);

if (shape.hasImage()) {
    // Substituir a imagem por uma nova
    shape.getImageData().setImage("Watermark.png");
}

doc.save("ModifiedDocument.docx");
```

## Criando um controle de conteúdo ComboBox

Um Controle de Conteúdo ComboBox permite que os usuários selecionem a partir de uma lista predefinida de opções. Vamos criar um em nosso documento.

```java
Document doc = new Document();
StructuredDocumentTag sdtComboBox = new StructuredDocumentTag(doc, SdtType.COMBO_BOX, MarkupLevel.BLOCK);
sdtComboBox.getListItems().add(new SdtListItem("Choose an item", "-1"));
sdtComboBox.getListItems().add(new SdtListItem("Item 1", "1"));
sdtComboBox.getListItems().add(new SdtListItem("Item 2", "2"));
doc.getFirstSection().getBody().appendChild(sdtComboBox);

doc.save("ComboBoxDocument.docx");
```

## Trabalhando com controle de conteúdo de texto enriquecido

Os Controles de Conteúdo de Rich Text são perfeitos para adicionar texto formatado aos seus documentos. Vamos criar um e definir seu conteúdo.

```java
Document doc = new Document();
StructuredDocumentTag sdtRichText = new StructuredDocumentTag(doc, SdtType.RICH_TEXT, MarkupLevel.BLOCK);
Paragraph para = new Paragraph(doc);
Run run = new Run(doc);
run.setText("Hello World");
run.getFont().setColor(Color.GREEN);
para.getRuns().add(run);
sdtRichText.getChildNodes().add(para);
doc.getFirstSection().getBody().appendChild(sdtRichText);

doc.save("RichTextDocument.docx");
```

## Definindo estilos de controle de conteúdo

Você pode aplicar estilos aos controles de conteúdo para aprimorar a aparência visual do seu documento. Vamos ver como definir o estilo de um controle de conteúdo.

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdt = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

// Aplicar um estilo personalizado
Style style = doc.getStyles().getByStyleIdentifier(StyleIdentifier.QUOTE);
sdt.setStyle(style);

doc.save("StyledDocument.docx");
```

## Vinculando um SDT a dados XML personalizados

Em alguns cenários, pode ser necessário vincular um SDT a dados XML personalizados para geração de conteúdo dinâmico. Vamos explorar como fazer isso.

```java
Document doc = new Document();
CustomXmlPart xmlPart = doc.getCustomXmlParts().add(UUID.randomUUID().toString(), "<root><text>Hello, World!</text></root>");
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.BLOCK);
doc.getFirstSection().getBody().appendChild(sdt);
sdt.getXmlMapping().setMapping(xmlPart, "/root[1]/text[1]", "");

doc.save("CustomXMLBinding.docx");
```

## Criando uma tabela com seções repetidas mapeadas para dados XML personalizados

Tabelas com seções repetidas podem ser extremamente úteis para apresentar dados estruturados. Vamos criar uma tabela assim e mapeá-la para dados XML personalizados.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
CustomXmlPart xmlPart = doc.getCustomXmlParts().add("Books", "<books>...</books>");
Table table = builder.startTable();
builder.insertCell();
builder.write("Title");
builder.insertCell();
builder.write("Author");
builder.endRow();
builder.endTable();

StructuredDocumentTag repeatingSectionSdt = new StructuredDocumentTag(doc, SdtType.REPEATING_SECTION, MarkupLevel.ROW);
repeatingSectionSdt.getXmlMapping().setMapping(xmlPart, "/books[1]/book", "");
table.appendChild(repeatingSectionSdt);

StructuredDocumentTag repeatingSectionItemSdt = new StructuredDocumentTag(doc, SdtType.REPEATING_SECTION_ITEM, MarkupLevel.ROW);
repeatingSectionSdt.appendChild(repeatingSectionItemSdt);

Row row = new Row(doc);
repeatingSectionItemSdt.appendChild(row);

StructuredDocumentTag titleSdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.CELL);
titleSdt.getXmlMapping().setMapping(xmlPart, "/books[1]/book[1]/title[1]", "");
row.appendChild(titleSdt);

StructuredDocumentTag authorSdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.CELL);
authorSdt.getXmlMapping().setMapping(xmlPart, "/books[1]/book[1]/author[1]", "");
row.appendChild(authorSdt);

doc.save("RepeatingTableDocument.docx");
```

## Trabalhando com tags de documentos estruturados de várias seções

As tags de documento estruturadas podem abranger várias seções em um documento. Nesta seção, exploraremos como trabalhar com SDTs de várias seções.

```java
Document doc = new Document("MultiSectionDocument.docx");
NodeCollection tags = doc.getChildNodes(NodeType.STRUCTURED_DOCUMENT_TAG_RANGE_START, true);

for (StructuredDocumentTagRangeStart tag : tags) {
    System.out.println(tag.getTitle());
}

doc.save("ModifiedMultiSectionDocument.docx");
```

## Conclusão

As tags de documentos estruturadas no Aspose.Words para Java oferecem uma maneira versátil de gerenciar e formatar o conteúdo dos seus documentos. Seja para criar modelos, formulários ou documentos dinâmicos, as SDTs oferecem a flexibilidade e o controle necessários. Seguindo os exemplos e diretrizes fornecidos neste artigo, você pode aproveitar o poder das SDTs para aprimorar suas tarefas de processamento de documentos.

## Perguntas frequentes

### Qual é a finalidade das Tags de Documentos Estruturados (SDTs)?

As tags de documentos estruturados (SDTs) servem para organizar e formatar o conteúdo dentro de documentos, facilitando a criação de modelos, formulários e documentos estruturados.

### Como posso verificar o estado atual de um Checkbox SDT?

Você pode verificar o estado atual de um Checkbox SDT usando o `setChecked` método, conforme demonstrado no artigo.

### Posso aplicar estilos aos Controles de Conteúdo?

Sim, você pode aplicar estilos aos Controles de Conteúdo para personalizar sua aparência no documento.

### É possível vincular um SDT a dados XML personalizados?

Sim, você pode vincular um SDT a dados XML personalizados, permitindo geração de conteúdo dinâmico e mapeamento de dados.

### O que são seções repetidas em SDTs?

Seções repetidas em SDTs permitem que você crie tabelas com dados dinâmicos, onde as linhas podem ser repetidas com base nos dados XML mapeados.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}