---
category: general
date: 2026-01-13
description: 使用 Aspose.Words 建立 Word 文件，學習如何插入矩形形狀、如何加入陰影，以及在 C# 中為形狀添加陰影。附有完整範例。
draft: false
keywords:
- create word document
- insert rectangle shape
- how to add shadow
- how to insert shape
- add shape shadow
language: zh-hant
og_description: 使用 Aspose.Words 建立 Word 文件，了解如何插入矩形形狀以及如何加入陰影。請參考完整的 C# 範例。
og_title: 製作帶陰影矩形的 Word 文件 – 完整教學
tags:
- Aspose.Words
- C#
- Document Automation
title: 建立帶陰影矩形的 Word 文件 – 步驟指南
url: /zh-hant/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 建立帶陰影矩形的 Word 文件 – 步驟說明指南

是否曾需要 **建立 Word 文件**，裡面包含一個漂亮的陰影矩形，但不知從何下手？你並非唯一遇到這個問題的人——許多開發者在第一次使用 Aspose.Words 時都會卡在這裡。

在本教學中，我們將一步步說明如何 **建立 Word 文件**、**插入矩形圖形**，以及 **如何加入陰影** 讓圖形更突出。最後，你將得到一段可直接在任何 .NET 專案中執行的 C# 程式碼片段。

## 你將學到的內容

- 插入圖形（矩形）到 Word 檔的完整程式碼。
- 必須調整的屬性，以 **加入圖形陰影** 並控制其外觀。
- 如何儲存結果並驗證陰影是否可見。
- 幾個實用小技巧與邊緣情況的說明，幫助你避免日後的頭痛。

不需要額外的文件說明——所有資訊都在這裡。

## 前置條件

在開始之前，請確保你已具備：

1. **.NET 6.0**（或任何較新的 .NET 版本）已安裝。  
2. Aspose.Words for .NET 的 **授權**，或使用免費評估模式進行測試。  
3. 開發環境——Visual Studio 2022 表現良好，但任何能編譯 C# 的編輯器皆可。

就這些。除了 `Aspose.Words` 之外不需要額外的 NuGet 套件。

## 第一步 – 建立專案並參考 Aspose.Words

首先，建立一個新的 console 應用程式，並加入 Aspose.Words 套件：

```bash
dotnet new console -n ShadowRectangleDemo
cd ShadowRectangleDemo
dotnet add package Aspose.Words
```

> **專業提示：** 若使用免費試用版，別忘了呼叫 `License.SetLicense` 並傳入授權檔案；否則程式庫會加上浮水印。

## 第二步 – 初始化 Document Builder

現在開始真正的 **建立 Word 文件** 流程。`Document` 類別提供空白畫布，而 `DocumentBuilder` 讓我們在上面繪製。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing; // For Color

// Initialise a new blank document
Document document = new Document();

// Initialise a builder to start adding content
DocumentBuilder builder = new DocumentBuilder(document);
```

為什麼需要 Builder？它抽象化了底層的 OpenXML 細節，讓你專注於 *想要的結果* 而不是 *檔案結構*。這就是 **快速插入圖形** 的核心。

## 第三步 – 插入矩形圖形

接下來就是 **插入矩形圖形**。矩形尺寸為 150 × 100 點（約 2 吋 × 1.3 吋）。

```csharp
// Insert a rectangle shape at the current cursor position
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 100);
```

`InsertShape` 方法會回傳一個 `Shape` 物件，我們可以進一步自訂。目前矩形僅是純白方塊——尚未加入陰影。

## 第四步 – 如何加入陰影（Add Shape Shadow）

只要知道要調整哪些屬性，加入陰影其實相當簡單。`ShadowFormat` 物件負責可見性、顏色、模糊、偏移與大小。

```csharp
// Make the shadow visible
rectangleShape.ShadowFormat.Visible = true;

// Choose a subtle gray tone
rectangleShape.ShadowFormat.Color = Color.Gray;

// Set 30 % transparency – the shadow will be faint but noticeable
rectangleShape.ShadowFormat.Transparency = 0.3;

// Offset the shadow 5 points right and 5 points down
rectangleShape.ShadowFormat.OffsetX = 5;
rectangleShape.ShadowFormat.OffsetY = 5;

