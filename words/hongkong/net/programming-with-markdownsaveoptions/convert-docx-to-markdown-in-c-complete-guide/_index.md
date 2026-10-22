---
category: general
date: 2026-03-25
description: 使用 Aspose.Words 快速將 DOCX 轉換為 Markdown，並從 Word 中提取圖片。一步一步學習完整程式碼。
draft: false
keywords:
- convert docx to markdown
- extract images from word
language: zh-hant
og_description: 使用 Aspose.Words 將 DOCX 轉換為 Markdown 並從 Word 中提取圖片。跟隨此完整教學，即可獲得即時可執行的解決方案。
og_title: 在 C# 中將 DOCX 轉換為 Markdown – 步驟指南
tags:
- Aspose.Words
- C#
- Markdown
title: 在 C# 中將 DOCX 轉換為 Markdown – 完整指南
url: /zh-hant/net/programming-with-markdownsaveoptions/convert-docx-to-markdown-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words 將 DOCX 轉換為 Markdown

是否曾經需要 **將 DOCX 轉換為 markdown**，卻不確定如何保留內嵌圖片？你並不孤單——許多開發者在將 Word 內容搬移到靜態網站生成器或文件倉庫時，都會遇到這個問題。  
好消息是，Aspose.Words for .NET 能為你完成繁重的工作，且只需一個小 callback，就能同時 **從 Word 檔案中擷取圖片**。

在本教學中，我們將示範一個實務範例：載入 `.docx`、將其儲存為 Markdown 檔案，並將每張圖片寫入專屬資料夾。完成後，你將擁有一個可直接執行的 Console 應用程式，隨時可以放入任何 .NET 專案中使用。

> **專業提示：** 如果你只需要文字而不在乎圖片，可以完全省略 `ResourceSavingCallback`——程式碼仍會產生乾淨的 Markdown。

## 需求環境

- **Aspose.Words for .NET**（最新版本，例如 24.12）。可從 NuGet 取得：`Install-Package Aspose.Words`。
- **.NET 6.0** 或更新版本（API 亦支援 .NET Framework，但 .NET 6 提供最佳效能）。
- 任意簡易的 Console 專案或你偏好的 C# 主機環境。
- 一個包含至少一張圖片的輸入 Word 檔案（`input.docx`），以便觀察圖片抽取的效果。

就這樣——不需要額外的函式庫，也不需要繁雜的命令列工具。讓我們開始吧。

![將 docx 轉換為 markdown 範例](images/convert-docx-to-markdown.png)

*圖片說明文字：將 docx 轉換為 markdown 範例*

## 步驟 1 – 建立專案並加入 Aspose.Words

為了保持整潔，先建立一個全新的 Console 應用程式：

```bash
dotnet new console -n DocxToMarkdownDemo
cd DocxToMarkdownDemo
dotnet add package Aspose.Words
```

開啟 `Program.cs`，清除自動產生的程式碼。我們稍後會貼上完整解決方案，現在只要確保專案能成功編譯即可。

## 步驟 2 – 載入來源 DOCX

首先，我們告訴 Aspose.Words 讀取 Word 檔案。此操作 **快速**——函式庫會解析文件結構，且不會開啟 Word 本身。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// Path to your source document
string inputPath = Path.Combine("YOUR_DIRECTORY", "input.docx");

// Load the DOCX into a Document object
Document doc = new Document(inputPath);
```

為什麼要使用 `Path.Combine` 包裝路徑？這樣可讓程式碼在 Windows、macOS 與 Linux 之間保持可移植性——當你將專案搬移至 CI 流程時，會特別有感。

## 步驟 3 – 使用資源 Callback 設定 Markdown 儲存選項

當你要求 Aspose.Words 以 Markdown 格式儲存時，預設會將圖片以 Base64 字串內嵌。對於小圖示尚可接受，但對於較大的照片會使檔案體積激增。因此，我們改為掛接一個 **resource‑saving callback**，將每張圖片寫入磁碟並更新 Markdown 連結。

```csharp
// Define where the Markdown and resources will live
string outputDir = Path.Combine("YOUR_DIRECTORY", "Output");
string resourcesDir = Path.Combine(outputDir, "Resources");

// Ensure directories exist
Directory.CreateDirectory(outputDir);
Directory.CreateDirectory(resourcesDir);

// Create Markdown options and plug in the callback
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new MyResourceSaver(resourcesDir)
};
```

請注意，我們將 `resourcesDir` 傳入 callback 的建構子——這樣可將路徑邏輯從 callback 本身抽離，使類別更具可重用性。

## 步驟 4 – 實作 Resource‑Saving Callback

此 callback 實作 `IResourceSavingCallback` 介面。對於 Aspose.Words 想要寫入的每張圖片，會提供一個 `ResourceSavingArgs` 物件。我們決定 **儲存位置**、給予唯一檔名，然後告訴引擎跳過預設的儲存行為。

```csharp
class MyResourceSaver : IResourceSavingCallback
{
    private readonly string _resourcesFolder;

