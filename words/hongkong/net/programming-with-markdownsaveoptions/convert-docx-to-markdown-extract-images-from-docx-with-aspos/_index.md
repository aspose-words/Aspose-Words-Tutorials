---
category: general
date: 2026-04-05
description: 學習如何在 C# 中將 DOCX 轉換為 Markdown，並從 DOCX 中提取圖片。一步一步的指南，附完整程式碼與技巧。
draft: false
keywords:
- convert docx to markdown
- extract images from docx
- Aspose.Words markdown conversion
- C# document processing
- image extraction C#
language: zh-hant
og_description: 使用 Aspose.Words 將 DOCX 轉換為 Markdown 並從 DOCX 中提取圖片。完整的 C# 教學，包含程式碼、說明與最佳實踐技巧。
og_title: 將 DOCX 轉換為 Markdown – 使用 C# 從 DOCX 提取圖片
tags:
- Aspose.Words
- C#
- Markdown
- DOCX
- Image extraction
title: 將 DOCX 轉換為 Markdown – 使用 Aspose.Words 從 DOCX 提取圖像
url: /zh-hant/net/programming-with-markdownsaveoptions/convert-docx-to-markdown-extract-images-from-docx-with-aspos/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 將 DOCX 轉換為 Markdown – 從 DOCX 中擷取圖片（C#）

是否曾經需要**將 DOCX 轉換為 Markdown**，卻苦於輸出中圖片消失？你並不是唯一遇到這個問題的人。在許多專案中，Markdown 版本非常適合版本控制或靜態網站產生器，但圖片卻被遺漏，讓本來豐富的文件變成一個空洞的純文字檔。  

好消息是？只要幾行 C# 程式碼加上 Aspose.Words，就能自動**將 DOCX 轉換為 Markdown** *以及* **從 DOCX 中擷取圖片**。本指南將帶你完整走過整個流程，說明每個步驟的原因，甚至示範如何保持圖片資料夾整潔。

## 你將學會

- 如何載入包含圖片的 DOCX。
- 如何定義自訂的 `IResourceSavingCallback` 以決定每張圖片的儲存位置。
- 如何設定 `MarkdownSaveOptions`，讓產生的 Markdown 正確引用已擷取的圖片。
- 處理特殊情況的技巧，例如圖片名稱重複或非 PNG 格式。
- 一個完整、可直接複製貼上的程式碼範例，讓你今天就能執行。

### 前置條件

- .NET 6.0 或更新版本（此 API 可在 .NET Core、.NET Framework 以及 .NET 5+ 上運作）。
- 一份 **Aspose.Words for .NET** 授權（免費試用版可用於測試）。
- 具備基本的 C# 與 Visual Studio（或你慣用的 IDE）使用經驗。

如果你已具備上述條件，讓我們開始吧。

---

## 步驟 1：設定專案並安裝 Aspose.Words

首先，建立一個新的 Console 應用程式（或整合到現有的解決方案中）。

```bash
dotnet new console -n DocxToMarkdownDemo
cd DocxToMarkdownDemo
dotnet add package Aspose.Words
```

> **專業提示：** 使用最新的 NuGet 版本（截至 2026 年 4 月為 24.12），即可取得最新的 Markdown 匯出改進。

---

## 步驟 2：建立回呼以將圖片儲存至指定位置

Aspose.Words 允許你在 Markdown 匯出過程中攔截每一個資源（圖片、SVG 等）。透過實作 `IResourceSavingCallback`，你可以：

1. 選擇一個與 Markdown 檔案同層的資料夾。
2. 產生唯一的檔名（避免覆寫已存在的圖片）。
3. 決定格式（此處強制使用 PNG 以保持一致性）。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

/// <summary>
/// Saves each image extracted from the DOCX into a dedicated folder
/// with a GUID‑based filename. The markdown file will reference the
/// new filename via <c>args.ResourceFileName</c>.
/// </summary>
class ImageResourceSaver : IResourceSavingCallback
{
    private readonly string _targetFolder;

