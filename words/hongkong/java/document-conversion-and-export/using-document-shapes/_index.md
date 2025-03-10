---
title: 在 Aspose.Words for Java 中使用文件形狀
linktitle: 使用文檔形狀
second_title: Aspose.Words Java 文件處理 API
description: 釋放 Aspose.Words for Java 中文件形狀的力量。透過逐步範例學習建立具有視覺吸引力的文件。
weight: 14
url: /zh-hant/java/document-conversion-and-export/using-document-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中使用文件形狀


## 在 Aspose.Words for Java 中使用文件形狀簡介

在本綜合指南中，我們將深入研究 Aspose.Words for Java 中的文件形狀世界。在創建具有視覺吸引力的互動式文件時，形狀是必不可少的元素。無論您需要新增標註、按鈕、圖像或浮水印，Aspose.Words for Java 都提供了高效能完成此操作的工具。讓我們透過原始程式碼範例逐步探索如何使用這些形狀。

## 文件形狀入門

在我們開始編寫程式碼之前，讓我們先設定一下環境。確保您已將 Aspose.Words for Java 整合到您的專案中。如果還沒有，您可以從 Aspose 網站下載[下載 Java 版 Aspose.Words](https://releases.aspose.com/words/java/)

## 將形狀新增至文檔

### 插入組形狀

一個`GroupShape`允許您將多個形狀組合在一起。以下是建立和插入的方法`GroupShape`:

```java
Document doc = new Document();
doc.ensureMinimum();

GroupShape groupShape = new GroupShape(doc);
Shape accentBorderShape = new Shape(doc, ShapeType.ACCENT_BORDER_CALLOUT_1);
accentBorderShape.setWidth(100.0);
accentBorderShape.setHeight(100.0);

groupShape.appendChild(accentBorderShape);

Shape actionButtonShape = new Shape(doc, ShapeType.ACTION_BUTTON_BEGINNING);
actionButtonShape.setLeft(100.0);
actionButtonShape.setWidth(100.0);
actionButtonShape.setHeight(200.0);

groupShape.appendChild(actionButtonShape);

groupShape.setWidth(200.0);
groupShape.setHeight(200.0);
groupShape.setCoordSize(new Dimension(200, 200));

DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertNode(groupShape);

doc.save("Your Directory Path" + "WorkingWithShapes.AddGroupShape.docx");
```

### 插入文字方塊形狀

若要插入文字方塊形狀，您可以使用`insertShape`方法如下例所示：

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertShape(ShapeType.TEXT_BOX, RelativeHorizontalPosition.PAGE, 100.0,
    RelativeVerticalPosition.PAGE, 100.0, 50.0, 50.0, WrapType.NONE);

shape.setRotation(30.0);
builder.writeln();

shape = builder.insertShape(ShapeType.TEXT_BOX, 50.0, 50.0);
shape.setRotation(30.0);

OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL);

doc.save("Your Directory Path" + "WorkingWithShapes.InsertShape.docx", saveOptions);
```

## 操縱形狀屬性

### 管理縱橫比

您可以控制是否鎖定形狀的縱橫比。以下是解鎖形狀縱橫比的方法：

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

### 將形狀放入表格儲存格中

如果需要在表格儲存格內放置形狀，可以使用以下程式碼來實現：

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

builder.startTable();
builder.getRowFormat().setHeight(100.0);
builder.getRowFormat().setHeightRule(HeightRule.EXACTLY);

for (int i = 0; i < 31; i++) {
    if (i != 0 && i % 7 == 0)
        builder.endRow();

    builder.insertCell();
    builder.write("Cell contents");
}

builder.endTable();

Shape watermark = new Shape(doc, ShapeType.TEXT_PLAIN_TEXT);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
watermark.isLayoutInCell(true); //如果將形狀放入儲存格中，則顯示表格儲存格外部的形狀。
watermark.setWidth(300.0);
watermark.setHeight(70.0);
watermark.setHorizontalAlignment(HorizontalAlignment.CENTER);
watermark.setVerticalAlignment(VerticalAlignment.CENTER);
watermark.setRotation(-40);
watermark.setFillColor(Color.GRAY);
watermark.setStrokeColor(Color.GRAY);
watermark.getTextPath().setText("watermarkText");
watermark.getTextPath().setFontFamily("Arial");
watermark.setName("WaterMark_{Guid.NewGuid()}");
watermark.setWrapType(WrapType.NONE);

Run run = (Run) doc.getChildNodes(NodeType.RUN, true).get(doc.getChildNodes(NodeType.RUN, true).getCount() - 1);
builder.moveTo(run);
builder.insertNode(watermark);

doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2010);
doc.save("Your Directory Path" + "WorkingWithShapes.LayoutInCell.docx");
```

## 使用 SmartArt 形狀

### 檢測 SmartArt 形狀

您可以使用以下程式碼偵測文件中的 SmartArt 形狀：

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### 更新 SmartArt 繪圖

若要更新文件中的 SmartArt 繪圖，請使用下列程式碼：

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## 結論

在本指南中，我們探索了 Aspose.Words for Java 中的文檔形狀世界。您已經學習如何在文件中添加各種形狀、操作其屬性以及使用 SmartArt 形狀。有了這些知識，您就可以輕鬆建立具有視覺吸引力的互動式文件。

## 常見問題解答

### 什麼是 Java 版 Aspose.Words？

Aspose.Words for Java 是一個 Java 函式庫，可讓開發人員以程式設計方式建立、修改和轉換 Word 文件。它提供了廣泛的功能和工具來處理各種格式的文件。

### 如何下載 Aspose.Words for Java？

您可以透過以下連結從 Aspose 網站下載 Aspose.Words for Java：[下載 Java 版 Aspose.Words](https://releases.aspose.com/words/java/)

### 使用文件形狀有什麼好處？

文件形狀為文件添加視覺元素和互動性，使文件更具吸引力和資訊量。使用形狀，您可以建立標註、按鈕、影像、浮水印等，從而增強整體使用者體驗。

### 我可以自訂形狀的外觀嗎？

是的，您可以透過調整形狀的屬性（例如大小、位置、旋轉和填滿顏色）來自訂形狀的外觀。 Aspose.Words for Java 提供了廣泛的形狀自訂選項。

### Aspose.Words for Java 與 SmartArt 相容嗎？

是的，Aspose.Words for Java 支援 SmartArt 形狀，讓您可以在文件中處理複雜的圖表和圖形。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
