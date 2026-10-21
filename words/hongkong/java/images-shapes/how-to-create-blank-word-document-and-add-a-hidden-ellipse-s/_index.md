---
category: general
date: 2026-09-21
description: 使用 C# 建立空白 Word 文件，內含隱藏的橢圓形。學習如何在 Word 中隱藏形狀，並以程式方式產生隱藏形狀。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to create ellipse
- hide shape in word
- create hidden shape
language: zh-hant
lastmod: 2026-09-21
og_description: 使用 C# 建立帶有隱藏橢圓形的空白 Word 文件。本指南說明如何在 Word 中隱藏形狀以及以程式方式建立隱藏形狀。
og_image_alt: Screenshot of a blank Word document that contains a hidden ellipse shape
  created with C#
og_title: 在 C# 中建立含隱藏橢圓形狀的空白 Word 文件
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create blank Word document with a hidden ellipse using C#. Learn how
    to hide shape in Word and generate a hidden shape programmatically.
  headline: How to create blank Word document and add a hidden ellipse shape in C#
  type: TechArticle
- questions:
  - answer: The shape’s XML adds a few hundred bytes, which is negligible for most
      use cases. The file remains essentially the same size as a truly empty document.
    question: Does hiding a shape affect document size?
  - answer: Yes. Load the document, locate the shape (`doc.GetChildNodes(NodeType.Shape,
      true)`), and set `shape.Hidden = false`.
    question: Can I unhide the shape later programmatically?
  - answer: No. Hidden objects are excluded from the print layout, so the printed
      page stays blank.
    question: Will the hidden shape appear when printing?
  - answer: 'The `Hidden` property is part of the OOXML spec, so any Word processor
      that fully implements OOXML (Word, LibreOffice, Google Docs) will respect the
      hidden flag. --- ## Conclusion You now know how to **create blank Word document**,
      **how to create ellipse**, **hide shape in Word**, and **create hidd'
    question: Is this approach compatible with Office Open XML (OOXML) only?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Word automation
title: 如何在 C# 中建立空白 Word 文件並加入隱藏的橢圓形
url: /zh-hant/java/images-shapes/how-to-create-blank-word-document-and-add-a-hidden-ellipse-s/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中建立空白 Word 文件並加入隱藏的橢圓形狀

如果您需要 **create blank Word document**（建立空白 Word 文件）且其中包含不可見的圖形，本指南將完整說明操作步驟。完成本教學後，您將得到一個看似空白的 .docx 檔案，實際上卻儲存了一個在版面中隱藏的橢圓形狀。

我們將使用 Aspose.Words for .NET 來建立文件、插入橢圓形、隱藏它，並儲存檔案。步驟亦涵蓋 **how to create ellipse** 物件、正確的 **hide shape in Word** 方法，以及可於任何 .NET 專案使用的 **create hidden shape** 程式碼。

## 前置條件

* .NET 6.0 SDK 或更新版本已安裝  
* Visual Studio 2022（或任何 C# 編輯器）  
* Aspose.Words for .NET 授權或免費評估版  
* 具備基本的 C# 語法知識  

除 `Aspose.Words` 之外，無需其他 NuGet 套件。

## 使用 Aspose.Words 建立空白 Word 文件

第一步是產生一個空的 Word 檔案。這為我們提供了一個乾淨的畫布，之後可在其上插入隱藏的圖形。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document doc = new Document();

        // The document is currently empty – it contains no paragraphs or shapes.
        // This is the foundation for all further operations.
```

**Why we start with a blank document** – 從空白檔案開始可確保沒有不需要的內容干擾隱藏的形狀，同時保持檔案大小最小，這在文件日後作為範本時相當有用。

## 如何在空白文件中建立橢圓形

接下來我們需要一個 `DocumentBuilder` 來加入內容。此建構器讓我們能精確地將形狀放置在指定位置。

```csharp
        // Step 2: Initialize a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert an ellipse shape (width: 100 points, height: 50 points)
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

        // The ellipse now exists on the page, but it is visible by default.
```

**Explanation** – `ShapeType.Ellipse` 告訴 Aspose.Words 繪製一個近似圓形的圖形。寬度與高度以點 (pt) 為單位測量 (1 pt ≈ 1/72 英吋)。您可以調整這些數值以符合設計需求。

## 在 Word 中隱藏形狀，使其不出現在版面上

即使被隱藏，形狀仍會存在於文件的 XML 中，這對於儲存中繼資料、條件格式或之後的程式化修改皆有幫助。要將其隱藏，我們將 `Hidden` 屬性設為 `true`。

```csharp
        // Step 4: Hide the shape so it does not appear in the layout
        ellipse.Hidden = true;

        // When Hidden = true, Word treats the shape as if it were not there.
        // The shape remains in the document’s DOM, allowing you to retrieve or modify it later.
