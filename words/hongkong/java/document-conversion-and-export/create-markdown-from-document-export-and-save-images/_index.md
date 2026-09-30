---
category: general
date: 2026-02-18
description: 使用簡易步驟將文件匯出為 Markdown，並將圖片儲存至子資料夾。學習如何在 C# 中將文件保存為 Markdown。
draft: false
keywords:
- create markdown from document
- export document to markdown
- save document as markdown
- save images to subfolder
language: zh-hant
og_description: 在 C# 中從文件建立 Markdown，並學習如何在匯出文件為 Markdown 時將圖片儲存至子資料夾。請遵循一步一步的指南。
og_title: 從文件建立 Markdown – 匯出並儲存圖片
tags:
- C#
- Aspose.Words
- Markdown export
title: 從文件建立 Markdown – 匯出及儲存圖片
url: /zh-hant/java/document-conversion-and-export/create-markdown-from-document-export-and-save-images/
---

formatting.

Let's craft final answer.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 從文件建立 Markdown – 匯出並儲存圖片

有沒有曾經需要**從文件建立 markdown**，卻不確定如何保持嵌入的圖片整齊？你並不孤單。在許多專案中，我們會程式化產生報告、手冊或部落格草稿，而最不想看到的就是圖片檔案散落在輸出資料夾中，形成一團亂。

在本教學中，我們將逐步示範一個完整、可直接執行的解決方案，**將文件匯出為 markdown**、將每張圖片存放於專屬的 *md‑resources* 子資料夾，最後使用 Aspose.Words for .NET API **將文件儲存為 markdown**。完成後，你將擁有一個可直接放入任何 C# 程式碼庫的單一方法，並提供一些處理邊緣情況的技巧。

> **快速概覽：**  
> • 設定 `MarkdownSaveOptions`  
> • 提供 `IResourceSavingCallback` 以將圖片導向子資料夾  
> • 使用已配置的選項呼叫 `Document.Save`  

如果你想了解為什麼我們選擇使用回呼 (callback) 而非後處理，請繼續閱讀——原因會一步步說明。

---

## 前置條件

- .NET 6.0 或更新版本（此程式碼亦相容 .NET Framework 4.7+）  
- Aspose.Words for .NET（NuGet 套件 `Aspose.Words`）  
- 一個來源 `Document` 物件（可以是 .docx、.pdf、.rtf 等）  

不需要額外的函式庫；回呼 API 已內建於 Aspose.Words。

---

## 第一步：建立 markdown 從文件 – 設定儲存選項

我們首先建立 `MarkdownSaveOptions`。此物件告訴 Aspose.Words 轉換時的行為，例如使用哪種 Markdown 風格、是否以 Base64 內嵌圖片，以及產生檔案的放置位置。

```csharp
// Step 1: Initialize Markdown save options
var markdownSaveOptions = new Aspose.Words.Saving.MarkdownSaveOptions();
```

> **為什麼這很重要：**  
> 若未明確建立 `MarkdownSaveOptions`，函式庫會回退到預設設定，直接將圖片以 Base64 字串嵌入 Markdown 檔案，導致檔案體積龐大，失去擁有乾淨 *images* 資料夾的初衷。

---

## 第二步：匯出文件為 markdown 並定義資源處理

現在告訴儲存器 **圖片要放哪裡**。`IResourceSavingCallback` 介面提供了一個鉤子，會在匯出過程中為每個資源（圖片、SVG 等）觸發。於回呼內我們：

1. 確認目標資料夾 (`md-resources/`) 已存在。  
2. 將 `OutputFileName` 設為資料夾路徑加上原始資源名稱。  

```csharp
// Step 2: Hook into the resource‑saving pipeline
markdownSaveOptions.ResourceSavingCallback = new Aspose.Words.Saving.IResourceSavingCallback(
    (args) =>
    {
        // All images will be placed in "md-resources" relative to the output .md file
        const string folder = "md-resources/";
        Directory.CreateDirectory(folder);          // Create folder if it doesn’t exist

        // Preserve the original file name (e.g., image001.png) but prepend the folder path
        args.OutputFileName = Path.Combine(folder, args.ResourceFileName);

        // Optional: you could also change the format here (e.g., convert BMP to PNG)
        // args.ResourceFileName = Path.ChangeExtension(args.ResourceFileName, ".png");
    });
```

> **常見問題：** *如果我想改為內嵌圖片而不是儲存呢？*  
> 只要省略回呼或在回呼內設定 `args.OutputFileName = null;`，儲存器就會自動以 Base64 內嵌圖片。

> **邊緣情況：** 某些舊文件可能包含重複的圖片名稱。上述回呼會覆寫先前的檔案。若要避免，可在檔名後加入 GUID：

