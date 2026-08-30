---
category: general
date: 2026-08-17
description: 如何使用 Aspose.Words 在 Word 文件中加入 ActiveX 控制項並插入圓餅圖。將切片突出顯示並以 DOCX 格式儲存，簡單幾步完成。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert pie chart
- save as docx
- how to insert chart
- explode pie slice
language: zh-hant
lastmod: 2026-08-17
og_description: 如何在 Aspose.Words 中加入 ActiveX 控制項、插入圓餅圖、將切片分離，並儲存為 DOCX – 完整逐步指南.
og_image_alt: Screenshot of a Word document showing an ActiveX button and a pie chart
  with an exploded slice
og_title: 如何在 Word 文件中加入 ActiveX 並插入圓餅圖
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: How to add ActiveX controls and insert a pie chart in a Word doc using
    Aspose.Words. Explode a slice and save as DOCX in a few steps.
  headline: How to add ActiveX and insert a pie chart in a Word doc
  type: TechArticle
tags:
- Aspose.Words
- ActiveX
- Chart
- DOCX
title: 如何在 Word 文件中加入 ActiveX 並插入圓餅圖
url: /zh-hant/java/using-document-elements/how-to-add-activex-and-insert-a-pie-chart-in-a-word-doc/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 文件中加入 ActiveX 並插入圓形圖表

如果您需要 **how to add ActiveX** 控制項並在 Word 文件中嵌入圖表，本教學將展示完整且可執行的解決方案。使用 Aspose.Words 您可以放置 ActiveX CommandButton、建立圓形圖表、將切片突出顯示，最後只需幾行 C# 程式碼即可 **save as DOCX**。

在以下各節中，您將看到所有必需的匯入、完整的程式碼清單，以及每一步驟重要性的說明。完成後，您將能夠在任何以程式方式產生的 .docx 檔案中整合互動控制項與視覺化資料。

## 前置條件

在開始之前，請確保您已具備：

* .NET 6.0 或更新版本（此程式碼亦相容於 .NET Framework 4.7+）
* Aspose.Words for .NET 套件（可透過 NuGet 取得）
* 如 Visual Studio 2022 或 VS Code 等開發環境
* 基本的 C# 與 Word 物件模型知識

不需要額外的第三方圖表函式庫——Aspose.Words 已內建圖表建立功能。

## 使用 Aspose.Words 新增 ActiveX 控制項

ActiveX 控制項讓您能直接在 Word 檔案中嵌入互動式 UI 元素。本指南示範如何加入一個 **CommandButton**，之後可連結至 VBA 程式碼。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Step 2: Insert a group shape to hold the ActiveX control
GroupShape groupShape = builder.InsertGroupShape();

// Step 3: Insert a rectangle shape, hide it, and attach it to the group
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
groupShape.AppendChild(rectangleShape);
rectangleShape.SetHidden(true);

// Step 4: Insert a plain‑text StructuredDocumentTag (optional placeholder)
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");

// Step 5: Insert the CommandButton ActiveX control
Forms2OleControl commandButton = builder.InsertForms2OleControl();
commandButton.SetActiveXControlType(Forms2OleControlType.CommandButton);
commandButton.SetCaption("Click Me");

// The CommandButton now appears in the document and can be used in VBA macros.
```

**為什麼這樣可行：**  
`InsertForms2OleControl` 會建立一個 OLE 容器，Word UI 會將其辨識為 ActiveX 控制項。將控制項類型設定為 `CommandButton` 並給予標題，即可在使用者開啟檔案時呈現為一般按鈕。

## 插入圓形圖表並突出顯示切片

圖表可在不離開文件的情況下呈現資料視覺化。以下步驟示範 **how to insert chart**，特別是將第一個切片突顯的 **pie chart**。

```csharp
// Step 6: Insert a pie chart (400 × 300 points)
Chart pieChart = (Chart)builder.InsertChart(ChartType.Pie, 400, 300);

// Populate the chart with sample data
pieChart.Series.Clear();
ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                          new[] { 12000, 15000, 9000, 13000 });

// Step 7: Explode the first slice for emphasis
series.SetExplode(0, true);

