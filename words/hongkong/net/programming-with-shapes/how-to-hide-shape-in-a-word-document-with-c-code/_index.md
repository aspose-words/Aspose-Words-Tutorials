---
category: general
date: 2026-09-14
description: 學習如何使用 C# 隱藏 Word 中的形狀——包括建立 Word 文件的程式碼、插入矩形形狀，以及以程式方式在 Word 中隱藏形狀。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape
- hide shape in word
- create word document code
- insert rectangle shape word
language: zh-hant
lastmod: 2026-09-14
og_description: 在 Word 中使用 C# 隱藏形狀——一步一步的教學，同時示範如何編寫 Word 文件程式碼並插入矩形形狀。
og_image_alt: Word document preview with a visible rectangle shape and a hidden ellipse
  shape
og_title: 如何使用 C# 程式碼在 Word 文件中隱藏形狀
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Learn how to hide shape in Word using C#—including create word document
    code, insert rectangle shape word, and hide shape in word programmatically.
  headline: How to hide shape in a Word document with C# code
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: 如何使用 C# 程式碼在 Word 文件中隱藏圖形
url: /zh-hant/net/programming-with-shapes/how-to-hide-shape-in-a-word-document-with-c-code/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 文件中使用 C# 程式碼隱藏圖形

如果您需要 **how to hide shape** 在 Word 檔案中，本教學提供完整解決方案。您將會看到如何建立 Word 文件、插入矩形圖形、加入橢圓形，並隱藏該橢圓，使開啟檔案時僅顯示矩形。

本指南涵蓋您所需的一切——不需要外部參考，只要程式碼與說明即可。完成後，您即可在任何以程式方式產生的 Word 文件中嵌入隱藏圖形。

## 前置條件

- .NET 6.0 或更新版本（此程式碼亦相容 .NET Framework 4.7+）
- Aspose.Words for .NET（免費試用版或正式授權版）  
  透過 NuGet 安裝：`dotnet add package Aspose.Words`
- 具備基本的 C# 與 Visual Studio（或您慣用的 IDE）知識

## 第一步：設定專案並匯入命名空間

建立一個新的主控台應用程式，並加入必要的 `using` 陳述式。這些匯入讓您能存取 `Document`、`DocumentBuilder` 以及用於操作圖形的繪圖類別。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The rest of the code follows in the next steps
        }
    }
}
```

**Why this matters** – 匯入正確的命名空間可避免編譯錯誤，並讓 API 可用於圖形建立與可見性控制。

## 第二步：建立新 Word 文件與 Builder

`Document` 代表檔案本身，而 `DocumentBuilder` 提供流暢的 API 以加入內容。這是首次應用 **how to hide shape** 邏輯的地方：在任何圖形存在之前，必須先有文件的上下文。

```csharp
// Step 2: Create a new blank document and a builder to edit it
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);
```

**Explanation** – `Document` 物件起始為空白。`DocumentBuilder` 會定位於第一段落的開頭，準備插入圖形或文字。

## 第三步：插入可見的矩形圖形

矩形將是文件開啟時仍然可見的圖形。您可以直接透過圖形物件控制其大小、位置與格式。

```csharp
// Step 3: Insert a visible rectangle shape and position it
Shape visibleRectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
visibleRectangle.Left = 50;                 // 50 points from the left margin
visibleRectangle.Top = 100;                 // 100 points from the top of the page
visibleRectangle.FillColor = System.Drawing.Color.LightBlue;
visibleRectangle.LineColor = System.Drawing.Color.DarkBlue;
```

**Why this step** – 新增矩形示範了 **insert rectangle shape word** 的需求。設定 `FillColor` 與 `LineColor` 可讓圖形在最終文件中更易辨識。

## 第四步：插入橢圓形並隱藏它

現在加入您想要隱藏的圖形。`Hidden` 屬性告訴 Word 在 UI 中不渲染此圖形，雖然它仍是文件結構的一部份。

```csharp
// Step 4: Insert an ellipse shape, position it, and hide it from view
Shape hiddenEllipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
hiddenEllipse.Left = 200;      // Position away from the rectangle
hiddenEllipse.Top = 100;
hiddenEllipse.Hidden = true;   // This flag implements how to hide shape
```

**Explanation** – 設定 `Hidden = true` 即為 **hide shape in word** 的核心。Word 於一般檢視與列印時會遵守此旗標，但若需要仍可透過程式碼存取該圖形。

## 第五步：儲存文件

最後，將文件寫入磁碟。選擇您有寫入權限的資料夾，並為檔案命名，以清楚說明本教學的目的。

```csharp
// Step 5: Save the document with both shapes
string outputPath = @"C:\Temp\ShapeVisibility.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

