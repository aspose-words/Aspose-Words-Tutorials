---
category: general
date: 2025-12-29
description: 儲存 docx 為 markdown 使用 Aspose.Words。學習將 Word 轉換為 markdown、擷取圖片、建立資源資料夾，並設定
  markdown 選項。
draft: false
keywords:
- save docx as markdown
- convert word to markdown
- how to extract images
- create resources folder
- how to configure markdown
language: zh-hant
og_description: 使用 Aspose.Words 將 docx 另存為 markdown。逐步指南：將 Word 轉換為 markdown、提取圖片、建立資源資料夾，並設定
  markdown。
og_title: 將 docx 另存為 markdown – 完整 C# 教程
tags:
- Aspose.Words
- C#
- Document Conversion
title: 將 docx 另存為 markdown – 完整 C# 指南（含圖片提取）
url: /zh-hant/net/programming-with-markdownsaveoptions/save-docx-as-markdown-full-c-guide-with-image-extraction/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 將 docx 另存為 markdown – 完整 C# 教學

是否曾經需要 **save docx as markdown**，卻不確定如何保留內嵌圖片？你並不孤單。許多開發者在轉換時圖片會遺失，導致 Markdown 檔案空空如也。在本指南中，我們將逐步說明一個實用解決方案，不僅能 **convert word to markdown**，還會示範 **how to extract images**，自動 **create resources folder**，以及正確 **how to configure markdown** 選項，以產生乾淨的輸出。

閱讀完本文後，你將擁有一段可直接執行的 C# 程式碼，能夠接受任意 `.docx`，提取所有圖片，將它們存放於專屬目錄，並產生一個 Markdown 檔案，圖片連結指向該資料夾。無需額外的後處理。

## 你將學會

- 使用 Aspose.Words 載入 Word 文件。
- 設定 `MarkdownSaveOptions` 以捕獲外部資源。
- 自動在 Markdown 檔案旁產生 **Resources** 資料夾。
- 使用 `ResourceSavingCallback` 寫入圖片檔案。
- 驗證產生的 Markdown 正確引用圖片。

### 前置條件

- .NET 6+（或 .NET Framework 4.6+）。  
- Aspose.Words for .NET（NuGet 套件 `Aspose.Words`）。  
- 一個包含至少一張圖片的範例 `input.docx`。

如果你已經具備上述條件，太好了——讓我們開始吧。

## 步驟 1 – 載入 Word 文件

我們首先要做的事就是開啟來源檔案。此步驟簡單卻關鍵；文件物件同時是文字與媒體的來源。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// Load the Word document that contains images.
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

> **為何重要：**  
> 載入檔案會在記憶體中建立一個表示，讓 Aspose 能夠列舉每個節點——段落、表格，以及關鍵的包含圖片的 `Shape` 物件。若未載入，就無法提取任何內容。

## 步驟 2 – 設定 Markdown 選項（轉換的核心）

現在我們告訴 Aspose 我們希望 Markdown 檔案如何運作。`MarkdownSaveOptions` 類別提供 `ResourceSavingCallback` 委派，會在每個外部資源（圖片、圖表等）時觸發。在該回呼中，我們決定檔案寫入位置以及嵌入的 URI。

```csharp
// Set up Markdown save options with a callback for external resources.
MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions
{
    // The callback runs for every image/chart the exporter needs to write.
    ResourceSavingCallback = (sender, args) =>
    {
        // Step 3 – Ensure the Resources folder exists.
        string resourcesFolder = "YOUR_DIRECTORY/Resources/";
        Directory.CreateDirectory(resourcesFolder);

        // Build the absolute path for the image file.
        string resourceFilePath = Path.Combine(resourcesFolder, args.ResourceFileName);
        args.Stream = new FileStream(resourceFilePath, FileMode.Create);

        // Use a relative path in the generated Markdown file.
        args.Uri = "Resources/" + args.ResourceFileName;
    }
};
```

### 如何設定 Markdown 以提取圖片

- **`ResourceSavingCallback`** – 讓我們可以自行決定每張圖片寫入位置的掛鉤。  
- **`args.ResourceFileName`** – Aspose 產生的唯一檔名（例如 `image001.png`）。  
- **`args.Uri`** – 最終出現在 Markdown 連結中的字串；我們將其設為相對路徑，使 Markdown 可攜。

> **提示：** 若需要自訂命名規則（例如保留原始圖片名稱），可在指派 `args.Uri` 前檢查並替換 `args.ResourceFileName`。

## 步驟 3 – 建立 Resources 資料夾（並提取圖片）

我們在前一步定義的回呼已會即時建立資料夾，但讓我們說明為何這是建議的做法。

```csharp
// Inside the callback (repeated for emphasis):
string resourcesFolder = "YOUR_DIRECTORY/Resources/";
Directory.CreateDirectory(resourcesFolder);
```

> **為何建立專屬資料夾？**  
> 將圖片存放於獨立目錄可讓 Markdown 保持整潔，且符合許多靜態網站產生器（如 Jekyll 或 Hugo）對資產的組織方式。若多次執行轉換，也能避免檔名衝突。

### 邊緣情況與變化

