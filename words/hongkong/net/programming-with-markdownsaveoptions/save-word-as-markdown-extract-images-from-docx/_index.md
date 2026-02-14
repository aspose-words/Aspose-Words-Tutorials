---
category: general
date: 2026-02-13
description: 在 C# 中將 Word 另存為 Markdown 並從 docx 中提取圖片。學習如何將 docx 轉換為 Markdown、從 docx
  儲存圖片，並保持資源有條理。
draft: false
keywords:
- save word as markdown
- convert docx to markdown
- how to extract images
- save images from docx
language: zh-hant
og_description: 使用完整的 C# 範例，將 Word 另存為 Markdown 並從 docx 中提取圖片。將 docx 轉換為 Markdown，儲存
  docx 中的圖片，並保持所有內容整潔。
og_title: 將 Word 另存為 Markdown – 從 DOCX 提取圖片
tags:
- Aspose.Words
- C#
- Markdown conversion
title: 將 Word 儲存為 Markdown – 從 docx 提取圖片
url: /zh-hant/net/programming-with-markdownsaveoptions/save-word-as-markdown-extract-images-from-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 將 Word 另存為 Markdown – 從 docx 中擷取圖片

是否曾經需要 **將 Word 另存為 Markdown**，同時保留原始 *.docx* 中的每一張圖片？也許你正在建構靜態網站產生器，或只是想把舊有的 Word 報告搬移到 Git 友善的格式。無論原因為何，痛點都相同：轉換時圖片會遺失，或是產生一堆斷掉的連結。

事實是——你不必自行撰寫解析器或手動搜尋 *.docx* 的 ZIP 結構。使用 Aspose.Words，你可以 **將 docx 轉換為 markdown**，同時 **將圖片從 docx 儲存** 到你指定的資料夾。本指南將逐步說明一個完整、可直接執行的 C# 程式，完成上述工作。

完成後，你將得到：

* 一個與原始 Word 版面相同的 markdown 檔案。  
* 一個名為 “MarkdownResources” 的資料夾，內含所有擷取出的圖片，檔名與來源完全一致。  
* 一套可重複使用的回呼模式，能套用於 PDF、HTML 或任何 Aspose 支援的格式。

> **先決條件** – 需要 .NET 6+（或 .NET Framework 4.7+）、有效的 Aspose.Words 授權（或免費試用版），以及 Visual Studio 或 VS Code。無需其他 NuGet 套件。

---

## 本教學涵蓋內容

我們會把解決方案拆成以下步驟：

1. **載入來源文件** – 開啟要轉換的 *.docx*。  
2. **建立資源儲存回呼** – 告訴 Aspose 每張圖片要存放到哪裡。  
3. **設定 `MarkdownSaveOptions`** – 把回呼掛到 markdown 匯出器。  
4. **儲存 markdown 檔案** – 一行程式碼完成所有重活。

在說明過程中，我們會解釋每個步驟的 **原因**、指出常見陷阱（例如資料夾權限不足），並示範如何針對 PNG 僅擷取或自訂圖片命名等邊緣情況進行調整。

---

## 步驟 1 – 載入來源文件

在執行任何操作前，你必須先取得指向 Word 檔案的 `Document` 實例。Aspose 會抽象 *.docx* 的 ZIP 結構，讓你像操作一般文件物件一樣使用它。

```csharp
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

// Adjust the path to where your .docx lives.
const string inputPath = @"YOUR_DIRECTORY\input.docx";

Document doc = new Document(inputPath);
```

*為什麼重要*：若檔案路徑錯誤，Aspose 會拋出 `FileNotFoundException`，導致整條流程中斷。使用常數（或更好的是設定值）可以在不觸及核心程式碼的情況下輕鬆切換檔案。

> **小技巧** – 若檔案由使用者提供，請將載入程式碼包在 try/catch 中，這樣可以回傳友善的錯誤訊息，而不是堆疊追蹤。

---

## 步驟 2 – 定義回呼決定每張圖片的儲存位置

Aspose 允許透過 `IResourceSavingCallback` 在儲存過程中掛鉤。每個外部資源（圖片、CSS 等）都會傳入一個 `ResourceSavingArgs` 物件。我們會利用它把每張圖片導入專屬資料夾，同時保留原始檔名。

```csharp
// Step 2: Define a callback that decides where each image is saved.
class MyMarkdownResourceCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Build a path like: YOUR_DIRECTORY\MarkdownResources\image001.png
        string resourcesFolder = Path.Combine("YOUR_DIRECTORY", "MarkdownResources");
        Directory.CreateDirectory(resourcesFolder); // ensures the folder exists

        string imagePath = Path.Combine(resourcesFolder, args.ResourceFileName);

        // Tell Aspose where to write the file.
        args.ResourceFilePath = imagePath;
        args.Stream = new FileStream(imagePath, FileMode.Create, FileAccess.Write);
    }
}
```

*為什麼重要*：若不使用回呼，Aspose 會把圖片直接放在 markdown 檔案同一資料夾，且使用通用名稱。自行控制路徑可讓專案保持整潔，避免命名衝突。

**邊緣情況** – 某些 Word 檔會多次嵌入相同圖片。`args.ResourceFileName` 已包含唯一雜湊碼，因此不會被覆寫。若想改用順序編號，可在回呼內維護一個靜態計數器。

---

## 步驟 3 – 設定 Markdown 儲存選項以使用自訂回呼

現在把回呼掛到 markdown 匯出器。`MarkdownSaveOptions` 也允許調整標題層級、程式碼區塊圍欄，或是否以 Base64 內嵌圖片（此處我們 **不** 這麼做）。

