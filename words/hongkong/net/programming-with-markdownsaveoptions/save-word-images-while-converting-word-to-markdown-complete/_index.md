---
category: general
date: 2026-02-20
description: 學習如何在 C# 中儲存 Word 圖片並將 Word 轉換為 Markdown。此一步一步的指南亦會示範如何從 Word 中擷取圖片以及匯出含圖片的
  Markdown。
draft: false
keywords:
- save word images
- convert word to markdown
- extract images from word
- convert docx to md
- export markdown with images
language: zh-hant
og_description: 在本指南中，我們將示範如何使用 Aspose.Words 儲存 Word 圖片並將 Word 轉換為 Markdown。請按照步驟匯出含圖片的
  Markdown。
og_title: 在將 Word 轉換為 Markdown 時保存 Word 圖片 – 完整 C# 教學
tags:
- Aspose.Words
- C#
- Markdown
title: 在將 Word 轉換為 Markdown 時保存 Word 圖片 – 完整 C# 指南
url: /zh-hant/net/programming-with-markdownsaveoptions/save-word-images-while-converting-word-to-markdown-complete/
---

: we kept them.

Now produce final content with same formatting.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在將 Word 轉換為 Markdown 時儲存 Word 圖片 – 完整 C# 指南

有沒有曾經在將 Word 文件轉換為 Markdown 時需要 **save word images**？你並非唯一遇到此問題的人——開發者常常會碰到圖片在簡單的 `convert docx to md` 後消失的狀況。在本教學中，我們將一步步說明一個乾淨、可投入生產環境的方式，來 **save word images**、**convert word to markdown**，並產生仍能顯示所有圖片的 Markdown 檔案。

假設你有一本 `input.docx` 的使用手冊，想要發佈在靜態網站上。你需要將文字轉成 Markdown，同時也要讓螢幕截圖、圖表與標誌正確顯示在相應位置。這就是我們要解決的問題——不需要外部工具，也不需要手動複製貼上，只要幾行 C# 程式碼搭配 Aspose.Words 即可。

在本指南結束時，你將能夠：

* 使用 Aspose.Words 載入 `.docx` 檔案。  
* 設定 `MarkdownSaveOptions`，讓轉換同時 **extracts images from word**。  
* 實作一個回呼函式，將每張圖片寫入指定資料夾並使用唯一名稱。  
* 驗證產生的 `.md` 檔案正確引用圖片，即已成功 **exported markdown with images**。

> **先決條件** – 你需要 .NET 6+（或 .NET Framework 4.6+）、有效的 Aspose.Words 授權（或使用免費評估版），以及基本的 C# 知識。如果你從未使用過 Aspose，也不用擔心；API 很直觀，以下程式碼是完整且自足的。

---

## 在將 Word 轉換為 Markdown 時如何儲存 Word 圖片

第一步是在轉換過程中 **save word images**。Aspose.Words 提供 `ResourceSavingCallback`，會在每個外部資源（圖片、圖表、SVG 等）時觸發。透過插入自訂實作，我們可以精確決定每張圖片寫入磁碟的路徑。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

// Load the source Word document
Document document = new Document("YOUR_DIRECTORY/input.docx");

// Configure Markdown save options and attach a callback that will handle external resources
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    // This callback will be invoked for every image, letting us control the file name and folder
    ResourceSavingCallback = new MyResourceCallback()
};

// Save the document as Markdown; the callback will store images in a custom folder
document.Save("YOUR_DIRECTORY/output.md", markdownOptions);

