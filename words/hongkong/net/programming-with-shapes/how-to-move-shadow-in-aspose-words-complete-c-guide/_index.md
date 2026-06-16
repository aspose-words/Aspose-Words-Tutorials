---
category: general
date: 2026-05-01
description: 如何使用 C# 在 Aspose.Words 中移動形狀的陰影。學習在幾分鐘內為形狀添加陰影、調整模糊、設定透明度以及旋轉陰影。
draft: false
keywords:
- how to move shadow
- add shadow to shape
- how to change blur
- how to set transparency
- how to rotate shadow
language: zh-hant
og_description: 如何使用 C# 在 Aspose.Words 中移動形狀的陰影。本教學示範如何為形狀添加陰影、更改模糊程度、設定透明度以及旋轉陰影。
og_title: 如何在 Aspose.Words 中移動陰影 – 完整 C# 指南
tags:
- Aspose.Words
- C#
- Document Automation
title: 在 Aspose.Words 中如何移動陰影 – 完整 C# 指南
url: /zh-hant/net/programming-with-shapes/how-to-move-shadow-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Aspose.Words 中移動陰影 – 完整 C# 指南

有沒有想過 **如何在 Word 文件中的形狀上移動陰影** 而不必手動開啟 Word？在我的日常工作中，我常常需要以程式方式微調形狀的陰影——無論是為了打造精緻的報告或是動態範本。好消息是？使用 Aspose.Words 只需幾行程式碼，即可完成，同時您還會學到 **add shadow to shape**、**how to change blur**、**how to set transparency**、以及 **how to rotate shadow**。

在本教學中，我們將示範一個真實情境：載入已有形狀的 DOCX 檔案，調整陰影的位置、柔和度、不透明度與方向，最後儲存結果。完成後您將擁有可重複使用的程式碼片段，能直接放入任何 .NET 專案，並了解每個屬性的意義。

## 前置條件 – 開始前您需要的項目

- **Aspose.Words for .NET**（版本 23.12 或更新）。您可以透過 NuGet 使用 `Install-Package Aspose.Words` 取得。
- .NET 6+ 開發環境（Visual Studio、VS Code、Rider——您喜歡的任何工具）。
- 一個已包含至少一個形狀（矩形、圓形或圖片皆可）的輸入 Word 檔案（`input.docx`）。
- 基本的 C# 語法認識——不需要太深入。

如果您缺少上述任一項，請先暫停並安裝相應的套件；本指南的後續內容皆假設已正確引用該套件。

## 步驟 1：載入文件並取得目標形狀 – **How to Move Shadow** 開始

我們首先要做的是載入來源文件，並定位要修改的形狀。Aspose.Words 將每個物件（段落、表格、形狀）視為樹狀結構中的節點，因而可以直接查詢。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // 📂 Load the source DOCX that already contains a shape with a shadow.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

        // 🎯 Retrieve the first shape in the document.
        // The GetChild method walks the node tree; the third argument (true) means “search deep”.
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

        // If no shape is found, bail out early.
        if (shape == null)
        {
            System.Console.WriteLine("No shape found in the document.");
            return;
        }

        // -------------------------------------------------
        // The next sections show **how to move shadow**,
        // **add shadow to shape**, **how to change blur**,
        // **how to set transparency**, and **how to rotate shadow**.
        // -------------------------------------------------
```

> **為什麼這很重要：** 只載入一次文件並重複使用相同的 `Document` 實例，可提升效能。`GetChild` 呼叫是安全的，因為若索引超出範圍會回傳 `null`，讓我們能優雅地處理缺少形狀的情況。

## 步驟 2：調整模糊半徑 – 掌握 **How to Change Blur**

柔和的陰影看起來更專業，而硬邊則顯得廉價。`BlurRadius` 屬性以點 (pt) 為單位控制柔軟度 (1 pt ≈ 1/72 英吋)。我們將其提升至 8 pt。

```csharp
        // Increase the blur radius to soften the shadow edges.
        shape.ShadowFormat.BlurRadius = 8.0; // 8 points ≈ 0.11 inches
```

> **專業提示：** 預設的模糊度為 0.5 pt。超過 5 pt 通常會明顯可見，但請注意不要設定過大，否則形狀會顯得與頁面脫節。

## 步驟 3：設定透明度 – 解答 **How to Set Transparency**

透明度決定陰影的透視程度。`0` 代表完全不透明；`1` 代表完全透明。為了取得細膩的效果，我們使用 `0.3`（30 % 透明）。

```csharp
        // Make the shadow semi‑transparent so the shape remains visible through it.
        shape.ShadowFormat.Transparency = 0.3; // 30% transparent
