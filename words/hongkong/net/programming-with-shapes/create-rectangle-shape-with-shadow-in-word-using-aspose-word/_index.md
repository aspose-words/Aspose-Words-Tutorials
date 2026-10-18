---
category: general
date: 2026-03-06
description: 在 Word 中建立矩形形狀，並使用 Aspose.Words 為形狀加入陰影。了解如何在 Word 中插入矩形，以及如何在 C# 中為形狀加入陰影。
draft: false
keywords:
- create rectangle shape
- add shape shadow
- how to insert rectangle in word
- how to add shadow to shape
language: zh-hant
og_description: 在 Word 中建立矩形形狀並使用 Aspose.Words 加上形狀陰影。一步一步的指南，教您如何在 Word 中插入矩形以及如何為形狀添加陰影。
og_title: 使用 Aspose.Words 在 Word 中建立帶陰影的矩形形狀
tags:
- Aspose.Words
- C#
- Word Automation
title: 使用 Aspose.Words 在 Word 中建立帶陰影的矩形形狀
url: /zh-hant/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-word-using-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words 在 Word 中建立帶陰影的矩形形狀

有沒有曾經需要在 Word 文件中**建立矩形形狀**，卻不確定如何讓它看起來更精緻？你並不孤單——大多數開發者在第一次嘗試為自動化文件加入視覺效果時，都會遇到相同的問題。好消息是？使用 Aspose.Words for .NET，你只需幾行 C# 程式碼，就能**建立矩形形狀**並**為形狀加入陰影**。

在本教學中，我們將一步步說明**如何在 Word 中插入矩形**，接著示範**如何為形狀加入陰影**，讓它從頁面中凸顯出來。完成後，你會得到一個可直接儲存的 `Shadow.docx`，在 Word 中開啟即可看到帶有柔和投影的灰色矩形。全程不需要額外的圖檔或手動調整——只要程式碼。

## 你將學到什麼

- 使用 Aspose.Words **建立矩形形狀** 所需的完整 C# 語句。  
- 如何啟用並透過 `Shadow` 物件設定陰影。  
- 各屬性意義（例如 `Transparency`、`Blur`、`Angle`）。  
- 常見陷阱（單位、版本相容性）與快速解決方式。  
- 一個完整、可直接複製貼上的程式範例，今天就能執行。

### 前置條件

- .NET 6+（或 .NET Framework 4.7+）。  
- Aspose.Words for .NET 23.10 或更新版本（NuGet 套件名稱為 `Aspose.Words`）。  
- 具備基本的 C# 與 Visual Studio（或其他 IDE）知識。  

如果已滿足上述條件，讓我們直接開始吧。

---

## 步驟 1：設定專案並匯入命名空間

首先，建立一個新的 Console 應用程式（或使用既有專案），並加入 Aspose.Words NuGet 套件：

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

接著在 `Program.cs` 中加入必要的命名空間：

```csharp
using System.Drawing;               // For Color
using Aspose.Words;                  // Core document classes
using Aspose.Words.Drawing;          // Shape and Shadow types
```

> **小技巧：** 若目標為 .NET 6+，可以啟用全域 `using` 指令，免除在每個檔案中重複寫入這些行。

---

## 步驟 2：在空白 Word 文件中**建立矩形形狀**

我們先建立一個全新的 `Document` 物件，並使用 `DocumentBuilder` 來操作它。`InsertShape` 方法就是魔法發生的地方。

```csharp
// Step 2: Initialize a new document and builder
Document document = new Document();                     // Blank Word file
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle – 200 × 100 points (≈2.78 × 1.39 inches)
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

為什麼是 200 × 100 點？在 Word 中，1 點等於 1/72 英吋，所以矩形大約是 2.8 × 1.4 英吋——足夠顯眼卻不會過於佔空間。你可以自行調整這兩個數值，只要記得它們是以 **點（points）** 為單位，而非像素。

---

## 步驟 3：**為形狀加入陰影** ─ 設定外觀

現在已有矩形，接下來給它加上一層細緻的灰色陰影。`Shadow` 物件屬於 `Shape`，提供多項實用屬性。

```csharp
// Step 3: Turn on the shadow and tweak its appearance
rectangle.Shadow.Enabled = true;               // Switch the shadow on
rectangle.Shadow.Color = Color.Gray;           // Shadow hue
rectangle.Shadow.Transparency = 0.3;           // 30 % transparent – looks softer
rectangle.Shadow.Blur = 5;                     // Blur radius (points)
rectangle.Shadow.Distance = 4;                 // How far the shadow sits from the shape
rectangle.Shadow.Angle = 45;                   // Direction in degrees (45° = down‑right)
rectangle.Shadow.Size = 100;                   // 100 % of the original shape size
```

### 各屬性說明

| Property | Effect | Typical values |
|----------|--------|----------------|
| **Enabled** | 開啟或關閉陰影 | `true` 或 `false` |
| **Color** | 陰影的基礎顏色 | 任意 `System.Drawing.Color` |
| **Transparency** | 透明度 (0 = 實心, 1 = 全透明) | 0.0 – 1.0 |
| **Blur** | 邊緣的柔和程度 | 0 – 10（數值越高越柔和） |
| **Distance** | 形狀與陰影之間的距離 | 0 – 20 點 |
| **Angle** | 光源的方向 | 0 – 360 度 |
| **Size** | 陰影相對於形狀的比例 | 0 – 200 % |

> **為什麼要調整這些設定？**  
> 微調陰影可以讓你符合公司品牌指引（例如使用 20 % 透明度的細緻陰影），而不必依賴外部圖像編輯工具。

---

## 步驟 4：儲存文件並驗證結果

最後，將檔案寫入磁碟。你可以自行決定儲存資料夾，只要把 `YOUR_DIRECTORY` 替換成實際路徑即可。

```csharp
// Step 4: Persist the document
string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

