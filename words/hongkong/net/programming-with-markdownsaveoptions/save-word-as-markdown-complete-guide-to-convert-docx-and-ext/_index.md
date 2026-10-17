---
category: general
date: 2026-03-13
description: 將 Word 儲存為 Markdown，並在將 DOCX 轉換為 Markdown 時提取圖片。了解如何使用 Aspose.Words 於
  C# 中從 DOCX 提取圖片。
draft: false
keywords:
- save word as markdown
- convert docx to markdown
- extract images from docx
- how to extract images
- extract embedded images word
language: zh-hant
og_description: 在 C# 中將 Word 儲存為 Markdown。本指南說明如何將 DOCX 轉換為 Markdown 並提取圖片，提供即用的解決方案。
og_title: 將 Word 儲存為 Markdown – 轉換 DOCX 並提取圖片
tags:
- Aspose.Words
- C#
- Markdown
title: 將 Word 儲存為 Markdown – 完整指南：轉換 DOCX 並提取圖片
url: /zh-hant/net/programming-with-markdownsaveoptions/save-word-as-markdown-complete-guide-to-convert-docx-and-ext/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 儲存 Word 為 Markdown – 完整的 DOCX 轉換與圖片抽取指南

曾經想 **將 Word 儲存為 markdown**，卻不知如何保留圖片完整嗎？你並不孤單。許多開發者在 DOCX 檔案內含嵌入圖形時卡住，簡易轉換器會拋出一堆失效的連結。  

在本教學中，我們將一步步示範一個實用解決方案，**將 DOCX 轉換為 markdown** **同時** 把每張圖片抽取到你自行指定的資料夾。完成後，你將擁有乾淨的 `.md` 檔案、整齊的 `markdown_resources` 目錄，以及對於為何回呼 (callback) 方法是處理資源最可靠方式的深入了解。

> **小技巧：** 同樣的模式也適用於 CSS、字型，或任何 Aspose.Words 在儲存過程中可能產生的外部資源。

![Save Word as Markdown conversion flow diagram](conversion-diagram.png "Conversion flow diagram")

## 你將學到什麼

- 如何使用 Aspose.Words for .NET **將 Word 儲存為 markdown**。
- **將 docx 轉換為 markdown** 同時保留圖片的完整步驟。
- 可重複使用的 `IResourceSavingCallback` 實作，**從 docx 中抽取圖片**。
- 常見陷阱（例如檔名重複、資料夾遺失）以及避免方式。
- 產生的 markdown 內容長什麼樣，圖片會被放在哪裡。

你需要一個近期版本的 **Aspose.Words for .NET**（本指南測試於 24.12）以及 .NET 6 以上的執行環境。除此之外不需要其他第三方函式庫。

---

## 前置條件

| 前置條件 | 為何重要 |
|----------|----------|
| Aspose.Words for .NET（NuGet `Aspose.Words`） | 提供 `Document` 類別與 `MarkdownSaveOptions`。 |
| .NET 6 或更新版本 | 確保 `using` 陳述式等語言功能可直接使用，無需額外程式碼。 |
| 含有圖片的 DOCX 檔（例如 `Images.docx`） | 我們將從此檔案轉換並抽取圖片。 |
| 對輸出資料夾的寫入權限 | 回呼會寫入圖片檔案，若無權限會拋出例外。 |

如果你已具備上述條件，太好了——讓我們直接開始。

---

## 步驟 1：載入來源 DOCX – Save Word as Markdown 的起點

