---
date: 2026-01-01
description: Изучите, как создавать поля формы и добавлять текст, таблицы, изображения,
  гиперссылки и многое другое с помощью Aspose.Words for Java DocumentBuilder. Пошаговое
  руководство для разработчиков.
linktitle: Adding Content using DocumentBuilder
second_title: Aspose.Words Java Document Processing API
title: Как создать поля формы и добавить содержимое с помощью DocumentBuilder в Aspose.Words
  для Java
url: /ru/java/document-manipulation/adding-content-using-documentbuilder/
weight: 26
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Добавление контента с помощью DocumentBuilder в Aspose.Words для Java

## Введение в добавление контента с помощью DocumentBuilder в Aspose.Words для Java

В этом пошаговом руководстве вы **создадите поля формы** и добавите разнообразный контент — текст, таблицы, горизонтальные линии, HTML, гиперссылки, изображения и многое другое — в документ Word с помощью Aspose.Words для Java. Независимо от того, создаёте ли вы отчёт, шаблон контракта или интерактивную форму, класс `DocumentBuilder` предоставляет тонкий контроль над каждым элементом. Приступим!

## Быстрые ответы
- **Как создать поля формы?** Используйте `insertTextInput`, `insertCheckBox` или `insertComboBox` у объекта `DocumentBuilder`.
- **Какой метод добавляет обычный текст?** Вызовите `builder.write("Your text")` или `builder.writeln("Your text")`.
- **Можно ли вставить горизонтальную линию?** Да — `builder.insertHorizontalRule()` добавляет разделитель‑линию.
- **Как встроить HTML?** Используйте `builder.insertHtml("<p>HTML content</p>")`.
- **Как добавить встроенное изображение?** `builder.insertImage("path/to/image.png")` помещает изображение в поток текста.

## Что такое DocumentBuilder и почему использовать его для создания полей формы?

`DocumentBuilder` — это fluent‑API Aspose.Words для программного создания и редактирования документов Word. Он абстрагирует низкоуровневую структуру OpenXML, позволяя сосредоточиться на *том*, что вы хотите добавить — например, **поля формы** — вместо того, *как* выглядит XML. Это делает его идеальным для генерации динамических форм, контрактов и любых документов, требующих взаимодействия с пользователем.

## Требования

Прежде чем начать, убедитесь, что библиотека Aspose.Words для Java установлена в вашем проекте. Скачать её можно [здесь](https://releases.aspose.com/words/java/).

## Добавление текста (how to add text)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a simple text paragraph
builder.write("This is a simple text paragraph.");

// Save the document
doc.save("path/to/your/document.docx");
```

## Добавление таблиц

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

## Добавление горизонтальной линии (add horizontal rule)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a horizontal rule
builder.insertHorizontalRule();

// Save the document
doc.save("path/to/your/document.docx");
```

## Добавление полей формы (create form fields)

### Текстовое поле формы

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a text input form field
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### Флажок формы

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a check box form field
builder.insertCheckBox("CheckBox", true, true, 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### Выпадающий список формы

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

## Добавление HTML (insert html word)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert HTML content
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// Save the document
doc.save("path/to/your/document.docx");
```

## Добавление гиперссылок (how to add hyperlink)

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

## Добавление оглавления

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

## Добавление изображений

### Встроенное изображение (insert inline image)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");

// Save the document
doc.save("path/to/your/document.docx");
```

### Плавающее изображение

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// Save the document
doc.save("path/to/your/document.docx");
```

## Добавление абзацев

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

## Перемещение курсора (Step 10)

Вы можете управлять позицией курсора в документе с помощью методов, таких как `moveToParagraph`, `moveToCell` и т.д.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

Это некоторые распространённые операции, которые можно выполнять с помощью `DocumentBuilder` из Aspose.Words для Java. Изучайте документацию библиотеки для более продвинутых возможностей и вариантов настройки. Приятного создания документов!

## Заключение

В этом полном руководстве мы показали, как **создавать поля формы** и добавлять различные типы контента — текст, таблицы, горизонтальные линии, HTML, гиперссылки, оглавление, изображения, отформатированные абзацы и навигацию курсора — с помощью `DocumentBuilder` из Aspose.Words для Java. Теперь у вас есть надёжная база для программного создания динамических, интерактивных документов Word.

## Часто задаваемые вопросы

### В: Что такое Aspose.Words для Java?

О: Aspose.Words для Java — это Java‑библиотека, позволяющая разработчикам программно создавать, изменять и обрабатывать документы Microsoft Word. Она предоставляет широкий набор функций для генерации документов, их форматирования и вставки контента.

### В: Как добавить оглавление в документ?

О: Чтобы добавить оглавление, используйте `DocumentBuilder` для вставки поля TOC, а затем вызовите `doc.updateFields()` после добавления вашего контента.

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

### В: Как вставить изображения в документ с помощью Aspose.Words для Java?

О: Вы можете вставлять изображения как встроенные, так и плавающие, используя `DocumentBuilder`.

#### Встроенное изображение:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");
```

#### Плавающее изображение:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### В: Можно ли форматировать текст и абзацы при добавлении контента?

О: Да, вы можете форматировать текст и абзацы с помощью `DocumentBuilder`. Устанавливайте свойства шрифта, выравнивание абзаца, отступы и другие параметры перед записью контента.

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

### В: Как переместить курсор в определённое место документа?

О: Используйте методы, такие как `moveToParagraph`, `moveToCell` и т.д., чтобы позиционировать курсор перед вставкой нового контента.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

Эти ответы охватывают наиболее распространённые сценарии работы с `DocumentBuilder` из Aspose.Words для Java. Для более детальной информации обратитесь к [документации библиотеки](https://reference.aspose.com/words/java/) или присоединитесь к сообществу Aspose.Words для получения поддержки.

---

**Последнее обновление:** 2026-01-01  
**Тестировано с:** Aspose.Words для Java 24.12  
**Автор:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}