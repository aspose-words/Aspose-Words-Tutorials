---
date: 2026-01-09
description: 學習如何建立多層清單、套用段落樣式、設定段落對齊，並使用 Aspose.Words for Java 產生 Word 文件。本指南涵蓋專業文件的格式化技巧。
linktitle: Formatting Documents
second_title: Aspose.Words Java Document Processing API
title: 如何在 Aspose.Words for Java 中建立多層清單並格式化文件
url: /zh-hant/java/document-manipulation/formatting-documents/
weight: 29
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中格式化文件

## Aspose.Words for Java 中文件格式化簡介

在 Java 文件處理的領域，Aspose.Words for Java 是一個強大且多功能的工具。無論是產生報表、製作發票，或是建立複雜版面配置，您常常需要 **建立多層清單** 結構並套用精緻的段落樣式。本完整指南將逐步說明如何格式化文件、從頭產生 Word 文件，以及微調段落對齊、左縮排與其他排版細節。讓我們一步一步開始吧。

## 快速解答
- **如何建立多層清單？** 使用 `DocumentBuilder.getListFormat().applyNumberDefault()`，然後依序加入清單項目。  
- **可以設定段落對齊方式嗎？** 可以，呼叫 `ParagraphFormat.setAlignment(ParagraphAlignment.CENTER)` 或其他對齊方式。  
- **哪個方法可加入左縮排？** 使用 `ParagraphFormat.setLeftIndent(double)` 來定義左側邊距。  
- **如何以程式方式產生 Word 文件？** 建立 `Document`，使用 `DocumentBuilder` 加入內容，最後呼叫 `save("MyDoc.docx")`。  
- **有沒有方法套用自訂段落樣式？** 透過 `ParagraphFormat.setStyleIdentifier(StyleIdentifier.TITLE)` 設定樣式識別碼。

## 環境設定

在深入文件格式化的細節之前，先確保您的環境已正確設定。請確認已在專案中正確安裝與配置 Aspose.Words for Java。您可以從 [此處](https://releases.aspose.com/words/java/) 下載。

## 建立簡易文件

讓我們先 **產生 Word 文件**，使用 Aspose.Words for Java。以下 Java 程式碼片段示範如何建立文件並加入文字：

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello, Aspose.Words for Java!");
doc.save("MyDocument.docx");
```

## 調整亞洲文字與拉丁文字之間的間距

Aspose.Words for Java 提供強大的文字間距處理功能。您可以如以下範例自動調整亞洲文字與拉丁文字之間的間距：

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setAddSpaceBetweenFarEastAndAlpha(true);
paragraphFormat.setAddSpaceBetweenFarEastAndDigit(true);
builder.writeln("Automatically adjust space between Asian and Latin text");
builder.writeln("Automatically adjust space between Asian text and numbers");
doc.save("SpaceBetweenAsianAndLatinText.docx");
```

## 處理亞洲排版

若要控制亞洲排版設定，請參考以下程式碼片段：

```java
Document doc = new Document("AsianTypography.docx");
ParagraphFormat format = doc.getFirstSection().getBody().getParagraphs().get(0).getParagraphFormat();
format.setFarEastLineBreakControl(false);
format.setWordWrap(true);
format.setHangingPunctuation(false);
doc.save("AsianTypographyLineBreakGroup.docx");
```

## 段落格式化

Aspose.Words for Java 讓您 **設定段落對齊**、**設定左縮排**，以及輕鬆格式化段落。請參考此範例：

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setAlignment(ParagraphAlignment.CENTER);
paragraphFormat.setLeftIndent(50.0);
paragraphFormat.setRightIndent(50.0);
paragraphFormat.setSpaceAfter(25.0);
builder.writeln("I'm a very nice formatted paragraph. I'm intended to demonstrate how the left and right indents affect word wrapping.");
builder.writeln("I'm another nice formatted paragraph. I'm intended to demonstrate how the space after paragraph looks like.");
doc.save("ParagraphFormatting.docx");
```

## 多層清單格式化

建立 **多層清單** 結構是文件格式化中的常見需求。Aspose.Words for Java 讓此工作變得簡單：

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.getListFormat().applyNumberDefault();
builder.writeln("Item 1");
// Add more items here...
doc.save("MultilevelListFormatting.docx");
```

## 套用段落樣式

Aspose.Words for Java 讓您 **套用段落樣式** 變得毫不費力：

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.TITLE);
builder.write("Hello, Styled Paragraph!");
doc.save("ApplyParagraphStyle.docx");
```

## 為段落加入框線與底紋

透過加入框線與底紋，提升文件的視覺效果：

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
BorderCollection borders = builder.getParagraphFormat().getBorders();
// Customize borders here...
Shading shading = builder.getParagraphFormat().getShading();
// Customize shading here...
builder.write("I'm a formatted paragraph with double border and nice shading.");
doc.save("ApplyBordersAndShadingToParagraph.docx");
```

