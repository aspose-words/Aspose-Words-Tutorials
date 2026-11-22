---
category: general
date: 2026-11-22
description: 使用 Java 在 Word 文件中新增矩形形狀，設定形狀大小，將多個形狀分組，並有效率地將形狀加入群組。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add rectangle shape
- set shape size
- group multiple shapes
- set shape dimensions
- append shape to group
language: zh-hant
lastmod: 2026-11-22
og_description: 使用 Java 在 Word 文件中新增矩形形狀，然後設定形狀大小、將多個形狀群組，並在單一工作流程中將形狀加入群組。
og_image_alt: Screenshot showing a rectangle shape added and grouped in a Word document
  using Java
og_title: 在 Java 中加入矩形形狀與群組形狀 – 完整指南
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  headline: Add rectangle shape and group shapes in Java
  type: TechArticle
- description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  name: Add rectangle shape and group shapes in Java
  steps:
  - name: Insert the rectangle shape
    text: The rectangle is the first visual element we want to place inside the document.
      By using the `Shape` constructor with `ShapeType.RECTANGLE`, you get a fully
      editable object.
  - name: Set shape size and dimensions
    text: Set shape size and dimensions
  - name: Create a group shape container
    text: '```java // Step 6: Create a group shape that will hold the rectangle and
      other shapes GroupShape groupShape = builder.insertGroupShape(); ```'
  - name: Append shape to group
    text: Append shape to group
  - name: Save the document
    text: '```java // Save the result to a new file doc.save("output.docx"); } } ```'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shape manipulation
title: 在 Java 中新增矩形形狀與群組形狀
url: /zh-hant/java/images-shapes/add-rectangle-shape-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Java 中新增矩形形狀並將形狀分組

如果您需要 **在 Word 文件中新增矩形形狀**，本指南將一步步帶您完成。您還會學會如何 **設定形狀大小**、**將多個形狀分組**，以及 **將形狀加入群組**，全程不離開 IDE。

在 DOCX 檔案內操作向量圖形常常感覺像在同時使用多個 API。完成本教學後，您將擁有一個完整、獨立的程式，能建立矩形、橢圓以及任何其他所需形狀，並將它們分組，使其作為單一物件移動。除了 Aspose.Words for Java，無需其他外部工具。

## 前置條件

開始之前，請確保您已具備：

* 已安裝 Java 17 或更新版本。
* Maven 3.8+（或 Gradle）以管理相依性。
* 有效的 Aspose.Words for Java 授權（評估版可用於測試）。
* 如 IntelliJ IDEA 或 VS Code 等 IDE，任何文字編輯器亦可。

上述條件可確保程式碼在任何現代開發環境中編譯與執行。

## 第一步：建立 Maven 專案

建立新的 Maven 專案，或在現有的 `pom.xml` 中加入 Aspose.Words 相依性：

```xml
<project>
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.example</groupId>
  <artifactId>shape‑demo</artifactId>
  <version>1.0.0</version>

  <dependencies>
    <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.12</version>
    </dependency>
  </dependencies>
</project>
```

此相依性會自動下載所有文件操作所需的類別，包括 `Document`、`DocumentBuilder`、`Shape` 與 `GroupShape`。執行 `mvn compile` 時，Maven 會自動取得相關 JAR。

## 第二步：載入文件並建立 DocumentBuilder

`DocumentBuilder` 提供流暢的 API 以插入內容。載入既有 DOCX 或從空白文件開始：

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document or create a new one
        Document doc = new Document("input.docx");          // replace with your path
        DocumentBuilder builder = new DocumentBuilder(doc);
```

提前建立 Builder 可讓游標定位於文件開頭，隨時準備插入形狀。

## 在 Word 文件中新增矩形形狀

### 第三步：插入矩形形狀

矩形是我們要放入文件的第一個視覺元素。使用 `Shape` 建構子搭配 `ShapeType.RECTANGLE`，即可取得可完整編輯的物件。

```java
        // Step 3: Insert a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        // The shape is not yet sized; we will set its dimensions next.
```

此時加入矩形尚未影響版面配置，直到設定大小並加入容器為止。

### 設定形狀大小與尺寸

#### 第四步：定義寬度與高度

設定形狀的尺寸決定其在頁面上的呈現方式。寬度與高度以點 (pt) 為單位（1 pt = 1/72 in）。

```java
        // Step 4: Set shape size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

您可以依設計需求調整這些數值。相同的方法適用於任何 `Shape` 實例，故亦可重複使用於圓形、箭頭或自訂繪圖。

