---
category: general
date: 2025-12-08
description: 使用 Aspose.Words 快速為圖形添加陰影。了解如何使用 Aspose 建立 Word 文件、如何為圖形添加陰影，以及如何在 C#
  中套用陰影透明度。
draft: false
keywords:
- add shadow to shape
- create word document using aspose
- how to add shape shadow
- apply shadow transparency
language: zh-hant
og_description: 使用 Aspose.Words 為 Word 檔案中的形狀添加陰影。本分步指南展示如何建立文件、加入形狀以及套用陰影透明度。
og_title: 為形狀添加陰影 – Aspose.Words C# 教程
tags:
- Aspose.Words
- C#
- Word Automation
title: 在 Word 文件中為圖形添加陰影 – 完整 Aspose.Words 指南
url: /hongkong/net/images-and-shapes/add-shadow-to-shape-in-a-word-document-complete-aspose-words/
---

{{< layout-start >}}

{{< layout-start >}}

# 為圖形新增陰影 – 完整 Aspose.Words 教學

是否曾想在 Word 檔案中 **為圖形新增陰影**，卻不確定要使用哪個 API 呼叫？你並不孤單。許多開發者在第一次嘗試為矩形或任何繪圖元素加上適當的投影時，常會卡關，尤其是使用 Aspose.Words for .NET 時。

在本教學中，我們將一步步說明你需要的全部知識：從 **使用 Aspose 建立 Word 文件** 到設定陰影、調整模糊度、距離、角度，甚至 **套用陰影透明度**。完成後，你將擁有一個可直接執行的 C# 程式，產生帶有柔和陰影矩形的 `.docx` 檔案——不需要在 Word 中手動調整。

---

## 你將學到什麼

- 如何在 Visual Studio 中建立 Aspose.Words 專案。  
- **使用 Aspose 建立 Word 文件** 並插入圖形的完整步驟。  
- **如何為圖形新增陰影**，並完整控制模糊度、距離、角度與透明度。  
- 常見問題的排除技巧（例如授權遺失、單位錯誤）。  
- 一段完整、可直接複製貼上的程式碼範例，讓你今天就能執行。

> **先備條件：** .NET 6+（或 .NET Framework 4.7.2+）、有效的 Aspose.Words 授權（或免費試用版），以及對 C# 的基本認識。

---

## 第一步 – 設定專案並加入 Aspose.Words

首先，開啟 Visual Studio，建立一個新的 **Console App (.NET Core)**，然後加入 Aspose.Words NuGet 套件：

```bash
dotnet add package Aspose.Words
```

> **小技巧：** 若你有授權檔 (`Aspose.Words.lic`)，請將它複製到專案根目錄，並在程式啟動時載入。這樣可避免在免費評估模式下出現浮水印。

```csharp
// Load the license (optional but recommended)
var license = new Aspose.Words.License();
license.SetLicense("Aspose.Words.lic");
```

---

## 第二步 – 建立新的空白文件

現在我們實際 **使用 Aspose 建立 Word 文件**。此物件將作為圖形的畫布。

```csharp
// Step 2: Initialize a new blank document
Document doc = new Document();   // Represents an empty .docx file
```

`Document` 類別是所有其他功能的入口點——段落、節，當然還有繪圖物件。

---

## 第三步 – 插入矩形圖形

文件準備好後，我們即可加入圖形。這裡選擇一個簡單的矩形，其他形狀（圓形、線條或自訂多邊形）同樣適用相同的邏輯。

```csharp
// Step 3: Create a rectangular shape that will hold the shadow
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width  = 150,   // Width in points (1 point = 1/72 inch)
    Height = 100    // Height in points
};
```

> **為什麼要使用圖形？** 在 Aspose.Words 中，`Shape` 物件可以容納文字、圖片，或僅作為裝飾元素。為圖形加入陰影遠比操作圖片框來得簡單。

---

## 第四步 – 設定陰影（Add Shadow to Shape）

這是本教學的核心——**如何為圖形新增陰影** 並微調外觀。`ShadowFormat` 屬性讓你完全掌控。

```csharp
// Step 4: Enable the shadow and configure its appearance
rectangle.ShadowFormat.Visible       = true;   // Turn the shadow on
rectangle.ShadowFormat.Blur          = 5.0;    // Blur radius – higher = softer edges
rectangle.ShadowFormat.Distance      = 3.0;    // Offset distance from the shape
rectangle.ShadowFormat.Angle         = 45;     // Direction in degrees (0 = right, 90 = down)
rectangle.ShadowFormat.Transparency  = 0.3;    // 30 % transparent – this is how we **apply shadow transparency**
```

### 各屬性說明

