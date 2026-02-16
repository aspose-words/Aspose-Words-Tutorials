---
date: 2026-02-16
description: 學習如何使用 Aspose.Words for Java 建立文字方塊、加入浮水印文字、將多個圖形群組、設定圖形長寬比，並將圖形放置於表格儲存格中。
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: 如何在 Aspose.Words for Java 中建立文字方塊並使用文件形狀
url: /zh-hant/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中使用文件形狀

## 介紹在 Aspose.Words for Java 中使用文件形狀

在本完整指南中，**您將學習如何建立文字方塊** 物件以及其他強大的形狀，使用 Aspose.Words for Java。形狀讓您能在 Word 文件中加入說明框、按鈕、浮水印、SmartArt 等，使文件在視覺上更具吸引力與互動性。我們將透過實務範例，從插入簡單文字方塊到群組多個形狀、設定長寬比、以及將形狀放入表格儲存格等步驟說明。

## 快速答案
- **什麼是新增文字方塊的主要方法？** 使用 `DocumentBuilder.insertShape(ShapeType.TEXT_BOX, …)`。
- **我可以將多個形狀群組在一起嗎？** 可以 – 建立 `GroupShape` 並加入子形狀。
- **如何鎖定或解除鎖定形狀的長寬比？** 呼叫 `shape.setAspectRatioLocked(true/false)`。
- **是否可以使用形狀加入浮水印？** 當然可以 – 插入帶有 `TEXT_PLAIN_TEXT` 的 `Shape`，並設定其填色/線條。
- **SmartArt 圖表能在 Aspose.Words 中使用嗎？** 可以 – 使用 `shape.hasSmartArt()` 偵測，並透過 `shape.updateSmartArtDrawing()` 更新。

## 什麼是文字方塊以及為什麼要建立文字方塊形狀？

文字方塊是一個容器，可容納格式化文字、圖片或其他形狀。於自動化流程中**建立文字方塊**，讓您能在頁面任意位置放置浮動內容，非常適合註解、說明框或裝飾元素，而不會影響主要文件的排版流程。

## 如何新增形狀

在開始撰寫程式碼之前，請確保已在專案中參考 Aspose.Words for Java。若尚未加入，請從官方網站下載程式庫：

[下載 Aspose.Words for Java](https://releases.aspose.com/words/java/)

### 將形狀加入文件

## 如何群組多個形狀

`GroupShape` 讓您可以將多個獨立形狀視為單一單位，方便一起移動或旋轉。

### 插入 GroupShape

以下是一個完整範例，建立群組、加入兩個不同形狀，並將群組插入文件。

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

## 如何建立文字方塊（create text box）

### 插入文字方塊形狀

`insertShape` 方法讓您輕鬆加入文字方塊。以下範例示範兩種定位與旋轉文字方塊的方式。

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

## 如何設定形狀的長寬比

### 管理長寬比

有時您需要讓形狀伸展而不保留原始比例。以下程式碼示範如何解除影像形狀的長寬比鎖定。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## 如何將形狀放置於表格儲存格中

### 在表格儲存格內放置形狀

以下為逐步範例，先建立表格，然後插入相對於頁面的浮水印形狀，同時也可放入儲存格內。

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
watermark.isLayoutInCell(true); // Display the shape outside of the table cell if it will be placed into a cell.
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

### 偵測 SmartArt 形狀

您可以使用 `hasSmartArt()` 方法在文件中程式化搜尋 SmartArt 物件。

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### 更新 SmartArt 繪圖

定位到 SmartArt 形狀後，可透過 `updateSmartArtDrawing()` 重新整理其內部繪圖資料。

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## 結論

在本指南中，我們介紹了如何**建立文字方塊** 物件、群組多個形狀、調整長寬比、將形狀嵌入表格儲存格、加入浮水印，以及使用 Aspose.Words for Java 操作 SmartArt 圖表。這些技巧讓您能以程式方式建立內容豐富、互動性高的 Word 文件。

## 常見問題

### 什麼是 Aspose.Words for Java？

Aspose.Words for Java 是一套 Java 程式庫，讓開發者能以程式方式建立、修改與轉換 Word 文件。它提供廣泛的功能與工具，以處理各種格式的文件。

### 如何下載 Aspose.Words for Java？

您可透過以下連結從 Aspose 官方網站下載 Aspose.Words for Java：

[下載 Aspose.Words for Java](https://releases.aspose.com/words/java/)

### 使用文件形狀的好處是什麼？

文件形狀可為您的文件增添視覺元素與互動性，使內容更具吸引力與資訊性。透過形狀，您可以建立說明框、按鈕、圖片、浮水印等，提升整體使用者體驗。

### 我可以自訂形狀的外觀嗎？

可以，您可以透過調整大小、位置、旋轉角度與填色等屬性，自訂形狀的外觀。Aspose.Words for Java 提供豐富的形狀自訂選項。

### Aspose.Words for Java 是否相容於 SmartArt？

是的，Aspose.Words for Java 支援 SmartArt 形狀，讓您能在文件中處理複雜的圖表與圖形。

## 常見問答

**Q: 我可以在同一個形狀內同時結合文字方塊與圖片嗎？**  
A: 可以。先建立文字方塊形狀後，使用 `builder.insertImage()` 插入圖片，然後依需求調整版面配置。

**Q: 如何確保浮水印顯示在所有文件內容的背後？**  
A: 將形狀的 `WrapType` 設為 `NONE`，並將 `RelativeHorizontalPosition` 與 `RelativeVerticalPosition` 設為 `PAGE`，即可將浮水印置於主流程之後。

**Q: 是否可以在 Word 中為群組形狀加入動畫效果？**  
A: 雖然 Aspose.Words 能建立與群組形狀，但動畫功能不受支援，因為動畫屬於 Word UI 的特性。

**Q: 支援 SmartArt 需要哪個版本的 Aspose.Words？**  
A: SmartArt 偵測與更新功能自 Aspose.Words 20.9 for Java 版起即提供，之後的版本皆支援。

**Q: 程式庫在處理大量形狀的巨型文件時效能如何？**  
A: 效能良好。可使用 `doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2010)` 或更高版本，以提升大量形狀文件的處理效能。

---

**最後更新：** 2026-02-16  
**測試環境：** Aspose.Words for Java 24.12  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}