---
category: general
date: 2026-08-10
description: 使用 C# 在 Word 中插入矩形形狀。了解如何隱藏形狀、在 Word 中隱藏形狀，以及使用 Aspose.Words 建立隱藏形狀。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- hide shape in word
- create hidden shape
language: zh-hant
lastmod: 2026-08-10
og_description: 使用 C# 在 Word 中插入矩形形狀。本教學說明如何隱藏形狀、在 Word 中隱藏形狀，以及使用完整程式碼範例建立隱藏形狀。
og_image_alt: Screenshot showing a hidden rectangle shape inserted into a Word document
  using C#
og_title: 使用 C# 在 Word 中插入矩形形狀 – 步驟教學
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
    shape in Word, and create hidden shape with Aspose.Words.
  headline: Insert rectangle shape in Word with C# – complete guide
  type: TechArticle
- description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
    shape in Word, and create hidden shape with Aspose.Words.
  name: Insert rectangle shape in Word with C# – complete guide
  steps:
  - name: Can I hide only the outline but keep the fill visible?
    text: Yes. Instead of setting `Hidden = true`, you can set `rectangle.LineFormat.Visible
      = false` to hide the border while keeping the fill color. This is a variation
      of **how to hide shape** that preserves part of the visual appearance.
  - name: Does the hidden flag work in older Word versions (2003, 2007)?
    text: The hidden attribute is part of the Open XML specification introduced with
      Word 2007. Documents saved in the older binary `.doc` format will not preserve
      the flag. To support legacy formats, save the document as `.docx` and, if needed,
      convert it later using Aspose.Words’ `SaveFormat.Doc`.
  - name: What if I need to hide multiple shapes at once?
    text: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` on each shape that meets your criteria (e.g., a specific
      `ShapeType` or a custom `AlternativeText` value).
  - name: Is there a performance impact when hiding shapes?
    text: The hidden flag adds a tiny XML attribute; it does not affect rendering
      speed. However, a very large number of hidden objects can increase file size
      marginally. Remove shapes you never need to keep the document lean.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: 使用 C# 在 Word 中插入矩形形狀 – 完整指南
url: /zh-hant/net/programming-with-shapes/insert-rectangle-shape-in-word-with-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 中使用 C# 插入矩形形狀 – 完整指南

如果您需要在 Word 文件中使用 C# **insert rectangle shape**，本指南會向您展示完整步驟。您還將學習 **how to hide shape** 使其不會出現在最終檔案中，這回應了常見問題 **hide shape in Word**，並示範如何以程式方式 **create hidden shape**。

本教學涵蓋從設定 Aspose.Words SDK 到驗證形狀已隱藏的全部內容。閱讀完本文後，您將擁有一段可重複使用的程式碼片段，能直接嵌入任何 .NET 專案中。

## 前置條件

- 安裝 .NET 6.0 或更新版本（程式碼亦相容於 .NET Framework 4.6+）
- 有效的 Aspose.Words for .NET 授權或臨時評估金鑰
- Visual Studio 2022（或任何支援 C# 的 IDE）
- 具備 C# 語法及 Word 檔案文件物件模型（DOM）的基本認識

除了 `Aspose.Words` 之外，無需其他 NuGet 套件。

## 步驟 1：建立新的空白文件與 DocumentBuilder

第一步是實例化 `Document` 物件。`DocumentBuilder` 提供方便的 API，用於插入形狀、段落和表格等內容。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document document = new Document();

// DocumentBuilder lets you add elements to the document.
DocumentBuilder builder = new DocumentBuilder(document);
```

**為什麼這很重要：** `Document` 代表整個 .docx 檔案，而 `DocumentBuilder` 維持一個游標，追蹤下一個元素的插入位置。初始化這兩個物件是任何 Word 自動化任務的基礎。

## 步驟 2：插入矩形形狀

現在插入矩形。`InsertShape` 方法需要指定形狀類型以及以點為單位的尺寸（1 點 ≈ 1/72 英吋）。**200 × 100 點** 的大小會產生大約 2.78 × 1.39 英吋的矩形。

