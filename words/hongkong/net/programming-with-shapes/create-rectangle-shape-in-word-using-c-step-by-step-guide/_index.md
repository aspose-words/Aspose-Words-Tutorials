---
category: general
date: 2026-01-03
description: 在 Word 中使用 C# 建立矩形形狀並為形狀添加陰影。學習如何在 Word 中插入形狀、為形狀添加陰影，以及以程式方式產生 Word
  文件。
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- insert shape in word
- how to add shape
- c# generate word document
language: zh-hant
og_description: 使用 C# 在 Word 中建立矩形形狀並為形狀添加陰影。請參考本指南在 Word 中插入形狀、設定陰影，並以程式方式產生文件。
og_title: 使用 C# 在 Word 中建立矩形形狀 – 完整教學
tags:
- C#
- Word Automation
- Aspose.Words
title: 使用 C# 在 Word 中建立矩形形狀 – 步驟教學
url: /zh-hant/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 中使用 C# 建立矩形形狀 – 完整教學

曾經需要在 Word 文件中 **create rectangle shape**（建立矩形形狀），卻不知從何開始嗎？你並不孤單——許多開發者在想要 **add shadow to shape**（為形狀加入陰影）以獲得更精緻的外觀時，都會卡在同一地方。在本教學中，我們將逐步說明如何 **insert shape in Word**（在 Word 中插入形狀），套用細緻的陰影，最後 **c# generate word document**（產生 Word 文件）讓你可以發佈給使用者。

我們會從專案設定講起，直到微調陰影屬性，最後提供一個可直接執行的程式碼範例。內容不囉嗦，只提供實用的重點，讓你快速完成任務。

## 你將學會

- 如何在 C# 中使用 Aspose.Words（或 Open XML）**create rectangle shape**
- 為了呈現深度，需要的 **add shadow to shape** 相關屬性
- 使用 `DocumentBuilder` 放置形狀的位置
- 如何儲存檔案，使其在 Microsoft Word 中正確開啟
- 技巧、常見問題與實務情境的變化

### 前置條件

- .NET 6.0 或更新版本（此程式碼可在 .NET Core 與 .NET Framework 上執行）
- 可操作 Word 檔案的 NuGet 套件——我們將使用 **Aspose.Words for .NET**，因為其 API 簡潔。若你偏好 Open XML SDK，概念相同，只是類別不同。
- Visual Studio、VS Code，或任何你喜歡的 C# IDE

> **專業提示：** 若預算有限，Aspose 提供免費試用版，非常適合學習。測試時只需將授權程式碼改為註解即可。

## 步驟 1：安裝 Word 處理函式庫

首先，將函式庫加入你的專案。於解決方案資料夾開啟終端機，執行以下指令：

```bash
dotnet add package Aspose.Words
```

如果使用 Open XML SDK，指令會是 `dotnet add package DocumentFormat.OpenXml`。本指南其餘部分以 Aspose.Words 為例，但切換 API 呼叫相當簡單。

## 步驟 2：建立新的空白文件

函式庫就緒後，我們即可透過全新的 `Document` 物件 **create rectangle shape**。把它想像成一張全新的畫布。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 2: Initialize a blank Word document
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);
```

`DocumentBuilder` 提供高階方式插入內容，無需深入低階節點樹。

## 步驟 3：插入矩形形狀

有了 builder 後，我們可以 **insert shape in Word**。`InsertShape` 方法接受形狀類型以及以點 (points) 為單位的尺寸（寬度、長度）。

```csharp
// Step 3: Insert a rectangle shape – 150pt wide, 80pt high
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

此時矩形已顯示於文件中，但看起來有點平淡。接下來的步驟將解決這個問題。

## 步驟 4：為形狀加入陰影

陰影能為形狀增添深度感。`Shadow` 物件讓我們微調模糊、距離、角度、顏色與透明度。以下是一套適用於大多數報告的完整設定。

```csharp
// Step 4: Configure a subtle shadow
rectangle.Shadow = new Shadow
{
    BlurRadius = 5.0,          // Soft edges
    Distance = 4.0,            // How far the shadow is offset
    Angle = 45,                // Direction in degrees (45° = down‑right)
    Color = Color.Black,       // Shadow color
    Transparency = 0.3         // 30 % transparent for a gentle look
};
```

**為什麼選擇這些數值？**  
- **BlurRadius** 為 `5.0`，保持邊緣平滑且不模糊。  
- **Distance** 為 `4.0`，使陰影偏移適度，易於辨識。  
- **Angle** 為 `45`，模擬左上方自然光照，常見於 UI 設計。  
- **Transparency** 為 `0.3`，避免陰影過於蓋過形狀填色。

