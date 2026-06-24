---
category: general
date: 2026-05-04
description: 了解如何在使用 Aspose.Words 將 DOCX 轉換為 Markdown 時保存圖像。本指南亦示範如何從 Word 中提取圖像以及將
  Word 儲存為 Markdown。
draft: false
keywords:
- how to save images
- convert docx to markdown
- extract images from word
- how to convert docx
- save word as markdown
language: zh-hant
og_description: 如何在使用 Aspose.Words 將 DOCX 轉換為 Markdown 時保存圖片。逐步指南，附完整 C# 程式碼。
og_title: 如何儲存圖片 – 使用 Aspose.Words 將 DOCX 轉換為 Markdown
tags:
- Aspose.Words
- C#
- Markdown conversion
title: 如何儲存圖像 – 使用 Aspose.Words 將 DOCX 轉換為 Markdown
url: /zh-hant/net/programming-with-markdownsaveoptions/how-to-save-images-convert-docx-to-markdown-with-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何儲存圖片 – 使用 Aspose.Words 將 DOCX 轉換為 Markdown

有沒有想過 **如何儲存圖片**，在把 Word 檔案轉成 Markdown 時？你並不是唯一遇到這個問題的人。許多開發者在轉換時會遇到圖片變成斷掉的連結，甚至完全遺失的情況。好消息是 Aspose.Words 提供了細緻的控制，讓你可以從 Word 中抽取圖片、決定儲存位置，同時產生乾淨的 Markdown 輸出。

在本教學中，我們將逐步說明一個完整、可直接執行的 C# 範例，展示 **如何儲存圖片** 到指定資料夾，同時將 `.docx` 轉成 `.md`。過程中也會提及 **convert docx to markdown**、**extract images from word**，以及 **how to convert docx** 的更廣泛議題，讓你 **save word as markdown** 時不會遺失任何資源。

## 前置條件

- .NET 6.0 或更新版本（API 在 .NET Framework 4.7+ 上的行為相同）
- 有效的 Aspose.Words 授權或免費試用版（免費版會在輸出檔案加上浮水印，但程式碼功能相同）
- 已包含圖片的 Word 文件（例如 `DocWithImages.docx`）
- Visual Studio 2022 或任何能編譯 C# 專案的編輯器

> **專業提示：** 若使用試用版，仍可測試圖片儲存的邏輯；只要記得最終產出的 PDF/MD 會帶有試用浮水印。

## 解決方案概觀

整體流程如下：

1. 使用 `Document` 載入來源 `.docx`。
2. 建立 `MarkdownSaveOptions` 物件，並掛接 `IResourceSavingCallback`。
3. 在回呼中決定每張圖片的資料夾與檔名。
4. 將文件儲存為 Markdown；回呼會把每張圖片寫入磁碟。

這就是 **如何儲存圖片** 在轉換過程中的核心。相同的模式也適用於其他資源類型（字型、CSS 等），如果你有需要的話。

## 步驟 1 – 載入包含圖片的 DOCX

首先，我們需要一個指向欲轉換 Word 檔的 `Document` 實例。這裡不需要特別技巧，只要呼叫建構子即可。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// Adjust the path to where your .docx lives
string sourcePath = @"C:\Docs\DocWithImages.docx";

Document sourceDoc = new Document(sourcePath);
```

> **為什麼重要：** 載入文件時 Aspose 會解析 Word 的 XML，任何缺少的字型或損壞的部分都會在此拋出例外，讓你在開始儲存圖片前就能發現問題。

## 步驟 2 – 設定 MarkdownSaveOptions 並加入圖片儲存回呼

`MarkdownSaveOptions` 類別允許透過 `ResourceSavingCallback` 在儲存過程中介入。此回呼會為每個外部資源（圖片、CSS 等）收到一個 `ResourceSavingArgs` 物件。

```csharp
// Define where the Markdown file will be written
string markdownPath = @"C:\Docs\Doc.md";

