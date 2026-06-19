---
category: general
date: 2026-05-26
description: 使用 C# 及 Aspose.Words 建立 Word 文件，插入矩形形狀、設定填色並加入陰影效果——逐步指南。
draft: false
keywords:
- create word document
- insert rectangle shape
- how to add shadow
- how to insert shape
- how to set fill
language: zh-hant
og_description: 使用 Aspose.Words 在 C# 中建立 Word 文件。學習如何插入矩形形狀、設定填色，並加入陰影效果。
og_title: 在 C# 中建立 Word 文件 – 插入矩形形狀與陰影
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Create Word document in C# with Aspose.Words, insert rectangle shape,
    set fill color, and add shadow effect – step‑by‑step guide.
  headline: Create Word Document – Insert Rectangle Shape & Shadow in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Create Word Document – Insert Rectangle Shape & Shadow in C#
url: /zh-hant/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 建立 Word 文件 – 在 C# 中插入矩形形狀與陰影

有沒有想過如何在不先開啟 Microsoft Word 的情況下，以程式方式 **create Word document**？你並非唯一有此需求的人。在許多自動化情境——例如發票、合約或大量報告產生——你需要一種可靠的方法來產生 .docx 檔案、在裡面放入形狀、設定顏色，甚至加上陰影以獲得更精緻的外觀。

在本教學中，我們將一步步說明：使用 Aspose.Words for .NET 來 **create Word document**、**insert rectangle shape**、套用填色，並 **add shadow**。完成後，你將得到一個可直接儲存的檔案，能夠串接至任何後續工作流程。  

我們也會提及 **how to insert shape** 的彈性寫法，以及為何 **how to set fill** 對視覺一致性很重要。沒有多餘說明，只有你可以直接 copy‑paste 並執行的程式碼。

## 前置條件

- 已安裝 .NET 6+（或 .NET Framework 4.7+）。
- 有效的 Aspose.Words for .NET 授權（或臨時評估金鑰）。
- Visual Studio、Rider，或任何你喜歡的 C# IDE。
- 基本熟悉 C# 語法——不需要任何進階知識。

都有了嗎？太好了，讓我們開始吧。

## 第一步 – 建立 Word 文件

首先，你需要一個空白的文件物件。它是所有內容的畫布。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document and a DocumentBuilder.
Document doc = new Document();                 // The document itself.
DocumentBuilder builder = new DocumentBuilder(doc); // Helper to add content.
```

`Document` 代表記憶體中的 .docx 檔案，而 `DocumentBuilder` 提供方便的 API 來插入文字、表格與形狀。以此方式 **Creating the Word document** 是即時的——沒有 UI、沒有 COM interop，純粹使用 .NET。

## 第二步 – 插入矩形形狀

既然已有文件，讓我們 **insert rectangle shape**。`InsertShape` 方法接受 `ShapeType` 列舉、寬度與高度（以點為單位）。我們將使用尺寸為 150 × 80 點的矩形，約等於 2 × 1 英吋。

```csharp
// Step 2: Insert a rectangle shape of the desired size.
Shape shape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

在背後，Aspose 會建立一個 `Shape` 物件，將其加入目前段落，並回傳可供樣式設定的參考。這就是 **how to insert shape** 的核心——只需一行程式碼，卻非常強大。

## 第三步 – 設定填色

沒有填色的形狀在白色頁面上會看不見。讓我們給它一個舒適的淡藍色背景。

```csharp
// Step 3: Apply a fill color to make the shape visible.
shape.FillColor = System.Drawing.Color.LightBlue; // Any System.Drawing.Color works.
```

你也可以使用漸層、紋理，甚至圖片填充，但純色讓範例保持簡潔。這示範了 **how to set fill** 在任何你建立的形狀上，確保讀者預期的視覺提示。

## 第四步 – 加入陰影

陰影能增加深度，使形狀更突出。Aspose.Words 會公開一個 `ShadowFormat` 物件，你可以在此切換可見性、選擇顏色，並微調模糊、距離與角度。

```csharp
// Step 4: Configure the shadow effect – enable it, set color, blur, distance and angle.
shape.ShadowFormat.Visible = true;                     // Turn the shadow on.
shape.ShadowFormat.Color = System.Drawing.Color.Gray; // Shadow color.
shape.ShadowFormat.BlurRadius = 4.0;                  // Softness in pixels.
shape.ShadowFormat.Distance = 3.0;                    // How far the shadow is offset.
shape.ShadowFormat.Angle = 45;                        // Direction of the offset (degrees).
```

