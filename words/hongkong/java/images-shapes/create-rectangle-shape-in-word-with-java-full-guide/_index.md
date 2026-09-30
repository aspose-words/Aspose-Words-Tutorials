---
category: general
date: 2026-02-10
description: 使用 Aspose.Words for Java 在 Word 文件中建立矩形形狀。了解如何設定陰影顏色、如何加入陰影，以及如何以程式方式建立
  Word 文件。
draft: false
keywords:
- create rectangle shape
- set shadow color
- create word document
- how to add shadow
- how to create shape
language: zh-hant
og_description: 使用 Aspose.Words for Java 在 Word 文件中建立矩形形狀。請按照此一步一步的教學設定陰影顏色、加入陰影，並建立
  Word 文件。
og_title: 使用 Java 在 Word 中建立矩形形狀 – 完整指南
tags:
- Aspose.Words
- Java
- Document Automation
title: 使用 Java 在 Word 中建立矩形形狀 – 完整指南
url: /zh-hant/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/
---

.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 中使用 Java 建立矩形形狀 – 完整指南

是否曾需要在 Word 文件中 **create rectangle shape**，卻不知從何開始？你並不孤單——許多開發者在首次嘗試以程式方式在 Word 中繪製圖形時都會卡住。好消息是？使用 Aspose.Words for Java，你可以在頁面上放置一個矩形，為它加上漂亮的陰影，並在幾秒鐘內儲存檔案。在本教學中，我們將逐步說明 **how to add shadow**、**set shadow color**，以及從頭 **create word document** 的完整過程。  

我們會涵蓋你需要的所有內容：必要的函式庫、每一行程式碼、為何某些設定重要，以及一些官方文件中未必提及的小技巧。完成後，你將擁有一個可直接執行的範例，能建立帶有柔和灰色陰影的矩形形狀，並儲存為 *Shadow.docx*。

## 前置條件 – 開始前你需要的東西

在深入程式碼之前，請確保你已具備以下項目：

| 需求 | 原因 |
|------|------|
| Java Development Kit (JDK) 8 或更新版本 | Aspose.Words 可在任何現代 JDK 上執行。 |
| Maven 或 Gradle（可選） | 簡化 Aspose.Words 相依性的加入。 |
| Aspose.Words for Java 授權（或免費試用） | 此函式庫為商業授權；試用版可用於測試。 |
| IDE（IntelliJ IDEA、Eclipse、VS Code 等） | 協助你快速執行與除錯範例。 |

如果你已經有 Java 專案，只需加入 Maven 坐標：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

不需要其他繁雜設定——只要一個普通的 `public static void main` 方法即可。