```csharp
// Step 3: Configure Markdown save options to use the custom callback.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // Attach our resource‑saving logic.
    ResourceSavingCallback = new MyMarkdownResourceCallback(),

    // Optional: keep original line breaks for better diff‑friendliness.
    ExportHeadersFooters = false,
    ExportImagesAsBase64 = false
};
```

*為什麼重要*：`ResourceSavingCallback` 屬性是文件模型與檔案系統之間的橋樑。若忘記設定，圖片會遺失，且 markdown 會引用不存在的檔案。

---

## 步驟 4 – 儲存文件為 Markdown，讓回呼為每個資源執行

最後，呼叫 Aspose 產生 markdown 檔案。程式庫會為每張圖片呼叫我們的回呼，寫入圖片檔，然後在 markdown 中插入相對連結。

```csharp
// Step 4: Save the document as Markdown, invoking the callback for each resource.
const string outputPath = @"YOUR_DIRECTORY\output.md";

doc.Save(outputPath, mdOptions);
```

程式執行完畢後，磁碟上應該會出現兩樣東西：

1. **output.md** – 原始 Word 內容的 Markdown 表示。  
2. **MarkdownResources/** – 放置所有擷取圖片的資料夾（例如 `image001.png`、`image002.jpg`）。

**驗證方式** – 在任意 markdown 檢視器開啟 `output.md`，你會看到類似 `![image001.png](MarkdownResources/image001.png)` 的圖片標記。若圖片正確顯示，即表示成功。

---

## 常見變化與假設情境

### 1. 想把圖片內嵌為 Base64？

在 `MarkdownSaveOptions` 中設定 `ExportImagesAsBase64 = true`。這會產生單一 markdown 檔，內含資料 URI，適合單檔文件，但會大幅增加檔案大小。

### 2. 只需要 PNG 圖片？

在回呼中加入副檔名過濾：

```csharp
if (Path.GetExtension(args.ResourceFileName).Equals(".png", StringComparison.OrdinalIgnoreCase))
{
    // Save as before.
}
else
{
    // Skip non‑PNG resources.
    args.Cancel = true;
}
```

### 3. 執行時變更輸出資料夾

透過命令列參數或設定檔傳入資料夾路徑，然後在建立 `resourcesFolder` 時使用該變數。如此一來工具即可在不同專案間重複使用。

### 4. 處理大型文件

對於巨大的 Word 檔，考慮以串流方式輸出以避免一次載入全部內容。Aspose 的 `Document` 已具備低記憶體占用，但你也可以在 `LoadOptions` 上設定 `MemoryOptimization = MemoryOptimization.MemoryOptimized`。

---

## 完整、可執行範例

以下程式碼可直接貼到新建的 Console App（`dotnet new console`）中。記得將 `YOUR_DIRECTORY` 替換為本機實際路徑，並加入 Aspose.Words NuGet 套件（`dotnet add package Aspose.Words`）。

```csharp
// Program.cs
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

namespace DocxToMarkdown
{
    // Step 2: Callback that saves each image into a dedicated folder.
    class MyMarkdownResourceCallback : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            string resourcesFolder = Path.Combine("YOUR_DIRECTORY", "MarkdownResources");
            Directory.CreateDirectory(resourcesFolder);

            string imagePath = Path.Combine(resourcesFolder, args.ResourceFileName);
            args.ResourceFilePath = imagePath;
            args.Stream = new FileStream(imagePath, FileMode.Create, FileAccess.Write);
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // Step 1: Load the source document.
            const string inputPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(inputPath);

            // Step 3: Configure the markdown options.
            MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
            {
                ResourceSavingCallback = new MyMarkdownResourceCallback(),
                ExportImagesAsBase64 = false,
                ExportHeadersFooters = false
            };

            // Step 4: Save as markdown.
            const string outputPath = @"YOUR_DIRECTORY\output.md";
            doc.Save(outputPath, mdOptions);

            Console.WriteLine("Conversion complete!");
            Console.WriteLine($"Markdown file: {outputPath}");
            Console.WriteLine($"Images folder: {Path.Combine("YOUR_DIRECTORY", "MarkdownResources")}");
        }
    }
}
```

**預期輸出**（於主控台）：

```
Conversion complete!
Markdown file: C:\Projects\MyDocs\output.md
Images folder: C:\Projects\MyDocs\MarkdownResources
```

開啟 `output.md` 後，你會看到包含指向 `MarkdownResources` 資料夾的圖片引用的 markdown 語法。所有圖片保留原始檔名，方便對照來源 Word 文件。

---

## 結論

我們剛剛示範了如何使用 Aspose.Words **將 Word 另存為 Markdown**，同時 **從 docx 中擷取圖片**。關鍵在於 `IResourceSavingCallback`——它讓你完整掌控每個資源的存放位置，從而保持 markdown 整潔、圖片有序。

在單一、獨立的程式中，你可以：

* 將任意 *.docx* 轉換成乾淨的 markdown（`convert docx to markdown`）。  
* 保留每張圖片（`save images from docx`）。  
* 依需求自訂輸出版面，供後續管線使用。

接下來的步驟？嘗試以相同回呼模式轉換成 HTML 或 PDF，或將此工具整合到 CI 工作流，自動同步 Word 報告至靜態網站倉庫。可能性無限，而你現在已擁有堅實的基礎。

有問題或發現更棒的調整方式？歡迎在下方留言——祝開發順利！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}