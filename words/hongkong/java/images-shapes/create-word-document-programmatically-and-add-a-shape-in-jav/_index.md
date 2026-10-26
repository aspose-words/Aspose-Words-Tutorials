---
category: general
date: 2026-10-26
description: 學習如何以程式方式建立 Word 文件、加入圖形，並在 Word 中隱藏物件，使用 Aspose.Words for Java – 逐步指南。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- how to hide shape
- how to add shape
- hide object in word
language: zh-hant
lastmod: 2026-10-26
og_description: 程式化建立 Word 文件，學習如何在 Word 中使用 Aspose.Words for Java 添加形狀並隱藏物件。完整、可執行的範例。
og_image_alt: Screenshot of a Word document created programmatically with a hidden
  ellipse shape
og_title: 以程式方式建立 Word 文件 – 在 Java 中新增及隱藏形狀
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to create Word document programmatically, add a shape, and
    hide object in Word using Aspose.Words for Java – step‑by‑step guide.
  headline: Create Word document programmatically and add a shape in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: 以程式方式建立 Word 文件並在 Java 中加入形狀
url: /zh-hant/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Java 中以程式方式建立 Word 文件並加入形狀

如果您需要 **以程式方式建立 Word 文件**，本教學將一步步示範如何完成、加入形狀，並在 Word 中隱藏該物件。無論您是在建構報表產生器或自動化合約系統，都能在短短幾分鐘內取得完整、可直接執行的解決方案。

您將學會：

* 使用 Aspose.Words for Java 初始化 Word 文件。  
* 透過 **how to add shape** 技術插入橢圓（或其他形狀）。  
* 隱藏該形狀，使其在開啟檔案時永不顯示，解答 **how to hide shape** 的問題。  

除了 Aspose.Words 函式庫外，無需其他外部工具，程式碼相容於 Java 17 及以上版本。

## 前置條件

開始之前，請確保您已具備：

* 已安裝 Java Development Kit (JDK) 17 或更新版本。  
* 用於管理相依性的 Maven 或 Gradle（範例使用 Maven）。  
* 有效的 Aspose.Words for Java 授權（免費評估版可用於測試）。  

若您是 Aspose.Words 新手，請參考官方的 Getting Started 指南，但不必閱讀即可跟隨本教學。

## Maven 相依性

將以下相依性加入 `pom.xml`：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

> **專業提示：** 請保持版本號為最新；較新版會修正形狀處理相關的錯誤。

## 步驟 1：以程式方式建立 Word 文件 – 初始化文件

在 **以程式方式建立 Word 文件** 時，第一步是實例化 `Document` 物件。此物件在記憶體中代表整個 .docx 檔案。

```java
import com.aspose.words.*;

public class WordShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document
        Document doc = new Document();

        // Create a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*此步驟的重要性*：`Document` 類別是所有 Word 處理操作的入口。沒有它，您無法新增頁面、段落或形狀。

## 步驟 2：how to add shape – 插入橢圓

現在說明 **how to add shape** 的部分。Aspose.Words 支援多種形狀類型（Ellipse、Rectangle、TextBox 等）。以下示範插入寬高皆為 50 點的橢圓。

```java
        // Insert an ellipse shape of size 50x50 points
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 50.0, 50.0);

        // Position the shape (optional)
        ellipse.setLeft(100);
        ellipse.setTop(100);
```

`insertShape` 方法會回傳一個 `Shape` 物件，您可以進一步自訂顏色、線條樣式、旋轉角度等。座標單位為點（1/72 英吋）。

*為何要加入形狀*：形狀可用於浮水印、裝飾元素或佔位符，之後再隱藏或取代。

## 步驟 3：how to hide shape – 使物件在 Word 中隱形

為了解答 **how to hide shape**，只需將形狀的 `Hidden` 屬性設為 `true`。這會告訴 Word 將該形狀視為隱藏物件，於文件檢視或列印時皆不會呈現。

```java
        // Hide the shape so it does not appear in the rendered document
        ellipse.setHidden(true);