| Situation | What to Adjust |
|-----------|----------------|
| **大量圖片的 DOCX（數百張）** | 考慮串流圖片以避免記憶體壓力；回呼已直接將每張圖片寫入磁碟，具記憶體效益。 |
| **非 PNG 圖片（例如 JPEG、GIF）** | `args.ResourceFileName` 已包含正確的副檔名，無需額外處理。 |
| **自訂輸出路徑** | 將 `"YOUR_DIRECTORY/Resources/"` 替換為相對於專案根目錄的路徑，或從設定檔讀取。 |

## 步驟 4 – 將文件另存為 Markdown

在完整設定選項後，最後一步只需一行程式碼即可寫入 Markdown 檔案，並為每張圖片觸發回呼。

```csharp
// Save the document as Markdown, applying the resource handling logic.
document.Save("YOUR_DIRECTORY/WithResources.md", markdownSaveOptions);
```

### 預期結果

- `WithResources.md` – 包含標準語法（`![Alt text](Resources/image001.png)`）的 Markdown 檔案，對應每張圖片。  
- `Resources/` – 已填入提取圖片檔案的資料夾。

你可以在任何檢視器（VS Code、GitHub 或靜態網站產生器）中開啟此 Markdown，應能看到原始圖片正確呈現在 Word 文件中的位置。

![顯示 Resources 資料夾及提取圖片的資料夾結構 – save docx as markdown](https://example.com/placeholder.png "提取圖片的資料夾結構 – save docx as markdown")

*圖片 alt 文字：“提取圖片的資料夾結構 – save docx as markdown” – 符合主要關鍵字的圖片 alt 要求。*

## 完整範例（可直接複製貼上）

以下是完整程式碼，可直接放入 Console 應用程式。請將 `YOUR_DIRECTORY` 替換為你機器上的實際路徑。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the source DOCX.
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Prepare Markdown options with a resource callback.
        MarkdownSaveOptions options = new MarkdownSaveOptions
        {
            ResourceSavingCallback = (sender, args) =>
            {
                // 3️⃣ Ensure the Resources folder exists.
                string resourcesFolder = "YOUR_DIRECTORY/Resources/";
                Directory.CreateDirectory(resourcesFolder);

                // 4️⃣ Write the image file to disk.
                string filePath = Path.Combine(resourcesFolder, args.ResourceFileName);
                args.Stream = new FileStream(filePath, FileMode.Create);

                // 5️⃣ Set the relative URI used in the Markdown file.
                args.Uri = "Resources/" + args.ResourceFileName;
            }
        };

        // 6️⃣ Save as Markdown – this triggers the callback for each image.
        document.Save("YOUR_DIRECTORY/WithResources.md", options);

        // Inform the user.
        System.Console.WriteLine("Conversion complete! Check the Resources folder and the Markdown file.");
    }
}
```

### 執行範例

1. 安裝 Aspose.Words NuGet 套件：  
   ```bash
   dotnet add package Aspose.Words
   ```
2. 編譯並執行：  
   ```bash
   dotnet run
   ```
3. 在任何 Markdown 檢視器中開啟 `WithResources.md`。所有圖片應會顯示。

## 常見問題與專業技巧

### 「可以將 .doc 轉換而非 .docx 嗎？」

當然可以——Aspose.Words 同時支援 `.doc` 與 `.docx`。只要在 `Document` 建構子中更改檔案副檔名即可。

### 「如果我不想要 Resources 資料夾怎麼辦？」

你可以將 `args.Uri` 指向任何位置，甚至是 URL。例如，設定 `args.Uri = "https://mycdn.com/" + args.ResourceFileName;`，即可省略資料夾建立。

### 「如何處理 SVG 圖形？」

Aspose 將 SVG 視為獨立的資源類型。在回呼中可檢查 `args.ResourceType`，若為 `ResourceType.Svg`，即可自行重新命名或另行處理。

### 「有沒有辦法將圖片嵌入為 Base64？」

可以——不寫入檔案，而是將 `args.Stream` 轉換為 Base64 字串，並指派 `args.Uri = "data:image/png;base64," + base64;`。如此可讓 Markdown 自包含，但會增加檔案大小。

### 「需要哪個版本的 Aspose.Words？」

`MarkdownSaveOptions` 類別於 Aspose.Words 22.9 版首次加入。若使用較舊版本，請透過 NuGet 升級。

## 結論

我們已說明完成 **save docx as markdown** 同時保留所有圖片所需的全部步驟。關鍵流程如下：

1. 使用 Aspose.Words 載入 DOCX。  
2. 設定 `MarkdownSaveOptions` 並實作 `ResourceSavingCallback`。  
3. 在回呼中 **建立 resources 資料夾**、寫入每張圖片，並設定相對 URI。  
4. 儲存文件，讓 Aspose 處理繁重的轉換工作。

現在你可以自動化文件流程、將舊有 Word 手冊遷移至適合靜態網站的 Markdown，或僅提供團隊一種輕量、版本控制的格式，同時不失去視覺內容。

### 接下來可以做什麼？

- 嘗試 **how to configure markdown** 以自訂標題樣式或表格格式。  
- 將此轉換與 CI/CD 流程結合，自動發布文件。  
- 深入探索 Aspose 其他匯出格式（HTML、PDF），了解相同回呼模式的應用。

還有其他想了解的情境嗎？歡迎留言或在 Aspose 論壇開新議題。祝轉換順利！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}