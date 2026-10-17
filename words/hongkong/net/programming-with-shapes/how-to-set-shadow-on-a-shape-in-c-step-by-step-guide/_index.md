---
category: general
date: 2026-04-10
description: 如何在 C# 中為形狀設定陰影 – 學習如何套用投影陰影、變更透明度、調整模糊程度，以及使用 Aspose.Words 為形狀添加陰影。
draft: false
keywords:
- how to set shadow
- apply drop shadow
- how to change transparency
- how to adjust blur
- add shape shadow
language: zh-hant
og_description: 如何在 C# 中為形狀設定陰影 – 本教學示範如何套用投影、變更透明度、調整模糊，並以清晰的程式碼範例加入形狀陰影。
og_title: 如何在 C# 中為形狀設定陰影 – 完整指南
tags:
- Aspose.Words
- C#
- Document Automation
title: 如何在 C# 中為形狀設定陰影 – 逐步指南
url: /zh-hant/net/programming-with-shapes/how-to-set-shadow-on-a-shape-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 中為形狀設定陰影 – 完整指南

有沒有想過在程式化建立 Word 文件時，**如何為形狀設定陰影**？你並不孤單。許多開發者在需要為文字方塊、標誌或說明框加入細緻的投影時，常會卡關，而 API 文件又顯得有點薄弱。  

在本教學中，我們將逐步說明完整流程：從載入 `.docx`、取得第一個 `Shape`、套用投影、微調透明度、調整模糊半徑，最後將位置調整到恰當。完成後，你將擁有一段可重用的程式碼片段，適用於 Aspose.Words .NET 2023 及更新版本，並且了解每個屬性為何重要。

## 需要的環境

- **Aspose.Words for .NET**（NuGet 套件 `Aspose.Words`）– 提供 `Document`、`Shape` 與 `ShadowFormat` 類別的函式庫。  
- **.NET 6+**（或 .NET Framework 4.7.2）– 任意近期的執行環境皆可。  
- 一個簡單的 Word 檔案（`input.docx`），內含至少一個形狀，例如文字方塊。  
- Visual Studio、VS Code 或你喜愛的 IDE。

就這樣。無需額外第三方工具、無 COM interop，純粹使用 C#。

![設定陰影範例](image-placeholder.png){:alt="在 Word 文件中為形狀設定陰影"}

## 設定陰影概述

**設定陰影** 的核心概念是操作附屬於 `Shape` 的 `ShadowFormat` 物件。可以把 `ShadowFormat` 想像成陰影的微型「樣式表」：它告訴渲染器陰影是否可見、顏色為何、透明度、模糊程度，以及相對於形狀的位置。  

以下是*完整*可執行的程式範例。隨意將它貼到 console 應用程式中，按 **F5**，即可在儲存的 `output.docx` 中看到陰影效果。

```csharp
using System;
using System.Drawing;               // For Color
using Aspose.Words;                 // Core document classes
using Aspose.Words.Drawing;         // Shape & ShadowFormat

class ShadowDemo
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1: Load the Word document that contains the shape.
        // -------------------------------------------------
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // -------------------------------------------------
        // Step 2: Retrieve the first shape (e.g., a textbox) from the document.
        // -------------------------------------------------
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found – make sure input.docx has a textbox.");
            return;
        }

        // -------------------------------------------------
        // Step 3: Make the shadow visible.
        // -------------------------------------------------
        shape.ShadowFormat.Visible = true;

        // -------------------------------------------------
        // Step 4: Set the shadow colour to a dark gray.
        // -------------------------------------------------
        shape.ShadowFormat.Color = Color.DarkGray;

        // -------------------------------------------------
        // Step 5: Define the shadow's transparency (30 % transparent).
        // -------------------------------------------------
        shape.ShadowFormat.Transparency = 0.3;   // 0 = opaque, 1 = fully transparent

        // -------------------------------------------------
        // Step 6: Configure the blur radius (size) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Size = 6;            // Larger value = softer edges

        // -------------------------------------------------
        // Step 7: Set the offset distance and direction (angle) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Distance = 2;        // How far the shadow is from the shape
        shape.ShadowFormat.Angle = 45;          // Angle in degrees (0 = right, 90 = down)

        // -------------------------------------------------
        // Save the modified document.
        // -------------------------------------------------
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Shadow applied successfully! Check output.docx.");
    }
}
```

### 為何這些設定很重要

- **Visible** – 若未開啟此旗標，其他所有屬性皆會被忽略。  
- **Color** – 深灰色模擬一般 UI 的投影；你可以替換成任意 `Color`。  
- **Transparency** – 0.3 可呈現*柔和*外觀，同時保持形狀可辨識。  
- **Size** – 控制模糊程度；數值 6 通常足以達到專業感。  
- **Distance & Angle** – 兩者共同決定*偏移*；2 pt、45° 產生細緻的對角投影。  