```

若需 **在 Word 中隱藏物件** 給特定使用者或條件，可在執行時依業務邏輯切換此屬性。

> **注意：** 隱藏的形狀仍然是文件 XML 結構的一部份，可稍後透過 `setHidden(false)` 重新顯示。

## 步驟 4：儲存文件

完成形狀的加入與隱藏後，將文件寫入磁碟。

```java
        // Save the document as a .docx file
        doc.save("HiddenShapeDemo.docx");
        System.out.println("Document created successfully.");
    }
}
```

當您在 Microsoft Word 中開啟 `HiddenShapeDemo.docx` 時，會看到空白頁面，因為橢圓已被隱藏。文件的其他行為與普通 Word 檔案相同。

## 完整可執行範例

將所有步驟整合，以下是完整、可執行的程式碼：

```java
import com.aspose.words.*;

public class WordShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a document programmatically
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: How to add shape – insert an ellipse (50x50 points)
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 50.0, 50.0);
        ellipse.setLeft(100);
        ellipse.setTop(100);

        // Step 3: How to hide shape – hide the ellipse so it never appears
        ellipse.setHidden(true);

        // Step 4: Save the file
        doc.save("HiddenShapeDemo.docx");
        System.out.println("Document created successfully.");
    }
}
```

**預期輸出**

```
Document created successfully.
```

開啟 `HiddenShapeDemo.docx` 後會看到空白頁面；隱藏的橢圓未被渲染，證明 **在 Word 中隱藏物件** 的操作成功。

## 邊緣情況與變體

| 情境 | 需要變更的地方 | 原因 |
|-----------|----------------|-----|
| 隱藏矩形而非橢圓 | 在 `insertShape` 中使用 `ShapeType.RECTANGLE` | 不同的視覺佔位符 |
| 同時隱藏多個形狀 | 迭代 `doc.getChildNodes(NodeType.SHAPE, true)` 並呼叫 `setHidden(true)` | 批次處理時很實用 |
| 僅在列印檢視中顯示形狀 | 設定 `shape.setVisible(false)` 並 `shape.setPrint(true)` | Word 會區分螢幕與列印可見性 |
| 使用不同的測量單位 | 呼叫 `builder.getDocument().getCompatibilityOptions().setMeasureUnit(MeasureUnit.INCHES)` | 符合您的版面配置需求 |

## 常見陷阱

* **忘記呼叫 `setHidden(true)`** – 形狀會照常顯示。  
* **在隱藏形狀之前就儲存文件** – 執行順序很重要；先隱藏再儲存。  
* **使用過舊的 Aspose.Words 版本** – 舊版可能沒有 `setHidden` API。  

務必在目標版本的 Microsoft Word 中測試產生的檔案，確保隱藏狀態如預期運作。

## 結論

本指南說明了如何使用 Aspose.Words for Java **以程式方式建立 Word 文件**、**加入形狀**，以及 **在 Word 中隱藏物件**。完整範例展示了從初始化文件到儲存檔案的每一步，確保形狀永不出現在文件中。

接下來您可以：

* 嘗試其他形狀類型（`ShapeType.LINE`、`ShapeType.TEXT_BOX`）。  
* 結合隱藏形狀與書籤，打造動態範本。  
* 探索 `setVisible` 與 `setPrint` 屬性，以更細緻地控制物件可見性。

祝開發順利，盡情自動化您的 Word 文件吧！


## 接下來您應該學習什麼？

以下教學與本指南所示技術密切相關，提供完整的程式碼範例與逐步說明，協助您掌握更多 API 功能並探索其他實作方式。

- [How to create blank word document with Aspose.Words for Java](/words/english/java/document-manipulation/how-to-create-blank-word-document-with-aspose-words-for-java/)
- [How to hide shape in a Word document using Java](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}