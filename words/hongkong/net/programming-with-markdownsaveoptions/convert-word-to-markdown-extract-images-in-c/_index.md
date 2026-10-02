---
category: general
date: 2026-02-18
description: 將 Word 轉換成 Markdown，並使用 Aspose.Words 從 docx 提取圖片。了解如何使用完整的 C# 範例從 Word
  產生 Markdown。
draft: false
keywords:
- convert word to markdown
- extract images from docx
- how to extract images
- generate markdown from word
- how to convert docx to markdown
language: zh-hant
og_description: 使用 Aspose.Words 將 Word 轉換為 Markdown，並從 docx 中提取圖片。本指南逐步說明如何從 Word
  產生 Markdown。
og_title: 將 Word 轉換為 Markdown – 在 C# 中提取圖像
tags:
- C#
- Aspose.Words
- Markdown
- Document Conversion
title: 將 Word 轉換為 Markdown – 在 C# 中提取圖片
url: /zh-hant/net/programming-with-markdownsaveoptions/convert-word-to-markdown-extract-images-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Convert Word to Markdown – Extract Images in C#

有沒有想過要 **將 Word 轉換成 Markdown** 同時把 `.docx` 檔案裡的每張圖片都抽出來？你並不是唯一有這個需求的人。許多開發者在需要把原本用 Word 撰寫的合約、部落格文章或技術規格，轉成乾淨的 markdown 時，常常卡住。好消息是？只要使用 Aspose.Words for .NET，幾行程式碼就能完成，而且最終會得到一個 markdown 檔案 *外加* 一個放置原始圖片的資料夾。

在本教學中，我們會一步步示範一個完整、可直接執行的 C# 程式，**從 Word 產生 markdown**、從 docx 抽取圖片，並把所有檔案寫入磁碟。完成後，你將清楚知道如何 **將 docx 轉換成 markdown**、如何 **從 docx 抽取圖片**，以及如何依自己的專案需求微調這個流程。

## 你需要的環境

- **Aspose.Words for .NET**（v23.10 或更新版本）。可使用 `Install-Package Aspose.Words` 取得免費試用的 NuGet 套件。
- .NET 6+ SDK（任何近期版本皆可）。
- 一個包含至少一張圖片的範例 `input.docx`。
- 一個你想放置 markdown 與圖片資源的資料夾。

不需要其他第三方函式庫。以下程式碼已包含所有必須的 `using` 指示，直接貼到 Console App 中按 **F5** 即可執行。

![Convert Word to Markdown example](/images/convert-word-to-markdown.png "convert word to markdown")

*Image alt text: convert word to markdown illustration showing a Word file turning into a Markdown file with images.*

---

## 步驟 1：載入來源 Word 文件

首先要把 Aspose.Words 指向你要轉換的檔案。把 `Document` 想成是通往 `.docx` 內部所有內容（文字、表格、圖片等）的入口。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 👉 Step 1: Load the Word document that contains images.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document document = new Document(inputPath);
```

> **為什麼這很重要：** 只載入一次文件即可降低記憶體使用量，且讓函式庫能檢查內部封裝結構，這對之後抽取圖片相當關鍵。

---

## 步驟 2：告訴 Aspose.Words 如何儲存為 Markdown

Aspose.Words 內建 `MarkdownSaveOptions` 類別，可讓你控制從換行字元到外部資源（如圖片）儲存資料夾等所有細節。

```csharp
        // 👉 Step 2: Configure Markdown save options with a resource‑saving callback.
        MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
        {
            // The callback fires for each external resource (e.g., an image) that needs a file.
            ResourceSavingCallback = new ResourceSavingCallback(args =>
            {
                // 👉 Step 3 inside the callback: decide where and how to store each image.
                string resourceFolder = @"YOUR_DIRECTORY\markdown-resources";
                Directory.CreateDirectory(resourceFolder); // creates if it doesn’t exist

                // Give each image a unique name to avoid collisions.
                string uniqueFileName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.FileName)}";
                args.FileName = Path.Combine(resourceFolder, uniqueFileName);

                // Optional: you could compress PNGs here by manipulating args.Stream.
            })
        };
