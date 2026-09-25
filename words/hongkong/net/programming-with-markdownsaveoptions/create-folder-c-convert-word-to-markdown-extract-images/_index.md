---
category: general
date: 2026-02-26
description: 建立資料夾 C# 教學，示範如何將 Word 轉換為 markdown、從 docx 提取圖片，以及將串流複製到檔案——一步完成。
draft: false
keywords:
- create folder c#
- convert word to markdown
- extract images from docx
- copy stream to file
language: zh-hant
og_description: 《Create folder C# 教學》帶你一步步完成 Word 轉 markdown、從 docx 中提取圖片，以及將串流複製到檔案，並提供清晰的程式碼範例。
og_title: 建立資料夾 C# – 將 Word 轉換為 Markdown 並提取圖片
tags:
- C#
- Aspose.Words
- Markdown
- Image Extraction
title: 建立資料夾 C# – 將 Word 轉換為 Markdown 並擷取圖片
url: /zh-hant/net/programming-with-markdownsaveoptions/create-folder-c-convert-word-to-markdown-extract-images/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 建立資料夾 C# – 將 Word 轉換為 Markdown 並擷取圖片

曾經需要 **create folder C#** 同時將 Word 文件轉換為 markdown 並把所有圖片抽取出來嗎？你並不是唯一對此感到困惑的人。在許多自動化流程中，你往往需要同時處理檔案系統操作、格式轉換以及二進位資料處理——一次搞定。  

在本指南中，我們將逐步說明一個完整且可執行的解決方案，正好做到這一點：它會建立目標目錄、將 `.docx` 轉換為 markdown、擷取每個內嵌圖片，並使用 **copy stream to file** 的邏輯將圖片儲存至指定位置。無需外部腳本、無需手動步驟。只需純粹的 C# 與 Aspose.Words 程式庫。

> **您將獲得**  
> * 一個清晰的資料夾結構，已備妥 markdown 與資產  
> * 一個正確引用已抽取圖片的 markdown 檔案  
> * 完整的原始碼，可直接放入任何 .NET 專案  

在深入之前，請確保您已擁有：

* 已安裝 .NET 6.0（或更新）SDK —— 程式碼使用了現代語言功能。  
* **Aspose.Words for .NET** 的授權（免費試用版可用於測試）。  
* Visual Studio 2022 或您喜愛的編輯器。  

如果您在想 *為何* 要抽取圖片而不是直接嵌入，請想想靜態網站產生器：它們偏好使用相對路徑的 markdown，且將資產放在專屬資料夾中，可保持整潔且有利於快取。

---

## 建立資料夾 C# 並準備輸出結構

我們首先需要一個磁碟上的位置來存放所有檔案。這一步就是執行 **create folder C#** 的動作，得益於 `Directory.CreateDirectory`，它出奇地簡單。此方法具備冪等性——若資料夾已存在不會拋出例外，省去額外檢查。

```csharp
using System;
using System.IO;

// Define the base output directory (adjust as needed)
string baseOutput = Path.Combine(Environment.CurrentDirectory, "output");

// Subfolders for markdown and images
string markdownFolder = Path.Combine(baseOutput, "markdown");
string imagesFolder   = Path.Combine(baseOutput, "MyImages");

// Ensure the folders exist
Directory.CreateDirectory(markdownFolder);
Directory.CreateDirectory(imagesFolder);

Console.WriteLine($"Created folders:\n • {markdownFolder}\n • {imagesFolder}");
```

**為何這很重要：**  
事先建立資料夾可確保後續儲存步驟不會因 `DirectoryNotFoundException` 而失敗。 同時提供可預測的目錄結構：`output/markdown` 用於 `.md` 檔案，`output/MyImages` 用於抽出的每張圖片。

> **小技巧：** 若多次執行程式，建議先清空圖片資料夾 (`Directory.GetFiles(imagesFolder).ToList().ForEach(File.Delete);`) 以避免遺留檔案。

## 使用 Aspose.Words 將 Word 轉換為 Markdown

目錄結構已就緒，現在將 Word 文件轉換為 markdown。 Aspose.Words 負責繁重的工作——不必再手動處理 OpenXML 或第三方轉換器。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Load the source DOCX (replace with your actual path)
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
var doc = new Document(inputPath);

// Configure markdown options and attach the image callback (we’ll define it later)
var mdOptions = new MarkdownSaveOptions
{
    // The callback will redirect each extracted image to our custom folder
    ResourceSavingCallback = new ImageSavingCallback(imagesFolder)
};

// Save the markdown file into the previously created folder
string markdownPath = Path.Combine(markdownFolder, "output.md");
doc.Save(markdownPath, mdOptions);