若需更戲劇化的效果，可提升 `BlurRadius` 並降低 `Transparency`。若想要微妙、幾乎看不見的提升，則相反調整這些數值。

## 步驟 5：儲存文件

最後，將檔案寫入磁碟。`Save` 方法會依檔案副檔名偵測格式，使用 `.docx` 即可得到現代 Word 格式。

```csharp
// Step 5: Persist the document
string outputPath = @"C:\Temp\ShadowRectangle.docx";
document.Save(outputPath);
```

在 Microsoft Word 中開啟 `ShadowRectangle.docx`，你會看到一個線條清晰且帶有柔和陰影的矩形——正是你在尋找「**how to add shape**」時想要的專業效果。

![在 Word 中建立帶陰影的矩形形狀](placeholder-image.png "在 Word 中建立帶陰影的矩形形狀")

*圖片說明文字：在 Word 中建立帶陰影的矩形形狀*

## 完整範例程式

將上述步驟整合起來，以下是完整且可直接執行的程式。複製貼上至 Console 應用程式，然後按 **F5**。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a new blank document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a rectangle shape (150pt × 80pt)
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Add a subtle shadow
            rect.Shadow = new Shadow
            {
                BlurRadius = 5.0,
                Distance = 4.0,
                Angle = 45,
                Color = Color.Black,
                Transparency = 0.3
            };

            // 4️⃣ Save the file
            string filePath = @"C:\Temp\ShadowRectangle.docx";
            doc.Save(filePath);

            System.Console.WriteLine($"Document saved to {filePath}");
        }
    }
}
```

### 預期結果

- 產生的 `ShadowRectangle.docx` 包含 **一個矩形形狀**，位於游標所在的中心位置。  
- 該矩形顯示 **柔和、30 % 透明的黑色陰影**，以 45° 角度偏移。  
- 未加入其他內容，使檔案保持輕量，易於嵌入更大的報告中。

## 常見問題與邊緣案例

### 如果需要其他形狀？

將 `ShapeType.Rectangle` 替換為任意其他 `ShapeType` 列舉值（例如 `Ellipse`、`Triangle`）。陰影 API 的使用方式相同，您可以直接重用先前的設定。

### 如何變更填色？

```csharp
rect.FillColor = Color.LightBlue;   // or any System.Drawing.Color
```

### 能將形狀加入特定段落嗎？

可以。於呼叫 `InsertShape` 前，使用 `builder.MoveToParagraph(index)` 將 `DocumentBuilder` 移至目標段落。這樣可確保形狀正確出現在指定位置。

### 舊版 Word 格式（.doc）怎麼處理？

只需更改副檔名：

```csharp
doc.Save(@"C:\Temp\ShadowRectangle.doc", SaveFormat.Doc);
```

陰影功能在 Word 2003 及之後的版本皆受支援，因此仍會看到效果。

### 使用 Open XML SDK 取代 Aspose？

步驟仍相同：建立 `WordprocessingDocument`，加入 `Drawing` 元素，設定 `<a:shadow>` 屬性。XML 較為冗長，但概念（尺寸、模糊、距離、角度）相同。

## 避免常見陷阱的技巧

- **不要忘記授權**，若使用付費版 Aspose，否則會出現浮水印。  
- **單位為點 (points)**，而非像素。一般螢幕像素約為 0.75 pt，請依此調整尺寸。  
- **若形狀的 `WrapType` 設為 `Inline`，陰影屬性會被忽略**。使用 `WrapType = WrapType.Square` 讓浮動形狀能正確呈現陰影。  
- **儲存至網路共享** 可能需要適當的權限，請先測試路徑是否可寫入。

## 結論

現在你已掌握如何在 Word 文件中使用 C# **create rectangle shape**、**add shadow to shape**，以及 **c# generate word document**，讓產出的檔案即具備精緻外觀。核心步驟——安裝函式庫、實例化 `Document`、插入形狀、設定陰影、儲存——簡單易記，且可靈活套用於其他形狀、顏色或動態資料。

接下來可以嘗試疊加多個形狀、嵌入圖片，或產生包含表格與圖表的完整報告。亦可探索條件格式化——根據資料值調整陰影強度，讓文件不僅實用，更具視覺吸引力。

歡迎自行嘗試，若遇到問題，請在下方留言。祝開發愉快，願你的 Word 文件永遠擁有完美的投影陰影！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}