**Result** – 在 Microsoft Word 中開啟 `ShapeVisibility.docx` 後，只會看到淡藍色的矩形。隱藏的橢圓不會出現，證明您已成功掌握 **how to hide shape** 在 Word 檔案中的技巧。

## 完整可執行範例

將所有程式碼片段組合，即可得到一個完整、可執行的程式：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a new document and builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert a visible rectangle
            Shape visibleRectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            visibleRectangle.Left = 50;
            visibleRectangle.Top = 100;
            visibleRectangle.FillColor = System.Drawing.Color.LightBlue;
            visibleRectangle.LineColor = System.Drawing.Color.DarkBlue;

            // Insert a hidden ellipse
            Shape hiddenEllipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
            hiddenEllipse.Left = 200;
            hiddenEllipse.Top = 100;
            hiddenEllipse.Hidden = true; // hides the shape

            // Save the document
            string outputPath = @"C:\Temp\ShapeVisibility.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### 預期輸出

- **視覺**：開啟 `ShapeVisibility.docx` 時，會看到一個位於左邊距附近的淡藍色矩形。橢圓不會顯示。
- **程式化**：隱藏的橢圓仍存在於文件的 XML（`<w:drawing>` 元素）中，且帶有 `w:hidden` 屬性。您可將檔案當作 zip 開啟，檢查 `document.xml` 以驗證。

## 常見問題與邊緣情況

| 問題 | 解答 |
|----------|--------|
| *我可以隱藏多個圖形嗎？* | 可以。對每個想要隱藏的圖形設定 `Hidden = true` 即可。 |
| *隱藏的圖形會列印嗎？* | 預設情況下 Word 不會列印隱藏物件。如需列印，請在列印前清除 `Hidden` 旗標。 |
| *舊版 Word 是否支援此隱藏屬性？* | `Hidden` 屬性屬於 Office Open XML 標準，支援 Word 2007 及之後的版本。 |
| *如果需要在執行時切換可見性該怎麼做？* | 透過 `document.GetChildNodes(NodeType.Shape, true)` 取得圖形，然後依需求切換 `Hidden` 屬性。 |

## 專業小技巧

- **效能**：若大量產生文件，請重複使用同一個 `DocumentBuilder` 實例，而非為每個檔案重新建立。
- **版本控制**：將產生的 `.docx` 檔案存放於受版本控制的資料夾；隱藏圖形可作為下游處理的中繼資料標記。
- **測試**：使用 Aspose.Words 將 DOCX 轉為 PDF（`document.Save("out.pdf")`）以自動化快速視覺測試。PDF 也會隱藏橢圓，證明隱藏旗標會在格式轉換中傳遞。

## 結論

您現在已了解如何在 Word 文件中使用 C# **how to hide shape**。本教學示範了建立文件、**insert rectangle shape word**、加入橢圓，並套用 `Hidden` 旗標以實現 **hide shape in word** 的行為。透過完整可執行的程式碼，您可以將隱藏圖形整合至任何自動化報表或範本工作流程。

### 後續步驟

- 探索其他圖形屬性，如旋轉、陰影與文字環繞。  
- 結合隱藏圖形與自訂文件屬性，以嵌入機器可讀的資料。  
- 研究 **create word document code** 的範例，了解表格、圖表與內容控制項的產生方式，擴充您的自動化工具箱。

盡情嘗試不同的圖形類型與可見性設定——您的下一個 Word 自動化專案只差幾行程式碼！

## 接下來該學什麼？

以下教學與本指南緊密相關，能進一步深化您所學的技巧。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您掌握更多 API 功能，並在專案中探索替代實作方式。

- [使用 C# 在 Word 中建立矩形圖形 – 步驟說明指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [建立帶陰影矩形的空白 Word 文件 – 步驟說明指南](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words 圖形陰影教學 – 在 C# 中為 Word 圖形加入陰影](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}