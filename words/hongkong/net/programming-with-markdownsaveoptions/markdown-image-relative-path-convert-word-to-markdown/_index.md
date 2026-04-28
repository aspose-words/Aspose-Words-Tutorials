---
category: general
date: 2026-04-28
description: 學習如何在將 Word 轉換為 Markdown 時設定圖片的相對路徑、從 Word 中提取圖片，並為匯出的圖片建立資源資料夾。
draft: false
keywords:
- markdown image relative path
- convert word to markdown
- extract images from word
- create resources folder
- export images from docx
language: zh-hant
og_description: 在將 Word 轉換為 Markdown 時設定圖片的相對路徑，提取 Word 中的圖片，並為匯出的圖片建立資源資料夾。
og_title: Markdown 圖片相對路徑 – 將 Word 轉換為 Markdown
tags:
- Aspose.Words
- C#
- Markdown
- Image Export
title: Markdown 圖片相對路徑 – 將 Word 轉換成 Markdown
url: /zh-hant/net/programming-with-markdownsaveoptions/markdown-image-relative-path-convert-word-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# markdown image 相對路徑 – 將 Word 轉換為 Markdown

有沒有曾經在 **convert Word to markdown** 時需要 **markdown image relative path**？你並不孤單。大多數開發者在生成的 Markdown 指向平面資料夾中的圖片時會卡住，導致在靜態網站或 GitHub 倉庫中預期的相對連結結構被破壞。

在本教學中，我們將逐步說明一個完整、端到端的解決方案，該方案 **extracts images from Word**、**creates a resources folder**，並重新寫入圖片引用，使其使用乾淨的 *markdown image relative path*。完成後，你將擁有一個可直接發布的 `.md` 檔案，以及一個整齊排列的 `Resources` 目錄，內含從原始 `.docx` 中提取的所有圖片。

> **你將獲得：** 一個單一的 C# 程式（無需外部腳本）、對每個部分 *why* 重要性的清晰說明，以及一些實用技巧，讓你可以直接複製貼上到自己的專案中。

## 前置條件

- **.NET 6.0** 或更新版本已安裝（你也可以目標 .NET Framework 4.7+，但 .NET 6 是新專案的最佳選擇）。
- **Aspose.Words for .NET**（撰寫本文時的最新 NuGet 套件，版本 23.12）。使用以下方式安裝：
  ```bash
  dotnet add package Aspose.Words
  ```
- 一個實際包含圖片的 Word 文件，假設名稱為 `WithImages.docx`。
- 一個用來存放輸出 markdown 及圖片的資料夾，例如 `C:\Projects\MarkdownExport`。

不需要額外的函式庫；其餘皆由 Aspose.Words 處理。

## 步驟 1：載入來源 Word 文件（convert word to markdown 的起點）

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Adjust the path to point at your own .docx file.
        string sourcePath = @"C:\Projects\MarkdownExport\WithImages.docx";

        // Load the document – this is where Aspose.Words parses the Word file.
        Document doc = new Document(sourcePath);
        
        // The rest of the workflow follows…
    }
}
```

*為什麼這很重要：* 載入文件讓我們可以存取內部節點樹，其中包含稍後需要 **export images from docx** 的圖片部分。如果載入失敗，後續步驟都不會執行，請再次確認路徑與檔案權限。

## 步驟 2：使用自訂回呼設定 `MarkdownSaveOptions`（create resources folder 的核心）

```csharp
// Inside Main(), after loading the document:
string outputFolder = @"C:\Projects\MarkdownExport";
string resourcesFolder = Path.Combine(outputFolder, "Resources");

// Make sure the folder exists before we start saving anything.
Directory.CreateDirectory(resourcesFolder);

// Set up the Markdown save options.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // Hook that runs for every image resource.
    ResourceSavingCallback = new MyMarkdownResourceCallback(resourcesFolder)
};

// Save the document as Markdown.
string markdownPath = Path.Combine(outputFolder, "Doc.md");
doc.Save(markdownPath, mdOptions);
```

請注意我們將 `resourcesFolder` 傳入回呼的建構子——這樣可以讓資料夾路徑保持彈性，避免在程式碼中硬編碼字串。

## 步驟 3：實作回呼以 **creates resources folder** 並重新寫入路徑

```csharp
/// <summary>
/// Handles image extraction and path rewriting for markdown export.
/// </summary>
class MyMarkdownResourceCallback : IResourceSavingCallback
{
    private readonly string _resourcesFolder;

