---
category: general
date: 2026-01-08
description: 建立空白 Word 文件，學習如何為矩形形狀加入陰影。插入形狀的 Word 檔案，並使用 Aspose.Words 於 C# 中為形狀加入陰影。
draft: false
keywords:
- create blank word
- how to add shadow
- rectangle shape word
- insert shape word
- add shape shadow
language: zh-hant
og_description: 建立空白 Word 文件，了解如何使用 C# 為矩形形狀添加陰影。完整程式碼、說明與技巧。
og_title: 建立空白 Word 文件 – 新增陰影矩形形狀
tags:
- Aspose.Words
- C#
- Document Automation
title: 建立帶陰影矩形形狀的空白 Word 文件 – 逐步指南
url: /zh-hant/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 建立帶陰影矩形形狀的空白 Word 文件 – 完整教學

是否曾需要 **程式化建立空白 Word** 檔案，然後為它加上一個漂亮的陰影矩形？你並非唯一遇到這個問題的人。許多開發者在發現插入圖形與套用效果並不像輸入文字那麼直接時，常會卡關。

在本指南中，我們將一步步說明整個流程——從產生空的 `.docx` 檔案，到 **如何為 rectangle shape word 物件加入陰影**，最後 **插入 shape word 內容** 並套用精緻的 **add shape shadow** 效果。完成後，你將擁有一段可直接使用的程式碼，適用於最新的 Aspose.Words for .NET。

---

## 需要的條件

- **Aspose.Words for .NET**（v24.10 或更新）——本教學所有功能的核心函式庫。  
- .NET 開發環境（Visual Studio、Rider，或 `dotnet` CLI）。  
- 基本的 C# 知識——只要會寫「Hello World」即可上手。  

不需要額外的 NuGet 套件；所有功能皆包含於 `Aspose.Words` 與 `System.Drawing` 中。

---

## 步驟 1：建立空白 Word 文件

首先要做的是建立一個空的 `Document` 物件。把它想像成全新的畫布——就像手動開啟一個全新的 Word 檔案一樣。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Initialize a brand‑new blank Word document
Document document = new Document();   // This creates an empty .docx in memory
```

*為什麼這很重要：*  
`Document` 實例代表整個 Word 檔案。從空白文件開始，讓你能完整掌控之後要加入的每個元素，無論是段落還是圖形。

---

## 步驟 2：定義矩形圖形（Rectangle Shape Word）

接下來需要一個圖形來操作。矩形是最簡單的幾何形狀，適合用於橫幅、佔位或簡易 UI 模型。

```csharp
// Step 2: Create a rectangle shape with specific dimensions
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width  = 200,   // Width in points (≈2.78 inches)
    Height = 100    // Height in points (≈1.39 inches)
};
```

*為什麼這很重要：*  
設定 `Width` 與 `Height` 能控制圖形的視覺佔位。`ShapeType.Rectangle` 讓 Aspose 繪製傳統的方框——之後示範 **add shape shadow** 時的理想範例。

---

## 步驟 3：為圖形套用陰影（How to Add Shadow）

陰影能提供深度，讓平面的矩形看起來像實體物件。Aspose.Words 提供 `Shadow` 屬性，可調整顏色、距離、模糊度與透明度。

```csharp
// Step 3: Enable and configure the shadow effect
rectangleShape.Shadow.Enabled      = true;               // Turn the shadow on
rectangleShape.Shadow.Color        = Color.Gray;         // Shadow color
rectangleShape.Shadow.Distance    = 5.0;                // How far the shadow is offset
rectangleShape.Shadow.BlurRadius  = 3.0;                // Softness of the edge
rectangleShape.Shadow.Transparency = 0.2;               // 0 = opaque, 1 = fully transparent
```

*為什麼這很重要：*  
每個屬性都會影響視覺效果：

- **Enabled** – 若未啟用，其他設定皆會被忽略。  
- **Color** – 選擇與文件主題相符的色調。  
- **Distance** – 數值越大，陰影越遠離圖形。  
- **BlurRadius** – 數值越高，陰影越柔和。  
- **Transparency** – 調整不透明度以取得微妙效果。

隨意試驗；若想要更戲劇化的效果，可將 `Distance` 提升至 `10`，並將 `Transparency` 設為 `0.5`。

---

## 步驟 4：將圖形插入文件（Insert Shape Word）

矩形準備好後，需要一個放置位置。最簡單的方式是將它加入文件正文的第一個段落。

```csharp
// Step 4: Append the shape to the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

*為什麼這很重要：*  
`FirstSection.Body.FirstParagraph` 在新建 `Document` 時必定存在。將圖形附加在此，可確保圖形出現在檔案最上方——非常適合作為標題橫幅或頁首。

