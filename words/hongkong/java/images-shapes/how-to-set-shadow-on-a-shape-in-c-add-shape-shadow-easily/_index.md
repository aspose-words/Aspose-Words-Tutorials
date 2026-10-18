---
category: general
date: 2026-04-28
description: 快速設定圖形陰影。了解如何為圖形添加陰影、設定陰影顏色，以及使用 Aspose.Words for .NET 自訂圖形陰影。
draft: false
keywords:
- how to set shadow
- add shape shadow
- set shadow color
- how to add shadow
- customize shape shadow
language: zh-hant
og_description: 如何在 C# 中使用 Aspose.Words 為形狀設定陰影。一步一步的指南，涵蓋新增形狀陰影、設定陰影顏色以及自訂形狀陰影。
og_title: C# 中如何為形狀設定陰影 – 完整指南
tags:
- Aspose.Words
- C#
- Document Automation
title: 在 C# 中如何為圖形設定陰影 – 輕鬆添加圖形陰影
url: /zh-hant/java/images-shapes/how-to-set-shadow-on-a-shape-in-c-add-shape-shadow-easily/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中為形狀設定陰影 – 輕鬆新增形狀陰影

有沒有想過 **如何在形狀上設定陰影**，卻不想翻閱無盡的 API 文件？你並不孤單。許多開發者在需要一個細緻的投影陰影讓圖表更突出時，常會卡住，因為找不到同時說明「做什麼」與「為什麼」的完整範例。

在本教學中，我們將一步步示範如何為形狀加入陰影、變更陰影顏色，並微調模糊程度、偏移量與透明度——全部使用 Aspose.Words for .NET。完成後，你將得到一段可直接放入任何 C# 專案的即用程式碼，並附上一些在更複雜情境下自訂形狀陰影的技巧。

> **注意：** 此程式碼相容於 Aspose.Words 22.9 或更新版本，且需要 .NET 6+（或 .NET Framework 4.7.2+）。

![Shape with custom shadow](shape-shadow.png "Shape with custom shadow")

## 你將學會

- **以程式方式為 Word 文件中的第一個形狀加入陰影**。  
- **將陰影顏色設定為任意 `System.Drawing.Color`**。  
- **透過調整模糊半徑、偏移量與透明度，自訂形狀陰影**。  
- 如有需要，如何處理多個形狀以及重設陰影設定。

全程不需外部工具或 Visual Basic 巨集，純粹使用 C#。

---

## 前置條件

| Requirement | Why It Matters |
|-------------|----------------|
| **Aspose.Words for .NET** (NuGet 套件 `Aspose.Words`) | 提供本範例中使用的 `Document`、`Shape` 與 `ShadowFormat` 類別。 |
| **.NET 6 SDK** (或 .NET Framework 4.7.2) | 確保與最新 API 相容。 |
| **一個 .docx 檔案**，內含至少一個形狀（例如矩形或圖片） | 本教學會操作 *第一個* 形狀；若沒有，可在 Word 中自行新增一個。 |

使用以下指令安裝套件：

```bash
dotnet add package Aspose.Words
```

---

## 步驟說明：如何為形狀設定陰影

### 1. 載入 Word 文件

先開啟 `.docx` 檔案。`Document` 建構子會將檔案讀入記憶體，讓我們可以完整存取其節點。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **為什麼要這樣做？** 載入文件是基礎，沒有它就無法遍歷形狀樹。

### 2. 取得第一個形狀（或任意你需要的形狀）

Aspose.Words 會將形狀儲存為 `NodeType.SHAPE` 類型的節點。`GetChild` 方法可取得第 *n* 個形狀；此處使用索引 0，即第一個形狀。

```csharp
// Grab the first shape in the document (depth‑first search)
Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (firstShape == null)
{
    throw new InvalidOperationException("No shape found in the document.");
}
```

> **小技巧：** 若要 **為特定形狀加入陰影**，只需將索引改為相應的值，或遍歷 `doc.GetChildNodes(NodeType.Shape, true)`。

### 3. 取得陰影格式物件

每個 `Shape` 都有 `ShadowFormat` 屬性，提供所有與陰影相關的設定。

```csharp
ShadowFormat shadow = firstShape.ShadowFormat;
```

現在可以開始調整陰影了。

### 4. 設定模糊半徑 – 讓邊緣更柔和

較大的模糊半徑會讓陰影看起來更擴散。數值單位為點 (1 pt ≈ 1/72 英吋)。

```csharp
shadow.BlurRadius = 5.0; // 5 pt blur – looks nicely soft
```

> **何時調整？** 若形狀很小，2–3 pt 的模糊即可；若是大型橫幅，建議提升至 8–10 pt。

### 5. 定義水平與垂直偏移量

