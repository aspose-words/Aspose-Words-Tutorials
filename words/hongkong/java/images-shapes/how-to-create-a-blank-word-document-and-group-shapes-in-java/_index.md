---
category: general
date: 2026-09-24
description: 學習如何在 Java 中使用 Aspose.Words 建立空白 Word 文件，並將矩形、線條等圖形進行群組。包含逐步程式碼。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shapes
- add rectangle shape
- group shapes in word
- set shape size
language: zh-hant
lastmod: 2026-09-24
og_description: 在 Java 中建立空白 Word 文件，學習如何將圖形分組、加入矩形圖形，並使用 Aspose.Words 設定圖形大小。
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: 在 Java 中建立空白 Word 文件並將圖形分組 – 步驟指南
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Learn how to create a blank Word document in Java and group shapes
    like rectangles and lines using Aspose.Words. Includes step‑by‑step code.
  headline: How to create a blank Word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: 如何在 Java 中建立空白 Word 文件並將圖形分組
url: /zh-hant/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Java 中建立空白 Word 文件並將圖形分組

如果您需要 **建立空白 Word 文件**，然後整理多個繪圖物件，本指南會精確說明操作步驟。使用 Aspose.Words for Java，您可以插入群組圖形、加入矩形圖形、繪製直線，並控制每個圖形的大小與位置——全部在一個可執行的程式中。

您將逐步完成從初始化文件到儲存最終 `.docx` 的每個步驟。完成後，您將了解 **如何分組圖形**、**加入矩形圖形** 以及 **設定圖形大小**，讓您的 Word 檔案呈現如預期的樣子。

## 前置條件

- Java 17 或更新版本（程式碼可在任何近期的 JDK 上編譯）
- Aspose.Words for Java 函式庫（從 [Aspose website](https://products.aspose.com/words/java) 下載）
- 可加入 Aspose.Words JAR 至 classpath 的 IDE 或建置工具（Maven/Gradle）
- 基本的 Java 語法知識

> **專業提示：** 使用 Maven 進行相依管理；在 `pom.xml` 中加入 `com.aspose:aspose-words:23.12`（或最新版本）。

## 步驟 1：建立空白 Word 文件

第一個任務是 **建立空白 Word 文件**。這會提供一個乾淨的畫布，之後您可以在上面插入圖形。

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document
        Document document = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(document);
```

*為什麼這很重要：* `Document` 物件代表整個 `.docx` 檔案。從空白文件開始可確保沒有隱藏的格式會干擾您之後加入的圖形。

## 步驟 2：插入群組圖形 – 多個物件的容器

**群組圖形** 像是一個容器，讓您一次移動、調整大小或旋轉多個圖形。這就是在 Word 中 **如何分組圖形** 的核心。

```java
        // Insert a group shape of width 300 points and height 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

*說明：* `insertGroupShape` 方法會建立一個 `GroupShape` 物件，並將其放置於目前游標位置。所有之後 `appendChild` 到此群組的圖形都會被視為單一單元。

## 步驟 3：加入矩形圖形並設定其大小

現在我們 **加入矩形圖形** 到群組，並精確 **設定圖形大小**。

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);   // set shape width
        rectangle.setHeight(100.0);  // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Add the rectangle to the group
        group.appendChild(rectangle);
```

*為什麼需要設定圖形大小：* 寬度與高度決定矩形在頁面上的顯示方式。`setLeft` 與 `setTop` 方法會相對於群組的原點定位矩形，讓您得到像素級的版面控制。

## 步驟 4：加入直線圖形並設定其尺寸

直線是另一種常見的繪圖物件。我們會將 **類似加入矩形圖形** 的邏輯套用於直線，示範相同的尺寸原則亦適用。

```java
        // Create a line shape
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);   // line length
        line.setHeight(0.0);    // height is zero for a horizontal line
        line.setLeft(20.0);
        line.setTop(130.0);

        // Add the line to the same group
        group.appendChild(line);
```

*重點：* 雖然直線沒有高度，仍需使用 `setWidth` 來定義其長度。定位（`setLeft`、`setTop`）遵循與其他圖形相同的座標系統。

## 步驟 5：儲存含有群組圖形的文件

最後，透過儲存文件來永久保存變更。這會產生一個 `.docx` 檔案，您可以在 Microsoft Word 中開啟以驗證結果。

```java
        // Save the document to disk
        document.save("GroupShapeDemo.docx");
    }
}
```

**預期輸出：** 開啟 `GroupShapeDemo.docx` 後會看到一個空白頁面，內含已群組的矩形與直線。選取任一圖形即會選取整個群組，讓您一起移動它們。

## 常見問題與邊緣案例處理

| Question | Answer |
|----------|--------|
| *我可以在群組中加入超過兩個圖形嗎？* | 可以。對每個額外的圖形呼叫 `group.appendChild(yourShape)`。 |
| *如果我需要使用不同的單位（例如公分）來設定大小，該怎麼辦？* | Aspose.Words 使用點 (point) 作為單位（1 point = 1/72 英吋）。可使用 `Points = centimeters * 28.3465` 進行換算。 |
| *在其他電腦開啟文件時，群組會保留其版面配置嗎？* | 絕對會。所有大小與位置資料皆儲存在 `.docx` 檔案中，使版面配置可攜帶。 |
| *之後要如何取消群組圖形？* | 取得 `GroupShape` 物件，然後遍歷 `group.getChildNodes(NodeType.SHAPE, true)`，將每個子圖形移出群組。 |
| *如果需要旋轉整個群組該怎麼辦？* | 在儲存前使用 `group.setRotationAngle(double angleInDegrees)`。 |

## 完整、可執行範例

以下是完整的程式碼，您可以直接複製貼上到 IDE 中。它包含所有必要的匯入與註解。

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape (container)
        GroupShape group = builder.insertGroupShape(300.0, 200.0);

        // Step 3: Add a rectangle shape and set its size
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);
        rectangle.setHeight(100.0);
        rectangle.setLeft(20.0);
        rectangle.setTop(20.0);
        group.appendChild(rectangle);

        // Step 4: Add a line shape and configure its dimensions
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);
        line.setHeight(0.0);
        line.setLeft(20.0);
        line.setTop(130.0);
        group.appendChild(line);

        // Step 5: Save the document with the grouped shapes
        document.save("GroupShapeDemo.docx");
    }
}
```

執行程式後，於 Microsoft Word 開啟 `GroupShapeDemo.docx`，即可看到如說明中所示的群組圖形。

## 結論

您現在已了解如何使用 Aspose.Words for Java **建立空白 Word 文件**、**在 Word 中分組圖形**、**加入矩形圖形**，以及 **設定圖形大小**。將圖形放入 `GroupShape` 後，您即可完整掌控整體的定位、縮放與旋轉——非常適合用於圖表、流程圖或嵌入自動化報告的自訂圖形。

**下一步：**  
- 探索 **如何分組圖形** 與更複雜的物件（如圖片或文字方塊）。  
- 嘗試使用 `setRotationAngle` 來旋轉整個群組。  
- 將此技巧與合併列印結合，產生包含品牌圖形的個人化文件。

歡迎將程式碼套用到您自己的專案，並在留言區分享您的成果！

## 接下來您可以學習什麼？

以下教學涵蓋與本指南技術密切相關的主題。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在自己的專案中探索替代實作方式。

- [在 Word 中使用 Java 建立矩形圖形 – 完整指南](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [使用 Java 建立 Word 文件 – 加入帶陰影效果的矩形圖形](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [使用 Aspose.Words for .NET 在 Word 文件中建立群組圖形](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}