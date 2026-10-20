---
date: 2025-12-14
description: 了解如何使用 Aspose.Words for Java **插入圖片形狀**。本指南將示範如何新增形狀、建立文字方塊形狀、在表格中放置形狀、設定形狀長寬比，以及加入標註形狀。
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: 在 Aspose.Words for Java 中使用文件形狀
url: /zh-hant/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Aspose.Words for Java **插入圖片形狀**

在本完整教學中，您將了解如何使用 Aspose.Words for Java **插入圖片形狀** 物件到 Word 文件。無論您是建立報告、行銷宣傳資料，或是互動表單，形狀都能讓您加入標註、按鈕、文字方塊、浮水印，甚至 SmartArt。我們將逐步說明每個步驟，解釋為何使用特定形狀，並提供可直接執行的程式碼片段。

## 快速解答
- **什麼是新增形狀的主要方式？** 使用 `DocumentBuilder.insertShape` 或建立 `Shape` 實例並將其加入文件樹。  
- **我可以將圖片作為形狀插入嗎？** 可以——呼叫 `builder.insertImage`，然後將回傳的 `Shape` 像其他形狀一樣處理。  
- **如何保持形狀的長寬比？** 根據需求設定 `shape.setAspectRatioLocked(true)` 或 `false`。  
- **可以將形狀群組化嗎？** 當然可以——將它們包裹在 `GroupShape` 中，並將群組作為單一節點插入。  
- **SmartArt 圖表能在 Aspose.Words 中使用嗎？** 可以，您可以以程式方式偵測並更新 SmartArt 形狀。

## 什麼是 **插入圖片形狀**？
「*圖片形狀*」是一種視覺元素，可在 Word 文件中容納點陣圖或向量圖形。在 Aspose.Words 中，圖片以 `Shape` 物件表示，讓您完整掌控大小、位置、旋轉與環繞方式。

## 為什麼在文件中使用形狀？
- **視覺衝擊力：** 形狀能吸引注意力至關鍵資訊。  
- **互動性：** 按鈕與標註可連結至 URL 或書籤。  
- **版面彈性：** 以絕對或相對座標精確定位圖形。  
- **自動化：** 無需手動編輯即可產生複雜版面。

## 前置條件
- Java Development Kit (JDK 8 或以上)  
- Aspose.Words for Java 程式庫（從官方網站下載）  
- 具備 Java 及物件導向程式設計的基本知識  

您可以在此下載程式庫：[Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

## 如何 **新增形狀** – 插入 GroupShape
`GroupShape` 允許您將多個形狀視為單一單元，方便一次移動或格式化多個元素。

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

## 建立 **文字方塊形狀**
文字方塊是一個可容納格式化文字的容器，您亦可將其旋轉以呈現動態外觀。

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

## 設定 **形狀長寬比**
有時您需要形狀自由伸展，有時則希望保留原始比例。控制長寬比相當簡單。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## 在 **表格中放置形狀**
將形狀嵌入表格儲存格對於報告版面相當實用。以下範例會建立表格，並插入跨整頁的浮水印樣式形狀。

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

## 新增 **標註形狀**
標註形狀非常適合突顯備註或警示。上述程式碼已示範 `ACCENT_BORDER_CALLOUT_1`，您可將 `ShapeType` 替換為任何標註變體以符合設計需求。

## 操作 SmartArt 形狀

### 偵測 SmartArt 形狀
可透過程式方式辨識 SmartArt 圖表，讓您依需求處理或取代它們。

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### 更新 SmartArt 繪圖
偵測後，您可重新整理 SmartArt 圖形，使其反映任何資料變更。

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## 常見問題與技巧
- **形狀未顯示：** 確認使用 `builder.insertNode` 將形狀插入於目標節點之後。  
- **旋轉異常：** 請記得旋轉是以形狀中心為基準，必要時調整 `setLeft`/`setTop`。  
- **長寬比被鎖定：** 預設多數形狀會鎖定長寬比，呼叫 `setAspectRatioLocked(false)` 可自由伸展。  
- **SmartArt 偵測失敗：** 請確認使用支援 SmartArt 的 Aspose.Words 版本（v24 以上）。

## 常見問與答

**Q: 什麼是 Aspose.Words for Java？**  
A: Aspose.Words for Java 是一個 Java 程式庫，讓開發人員能以程式方式建立、修改與轉換 Word 文件。它提供廣泛的功能與工具，以處理各種格式的文件。

**Q: 如何下載 Aspose.Words for Java？**  
A: 您可透過以下連結從 Aspose 官方網站下載 Aspose.Words for Java：[Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

**Q: 使用文件形狀有什麼好處？**  
A: 文件形狀能為文件加入視覺元素與互動性，使其更具吸引力與資訊性。透過形狀，您可以建立標註、按鈕、圖片、浮水印等，提升整體使用者體驗。

**Q: 我可以自訂形狀的外觀嗎？**  
A: 可以，您可透過調整大小、位置、旋轉與填色等屬性來自訂形狀外觀。Aspose.Words for Java 提供豐富的形狀自訂選項。

**Q: Aspose.Words for Java 是否相容於 SmartArt？**  
A: 是的，Aspose.Words for Java 支援 SmartArt 形狀，讓您能在文件中使用複雜的圖表與圖形。

---

**最後更新：** 2025-12-14  
**測試環境：** Aspose.Words for Java 24.12（最新）  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}