// Optional: Customize colors or labels here if needed
```

**為什麼要突顯切片：**  
呼叫 `SetExplode(0, true)` 會指示 Aspose.Words 將第一個資料點偏移，將讀者的目光引向該區段。這是簡報中常用的強調關鍵數值的技巧。

## Save as DOCX

在加入 ActiveX 按鈕與圖表後，將文件寫入磁碟。本步驟示範使用標準方法 **save as DOCX**。

```csharp
// Step 8: Save the document in DOCX format
document.Save("Output.docx", SaveFormat.Docx);
```

檔案 `Output.docx` 現在包含互動按鈕、帶有突顯切片的圓形圖表，且可在 Microsoft Word 中直接開啟，無需額外外掛。

## 完整可執行範例

將所有內容整合在一起，以下是一個可直接複製到主控台應用程式並立即執行的自包含程式。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert group shape and hidden rectangle (required for ActiveX positioning)
        GroupShape group = builder.InsertGroupShape();
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        group.AppendChild(rect);
        rect.SetHidden(true);

        // Optional placeholder tag
        builder.InsertStructuredDocumentTag(StructuredDocumentTagType.PlainText, "MyTag");

        // Insert CommandButton ActiveX control
        Forms2OleControl button = builder.InsertForms2OleControl();
        button.SetActiveXControlType(Forms2OleControlType.CommandButton);
        button.SetCaption("Click Me");

        // Insert pie chart and explode first slice
        Chart chart = (Chart)builder.InsertChart(ChartType.Pie, 400, 300);
        chart.Series.Clear();
        ChartSeries series = chart.Series.Add("Revenue", new[] { "Jan", "Feb", "Mar" },
                                               new[] { 5000, 7000, 3000 });
        series.SetExplode(0, true); // explode pie slice

        // Save the document
        doc.Save("Output.docx", SaveFormat.Docx);

        Console.WriteLine("Document created successfully: Output.docx");
    }
}
```

**預期結果：**  
在 Word 中開啟 `Output.docx` 後，會看到標示為 *Click Me* 的按鈕，以及第一個切片（January）相對於其他切片偏移的圓形圖表。按鈕已可供 VBA 事件處理使用，圖表則可使用 Word 內建的圖表工具進行編輯。

## 常見問題與邊緣案例

* **我可以加入其他 ActiveX 類型嗎？**  
  可以。將 `Forms2OleControlType.CommandButton` 替換為 `Forms2OleControlType` 列舉中的任意值（例如 `CheckBox`、`OptionButton`）。插入方式相同。

* **如果我要使用不同的圖表類型該怎麼做？**  
  在 `InsertChart` 呼叫中使用 `ChartType.Bar`、`ChartType.Line` 等列舉值。**how to insert chart** 的步驟保持不變，僅列舉值不同。

* **如何控制突顯切片的大小？**  
  Aspose.Words 目前僅支援二元的突顯旗標（true/false）。若需更細緻的控制（例如偏移距離），必須在儲存後編輯底層的 OOXML。

* **此文件與較舊的 Word 版本相容嗎？**  
  儲存為 DOCX 可確保與 Word 2007 及之後版本相容。若需支援 Word 2003，可改為 `SaveFormat.Doc`，但該格式對 ActiveX 的支援有限。

* **需要引用 `System.Drawing` 嗎？**  
  不需要。所有繪圖物件皆由 Aspose.Words 提供，唯一必須的 NuGet 套件即為 `Aspose.Words`。

## 結論

您現在已掌握 **how to add ActiveX**、**insert a pie chart**、**explode a pie slice**，以及使用 Aspose.Words for .NET **save as DOCX** 的完整流程。此完整範例涵蓋從文件建立到最終儲存的每一步，並說明每個 API 呼叫背後的原理。

接下來，您可以探索：

* 為 CommandButton 點擊事件加入 VBA 巨集（**how to insert chart** 並自動更新資料）
* 客製化圖表外觀（顏色、資料標籤）以符合企業品牌
* 嵌入其他 ActiveX 控制項，如 **ComboBox** 或 **ListBox**，打造更豐富的表單

歡迎自行實驗程式碼、替換範例資料，並將此解決方案整合到您自己的文件產生流程中。祝開發順利！

## 接下來該學什麼？

以下教學與本指南所示技術緊密相關，提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能並探索替代實作方式。

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert a Simple Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Insert a Bubble Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}