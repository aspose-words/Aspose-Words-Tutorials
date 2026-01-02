---
category: general
date: 2026-01-02
description: 使用 Aspose.Words 建立 Word 文件，加入矩形形狀、設定形狀填充顏色，並儲存為 docx 檔案。學習如何在幾分鐘內建立帶陰影的矩形。
draft: false
keywords:
- create word document
- add rectangle shape
- set shape fill color
- save docx file
- how to create rectangle
language: zh-hant
og_description: 建立 Word 文件，加入自訂矩形，設定填色、加入陰影，並儲存為 DOCX。完整程式碼與說明。
og_title: 建立帶有矩形形狀的 Word 文件 – 逐步說明
tags:
- Aspose.Words
- C#
- Document Generation
title: 建立帶有矩形形狀與陰影的 Word 文件 – 完整指南
url: /zh-hant/net/programming-with-shapes/create-word-document-with-rectangle-shape-and-shadow-complet/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 建立含矩形形狀與陰影的 Word 文件 – 完整指南

有沒有想過如何 **create word document**（建立 Word 文件），在裡面加入一個設計精美的矩形？也許你需要一個用來放置標誌的佔位格、彩色橫幅，或僅僅在報告中提供視覺提示。在本教學中，我們將 **add rectangle shape**（加入矩形形狀），設定填色，套用細緻的陰影，最後 **save docx file**（儲存 docx 檔）— 全部使用 Aspose.Words for .NET。

你將得到一段可直接執行的 C# 程式碼片段、每一行的清晰說明，以及一些可在自己專案中重複使用的技巧。沒有冗長說明，只有實用的解決方案，讓你直接 copy‑paste。

## 需要的環境

- .NET 6 或更新版本（此程式碼亦可於 .NET Framework 上執行）  
- Visual Studio 2022（或任何你喜歡的編輯器）  
- **Aspose.Words** NuGet 套件 (`Install-Package Aspose.Words`)  

如果你已經具備上述條件，太好了 – 讓我們開始吧。

## 步驟 1 – 初始化新文件 (How to create word document)

首先，你需要在記憶體中 **create word document**。可以把它想像成打開一張空白畫布，之後再在上面繪製矩形。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // for Color struct

// Create a fresh, empty document
Document document = new Document();

// DocumentBuilder helps us add content step‑by‑step
DocumentBuilder builder = new DocumentBuilder(document);

// Write a simple heading so you can see something when you open the file
builder.Writeln("Shadow Demo");
```

> **Why this matters:** `Document` 代表整個 DOCX 檔案，而 `DocumentBuilder` 是一個方便的輔助工具，讓你可以插入文字、表格、圖片與形狀，而不必手動處理底層的節點樹。

## 步驟 2 – 插入矩形形狀 (Add rectangle shape)

現在我們將 **add rectangle shape** 到文件中。`InsertShape` 方法接受形狀類型以及以點為單位的尺寸（1 點 = 1/72 英吋）。

```csharp
// Insert a rectangle that will later receive a custom shadow
Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);

// Give the rectangle a light‑blue background so it stands out
rect.FillColor = Color.LightBlue;
```

> **Pro tip:** 若需要建立其他幾何形狀（橢圓、三角形等），只要將 `ShapeType.Rectangle` 改成相應的列舉值即可。

## 步驟 3 – 設定陰影 (Set shape fill color & shadow)

陰影可以讓平面的形狀看起來更具立體感。此處我們啟用陰影並微調其外觀。

```csharp
// Turn the shadow on
rect.ShadowFormat.Enabled = true;

// Choose a subtle gray for the shadow color
rect.ShadowFormat.Color = Color.Gray;

// Blur softens the edge of the shadow – 8 points looks nice
rect.ShadowFormat.BlurRadius = 8;

// Distance controls how far the shadow is offset from the shape
rect.ShadowFormat.Distance = 5;

// Angle determines the direction; 45° gives a bottom‑right offset
rect.ShadowFormat.Angle = 45;

// Transparency makes the shadow partially see‑through (0 = opaque, 1 = invisible)
rect.ShadowFormat.Transparency = 0.3; // 30 % transparent
```

> **Why these values?** 適度的模糊半徑與 5 點的距離可避免陰影蓋過形狀，而 45° 則模擬光源從左上方射入——這是常見的 UI 慣例。

## 步驟 4 – 儲存文件 (Save docx file)

最後，我們將 **save docx file** 至磁碟。請依你的環境調整路徑。

```csharp
// Replace with the folder you actually want to use
string outputPath = @"C:\Temp\ShadowDemo.docx";

