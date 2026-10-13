---
category: general
date: 2026-01-03
description: 一次性將 Word 轉換為 Markdown 並嵌入 base64 圖片。了解如何將 Word 儲存為 Markdown、從 Word 產生
  Markdown，以及使用 base64 圖片 data uri。
draft: false
keywords:
- convert word to markdown
- embed images as base64
- save word as markdown
- base64 image data uri
- generate markdown from word
language: zh-hant
og_description: 將 Word 轉換為 Markdown，並將圖片嵌入為 base64 資料 URI。此一步一步的教學示範如何將 Word 儲存為 Markdown
  以及如何從 Word 產生 Markdown。
og_title: 將 Word 轉換為 Markdown – Base64 圖片嵌入指南
tags:
- Aspose.Words
- C#
- Markdown
title: 將 Word 轉換為 Markdown – 嵌入圖片為 Base64
url: /zh-hant/net/programming-with-markdownsaveoptions/convert-word-to-markdown-embed-images-as-base64/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 轉換 Word 為 Markdown – 以 Base64 嵌入圖片

有沒有曾經需要 **convert Word to markdown**（將 Word 轉換為 markdown），卻一直被圖片卡住？你並不是唯一遇到這個問題的人。Word 喜歡把圖片存成獨立檔案，而 markdown 則偏好使用 `data:image/...;base64,` 這類字串，將所有內容整合在單一檔案中。

在本教學中，我們將逐步說明一個完整、可直接執行的解決方案，該方案 **saves Word as markdown**（將 Word 儲存為 markdown）、**embeds images as base64**（以 Base64 嵌入圖片），甚至示範如何使用 Aspose.Words for .NET **generate markdown from Word**（從 Word 產生 markdown）。完成後，你將得到一個單一的 `.md` 檔案，呈現效果與原始文件完全相同——不需要額外的圖片資料夾。

## 需要的環境

- **.NET 6.0 或更新版本**（任何能引用 NuGet 套件的環境）
- **Aspose.Words for .NET**（免費試用版足以測試）
- 一個包含少量圖片的簡易 `.docx` 檔案（我們稱之為 `input.docx`）
- 你喜愛的 IDE（Visual Studio、Rider、VS Code——隨你選擇）

如果你已經具備上述條件，太好了——直接開始吧。若尚未安裝，只需一行指令即可安裝 NuGet 套件：

```bash
dotnet add package Aspose.Words
```

## 步驟 1：載入 Word 文件 — **convert word to markdown** 的起點

首先，我們需要將 `.docx` 載入記憶體。這就是轉換魔法的起點。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

// Load the Word file that contains the images.
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

> **為什麼這很重要：**  
> 載入文件讓 Aspose 完全存取文字、樣式以及所有嵌入的資源。若缺少此步驟，將無法進行任何轉換。

## 步驟 2：設定 MarkdownSaveOptions 並使用 Resource‑Saving Callback

Aspose 允許你攔截所有通常會寫入磁碟的資源（例如圖片）。透過提供自訂的 `IResourceSavingCallback`，我們可以將預設的檔案儲存方式改為 **base64 圖片 data uri**。

```csharp
// Configure Markdown save options so that images become Base64 URIs.
MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new MyResourceHandler()
};
```

### 自訂處理程式 – 將圖片轉為 Base64

以下為完整實作。請注意我們如何檢查 `args.ResourceType == ResourceType.Image`，接著：

1. 將圖片寫入 `MemoryStream`。
2. 將位元組陣列轉換為 Base64 字串。
3. 組合 `data:image/jpeg;base64,` URI，並指派給 `args.Uri`。

```csharp
// Custom handler that converts each image resource to a Base64 data URI.
class MyResourceHandler : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Only process images – leave other resources untouched.
        if (args.ResourceType == ResourceType.Image)
        {
            // Prepare an in‑memory stream for the image.
            using (MemoryStream ms = new MemoryStream())
            {
                // Save the image using default JPEG options.
                args.ResourceData.Save(ms, ImageSaveOptions.DefaultJpeg);
                // Build the Base64 data URI.
                string base64 = Convert.ToBase64String(ms.ToArray());
                args.Uri = $"data:image/jpeg;base64,{base64}";
                // No need to keep the stream open after we set the URI.
                args.KeepResourceStreamOpen = false;
            }
        }
    }
}
```

> **專業提示：** 若來源 Word 使用 PNG 圖片，請將 `ImageSaveOptions.DefaultJpeg` 換成 `ImageSaveOptions.DefaultPng`，並相應地更改 MIME 類型（`image/png`）。

## 步驟 3：將文件儲存為 Markdown – 最後的 **save word as markdown** 步驟

現在 Callback 已設定完成，實際的儲存只需要一行程式碼。

```csharp
// Save the document to a Markdown file. Images are already embedded.
document.Save("YOUR_DIRECTORY/output.md", markdownSaveOptions);
```

當你在任何 markdown 檢視器（VS Code 預覽、GitHub 等）開啟 `output.md` 時，會看到文字與原始 Word 檔案完全相同，且圖片會內嵌顯示，無需額外的圖片檔案。

## 預期輸出