首先，我們要開啟 Word 文件。Aspose.Words 會將檔案讀入記憶體，保留所有內部結構（段落、表格、圖片等）。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// Load the DOCX that contains images.
Document sourceDoc = new Document("YOUR_DIRECTORY/Images.docx");
```

> **為何重要：** 先載入檔案可讓我們在需要除錯缺圖時，檢查內容（例如 `sourceDoc.GetChildNodes(NodeType.Shape, true)`）。

---

## 步驟 2：設定 Markdown 儲存選項與圖片儲存回呼

當 Aspose.Words 寫入 markdown 檔案時，可能需要儲存外部資源（如圖片）。透過掛載 `ResourceSavingCallback`，我們即可完全掌控這些檔案的存放位置與命名方式。

```csharp
// Prepare markdown options and tell Aspose.Words to use our callback.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // The callback fires for every image, CSS file, etc.
    ResourceSavingCallback = new ImageSavingCallback()
};
```

> **如何抽取圖片：** 回呼會收到一個 `ResourceSavingArgs` 例項，內含圖片串流、原始檔名與索引。我們可以重新命名、搬移，甚至完全跳過儲存。

---

## 步驟 3：將文件儲存為 Markdown – Save Word as Markdown 的核心

現在呼叫 `Document.Save`。函式庫會為每張圖片呼叫我們的回呼，將圖片寫入指定位置，最後產生含正確 `![]()` 連結的 markdown 檔案。

```csharp
// Execute the conversion. The markdown file will reference the extracted images.
sourceDoc.Save("YOUR_DIRECTORY/DocWithImages.md", mdOptions);
```

此時，你應該在 `YOUR_DIRECTORY` 中看到兩樣東西：

1. `DocWithImages.md` – 原始 Word 檔的 markdown 表現形式。
2. `markdown_resources` 資料夾 – 包含 `img_0.png`、`img_1.jpg`… 等檔案的集合。

---

## 步驟 4：實作圖片儲存回呼 – 從 DOCX 抽取圖片

以下為完整的回呼類別。它會在需要時建立資料夾、產生唯一檔名、寫入圖片串流，然後透過設定 `args.FileName` 告訴 Aspose.Words 使用我們的檔名，並將 `args.Stream = null` 以跳過預設儲存。

```csharp
public class ImageSavingCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // 1️⃣ Ensure the resources folder exists.
        string resourcesFolder = "YOUR_DIRECTORY/markdown_resources";
        Directory.CreateDirectory(resourcesFolder);

        // 2️⃣ Build a unique name – img_0.png, img_1.jpg, etc.
        string imageFileName = Path.Combine(
            resourcesFolder,
            $"img_{args.ImageIndex}{Path.GetExtension(args.FileName)}");

        // 3️⃣ Write the image stream to disk.
        using (FileStream fileStream = new FileStream(imageFileName, FileMode.Create))
        {
            args.Stream.CopyTo(fileStream);
        }

        // 4️⃣ Tell the markdown writer to reference the new name.
        args.FileName = Path.GetFileName(imageFileName);
        args.Stream = null; // Prevent default saving – we already handled it.
    }
}
```

### 為何這樣可行

- **確定的檔名** – 使用 `args.ImageIndex` 可保證唯一性，即使原始 DOCX 有重複名稱也不會衝突。
- **資料夾隔離** – 所有抽出的資產都放在 `markdown_resources` 下，讓專案保持整潔。
- **效能** – 直接複製串流，無額外緩衝或影像處理，轉換速度快。

---

## 步驟 5：驗證輸出 – Markdown 長什麼樣

在任意編輯器開啟 `DocWithImages.md`，你應該會看到類似以下內容：

```markdown
# Sample Document

Here is an illustration:

![](markdown_resources/img_0.png)

Another picture appears below:

