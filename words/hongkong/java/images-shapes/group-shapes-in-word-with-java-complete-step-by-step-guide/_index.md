---
category: general
date: 2026-08-01
description: 使用 Aspose.Words 於 Java 中對 Word 進行形狀群組。了解如何快速群組形狀並插入矩形形狀，並附上完整程式碼範例。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- insert rectangle shape
- Aspose.Words Java
- shape grouping tutorial
- Word document automation
language: zh-hant
lastmod: 2026-08-01
og_description: 在 Word 中使用 Java 進行圖形分組。本指南示範如何分組圖形、插入矩形圖形，以及使用 Aspose.Words 儲存 DOCX。
og_image_alt: Screenshot of grouped shapes in a Word document created with Java
og_title: 使用 Java 在 Word 中群組圖形 – 完整程式教學
schemas:
- author: Aspose
  dateModified: '2026-08-01'
  description: Group shapes in Word with Java using Aspose.Words. Learn how to group
    shapes and insert rectangle shape quickly with a full code example.
  headline: Group Shapes in Word with Java – Complete Step-by-Step Guide
  type: TechArticle
- description: Group shapes in Word with Java using Aspose.Words. Learn how to group
    shapes and insert rectangle shape quickly with a full code example.
  name: Group Shapes in Word with Java – Complete Step-by-Step Guide
  steps:
  - name: 1. Can I group more than two shapes?
    text: 'Absolutely. Just pass a larger array to `insertGroupShape`:'
  - name: 2. What if I need to change the group’s position after creation?
    text: 'Use the group’s `setLeft` and `setTop` methods, just like any other shape:'
  - name: 3. How do I apply a border or fill to the whole group?
    text: The group itself can have formatting, but it doesn’t affect the children
      directly. If you want a common border, wrap the shapes in a rectangle shape
      first, then group everything. Alternatively, iterate over each child shape and
      set the same `fillColor` or `strokeWeight`.
  - name: 4. Does `setHidden(true)` affect printing?
    text: Hidden shapes are **not** printed by default in Word, which can be useful
      for watermarks or template markers. If you need the shape to print but stay
      invisible on screen, you’ll have to use a different approach (e.g., set its
      opacity to 0%).
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: 使用 Java 在 Word 中群組形狀 – 完整逐步指南
url: /zh-hant/java/images-shapes/group-shapes-in-word-with-java-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 中使用 Java 群組形狀 – 完整逐步指南

如果您需要使用 Java **在 Word 中群組形狀**，本指南將為您提供完整說明。無論您是在構建報告產生器或動態範本引擎，群組形狀都能讓文件看起來更精緻，並將相關圖形保持在一起。

在接下來的幾分鐘內，您將看到如何 **群組形狀** 以及如何使用 Aspose.Words **插入矩形形狀** 物件，並提供一些實用技巧，幫助您避免常見的陷阱。準備好將那些散落的矩形與橢圓整理成整齊的群組了嗎？讓我們開始吧。

## 本教學涵蓋內容

* 最小前置條件（Java 17+、Aspose.Words 24.10 或更新版本）。
* 一個完整且可執行的 Java 程式，能建立 Word 文件、插入矩形與橢圓、將它們群組、（如需）隱藏群組，並儲存檔案。
* 說明每個 API 呼叫的重要性，而不僅僅是它的功能。
* 針對較舊的 Aspose.Words 版本以及超過兩個形狀的群組情況的邊緣案例處理。
* 預期輸出以及快速驗證結果的方法。

完成後，您即可將此程式碼片段直接放入任何 Java 專案，立即開始在 Word 中群組形狀，而不必在零散的文件中搜尋。

---

## 前置條件

| Requirement | Why it matters |
|-------------|----------------|
| **Java 17+** | 現代語言功能與更佳效能。 |
| **Aspose.Words for Java 24.10+** | `setHidden` 方法僅在此版本之後才存在。 |
| **A Maven or Gradle build** | 讓相依管理變得輕鬆。 |
| **An IDE (IntelliJ, Eclipse, VS Code)** | 有助於快速測試，但任何文字編輯器皆可使用。 |

