---
category: general
date: 2026-07-03
description: 在 Java 中建立矩形形狀，學習如何為形狀添加陰影、套用陰影效果、設定形狀透明度，並快速建立空白文件。
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- apply shadow effect
- set shape transparency
- create blank document
language: zh-hant
og_description: 在 Java 中建立帶有陰影、透明度的矩形形狀及空白文件。跟隨本指南，精通形狀處理。
og_title: 在 Java 中建立矩形形狀 – 完整程式設計教學
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  headline: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  name: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  steps:
  - name: What if I want a different shadow color?
    text: 'Simply change the `setColor` call:'
  - name: Can I apply the same shadow to multiple shapes?
    text: 'Yes. Create one `ShadowEffect` instance, configure it, then reuse it:'
  - name: How do I change the shadow blur dynamically?
    text: Expose a UI slider that maps to `setBlurRadius`. Values between `2` and
      `12` are typical; larger numbers produce a “glow” rather than a crisp shadow.
  - name: What if I need the shape to float rather than be inline?
    text: 'Swap the wrap type:'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Automation
title: 在 Java 中建立矩形形狀 – 完整逐步指南
url: /zh-hant/java/images-shapes/create-rectangle-shape-in-java-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Java 中建立矩形形狀 – 完整步驟指南

有沒有想過要 **在 Word 文件中使用 Java 建立矩形形狀**？你並不是唯一有此需求的人——開發者常常需要快速加入幾何圖形，並為其加上細緻的陰影，使版面看起來更精緻。在本教學中，我們將一步步說明：從 **建立空白文件** 到 **為形狀加入陰影**、**套用陰影效果**，甚至 **設定形狀透明度**，讓你的文件看起來更專業。

以下程式碼片段是一個完整可執行的範例，你只要直接複製貼上到專案中即可。無需額外文件說明——跟著步驟走，了解「為什麼」這樣寫，你就能在幾秒鐘內產生帶陰影的矩形。

## 你將學到

- 如何以 Aspose.Words for Java 程式化 **建立矩形形狀**。
- 完整的呼叫方式，**為形狀加入陰影** 並設定視覺屬性。
- **套用陰影效果** 以及調整偏移、模糊半徑與顏色等參數的方法。
- **設定形狀透明度** 的技巧，讓外觀更柔和。
- 如何 **建立空白文件**、插入形狀，並儲存結果。

> **專業小技巧：** 以上所有操作皆在同一個 `Document` 實例上完成，這意味著你可以串接這些動作，而不必擔心中間的檔案 I/O。

## 前置條件

在開始之前，請確保你已具備：

- 已安裝 Java 17（或任何較新的 JDK）。
- 已將 Aspose.Words for Java 套件加入專案（Maven 坐標：`com.aspose:aspose-words:23.12`）。
- 一個 Java IDE 或簡易文字編輯器——不需要特別花俏，只要能編譯與執行即可。

如果缺少上述任一項，請從 Oracle 下載 JDK，並透過 Maven 或 Gradle 取得 Aspose 相依套件。完成設定後，即可開始動手。

## 步驟 1：**建立空白文件** – 所有工作的畫布

首先，你需要一個空的 `Document` 物件。把它想像成一張全新的紙張；沒有它，就無法放置矩形。

```java
// Step 1: Create a new blank document
Document document = new Document();
```

為什麼要先建立空白文件？因為每個形狀都必須位於 `Section` 之中，而新建的 `Document` 已經自動包含一個預設的 Section，且其 Body 已準備好接受節點。若跳過此步，之後必須手動建立 Section，會增加不必要的複雜度。

## 步驟 2：**建立矩形形狀** 並定義尺寸

現在有了畫布，讓我們 **建立矩形形狀**。`Shape` 類別需要傳入文件參考與 `ShapeType`。此處選擇 `RECTANGLE`，並以點 (pt) 為單位設定寬高（1 pt ≈ 1/72 英吋）。

```java
// Step 2: Insert a rectangle shape and define its size and layout
Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
rectangleShape.setWidth(200);   // 200 pt ≈ 2.78 inches
rectangleShape.setHeight(100);  // 100 pt ≈ 1.39 inches
rectangleShape.setWrapType(WrapType.INLINE);
```

為什麼要設定 `WrapType.INLINE`？內聯換行讓形狀在段落中行為如同字元，確保它會隨周圍文字一起移動。如果需要浮動效果，可改用 `WrapType.SQUARE` 或 `WrapType.TOP_BOTTOM`。

## 步驟 3：**套用陰影效果** – 為矩形增添深度

平面的矩形看起來…嗯，真的很平。加入陰影即可讓它更突出。我們將 **套用陰影效果**，方法是建立 `ShadowEffect` 實例，然後調整其視覺屬性。

```java
// Step 3: Create a shadow effect and configure its visual properties
ShadowEffect shadowEffect = new ShadowEffect();
shadowEffect.setColor(Color.getGray(0.5));   // medium gray
shadowEffect.setOffsetX(5);                  // horizontal offset (points)
shadowEffect.setOffsetY(5);                  // vertical offset (points)
shadowEffect.setBlurRadius(8);               // softness of the shadow
shadowEffect.setTransparency(0.3);           // 30 % transparent
```

讓我們逐項說明：

- **Color** – `Color.getGray(0.5)` 產生 50 % 灰色，屬中性且適用於大多數背景。
- **OffsetX/Y** – 正值會將陰影向右與向下推移；負值則相反。
- **BlurRadius** – 數值越大，陰影越柔和、擴散。
- **Transparency** – 範圍從 `0`（不透明）到 `1`（全透明）。此處使用 `0.3`，呈現細緻的效果。

## 步驟 4：**為形狀加入陰影** – 綁定效果