為什麼選擇這些特定的數值？45° 的角度提供自然的右上方光源，適度的模糊讓陰影保持柔和，短距離則避免形狀看起來脫節。歡迎自行實驗——例如將角度改為 135°，陰影就會落在左下方。

## 第五步 – 儲存文件

所有工作已完成；現在將檔案寫入磁碟。選擇任意路徑即可，只要確保資料夾已存在。

```csharp
// Step 5: Save the document with the shaped shadow.
doc.Save("YOUR_DIRECTORY/ShadowShape.docx");
```

當你在 Microsoft Word 中開啟 `ShadowShape.docx` 時，會看到一個淡藍色矩形搭配柔和的灰色陰影——正是我們程式碼所產生的效果。

## 完整範例程式

將上述步驟整合起來，以下是完整、可直接 copy‑paste 的程式：

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a rectangle shape (150 × 80 points).
        Shape shape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

        // 3️⃣ Set a solid fill color so the shape is visible.
        shape.FillColor = System.Drawing.Color.LightBlue;

        // 4️⃣ Add a subtle shadow for depth.
        shape.ShadowFormat.Visible = true;
        shape.ShadowFormat.Color = System.Drawing.Color.Gray;
        shape.ShadowFormat.BlurRadius = 4.0;   // pixels
        shape.ShadowFormat.Distance = 3.0;     // pixels
        shape.ShadowFormat.Angle = 45;        // degrees

        // 5️⃣ Persist the document.
        doc.Save("ShadowShape.docx");
    }
}
```

### 預期結果

- 目標資料夾中會出現名為 **ShadowShape.docx** 的檔案。
- 在 Word 中開啟時，會看到位於首頁中央的淡藍色矩形。
- 該矩形在 45° 角度投射出灰色陰影，呈現細緻的 3‑D 效果。

## 常見問題與邊緣情況

**如果需要其他形狀呢？**  
將 `ShapeType.Rectangle` 替換為其他列舉值（例如 `Ellipse`、`Star`、`Arrow` 等）。其餘程式碼保持不變。

**可以在形狀內加入文字嗎？**  
可以——在建立形狀後，呼叫 `shape.AppendChild(new Paragraph(doc))`，再插入包含文字的 `Run`。若需要換行，請記得設定 `shape.TextBox` 屬性。

**DPI 或測量單位怎麼處理？**  
Aspose 使用點作為單位（1 pt = 1/72 英吋）。若想使用公分，可乘以 28.35（因為 1 cm ≈ 28.35 pt）。

**需要授權才能運作嗎？**  
評估版會在首頁加上浮水印。正式授權則會移除浮水印，並解鎖完整 API。

## 小技巧與注意事項

- **專業提示：** 若希望形狀位於文件最末端，插入前先呼叫 `builder.MoveToDocumentEnd()`。
- **注意事項：** 儲存至唯讀資料夾會拋出 `UnauthorizedAccessException`。請確保應用程式具有寫入權限。
- **效能說明：** 若大量產生（數百份文件），可重複使用單一 `Document` 實例作為範本，並使用 `doc.Clone(true)` 進行複製，以避免重複的初始化開銷。

## 結論

現在你已掌握使用 Aspose.Words for .NET 來 **create Word document**、**insert rectangle shape**、**set fill**，以及 **add shadow** 的方法。上方的程式碼片段是一個獨立的解決方案，能直接嵌入任何 C# 專案，無論是主控台應用程式、Web API，或是背景服務。

從此你可以進一步探索：

- 新增多個不同顏色的形狀。
- 使用漸層或圖片填充（`shape.FillColor = ...` → `shape.FillPattern`）。
- 將形狀與表格結合，以建立複雜的報告版面。

試試看，調整參數，你會發現自動產生的 Word 檔案只需幾行程式碼就能更顯專業。祝開發愉快！

## 相關教學

- [使用 C# 在 Word 中建立矩形形狀 – 步驟指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words 形狀陰影教學 – 在 C# 中為 Word 形狀加入陰影](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [使用 Aspose.Words for .NET 在 Word 文件中建立群組形狀](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}