```

> **為什麼您可能在意：** 若形狀顏色較深，完全不透明的陰影會掩蓋底層文字。調整透明度可保持文件可讀性，同時仍提供層次感。

## 步驟 4：移動陰影 – **How to Move Shadow** 的核心

`Distance` 屬性定義陰影相對於形狀的偏移距離，以點為單位。距離越大，陰影越遠離形狀，產生更戲劇化的效果。

```csharp
        // Move the shadow farther from the shape for a more pronounced effect.
        shape.ShadowFormat.Distance = 4.0; // 4 points ≈ 0.055 inches
```

> **如果需要極小的偏移呢？** 將 `Distance` 設為 `0` 會使陰影直接位於形狀後方，這對浮雕效果很有幫助。

## 步驟 5：旋轉光源 – 解決 **How to Rotate Shadow**

陰影不一定垂直向下；它會依光源角度而變化。`Angle` 屬性（以度為單位）繞形狀旋轉陰影。我們將其傾斜 45°。

```csharp
        // Rotate the light source to change the shadow direction.
        shape.ShadowFormat.Angle = 45; // 45 degrees clockwise from the vertical axis
```

> **快速實驗：** 嘗試 `90` 產生右側陰影，或 `-30` 產生左傾陰影。視覺變化會立即顯現。

## 步驟 6：儲存文件 – 觀察 **Add Shadow to Shape** 的結果

現在我們已調整完陰影，將把文件寫回磁碟。您可以覆寫原檔或建立新檔；範例使用新輸出檔案。

```csharp
        // Save the modified document with the adjusted shadow.
        doc.Save(@"YOUR_DIRECTORY\output.docx");

        System.Console.WriteLine("Shadow adjustments applied and saved to output.docx");
    }
}
```

> **預期輸出：** 開啟 `output.docx`。形狀的陰影將變得更柔和、略微偏移、半透明，且以 45° 角度呈現。若與 `input.docx` 並排比較，差異顯而易見。

### 完整可執行範例（直接複製貼上）

以下是一個完整的程式碼區塊。將其貼到新的 Console 專案中，將 `YOUR_DIRECTORY` 替換為實際的資料夾路徑，然後執行。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // Load the source document that already contains a shape with a shadow.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

        // Retrieve the first shape in the document (the one we will modify).
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

        if (shape == null)
        {
            System.Console.WriteLine("No shape found in the document.");
            return;
        }

        // 1️⃣ Change blur – soften the edges.
        shape.ShadowFormat.BlurRadius = 8.0;

        // 2️⃣ Set transparency – make it 30% see‑through.
        shape.ShadowFormat.Transparency = 0.3;

        // 3️⃣ Move the shadow – increase distance from the shape.
        shape.ShadowFormat.Distance = 4.0;

        // 4️⃣ Rotate the shadow – change light direction.
        shape.ShadowFormat.Angle = 45;

        // Save the result.
        doc.Save(@"YOUR_DIRECTORY\output.docx");
        System.Console.WriteLine("Shadow adjustments applied and saved to output.docx");
    }
}
```

## 常見問題與邊緣情況

### 如果文件中有多個形狀呢？

您可以遍歷所有形狀：

```csharp
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    // Apply the same shadow settings or customize per shape.
}
```

### 我可以為目前沒有陰影的形狀新增陰影嗎？

當然可以。`ShadowFormat` 物件始終存在，只需啟用即可：

```csharp
shape.ShadowFormat.Enabled = true;
```

### 這適用於圖片和 SmartArt 嗎？

是的。任何繼承自 `Shape` 的節點——包括圖片、圖表與 SmartArt——皆具備 `ShadowFormat`，且可使用相同的屬性。

### 如何控制陰影顏色？

使用 `Color` 屬性：

```csharp
shape.ShadowFormat.Color = System.Drawing.Color.Gray;
```

### 相容性考量？

Aspose.Words 23.12 以上支援 .NET 6、.NET Core 3.1 與 .NET Framework 4.6.2+。此範例所示的 API 在這些版本中皆保持穩定。

## 結論

我們剛剛說明了如何使用 Aspose.Words 在形狀上 **how to move shadow**，同時也示範了 **add shadow to shape**、**how to change blur**、**how to set transparency** 與 **how to rotate shadow**。完整且可執行的範例讓您在數秒內調整任意形狀的陰影，為文件帶來精緻、專業的外觀，且無需開啟 Word。

準備好進一步了嗎？試著將這些陰影調整與 **conditional formatting** 結合——例如，只對標題或超過特定尺寸的圖表套用較深的陰影。或探索形狀本身的 **gradient fills**，打造真正吸睛的設計。

如果遇到任何問題，歡迎在下方留言。祝程式開發愉快，願您的陰影永遠落在理想的位置！

![Diagram showing the effect of moving a shadow on a shape – how to move shadow example](https://example.com/images/shadow-demo.png "how to move shadow example")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}