偏移量決定陰影相對於形狀的位移距離。正值向右/下移動，負值向左/上移動。

```csharp
shadow.DistanceX = 3.0; // 3 pt to the right
shadow.DistanceY = 3.0; // 3 pt downwards
```

### 6. 微調透明度（不透明度）

`Transparency` 的範圍是 `0.0`（完全不透明）到 `1.0`（完全透明）。約 `0.3` 的數值可呈現細膩的半透明效果。

```csharp
shadow.Transparency = 0.3; // 30 % transparent
```

### 7. 選擇陰影顏色 – **將陰影顏色設定為任意 `System.Drawing.Color`**

你可以使用任何預設顏色，或以 RGB 自訂顏色。

```csharp
shadow.Color = Color.FromArgb(0, 120, 215); // A calm blue shade
```

若想要傳統的黑色陰影，只需使用 `Color.Black`。

### 8. 儲存已修改的文件

最後，把變更寫回檔案。可以直接覆寫原檔，或另存新檔。

```csharp
doc.Save("YOUR_DIRECTORY/output_with_shadow.docx");
```

---

## 完整範例（一次完成所有步驟）

將以下程式碼貼到 Console App 的 `Main` 方法中即可直接編譯執行（前提是已安裝 NuGet 套件）。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1. Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first shape (add shape shadow)
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            System.Console.WriteLine("No shape found – aborting.");
            return;
        }

        // 3. Get the shadow formatting object
        ShadowFormat shadow = shape.ShadowFormat;

        // 4. Set blur radius
        shadow.BlurRadius = 5.0;

        // 5. Define offsets
        shadow.DistanceX = 3.0;
        shadow.DistanceY = 3.0;

        // 6. Adjust transparency (0 = opaque, 1 = fully transparent)
        shadow.Transparency = 0.3;

        // 7. Set shadow color (set shadow color)
        shadow.Color = Color.GetBlue(); // or any custom color

        // 8. Save the result
        doc.Save("YOUR_DIRECTORY/output_with_shadow.docx");

        System.Console.WriteLine("Shadow applied successfully!");
    }
}
```

**預期結果：** 在 Word 中開啟 `output_with_shadow.docx`，第一個形狀會顯示藍色柔和陰影，水平與垂直偏移 3 pt，具細緻的模糊與 30% 透明度。

---

## 常見變化與例外情況

### 為 *所有* 形狀加入陰影

若文件中有多個圖表，想一次處理每個形狀，可使用迴圈：

```csharp
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape s in shapes)
{
    ShadowFormat sf = s.ShadowFormat;
    sf.BlurRadius = 4.0;
    sf.DistanceX = 2.0;
    sf.DistanceY = 2.0;
    sf.Transparency = 0.25;
    sf.Color = Color.Gray;
}
```

### 重設陰影

有時形狀已經有陰影，需要將其移除。只要把 `ShadowFormat.Visible` 設為 `false`：

```csharp
shape.ShadowFormat.Visible = false;
```

### 使用帶有 Alpha 的自訂顏色（半透明）

```csharp
shadow.Color = Color.FromArgb(128, 255, 0, 0); // 50 % transparent red
```

### 相容性說明

`ShadowFormat` API 在各版本的 Aspose.Words 中皆相當穩定，但舊版（< 19.1）使用的欄位命名略有不同。建議始終使用最新的 NuGet 套件以獲得最佳效果。

---

## 打造完美陰影的專業技巧

- **平衡模糊與偏移：** 大幅模糊搭配極小偏移會產生「發光」感，而非真實的投影陰影。請同時調整 `BlurRadius` 與 `DistanceX/Y`。  
- **配合文件主題：** 若 Word 使用深色主題，使用淺色陰影（`Color.White`）可營造微妙的提升感。  
- **效能考量：** 對上百個形狀調整陰影可能會多耗幾毫秒/形狀。若處理大型報表，建議批次執行。  
- **測試方式：** 同時在 Word 桌面版與 Word Online 開啟產生的 `.docx`，確保陰影呈現一致。

---

## 結論

我們已說明 **如何在 C# 中為形狀設定陰影**。依循上述八個步驟，你可以 **為形狀加入陰影**、**設定陰影顏色**，並完整 **自訂形狀陰影** 以符合任何設計需求。此範例獨立、即插即用，為你進一步擴充至多形狀、動態顏色或使用者自訂參數提供了堅實基礎。

準備好挑戰下一個目標了嗎？試著將此技巧與 **形狀旋轉** 結合，或在整份報告中為每個圖表自動套用品牌化陰影。可能性無限，而你剛學會的程式碼正是最佳的跳板。

如果本指南對你有幫助，歡迎為儲存庫加星、留下評論，或在下方分享你自己的陰影調整祕訣。祝開發愉快！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}