| Property | Effect | Typical Values |
|----------|--------|----------------|
| **Visible** | 開啟或關閉陰影。 | `true` / `false` |
| **Blur** | 使陰影邊緣變得柔和。 | `0`（硬）到 `10`（非常柔） |
| **Distance** | 將陰影從圖形向外移動的距離。 | 常見為 `1`–`5` 點 |
| **Angle** | 控制偏移的方向。 | `0`–`360` 度 |
| **Transparency** | 讓陰影呈現半透明。 | `0`（不透明）到 `1`（完全透明） |

> **邊緣情況：** 若將 `Transparency` 設為 `1`，陰影會完全消失——可用於程式中動態切換。

---

## 第五步 – 將圖形加入文件

現在把圖形附加到文件正文的第一個段落。若文件中尚未有段落，Aspose 會自動建立。

```csharp
// Step 5: Append the shape to the first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(rectangle);
```

如果你的文件已經有內容，也可以使用 `InsertAfter` 或 `InsertBefore` 在任意節點插入圖形。

---

## 第六步 – 儲存文件

最後，將檔案寫入磁碟。你可以選擇任何支援的格式（`.docx`、`.pdf`、`.odt` 等），但本教學仍以原生 Word 格式為例。

```csharp
// Step 6: Save the document with the shadowed shape
string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowedShape.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

開啟產生的 `ShadowedShape.docx`，你會看到一個帶有柔和、45 度、透明度 30 % 的矩形——正是我們剛剛設定的效果。

---

## 完整可執行範例

以下是 **完整、可直接複製貼上** 的程式碼，已整合上述所有步驟。將它存為 `Program.cs`，然後以 `dotnet run` 執行。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // OPTIONAL: Load Aspose.Words license (remove if using trial)
        // -------------------------------------------------
        try
        {
            var license = new License();
            license.SetLicense("Aspose.Words.lic");
        }
        catch (Exception ex)
        {
            Console.WriteLine("License not found – running in evaluation mode: " + ex.Message);
        }

        // -------------------------------------------------
        // 1. Create a new blank document
        // -------------------------------------------------
        Document doc = new Document();

        // -------------------------------------------------
        // 2. Insert a rectangle shape
        // -------------------------------------------------
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width  = 150,
            Height = 100
        };

        // -------------------------------------------------
        // 3. Configure the shadow – this is where we **add shadow to shape**
        // -------------------------------------------------
        rectangle.ShadowFormat.Visible      = true;   // Show the shadow
        rectangle.ShadowFormat.Blur         = 5.0;    // Soft edges
        rectangle.ShadowFormat.Distance     = 3.0;    // Offset distance
        rectangle.ShadowFormat.Angle        = 45;     // Direction in degrees
        rectangle.ShadowFormat.Transparency = 0.3;    // 30 % transparent (apply shadow transparency)

        // -------------------------------------------------
        // 4. Add the shape to the document
        // -------------------------------------------------
        doc.FirstSection.Body.FirstParagraph.AppendChild(rectangle);

        // -------------------------------------------------
        // 5. Save the file
        // -------------------------------------------------
        string outFile = Path.Combine(Environment.CurrentDirectory, "ShadowedShape.docx");
        doc.Save(outFile);
        Console.WriteLine($"Document created successfully: {outFile}");
    }
}
```

**預期結果：** 產生名為 `ShadowedShape.docx` 的檔案，內含一個帶有細緻、半透明、45° 角度投影的矩形。

---

## 變化與進階技巧

### 更改陰影顏色

預設情況下，陰影會繼承圖形的填色，但你也可以自行指定顏色：

```csharp
rectangle.ShadowFormat.Color = System.Drawing.Color.Gray;
```

### 多個圖形搭配不同陰影

若需要多個圖形，只要重複建立與設定的步驟即可。若日後要引用，記得為每個圖形設定唯一名稱。

### 匯出為 PDF 並保留陰影

Aspose.Words 在儲存為 PDF 時會保留陰影效果：

```csharp
doc.Save("ShadowedShape.pdf");
```

### 常見問題

| 症狀 | 可能原因 | 解決方式 |
|------|----------|----------|
| 陰影不顯示 | `ShadowFormat.Visible` 為 `false` | 設為 `true`。 |
| 陰影太硬 | `Blur` 設為 `0` | 將 `Blur` 提升至 3–6。 |
| PDF 中陰影消失 | 使用舊版 Aspose.Words (< 22.9) | 升級至最新版本。 |

---

## 結論

我們已完整說明 **如何使用 Aspose.Words 為圖形新增陰影**，從文件初始化到微調模糊度、距離、角度，以及 **套用陰影透明度**。完整範例展示了乾淨、可投入生產環境的作法，且可依需求套用於任何圖形或文件版面。

對於更複雜的情境（例如帶陰影的表格或動態資料驅動的圖形）有任何疑問，歡迎在下方留言，或參考 Aspose.Words 圖片處理與段落格式化的相關教學。

祝開發順利，讓你的 Word 文件更添視覺魅力！

--- 

![add shadow to shape example](shadowed_shape.png "add shadow to shape example")

{{< layout-end >}}

{{< layout-end >}}