```csharp
// Insert a rectangle of 200x100 points.
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

**為什麼這很重要：** 您取得的 `Shape` 物件可完全自訂——顏色、邊框、文字與可見性皆可在儲存文件前調整。

## 步驟 3：隱藏形狀

為了避免矩形在顯示或列印時出現，將其 `Hidden` 屬性設為 `true`。此屬性直接對應 Word 的「Hidden」屬性，Word 會在檢視與列印模式下皆遵守。

```csharp
// Hide the shape so it never appears.
rectangle.Hidden = true;
```

**為什麼這很重要：** 設定 `Hidden` 是在 **hide shape in Word** 時的標準做法，且不會將形狀從文件結構中移除。形狀仍可被程式存取，方便之後進行條件格式化或資料驅動的可見性切換等操作。

## 步驟 4：儲存文件

最後，將文件寫入磁碟。可自行選擇任意資料夾；範例中使用的是佔位路徑，請自行替換為實際路徑。

```csharp
// Save the document with the hidden rectangle.
document.Save(@"C:\Temp\HiddenShape.docx");
```

**為什麼這很重要：** 儲存會完成檔案並將隱藏旗標寫入底層的 Open XML。當您在 Microsoft Word 中開啟文件時，矩形將不會顯示，證明您已成功 **create hidden shape**。

## 步驟 5：驗證隱藏的形狀

在 Microsoft Word 中開啟產生的 `HiddenShape.docx`：

1. 前往 **File → Options → Display**，確認 *“Show hidden text”* 為 **未勾選**。  
2. 矩形在任何頁面上都不應該可見。  
3. 為了再次確認，可啟用 *“Show hidden text”*；此時矩形會以淡淡的虛線輪廓顯示，證明形狀仍在但被隱藏。

如果矩形仍然可見，請確認您在設定 `Hidden = true` 後已儲存檔案，且開啟的是正確的檔案。

## 完整可執行範例

以下是完整程式碼，您可以直接複製、貼上並執行。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a rectangle shape of 200x100 points.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // Step 3: Hide the shape so it does not appear when viewed or printed.
        rectangle.Hidden = true;

        // Step 4: Save the document with the hidden shape.
        string outputPath = @"C:\Temp\HiddenShape.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
        Console.WriteLine("Open the file in Word to verify that the rectangle is hidden.");
    }
}
```

**預期輸出：** 主控台會印出檔案路徑與簡短提醒。當在 Word 中開啟檔案時，除非啟用隱藏文字，否則矩形不會顯示。

## 常見問題與邊緣案例

### 我可以只隱藏輪廓而保留填色嗎？

可以。您可以將 `rectangle.LineFormat.Visible = false`，以隱藏邊框但保留填色，而不是設定 `Hidden = true`。這是 **how to hide shape** 的一種變形，仍保留部分視覺外觀。

### 隱藏旗標在較舊的 Word 版本（2003、2007）是否有效？

隱藏屬性屬於 Word 2007 引入的 Open XML 規範。以舊的二進位 `.doc` 格式儲存的文件不會保留此旗標。若需支援舊版格式，請將文件儲存為 `.docx`，必要時再使用 Aspose.Words 的 `SaveFormat.Doc` 進行轉換。

### 如果需要一次隱藏多個形狀該怎麼做？

遍歷 `Document.GetChildNodes(NodeType.Shape, true)` 集合，對符合條件的每個形狀（例如特定的 `ShapeType` 或自訂的 `AlternativeText` 值）設定 `Hidden = true`。

```csharp
foreach (Shape shp in document.GetChildNodes(NodeType.Shape, true))
{
    if (shp.AlternativeText == "HideMe")
        shp.Hidden = true;
}
```

### 隱藏形狀會對效能產生影響嗎？

隱藏旗標僅會新增一個極小的 XML 屬性，對渲染速度影響不大。然而，若隱藏的物件數量極多，可能會略微增加檔案大小。請移除不需要的形狀，以保持文件精簡。

## 提示與最佳實踐

- **使用有意義的名稱** 為形狀命名，例如 `rectangle.Name = "MyHiddenRectangle"`；這有助於日後在 DOM 中搜尋形狀。  
- **設定 `AlternativeText`** 為自訂標籤（例如 `"HiddenShape"`），可在不依賴索引的情況下定位形狀。  
- **將程式碼包在 try‑catch 區塊**，以優雅地處理授權錯誤或 I/O 例外。  
- **在儲存後釋放 Document**，若在迴圈中處理大量檔案，可釋放非受控資源：`document.Dispose();`。

## 結論

現在您已了解如何使用 C# 在 Word 文件中 **insert rectangle shape**、如何 **hide shape in Word**，以及如何 **create hidden shape**——即使形狀仍屬於文件結構，卻對最終使用者隱形。完整的可執行範例示範了從文件建立到驗證的整個工作流程。

接下來，您可以探索根據使用者輸入 **how to hide shape** 的方式，或將隱藏形狀與內容控制項結合，以實現動態文件產生。此技巧亦可套用於其他形狀類型，如橢圓、箭頭或自訂圖形。

歡迎嘗試不同的尺寸、顏色與可見性設定。若遇到任何問題，請重新檢視上述步驟或參考 Aspose.Words 文件以取得更深入的 API 資訊。祝開發順利！

## 接下來該學什麼？

以下教學涵蓋與本指南緊密相關的主題，建立在已示範的技巧之上。每個資源皆提供完整可運作的程式碼範例與逐步說明，協助您精通更多 API 功能，並在專案中探索替代實作方式。

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}