```

**Why hide the shape** – 隱藏的形狀會被版面引擎忽略，因而頁面看起來完全空白。然而，形狀資料仍會保留，可用於儲存標記、書籤或下游程序可讀取的自訂 XML。

## 儲存含有隱藏形狀的文件

最後我們將檔案寫入磁碟。儲存的 `.docx` 於 Microsoft Word 開啟時不會顯示任何可見內容，但隱藏的橢圓形仍然存在。

```csharp
        // Step 5: Save the document with the hidden shape
        doc.Save(@"C:\Temp\HiddenEllipse.docx");

        // The file now contains a hidden ellipse and appears empty when opened.
    }
}
```

**Verification** – 在 Word 中開啟產生的檔案，然後按 `Alt+F9` 切換欄位代碼，接著 `Ctrl+A` → `Ctrl+Shift+F9` 以檢視隱藏物件。您會在文件的 XML (`word/document.xml`) 中看到橢圓形，但頁面上什麼也看不到。

---

## 完整、可執行的範例

以下是完整的程式碼，您可以直接複製貼上到新的主控台專案中。它包含所有 `using` 指令與 `Main` 方法，讓您無需額外框架即可執行。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace HiddenShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank Word document
            Document doc = new Document();

            // 2️⃣ Prepare a builder to insert content
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert an ellipse (100 pt × 50 pt)
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

            // 4️⃣ Hide the ellipse so the page stays empty
            ellipse.Hidden = true;

            // 5️⃣ Save the file
            string outPath = @"C:\Temp\HiddenEllipse.docx";
            doc.Save(outPath);

            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

**Expected output** – 執行程式時，主控台會輸出檔案路徑，且產生的 Word 檔案不含任何可見物件。若使用 zip 工具檢查文件（`.docx` 為 zip 壓縮檔），您會在 `word/document.xml` 中找到描述橢圓形的 `<w:pict>` 元素。

---

## 常見變化與邊緣情況

| 情境 | 需要變更的內容 | 為何重要 |
|----------|----------------|----------------|
| **Different shape** | 將 `ShapeType.Ellipse` 替換為 `ShapeType.Rectangle`、`ShapeType.Line` 等。 | 讓您在保持相同工作流程的同時，隱藏其他圖形。 |
| **Multiple hidden shapes** | 多次呼叫 `InsertShape`，並對每個形狀設定 `Hidden = true`。 | 用於嵌入一系列標記或佔位符。 |
| **Conditional visibility** | 同時將 `shape.Visible = false` 與 `shape.Hidden = true` 設定，以提升安全性。 | 某些較舊的 Word 版本對 `Visible` 的處理不同；同時設定兩者可涵蓋所有情況。 |
| **Saving to a stream** | 將 `doc.Save(path)` 改為 `doc.Save(stream, SaveFormat.Docx)`。 | 允許直接透過 HTTP 傳送文件或將其儲存於資料庫中。 |
| **Applying a style** | 插入後，於隱藏前修改 `ellipse.FillColor`、`ellipse.LineWeight` 等屬性。 | 形狀的樣式會保留在 XML 中，日後取消隱藏時可再利用。 |

**Pro tip:** 請務必在目標 Word 版本（例如 Word 2019、Word 365）上測試隱藏形狀，因為當隱藏物件與複雜版面互動時，偶爾會出現渲染異常。

---

## 常見問答

**Q: 隱藏形狀會影響文件大小嗎？**  
A: 形狀的 XML 只會增加數百位元組，對大多數使用情境而言可忽略不計。檔案大小基本與真正的空白文件相同。

**Q: 我可以稍後以程式方式取消隱藏形狀嗎？**  
A: 可以。載入文件，定位形狀 (`doc.GetChildNodes(NodeType.Shape, true)`)，然後將 `shape.Hidden = false`。

**Q: 隱藏形狀在列印時會出現嗎？**  
A: 不會。隱藏的物件會被排除於列印版面，因此列印出的頁面仍保持空白。

**Q: 此方法僅相容於 Office Open XML (OOXML) 嗎？**  
A: `Hidden` 屬性屬於 OOXML 規範，任何完整實作 OOXML 的 Word 處理器（如 Word、LibreOffice、Google Docs）都會遵守此隱藏旗標。

---

## 結論

您現在已了解如何使用 Aspose.Words for .NET **create blank Word document**、**how to create ellipse**、**hide shape in Word** 以及 **create hidden shape**。本教學涵蓋了完整的生命週期——從初始化空白檔案、插入、隱藏到儲存形狀——並提供驗證步驟與常見變化。

接下來，您可以探索：

* 加入隱藏的文字方塊以儲存中繼資料（將 `hide shape in word` 技術應用於文字）  
* 使用自訂 XML 部分在隱藏形狀旁儲存結構化資料  
* 將含隱藏形狀的文件轉換為 PDF，同時保留隱藏元素  

嘗試不同的形狀與可見性設定，了解隱藏內容如何在 Word 檔案中充當輕量級資料儲存。  
祝編程愉快！

## 接下來該學什麼？

以下教學涵蓋與本指南密切相關的主題，並在此基礎上延伸技術。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在專案中探索替代實作方式。

- [使用 C# 建立矩形形狀於 Word – 步驟指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [在 Word 文件中使用 Aspose.Words for .NET 建立群組形狀](/words/english/net/working-with-shapes/add-group-shape/)
- [使用陰影矩形建立 Word 文件 – 步驟指南](/words/english/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}