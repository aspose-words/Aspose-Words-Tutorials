---
category: general
date: 2026-03-17
description: 在 C# 中將 Word 轉換為 Markdown，同時從 DOCX 提取圖片。了解如何提取圖片、設定回呼，以及將 Markdown 儲存至含
  assets 資料夾的目錄。
draft: false
keywords:
- convert word to markdown
- extract images from docx
- how to extract images
- how to convert docx
language: zh-hant
og_description: 在 C# 中將 Word 轉換為 Markdown，並學習如何從 DOCX 中提取圖片。逐步程式碼、說明與技巧，確保順暢轉換。
og_title: 將 Word 轉換為 Markdown 並從 DOCX 提取圖片（C#）– 完整指南
tags:
- Aspose.Words
- C#
- Markdown
- Document Conversion
title: 將 Word 轉換為 Markdown 並從 DOCX 中提取圖片 (C#)
url: /zh-hant/net/programming-with-markdownsaveoptions/convert-word-to-markdown-extract-images-from-docx-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 將 Word 轉換為 Markdown 並從 DOCX 中提取圖片 (C#)

是否曾經需要 **將 Word 轉換為 Markdown**，卻被神祕消失的圖片卡住？你並不是唯一遇到這個問題的人。在許多實務專案——例如靜態網站產生器、文件化流程或無頭 CMS——你往往同時需要 Markdown 文字 **以及** 原始圖片，且這些圖片要整齊地放在 *assets* 資料夾中。  

在本教學中，你將會看到 **如何使用 Aspose.Words for .NET**，在 **將 docx 轉換為 markdown** 的同時 **提取圖片**。我們會一步步說明如何設定資源儲存回呼、處理檔名重複等邊緣情況，最終得到一個乾淨的資料夾結構，直接供靜態網站建構工具使用。  

## 你將學會

- 載入 `.docx` 檔並為轉換做準備。  
- 實作 `IResourceSavingCallback` 以 **從 DOCX 提取圖片**。  
- 設定 `MarkdownSaveOptions`，讓 markdown 正確引用 assets。  
- 執行程式碼，驗證 `.md` 檔與圖片資料夾皆如預期產生。  

**先備條件** – 需要 .NET 6+（或 .NET Framework 4.7.2+）以及 Aspose.Words 授權（免費試用版即可完成本示範）。具備 C# 與檔案 I/O 基礎會更順利，但本指南是自足的。

![Convert Word to Markdown folder layout](https://example.com/convert-word-to-markdown.png "Convert Word to Markdown folder layout")

*轉換後的資料夾結構 – markdown 檔與存放所有提取圖片的 `assets` 資料夾並列。*

---

## Step 1: Load the Source Document (convert word to markdown)

首先，我們讀取想要轉成 markdown 的 `.docx`。Aspose.Words 會將底層 OPC 格式抽象化，只需一行程式碼即可完成。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

// Adjust these paths to match your environment.
string inputPath  = Path.Combine("YOUR_DIRECTORY", "input.docx");
string outputDir  = Path.Combine("YOUR_DIRECTORY", "output");

// Ensure the output folder exists.
Directory.CreateDirectory(outputDir);

// Load the DOCX file.
Document document = new Document(inputPath);
```

*為什麼這很重要：* 先載入文件會得到一個 `Document` 物件，裡面同時包含文字內容 **以及** 嵌入的資源（圖片、圖表等）。若缺少這一步，之後就無法 **提取圖片**。

---

## Step 2: Create a Callback to **how to extract images** from the DOCX

Aspose.Words 會在每次需要寫入資源（例如圖片）時呼叫你的 `IResourceSavingCallback`。透過自訂實作，我們可以決定 **檔案存放位置** 以及 **markdown 如何引用**。

```csharp
/// <summary>
/// Saves each extracted resource (image, video, etc.) into an "assets" sub‑folder
/// and rewrites the markdown reference to point at that relative path.
/// </summary>
class MyMarkdownResourceCallback : IResourceSavingCallback
{
    private readonly string _outputDirectory;

    public MyMarkdownResourceCallback(string outputDirectory)
    {
        _outputDirectory = outputDirectory;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // 1️⃣ Build the assets folder path.
        string assetsFolder = Path.Combine(_outputDirectory, "assets");
        Directory.CreateDirectory(assetsFolder);

        // 2️⃣ Resolve potential filename collisions.
        string safeFileName = GetUniqueFileName(assetsFolder, args.ResourceFileName);

        // 3️⃣ Write the resource stream to disk.
        string assetPath = Path.Combine(assetsFolder, safeFileName);
        using (FileStream fs = new FileStream(assetPath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }

        // 4️⃣ Tell the markdown writer the *relative* path it should embed.
        args.ResourceFileName = Path.Combine("assets", safeFileName);
        args.KeepResourceStreamOpen = false; // we already closed it
    }

    // Helper: ensure we don't overwrite an existing file.
    private string GetUniqueFileName(string folder, string originalName)
    {
        string filePath = Path.Combine(folder, originalName);
        if (!File.Exists(filePath))
            return originalName;

        string nameWithoutExt = Path.GetFileNameWithoutExtension(originalName);
        string ext = Path.GetExtension(originalName);
        int counter = 1;

        while (File.Exists(filePath))
        {
            string candidate = $"{nameWithoutExt}_{counter}{ext}";
            filePath = Path.Combine(folder, candidate);
            counter++;
        }

        return Path.GetFileName(filePath);
    }
}
```

**重點說明**  

- **為什麼使用 assets 子資料夾？** 將圖片與 `.md` 檔分開，符合大多數靜態網站產生器的預期布局。  
- **衝突處理** 可避免同一張圖片出現多次時產生「檔案已存在」的例外。  
- 設定 `args.KeepResourceStreamOpen = false` 讓 Aspose 知道我們已自行處理串流，避免記憶體泄漏。

---

## Step 3: Wire the Callback into **MarkdownSaveOptions**

現在告訴 Aspose.Words 在寫入資源時使用我們的回呼。這就是 **將 docx 轉換為 markdown** 同時保留媒體的核心。

```csharp
// Instantiate the callback with the output directory.
var resourceCallback = new MyMarkdownResourceCallback(outputDir);

// Configure markdown options.
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    // The callback does the heavy lifting for image extraction.
    ResourceSavingCallback = resourceCallback,

    // Optional: make the markdown more GitHub‑friendly.
    ExportImagesAsBase64 = false, // we want separate files, not embedded data URIs.
    ExportHeadersFooters = true,
    ExportDocumentProperties = false
};
```

*為什麼將 `ExportImagesAsBase64 = false`：* 以 Base64 編碼的圖片會讓 markdown 檔變得龐大，失去使用乾淨 `assets` 資料夾的意義。關閉此設定後，markdown 只會留下簡單的 `![](assets/image.png)` 參照。

---

## Step 4: Save the Document as Markdown

所有設定完成後，只需一行程式碼即可同時產生 `.md` 檔與圖片。

```csharp
string markdownPath = Path.Combine(outputDir, "output.md");

// Save the document.
document.Save(markdownPath, markdownOptions);
Console.WriteLine($"✅ Conversion complete! Markdown saved to: {markdownPath}");
Console.WriteLine($"📁 Extracted images are in: {Path.Combine(outputDir, "assets")}");
```

**執行結果應該會看到**  

- `output.md` 內的 markdown 文字，且每個圖片標籤皆指向 `assets/<image_name>`。  
- 一個 `assets` 資料夾，內含從 `input.docx` 中嵌入的 PNG、JPEG 或 GIF 檔案。  

在任意 markdown 檢視器（VS Code、GitHub、MkDocs）開啟 `output.md`，即可看到圖片如同在 Word 文件中呈現的樣子。

---

## Handling Common Pitfalls (FAQ)

### 如果 DOCX 中出現重複的圖片名稱該怎麼辦？
我們的 `GetUniqueFileName` 輔助函式會在檔名後加上遞增的後綴（`image_1.png`、`image_2.png`…），確保不會覆寫任何檔案。

### 是否需要 Aspose.Words 的授權？
試用版足以進行測試，但 **正式上線** 時應購買授權，以移除評估水印並取得完整效能。

### 能否一次批次轉換多個 Word 檔？
當然可以。將載入與儲存的程式碼包在 `foreach (var file in Directory.GetFiles(sourceFolder, "*.docx"))` 迴圈中，重複使用同一個 `MyMarkdownResourceCallback` 實例（或視需求為每個檔案建立新實例，以產生獨立的 assets 資料夾）。

### 非圖片資源（例如嵌入的 PDF）怎麼處理？
回呼會收到 **任何** 資源類型。你可以檢查 `args.ResourceType`，決定是保留、忽略或重新命名。

### 此作法是否相容 .NET Core？
相容。上述程式碼以 .NET 6 為目標，但只要調整專案檔，即可降級至 .NET Framework 4.7.2。Aspose.Words 同時支援兩種執行環境。

---

## Pro Tips & Best Practices

- **保持 assets 資料夾整潔** – 批次轉換後，可執行簡易腳本刪除可能產生的零位元檔案。  
- **使用具意義的檔名** – 若需要可讀性高的圖片名稱，可從 `args.ResourceFileName` 取得原始 `AltText`（若有），並納入檔名。  
- **版本控制** – 只將 markdown 放入 repo，assets 資料夾可在 CI 流程中自動產生，減少儲存庫體積。  
- **效能優化** – 處理大型文件時，可將 `markdownOptions.SaveFormat = SaveFormat.Markdown;`，先寫入 `MemoryStream` 再輸出，以降低記憶體佔用。

---

## Full Working Example (Copy‑Paste Ready)

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

/// <summary>
/// Demonstrates converting a DOCX to Markdown while extracting images into an assets folder.
/// </summary>
class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // 1️⃣ Paths – adjust these to your environment.
        // -----------------------------------------------------------------
        string inputPath = Path.Combine("YOUR_DIRECTORY", "input.docx");
        string outputDir = Path.Combine("YOUR_DIRECTORY", "output");
        Directory.CreateDirectory(outputDir);

        // -----------------------------------------------------------------
        // 2️⃣ Load the source document.
        // -----------------------------------------------------------------
        Document doc = new Document(inputPath);

        // -----------------------------------------------------------------
        // 3️⃣ Set up the resource‑saving callback.
        // -----------------------------------------------------------------
        var callback = new MyMarkdownResourceCallback(outputDir);

        // -----------------------------------------------------------------
        // 4️⃣ Configure Markdown options.
        // -----------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = callback,
            ExportImagesAsBase64 = false,
            ExportHeadersFooters = true,
            ExportDocumentProperties = false
        };

        // -----------------------------------------------------------------
        // 5️⃣ Save as Markdown.
        // -----------------------------------------------------------------
        string markdownFile = Path

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}