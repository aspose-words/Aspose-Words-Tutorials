---
category: general
date: 2026-07-26
description: 在 Java 中使用 Aspose.Words 插入矩形形狀。了解如何設定形狀大小、定位形狀，以及如何在 DOCX 檔案中將形狀分組。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- set shape size
- position shape
- how to group shapes
- how to add rectangle
language: zh-hant
lastmod: 2026-07-26
og_description: 在 Java 中插入矩形形狀，打造豐富的 DOCX 圖形。跟隨此一步一步的指引，輕鬆設定形狀大小、定位形狀及群組形狀。
og_image_alt: Screenshot showing a rectangle shape inserted and grouped in a Java‑generated
  Word document
og_title: 在 Java 中插入矩形形狀 – 掌握分組與定位
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert rectangle shape in Java using Aspose.Words. Learn how to set
    shape size, position shape, and how to group shapes in a DOCX file.
  headline: Insert Rectangle Shape in Java – Group and Position Shapes
  type: TechArticle
tags:
- Aspose.Words
- Java
- Shapes
- DOCX
title: 在 Java 中插入矩形形狀 – 群組與定位形狀
url: /zh-hant/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Java 中插入矩形形狀 – 群組與定位形狀

是否曾經需要在撰寫 Java 程式碼時 **插入矩形形狀** 到 Word 文件中？你並非唯一遇到此需求的人——開發報表、發票或自訂範本的程式設計師常常會碰到這個問題。好消息是，只要幾行 Aspose.Words for Java 的程式碼，你就可以 **插入矩形形狀**、**設定形狀大小**、**定位形狀**，甚至 **如何群組形狀**，讓它們如同一個單位一起移動。

在本指南中，我們將從建立空白文件到儲存包含兩個整齊群組矩形的 `.docx`，完整說明整個流程。完成後，你將了解 **如何新增矩形** 物件、控制其尺寸、精確放置位置，並將它們打包成可重複使用的群組。除了 Aspose.Words 之外不需要其他外部函式庫，且程式碼相容於 Java 8 以上。

## 前置條件

- 已安裝 Java 8 或更新版本（我使用 JDK 17，但任何支援 Maven 的版本皆可）
- Aspose.Words for Java 23.9 或更新版本 – 將相依性加入你的 `pom.xml` 或下載 JAR
- 具備基本的 Java 語法概念（只要會寫 `main` 方法即可）
- 任意你喜好的 IDE 或文字編輯器（IntelliJ IDEA、Eclipse、VS Code…）

> **小技巧：** 若你使用 Maven，相依性寫法如下：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

現在基礎已備妥，讓我們深入程式碼。

## 插入矩形形狀並設定其大小

首先，你需要建立一個全新的 `Document` 與 `DocumentBuilder`。Builder 就像是你的「筆」，用來在頁面上繪製形狀。以下我們 **插入矩形形狀**，並立即 **設定形狀大小** 為 100 × 80 點。

```java
import com.aspose.words.*;

public class GroupedRectanglesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a builder to add content
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape(400, 200);
        // The group itself is 400×200 points – adjust as needed

        // ---------- First rectangle ----------
        // Insert rectangle shape
        Shape rectangle1 = new Shape(document, ShapeType.RECTANGLE);
        // Set shape size
        rectangle1.setWidth(100);
        rectangle1.setHeight(80);
        // Position shape inside the group
        rectangle1.setLeft(20);   // 20 points from the left edge of the group
        rectangle1.setTop(30);    // 30 points from the top edge of the group
        // Add the rectangle to the group
        group.appendChild(rectangle1);
```

請注意 `setWidth`/`setHeight` 呼叫是以點為單位 **設定形狀大小**（1 pt ≈ 1/72 英吋）。如果你偏好單一方法，也可以使用 `setSize`，但明確的呼叫方式能讓意圖一目了然。

## 在頁面上定位形狀

在取得第一個矩形後，我們需要 **定位形狀** 第二個，使其不與第一個重疊。定位方式相同：設定相對於群組原點的 `Left` 與 `Top` 屬性。

```java
        // ---------- Second rectangle ----------
        Shape rectangle2 = new Shape(document, ShapeType.RECTANGLE);
        rectangle2.setWidth(120);
        rectangle2.setHeight(60);
        // Position this rectangle a bit farther to the right and lower down
        rectangle2.setLeft(150);
        rectangle2.setTop(50);
        group.appendChild(rectangle2);
```

如果你在想為什麼使用 `setLeft` 而非 `setX`，那是因為 Aspose.Words 採用了傳統的 Windows GDI 座標系統——`Left` 為水平偏移，`Top` 為垂直偏移。調整這些數值即可微調版面，而不必去弄表格或段落。

