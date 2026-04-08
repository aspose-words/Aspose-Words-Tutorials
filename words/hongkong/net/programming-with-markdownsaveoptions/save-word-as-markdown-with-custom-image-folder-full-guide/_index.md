---
category: general
date: 2026-04-07
description: 將 Word 另存為 Markdown，並使用回調從 docx 中提取圖片。了解如何使用回調高效儲存 Markdown 圖片資料夾。
draft: false
keywords:
- save word as markdown
- extract images from docx
- how to use callback
- markdown images folder
language: zh-hant
og_description: 將 Word 另存為 Markdown，並使用回調函數從 docx 中提取圖片。本指南說明如何使用回調函數建立 Markdown 圖片資料夾。
og_title: 將 Word 另存為 Markdown – 完整逐步指南
tags:
- Aspose.Words
- C#
- Markdown
- Image Extraction
title: 將 Word 另存為 Markdown 並自訂圖片資料夾 – 完整指南
url: /zh-hant/net/programming-with-markdownsaveoptions/save-word-as-markdown-with-custom-image-folder-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 將 Word 儲存為 Markdown – 完整步驟指南

是否曾經需要 **將 Word 儲存為 Markdown**，卻不確定要如何處理內嵌的圖片？你並不孤單。在許多專案中，Markdown 輸出看起來很不錯——*直到* 你發現圖片連結失效，因為檔案從未離開 Word 套件。

好消息是，Aspose.Words 為你提供了一個乾淨的方式來 **從 docx 中擷取圖片**，並將它們放在你想要的位置，透過 **callback** 讓你自行控制 Markdown 圖片資料夾。在本教學中，我們將一步步說明整個流程，從載入 `.docx` 檔案，到最終得到整齊的 PNG（或其他格式）資料夾，以及指向這些圖片的 Markdown 檔案。

完成本指南後，你將能夠：

* 只用一行程式碼將任何 Word 文件轉換為 Markdown。  
* 自動將每張圖片匯出至專屬的 `images` 子資料夾。  
* 自訂檔名以避免衝突，即使來源文件包含數十張圖片。  

無需外部腳本，無需手動複製貼上——只需純粹的 C# 與 Aspose.Words。

## 前置條件

在開始之前，請確保你已具備：

* **Aspose.Words for .NET**（最新穩定版；撰寫本文時為 24.9）。  
* .NET 開發環境（Visual Studio、Rider，或 `dotnet` CLI）。  
* 一個包含至少一張圖片的 Word 文件（`.docx`），例如 `DocWithImages.docx`。  

如果你從未使用過 Aspose.Words，也別擔心。此函式庫完全受管理，不需要 COM interop，且可在 .NET 6+ 以及 .NET Framework 4.8 上執行。

## Step 1 – 設定專案並安裝套件

首先，建立一個新的 console 應用程式（或將程式碼加入現有專案）。

```bash
dotnet new console -n WordToMarkdownDemo
cd WordToMarkdownDemo
dotnet add package Aspose.Words
```

> **專業提示：** 若目標是 .NET 6，預設的 `Program.cs` 已使用頂層語句（top‑level statements），可讓範例更簡潔。

## Step 2 – 建立 Callback 以控制圖片儲存

Aspose.Words 會對每個需要寫入的外部資源（圖片、CSS 等）呼叫 `IResourceSavingCallback.ResourceSaving`。實作此介面即可完整掌控 **Markdown 圖片資料夾** 的建立方式。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

/// <summary>
/// Handles the saving of resources (e.g., images) when a document is converted to Markdown.
/// </summary>
class MyMarkdownResourceCallback : IResourceSavingCallback
{
    // Folder where we want to dump the images.
    private readonly string _imageFolder;

    public MyMarkdownResourceCallback(string imageFolder)
    {
        _imageFolder = imageFolder;
        // Ensure the folder exists before the first write.
        Directory.CreateDirectory(_imageFolder);
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Build a unique filename: img_<guid>.<originalExtension>
        string uniqueName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.FileName)}";

        // Full path where the image will be saved.
        string fullPath = Path.Combine(_imageFolder, uniqueName);
        args.ResourceFileName = fullPath;

        // Copy the incoming stream to our file.
        using (FileStream outStream = File.OpenWrite(fullPath))
            args.Stream.CopyTo(outStream);

        // Tell Aspose we’ve handled the write; skip its default behavior.
        args.Cancel = true;
    }
}
```

### 為什麼要使用 Callback？

* **細部控制** – 你決定資料夾結構與命名規則。  
* **效能** – 只寫入一次串流，避免函式庫的二次寫入備援。  
* **彈性** – 可在此加入日誌、圖片最佳化，甚至上傳至雲端儲存。

## Step 3 – 載入 Word 文件

Callback 準備好後，只需要把 Aspose.Words 指向來源檔案即可。

```csharp
// Path to the source .docx (adjust as needed).
string sourcePath = Path.Combine("YOUR_DIRECTORY", "DocWithImages.docx");