在 Microsoft Word 中開啟 `Shadow.docx`，你應該會看到一個帶有柔和投影、以 45° 角度偏移的灰色矩形。這樣的視覺效果讓形狀彷彿「浮起」於頁面，非常適合用於正式報告或發票等文件。

---

## 完整範例程式

以下是可直接貼到 `Program.cs` 的完整程式碼。所有部份皆完整，編譯後即可執行。

```csharp
using System;
using System.Drawing;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape (200 × 100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // 3️⃣ Enable the shape's shadow and configure its appearance
        rectangle.Shadow.Enabled = true;               // Turn the shadow on
        rectangle.Shadow.Color = Color.Gray;           // Shadow colour
        rectangle.Shadow.Transparency = 0.3;           // 30 % transparent
        rectangle.Shadow.Blur = 5;                     // Blur radius
        rectangle.Shadow.Distance = 4;                 // Offset from the shape
        rectangle.Shadow.Angle = 45;                   // Direction in degrees
        rectangle.Shadow.Size = 100;                   // Shadow size as a percentage

        // 4️⃣ Save the document with the shadowed shape
        string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### 預期輸出

- **檔案：** `Shadow.docx` 會出現在專案的執行目錄。  
- **視覺：** 頁面中央出現一個預設白色填滿的矩形，右下方偏移 4 點的灰色陰影，略帶模糊，呈現自然的立體感。

---

## 常見問題與特殊情況

### 1. 若需要使用其他單位（例如公分）該怎麼辦？

Aspose.Words 以點為單位，但你可以使用以下簡易公式將公分轉換為點：  
`points = centimeters * 28.3465`。

```csharp
double cmWidth = 5.0; // 5 cm
double cmHeight = 2.5; // 2.5 cm
Shape rectCm = builder.InsertShape(ShapeType.Rectangle,
                                   (float)(cmWidth * 28.3465),
                                   (float)(cmHeight * 28.3465));
```

### 2. 舊版 Aspose.Words 能使用嗎？

`Shadow` API 是在 14.0 版首次加入。若使用較舊的版本，請透過 NuGet 進行升級。形狀建立的部分在多個版本中皆相容，基本不會出現破壞性變更。

### 3. 能否為其他形狀（例如圓形）加入陰影？

當然可以──任何 `Shape` 物件都具備 `Shadow` 屬性。只要把 `ShapeType.Rectangle` 換成 `ShapeType.Ellipse`、`ShapeType.Cloud` 等，即可套用相同的陰影設定。

### 4. 若想要彩色陰影（例如品牌藍）該怎麼做？

將 `Color.Gray` 替換成你想要的任何 `Color`：

```csharp
rectangle.Shadow.Color = Color.FromArgb(30, 0, 120); // Dark blue
```

記得同時調整 `Transparency`，避免顏色過於突出。

---

## 🎨 視覺摘要

![使用 Aspose.Words 在 Word 中建立帶陰影的矩形形狀](image-placeholder.png "使用 Aspose.Words 在 Word 中建立帶陰影的矩形形狀")

*Alt text: 使用 Aspose.Words 在 Word 中建立帶陰影的矩形形狀*

此佔位圖示顯示最終文件——僅有矩形與柔和的灰色陰影。

---

## 結論

現在你已掌握如何在 Word 檔案中**建立矩形形狀**、**加入形狀陰影**，並使用 Aspose.Words for .NET 微調每一項視覺細節。這段簡短的程式碼涵蓋了完整工作流程——從

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}