    public ImageResourceSaver(string targetFolder)
    {
        _targetFolder = targetFolder;
        // Ensure the folder exists before we start writing files.
        Directory.CreateDirectory(_targetFolder);
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Generate a unique name to avoid collisions.
        string newFileName = $"img_{Guid.NewGuid():N}.png";

        // Full physical path where the image will be written.
        string fullPath = Path.Combine(_targetFolder, newFileName);

        // Tell the markdown exporter what name to use in the .md file.
        args.ResourceFileName = newFileName;

        // Provide a stream that writes to the desired location.
        args.Stream = new FileStream(fullPath, FileMode.Create);
    }
}
```

### 為什麼使用 GUID 作為檔名？

如果來源 DOCX 中有兩張圖片的原始名稱相同，直接複製貼上會導致其中一張被覆寫。使用 `Guid.NewGuid()` 可保證唯一性，對於在自動化流水線中多次執行轉換特別有用。

---

## 步驟 3：載入 DOCX 並設定 Markdown 選項

現在，我們將文件載入記憶體，並掛接剛剛建立的回呼。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // --------------------------------------------------------------------
        // 1️⃣  Define paths – adjust these to match your environment.
        // --------------------------------------------------------------------
        string sourceDocx = @"C:\Docs\WithImages.docx";
        string outputMarkdown = @"C:\Docs\DocWithImages.md";
        string imagesFolder = @"C:\Docs\MarkdownResources";

        // --------------------------------------------------------------------
        // 2️⃣  Load the Word document.
        // --------------------------------------------------------------------
        Document doc = new Document(sourceDocx);

        // --------------------------------------------------------------------
        // 3️⃣  Configure MarkdownSaveOptions with our custom saver.
        // --------------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            // This tells Aspose.Words to call ImageResourceSaver for each image.
            ResourceSavingCallback = new ImageResourceSaver(imagesFolder)
        };

        // --------------------------------------------------------------------
        // 4️⃣  Perform the conversion.
        // --------------------------------------------------------------------
        doc.Save(outputMarkdown, mdOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown saved to: {outputMarkdown}");
        Console.WriteLine($"Images saved to:   {imagesFolder}");
    }
}
```

### 程式碼逐步說明

| 步驟 | 目的 |
|------|------|
| **定義路徑** | 讓專案保持彈性；可指向任何資料夾而不需重新編譯。 |
| **載入 DOCX** | `Document` 會解析 Word 檔案，讓所有元素（段落、表格、圖片）皆可存取。 |
| **設定 `MarkdownSaveOptions`** | `ResourceSavingCallback` 是擷取圖片的掛點。若未設定，Aspose.Words 會將圖片以 base64 字串嵌入，或根據設定直接省略。 |
| **儲存** | `doc.Save` 會寫入 Markdown 檔案，並為每張圖片觸發回呼。 |

---

## 步驟 4：驗證輸出 – 你應該看到什麼？

執行程式後，開啟 `DocWithImages.md`。你會看到類似以下的 Markdown 圖片連結：

```markdown
![img_1a2b3c4d5e6f7g8h9i0j.png](MarkdownResources/img_1a2b3c4d5e6f7g8h9i0j.png)
```

在 `C:\Docs\MarkdownResources` 中，你會找到一系列以 GUID 命名的 PNG 檔案。打開任一檔案，應與原始 DOCX 中嵌入的圖片完全相同。

如果在支援相對路徑的檢視器中開啟 Markdown 檔案（例如 VS Code 預覽、GitHub，或靜態網站產生器），圖片將會如同在 Word 中一樣正確顯示。

### 常見問題與避免方法

| 症狀 | 可能原因 | 解決方式 |
|------|----------|----------|
| 圖片顯示為斷開連結 | `ResourceFileName` 未設定，導致 Markdown 指向不存在的檔案。 | 在回呼中確保設定 `args.ResourceFileName = newFileName;`。 |
| PNG 檔案過大 | 原始圖片為 JPEG 或 BMP；轉換為 PNG 會增加檔案大小。 | 透過 `args.ResourceContentType` 偵測原始格式並保留：`args.ResourceFileName = $"{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";` |
| 仍出現重複圖片 | 使用了固定檔名而非 GUID。 | 改回使用 GUID 邏輯，或為每種圖片類型加入計數器。 |
| 轉換拋出 `FileNotFoundException` | 來源 DOCX 路徑錯誤或資料夾缺乏讀取權限。 | 確認路徑並授予相應的檔案系統權限。 |