// Load the document into memory.
Document doc = new Document(sourcePath);
```

> **如果找不到檔案會怎樣？**  
> `Document` 會拋出 `FileNotFoundException`。若路徑是動態的，請使用 `try/catch` 包住載入程式碼。

## Step 4 – 設定 MarkdownSaveOptions

`MarkdownSaveOptions` 類別讓我們插入剛才建立的 Callback，同時設定圖片相對於 Markdown 檔案的資料夾位置。

```csharp
// Define where we want the images folder to sit.
string markdownFolder = Path.Combine("YOUR_DIRECTORY", "markdown-output");
string imagesSubFolder = Path.Combine(markdownFolder, "images");

// Ensure the markdown output directory exists.
Directory.CreateDirectory(markdownFolder);

// Create the save options and attach the callback.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // This callback will be invoked for every image.
    ResourceSavingCallback = new MyMarkdownResourceCallback(imagesSubFolder),

    // Optional: keep image references relative to the markdown file.
    ImagesFolder = "images"
};
```

`ImagesFolder` 屬性告訴 Aspose 產生類似 `![Alt text](images/img_123.png)` 的 Markdown 連結。因為我們在 Callback 中也設定了 `ResourceFileName`，實際檔案會正確寫入該位置。

## Step 5 – 儲存為 Markdown 並驗證結果

最後，我們寫入 Markdown 檔案。Callback 已經把 `images` 子資料夾填滿。

```csharp
// Destination markdown file.
string markdownPath = Path.Combine(markdownFolder, "Doc.md");

// Save the document.
doc.Save(markdownPath, mdOptions);

// Quick sanity check – list the generated files.
Console.WriteLine("Markdown saved to: " + markdownPath);
Console.WriteLine("Extracted images:");
foreach (var img in Directory.GetFiles(imagesSubFolder))
{
    Console.WriteLine("  • " + Path.GetFileName(img));
}
```

### 預期輸出

執行程式時應會印出類似以下內容：

```
Markdown saved to: C:\Project\markdown-output\Doc.md
Extracted images:
  • img_5c2a1f8b-3e7b-4d9a-9c1f-2b6e5f9d9a3c.png
  • img_a7d4c9e2-1f55-4c2b-8f6a-9e1b2c3d4e5f.jpg
```

在任何 Markdown 檢視器中開啟 `Doc.md`，即可看到正確指向 `images` 資料夾的圖片連結。

---

## 常見問題 (FAQ)

### 如何在不轉換為 Markdown 的情況下 **從 docx 中擷取圖片**？

你可以重複使用相同的 `MyMarkdownResourceCallback`，但改為呼叫 `doc.Save("images.zip", SaveFormat.Zip)`。Callback 仍會對每張圖片觸發，讓你自行決定儲存位置。

### 如果需要 **不同的圖片格式** 該怎麼辦？

`args.FileName` 已包含原始副檔名（`.png`、`.jpg` 等）。若必須將所有圖片轉為單一格式，可在 `ResourceSaving` 內部加入轉換步驟，再寫入串流。

### 能否為每個文件 **自訂 Markdown 圖片資料夾**？

當然可以。Callback 透過建構子接收資料夾路徑，因此在批次處理時，你可以為每個文件實例化不同的 Callback，指定不同的資料夾。

### 這在 **大型文件**（數百張圖片）下可行嗎？

可以。Callback 直接將圖片串流寫入磁碟，保持低記憶體使用量。只要確保目標磁碟有足夠空間，且不會觸及作業系統的檔案句柄上限即可。

---

## 完整範例程式

以下是可直接複製貼上的完整程式碼。將 `YOUR_DIRECTORY` 替換為適合你環境的絕對或相對路徑。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class MyMarkdownResourceCallback : IResourceSavingCallback
{
    private readonly string _imageFolder;

    public MyMarkdownResourceCallback(string imageFolder)
    {
        _imageFolder = imageFolder;
        Directory.CreateDirectory(_imageFolder);
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        string uniqueName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.FileName)}";
        string fullPath = Path.Combine(_imageFolder, uniqueName);
        args.ResourceFileName = fullPath;

        using (FileStream outStream = File.OpenWrite(fullPath))
            args.Stream.CopyTo(outStream);

        args.Cancel = true;
    }
}

class Program
{
    static void Main()
    {
        // Adjust these paths.
        string baseDir = Path.Combine(Environment.CurrentDirectory, "demo");
        string sourceDoc = Path.Combine(baseDir, "DocWithImages.docx");
        string markdownDir = Path.Combine(baseDir, "markdown-output");
        string imagesDir = Path.Combine(markdownDir, "images");
        string markdownFile = Path.Combine(markdownDir, "Doc.md");

        // Load the document.
        Document doc;
        try
        {
            doc = new Document(sourceDoc);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
            return;
        }

        // Configure save options with our callback.
        var mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new MyMarkdownResourceCallback(imagesDir),
            ImagesFolder = "images"
        };

        // Ensure output folder exists.
        Directory.CreateDirectory(markdownDir);

        // Save as markdown.
        doc.Save(markdownFile, mdOptions);

        Console.WriteLine($"✅ Markdown saved to: {markdownFile}");
        Console.WriteLine("🖼️ Extracted images:");
        foreach (var file in Directory.GetFiles(imagesDir))
            Console.WriteLine($"   - {Path.GetFileName(file)}");
    }
}
```

執行程式（`dotnet run`）後，你會看到新產生的 `Doc.md`，以及包含圖片的 `images` 子資料夾。

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}