## 變更亞洲段落間距與縮排

微調亞洲文字的段落間距與縮排：

```java
Document doc = new Document("AsianTypography.docx");
ParagraphFormat format = doc.getFirstSection().getBody().getFirstParagraph().getParagraphFormat();
format.setCharacterUnitLeftIndent(10.0);
format.setCharacterUnitRightIndent(10.0);
format.setCharacterUnitFirstLineIndent(20.0);
format.setLineUnitBefore(5.0);
format.setLineUnitAfter(10.0);
doc.save("ChangeAsianParagraphSpacingAndIndents.docx");
```

## 吸附至格線

在處理亞洲字元時，透過吸附至格線來最佳化版面配置：

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Paragraph par = doc.getFirstSection().getBody().getFirstParagraph();
par.getParagraphFormat().setSnapToGrid(true);
builder.writeln("Lorem ipsum dolor sit amet, consectetur adipiscing elit...");
par.getRuns().get(0).getFont().setSnapToGrid(true);
doc.save("SnapToGrid.docx");
```

## 偵測段落樣式分隔符

如果需要在文件中找出樣式分隔符，可使用以下程式碼：

```java
Document doc = new Document("Document.docx");
for (Paragraph paragraph : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (paragraph.getBreakIsStyleSeparator())
    {
        System.out.println("Separator Found!");
    }
}
```

## 結論

在本篇文章中，我們探討了 Aspose.Words for Java 中文件格式化的各種面向，包括如何 **建立多層清單**、**套用段落樣式**、**設定段落對齊** 與 **設定左縮排**。掌握這些技巧後，您即可為 Java 應用程式產生專業的 Word 文件。更多深入指引，請參閱 [Aspose.Words for Java 文件](https://reference.aspose.com/words/java/)。

## 常見問與答

**Q: 如何下載 Aspose.Words for Java？**  
A: 您可從 [此連結](https://releases.aspose.com/words/java/) 下載 Aspose.Words for Java。

**Q: Aspose.Words for Java 是否適合建立複雜文件？**  
A: 當然！Aspose.Words for Java 提供廣泛功能，能輕鬆建立與格式化複雜文件。

**Q: 我可以使用 Aspose.Words for Java 為段落套用自訂樣式嗎？**  
A: 可以，您可以為段落套用自訂樣式，讓文件呈現獨特的外觀與感受。

**Q: Aspose.Words for Java 支援多層清單嗎？**  
A: 支援，Aspose.Words for Java 提供完善的多層清單建立與格式化功能。

**Q: 如何最佳化亞洲文字的段落間距？**  
A: 您可透過調整 Aspose.Words for Java 中相關設定，微調亞洲文字的段落間距。

**Q: 產生 Word 文件的最簡單方法是什麼？**  
A: 建立 `Document`，使用 `DocumentBuilder` 加入內容，最後呼叫 `save("YourFile.docx")`。

**Q: 大型文件有什麼效能建議嗎？**  
A: 使用串流 API，並及時釋放不再使用的物件，以降低記憶體使用量。

---

**最後更新：** 2026-01-09  
**測試環境：** Aspose.Words for Java 24.12（最新發行版）  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}