若需將圖形插入其他位置，只要定位到特定的 `Paragraph` 或 `Run`，再使用 `InsertAfter` 或 `InsertBefore` 即可。

---

## 步驟 5：儲存 Word 檔案

最後一步是將記憶體中的文件寫入磁碟。選擇一個你有寫入權限的資料夾，並為檔案命名。

```csharp
// Step 5: Save the document with the shadowed rectangle
string outputPath = @"C:\Temp\ShadowedRectangle.docx";
document.Save(outputPath);
```

*為什麼這很重要：*  
呼叫 `Save` 會產生符合規範的 `.docx` 檔案。使用 Microsoft Word、LibreOffice 或任何檢視器開啟，你會看到一個帶有柔和灰色陰影的矩形——正是我們剛設定的樣子。

---

## 完整範例程式

以下是可直接貼到 Console 應用程式的完整程式碼，包含所有 `using` 指令、圖形建立、陰影設定、插入與儲存。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Define a rectangle shape (rectangle shape word)
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
        {
            Width  = 200,
            Height = 100
        };

        // 3️⃣ How to add shadow – configure the shadow effect
        rectangleShape.Shadow.Enabled      = true;
        rectangleShape.Shadow.Color        = Color.Gray;
        rectangleShape.Shadow.Distance    = 5.0;
        rectangleShape.Shadow.BlurRadius  = 3.0;
        rectangleShape.Shadow.Transparency = 0.2;

        // 4️⃣ Insert shape word into the first paragraph
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // 5️⃣ Save the file (add shape shadow persisted)
        string outputPath = @"C:\Temp\ShadowedRectangle.docx";
        document.Save(outputPath);

        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**預期結果：**  
開啟 `ShadowedRectangle.docx`，你會看到頁面頂部正中有一個淡灰色矩形，陰影向右下方偏移 5 pts。沒有額外文字，僅有圖形——正是程式碼產生的結果。

---

## 常見問題與邊緣案例

### 如果需要其他形狀該怎麼辦？

將 `ShapeType.Rectangle` 替換為任意 `ShapeType` 列舉值（`Ellipse`、`Triangle`、`Star` 等），陰影屬性仍然適用。

### 可以加入多個陰影嗎？

Aspose.Words 只支援每個圖形一個陰影。若需層疊效果，可建立兩個重疊的圖形，分別設定不同的陰影。

### 在 .NET Core 上如何使用？

相同的 API 在 .NET 6/7/8 上皆可使用。只要引用 **Aspose.Words.NETCore** 套件（或現在已跨平台的標準套件）即可。

### `System.Drawing` 在 Linux 上仍受支援嗎？

自 .NET 6 起，`System.Drawing.Common` 僅限 Windows。跨平台專案可改用 `Aspose.Drawing`（獨立 NuGet）或直接使用 `Aspose.Words` 提供的顏色類別。

### DPI 縮放會有影響嗎？

圖形尺寸以點為單位（1 pt = 1/72 inch）。若需針對特定 DPI 取得像素精準尺寸，可依公式 `points = pixels * 72 / dpi` 計算。

---

## 專業技巧與常見陷阱

- **技巧**：若希望圖形隨文字流動而非漂浮，可設定 `rectangleShape.WrapType = WrapType.Inline;`。  
- **注意**：別忘了啟用陰影 (`Enabled = true`)；未啟用時其他設定會被靜默忽略。  
- **效能提醒**：在緊密迴圈中加入大量圖形會較慢。建議一次將圖形加入同一個 `Section`，最後只呼叫一次 `document.UpdatePageLayout()`。  
- **版本檢查**：陰影 API 自 Aspose.Words 20.2 起加入。若使用較舊版本，請升級以取得相關屬性。

---

## 結論

我們已 **建立空白 Word** 文件、**建立 rectangle shape word**、學會 **如何加入陰影**，最後 **插入 shape word 內容** 並套用精緻的 **add shape shadow** 效果，全部皆透過 Aspose.Words for .NET 完成。

此程式碼可直接執行，支援 Windows 與跨平台 .NET，亦可延伸至其他形狀、顏色，甚至動畫 GIF。接下來，你可以嘗試在矩形內加入文字、套用漸層填色，或產生包含多個樣式圖形的完整報表。

有更多想法嗎？試著把灰色陰影換成藍色，或提升模糊度營造夢幻感，甚至將多個圖形組合成自訂商標。可能性無限，而現在你已掌握了實作的基礎。

祝開發順利，讓你的文件永遠保持銳利且帶有恰到好處的陰影！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}