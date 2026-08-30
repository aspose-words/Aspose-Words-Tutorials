---
category: general
date: 2026-07-16
description: 如何在 Java 中使用 Aspose.Words 插入群組圖形 – 新增矩形圖形、設定圖形尺寸，並建立彩色矩形與圓形。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert group
- add rectangle shape
- set shape dimensions
- create colored rectangle
- create colored circle
language: zh-hant
lastmod: 2026-07-16
og_description: 如何在 Java 中插入群組圖形：實作指南，新增矩形圖形、設定圖形尺寸，並使用 Aspose.Words 建立彩色矩形與圓形。
og_image_alt: Screenshot showing a grouped blue rectangle and red circle in a Java‑generated
  Word document
og_title: 在 Java 中插入群組形狀 – 完整 Aspose.Words 教程
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  headline: how to insert group shape in Java – Complete Guide
  type: TechArticle
- description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  name: how to insert group shape in Java – Complete Guide
  steps:
  - name: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
    text: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
  - name: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
    text: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
  - name: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
    text: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
  - name: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
    text: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
  - name: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
    text: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shapes
- Document Automation
- Group Shapes
title: 在 Java 中插入群組形狀 – 完整指南
url: /zh-hant/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Java 中插入群組形狀 – 完整指南

有沒有想過 **如何在 Word 文件中使用 Java 插入群組形狀**？你並不是唯一有此疑問的人。無論你是在打造報告產生器或是動態傳單產生器，將形狀群組化都能讓版面保持整潔，程式碼也更易於管理。

在本教學中，我們將一步步說明如何 **新增矩形形狀**、**設定形狀尺寸**，以及使用 Aspose.Words 程式庫 **建立彩色矩形** 與 **建立彩色圓形**。完成後，你將擁有一個可執行的程式，產生的 .docx 檔案中會有一個藍色矩形與一個紅色圓形，兩者都整齊地包在同一個群組內。

## 前置條件

在開始之前，請確保你已具備以下環境：

- 已安裝並設定 Java 17（或任何較新的 JDK）。
- 使用 Maven 或 Gradle 來管理相依性。
- Aspose.Words for Java 23.9 或更新版本 – 可從 Maven Central 取得。
- 具備基本的 Java 語法概念 – 不需要太高階的知識。

如果缺少上述任一項，請從 Oracle 官網下載 JDK，並在 `pom.xml` 中加入 Aspose.Words 相依性：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

基礎工作完成後，讓我們動手實作吧。

## 如何插入群組形狀 – 概觀

核心概念非常簡單：建立一個 `Document`，開啟 `DocumentBuilder`，插入 **群組形狀**，然後把個別形狀（矩形與圓形）放入該群組。群組就像一個容器，之後搬移它時，裡面的所有物件都會一起移動，非常適合複雜版面配置。

以下是完整、可直接執行的程式碼範例。你可以把它貼到一個名為 `InsertGroupShapeDemo` 的新 Java 類別中。

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to insert a group shape, add a rectangle and a circle,
 * set their dimensions, and apply colors using Aspose.Words for Java.
 */