```markdown
# Sample Title

Here’s a paragraph that originally lived in Word.

![Embedded Image](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAkGBxISEhU...
```

`![Embedded Image]` 這一行是一個 **base64 image data uri**——整張圖片直接在此編碼。沒有額外的資料夾，也不會出現斷掉的連結。

## 邊緣案例與處理方式

| 情況 | 處理方式 |
|-----------|------------|
| **大型圖片** – Base64 會使大小膨脹約 33% | 考慮在轉換前先調整大小：`args.ResourceData.Save(ms, new ImageSaveOptions { ImageResolution = 72 })`。 |
| **非 JPEG 圖片**（PNG、GIF） | 透過 `args.ResourceData.ImageType` 偵測原始格式，並設定正確的 MIME 類型（`image/png`、`image/gif`）。 |
| **超長文件**（數百張圖片） | 留意記憶體使用情況；若記憶體不足，可暫時將每張圖片串流寫入磁碟。 |
| **需要分離的圖片檔案**（例如靜態網站） | 對想保留為檔案的圖片，在回呼中回傳 `false`，讓 Aspose 寫入資料夾。 |

## 常見問題（先行解答）

- **這能處理 .doc 檔案嗎？** 可以——Aspose.Words 能以與載入 `.docx` 相同的方式載入舊版 `.doc` 檔案。只要使用 `new Document("myfile.doc")` 即可。
- **表格與註腳怎麼處理？** Markdown 匯出器完整支援它們。表格會轉為 markdown 表格，註腳則會變成內嵌參考。
- **我可以更換 markdown 風格嗎？** `MarkdownSaveOptions` 提供 `MarkdownVersion` 屬性（CommonMark、GitHub 等）。若需特定語法，請在儲存前設定此屬性。

## 完整、可直接執行的範例

以下為完整程式碼，你可以直接貼到 Console 應用程式中。它包含所有 using 陳述式、處理程式類別與錯誤處理。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

namespace WordToMarkdownDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            try
            {
                // 1️⃣ Load the source Word document.
                Document doc = new Document("YOUR_DIRECTORY/input.docx");

                // 2️⃣ Prepare Markdown options with our custom image handler.
                MarkdownSaveOptions options = new MarkdownSaveOptions
                {
                    ResourceSavingCallback = new MyResourceHandler()
                };

                // 3️⃣ Save as Markdown – images become Base64 URIs.
                string outputPath = "YOUR_DIRECTORY/output.md";
                doc.Save(outputPath, options);

                Console.WriteLine($"✅ Success! Markdown saved to {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"❌ Conversion failed: {ex.Message}");
            }
        }
    }

    // Custom callback that embeds images as Base64 data URIs.
    class MyResourceHandler : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            if (args.ResourceType == ResourceType.Image)
            {
                using (MemoryStream ms = new MemoryStream())
                {
                    // Preserve original format if you prefer PNG/GIF.
                    args.ResourceData.Save(ms, ImageSaveOptions.DefaultJpeg);
                    string base64 = Convert.ToBase64String(ms.ToArray());
                    args.Uri = $"data:image/jpeg;base64,{base64}";
                    args.KeepResourceStreamOpen = false;
                }
            }
        }
    }
}
```

執行程式，開啟產生的 `output.md`，即可看到與 Word 檔案完全相同的 markdown 複製版——**convert word to markdown** 從未如此簡單。

## 重點回顧

我們從 **convert word to markdown** 同時內嵌圖片的問題開始說起。透過載入文件、設定 `MarkdownSaveOptions` 的回呼，並儲存檔案，我們完成了一個乾淨的 **save word as markdown** 解決方案，產生 **base64 image data uri** 字串。現在你也知道如何 **embed images as base64**、處理各種邊緣案例，並針對不同圖片類型微調流程。

## 接下來可以做什麼？

- **產生 HTML 而非 markdown** – 將 `MarkdownSaveOptions` 換成 `HtmlSaveOptions`，並重複使用相同的回呼。
- **批次轉換多個檔案** – 在資料夾上使用 `foreach` 迴圈包住邏輯。
- **整合至 CI 流程** – 自動化產生靜態網站的文件。

歡迎自行實驗、調整圖片品質，甚至加入自訂的資源處理（例如上傳圖片至 CDN 並插入 URL）。只要結合 Aspose.Words 與一點 C# 靈感，想像空間無限。

祝程式開發愉快，願你的 markdown 永遠完美呈現！

![示意圖：convert word to markdown 流程 – 以 base64 嵌入圖片](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iNjAwIiBoZWlnaHQ9IjQwMCIgdmlld0JveD0iMCAwIDYwMCA0MDAiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI+PHJlY3Qgd2lkdGg9IjYwMCIgaGVpZ2h0PSI0MDAiIGZpbGw9IiNmZmYiIHN0cm9rZT0iI2NjYyIgLz48dGV4dCB4PSI1MCIgeT0iMjAwIiBmb250LXNpemU9IjM2IiBmaWxsPSIjMDAwIj5JbWFnZSBJbWFnZSBJbWFnZSBJbWFnZTwvdGV4dD48L3N2Zz4= "convert word to markdown flow diagram")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}