將 Aspose.Words 的 Maven 相依加入您的 `pom.xml`：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version>
</dependency>
```

如果您偏好 Gradle，等效的設定如下：

```gradle
implementation 'com.aspose:aspose-words:24.10'
```

---

## 步驟 1：建立新文件與 Builder

首先，我們建立一個空的 `Document` 與 `DocumentBuilder`。Builder 是核心工具，讓我們能插入形狀、文字等內容。

```java
// Step 1: Create a new empty document and a builder to work with it.
Document doc = new Document();                     // The container for all Word content.
DocumentBuilder builder = new DocumentBuilder(doc); // Fluent API to add elements.
```

*為何需要此步驟？*  

`Document` 代表整個 DOCX 檔案，而 `DocumentBuilder` 提供方便的游標式 API。若沒有 Builder，您必須手動操作低階節點集合，這很容易出錯。

---

## 步驟 2：插入矩形形狀（以及橢圓）

現在我們加入想要群組的兩個基本形狀。請留意 **insert rectangle shape** 呼叫——這正是您在尋找的次要關鍵字。

```java
// Step 2: Insert two simple shapes – a rectangle and an ellipse.
Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
Shape ellipseShape   = builder.insertShape(ShapeType.ELLIPSE, 100, 50);
```

需要注意的幾點：

* 寬度 (`100`) 與高度 (`50`) 以點 (pt) 為單位（1 pt ≈ 1/72 英吋）。請依版面需求調整。
* 矩形先被繪製，預設會位於橢圓之後（在底層）。若需相反順序，請先插入橢圓。
* 兩個形狀皆繼承 Builder 目前的格式設定（顏色、線條樣式）。如有需要，可在群組前自行客製化。

---

## 步驟 3：使用 Aspose.Words 群組形狀

以下是本教學的核心——**如何群組形狀**。`insertGroupShape` API 接受一個現有形狀的陣列，並回傳代表群組的新 `Shape`。

```java
// Step 3: Group the two shapes together using the InsertGroupShape API.
Shape groupShape = builder.insertGroupShape(new Shape[] { rectangleShape, ellipseShape });
```

為何要使用群組？

* 群組會作為單一單位移動，保持相對位置。
* 可一次呼叫即對整個集合套用變形（旋轉、縮放）。
* 群組化簡化後續編輯——如需調整單一元素，可再解除群組。

---

## 步驟 4（可選）：在文件檢視中隱藏群組

如果您不希望使用者在 Word 開啟文件時看到此群組，可將其隱藏。此步驟為可選，但對於背景圖形或浮水印相當實用。

```java
// Step 4: (Optional) Hide the group so it does not appear in the document view.
groupShape.setHidden(true);   // Requires Aspose.Words 24.10 or later
```

**如果您使用較舊的 Aspose.Words 版本呢？**  
`setHidden` 方法將無法編譯。此時可透過將形狀的 `WrapType` 設為 `NONE`，並將其移至文字層之後，以達成類似效果：

```java
groupShape.setWrapType(WrapType.NONE);
groupShape.getParagraph().getParagraphFormat().setStyleIdentifier(StyleIdentifier.BACKGROUND);
```

雖然稍嫌冗長，但仍能將群組隱藏於讀者視線之外。

---

## 步驟 5：儲存文件

最後，將文件寫入磁碟。將路徑改為您希望檔案存放的位置。

```java
// Step 5: Save the document with the grouped shapes.
doc.save("YOUR_DIRECTORY/GroupShapeResult.docx");
```

當您在 Microsoft Word 開啟 `GroupShapeResult.docx` 時，會看到一個矩形與橢圓整齊地被群組在一起。若設定 `setHidden(true)`，群組在編輯器中會隱形，但仍存在於檔案中（對於後續程式處理很有用）。

---

## 完整範例程式

將上述步驟整合起來，以下是完整、獨立的 Java 類別，您可以直接複製貼上至專案中：

```java
import com.aspose.words.*;

public class GroupShapeTutorial {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a builder to work with it.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert two simple shapes – a rectangle and an ellipse.
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        Shape ellipseShape   = builder.insertShape(ShapeType.ELLIPSE, 100, 50);

        // Step 3: Group the two shapes together using the InsertGroupShape API.
        Shape groupShape = builder.insertGroupShape(new Shape[] { rectangleShape, ellipseShape });

        // Step 4: (Optional) Hide the group so it does not appear in the document view.
        groupShape.setHidden(true);   // Requires Aspose.Words 24.10 or later

        // Step 5: Save the document with the grouped shapes.
        doc.save("YOUR_DIRECTORY/GroupShapeResult.docx");
    }
}
```

**預期輸出：** 產生一個名為 `GroupShapeResult.docx` 的檔案，內含一個包含藍色填滿矩形與紅色輪廓橢圓（預設顏色）的單一群組。若開啟文件、選取該群組，右鍵 → **Group → Ungroup**，即可看到兩個原始形狀重新出現。

---

## 常見問題與邊緣案例

### 1. 我可以群組超過兩個形狀嗎？

當然可以。只要將較大的陣列傳給 `insertGroupShape` 即可：

```java
Shape triangle = builder.insertShape(ShapeType.TRIANGLE, 80, 80);
Shape[] manyShapes = new Shape[] { rectangleShape, ellipseShape, triangle };
Shape bigGroup = builder.insertGroupShape(manyShapes);
```

API 會線性擴展；唯一的限制是極大群組所需的記憶體。

### 2. 若需在建立後變更群組位置該怎麼辦？

使用群組的 `setLeft` 與 `setTop` 方法，與其他形狀相同：

```java
groupShape.setLeft(150);
groupShape.setTop(200);
```

因為群組的行為如同單一形狀，所有子形狀會一起移動。

### 3. 如何為整個群組套用邊框或填色？

群組本身可以設定格式，但不會直接影響子形狀。若想要共用邊框，可先將形狀包在一個矩形形狀內，再一起群組。或者，遍歷每個子形狀，設定相同的 `fillColor` 或 `strokeWeight`。

### 4. `setHidden(true)` 會影響列印嗎？

在 Word 中，隱藏的形狀預設 **不會** 被列印，這對於浮水印或範本標記很有用。若需要形狀列印但在螢幕上保持隱形，必須採用其他方式（例如將不透明度設為 0%）。

---

## 實戰技巧

* **為形狀命名** – `groupShape.setName("HeaderGraphics");` 可在之後依名稱取得形狀時，讓除錯更容易。  
* **重複使用 Builder** – 插入群組後，Builder 的游標仍停留在群組所在位置，您可以直接在群組之後繼續加入段落，而無需重新設定位置。  
* **版本防護** – 若您的函式庫可能在較舊的 Aspose.Words 版本上執行，請將 `setHidden` 呼叫包在 `try‑catch` 捕捉 `NoSuchMethodError`，並回退至前述的 `WrapType.NONE` 作法。  
* **效能提示** – 在產生數千

## 接下來該學什麼？

以下教學涵蓋與本指南緊密相關的主題，並以此為基礎。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在專案中探索其他實作方式。

- [在 Aspose.Words for Java 中使用文件形狀](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [建立 Word 文件 Java – 添加帶陰影效果的矩形形狀](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [在 Aspose.Words for Java 中渲染形狀](/words/english/java/rendering-documents/rendering-shapes/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}