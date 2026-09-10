---
date: 2026-01-01
description: Узнайте, как извлекать текст с помощью Aspose.Words для Java. Это пошаговое
  руководство демонстрирует различные методы извлечения с готовыми к запуску примерами
  кода.
linktitle: Extracting Content from Documents
second_title: Aspose.Words Java Document Processing API
title: Как извлечь текст с помощью Aspose.Words для Java
url: /ru/java/document-manipulation/extracting-content-from-documents/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Как извлечь текст с помощью Aspose.Words для Java

## Как извлечь текст с помощью Aspose.Words для Java

В мире обработки документов **как извлечь текст с помощью Aspose.Words** — частый вопрос у Java‑разработчиков. Независимо от того, нужно ли получить обычный текст, таблицы, изображения или такие специфические элементы, как закладки или комментарии, Aspose.Words для Java предоставляет богатый API, который делает задачу простой. В этом руководстве мы пройдем через десятки сценариев извлечения, объясним, почему каждый подход важен, и предоставим готовые к запуску примеры кода, которые вы можете вставить в свой проект.

## Быстрые ответы
- **Какая библиотека нужна?** Aspose.Words для Java (скачать с официального сайта).  
- **Можно ли извлечь только обычный текст?** Да — используйте `Document.getText()` или `DocumentBuilder` с полями.  
- **Можно ли извлечь содержимое между закладками?** Конечно, используйте `BookmarkStart`/`BookmarkEnd` вместе с `ExtractContentHelper`.  
- **Нужна ли лицензия для продакшн?** Коммерческая лицензия требуется для использования не в режиме пробной версии.  
- **Какие версии Java поддерживаются?** Java 8 и новее полностью совместимы.

## Предварительные требования