---

## 步驟 5：進階調整（可選）

### 5.1 保留原始圖片格式

如果希望輸出圖片保留原始副檔名，請修改回呼：

```csharp
public void ResourceSaving(ResourceSavingArgs args)
{
    string ext = Path.GetExtension(args.ResourceFileName).ToLowerInvariant();
    // Default to .png if Aspose couldn't determine an extension.
    if (string.IsNullOrEmpty(ext)) ext = ".png";

    string newFileName = $"img_{Guid.NewGuid():N}{ext}";
    string fullPath = Path.Combine(_targetFolder, newFileName);
    args.ResourceFileName = newFileName;
    args.Stream = new FileStream(fullPath, FileMode.Create);
}
```

### 5.2 以 Base64 內嵌圖片（當你*不想*使用獨立檔案時）

有時單一檔案的 Markdown 會更方便（例如透過電郵傳送）。請變更設定：

```csharp
mdOptions.ImagesFolder = string.Empty; // disables external folder
mdOptions.ExportImagesAsBase64 = true;
```

但請記住：對於大多數靜態網站工作流程而言，**從 DOCX 中擷取圖片** 是主要目標，因此使用資料夾方式通常較佳。

---

## 完整可執行範例（可直接複製貼上）

以下是一個完整的單檔程式碼。只需將路徑替換為自己的路徑後執行即可。

```csharp
// ---------------------------------------------------------------
// Convert DOCX to Markdown – Extract Images from DOCX
// ---------------------------------------------------------------
// NuGet: Aspose.Words (>= 24.12)
// ---------------------------------------------------------------
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class ImageResourceSaver : IResourceSavingCallback
{
    private readonly string _targetFolder;
    public ImageResourceSaver(string targetFolder) => Directory.CreateDirectory(_targetFolder = targetFolder);

    public void ResourceSaving(ResourceSavingArgs args)
    {
        string ext = Path.GetExtension(args.ResourceFileName).ToLowerInvariant();
        if (string.IsNullOrEmpty(ext)) ext = ".png";
        string newFileName = $"img_{Guid.NewGuid():N}{ext}";
        string fullPath = Path.Combine(_targetFolder, newFileName);
        args.ResourceFileName = newFileName;
        args.Stream = new FileStream(fullPath, FileMode.Create);
    }
}

class Program
{
    static void Main()
    {
        // 👉 Adjust these paths:
        string sourceDocx = @"C:\Docs\WithImages.docx";
        string outputMd  = @"C:\Docs\DocWithImages.md";
        string imgFolder = @"C:\Docs\MarkdownResources";

        // Load the DOCX.
        Document doc = new Document(sourceDocx);

        // Set up markdown options with our image saver.
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new ImageResourceSaver(imgFolder)
        };

        // Perform conversion.
        doc.Save(outputMd, mdOptions);

        Console.WriteLine("✅ DOCX successfully converted to Markdown.");
        Console.WriteLine($"📄 Markdown: {outputMd}");
        Console.WriteLine($"🖼️ Images folder: {imgFolder}");
    }
}
```

使用 `dotnet run` 執行。當主控台顯示 ✅ 行時，開啟 Markdown 檔案，即可看到圖片正確呈現。

---

## 結論

現在，你已擁有一套使用 Aspose.Words 在 C# 中**完整、可投入生產的 DOCX 轉換為 Markdown 並擷取圖片**解決方案。主要關鍵字遍佈全文，提升對搜尋引擎與 AI 助手的相關性。  

一次執行，程式碼會：

1. 載入 Word 文件。
2. 透過 `IResourceSavingCallback` 攔截每張圖片。
3. 將每張圖片儲存至可預測且唯一名稱的資料夾。
4. 產生引用這些圖片的 Markdown。

從此你可以：

- Plug

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}