```csharp
args.OutputFileName = Path.Combine(folder,
    $"{Path.GetFileNameWithoutExtension(args.ResourceFileName)}_{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}");
```

---

## 第三步：將文件儲存為 markdown 並驗證已儲存的圖片

選項全部設定完成後，最後只需一行程式碼即可寫入 Markdown 檔案與相關圖片。

```csharp
// Step 3: Perform the actual export
string outputPath = @"C:\Exports\MyReport.md";
doc.Save(outputPath, markdownSaveOptions);
```

若一切順利，你會看到：

- `MyReport.md` – 你的來源文件的 Markdown 表示。  
- `md-resources/` – 與 .md 檔案同層的資料夾，內含所有抽取出的圖片（例如 `image001.png`、`image002.jpg`）。  

**範例 Markdown 片段**（由 Aspose.Words 自動產生）：

```markdown
# Sample Report

Here is an introductory paragraph.

![Sample image](md-resources/image001.png)

More text follows...
```

> **專業提示：** 在 VS Code 或任何 Markdown 預覽工具中開啟產生的 `.md` 檔案；圖片應立即顯示，因為相對路徑已正確對應到資料夾結構。

---

## 完整、可執行的範例

以下是一個自包含的主控台程式，你可以直接貼到新建的 .NET 專案中執行。它會建立一個簡單的 Word 文件、加入圖片，然後**從文件建立 markdown**，同時將圖片存入子資料夾。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a sample Word document with an image
        var doc = new Document();
        var builder = new DocumentBuilder(doc);
        builder.Writeln("Hello, this is a test document.");
        builder.InsertImage("sample-image.png"); // Ensure this file exists next to exe

        // 2️⃣ Configure markdown export options (see Step 1 & 2 above)
        var markdownOptions = new MarkdownSaveOptions();
        markdownOptions.ResourceSavingCallback = new IResourceSavingCallback(
            (args) =>
            {
                const string folder = "md-resources/";
                Directory.CreateDirectory(folder);
                args.OutputFileName = Path.Combine(folder, args.ResourceFileName);
            });

        // 3️⃣ Save as markdown (Step 3)
        string outputFolder = Path.Combine(Environment.CurrentDirectory, "output");
        Directory.CreateDirectory(outputFolder);
        string markdownPath = Path.Combine(outputFolder, "ExportedDoc.md");
        doc.Save(markdownPath, markdownOptions);

        Console.WriteLine($"✅ Markdown saved to: {markdownPath}");
        Console.WriteLine("📂 Images saved in: md-resources/");
    }
}
```

**執行後你應該看到的結果**：

```
✅ Markdown saved to: C:\MyProject\output\ExportedDoc.md
📂 Images saved in: md-resources/
```

開啟 `ExportedDoc.md` —— 圖片參考會指向 `md-resources/sample-image.png`，且圖片會在任何 Markdown 檢視器中正確顯示。

---

## 常見變化情境

| 情境 | 如何調整程式碼 |
|----------|----------------------|
| **跳過圖片匯出**（以 Base64 內嵌） | 完全省略 `ResourceSavingCallback`，或在回呼內設定 `args.OutputFileName = null;`。 |
| **變更圖片格式**（例如全部轉為 PNG） | 在回呼內修改 `args.ResourceFileName`，必要時於寫入前轉換串流。 |
| **自訂資料夾名稱** | 將 `"md-resources/"` 替換為你偏好的相對或絕對路徑。 |
| **批次處理多個文件** | 迭代 `Document` 物件集合，重複使用同一個 `MarkdownSaveOptions` 實例（只需確保每次執行前資料夾已清空或使用唯一名稱）。 |

---

## 結論

我們剛剛示範了**如何從文件建立 markdown**、**將文件匯出為 markdown**，以及**使用回呼驅動方式將圖片儲存至子資料夾**的整潔作法。關鍵要點如下：

- 使用 `MarkdownSaveOptions` 取得對匯出的精細控制。  
- 實作 `IResourceSavingCallback` 將圖片導向專屬資料夾，保持 Markdown 的整潔。  
- 同樣的模式也適用於其他資源類型（SVG、音訊）——只要檢查 `args.ResourceType` 即可。  

接下來，你可以探索**使用自訂標題樣式儲存為 markdown**，或將此例程整合至 ASP.NET Web API，回傳包含 `.md` 檔案與其資源的 ZIP。無論哪種方式，這些建構塊現在已在你的工具箱中。

有任何問題，或發現我們未涵蓋的特殊情況？歡迎在下方留言，祝編程愉快！

---

![從文件建立 markdown 範例](placeholder.png "從文件建立 markdown 範例")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}