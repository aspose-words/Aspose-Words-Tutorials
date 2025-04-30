---
"description": "Узнайте, как использовать структурированные теги документов (SDT) в Aspose.Words для Java с помощью этого всеобъемлющего руководства. Создавайте, изменяйте и привязывайте SDT к пользовательским данным XML."
"linktitle": "Использование структурированных тегов документов (SDT)"
"second_title": "API обработки документов Java Aspose.Words"
"title": "Использование структурированных тегов документов (SDT) в Aspose.Words для Java"
"url": "/ru/java/document-manipulation/using-structured-document-tags/"
"weight": 19
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Использование структурированных тегов документов (SDT) в Aspose.Words для Java


## Введение в использование структурированных тегов документов (SDT) в Aspose.Words для Java

Структурированные теги документов (SDT) — это мощная функция в Aspose.Words для Java, которая позволяет вам создавать и управлять структурированным контентом в ваших документах. В этом подробном руководстве мы проведем вас через различные аспекты использования SDT в Aspose.Words для Java. Независимо от того, новичок вы или опытный разработчик, вы найдете в этой статье ценные идеи и практические примеры.

## Начиная

Прежде чем погрузиться в детали, давайте настроим нашу среду и создадим базовый SDT. В этом разделе мы рассмотрим следующие темы:

- Создание нового документа
- Добавление структурированного тега документа
- Сохранение документа

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Создайте структурированный тег документа типа CHECKBOX
StructuredDocumentTag sdtCheckBox = new StructuredDocumentTag(doc, SdtType.CHECKBOX, MarkupLevel.INLINE);
builder.insertNode(sdtCheckBox);

// Сохранить документ
doc.save("WorkingWithSDT.docx");
```

## Проверка текущего состояния флажка SDT

После добавления SDT флажка в документ вы можете захотеть проверить его текущее состояние программным способом. Это может быть полезно, когда вам нужно проверить ввод пользователя или выполнить определенные действия на основе состояния флажка.

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtCheckBox = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtCheckBox.getSdtType() == SdtType.CHECKBOX) {
    // Флажок отмечен
    sdtCheckBox.setChecked(true);
}

doc.save("UpdatedDocument.docx");
```

## Изменение элементов управления содержимым

В этом разделе мы рассмотрим, как изменять элементы управления содержимым в вашем документе. Мы рассмотрим три типа элементов управления содержимым: простой текст, раскрывающийся список и изображение.

### Изменение элемента управления содержимым простого текста

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtPlainText = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtPlainText.getSdtType() == SdtType.PLAIN_TEXT) {
    // Очистить существующее содержимое
    sdtPlainText.removeAllChildren();

    // Добавить новый текст
    Paragraph para = (Paragraph) sdtPlainText.appendChild(new Paragraph(doc));
    Run run = new Run(doc, "New text goes here");
    para.appendChild(run);
}

doc.save("ModifiedDocument.docx");
```

### Изменение элемента управления содержимым раскрывающегося списка

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtDropDown = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtDropDown.getSdtType() == SdtType.DROP_DOWN_LIST) {
    // Выберите второй пункт из списка
    SdtListItem secondItem = sdtDropDown.getListItems().get(2);
    sdtDropDown.getListItems().setSelectedValue(secondItem);
}

doc.save("ModifiedDocument.docx");
```

### Изменение управления содержимым изображения

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtPicture = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);
Shape shape = (Shape) sdtPicture.getChild(NodeType.SHAPE, 0, true);

if (shape.hasImage()) {
    // Заменить изображение на новое
    shape.getImageData().setImage("Watermark.png");
}

