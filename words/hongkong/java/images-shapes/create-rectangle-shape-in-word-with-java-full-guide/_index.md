---
category: general
date: 2026-02-15
description: 使用 Java 在 Word 文件中建立矩形形狀。學習如何加入形狀陰影、儲存 Word 文件，以及使用 Aspose.Words 新增矩形形狀。
draft: false
keywords:
- create rectangle shape
- save word document
- how to shadow shape
- add shape shadow
- add rectangle shape
language: zh-hant
og_description: 使用 Java 在 Word 檔案中建立矩形形狀。本指南示範如何加入形狀陰影、儲存 Word 文件，以及一步一步新增矩形形狀。
og_title: 創建矩形形狀 – Java Aspose.Words 教程
tags:
- Aspose.Words
- Java
- Document Automation
title: 使用 Java 在 Word 中建立矩形形狀 – 完整指南
url: /zh-hant/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 中使用 Java 建立矩形形狀 – 完整指南

有沒有曾經需要在 Word 檔案中**建立矩形形狀**，卻不知道從哪裡開始？你並不是唯一遇到這個問題的人——許多開發者在自動化報告或發票時都會卡在這裡。好消息是？使用 Aspose.Words for Java，你可以快速產生矩形、為它加上漂亮的陰影，並只用幾行程式碼就儲存 Word 文件。

在本教學中，我們將逐步說明所有必備步驟：從初始化空白文件、設定陰影，到最後儲存檔案。完成後，你將了解**如何為形狀加陰影**、**如何加入形狀陰影**，以及**如何在任何產生的 Word 文件中加入矩形形狀**。不需要額外文件——只要純粹、可執行的程式碼。

## 前置條件

- Java 8 或更新版本（API 亦支援 Java 11 以上）。  
- Aspose.Words for Java 函式庫（版本 23.9 或更新）。  
- 如 IntelliJ IDEA 或 Eclipse 等 IDE——皆可。  
- 具備基本的 Java 語法知識。

> **專業提示：** 若使用 Maven，請將 Aspose.Words 相依性加入 `pom.xml`，其餘交給 IDE 處理。

---

## 第一步：初始化新文件 – 如何 **建立矩形形狀**  

首先，你需要一個乾淨的畫布。在 Aspose.Words 中，這個畫布就是 `Document` 物件。

```java
import com.aspose.words.*;

public class ShadowShapeExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();
```

`Document` 類別代表整個 .docx 檔案。可以把它想像成筆記本，之後你會在其中**加入矩形形狀**及其陰影。

## 第二步：建立矩形 – **加入矩形形狀**  

現在我們實際建構矩形，並設定其尺寸、版面配置與填色。

```java
        // Step 2: Create a rectangle shape and set its size and layout
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(200);
        rectangleShape.setHeight(100);
        rectangleShape.setWrapType(WrapType.INLINE);
        rectangleShape.setFillColor(java.awt.Color.LIGHT_GRAY);
```

為什麼使用 `INLINE` 包裝？因為我們希望形狀的行為像段落——非常適合簡單報告。若之後需要文字繞排形狀，可改為 `TOPBOTTOM`。

## 第三步：套用陰影 – **如何為形狀加陰影**  

單純的矩形看起來有點單調。加入陰影可增添立體感，使文件更顯精緻。這正是我們實作“**如何為形狀加陰影**”的地方。

```java
        // Step 3: Configure the shape's shadow appearance
        rectangleShape.getShadowFormat().setVisible(true);
        rectangleShape.getShadowFormat().setColor(java.awt.Color.DARK_GRAY);
        rectangleShape.getShadowFormat().setBlurRadius(5.0);
        rectangleShape.getShadowFormat().setOffsetX(4.0);
        rectangleShape.getShadowFormat().setOffsetY(4.0);
        rectangleShape.getShadowFormat().setTransparency(0.3);
```

每個屬性都有其特定功能：

- `setVisible(true)` 開啟陰影。  
- `setColor` 選擇深灰色以呈現細膩效果。  
- `setBlurRadius` 控制邊緣的柔和程度。  
- `setOffsetX/Y` 將陰影向右與向下移動，模擬光源。  
- `setTransparency` 讓陰影略帶透明，使形狀仍為焦點。

> **注意：** 若需要彩色陰影，只要將不同的 `java.awt.Color` 傳入 `setColor` 即可。

## 第四步：將形狀插入文件  

矩形及其陰影準備好後，我們將它插入文件的第一個節中。

```java
        // Step 4: Add the shape to the first section of the document
        document.getFirstSection().getBody().appendChild(rectangleShape);
```

將其附加至 body 會把形狀放在新段落的位置。若想將矩形放在特定位置，可使用 `insertBefore` 或操作 `Paragraph` 集合。

## 第五步：**儲存 Word 文件** – 永久保存你的工作  

最後一步是將檔案寫入磁碟。這就是實際**儲存 Word 文件**的時刻。

```java
        // Step 5: Save the document with the shadowed shape
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

將 `YOUR_DIRECTORY` 替換為你機器上的絕對或相對路徑。執行程式後，於 Microsoft Word 開啟 `ShadowShape.docx`——你應該會看到一個淡灰色矩形，帶有柔和的深色陰影。

![使用 Aspose.Words 建立的帶陰影矩形形狀示意圖](https://example.com/rectangle-shadow.png "建立帶陰影的矩形形狀")

---

## 常見問題與邊緣情況  

### 如果需要多個矩形該怎麼辦？

只需在迴圈中重複 **第 2 步** 與 **第 3 步**，每次調整 `setWidth`、`setHeight` 或 `setFillColor`。記得為每個形狀使用唯一的變數名稱，或將它們存入清單中。

### 能否匯出為 PDF 而非 DOCX？

當然可以。形狀加入後，呼叫 `document.save("output.pdf")`。Aspose.Words 會處理轉換，並保留陰影效果。

### 舊版 Word 呢？

使用 `document.save("file.doc", SaveFormat.DOC)` 的重載方法。API 會自動降級功能，但需注意某些陰影樣式在舊版格式中可能略有差異。

### 如何變更陰影方向？

調整 `setOffsetX` 與 `setOffsetY`。正值 X 使陰影向右移動，負值則向左；正值 Y 使陰影向下，負值則向上。透過這些數值即可模擬任意角度的光源。

---

## 使用形狀的技巧  

- **群組形狀**：若需要在矩形旁加標籤，可建立 `GroupShape`，並將矩形與 `TextBox` 皆加入其中。  
- **Z‑順序很重要**：使用 `shape.moveToFront()` 或 `shape.moveToBack()` 來控制哪個形狀位於上層。  
- **效能**：加入數百個形狀可能較慢。將它們批次放入同一節，最後一次呼叫 `document.updatePageLayout()`。

---

## 重點回顧  

我們已說明如何使用 Java 在 Word 文件中**建立矩形形狀**、如何**加入形狀陰影**，以及如何**儲存 Word 文件**。完整、可執行的程式碼位於上述程式碼片段，你也了解每個屬性的「為什麼」——因此可以依需求調整顏色、模糊度與偏移量，以符合任何設計。

準備好接受下一個挑戰了嗎？試著將矩形與圖表結合，或將檔案匯出為 PDF，觀察陰影的呈現。你也可以探索在表格內**加入矩形形狀**，以打造精美的報告版面。

祝程式開發愉快，願你的文件永遠如程式碼般銳利！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}