// Create the options object and attach the callback
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    // This is the heart of how to save images
    ResourceSavingCallback = new ImageSavingCallback()
};
```

### 回呼實作

以下是完整的 `ImageSavingCallback` 實作。它會在 Markdown 檔旁建立 `Images` 子資料夾，為每張圖片給予順序名稱（`img_0.png`、`img_1.jpg`…），並可選擇將圖片串流至其他位置（例如雲端儲存桶）。

```csharp
class ImageSavingCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Only handle images; other resources (like CSS) are ignored here
        if (args.ResourceType != ResourceType.Image)
            return;

        // Build a folder called "Images" right next to the markdown file
        string markdownDir = Path.GetDirectoryName(args.DestinationFileName);
        string imagesFolder = Path.Combine(markdownDir, "Images");
        Directory.CreateDirectory(imagesFolder);

        // Compose a safe file name: img_<index>.<original extension>
        string newFileName = $"img_{args.Index}{Path.GetExtension(args.FileName)}";
        args.FileName = Path.Combine(imagesFolder, newFileName);

        // If you wanted to push the image to a remote store, you could replace args.Stream here.
        // For now we just let Aspose write to the local file system.
    }
}
```

> **這對你有何幫助：** 透過自訂 `args.FileName`，你可以精確控制 **如何儲存圖片**——無論是放在單一資料夾、依日期分層，甚至存入資料庫 BLOB。回呼會對每張圖片執行一次，省去事後手動調整 Markdown 的麻煩。

## 步驟 3 – 將文件儲存為 Markdown

當選項與回呼都設定好後，實際的轉換只需要一行程式碼。

```csharp
// Save the document; the callback will fire for each image automatically
sourceDoc.Save(markdownPath, markdownOptions);
```

執行完畢後，你會得到：

- `Doc.md` – 你的 Word 內容的 Markdown 版。
- `Images\img_0.png`、`Images\img_1.jpg`、… – 從原始 DOCX 抽出的每張圖片。

## 完整、可直接執行的範例

把所有程式碼組合起來，以下是一個可直接貼到新 C# 專案的完整主控台應用程式。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

namespace DocxToMarkdownDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -----------------------------------------------------------------
            // 1️⃣ Load the source DOCX that contains images
            // -----------------------------------------------------------------
            string sourcePath = @"C:\Docs\DocWithImages.docx";
            Document sourceDoc = new Document(sourcePath);

            // -----------------------------------------------------------------
            // 2️⃣ Prepare Markdown options with a custom image‑saving callback
            // -----------------------------------------------------------------
            string markdownPath = @"C:\Docs\Doc.md";
            MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
            {
                ResourceSavingCallback = new ImageSavingCallback()
            };

            // -----------------------------------------------------------------
            // 3️⃣ Perform the conversion – this is where we actually learn
            //     how to save images while converting docx to markdown
            // -----------------------------------------------------------------
            sourceDoc.Save(markdownPath, markdownOptions);

            Console.WriteLine("Conversion complete!");
            Console.WriteLine($"Markdown file: {markdownPath}");
            Console.WriteLine("Images folder: " + Path.Combine(Path.GetDirectoryName(markdownPath), "Images"));
        }
    }

    // -----------------------------------------------------------------
    // 4️⃣ Callback that decides where each image ends up
    // -----------------------------------------------------------------
    class ImageSavingCallback : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            if (args.ResourceType != ResourceType.Image)
                return;

            string markdownDir = Path.GetDirectoryName(args.DestinationFileName);
            string imagesFolder = Path.Combine(markdownDir, "Images");
            Directory.CreateDirectory(imagesFolder);

            string newFileName = $"img_{args.Index}{Path.GetExtension(args.FileName)}";
            args.FileName = Path.Combine(imagesFolder, newFileName);

            // Optional: redirect the image stream elsewhere (e.g., cloud storage)
            // args.Stream = new MemoryStream(); // your custom stream here
        }
    }
}
```

### 預期結果

執行程式後：

- 在任意文字編輯器開啟 `C:\Docs\Doc.md`，會看到類似 `![](Images/img_0.png)` 的 Markdown 圖片連結。
- `Images` 資料夾會包含每一張抽出的圖片，名稱依序編號。
- 只要支援本機圖片的 Markdown 檢視器（VS Code 預覽、GitHub 等）都能正確顯示。

## 常見問題 (FAQs)

### 這能支援其他圖片格式嗎（SVG、TIFF）？

可以。`Path.GetExtension(args.FileName)` 會保留原始副檔名，所以 SVG、TIFF、BMP 甚至 EMF 都會原樣儲存。唯一需要注意的是部分 Markdown 渲染器可能不支援直接顯示 SVG，若有此需求可先將 SVG 轉成 PNG。

### 若想把圖片以 Base64 內嵌而不是獨立檔案，該怎麼做？

在 `ResourceSaving` 內，你可以改寫為寫入記憶體串流，然後自行修改 Markdown 連結。Aspose 並未提供直接「內嵌 Base64」的開關，但回呼讓你完全掌控 `args.Stream`。

### 與內建的 `ExportImages` 方法有何不同？

`ExportImages` 只會把所有圖片抽取到資料夾，**不會**產生 Markdown。使用回呼同時完成兩件事，確保 `.md` 中的圖片檔名與實際檔案一致，這正是 **如何正確儲存圖片** 的關鍵。

### 能一次批次轉換多個 DOCX 嗎？

當然可以。把核心邏輯包在 `foreach (var file in Directory.GetFiles(..., "*.docx"))` 迴圈裡，調整輸出路徑，並重複使用同一個 `ImageSavingCallback`。記得每個文件都要重新建立 `MarkdownSaveOptions`，因為 `args.DestinationFileName` 會隨每次迭代而變化。

## 邊緣情況與最佳實踐

| 情境 | 需要注意的地方 | 推薦的解決方式 |
|-----------|----------------------|-----------------|
| **大型 DOCX（數百 MB）** | 載入時可能產生記憶體壓力 | 使用 `LoadOptions` 並設定 `LoadOptions.LoadFormat = LoadFormat.Docx` 以串流方式載入部份內容 |
| **圖片名稱衝突** | 若目標資料夾已存在同名 `img_0.png` 可能被覆寫 | 在檔名後加 GUID：`newFileName = $"img_{args.Index}_{Guid.NewGuid():N}{Path.GetExtension(args.FileName)}"` |
| **輸出資料夾唯讀** | 儲存時會拋出 `UnauthorizedAccessException` | 確保執行程序具備寫入權限，或改用可寫入的路徑 |
| **非圖片資源（CSS、字型）** | 回呼也會收到這類資源 | 用 `if (args.ResourceType != ResourceType.Image) return;` 進行過濾（範例已示） |
| **Unicode 檔名** | 某些檔案系統可能無法正確處理特殊字元 | 使用 `Path.GetInvalidFileNameChars()` 先清理 `args.FileName` 再指定 |

## 相關主題推薦

- **convert docx to markdown** 搭配自訂標題樣式（使用 `MarkdownSaveOptions.ExportImagesAsBase64` 內嵌圖片）
- **extract images from word** 使用 `Document.GetChildNodes(NodeType.Shape,` 

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}