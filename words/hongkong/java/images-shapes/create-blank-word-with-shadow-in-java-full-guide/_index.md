---
category: general
date: 2026-05-04
description: 在 Java 中建立空白 Word 文件，學習如何設定形狀的陰影顏色、模糊度與偏移量 – 快速教學。
draft: false
keywords:
- create blank word
- set shadow color
- how to add shadow
- how to set blur
- how to set offset
language: zh-hant
og_description: 在 Java 中建立空白 Word 文件，並學習如何為形狀設定陰影顏色、模糊與偏移。跟隨此一步一步的教學。
og_title: 在 Java 中創建帶陰影的空白文字 – 完整指南
tags:
- Aspose.Words
- Java
- Document Automation
title: 在 Java 中創建帶陰影的空白文字 – 完整指南
url: /zh-hant/java/images-shapes/create-blank-word-with-shadow-in-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Java 中建立空白 Word 並加上陰影 – 完整指南

有沒有需要 **create blank word** 檔案的時候，想讓它看起來更有質感？你並不是唯一有這個需求的人。在許多報表或範本產生的專案中，第一件事往往就是產生一個空的 Word 文件，然後再加入帶陰影的圖形，讓文件更具專業感。  

在本教學中，我們將一步步說明如何使用 Aspose.Words for Java **create blank word**，**how to add shadow** 到圖形，以及 **set shadow color**、**how to set blur**、**how to set offset** 的細節。完成後，你會得到一個可直接使用的 `.docx` 檔案，裡面展示了一個帶有柔和半透明紅色陰影的矩形。

## 需要的環境

- **Aspose.Words for Java**（任意近期版本；程式碼在 23.9 以上皆可執行）
- JDK 8 或更新版本
- IDE 或簡易文字編輯器加上終端機
- 基本的 Java 知識——只要能執行 `main` 方法即可

示範不需要額外的 Maven 或 Gradle 設定，只要把 Aspose JAR 放到 classpath 中即可使用。

---

![create blank word document with shadow example](image-placeholder.png){: .center alt="建立帶陰影的空白 Word 文件範例"}

## Create blank word – 初始化 Document

第一步是建立一個全新的、空的 Word 檔案。把它想像成一張白紙，之後可以在上面繪製圖形、表格或文字。

```java
import com.aspose.words.*;

public class ShadowDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank Word document
        Document document = new Document();

        // Step 2: Initialise a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(document);
```

> **為什麼這很重要：** `Document` 代表整個 `.docx` 套件。使用預設建構子建立它，即等同於 **create blank word** —— 沒有內容、沒有段落，只有檔案結構等你填入。

## How to add shadow to a shape

現在文件已經乾淨，我們來插入一個矩形，作為陰影的載體。視覺效果就從這裡開始。

```java
        // Step 3: Insert a rectangle shape that will receive a custom shadow
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
```

> **小技巧：** `insertShape` 會自動把圖形加入目前段落，所以除非需要絕對定位，否則不必手動處理位置。

## Set shadow color – 讓陰影更突出

沒有顏色的陰影只是一團灰色模糊，會顯得平淡。設定陰影顏色即可配合品牌或讓它更顯眼。

```java
        // Step 4a: Make the shadow visible and set its color
        rectangleShape.getShadowFormat().setVisible(true);
        rectangleShape.getShadowFormat().setColor(java.awt.Color.RED); // set shadow color
```

> **發生了什麼：** `ShadowFormat` 控制陰影的所有視覺屬性。啟用 `setVisible(true)` 會開啟效果，而 `setColor` 讓你挑選任意 `java.awt.Color`。範例中我們選擇紅色，以清楚示範 **set shadow color**。

## How to set blur for a subtle effect

銳利、硬邊的陰影會顯得刺眼。加入模糊可以柔化邊緣，讓外觀更自然。

```java
        // Step 4b: Define how fuzzy the shadow should be
        rectangleShape.getShadowFormat().setBlur(5.0); // how to set blur
```

