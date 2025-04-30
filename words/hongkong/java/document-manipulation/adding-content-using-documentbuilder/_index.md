---
"description": "使用 Aspose.Words for Java 掌握文件建立。新增文字、表格、圖像等內容的逐步指南。輕鬆建立令人驚嘆的 Word 文件。"
"linktitle": "使用 DocumentBuilder 新增內容"
"second_title": "Aspose.Words Java文件處理API"
"title": "使用 Aspose.Words for Java 中的 DocumentBuilder 新增內容"
"url": "/zh-hant/java/document-manipulation/adding-content-using-documentbuilder/"
"weight": 26
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for Java 中的 DocumentBuilder 新增內容


## 使用 Aspose.Words for Java 中的 DocumentBuilder 新增內容簡介

在本逐步指南中，我們將探討如何使用 Aspose.Words for Java 的 DocumentBuilder 在 Word 文件中新增各種類型的內容。我們將介紹如何插入文字、表格、水平規則、表單欄位、HTML、超連結、目錄、內聯和浮動圖像、段落等。讓我們開始吧！

## 先決條件

在開始之前，請確保您的專案中已設定了 Aspose.Words for Java 程式庫。您可以從下載 [這裡](https://releases。aspose.com/words/java/).

## 新增文字

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 插入簡單文字段落
builder.write("This is a simple text paragraph.");

// 儲存文件
doc.save("path/to/your/document.docx");
```

## 新增表格

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 開始一個表
Table table = builder.startTable();

// 插入儲存格和內容
builder.insertCell();
builder.write("Cell 1");

builder.insertCell();
builder.write("Cell 2");

// 結束表
builder.endTable();

// 儲存文件
doc.save("path/to/your/document.docx");
```

## 添加水平線

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 插入水平線
builder.insertHorizontalRule();

// 儲存文件
doc.save("path/to/your/document.docx");
```

## 新增表單字段

### 文字輸入表單字段

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 插入文字輸入表單字段
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// 儲存文件
doc.save("path/to/your/document.docx");
```

### 複選框表單字段

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 插入複選框表單域
builder.insertCheckBox("CheckBox", true, true, 0);

// 儲存文件
doc.save("path/to/your/document.docx");
```

### 組合框表單字段

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 定義組合方塊的項目
String[] items = { "Option 1", "Option 2", "Option 3" };

// 插入組合框表單域
builder.insertComboBox("DropDown", items, 0);

// 儲存文件
doc.save("path/to/your/document.docx");
```

## 新增 HTML

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 插入 HTML 內容
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// 儲存文件
doc.save("path/to/your/document.docx");
```

## 新增超連結

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 插入超連結
builder.write("Visit ");
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Aspose Website", "http://www.aspose.com", 假);
builder.getFont().clearFormatting();
builder.write(" for more information.");

// 儲存文件
doc.save("path/to/your/document.docx");
```

## 新增目錄

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 插入目錄
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// 新增文件內容
// …

// 更新目錄
doc.updateFields();

// 儲存文件
doc.save("path/to/your/document.docx");
```

## 新增影像

### 內嵌影像

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 插入內嵌影像
builder.insertImage("path/to/your/image.png");

// 儲存文件
doc.save("path/to/your/document.docx");
```

### 浮動影像

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 插入浮動影像
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// 儲存文件
doc.save("path/to/your/document.docx");
```

## 新增段落

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 設定段落格式
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

// 插入段落
builder.writeln("This is a formatted paragraph.");

// 儲存文件
doc.save("path/to/your/document.docx");
```

## 步驟 10：移動遊標

您可以使用各種方法控製文件中的遊標位置，例如 `moveToParagraph`， `moveToCell`等等。以下是一個例子：

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 將遊標移到特定段落
builder.moveToParagraph(2, 0);

// 在新的遊標位置添加內容
builder.writeln("This is the 3rd paragraph.");
```

這些是您可以使用 Aspose.Words for Java 的 DocumentBuilder 執行的一些常見操作。探索庫的文檔以了解更多高級功能和自訂選項。祝您文件建立愉快！


## 結論

在本綜合指南中，我們探討了 Aspose.Words for Java 的 DocumentBuilder 在 Word 文件中新增各種類型內容的功能。我們已經介紹了文字、表格、水平規則、表單欄位、HTML、超連結、目錄、圖像、段落和遊標移動。

## 常見問題解答

### Q：什麼是 Aspose.Words for Java？

答：Aspose.Words for Java 是一個 Java 函式庫，可讓開發人員以程式設計方式建立、修改和操作 Microsoft Word 文件。它為文件生成、格式化和內容插入提供了廣泛的功能。

### Q：如何在我的文件中新增目錄？

答：若要新增目錄，請使用 `DocumentBuilder` 在文件中插入目錄字段。確保在新增內容後更新文件中的欄位以填入目錄。以下是一個例子：

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 插入目錄字段
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// 新增文件內容
// …

// 更新目錄
doc.updateFields();
```

### Q：如何使用 Aspose.Words for Java 將圖片插入文件？

答：您可以使用 `DocumentBuilder`。以下是兩者的範例：

#### 內嵌圖片：

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 插入內嵌影像
builder.insertImage("path/to/your/image.png");
```

#### 浮動影像：

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 插入浮動影像
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### Q：新增內容時可以設定文字和段落的格式嗎？

答：是的，您可以使用 `DocumentBuilder`。您可以設定字體屬性、段落對齊、縮排等。以下是一個例子：

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 設定字體和段落格式
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

// 插入格式化的段落
builder.writeln("This is a formatted paragraph.");
```

### Q：如何將遊標移到文件中的特定位置？

答：您可以使用以下方法控制遊標位置 `moveToParagraph`， `moveToCell`等等。以下是一個例子：

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 將遊標移到特定段落
builder.moveToParagraph(2, 0);

// 在新的遊標位置添加內容
builder.writeln("This is the 3rd paragraph.");
```

這些是一些常見問題和解答，可協助您開始使用 Aspose.Words for Java 的 DocumentBuilder。如果您還有其他問題或需要進一步的協助，請參閱 [圖書館的文獻](https://reference.aspose.com/words/java/) 或向 Aspose.Words 社群和支持資源尋求協助。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}