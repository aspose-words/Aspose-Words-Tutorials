---
title: 在 Aspose.Words for Java 中使用結構化文件標籤 (SDT)
linktitle: 使用結構化文件標籤 (SDT)
second_title: Aspose.Words Java 文件處理 API
description: 透過這份綜合指南了解如何在 Aspose.Words for Java 中使用結構化文件標籤 (SDT)。建立、修改 SDT 並將其綁定到自訂 XML 資料。
weight: 19
url: /zh-hant/java/document-manipulation/using-structured-document-tags/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中使用結構化文件標籤 (SDT)


## 在 Aspose.Words for Java 中使用結構化文件標籤 (SDT) 簡介

結構化文件標籤 (SDT) 是 Aspose.Words for Java 中的強大功能，可讓您在文件中建立和操作結構化內容。在本綜合指南中，我們將引導您了解在 Aspose.Words for Java 中使用 SDT 的各個面向。無論您是初學者還是經驗豐富的開發人員，您都會在本文中找到有價值的見解和實際範例。

## 入門

在深入了解細節之前，我們先設定環境並建立基本的 SDT。在本節中，我們將討論以下主題：

- 建立新文檔
- 新增結構化文件標籤
- 儲存文件

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

//建立 CHECKBOX 類型的結構化文件標籤
StructuredDocumentTag sdtCheckBox = new StructuredDocumentTag(doc, SdtType.CHECKBOX, MarkupLevel.INLINE);
builder.insertNode(sdtCheckBox);

//儲存文件
doc.save("WorkingWithSDT.docx");
```

## 檢查複選框 SDT 的目前狀態

將複選框 SDT 新增至文件後，您可能需要以程式設計方式檢查其目前狀態。當您需要驗證使用者輸入或根據複選框狀態執行特定操作時，這非常有用。

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtCheckBox = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtCheckBox.getSdtType() == SdtType.CHECKBOX) {
    //複選框被選中
    sdtCheckBox.setChecked(true);
}

doc.save("UpdatedDocument.docx");
```

## 修改內容控件

在本節中，我們將探討如何修改文件中的內容控制項。我們將介紹三種類型的內容控制項：純文字、下拉清單和圖片。

### 修改純文字內容控件

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtPlainText = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtPlainText.getSdtType() == SdtType.PLAIN_TEXT) {
    //清除現有內容
    sdtPlainText.removeAllChildren();

    //新增文字
    Paragraph para = (Paragraph) sdtPlainText.appendChild(new Paragraph(doc));
    Run run = new Run(doc, "New text goes here");
    para.appendChild(run);
}

doc.save("ModifiedDocument.docx");
```

### 修改下拉式清單內容控件

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtDropDown = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtDropDown.getSdtType() == SdtType.DROP_DOWN_LIST) {
    //從清單中選擇第二項
    SdtListItem secondItem = sdtDropDown.getListItems().get(2);
    sdtDropDown.getListItems().setSelectedValue(secondItem);
}

doc.save("ModifiedDocument.docx");
```

### 修改圖片內容控件

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtPicture = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);
Shape shape = (Shape) sdtPicture.getChild(NodeType.SHAPE, 0, true);

if (shape.hasImage()) {
    //將圖像替換為新圖像
    shape.getImageData().setImage("Watermark.png");
}

doc.save("ModifiedDocument.docx");
```

## 建立組合框內容控件

組合框內容控制項可讓使用者從預先定義的選項清單中進行選擇。讓我們在文檔中建立一個。

```java
Document doc = new Document();
StructuredDocumentTag sdtComboBox = new StructuredDocumentTag(doc, SdtType.COMBO_BOX, MarkupLevel.BLOCK);
sdtComboBox.getListItems().add(new SdtListItem("Choose an item", "-1"));
sdtComboBox.getListItems().add(new SdtListItem("Item 1", "1"));
sdtComboBox.getListItems().add(new SdtListItem("Item 2", "2"));
doc.getFirstSection().getBody().appendChild(sdtComboBox);

doc.save("ComboBoxDocument.docx");
```

## 使用富文本內容控件

富文本內容控制項非常適合為文件新增格式化文字。讓我們創建一個並設定其內容。

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

## 設定內容控制樣式

您可以將樣式套用至內容控制項以增強文件的視覺外觀。讓我們看看如何設定內容控制項的樣式。

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdt = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

//套用自訂樣式
Style style = doc.getStyles().getByStyleIdentifier(StyleIdentifier.QUOTE);
sdt.setStyle(style);

doc.save("StyledDocument.docx");
```

## 將 SDT 綁定到自訂 XML 數據

在某些情況下，您可能需要將 SDT 綁定到自訂 XML 資料以產生動態內容。讓我們探討一下如何實現這一目標。

```java
Document doc = new Document();
CustomXmlPart xmlPart = doc.getCustomXmlParts().add(UUID.randomUUID().toString(), "<root><text>Hello, World!</text></root>");
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.BLOCK);
doc.getFirstSection().getBody().appendChild(sdt);
sdt.getXmlMapping().setMapping(xmlPart, "/root[1]/text[1]", "");

doc.save("CustomXMLBinding.docx");
```

## 建立具有對應到自訂 XML 資料的重複部分的表

具有重複部分的表格對於呈現結構化資料非常有用。讓我們建立這樣一個表並將其對應到自訂 XML 資料。

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

## 使用多部分結構化文件標籤

結構化文件標籤可以跨越文件中的多個部分。在本節中，我們將探討如何使用多部分 SDT。

```java
Document doc = new Document("MultiSectionDocument.docx");
NodeCollection tags = doc.getChildNodes(NodeType.STRUCTURED_DOCUMENT_TAG_RANGE_START, true);

for (StructuredDocumentTagRangeStart tag : tags) {
    System.out.println(tag.getTitle());
}

doc.save("ModifiedMultiSectionDocument.docx");
```

## 結論

Aspose.Words for Java 中的結構化文件標籤提供了一種通用的方法來管理文件中的內容並設定其格式。無論您需要建立範本、表單或動態文檔，SDT 都能提供您所需的靈活性和控制力。透過遵循本文中提供的範例和指南，您可以利用 SDT 的強大功能來增強文件處理任務。

## 常見問題解答

### 結構化文件標籤 (SDT) 的用途是什麼？

結構化文件標籤 (SDT) 的目的是組織和格式化文件中的內容，從而更輕鬆地建立範本、表單和結構化文件。

### 如何檢查 Checkbox SDT 的目前狀態？

您可以使用以下命令檢查複選框 SDT 的目前狀態`setChecked`方法，如文章所示。

### 我可以將樣式套用到內容控制項嗎？

是的，您可以將樣式套用至內容控制項以自訂它們在文件中的外觀。

### 是否可以將 SDT 綁定到自訂 XML 資料？

是的，您可以將 SDT 綁定到自訂 XML 數據，從而允許動態內容產生和資料映射。

### SDT 中的重複部分是什麼？

SDT 中的重複部分可讓您建立包含動態資料的資料表，其中可以根據已對應的 XML 資料重複行。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