僅建立效果還不夠，我們必須 **為形狀加入陰影**，將 `ShadowEffect` 物件指派給矩形。

```java
// Step 4: Apply the shadow effect to the rectangle shape
rectangleShape.setShadowEffect(shadowEffect);
```

在背後，這個呼叫會更新 Word 用來渲染陰影的 OpenXML 標記（`<w:shdw>`）。若檢視儲存的 `.docx`，會看到 `<w:effect>` 元素已填入我們設定的參數。

## 步驟 5：**設定形狀透明度** – 可選但常用

有時你希望矩形本身半透明，讓底下的文字仍可透視。`Shape` 類別提供 `setFillColor` 與 `setFillTransparency`。以下範例將矩形設定為 40 % 透明：

```java
// Optional: make the rectangle partially transparent
rectangleShape.setFillColor(Color.getWhite());
rectangleShape.setFillTransparency(0.4); // 40 % transparent
```

為什麼會這樣做？想像水印或突顯的說明框，需要保留底層內容的可讀性。依設計需求自行調整透明度數值即可。

## 步驟 6：將形狀插入文件

我們已建立矩形、加入陰影，且（可選）設定透明度。最後一步是 **將形狀加入文件的第一個 Section**。

```java
// Step 5: Add the shape to the first section of the document
document.getFirstSection().getBody().appendChild(rectangleShape);
```

把形狀附加到 Body 後，會放在第一段落的結尾。如果需要特定插入位置，可取得目標 `Paragraph`，再使用 `insertBefore` 或 `insertAfter`。

## 步驟 7：儲存文件 – 查看結果

所有工作最終只需一次 `save` 呼叫。請依你的環境選擇合適的路徑。

```java
// Step 6: Save the document with the shadowed shape
document.save("YOUR_DIRECTORY/ShadowShape.docx");
```

開啟產生的 `ShadowShape.docx`（使用 Microsoft Word 或 LibreOffice），即可看到一個帶有柔和灰色陰影、若執行了可選步驟則略帶透明的清晰矩形。視覺效果正是我們程式化設定的參數所呈現。

---

![create rectangle shape with shadow in a Word document](https://example.com/images/rectangle-shadow.png "create rectangle shape with shadow")

*圖片替代文字:* **create rectangle shape with shadow** – 最終輸出的視覺示意。

## 常見問題與邊緣情況

### 想換成不同的陰影顏色？

只要修改 `setColor` 呼叫即可：

```java
shadowEffect.setColor(Color.getRed()); // bright red shadow
```

請記得，過於鮮豔的陰影會顯得不專業；通常使用低調色調較佳。

### 可以把同一個陰影套用到多個形狀嗎？

可以。先建立一個 `ShadowEffect` 實例，完成設定後重複使用：

```java
Shape circle = new Shape(document, ShapeType.OVAL);
circle.setShadowEffect(shadowEffect); // same effect as rectangle
```

只要在將 `ShadowEffect` 附加給其他形狀之後，不再變更該實例，即可避免所有已套用的形狀同時改變，除非你真的想同步更新。

### 如何動態調整陰影模糊程度？

在 UI 中加入滑桿，對應 `setBlurRadius`。常見範圍為 `2`~`12`；數值過大會產生「發光」而非清晰陰影。

### 若需要形狀浮動而非內聯，該怎麼做？

切換換行類型：

```java
rectangleShape.setWrapType(WrapType.SQUARE);
rectangleShape.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangleShape.setHorizontalAlignment(HorizontalAlignment.CENTER);
```

浮動形狀提供更大的版面配置自由度，但也需要額外的定位邏輯。

## 完整範例程式

以下提供完整、可直接複製貼上的程式碼，已整合所有前述步驟。以普通 Java 應用程式執行即可。

```java
import com.aspose.words.*;

public class ShadowRectangleDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank document
        Document document = new Document();

        // 2. Build the rectangle shape
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(200);
        rectangleShape.setHeight(100);
        rectangleShape.setWrapType(WrapType.INLINE);

        // 3. Configure shadow effect
        ShadowEffect shadowEffect = new ShadowEffect();
        shadowEffect.setColor(Color.getGray(0.5));
        shadowEffect.setOffsetX(5);
        shadowEffect.setOffsetY(5);
        shadowEffect.setBlurRadius(8);
        shadowEffect.setTransparency(0.3);

        // 4. Apply shadow to the rectangle
        rectangleShape.setShadowEffect(shadowEffect);

        // 5. (Optional) Make rectangle semi‑transparent
        rectangleShape.setFillColor(Color.getWhite());
        rectangleShape.setFillTransparency(0.4);

        // 6. Insert shape into the document
        document.getFirstSection().getBody().appendChild(rectangleShape);

        // 7. Save the file
        document.save("ShadowShape.docx");
    }
}
```

**預期結果：** 開啟 `ShadowShape.docx` 後，你會看到一個白色矩形（200 × 100 pt），置於第一段落置中，陰影為中灰色、水平與垂直偏移 5 pt、模糊半徑 8，透明度 30 %。矩形本身透明度為 40 %，底層文字得以透視。

## 小結

我們已從頭 **建立矩形形狀**、**為形狀加入陰影**、**套用陰影效果**，甚至 **設定形狀透明度**，同時以 **建立空白文件** 為基礎。此流程簡潔、依賴 Aspose.Words 流暢的 API，且可延伸至圓形、星形或自訂多邊形。

接下來的路線圖是什麼？試著把 `ShapeType.RECTANGLE` 換成 `ShapeType.OVAL`，產生帶陰影的圓形，或是實驗漸層填色…

## 接下來該學什麼？

以下教學與本篇內容緊密相關，能進一步深化你對 API 的掌握，並提供其他實作方式供你在專案中參考。

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}