#### 第五步：將矩形插入文件

現在矩形已有尺寸，將它放置於頁面上。`DocumentBuilder` 的 `insertShape` 方法會在目前游標位置加入形狀。

```java
        // Insert the rectangle at the builder’s current position
        builder.insertShape(rectangle);
```

此時矩形會單獨顯示在頁面上。接下來的步驟將說明如何與其他形狀結合。

## 將多個形狀分組

將形狀分組後，可一次移動、旋轉或調整大小，對於建立複雜圖表特別有用。

### 第六步：建立群組形狀容器

```java
        // Step 6: Create a group shape that will hold the rectangle and other shapes
        GroupShape groupShape = builder.insertGroupShape();
```

`insertGroupShape` 呼叫會在文件中加入一個空的容器。之後加入此容器的任何形狀，都會成為群組的一部份。

### 將形狀加入群組

#### 第七步：將矩形加入群組

```java
        // Append the previously created rectangle to the group
        groupShape.appendChild(rectangle);
```

加入後，矩形會從文件主體移至群組的內部集合。矩形現在會遵循群組的變換設定。

#### 第八步：加入橢圓作示範

```java
        // Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(80);
        ellipse.setHeight(80);
        groupShape.appendChild(ellipse);
```

橢圓與矩形共享相同的座標空間，若需要可透過調整 `setLeft` 與 `setTop` 屬性來視覺對齊。

### 第九步：儲存文件

```java
        // Save the result to a new file
        doc.save("output.docx");
    }
}
```

執行程式後會產生 `output.docx`。在 Microsoft Word 或 LibreOffice 開啟，即可看到矩形與橢圓已被分組。選取任一形狀時，整個群組會同時被選取，證明 **將形狀加入群組** 已成功。

![在 Java 中新增矩形形狀範例](image.png){alt="在 Java 中新增矩形形狀範例"}

*此截圖顯示矩形與橢圓位於同一個群組中，已可共同操作。*

## 為何採用此方式

* **單一真相來源** – 所有形狀屬性在建立群組前就已設定，避免版面異常。
* **可重用性** – 相同的 `setWidth`/`setHeight` 方法適用於任何形狀，您可將範例延伸至箭頭、星形或自訂 SVG。
* **效能** – 分組可減少 Word 渲染器需處理的繪圖物件數量，提升大型文件的開啟速度。
* **可維護性** – 形狀建立與分組邏輯集中，未來開發者可在不搜尋無關程式碼的情況下調整尺寸或新增形狀。

## 常見變形與邊緣情況

| 情境 | 調整方式 |
|----------|------------|
| **不同單位** | 使用 `PointsToPixels` 轉換，或設定 `Shape.setWrapType(WrapType.INLINE)` 以進行行內放置。 |
| **旋轉群組** | 呼叫 `groupShape.setRotation(45);` 以將所有子形狀旋轉 45°。 |
| **在形狀內加入文字** | 在設定尺寸後使用 `Shape.setText("Label");`。 |
| **動態尺寸** | 透過 `doc.getFirstSection().getPageSetup().getPageWidth()` 取得頁面寬度，並依比例計算形狀大小。 |

這些變形說明了核心流程——**新增矩形形狀**、**設定形狀大小**、**分組多個形狀**、**將形狀加入群組**——如何因應各種實務需求而彈性調整。

## 結論

您現在已掌握如何使用 Java **新增矩形形狀**至 Word 文件、**設定形狀大小**、**分組多個形狀**，以及 **將形狀加入群組** 的完整作法。完整範例可編譯為單一可執行類別，產生的 DOCX 檔案即展示預期結果。

接下來您可以探索：

* 為每個形狀加入文字標籤或超連結。
* 將群組再度嵌套，以建立階層式圖表。
* 在保留形狀群組的前提下，將文件匯出為 PDF。

歡迎嘗試不同的尺寸、顏色與額外形狀類型。精通形狀操作將為自動化報表產生、動態圖表與豐富文件體驗開啟大門——全部直接透過 Java 程式碼完成。

## 接下來該學什麼？

以下教學與本指南緊密相關，能進一步深化您所學的技巧。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您掌握更多 API 功能，並在專案中探索替代實作方式。

- [在 Java 中插入矩形形狀 – 分組與定位形狀](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [使用 Aspose.Words 在 Word 文件的群組形狀中建立並插入橢圓與矩形](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [使用 Java 在 Word 文件中建立矩形形狀](/words/english/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}