![建立矩形形狀範例](https://example.com/rectangle-shadow.png "在 Word 中建立帶陰影的矩形形狀")

*圖片說明：展示帶有灰色陰影的青色矩形的 create rectangle shape 範例。*

## 步驟 1 – 建立新 Word 文件

我們首先要做的是建立一個空白文件。可以把它想像成打開一個全新的 Word 檔案，之後再在上面繪圖。

```java
// Step 1: Initialize a blank Document object
Document document = new Document();
```

為什麼要從空白的 `Document` 開始？因為 Aspose.Words 把 `Document` 類別視為所有後續操作的畫布——加入段落、表格或圖形。如果跳過這一步，當你嘗試插入任何內容時就會拋出 `NullPointerException`。

## 步驟 2 – 設定 DocumentBuilder

`DocumentBuilder` 是你在 `Document` 中書寫的好幫手。它是加入內容的推薦方式，因為會自動管理游標位置。

```java
// Step 2: Create a DocumentBuilder tied to our document
DocumentBuilder builder = new DocumentBuilder(document);
```

你可能會想，‘為什麼不直接操作文件？’答案是：builder 抽象化了像是節(section)處理等底層細節，使程式碼更簡潔且不易出錯。

## 步驟 3 – 插入矩形形狀

現在是有趣的部分——**how to create shape**。我們將插入一個 100 × 50 點的矩形，並填入青色，使其可見。

```java
// Step 3: Insert a rectangle shape of size 100x50 points
Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);

// Apply a solid fill color to make the shape visible
rectangle.setFillColor(java.awt.Color.CYAN);
```

以下說明幾點：

* `ShapeType.RECTANGLE` 告訴 Aspose 我們想要矩形；你也可以改成 `OVAL`、`LINE` 等。
* 尺寸以點為單位（1 pt ≈ 1/72 英吋）。依需求調整以符合版面。
* 若未設定填色，形狀在白色頁面上會看不見——因此使用青色。

## 步驟 4 – 加入陰影並 **設定陰影顏色**

這裡說明 **how to add shadow** 的解答。`ShadowFormat` 物件控制陰影的所有視覺屬性，從顏色到模糊半徑。

```java
// Step 4: Enable the shape's shadow and configure its appearance
rectangle.getShadowFormat().setVisible(true);                     // Turn the shadow on
rectangle.getShadowFormat().setColor(java.awt.Color.GRAY);      // **set shadow color** to gray
rectangle.getShadowFormat().setBlurRadius(5.0);                  // Soft blur for realism
rectangle.getShadowFormat().setOffsetX(4.0);                     // Horizontal offset
rectangle.getShadowFormat().setOffsetY(4.0);                     // Vertical offset
rectangle.getShadowFormat().setTransparency(0.3);               // 30 % transparent
```

為什麼使用這些特定值？

* **可見性** – 若未呼叫 `setVisible(true)`，其餘設定皆會被忽略。
* **顏色** – 灰色是中性選擇，適用於亮色與暗色背景。可自行將 `java.awt.Color.GRAY` 換成任何 `java.awt.Color`。
* **模糊半徑** – `5.0` 產生柔和的羽化；較大數值會使陰影更擴散。
* **OffsetX/Y** – 偏移量使陰影向右下方移動，模擬光源來自左上角。
* **透明度** – 半透明陰影與頁面融合度更佳，特別是列印時。

若需要較銳利的效果，可將模糊半徑降至 `0` 並增加偏移量。鼓勵自行實驗——陰影屬於高度視覺化的元素，適當設定取決於文件設計。

## 步驟 5 – 儲存文件

最後，我們將所有內容寫入 `.docx` 檔案。你可以自行選擇路徑，只要確保目錄已存在即可。

```java
// Step 5: Save the document with the shaped shadow to a file
document.save("YOUR_DIRECTORY/Shadow.docx");
```

當你在 Microsoft Word 中開啟 *Shadow.docx* 時，會看到一個帶有細微灰色陰影、向右下方偏移 4 pts 的青色矩形。這就是完整的 **create word document** 工作流程。

### 預期結果

| 元素 | 外觀 |
|------|------|
| 矩形 | 青色填充，100 × 50 pt 大小 |
| 陰影 | 灰色，30 % 透明，5 pt 模糊，偏移 (4, 4) |
| 檔案 | `Shadow.docx` 儲存在你提供的路徑 |

如果形狀未顯示，請再次確認填色與頁面背景不同，且陰影已設定為可見。

## 專業技巧與常見陷阱

* **專業提示：** 若想為形狀加上邊框，可使用 `rectangle.setStrokeColor(java.awt.Color.BLACK);`。這會讓矩形在列印頁面上更突出。
* **注意：** 儲存至唯讀資料夾會拋出 `IOException`。請選擇可寫入的位置或調整檔案權限。
* **特殊情況：** 若需要透明填色（無顏色），可呼叫 `rectangle.setFillColor(java.awt.Color.WHITE); rectangle.setFillOpacity(0.0);`。形狀仍會投射陰影，適合用於浮水印式圖形。
* **效能說明：** 在迴圈中加入數百個形狀會增加記憶體使用量。請在所有形狀加入完畢後僅呼叫一次 `document.save`。

## 完整可執行範例

以下是完整程式碼，你可以直接複製貼上到名為 `ShadowDemo` 的 Java 類別中。只要 classpath 中有 Aspose.Words JAR，即可直接編譯執行。

```java
import com.aspose.words.*;

public class ShadowDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to construct the document content
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 3: Insert a rectangle shape of size 100x50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        // Apply a solid fill color to make the shape visible
        rectangle.setFillColor(java.awt.Color.CYAN);

        // Step 4: Enable the shape's shadow and configure its appearance
        rectangle.getShadowFormat().setVisible(true);
        rectangle.getShadowFormat().setColor(java.awt.Color.GRAY); // set shadow color
        rectangle.getShadowFormat().setBlurRadius(5.0);
        rectangle.getShadowFormat().setOffsetX(4.0);
        rectangle.getShadowFormat().setOffsetY(4.0);
        rectangle.getShadowFormat().setTransparency(0.3);

        // Step 5: Save the document with the shaped shadow to a file
        document.save("YOUR_DIRECTORY/Shadow.docx");
    }
}
```

執行程式，開啟產生的 *Shadow.docx*，即可看到如說明中所述的矩形與陰影。

## 如果需要更多形狀呢？

你可能會想，‘我可以多次 **create rectangle shape** 或使用其他形狀嗎？’答案是肯定的。只要將插入程式碼放入迴圈，並使用 `builder.moveTo` 或 `builder.insertParagraph` 調整座標。相同的陰影設定可以抽取成輔助方法重複使用：

```java
private static void applyStandardShadow(Shape shape) {
    shape.getShadowFormat().setVisible(true);
    shape.getShadowFormat().setColor(java.awt.Color.GRAY);
    shape.getShadowFormat().setBlurRadius(5.0);
    shape.getShadowFormat().setOffsetX(4.0);
    shape.getShadowFormat().setOffsetY(4.0);
    shape.getShadowFormat().setTransparency(0.3);
}
```

在每次插入形狀後呼叫 `applyStandardShadow(rectangle);`，以保持程式碼 DRY（不要重複自己）。

## 下一步 – 超越基礎

既然你已了解 **how to add shadow**，可以進一步探索以下相關主題：

* **How to set shadow color** 用於文字執行 – 為標題增添細微立體感。
* **Create word document** 搭配表格與影像 – 將形狀與其他內容結合。
* **How to create shape** 使用 Word 內建的動畫功能

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}