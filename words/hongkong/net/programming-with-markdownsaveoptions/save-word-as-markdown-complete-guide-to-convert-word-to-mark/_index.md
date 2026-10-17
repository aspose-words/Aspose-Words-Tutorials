---
category: general
date: 2026-03-22
description: 使用 Aspose.Words 快速將 Word 另存為 Markdown。了解如何將 Word 轉換為 Markdown、從 docx
  提取圖片以及在 C# 中匯出 Word 圖片。
draft: false
keywords:
- save word as markdown
- convert word to markdown
- extract images from docx
- export images from word
language: zh-hant
og_description: 使用 Aspose.Words 將 Word 儲存為 Markdown。本教學示範如何將 Word 轉換為 Markdown、從 docx
  中提取圖片以及從 Word 匯出圖片。
og_title: 將 Word 另存為 Markdown – 步驟式轉換指南
tags:
- Aspose.Words
- C#
- Markdown
title: 將 Word 另存為 Markdown – 完整指南：將 Word 轉換為 Markdown 及提取圖片
url: /zh-hant/net/programming-with-markdownsaveoptions/save-word-as-markdown-complete-guide-to-convert-word-to-mark/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 將 Word 儲存為 Markdown – 完整指南

有沒有曾經需要 **將 Word 儲存為 markdown**，卻不知從何開始？你並不孤單——開發者常常詢問如何 **將 Word 轉換為 markdown** 同時保留所有內嵌圖片。好消息是 Aspose.Words 讓整個流程變得輕而易舉，而且你還可以 **從 docx 中提取圖片**，無需自行撰寫解析器。在本教學中，我們將示範一個可直接執行的 C# 範例，完成上述工作，並示範如何 **從 word 匯出圖片** 到整齊的資料夾。

我們將涵蓋所有必備知識：安裝函式庫、設定資源儲存回呼、載入 .docx，最後寫入 .md 檔案以及一系列圖片檔案。完成後，你只需一個指令即可將任何 Word 文件轉換為乾淨的 markdown，並取得可在任何地方重複使用的圖片資產。

---

## 所需條件

- **.NET 6**（或任何較新的 .NET 執行環境）— 此程式碼亦可在 .NET 5 以上編譯。  
- **Aspose.Words for .NET**— 你可以從 Aspose 官方網站取得免費試用版，或使用 NuGet 套件：`Install-Package Aspose.Words`。  
- 一個 **sample .docx**，內含至少一張圖片（以驗證圖片抽取功能）。  
- 你熟悉的 IDE 或編輯器（Visual Studio、Rider、VS Code…）。

不需要其他第三方工具；所有操作皆在同一程序內執行。

---

## 步驟 1：建立資源儲存處理程式（從 DOCX 抽取圖片）

當 Aspose.Words 將文件儲存為 markdown 時，會透過回呼將每個內嵌圖片串流出來。實作 `IResourceSavingCallback` 後，我們即可決定這些圖片在磁碟上的存放位置。以下的處理程式會建立 `Images` 資料夾，為每張圖片產生唯一名稱，並相應更新 markdown 的引用。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

/// <summary>
/// Handles image resources while saving a document as markdown.
/// </summary>
class MyMarkdownResourceHandler : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // 1️⃣ Ensure the Images folder exists
        string imageFolder = "Images";
        Directory.CreateDirectory(imageFolder);

        // 2️⃣ Build a unique filename (helps when the source doc has duplicate names)
        string uniqueFileName = Guid.NewGuid().ToString() + Path.GetExtension(args.FileName);
        string imagePath = Path.Combine(imageFolder, uniqueFileName);

        // 3️⃣ Write the image stream to disk
        using (FileStream fs = new FileStream(imagePath, FileMode.Create))
        {
            args.Stream.CopyTo(fs);
        }

        // 4️⃣ Tell Aspose to reference the new filename in the markdown output
        args.FileName = uniqueFileName;
        args.Stream = null; // we already saved the file, no need for Aspose to keep the stream open
    }
}
```

**為何重要：**  
若未使用回呼，Aspose 會將圖片以 base‑64 字串嵌入，或以原始檔名直接寫入同一資料夾，易造成衝突。透過自行控制儲存位置，我們實際上 **從 word 匯出圖片**，並讓 markdown 保持整潔。

---

## 步驟 2：載入來源文件（將 Word 轉換為 Markdown）

處理程式準備好之後，我們需要開啟要轉換的 .docx。`Document` 類別會抽象化各種檔案格式的細節，因此你可以傳入 `.docx`、`.rtf`，甚至是 PDF（前提是擁有相應授權）。

```csharp
// Adjust the path to point at your actual .docx file
string inputPath = Path.Combine("YOUR_DIRECTORY", "input.docx");