doc.save("ModifiedDocument.docx");
```

## Создание элемента управления содержимым ComboBox

Элемент управления содержимым ComboBox позволяет пользователям выбирать из предопределенного списка вариантов. Давайте создадим один в нашем документе.

```java
Document doc = new Document();
StructuredDocumentTag sdtComboBox = new StructuredDocumentTag(doc, SdtType.COMBO_BOX, MarkupLevel.BLOCK);
sdtComboBox.getListItems().add(new SdtListItem("Choose an item", "-1"));
sdtComboBox.getListItems().add(new SdtListItem("Item 1", "1"));
sdtComboBox.getListItems().add(new SdtListItem("Item 2", "2"));
doc.getFirstSection().getBody().appendChild(sdtComboBox);

doc.save("ComboBoxDocument.docx");
```

## Работа с элементом управления содержимым Rich Text

Rich Text Content Controls идеально подходят для добавления форматированного текста в ваши документы. Давайте создадим один и настроим его содержимое.

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

## Настройка стилей управления содержимым

Вы можете применять стили к элементам управления содержимым, чтобы улучшить внешний вид вашего документа. Давайте посмотрим, как задать стиль элемента управления содержимым.

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdt = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

// Применить пользовательский стиль
Style style = doc.getStyles().getByStyleIdentifier(StyleIdentifier.QUOTE);
sdt.setStyle(style);

doc.save("StyledDocument.docx");
```

## Привязка SDT к пользовательским XML-данным

В некоторых сценариях вам может потребоваться привязать SDT к пользовательским данным XML для динамической генерации контента. Давайте рассмотрим, как этого добиться.

```java
Document doc = new Document();
CustomXmlPart xmlPart = doc.getCustomXmlParts().add(UUID.randomUUID().toString(), "<root><text>Hello, World!</text></root>");
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.BLOCK);
doc.getFirstSection().getBody().appendChild(sdt);
sdt.getXmlMapping().setMapping(xmlPart, "/root[1]/text[1]", "");

doc.save("CustomXMLBinding.docx");
```

## Создание таблицы с повторяющимися разделами, сопоставленными с пользовательскими XML-данными

Таблицы с повторяющимися разделами могут быть чрезвычайно полезны для представления структурированных данных. Давайте создадим такую таблицу и сопоставим ее с пользовательскими данными XML.

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

## Работа с тегами многосекционных структурированных документов

Структурированные теги документа могут охватывать несколько разделов документа. В этом разделе мы рассмотрим, как работать с многосекционными SDT.

```java
Document doc = new Document("MultiSectionDocument.docx");
NodeCollection tags = doc.getChildNodes(NodeType.STRUCTURED_DOCUMENT_TAG_RANGE_START, true);

for (StructuredDocumentTagRangeStart tag : tags) {
    System.out.println(tag.getTitle());
}

doc.save("ModifiedMultiSectionDocument.docx");
```

## Заключение

Структурированные теги документов в Aspose.Words для Java предоставляют универсальный способ управления и форматирования содержимого в ваших документах. Независимо от того, нужно ли вам создавать шаблоны, формы или динамические документы, SDT предлагают необходимую вам гибкость и контроль. Следуя примерам и рекомендациям, приведенным в этой статье, вы можете использовать возможности SDT для улучшения задач по обработке документов.

## Часто задаваемые вопросы

### Какова цель структурированных тегов документов (SDT)?

Структурированные теги документов (SDT) служат для организации и форматирования содержимого документов, упрощая создание шаблонов, форм и структурированных документов.

### Как проверить текущее состояние Checkbox SDT?

Вы можете проверить текущее состояние SDT флажка, используя `setChecked` метод, как показано в статье.

### Могу ли я применять стили к элементам управления содержимым?

Да, вы можете применять стили к элементам управления содержимым, чтобы настроить их внешний вид в документе.

### Можно ли привязать SDT к пользовательским XML-данным?

Да, вы можете привязать SDT к пользовательским данным XML, что позволит динамически генерировать контент и отображать данные.

### Что такое повторяющиеся разделы в SDT?

Повторяющиеся разделы в SDT позволяют создавать таблицы с динамическими данными, в которых строки могут повторяться на основе сопоставленных XML-данных.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}