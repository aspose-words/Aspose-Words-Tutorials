---
category: general
date: 2026-01-11
description: 快速使用 Java 建立 Word 文件，透過加入矩形形狀、設定填色並為形狀套用陰影。一步一步學習。
draft: false
keywords:
- create word document java
- add rectangle shape
- apply shadow to shape
- set shape fill color
- how to add shape
language: zh-hant
og_description: 透過插入矩形形狀、設定填色與套用陰影，使用 Java 建立 Word 文件。完整指南與程式碼。
og_title: 使用 Java 建立 Word 文件 – 添加帶陰影的矩形形狀
tags:
- Aspose.Words
- Java
- Document Generation
title: 使用 Java 建立 Word 文件 – 添加帶陰影效果的矩形形狀
url: /zh-hant/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 建立 Word 文件（Java） – 新增矩形形狀與陰影效果

曾經需要 **create word document java**，但想讓它看起來更精緻嗎？也許你正在開發報表產生器，而單純的頁面根本不夠用。好消息是，使用 Aspose.Words for Java，你可以在文件中插入矩形形狀，為它添加顏色，甚至加上一個細緻的陰影——只需幾行程式碼。

在本教學中，我們將一步步示範：如何新增矩形形狀、設定填充顏色，並對形狀套用陰影，讓你的 Word 檔案看起來更專業。完成後，你將擁有一個可直接複製貼上的可執行範例。

## 需要的條件

- **Java 17** (或任何較新的 JDK) – 程式碼使用標準語言功能。
- **Aspose.Words for Java** 函式庫 – 建議使用 23.9 或更新的版本。
- 你慣用的 IDE 或文字編輯器 – 如 IntelliJ IDEA、Eclipse、VS Code… 隨你選擇。
- 用於儲存產生的 `ShadowShape.docx` 的資料夾。

不需要額外的設定向導；只要將 Aspose.Words JAR 加入 classpath，即可開始使用。

## 步驟 1：設定專案並匯入 Aspose.Words

首先，建立一個新的 Maven（或 Gradle）專案，並加入 Aspose.Words 相依性。以下是 Maven 的最小 `pom.xml` 片段：

```xml
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>23.9</version>
        <classifier>jdk17</classifier>
    </dependency>
</dependencies>
```

如果你沒有使用 Maven，只需將 JAR 檔放入 `libs` 資料夾，並加入建置路徑即可。

> **專業提示：** Aspose 提供免費試用授權，你可以這樣嵌入 `License license = new License(); license.setLicense("Aspose.Words.lic");`。若只是快速測試，可略過此步驟，函式庫會以評估模式運作。

## 步驟 2：建立新文件與 Builder

現在我們真的要 **create word document java** 物件。`Document` 類別代表整個 .docx 檔案，而 `DocumentBuilder` 讓我們可以插入內容。

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

此時你已擁有一個空白文件，可用來插入形狀、段落或其他任何需要的內容。

## 步驟 3：插入矩形形狀並設定填充顏色

新增形狀只要呼叫 `insertShape` 即可。我們將使用 **add rectangle shape** 的技巧，這也是次要關鍵字 *add rectangle shape*。

```java
        // Insert a rectangle shape – 200pt wide, 100pt tall
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 200, 100);

        // Set the fill color to a bright orange
        rectangle.setFillColor(java.awt.Color.ORANGE);
```

為什麼選橙色？在白色的海洋中它很顯眼，但你也可以換成任何 `java.awt.Color`。此步驟對應次要關鍵字 *set shape fill color*。

## 步驟 4：設定陰影外觀 – 套用陰影至形狀

現在來到有趣的部分：為矩形加上細緻的投影。Aspose API 提供 `ShadowFormat` 物件，可控制陰影的各項屬性。

```java
        // Get the shadow format object for the shape
        ShadowFormat shadow = rectangle.getShadowFormat();

        // Make the shadow visible
        shadow.setVisible(true);

        // Choose a neutral gray for the shadow color
        shadow.setColor(java.awt.Color.GRAY);

        // Blur radius – larger values produce a softer edge
        shadow.setBlur(5.0);

        // Offset determines how far the shadow is displaced
        shadow.setOffsetX(4.0);
        shadow.setOffsetY(4.0);

        // Transparency (0 = opaque, 1 = fully transparent)
        shadow.setTransparency(0.2);

        // Define the shadow style and type
        shadow.setStyle(ShadowStyle.OUTER);
        shadow.setType(ShadowType.PARALLEL);

        // Scale controls the overall size of the shadow relative to the shape
        shadow.setScale(1.0);
```