// Load the Word file into Aspose.Words
Document doc = new Document(inputPath);
```

**提示：** 若文件較大，建議使用 `LoadOptions` 以降低記憶體使用量，但對於大多數日常檔案，預設載入器已足夠。

---

## 步驟 3：設定 Markdown 儲存選項（將 Word 儲存為 Markdown）

在此將所有設定結合起來。`MarkdownSaveOptions` 允許我們注入先前撰寫的回呼，並且可以微調一些格式旗標（例如使用 GitHub 風格的 markdown）。

```csharp
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // Use the custom handler to dump images into the Images folder
    ResourceSavingCallback = new MyMarkdownResourceHandler(),

    // Optional: generate GitHub‑compatible markdown (tables, code fences, etc.)
    ExportImagesAsBase64 = false,
    ExportHeadersFooters = false,
    ExportDocumentProperties = false,
    UseGitHubFlavor = true
};
```

**發生了什麼：**  
`ExportImagesAsBase64 = false` 告訴 Aspose 將圖片以外部檔案方式引用——這正是我們想要的乾淨 markdown。其他旗標則讓輸出僅聚焦於正文內容。

---

## 步驟 4：將文件儲存為 Markdown 並驗證輸出

最後，我們請 Aspose 寫入 markdown 檔案。所有圖片會放入 `Images` 子資料夾，markdown 內則包含指向這些檔案的相對連結。

```csharp
// Destination markdown file
string outputPath = Path.Combine("YOUR_DIRECTORY", "output.md");

// Perform the conversion
doc.Save(outputPath, mdOptions);
```

呼叫完成後，你應該在 `YOUR_DIRECTORY` 中看到兩樣東西：

1. **output.md** – 一個 markdown 檔案，所有圖片皆以 `![](Images/123e4567‑e89b‑12d3‑a456‑426614174000.png)` 方式引用。  
2. **Images/** – 一個資料夾，內含從原始 Word 文件抽取出的 PNG/JPEG 圖片。

你可以在任何 markdown 檢視器（VS Code、GitHub、Typora）中開啟 `output.md`，圖片會正確顯示於原始檔案中的位置。

---

## 完整可執行範例（全部組合）

以下為完整程式碼，可直接貼到 Console 應用程式中。只需將 `YOUR_DIRECTORY` 替換為放置 `.docx` 的路徑即可。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

// ------------------------------------------------------------
// Step 1: Resource‑saving handler (extract images from docx)
// ------------------------------------------------------------
class MyMarkdownResourceHandler : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        string imageFolder = "Images";
        Directory.CreateDirectory(imageFolder);

        string uniqueFileName = Guid.NewGuid().ToString() + Path.GetExtension(args.FileName);
        string imagePath = Path.Combine(imageFolder, uniqueFileName);

        using (FileStream fs = new FileStream(imagePath, FileMode.Create))
            args.Stream.CopyTo(fs);

        args.FileName = uniqueFileName;
        args.Stream = null;
    }
}

// ------------------------------------------------------------
// Main program – save word as markdown
// ------------------------------------------------------------
class Program
{
    static void Main()
    {
        // Step 2: Load the source document (convert word to markdown)
        string inputPath = Path.Combine("YOUR_DIRECTORY", "input.docx");
        Document doc = new Document(inputPath);

        // Step 3: Configure save options (export images from word)
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new MyMarkdownResourceHandler(),
            ExportImagesAsBase64 = false,
            UseGitHubFlavor = true
        };

        // Step 4: Save as markdown
        string outputPath = Path.Combine("YOUR_DIRECTORY", "output.md");
        doc.Save(outputPath, mdOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown file: {outputPath}");
        Console.WriteLine("Images folder: Images (inside the same directory)");
    }
}
```

執行程式 (`dotnet run`)，即可 **將 Word 儲存為 markdown**，同時 **從 word 匯出圖片** 到整齊的資料夾。

---

## 預期結果

| 檔案 | 說明 |
|------|-------------|
| `output.md` | 含有圖片引用（如 `![](Images/abcd1234.png)`）的 Markdown 文字。 |
| `Images/` | 從原始 `.docx` 抽取的每張圖片檔案。檔名採用 GUID 以避免衝突。 |

在 markdown 預覽工具中開啟 `output.md`，即可看到原始的版面配置、標題、項目清單，以及所有圖片正確顯示於相應位置。

---

## 常見問題與特殊情況

- **如果文件包含 SVG 或 WMF 圖片呢？**  
  當 `ExportImagesAsBase64 = false` 時，Aspose.Words 會自動將這些格式光柵化為 PNG，無需額外程式碼。

- **我可以更改 images 資料夾的名稱嗎？**  
  當然可以——只需修改 `MyMarkdownResourceHandler` 內的 `imageFolder` 變數。記得保持資料夾路徑相對於 markdown 檔案，才能讓連結保持有效。

- **是否需要商業授權？**  
  免費試用版可供評估使用，但會在輸出中加入浮水印。正式上線時建議購買正式授權；API 使用方式不變。

- **表格或註腳怎麼處理？**  
  `MarkdownSaveOptions` 已支援表格（GitHub 風格的 markdown）。註腳預設會被忽略；若需要可將 `ExportHeadersFooters = true` 設為 true。

- **大型文件導致記憶體壓力？**  
  可使用 `LoadOptions` 搭配 `LoadFormat.Docx` 並將 `LoadOptions.MemoryOptimization = true`。由於有回呼的關係，轉換過程仍具串流友好性。

---

## 結論

現在你已掌握完整的步驟，能夠 **將 Word 儲存為 markdown**、**將 Word 轉換為 markdown**，以及 **從 docx 抽取圖片**——全部只需幾行 C# 程式碼。關鍵在於自訂的 `IResourceSavingCallback`，讓你 **從 word 匯出圖片** 到指定位置。接下來，你可以將此流程整合至建置管線、Web 服務，或是批次將 Word 報告轉換為開發者友善的 markdown 的桌面工具中。

接下來可以嘗試調整 `MarkdownSaveOptions` 產生純文字連結，或將此與靜態網站產生器結合，發布文件說明。

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}