    public MyMarkdownResourceCallback(string resourcesFolder)
    {
        _resourcesFolder = resourcesFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // 1️⃣ Build the full file system path where the image will be stored.
        string targetPath = Path.Combine(_resourcesFolder, args.ResourceFileName);
        
        // 2️⃣ Ensure the directory exists (in case Aspose creates sub‑folders).
        Directory.CreateDirectory(Path.GetDirectoryName(targetPath));

        // 3️⃣ Write the image stream to disk.
        using (FileStream fileStream = File.Create(targetPath))
        {
            args.Stream.CopyTo(fileStream);
        }

        // 4️⃣ Update the markdown reference to use a relative path.
        // This is the crucial line that gives us the markdown image relative path.
        args.ResourceFileName = Path.Combine("Resources", args.ResourceFileName);
    }
}
```

*為什麼這有效：* `args.Stream` 包含原始的圖片位元組。將其複製到我們的 `Resources` 資料夾內的檔案時，我們安全地 **export images from docx**。接著我們將 `args.ResourceFileName` 替換為相對 URL（`Resources/image.png`）。當 Aspose.Words 稍後寫入 markdown 時，會注入這個字串，從而得到期望的 *markdown image relative path*。

## 步驟 4：驗證產生的 Markdown（最終輸出樣式）

在任意文字編輯器中開啟 `Doc.md`。你應該會看到類似以下內容：

```markdown
# Sample Heading

Here is an inline picture:

![Image 0](Resources/Image_0.png)

And a picture inside a table:

![Image 1](Resources/Image_1.jpg)
```

重要的是每個圖片引用都指向 `Resources/...` —— 這就是我們想要的 **markdown image relative path**。

![markdown image relative path example](example.png "markdown image relative path example")

*提示：* 若在支援相對連結的檢視器（如 VS Code 預覽、GitHub 或靜態網站產生器）中開啟 markdown，圖片會正確顯示，且不需額外設定。

## 步驟 5：常見陷阱與專業提示

| Issue | Why it happens | How to fix it |
|-------|----------------|---------------|
| Images end up in the root folder instead of `Resources` | The callback wasn’t attached or `args.ResourceFileName` wasn’t overwritten. | Double‑check that `ResourceSavingCallback` is set **before** calling `doc.Save`. |
| Filenames contain illegal characters | Word sometimes names images with spaces or Unicode symbols. | Use `Path.GetInvalidFileNameChars()` to sanitize `args.ResourceFileName` inside the callback. |
| Large documents take a long time to process | Each image is written synchronously. | Switch to asynchronous I/O (`await args.Stream.CopyToAsync(fileStream)`) if you’re on .NET 6+ and need performance. |
| Relative paths break when the markdown is moved | The path is relative to the markdown file location. | Keep `Doc.md` and the `Resources` folder together, or adjust the callback to use a different relative prefix (e.g., `../assets`). |

## 步驟 6：擴充解決方案（如果需要更多控制）

- **Multiple output formats:** 將 `MarkdownSaveOptions` 替換為 `HtmlSaveOptions` 或 `PdfSaveOptions`，同時保留相同的回呼——Aspose.Words 會對每張圖片呼叫它，無論輸出格式為何。
- **Custom image naming:** 若想重新命名圖片（例如 `figure-01.png`），請在寫入檔案前於回呼中修改 `args.ResourceFileName`。
- **Embedding images as Base64:** 將 `args.ResourceFileName` 設為資料 URI（`data:image/png;base64,...`），並跳過檔案寫入。這對單一檔案的 markdown 匯出非常方便。

## 結論

現在你已擁有一個完整功能的 C# 程式，能 **converts Word to markdown**、**extracts images from word**、**creates a resources folder**，並為每張圖片保證乾淨的 **markdown image relative path**。此程式碼自包含、相容最新的 Aspose.Words 版本，且可輕鬆嵌入任何 .NET 專案。

接下來的步驟？試著將產生的 markdown 輸入 Hugo 或 Jekyll 等靜態網站產生器，或是實驗回呼以直接將圖片嵌入為 Base64 字串。如果遇到特殊情況——例如 SVG 圖片或異常大的檔案——請回顧「常見陷阱」表格；通常只要微調即可解決。

祝程式開發愉快，願你的 markdown 永遠指向正確的資料夾！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}