```

> **為什麼要使用回呼函式？** `ResourceSavingCallback` 讓你完全掌控每張抽取圖片的檔名與儲存位置。若不使用，Aspose 會把所有檔案丟到同一資料夾，且使用通用名稱，對大型專案來說會相當雜亂。

---

## 步驟 3：將文件儲存為 Markdown

設定完成後，儲存只需要一行程式碼。函式庫會負責繁重的工作：把段落、標題、清單、表格轉成 markdown，並透過先前設定的回呼，把每張圖片寫入你指定的資料夾。

```csharp
        // 👉 Step 4: Save the document as a Markdown file.
        string outputPath = @"YOUR_DIRECTORY\output.md";
        document.Save(outputPath, markdownOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown saved to: {outputPath}");
        Console.WriteLine($"Images extracted to: {Path.GetDirectoryName(outputPath)}\\markdown-resources");
    }
}
```

### 預期結果

- `output.md` 內含 markdown 語法（例如 `![Image](markdown-resources/img_1234.png)`）。
- `markdown-resources` 資料夾保存了原始 Word 檔案中的所有圖片，且每張都有唯一名稱。

在任意 markdown 檢視器（VS Code、GitHub、或靜態網站產生器）開啟 `output.md`，你應該會看到與原始 Word 版面相同的文字與圖片，只是以輕量、適合網路的格式呈現。

---

## 步驟 4：常見變形與例外情況

### 4.1 處理已存在的資源資料夾

若多次執行轉換，舊的圖片可能會殘留。可在每次執行前加入簡易的防護程式碼，先清空資料夾：

```csharp
if (Directory.Exists(resourceFolder))
{
    foreach (var file in Directory.GetFiles(resourceFolder))
        File.Delete(file);
}
else
{
    Directory.CreateDirectory(resourceFolder);
}
```

### 4.2 變更圖片格式

有時需要把所有圖片轉成 JPEG 以利網頁優化。只要在回呼裡重新編碼串流即可：

```csharp
using (var img = System.Drawing.Image.FromStream(args.Stream))
{
    var jpegStream = new MemoryStream();
    img.Save(jpegStream, System.Drawing.Imaging.ImageFormat.Jpeg);
    jpegStream.Position = 0;
    args.Stream = jpegStream;
    args.FileName = Path.ChangeExtension(args.FileName, ".jpg");
}
```

> **小技巧：** `System.Drawing.Common` 只在 Windows 上完整支援；在 Linux/macOS 上建議改用 `ImageSharp` 以確保跨平台相容。

### 4.3 保留表格樣式

如果你的 Word 文件大量使用表格格式，可調整 `MarkdownSaveOptions`：

```csharp
markdownOptions.ExportTableColumnWidths = true;   // keeps column widths
markdownOptions.ExportTableBorders = true;       // adds markdown border syntax
```

### 4.4 使用不同的輸出目錄

`Save` 方法接受任意絕對或相對路徑。於 CI/CD 流程中，你可以指向暫存的建置資料夾：

```csharp
document.Save(Path.Combine(Path.GetTempPath(), "doc.md"), markdownOptions);
```

---

## 常見問答

**Q: 這個方法能處理 `.doc`（二進位）檔案嗎？**  
A: 能。`new Document("file.doc")` 會自動偵測格式，因而同時支援 `.doc` 與 `.docx`。

**Q: 若 Word 檔案內含嵌入的 SVG 圖片，會怎樣？**  
A: Aspose.Words 會以原始格式抽取 SVG。若需要點陣圖版本，必須在回呼中自行將 SVG 串流轉換（例如使用 `Svg.Skia`）。

**Q: 能否完全不抽取圖片？**  
A: 設定 `markdownOptions.ExportImagesAsBase64 = true;` 即可把圖片直接以 data URI 內嵌於 markdown，適合產出單一檔案的 README。

---

## 重點回顧與後續行動

我們剛完成了完整的 **convert word to markdown** 工作流程：

1. 載入 `.docx`。
2. 使用 `MarkdownSaveOptions` 並設定 `ResourceSavingCallback`。
3. 儲存文件，讓回呼將每張圖片寫入專屬資料夾。

整個解決方案不到 50 行 C# 程式碼。

如果想更進一步，可考慮：

- **產生靜態網站**：將 markdown 匯入 Hugo、Jekyll 等產生器。
- **批次處理**：把程式碼包在 `foreach` 迴圈裡，一次處理多個檔案。
- **進階圖片處理**：在回呼中即時調整大小、加水印或轉檔。

盡情試驗吧——改寫回呼邏輯、調整儲存選項，或把它整合到更大的文件流水線中。未來的可能性無限，而你現在已擁有堅實的基礎，能在任何 **generate markdown from word** 專案中得心應手。

祝程式開發順利，願你的 markdown 永遠乾淨，圖片永遠不會遺失！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}