// -----------------------------------------------------------------
// Callback implementation – stores each image in a dedicated folder with a unique name
class MyResourceCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Define the folder where resources will be saved
        string resourceFolder = "YOUR_DIRECTORY/MarkdownResources";
        Directory.CreateDirectory(resourceFolder);

        // Generate a unique file name while preserving the original extension
        string uniqueFileName = $"{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";

        // Tell Aspose.Words where to write the resource
        args.ResourceFileName = Path.Combine(resourceFolder, uniqueFileName);
    }
}
```

這就是完整的解決方案——執行後你會得到 `output.md` 以及一個充滿圖片檔案的 `MarkdownResources` 資料夾。Markdown 會包含類似 `![](MarkdownResources/7f3c2a1e-...png)` 的連結，代表你已成功一次性 **save word images** 與 **export markdown with images**。

## 設定 Markdown 選項以 convert docx to md

為什麼要使用回呼呢？預設情況下 Aspose.Words 會將圖片以 base‑64 字串嵌入 Markdown，這會導致檔案體積膨脹且版本控制變得混亂。設定 `ResourceSavingCallback` 可讓程式庫 **convert docx to md** *並* 將每張圖片寫入磁碟，而不是內嵌。

### 可能需要調整的關鍵屬性

| Property | Typical value | When to change |
|----------|---------------|----------------|
| `ExportImagesAsBase64` | `false` (default) | 保持圖片為獨立檔案。 |
| `ImagesFolder` | `null` (ignored when callback is used) | 若不需要動態命名，可設定固定資料夾。 |
| `ExportHeadersFooters` | `true` | 保留可能包含圖片的頁首/頁尾內容。 |
| `EncodeUrls` | `true` | 若路徑包含空格或非 ASCII 字元時需要。 |

> **專業提示**：如果你為多語系產生文件，考慮在 `resourceFolder` 加入語言代碼（例如 `MarkdownResources/en`），讓圖片路徑保持整潔。

## 實作資源回呼以 extract images from word

前一段程式碼中的回呼負責主要工作，但讓我們稍作說明。`IResourceSavingCallback` 會在每個外部資源時收到 `ResourceSavingArgs` 物件。最重要的欄位包括：

* `ResourceFileName` – 檔案將寫入的路徑。  
* `ResourceFileExtension` – 原始副檔名（`.png`、`.jpg` 等）。  
* `ResourceType` – 告訴你它是圖片、圖表或其他類型。

如果你只在意圖片，可以過濾掉非圖片資源：

```csharp
public void ResourceSaving(ResourceSavingArgs args)
{
    // Skip non‑image resources – we only want to save pictures
    if (args.ResourceType != ResourceType.Image)
        return;

    string resourceFolder = "YOUR_DIRECTORY/MarkdownResources";
    Directory.CreateDirectory(resourceFolder);

    string uniqueFileName = $"{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";
    args.ResourceFileName = Path.Combine(resourceFolder, uniqueFileName);
}
```

### 邊緣案例處理

1. **Duplicate images** – 如果同一張圖片出現多次，回呼仍會為每次寫入新檔案。若想去除重複，可保留一個 `Dictionary<string, string>`，將圖片位元組的雜湊對映到已存在的檔名。  
2. **Unsupported formats** – Aspose.Words 能匯出 PNG、JPEG、GIF、BMP 與 TIFF。若遇到罕見格式，需自行轉換（例如使用 `System.Drawing`）。  
3. **Large documents** – 對於巨大的 PDF 或 DOCX，建議串流輸出以避免記憶體耗盡。`MarkdownSaveOptions` 支援 `SaveOptions.UseMemoryCache = false`。

## 儲存文件並驗證 exported markdown with images

執行程式碼後，使用任意文字編輯器開啟 `output.md`。你應該會看到類似以下內容：

```markdown
# Chapter 1

Here is a diagram:

![](MarkdownResources/2c7f9a3e-9b4d-4f6a-8d12-5e9f2c7a1b3c.png)

And another screenshot:

![](MarkdownResources/7a1d4e2f-3c9b-4a5d-9e8f-6b2c3d4e5f6a.jpg)
```

若圖片連結正確，於檢視器（VS Code 預覽、GitHub 或靜態網站產生器）開啟 Markdown 檔案。圖片應自動呈現，證明你已成功 **save word images** 與 **export markdown with images**。

### 快速驗證腳本

若想自動化檢查，以下程式碼會掃描產生的 Markdown，找出缺少的檔案：

```csharp
using System;
using System.IO;
using System.Text.RegularExpressions;

string mdPath = "YOUR_DIRECTORY/output.md";
string mdFolder = Path.GetDirectoryName(mdPath)!;
string[] lines = File.ReadAllLines(mdPath);

foreach (var line in lines)
{
    var match = Regex.Match(line, @"!\[.*?\]\((.+?)\)");
    if (match.Success)
    {
        string imgPath = Path.Combine(mdFolder, match.Groups[1].Value);
        if (!File.Exists(imgPath))
            Console.WriteLine($"Missing image: {imgPath}");
    }
}
Console.WriteLine("Verification complete.");
```

在轉換後執行它；任何缺少的圖片都會印在主控台上。

## 轉換 word to markdown 時的常見陷阱與最佳實踐

| Pitfall | Why it hurts | Fix |
|---------|--------------|-----|
| **Images end up with long GUID names** | 在原始碼管理中難以閱讀。 | 後處理資料夾，將檔案重新命名為有意義的名稱（例如根據原始 `args.ResourceFileName`）。 |
| **Relative paths break after moving the Markdown file** | `![]()` 連結是相對於 `.md` 檔案的位置。 | 將圖片資料夾與 Markdown 檔案放在同一層，或在靜態網站設定中使用一致的基礎路徑。 |
| **Missing images when `ExportImagesAsBase64` is `true`** | 回呼不會觸發，因為圖片已內嵌。 | 確保 `ExportImagesAsBase64 = false`（預設）。 |
| **Large documents cause `OutOfMemoryException`** | Aspose 會將整個文件載入記憶體。 | 使用 `LoadOptions` 並設定 `LoadFormat.Docx`，若可用則啟用 `MemoryOptimization` 標誌。 |
| **Non‑ASCII file names break on some platforms** | URL 編碼可能失敗。 | 使用 ASCII 字元，或設定 `EncodeUrls = true`。 |

## 總結

我們已說明使用 Aspose.Words 在 **save word images** 同時 **convert word to markdown** 所需的全部步驟。核心概念很簡單：掛上 `ResourceSavingCallback`，指定一個你掌控的資料夾，讓程式庫自行處理。執行完畢後，你會得到乾淨的 `.md` 檔案與整齊的圖片資源——非常適合發佈或版本控制。

如果你想 **extract images from word** 用於其他用途（例如建立相簿），只需重複使用回呼程式碼而不執行 Markdown 儲存步驟。同樣地，這個模式也適用於批次作業的 **convert docx to md**——只要遍歷 `.docx` 目錄並呼叫相同的邏輯即可。

**接下來的步驟** 你可以探索：

* 將轉換整合到 ASP.NET Core API，讓使用者上傳 DOCX 並取得可下載的 Markdown 套件。  
* 加入對表格的支援以及

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}