這就是 **設定陰影** 的要點。接下來，我們會逐一說明每個部分，讓你能分別**套用投影**、**變更透明度**、**調整模糊**，以及**為形狀加入陰影**。

---

## 為形狀套用投影

當有人問「在 C# 中如何**套用投影**？」時，通常只需要開啟可見性以及設定顏色。以下程式碼片段僅示範這兩行：

```csharp
shape.ShadowFormat.Visible = true;          // Turns the shadow on
shape.ShadowFormat.Color   = Color.Black;   // Classic black drop shadow
```

> **專業提示：** 若目標為較舊的 Word 版本（2003‑2007），請使用標準顏色。某些特殊的 ARGB 值可能會被舊版渲染器忽略。

---

## 如何變更陰影的透明度

透明度以 **0 到 1 之間的浮點數** 表示。**0** 代表完全不透明的陰影；**1** 則使其完全不可見。大多數設計師會在 **0.2‑0.4** 左右取得自然的外觀。

```csharp
shape.ShadowFormat.Transparency = 0.35; // 35 % transparent
```

### 邊緣情況

- **Negative values** – Aspose.Words 會將其限制為 0，但最好先驗證輸入。  
- **Values > 1** – 會被限制為 1，等同於隱藏陰影。  

若需要讓使用者選擇百分比，請先進行轉換：

```csharp
float percent = 30;                     // User enters 30 %
shape.ShadowFormat.Transparency = percent / 100f;
```

---

## 如何調整陰影的模糊（Size）

`**Size**` 屬性控制模糊半徑。較大的數值會產生更柔和、較為散布的陰影。單位為點 (pt)，而非像素。

```csharp
shape.ShadowFormat.Size = 10;  // A generous blur for a “soft” effect
```

#### 何時使用小模糊或大模糊

- **小模糊 (2‑4 pt)** – 適用於 UI 風格的說明框，需要清晰邊緣時。  
- **大模糊 (8‑12 pt)** – 適合列印報告或形狀與背景距離較遠的情況。

---

## 為形狀加入陰影 – 位置與方向

**為形狀加入陰影** 的最後一步是設定偏移。兩個屬性共同作用：

| 屬性 | 說明 |
|----------|---------|
| **Distance** | 陰影與形狀之間的距離（單位：點）。 |
| **Angle**    | 偏移的方向（0° = 向右，90° = 向下，180° = 向左，270° = 向上）。 |

以下範例會產生細緻的右下角陰影：

```csharp
shape.ShadowFormat.Distance = 1.5; // Slight lift
shape.ShadowFormat.Angle    = 135; // Down‑left direction (135°)
```

你可以透過調整角度來模擬不同光源。常見的技巧是讓使用者從下拉選單中選擇「光源」並對應到相應的角度值。

---

## 完整範例（結合所有步驟）

以下程式與前述相同，但加入了**額外註解**，使邏輯一目了然。將此程式碼複製到 `Program.cs` 後執行；輸出檔案將包含一個陰影調校完美的文字方塊。

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeShadowDemo
{
    class Program
    {
        static void Main()
        {
            // Load the source document (must contain at least one shape)
            Document doc = new Document("YOUR_DIRECTORY/input.docx");

            // Grab the first shape we encounter – usually a textbox or picture
            Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
            if (shape == null)
            {
                Console.WriteLine("No shape found in the document.");
                return;
            }

            // ---------- Apply Drop Shadow ----------
            shape.ShadowFormat.Visible = true;          // Turn it on
            shape.ShadowFormat.Color   = Color.DarkGray; // Soft dark colour

            // ---------- How to Change Transparency ----------
            shape.ShadowFormat.Transparency = 0.3; // 30 % transparent – looks natural

            // ---------- How to Adjust Blur ----------
            shape.ShadowFormat.Size = 6; // Moderate blur for a professional feel

            // ---------- Add Shape Shadow (position) ----------
            shape.ShadowFormat.Distance = 2; // Slight offset
            shape.ShadowFormat.Angle    = 45; // Diagonal down‑right

            // Save the result
            doc.Save("YOUR_DIRECTORY/output.docx");
            Console.WriteLine("Document saved with shadow. Open output.docx to verify.");
        }
    }
}
```

**預期結果：** 開啟 `output.docx`。第一個文字方塊會顯示深灰色、30 % 透明度、稍微模糊（size = 6）且在 45° 角度、2 pt 偏移的陰影。此效果細緻卻明顯，正是大多數 UI 設計師所追求的。

---

## 常見問題與注意事項

- **「這也適用於圖片嗎？」**  
  會的。任何 `Shape`——無論是文字方塊、圖片或自動圖形——皆具備 `ShadowFormat`。只需將取得形狀的程式碼換成相應的索引或名稱即可。

- **「如果文件中有多個形狀該怎麼辦？」**  
  迭代 `doc.GetChildNodes(NodeType.Shape, true)`，對每個形狀套用相同設定。也可以依 `shape.Name` 或 `shape` 進行篩選。

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}