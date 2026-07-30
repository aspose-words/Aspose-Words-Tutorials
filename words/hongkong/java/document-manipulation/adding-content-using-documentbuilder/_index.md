---
date: 2026-01-01
description: 學習如何使用 Aspose.Words for Java 的 DocumentBuilder 建立表單欄位，並加入文字、表格、圖片、超連結等。開發人員的逐步指南。
linktitle: Adding Content using DocumentBuilder
second_title: Aspose.Words Java Document Processing API
title: 如何在 Aspose.Words for Java 中使用 DocumentBuilder 建立表單欄位並加入內容
url: /zh-hant/java/document-manipulation/adding-content-using-documentbuilder/
weight: 26
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for Java 的 DocumentBuilder 添加內容

## 使用 Aspose.Words for Java 的 DocumentBuilder 添加內容簡介

在本分步指南中，您將 **建立表單欄位**，並將各種內容——文字、表格、水平線、HTML、超連結、圖片等——加入 Word 文件，使用 Aspose.Words for Java。無論是建立報告、合約範本，或是互動式表單，`DocumentBuilder` 類別都能讓您對每個元素進行精細控制。讓我們立即開始吧！

## 快速解答
- **如何建立表單欄位？** 在 `DocumentBuilder` 上使用 `insertTextInput`、`insertCheckBox` 或 `insertComboBox`。
- **哪個方法可加入純文字？** 呼叫 `builder.write("Your text")` 或 `builder.writeln("Your text")`。
- **可以插入水平線嗎？** 可以——`builder.insertHorizontalRule()` 會加入分隔線。
- **如何嵌入 HTML？** 使用 `builder.insertHtml("<p>HTML content</p>")`。
- **如何加入行內圖片？** `builder.insertImage("path/to/image.png")` 會將圖片置於文字流中。

## DocumentBuilder 是什麼？為什麼使用它來建立表單欄位？

`DocumentBuilder` 是 Aspose.Words 提供的流暢 API，用於以程式方式建構與編輯 Word 文件。它抽象化了底層的 OpenXML 結構，讓您只需關注 *要加入什麼*（例如 **表單欄位**），而不必在意 *XML 如何呈現*。因此它非常適合產生動態表單、合約或任何需要使用者互動的文件。

## 前置條件

在開始之前，請確保您的專案已安裝 Aspose.Words for Java 套件。您可以從 [此處](https://releases.aspose.com/words/java/) 下載。

## Adding Text (how to add text)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a simple text paragraph
builder.write("This is a simple text paragraph.");

// Save the document
doc.save("path/to/your/document.docx");
```

## Adding Tables

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

## Adding a Horizontal Rule (add horizontal rule)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a horizontal rule
builder.insertHorizontalRule();

// Save the document
doc.save("path/to/your/document.docx");
```

## Adding Form Fields (create form fields)

### Text Input Form Field

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a text input form field
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### Check Box Form Field

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a check box form field
builder.insertCheckBox("CheckBox", true, true, 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### Combo Box Form Field

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

## Adding HTML (insert html word)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert HTML content
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// Save the document
doc.save("path/to/your/document.docx");
```

## Adding Hyperlinks (how to add hyperlink)

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

## Adding a Table of Contents

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

## Adding Images

### Inline Image (insert inline image)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");

// Save the document
doc.save("path/to/your/document.docx");
```

### Floating Image

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// Save the document
doc.save("path/to/your/document.docx");
```

## Adding Paragraphs

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

## Moving the Cursor (Step 10)

您可以使用 `moveToParagraph`、`moveToCell` 等方法來控制文件內的游標位置。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

這些是使用 Aspose.Words for Java 的 `DocumentBuilder` 可執行的一些常見操作。請參考函式庫文件以探索更進階的功能與自訂選項。祝您文件製作愉快！

## Conclusion

在本完整指南中，我們示範了如何 **建立表單欄位**，以及如何使用 Aspose.Words for Java 的 `DocumentBuilder` 加入各類內容——文字、表格、水平線、HTML、超連結、目錄、圖片、格式化段落與游標導向。現在，您已具備穩固的基礎，能以程式方式產生動態、互動的 Word 文件。

## FAQ's

### Q: 什麼是 Aspose.Words for Java？

A: Aspose.Words for Java 是一套 Java 函式庫，允許開發者以程式方式建立、修改與操作 Microsoft Word 文件。它提供廣泛的功能，用於文件產生、格式設定與內容插入。

### Q: 如何在文件中加入目錄？

A: 若要加入目錄，請使用 `DocumentBuilder` 插入 TOC 欄位，然後在加入內容後呼叫 `doc.updateFields()`。

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

### Q: 如何使用 Aspose.Words for Java 在文件中插入圖片？

A: 您可以使用 `DocumentBuilder` 插入行內或浮動圖片。

#### Inline Image:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");
```

#### Floating Image:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### Q: 加入內容時可以格式化文字與段落嗎？

A: 可以，您可以使用 `DocumentBuilder` 來格式化文字與段落。寫入內容前，先設定字型屬性、段落對齊、縮排等。

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

### Q: 如何將游標移動到文件中的特定位置？

A: 使用 `moveToParagraph`、`moveToCell` 等方法，在插入新內容前定位游標。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

以上答案涵蓋了使用 Aspose.Words for Java 的 `DocumentBuilder` 時最常見的情境。欲取得更深入的資訊，請參考 [函式庫文件](https://reference.aspose.com/words/java/) 或加入 Aspose.Words 社群取得支援。

---

**最後更新：** 2026-01-01  
**測試環境：** Aspose.Words for Java 24.12  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}