## 如何群組形狀

你可能會問，「為什麼要花時間建立群組？」當你希望多個形狀一起移動、整體旋轉，或共享相同樣式時，群組就很有意義。上述程式碼已透過 `builder.insertGroupShape` 建立了 `GroupShape`。這個物件本質上是一個容器——可想像成放置其他形狀檔案的資料夾。

> **為什麼重要：** 若日後想加入說明文字或旋轉整個圖表，只需修改群組本身，而不必逐一調整每個矩形。

## 如何將矩形加入群組

將 **如何將矩形加入群組** 的動作僅是呼叫 `group.appendChild(rectangle)`。在底層，Aspose.Words 會更新群組的內部集合，並自動重新計算邊界框，使群組仍符合其設定的寬度與高度。

```java
        // At this point the group already contains both rectangles.
        // You can also set the group’s border or fill if you like.
        group.getShapeStyle().setLineColor(Color.BLACK);
        group.getShapeStyle().setFillColor(Color.LIGHTGRAY);
```

你可以嘗試其他 `ShapeType`——例如 `ShapeType.ELLIPSE`、`ShapeType.TRIANGLE` 等，`appendChild` 的模式同樣適用。

## 儲存文件

最後，我們將文件寫入磁碟。路徑可以是絕對或相對路徑，只要確保資料夾已存在即可。

```java
        // Step 5: Save the document containing the grouped shapes
        String outPath = "output/GroupShape.docx";
        document.save(outPath);
        System.out.println("Document saved to: " + outPath);
    }
}
```

當你在 Microsoft Word 中開啟 `GroupShape.docx` 時，會看到兩個並排的矩形，都被鎖定在一個淺灰色方框內。選取灰色方框會同時突顯兩個矩形——證明 **如何群組形狀** 確實有效。

![在 Word 文件中的群組矩形](placeholder-image.png){: .center-image alt="插入矩形形狀範例，顯示兩個矩形在 Java 產生的 DOCX 檔案中被群組"}

*圖片替代文字（SEO）：* **插入矩形形狀範例，顯示兩個矩形在 Java 產生的 DOCX 檔案中被群組**。

## 預期輸出

- 位於 `output` 資料夾中的 `GroupShape.docx` 檔案。
- 文件內部：一個 400 × 200 pt 的群組，內含兩個矩形（100 × 80 pt 與 120 × 60 pt），分別位於 (20, 30) 與 (150, 50)。
- 該群組具有細黑色邊框與淺灰色填充，使群組關係一目了然。

開啟檔案並嘗試拖曳灰色方框——兩個矩形應會一起移動。若未如預期，請再次確認已對每個形狀呼叫 `group.appendChild`。

## 常見陷阱與邊緣情況

| 問題 | 為什麼會發生 | 解決方式 |
|------|--------------|----------|
| **矩形出現在頁面之外** | `Left`/`Top` 值超出群組尺寸 | 增加群組大小 (`insertGroupShape(width, height)`) 或減少偏移量 |
| **儲存後群組消失** | 群組的 `Width`/`Height` 被設定為 0 | 呼叫 `insertGroupShape` 時提供非零尺寸 |
| **形狀顏色顯示不正確** | 預設填充為透明，Word 可能將其顯示為白色 | 明確設定 `setFillColor` 或使用 `ShapeStyle` |
| **例外 `ArgumentOutOfRangeException`** | 使用負座標 | 保持 `Left` 與 `Top` 為非負值 |

提前處理這些問題，可避免許多新手常見的「為什麼我的形狀會消失？」的頭痛。

## 重點回顧與後續步驟

我們已完整說明在 Java 中 **插入矩形形狀** 的全流程：建立文件、**設定形狀大小**、**定位形狀**、**如何群組形狀**，以及 **如何將矩形加入群組**。完整且可執行的範例位於上方程式碼區塊，你可以直接貼到 Maven 專案中執行，查看結果。

接下來可以考慮嘗試：

- 在每個矩形內加入文字，透過

## 接下來該學什麼？

以下教學涵蓋與本指南技術密切相關的主題。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助你精通更多 API 功能，並在自己的專案中探索其他實作方式。

- [建立 Word 文件（Java） – 新增帶陰影效果的矩形形狀](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [在 Word 文件中使用 Aspose.Words for .NET 建立群組形狀](/words/english/net/working-with-shapes/add-group-shape/)
- [建立帶陰影矩形形狀的空白 Word 文件 – 步驟說明指南](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}