// Persist the document as a .docx file
document.Save(outputPath);
```

當你在 Word 中開啟 `ShadowDemo.docx` 時，應該會看到一個淡藍色的矩形，帶有柔和的灰色陰影，就如下方截圖所示。

![建立含矩形形狀與陰影的 Word 文件](https://example.com/images/rectangle-shadow.png "建立含矩形形狀與陰影的 Word 文件")

*圖片說明文字:* **Create Word Document** 顯示帶陰影的矩形形狀。

## 完整、可直接執行的範例 (How to create rectangle and save)

將所有步驟整合起來，以下是完整程式碼，你可以直接複製到 Console 應用程式中：

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace AsposeRectangleDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 1: Initialize the document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);
            builder.Writeln("Shadow Demo");

            // Step 2: Insert the rectangle
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
            rect.FillColor = Color.LightBlue;   // set shape fill color

            // Step 3: Apply shadow formatting
            rect.ShadowFormat.Enabled = true;
            rect.ShadowFormat.Color = Color.Gray;
            rect.ShadowFormat.BlurRadius = 8;
            rect.ShadowFormat.Distance = 5;
            rect.ShadowFormat.Angle = 45;
            rect.ShadowFormat.Transparency = 0.3;

            // Step 4: Save the file
            string output = @"C:\Temp\ShadowDemo.docx";
            doc.Save(output);

            System.Console.WriteLine($"Document saved to {output}");
        }
    }
}
```

### 預期結果

- 目標資料夾中會出現名為 **ShadowDemo.docx** 的檔案。  
- 在 Microsoft Word 中開啟它時，會看到單一頁面，文字 “Shadow Demo” 之後是一個淡藍色的矩形。  
- 該矩形在 45° 角度投射出柔和的灰色陰影，呈現輕微的 3D 效果。

## 常見問題與邊緣情況

### 如果需要不同尺寸呢？

只要將 `InsertShape` 中的 `200, 100` 參數改成其他值即可。這兩個數字分別代表寬度與高度（單位為點）。若要正方形，使用相同的數值即可。

### 要如何讓陰影更明顯？

增加 `BlurRadius` 可得到更平滑的邊緣，提升 `Distance` 會使偏移距離變大，或降低 `Transparency`（例如 `0.1`）讓陰影變得更深。

### 如何為矩形加入邊框？

```csharp
rect.LineColor = Color.DarkBlue;   // border color
rect.LineWidth = 2;                // thickness in points
```

### 這是否相容於較舊版本的 Aspose.Words？

是的。`ShadowFormat` 類別自 2020 年初的版本起即已存在。若你使用的是非常舊的版本，可能需要升級才能使用所有屬性。

## 提示與陷阱

- **Pro tip:** 完成後務必釋放大型文件（`doc.Dispose()`），尤其在 Web 應用程式中，以釋放原生資源。  
- **Watch out for:** 使用相對路徑且未取得適當權限可能導致 `UnauthorizedAccessException`。建議使用絕對路徑或確保應用程式池具備寫入權限。  
- **Remember:** `FillColor` 屬性接受任何 `System.Drawing.Color`。可自行使用 `Color.FromArgb(255, 173, 216, 230)` 來取得自訂的柔和色調。

## 往後的步驟

現在你已了解如何 **create word document**、**add rectangle shape**、**set shape fill color**，以及 **save docx file**，可以進一步嘗試以下操作：

- 插入多個形狀，並使用 `RelativeHorizontalPosition` 與 `RelativeVerticalPosition` 進行排列。  
- 使用 `Shape.TextBox` 結合文字為矩形加上說明文字。  
- 將相同文件匯出為 PDF（`doc.Save("output.pdf")`）以便分發。

如果你對更進階的圖形感興趣，可參考 Aspose.Words 對 **WordArt**、**charts** 與 **inline images** 的支援。它們的使用方式相同：建立節點、設定屬性，最後儲存。

---

### TL;DR

- 使用 `Document` 與 `DocumentBuilder` 來 **create word document**。  
- 呼叫 `InsertShape(ShapeType.Rectangle, …)` 以 **add rectangle shape**。  
- 設定 `FillColor` 以取得想要的背景色。  
- 啟用 `ShadowFormat` 並微調其屬性，以獲得精緻外觀。  
- 最後以 `document.Save("yourPath.docx")` **save docx file**。

祝開發順利，盡情讓你的 Word 檔案更具風格吧！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}