// Soften the edges with a blur radius of 4 points
rectangleShape.ShadowFormat.BlurRadius = 4;

// Scale the shadow to 75 % of the shape size (percentage)
rectangleShape.ShadowFormat.Size = 75;
```

上述程式碼說明了 **如何加入陰影**：開啟陰影、選擇顏色、調整透明度、偏移、模糊與大小。你可以自行嘗試不同數值，以得到濃重的投影或輕柔的陰影。

### 常見變化

- **不同顏色：** 使用 `Color.Black` 取得經典投影，或 `Color.BlueViolet` 創造風格化效果。  
- **零模糊：** 設定 `BlurRadius = 0` 可得到銳利的邊緣。  
- **較大偏移：** 增加 `OffsetX`/`OffsetY` 讓陰影遠離圖形。

## 第五步 – 儲存文件並驗證

最後，將文件寫入磁碟。產生的檔案為標準的 `.docx`，任何現代的 Word 處理程式皆可開啟。

```csharp
// Save the document to the desired folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowRectangle.docx");
document.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

在 Microsoft Word 中開啟產生的 *ShadowRectangle.docx*。你應該會看到一個帶有柔和灰色陰影、向右下偏移的矩形——正是程式碼所指定的效果。

> **預期輸出：** 一個單頁 Word 檔，內含 150 × 100 點的矩形，陰影為 30 % 透明的灰色，偏移 5 點，模糊 4 點，大小為圖形的 75 %。

## 完整範例程式

將所有步驟整合，以下是完整、可直接執行的程式：

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialise a new blank document
        Document document = new Document();

        // 2️⃣ Create a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Insert a rectangle shape (150 × 100 points)
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 100);

        // 4️⃣ How to add shadow – configure the ShadowFormat
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = Color.Gray;
        rectangleShape.ShadowFormat.Transparency = 0.3; // 30 % transparent
        rectangleShape.ShadowFormat.OffsetX = 5;        // horizontal offset
        rectangleShape.ShadowFormat.OffsetY = 5;        // vertical offset
        rectangleShape.ShadowFormat.BlurRadius = 4;    // softer edge
        rectangleShape.ShadowFormat.Size = 75;         // size as a percentage

        // 5️⃣ Save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowRectangle.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

執行程式（`dotnet run`），即可得到一個帶有漂亮陰影矩形的全新 Word 檔——非常適合報告、證書或任何視覺提示。

## 常見問題 (FAQs)

**Q: 我可以插入其他圖形（橢圓、星形）並使用相同的陰影程式碼嗎？**  
A: 當然可以。`InsertShape` 方法接受任何 `ShapeType` 列舉值。取得 `Shape` 之後，`ShadowFormat` 屬性皆可相同使用，因此 **如何加入陰影** 與圖形類型無關。

**Q: 若需要在圖形兩側都有陰影該怎麼辦？**  
A: Aspose.Words 只支援每個圖形單一投影。若想模擬雙側效果，可複製圖形、分別設定不同的偏移，並將其中一個的 `ShadowFormat.Visible` 設為 `false`，另一個保留陰影。

**Q: 這在 .NET Framework 4.8 上可用嗎？**  
A: 可以。API 與版本無關，只要引用對應目標框架的 Aspose.Words DLL 即可。

## 小技巧與常見陷阱

- **務必設定 `Visible = true`**——否則陰影屬性會被忽略。  
- **透明度值介於 0.0（不透明）到 1.0（全透明）**。常見錯誤是寫成 `30` 而非 `0.3`。  
- **寫入唯讀資料夾會拋出例外**。請確保輸出目錄具有寫入權限。

## 往後的方向

既然已掌握 **如何插入圖形**、**加入圖形陰影**，以及 **使用 Aspose.Words 建立 Word 文件**，你可以進一步探索：

- 在矩形內插入 **文字**（使用 `builder.InsertParagraph()` 於插入圖形前）。  
- 套用 **漸層填色** 或 **圖案邊框**，提升視覺豐富度。  
- 自動產生多頁文件，每頁都有不同的陰影圖形，以建立動態報告。

盡情實驗吧——改變陰影的顏色、模糊或大小，會讓你的文件外觀產生巨大的差異。

---

*準備好投入正式環境了嗎？取得程式碼、調整參數，讓你的 Word 文件在數秒內獲得專業的光澤。*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}