public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to work with it.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape that will contain other shapes.
        Shape group = builder.insertGroupShape();

        // Step 3: Create a blue rectangle, set its size and position, and add it to the group.
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);          // set shape dimensions – width
        rectangle.setHeight(50.0);          // set shape dimensions – height
        rectangle.setLeft(20.0);            // X‑coordinate inside the group
        rectangle.setTop(20.0);             // Y‑coordinate inside the group
        rectangle.getFill().setForeColor(Color.BLUE); // create colored rectangle
        group.appendChild(rectangle);       // add rectangle shape to the group

        // Step 4: Create a red circle, set its size and position, and add it to the same group.
        Shape circle = new Shape(doc, ShapeType.ELLIPSE);
        circle.setWidth(60.0);              // set shape dimensions – width (diameter)
        circle.setHeight(60.0);             // set shape dimensions – height (diameter)
        circle.setLeft(150.0);              // X‑coordinate inside the group
        circle.setTop(20.0);                // Y‑coordinate inside the group
        circle.getFill().setForeColor(Color.RED); // create colored circle
        group.appendChild(circle);          // add circle shape to the group

        // Step 5: Save the document with the grouped shapes.
        doc.save("GroupShapeDemo.docx");
        System.out.println("Document saved successfully.");
    }
}
```

> **小技巧：** `setLeft` 與 `setTop` 的數值是相對於群組的原點，而非頁面。之後若要重新定位整個群組，只要調整這兩個值即可，十分方便。

### 剛剛發生了什麼？

1. **Document & Builder** – 我們先建立一個空的 Word 檔案，並取得 `DocumentBuilder` 以便插入內容。
2. **群組形狀** – `builder.insertGroupShape()` 會建立一個容器。把它想像成繪圖物件的資料夾。
3. **藍色矩形** – 我們建立一個 `RECTANGLE` 型別的 `Shape`，設定大小與位置，並填入藍色——這就是 **建立彩色矩形** 的步驟。
4. **紅色圓形** – 同樣的流程，只是改用 `ELLIPSE` 來產生完美的圓形，並填入紅色——即 **建立彩色圓形** 的部分。
5. **儲存** – 最後把所有內容寫入 `GroupShapeDemo.docx`。

執行程式 (`mvn compile exec:java -Dexec.mainClass=InsertGroupShapeDemo`) 後開啟產生的檔案，你應該會看到左側的藍色矩形與右側的紅色圓形，兩者都被鎖定在同一個群組框內。

## 新增矩形形狀

如果只需要單獨的矩形而不想使用群組，可以省略 `insertGroupShape()`，直接把矩形加到文件的 body 中。不過，使用群組可以一次移動、旋轉或刪除多個形狀，彈性更大。

```java
Shape rect = new Shape(doc, ShapeType.RECTANGLE);
rect.setWidth(120);
rect.setHeight(70);
rect.getFill().setForeColor(Color.GREEN);
builder.insertNode(rect);
```

可以看到我們在此使用了 **新增矩形形狀** 的邏輯。矩形會作為獨立物件出現在頁面上。實務上大多數情況仍建議使用群組，因為它能保留相對位置。

## 設定形狀尺寸

當你看到 `setWidth` 與 `setHeight` 方法時，請記得它們接受的單位是 **點**（1/72 英吋）。如果你習慣使用公釐，先自行換算：

```java
double mmToPoints = 72.0 / 25.4;
double widthInMm = 50; // 50 mm
rectangle.setWidth(widthInMm * mmToPoints);
rectangle.setHeight(30 * mmToPoints);
```

此片段示範了 **設定形狀尺寸** 時的單位換算——當設計規格來自使用公制的 UI 原型時特別方便。

## 建立彩色矩形

為形狀上色只需要呼叫 `getFill().setForeColor()`，傳入任意 `java.awt.Color` 即可。想要漸層效果嗎？使用 `setForeColor` 設定起始色，`setBackColor` 設定結束色。

```java
rectangle.getFill().setForeColor(Color.MAGENTA);
rectangle.getFill().setBackColor(Color.YELLOW);
rectangle.getFill().setFillType(FillType.GRADIENT);
```

這是一個快速的方式，利用 **建立彩色矩形** 並搭配漸層填色，而非單色。

## 建立彩色圓形

圓形其實就是寬高相等的橢圓。上色的方式相同：

```java
circle.getFill().setForeColor(new Color(255, 165, 0)); // orange
```

如果需要透明填色，請設定 alpha 通道：

```java
circle.getFill().setForeColor(new Color(0, 0, 255, 128)); // semi‑transparent blue
```

現在你已掌握 **建立彩色圓形** 的技巧。

## 儲存文件

Aspose.Words 支援多種輸出格式：DOCX、PDF、HTML、PNG 等等。此範例我們仍以 DOCX 為主，因為它能完整保留向量形狀。

```java
doc.save("GroupShapeDemo.pdf", SaveFormat.PDF);
```

只要切換 `SaveFormat`，即可產生相同群組藝術作品的 PDF 版本。

## 常見陷阱與避免方法

- **忘記把形狀加入群組？** 形狀會出現在頁面上，但不會隨群組一起移動。務必呼叫 `group.appendChild(yourShape)`。

## 接下來該學什麼？

以下教學與本篇內容密切相關，能進一步深化你對 API 的運用，並提供其他實作方式供你在專案中參考：

- [建立 Word 文件 Java – 新增帶陰影效果的矩形形狀](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [如何使用 Aspose.Words for Java 的 DocumentBuilder 建立表單欄位並新增內容](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [在 Word 中使用 Aspose.Words 建立矩形形狀 – 步驟指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}