> **為什麼模糊重要：** `setBlur` 的數值以點 (point) 為單位。`5.0` 會產生柔和的擴散；數值越大陰影越模糊，數值越小則輪廓越銳利。

## How to set offset – 定位陰影

Offset 決定陰影相對於圖形的落點。把它想成 X 與 Y 的位移。

```java
        // Step 4c: Position the shadow horizontally and vertically
        rectangleShape.getShadowFormat().setOffsetX(8.0); // how to set offset (horizontal)
        rectangleShape.getShadowFormat().setOffsetY(8.0); // how to set offset (vertical)
```

> **Offset 說明：** 正值 X 會讓陰影向右移，正值 Y 會向下移。若想讓陰影出現在相反方向，可使用負數。

## 微調透明度

如果想讓陰影不那麼搶眼，可以調整透明度。這一步不是關鍵字需求，但能讓視覺控制更完整。

```java
        // Optional: Make the shadow semi‑transparent (30 % transparent)
        rectangleShape.getShadowFormat().setTransparency(0.3);
```

## Saving the document – 看看結果

最後，把文件寫入磁碟。你會得到一個 `.docx`，可在 Word、LibreOffice 或任何支援該格式的檢視器中開啟。

```java
        // Step 5: Save the document with the shaped shadow
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

> **你會看到什麼：** 開啟 `ShadowShape.docx`。單頁會顯示一個 150 × 80 pt 的矩形，帶有紅色、稍微模糊且向右下偏移 8 pt 的陰影。陰影透明度為 30%，因此矩形仍然清晰可見。

---

## 常見問題與邊緣情況

### 如果需要其他形狀該怎麼辦？

將 `ShapeType.RECTANGLE` 換成其他列舉值（`ELLIPSE`、`CLOUD`、`CALLOUT` 等）。陰影設定在所有形狀上皆相同。

### 能否將相同的陰影套用到多個圖形而不重複程式碼？

當然可以。建立一個輔助方法：

```java
private static void applyShadow(Shape shape, java.awt.Color color,
                                double blur, double offsetX, double offsetY,
                                double transparency) {
    shape.getShadowFormat().setVisible(true);
    shape.getShadowFormat().setColor(color);
    shape.getShadowFormat().setBlur(blur);
    shape.getShadowFormat().setOffsetX(offsetX);
    shape.getShadowFormat().setOffsetY(offsetY);
    shape.getShadowFormat().setTransparency(transparency);
}
```

然後對任何圖形呼叫 `applyShadow(rectangleShape, Color.RED, 5.0, 8.0, 8.0, 0.3);`。

### 這在較舊的 Aspose 版本上可用嗎？

`ShadowFormat` API 從 19.8 版起就穩定了，對大多數近期版本都適用。若使用非常舊的版本，請查閱 `ShadowFormat` 的 Javadoc 以確認方法名稱。

### 如何在匯出 PDF 時保留陰影？

在建立圖形後，直接呼叫 `document.save("output.pdf");`。Aspose.Words 會正確在 PDF 中呈現陰影，保留模糊與透明度。

---

## Recap – create blank word with a custom shadow

我們先使用 `new Document()` **create blank word**，接著插入矩形、**set shadow color**，學會 **how to add shadow**，調整 **how to set blur**，最後透過 **how to set offset** 把陰影定位得恰到好處。完整、可執行的程式碼已在上方程式碼片段中示範，產生的檔案清楚展示了效果。

---

## 接下來可以做什麼？

- **嘗試其他陰影屬性**，如 `ShadowFormat.setStyle(ShadowStyle.OUTER)`，取得不同的視覺風格。
- **結合多個圖形**，每個都帶有自己的陰影，打造複雜圖表。
- **在圖形內加入文字**，使用 `builder.insertHtml("<b>Hello</b>")` 於插入圖形前，然後套用相同的陰影邏輯。
- **探索其他格式設定**，例如線條樣式、填色或漸層填色——Aspose.Words 為這些提供了豐富的 API。

隨意調整模糊半徑、位移或顏色，直到陰影與文件的設計語言完美契合。祝開發順利，讓你的產生的 Word 文件更顯精緻！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}