Console.WriteLine($"Word document converted to markdown at: {markdownPath}");
```

**背後發生了什麼？**  
`MarkdownSaveOptions` 告訴 Aspose 輸出 markdown 語法。 預設情況下，程式庫會將圖片放在與 markdown 檔案相同的資料夾，並使用自動產生的檔名。 透過提供 `ResourceSavingCallback`，我們攔截此行為，並在自訂位置使用 **copy stream to file** 方式儲存。

## 從 DOCX 抽取圖片並儲存

回呼類別實作 `IResourceSavingCallback`。 在其中我們會收到 `ResourceSavingArgs` 物件，內含原始圖片串流與建議的檔名。 接著將該串流寫入磁碟，若需要可重新命名檔案，並告訴 Aspose 我們已處理完畢。

```csharp
using Aspose.Words.Saving;
using System.IO;

/// <summary>
/// Handles image extraction during markdown conversion.
/// </summary>
public class ImageSavingCallback : IResourceSavingCallback
{
    private readonly string _targetFolder;

    public ImageSavingCallback(string targetFolder)
    {
        _targetFolder = targetFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Ensure the target folder exists (defensive, though we created it earlier)
        Directory.CreateDirectory(_targetFolder);

        // Build a new, friendly file name – you can customize the pattern
        string newFileName = $"img_{Path.GetFileName(args.ResourceFileName)}";
        string fullPath = Path.Combine(_targetFolder, newFileName);

        // **Copy stream to file** – the core of the image extraction
        using (FileStream fs = new FileStream(fullPath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }

        // Tell Aspose to use our new path in the markdown reference
        args.ResourceFileName = Path.Combine("MyImages", newFileName);
        args.Handled = true; // Prevent default saving logic
    }
}
```

### Markdown 的呈現樣式

轉換完成後，產生的 `output.md` 會包含以下類似的行：

```markdown
![Image 1](MyImages/img_picture1.png)
```

由於我們將 `args.ResourceFileName` 改為相對路徑，markdown 直接指向我們建立的資料夾。 這正是靜態網站產生器所期待的。

**邊緣案例處理：**  
*若文件中有重複的圖片名稱*，在原名稱前加上 `img_` 前綴通常可避免衝突，亦可加入 GUID (`Guid.NewGuid()`) 以確保絕對唯一。

## Copy stream to file – 處理圖片資料

您可能會想為何不直接呼叫 `File.WriteAllBytes`。 答案在於 **stream flexibility**（串流彈性）。 `args.Stream` 可能是記憶體串流、網路串流，或其他任何實作。 使用 `CopyTo` 可保持中立，讓 .NET 有效處理緩衝區大小。

以下是一個精簡的工具方法，若您需要將一般串流複製到其他位置時可使用：

```csharp
/// <summary>
/// Copies any readable stream to a file on disk.
/// </summary>
public static void CopyStreamToFile(Stream source, string destinationPath)
{
    using (var file = new FileStream(destinationPath, FileMode.Create, FileAccess.Write))
    {
        source.CopyTo(file);
    }
}
```

若偏好單一職責的做法，可將 `ImageSavingCallback` 中的內嵌複製改為呼叫 `CopyStreamToFile`。

## 完整可執行範例

將所有部件組合起來，即可得到一個可自行執行的程式，您可從命令列執行：

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create the folder structure
        string baseOutput = Path.Combine(Environment.CurrentDirectory, "output");
        string markdownFolder = Path.Combine(baseOutput, "markdown");
        string imagesFolder   = Path.Combine(baseOutput, "MyImages");
        Directory.CreateDirectory(markdownFolder);
        Directory.CreateDirectory(imagesFolder);

        // 2️⃣ Load the DOCX
        string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        var doc = new Document(inputPath);

        // 3️⃣ Set up markdown options with our image callback
        var mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new ImageSavingCallback(imagesFolder)
        };

        // 4️⃣ Save as markdown
        string markdownPath = Path.Combine(markdownFolder, "output.md");
        doc.Save(markdownPath, mdOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown: {markdownPath}");
        Console.WriteLine($"Images folder: {imagesFolder}");
    }
}

// ---------- ImageSavingCallback (same as earlier) ----------
public class ImageSavingCallback : IResourceSavingCallback
{
    private readonly string _targetFolder;
    public ImageSavingCallback(string targetFolder) => _targetFolder = targetFolder;

    public void ResourceSaving(ResourceSavingArgs args)
    {
        Directory.CreateDirectory(_targetFolder);
        string newFileName = $"img_{Path.GetFileName(args.ResourceFileName)}";
        string fullPath = Path.Combine(_targetFolder, newFileName);
        using (FileStream fs = new FileStream(fullPath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }
        args.ResourceFileName = Path.Combine("MyImages", newFileName);
        args.Handled = true;
    }
}
```

**預期結果**

* `output/markdown/output.md` – 一個 markdown 檔案，圖片引用類似 `![Alt text](MyImages/img_picture1.png)`。  
* `output/MyImages/` – 每張原本位於 `input.docx` 內的圖片皆以 PNG/JPEG 檔案形式儲存。  

在任何檢視器（VS Code、GitHub，或靜態網站產生器）中開啟 markdown，即可看到圖片正確呈現在原始 Word 檔案中的位置。

## 常見問題與疑難排解

| 問題 | 答案 |
|----------|--------|
| **如果目標資料夾已經有檔案怎麼辦？** | `Directory.CreateDirectory` 不會覆寫。如果需要全新執行，請刪除

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}