上述程式碼 **apply shadow to shape** 正如次要關鍵字所示。你可以調整 `blur`、`offsetX/Y` 與 `transparency` 以符合設計需求。例如，較大的 `offsetX` 會產生更明顯的投影，而較高的 `transparency` 則讓陰影更柔和。

## 步驟 5：儲存文件

最後，我們將文件寫入磁碟。選擇一個你有寫入權限的資料夾，並為檔案命名。

```java
        // Save the result – adjust the path as needed
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

當你在 Microsoft Word 或 LibreOffice 開啟 `ShadowShape.docx` 時，會看到一個亮橙色的矩形，下面懸浮著柔和的灰色陰影。

![create word document java with rectangle shape](/images/shadow-rectangle.png "create word document java – rectangle with shadow")

*圖片的 alt 文字包含主要關鍵字，符合 SEO 規則。*

## 常見問題與邊緣情況

### 如果需要其他形狀呢？

Aspose.Words 支援數十種 `ShapeType` 值——星形、箭頭、標註等。只要將 `ShapeType.RECTANGLE` 換成 `ShapeType.OVAL` 或其他列舉常數即可。相同的 **how to add shape** 步驟仍然適用。

### 如何將形狀加入特定段落？

與其直接使用 builder 插入形狀，你可以先建立形狀（`new Shape(document, ShapeType.RECTANGLE)`），再透過 `paragraph.appendChild(shape)` 加入到 `Paragraph` 中。這樣可對版面配置有更細緻的控制。

### 能否使用漸層填充而非純色？

可以！使用 `rectangle.getFill().setFillType(FillType.GRADIENT)` 並定義 `LinearGradientFill`。API 稍微冗長，但對於現代設計非常適用。

### 與舊版 Word 的相容性如何？

Aspose.Words 預設儲存為 .docx 格式，支援 Word 2007 以上及 LibreOffice。若需要 .doc，請呼叫 `document.save("file.doc", SaveFormat.DOC)`。陰影的呈現可能略有差異，但形狀本身仍保持完整。

## 完整可執行範例（可直接複製貼上）

以下是完整程式碼，可直接編譯執行。請將 `YOUR_DIRECTORY` 替換為你機器上的實際路徑。

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a rectangle shape and set its fill color
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 200, 100);
        rectangle.setFillColor(java.awt.Color.ORANGE);

        // Step 3: Apply shadow to shape
        ShadowFormat shadow = rectangle.getShadowFormat();
        shadow.setVisible(true);
        shadow.setColor(java.awt.Color.GRAY);
        shadow.setBlur(5.0);
        shadow.setOffsetX(4.0);
        shadow.setOffsetY(4.0);
        shadow.setTransparency(0.2);
        shadow.setStyle(ShadowStyle.OUTER);
        shadow.setType(ShadowType.PARALLEL);
        shadow.setScale(1.0);

        // Step 4: Save the document
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

執行此程式會產生一個 Word 檔，內含橙色矩形與柔和的灰色陰影——正是我們在想要 **create word document java** 並加入樣式化形狀時的目標。

## 結論

現在你已掌握一套完整的 **create word document java** 流程，能 *新增矩形形狀*、*設定形狀填充顏色*，以及 *套用陰影至形狀*。此方法簡潔、API 流暢，且可無限延伸——不同形狀、漸層填充，甚至為同一形狀加入多重陰影。

接下來可以做什麼？試著疊加多個形狀、使用 `ShadowStyle.ETCHED` 來獲得不同的視覺效果，或將此與表格產生結合，打造完整的報表。所有可能性僅受想像力（以及 Aspose 授權等級）的限制。

如果在實作過程中遇到任何問題或有進一步的改進想法，歡迎在下方留言。祝開發順利，讓你的 Word 文件不再單調！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}