1. **Aspose.Words для Java** — установите библиотеку и добавьте её в проект. Скачать её можно [здесь](https://releases.aspose.com/words/java/).  
2. **Пример документа** — для примеров будем использовать файл `Extract content.docx`. Поместите его в папку, к которой ваш код сможет обращаться.

## Извлечение содержимого между узлами уровня блока

```java
// Java code sample for extracting content between block-level nodes
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph startPara = (Paragraph) doc.getLastSection().getChild(NodeType.PARAGRAPH, 2, true);
Table endTable = (Table) doc.getLastSection().getChild(NodeType.TABLE, 0, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara, endTable, true);
Collections.reverse(extractedNodes);
while (extractedNodes.size() > 0) {
    endTable.getParentNode().insertAfter((Node) extractedNodes.get(0), endTable);
    extractedNodes.remove(0);
}
doc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenBlockLevelNodes.docx");
```

## Извлечение содержимого между закладками

```java
// Java code sample for extracting content between bookmarks
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Bookmark bookmark = doc.getRange().getBookmarks().get("Bookmark1");
BookmarkStart bookmarkStart = bookmark.getBookmarkStart();
BookmarkEnd bookmarkEnd = bookmark.getBookmarkEnd();
ArrayList<Node> extractedNodesInclusive = ExtractContentHelper.extractContent(bookmarkStart, bookmarkEnd, true);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodesInclusive);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenBookmark.IncludingBookmark.docx");
ArrayList<Node> extractedNodesExclusive = ExtractContentHelper.extractContent(bookmarkStart, bookmarkEnd, false);
dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodesExclusive);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenBookmark.WithoutBookmark.docx");
```

## Извлечение содержимого между диапазонами комментариев

```java
// Java code sample for extracting content between comment ranges
Document doc = new Document("Your Directory Path" + "Extract content.docx");
CommentRangeStart commentStart = (CommentRangeStart) doc.getChild(NodeType.COMMENT_RANGE_START, 0, true);
CommentRangeEnd commentEnd = (CommentRangeEnd) doc.getChild(NodeType.COMMENT_RANGE_END, 0, true);
ArrayList<Node> extractedNodesInclusive = ExtractContentHelper.extractContent(commentStart, commentEnd, true);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodesInclusive);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenCommentRange.IncludingComment.docx");
ArrayList<Node> extractedNodesExclusive = ExtractContentHelper.extractContent(commentStart, commentEnd, false);
dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodesExclusive);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenCommentRange.WithoutComment.docx");
```

## Извлечение содержимого между абзацами

```java
// Java code sample for extracting content between paragraphs
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph startPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 6, true);
Paragraph endPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 10, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara, endPara, true);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenParagraphs.docx");
```

## Извлечение содержимого между стилями абзацев

```java
// Java code sample for extracting content between paragraph styles
Document doc = new Document("Your Directory Path" + "Extract content.docx");
ArrayList<Paragraph> parasStyleHeading1 = ExtractContentHelper.paragraphsByStyleName(doc, "Heading 1");
ArrayList<Paragraph> parasStyleHeading3 = ExtractContentHelper.paragraphsByStyleName(doc, "Heading 3");
Node startPara1 = parasStyleHeading1.get(0);
Node endPara1 = parasStyleHeading3.get(0);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara1, endPara1, false);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenParagraphStyles.docx");
```

## Извлечение содержимого между запусками (Runs)

```java
// Java code sample for extracting content between runs
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph para = (Paragraph) doc.getChild(NodeType.PARAGRAPH, 7, true);
Run startRun = para.getRuns().get(1);
Run endRun = para.getRuns().get(4);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startRun, endRun, true);
Node node = (Node) extractedNodes.get(0);
System.out.println(node.toString());
```

## Извлечение содержимого с помощью DocumentVisitor

```java
// Java code sample for extracting content using DocumentVisitor
Document doc = new Document("Your Directory Path" + "Absolute position tab.docx");
MyDocToTxtWriter myConverter = new MyDocToTxtWriter();
doc.accept(myConverter);
System.out.println(myConverter.getText());
```

## Извлечение содержимого с помощью Field

```java
// Java code sample for extracting content using Field
Document doc = new Document("Your Directory Path" + "Extract content.docx");
DocumentBuilder builder = new DocumentBuilder(doc);
builder.moveToMergeField("Fullname", false, false);
FieldStart startField = (FieldStart) builder.getCurrentNode();
Paragraph endPara = (Paragraph) doc.getFirstSection().getChild(NodeType.PARAGRAPH, 5, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startField, endPara, false);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentUsingField.docx");
```

## Извлечение оглавления (Table of Contents)

```java
// Java code sample for extracting table of contents
Document doc = new Document("Your Directory Path" + "Table of contents.docx");
for (Field field : doc.getRange().getFields()) {
    if (field.getType() == FieldType.FIELD_HYPERLINK) {
        FieldHyperlink hyperlink = (FieldHyperlink) field;
        if (hyperlink.getSubAddress() != null && hyperlink.getSubAddress().startsWith("_Toc")) {
            Paragraph tocItem = (Paragraph) field.getStart().getAncestor(NodeType.PARAGRAPH);
            System.out.println(tocItem.toString().trim());
            System.out.println("------------------");
            Bookmark bm = doc.getRange().getBookmarks().get(hyperlink.getSubAddress());
            Paragraph pointer = (Paragraph) bm.getBookmarkStart().getAncestor(NodeType.PARAGRAPH);
            System.out.println(pointer.toString());
        }
    }
}
```

## Извлечение только текста

```java
// Java code sample for extracting text only
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertField("MERGEFIELD Field");
System.out.println("GetText() Result: " + doc.getText());
System.out.println("ToString() Result: " + doc.toString());
```

## Извлечение содержимого на основе стилей

```java
// Java code sample for extracting content based on styles
Document doc = new Document("Your Directory Path" + "Styles.docx");
final String PARA_STYLE = "Heading 1";
final String RUN_STYLE = "Intense Emphasis";
ArrayList<Paragraph> paragraphs = paragraphsByStyleName(doc, PARA_STYLE);
System.out.println("Paragraphs with \"{paraStyle}\" styles ({paragraphs.Count}):");
for (Paragraph paragraph : paragraphs)
    System.out.println(paragraph.toString(SaveFormat.TEXT));
ArrayList<Run> runs = runsByStyleName(doc, RUN_STYLE);
System.out.println("\nRuns with \"{runStyle}\" styles ({runs.Count}):");
for (Run run : runs)
    System.out.println(run.getRange().getText());
}

public ArrayList<Paragraph> paragraphsByStyleName(Document doc, String styleName) {
    ArrayList<Paragraph> paragraphsWithStyle = new ArrayList<Paragraph>();
    NodeCollection paragraphs = doc.getChildNodes(NodeType.PARAGRAPH, true);
    for (Paragraph paragraph : (Iterable<Paragraph>) paragraphs) {
        if (paragraph.getParagraphFormat().getStyle().getName().equals(styleName))
            paragraphsWithStyle.add(paragraph);
    }
    return paragraphsWithStyle;
}

public ArrayList<Run> runsByStyleName(Document doc, String styleName) {
    ArrayList<Run> runsWithStyle = new ArrayList<Run>();
    NodeCollection runs = doc.getChildNodes(NodeType.RUN, true);
    for (Run run : (Iterable<Run>) runs) {
        if (run.getFont().getStyle().getName().equals(styleName))
            runsWithStyle.add(run);
    }
    return runsWithStyle;
}
```

## Извлечение и вывод текста

```java
// Java code sample for extracting and printing text
Document doc = new Document("Your Directory Path" + "Tables.docx");
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);
System.out.println("Contents of the table: ");
System.out.println(table.getRange().getText());
System.out.println("\nContents of the row: ");
System.out.println(table.getRows().get(1).getRange().getText());
System.out.println("\nContents of the cell: ");
System.out.println(table.getLastRow().getLastCell().getRange().getText());
```

## Извлечение изображений в файлы

```java
// Java code sample for extracting images to files
Document doc = new Document("Your Directory Path" + "Images.docx");
NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
int imageIndex = 0;
for (Shape shape : (Iterable<Shape>) shapes) {
    if (shape.hasImage()) {
        String imageFileName = MessageFormat.format("Image.ExportImages.{0}_{1}",
                imageIndex, FileFormatUtil.imageTypeToExtension(shape.getImageData().getImageType()));
        shape.getImageData().save("Your Directory Path" + imageFileName);
        imageIndex++;
    }
}
```

## Заключение

Поздравляем! Теперь у вас есть полноценный набор инструментов для **как извлечь текст с помощью Aspose.Words** в Java. От узлов уровня блока до закладок, комментариев, стилей и даже изображений — API предоставляет тонкий контроль над тем, что вы извлекаете из документа. Используйте эти фрагменты как основу, адаптируйте их под свои структуры файлов и автоматизируйте процесс извлечения в больших наборах документов.

## Часто задаваемые вопросы

**В: Как извлечь содержимое из документа, защищённого паролем?**  
О: Загрузите документ с помощью конструктора с паролем: `new Document(path, new LoadOptions("password"))`, затем выполните любой из методов извлечения, показанных выше.

**В: Можно ли извлечь содержимое из нескольких документов за один запуск?**  
О: Да. Пройдите в цикле список путей к файлам, создайте `Document` для каждого и примените одну и ту же логику извлечения внутри цикла.

**В: Есть ли способ извлечь только видимый текст (игнорируя скрытый или коды полей)?**  
О: Используйте `doc.getText()` для получения обычного видимого текста. Для более тонкой настройки пройдитесь по узлам и отфильтруйте их по `NodeType.RUN` и `Run.getFont().getHidden()`.

**В: В какие форматы можно сохранять извлечённое содержимое?**  
О: После извлечения вы можете сохранить `Document` как DOCX, PDF, HTML, TXT или любой другой формат, поддерживаемый Aspose.Words, с помощью `doc.save("output.pdf")`.

**В: Поддерживает ли Aspose.Words извлечение содержимого из больших (сотни МБ) файлов?**  
О: Да, но рекомендуется использовать `LoadOptions` с указанием `LoadFormat` и `MemoryOptimization`, чтобы снизить потребление памяти.

---

**Последнее обновление:** 2026-01-01  
**Тестировано с:** Aspose.Words для Java 24.12  
**Автор:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}