![](markdown_resources/img_1.jpg)
```

若在支援相對路徑的檢視器（VS Code 預覽、GitHub 等）中開啟 markdown，圖片會正確顯示。

### 快速檢查

```bash
# On Linux/macOS
cat YOUR_DIRECTORY/DocWithImages.md | grep -E '\!\[.*\]\(markdown_resources/img_.*\)'
```

每張圖片應該會產生一行；行數應與 `Images.docx` 中原始嵌入的圖片數量相符。

---

## 常見問題與邊緣案例

### 如果 DOCX 包含 SVG 或 EMF 圖形該怎麼辦？

Aspose.Words 會自動將大多數向量格式轉為 PNG。回呼仍會收到串流，且檔案副檔名為 `.png`，不需要額外程式碼。

### 如何變更輸出資料夾名稱？

只要修改 `ImageSavingCallback` 中的 `resourcesFolder` 變數即可。記得同時保留相同的相對參考（`args.FileName = Path.GetFileName(imageFileName)`），讓 markdown 連結保持正確。

### 能否跳過儲存特定圖片（例如過大的）？

可以。於回呼內檢查 `args.Stream.Length`。若超過門檻，你可以改名為佔位圖，或設定 `args.Cancel = true` 完全省略。

```csharp
if (args.Stream.Length > 5 * 1024 * 1024) // >5 MB
{
    args.Cancel = true; // Image will be omitted from markdown.
    return;
}
```

### 這個方式能否用於其他資源類型（如 CSS）？

絕對可以。相同的回呼會對任何外部資源觸發。你可以根據 `args.ContentType` 分支處理 CSS、字型或影片等。

---

## 完整可執行範例 – 直接複製貼上

以下是一個自包含的程式，你只要把它貼到 Console App 中即可。將 `YOUR_DIRECTORY` 替換為你機器上的絕對或相對路徑。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

namespace DocxToMarkdownDemo
{
    class Program
    {
        static void Main()
        {
            // ① Load the source DOCX that contains images.
            Document sourceDoc = new Document("YOUR_DIRECTORY/Images.docx");

            // ② Configure markdown options with our callback.
            MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
            {
                ResourceSavingCallback = new ImageSavingCallback()
            };

            // ③ Save as markdown – images will be stored by the callback.
            sourceDoc.Save("YOUR_DIRECTORY/DocWithImages.md", mdOptions);

            // ④ Inform the user.
            System.Console.WriteLine("Conversion complete! Check the markdown file and the markdown_resources folder.");
        }
    }

    // ⑤ Callback that extracts each image to a custom folder.
    public class ImageSavingCallback : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            string resourcesFolder = "YOUR_DIRECTORY/markdown_resources";
            Directory.CreateDirectory(resourcesFolder);

            string imageFileName = Path.Combine(
                resourcesFolder,
                $"img_{args.ImageIndex}{Path.GetExtension(args.FileName)}");

            using (FileStream fileStream = new FileStream(imageFileName, FileMode.Create))
            {
                args.Stream.CopyTo(fileStream);
            }

            args.FileName = Path.GetFileName(imageFileName);
            args.Stream = null; // Skip default saving.
        }
    }
}
```

執行程式、開啟產生的 markdown，你會看到所有圖片正好出現在原始 Word 文件的相同位置。

---

## 結論

我們剛剛說明了 **如何在保存 Word 為 markdown 時** **抽取 docx 中的圖片**，並以乾淨的回呼模式完成。關鍵在於 `IResourceSavingCallback` 讓你對每個外部檔案擁有完整控制，使轉換在任何生產流程中都可靠。

在單一、可直接複製的範例中，我們：

1. 載入含圖片的 DOCX。
2. 使用自訂 `ImageSavingCallback` 設定 `MarkdownSaveOptions`。
3. 儲存文件為 markdown，讓回呼將每張圖片寫入 `markdown_resources`。
4. 驗證輸出，並討論如何針對邊緣案例調整流程。

接下來你可以：

- 透過遍歷資料夾批次 **將 docx 轉換為 markdown**。
- 依據原始說明文字重新命名圖片，以提升 SEO。
- **與靜態網站產生器**（如 Hugo、Jekyll）整合，將 markdown 資料夾搬入內容樹。
- **擴充回呼**，同時抽取嵌入字型或 CSS，實現完整的自包含 HTML 匯出。

盡情實驗吧——或許可以改用 GUID 作為圖片命名以保證絕對唯一，或加入日誌記錄每個儲存的資源。只要掌握了儲存流程，未來的可能性無限。

祝開發順利，願你的 markdown 永遠正確顯示圖片！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}