    public MyResourceSaver(string resourcesFolder)
    {
        _resourcesFolder = resourcesFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Build a unique, deterministic file name
        string ext = Path.GetExtension(args.FileName);          // e.g., ".png"
        string fileName = $"img_{args.Index}{ext}";            // img_0.png, img_1.jpg, …

        // Full path on disk
        string filePath = Path.Combine(_resourcesFolder, fileName);

        // Write the image bytes
        using (FileStream fs = new FileStream(filePath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }

        // Update the Markdown URI so it points to the saved image
        args.Uri = $"Resources/{fileName}";

        // Tell Aspose.Words we handled the saving
        args.Cancel = true;
    }
}
```

**為什麼重要：** 透過設定 `args.Uri`，我們能精確控制最終 `.md` 檔案中圖片的引用方式。相對路徑 `Resources/img_0.png` 無論在 VS Code、GitHub，或是靜態網站生成器中開啟 Markdown，都能正常運作。

## 步驟 5 – 將文件儲存為 Markdown

現在進入最後一步：請 Aspose.Words 寫入 Markdown 檔案。先前掛接的 callback 會自動對每張圖片觸發。

```csharp
// Destination Markdown file
string markdownPath = Path.Combine(outputDir, "output.md");

// Perform the conversion
doc.Save(markdownPath, mdOptions);
```

執行完畢後，你將得到：

- `output.md` – 原始 Word 內容的乾淨 Markdown 表示。
- `Resources/` 資料夾 – 包含從 DOCX 中抽取的所有圖片。

## 完整範例程式

以下是 **完整、可直接複製貼上的** 程式碼。將 `YOUR_DIRECTORY` 替換為存放 `input.docx` 的絕對或相對路徑。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

class Program
{
    static void Main()
    {
        // ------------------------------------------------------------
        // 1️⃣  Define paths
        // ------------------------------------------------------------
        string baseDir = Path.Combine(Environment.CurrentDirectory, "DemoFiles");
        string inputPath = Path.Combine(baseDir, "input.docx");
        string outputDir = Path.Combine(baseDir, "Output");
        string resourcesDir = Path.Combine(outputDir, "Resources");

        // Create folders if they don't exist
        Directory.CreateDirectory(outputDir);
        Directory.CreateDirectory(resourcesDir);

        // ------------------------------------------------------------
        // 2️⃣  Load the DOCX
        // ------------------------------------------------------------
        Document doc = new Document(inputPath);

        // ------------------------------------------------------------
        // 3️⃣  Prepare Markdown options with a resource callback
        // ------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new MyResourceSaver(resourcesDir)
        };

        // ------------------------------------------------------------
        // 4️⃣  Save as Markdown
        // ------------------------------------------------------------
        string markdownPath = Path.Combine(outputDir, "output.md");
        doc.Save(markdownPath, mdOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown file: {markdownPath}");
        Console.WriteLine($"Images folder: {resourcesDir}");
    }
}

// -----------------------------------------------------------------
// Callback that writes each image to the Resources folder
// -----------------------------------------------------------------
class MyResourceSaver : IResourceSavingCallback
{
    private readonly string _resourcesFolder;

    public MyResourceSaver(string resourcesFolder)
    {
        _resourcesFolder = resourcesFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Create a deterministic file name like img_0.png
        string extension = Path.GetExtension(args.FileName);
        string fileName = $"img_{args.Index}{extension}";
        string filePath = Path.Combine(_resourcesFolder, fileName);

        // Persist the image bytes
        using (FileStream fs = new FileStream(filePath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }

        // Update the Markdown link to point to the saved image
        args.Uri = $"Resources/{fileName}";

        // Cancel default saving because we already wrote the file
        args.Cancel = true;
    }
}
```

### 預期輸出

在任意 Markdown 檢視器中開啟 `Output/output.md`，應該會看到類似以下的內容：

```markdown
# My Sample Document

Here is a paragraph that came from Word.

![Image 1](Resources/img_0.png)

Another paragraph with **bold** text.
```

`Resources` 資料夾將包含 `img_0.png`、`img_1.jpg` 等檔案，對應原本嵌入於 `input.docx` 的圖片。

## 常見問題 (FAQ)

**這能用於 .doc 檔案嗎？**  
可以。Aspose.Words 能載入 `.doc`、`.docx`、`.rtf` 以及其他多種格式。只需在 `inputPath` 中更改檔案副檔名即可。

**如果需要圖片的絕對 URL 該怎麼辦？**  
將 `args.Uri = $"Resources/{fileName}";` 改為類似 `args.Uri = $"https://mycdn.com/docs/{fileName}";` 的寫法。Markdown 便會引用遠端位置。

**我能控制圖片品質或格式嗎？**  
callback 會取得原始圖片的串流。若想將 PNG 轉為 JPEG，可將串流載入 `System.Drawing.Image`，重新編碼後再寫入新位元組，最後再設定 `args.Uri`。

**`ResourceSavingCallback` 是執行緒安全的嗎？**  
Aspose.Words 會依序呼叫每個資源的 callback，因此

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}