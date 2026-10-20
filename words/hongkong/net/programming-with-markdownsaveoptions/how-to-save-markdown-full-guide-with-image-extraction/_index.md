---
category: general
date: 2026-03-30
description: 如何在 C# 中儲存 Markdown 檔案，同時從 Markdown 中提取圖像，並使用 Aspose.Words 將文件儲存為 Markdown。
draft: false
keywords:
- how to save markdown
- extract images from markdown
- save document as markdown
- markdown resource handling
- C# markdown export
language: zh-hant
og_description: 如何快速儲存 Markdown。學習從 Markdown 中提取圖片，並以完整程式碼範例將文件儲存為 Markdown。
og_title: 如何儲存 Markdown – 完整 C# 教學
tags:
- C#
- Markdown
- Aspose.Words
title: 如何儲存 Markdown – 完整指南與圖片提取
url: /zh-hant/net/programming-with-markdownsaveoptions/how-to-save-markdown-full-guide-with-image-extraction/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何儲存 Markdown – 完整 C# 指南

有沒有想過 **如何儲存 markdown** 同時保留所有嵌入的圖片？你並不是唯一有此疑問的人。許多開發者在使用函式庫時，會遇到圖片被隨意放入某個資料夾，甚至根本不被輸出。好消息是，只要寫幾行 C# 程式碼搭配 Aspose.Words，就能將文件匯出為 markdown，提取每張圖片，並精確控制每個檔案的儲存位置。

在本教學中，我們將示範一個實務案例：取得 `Document` 物件、設定 `MarkdownSaveOptions`，並告訴儲存器每張圖片要放在哪裡。完成後，你將能 **將文件儲存為 markdown**、**從 markdown 提取圖片**，並擁有整齊的資料夾結構以便發佈。沒有模糊的說明——只有完整、可直接執行的範例，讓你直接 copy‑paste。

## 需要的環境

- **.NET 6+**（任何較新的 SDK 都可）
- **Aspose.Words for .NET**（NuGet 套件 `Aspose.Words`）
- 對 C# 語法有基本了解（我們會保持簡單）
- 一個已存在的 `Document` 實例（我們會為示範建立一個）

如果你已備妥，讓我們馬上開始吧。

## 步驟 1：設定專案並匯入命名空間

首先，建立一個新的 console 應用程式（或整合到現有的解決方案中）。接著加入 Aspose.Words 套件：

```bash
dotnet add package Aspose.Words
```

現在匯入所需的命名空間：

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;
```

> **小技巧：** 請將 `using` 陳述式放在檔案最上方；這樣不論是人類還是 AI 解析器，都能更容易閱讀程式碼。

## 步驟 2：建立範例文件（或載入自己的文件）

為了示範，我們會建立一個包含段落與嵌入圖片的小文件。如果你已經有來源檔案，請將此段落改成 `Document.Load("YourFile.docx")`。

```csharp
// Step 2: Build a simple document with an image
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Add some text
builder.Writeln("Hello, Markdown world!");

// Insert an image from disk (make sure the path exists)
string imagePath = @"YOUR_DIRECTORY/sample-image.png";
builder.InsertImage(imagePath);
```

> **為什麼這很重要：** 若省略圖片，之後就沒有可 *提取* 的內容，也看不到回呼的執行效果。

## 步驟 3：使用 Resource‑Saving Callback 設定 MarkdownSaveOptions

這就是解決方案的核心。`ResourceSavingCallback` 會在 **每一個** 外部資源（圖片、字型、CSS 等）被儲存時觸發。我們會利用它建立專屬的 `Resources` 子資料夾，並為每個檔案指定唯一名稱。

```csharp
// Step 3: Define markdown save options and attach a callback
var markdownSaveOptions = new MarkdownSaveOptions
{
    // This delegate runs for each resource the saver wants to write out
    ResourceSavingCallback = (sender, args) =>
    {
        // Ensure the Resources folder exists (creates it only once)
        string resourcesFolder = @"YOUR_DIRECTORY/Resources/";
        Directory.CreateDirectory(resourcesFolder);

        // Build a unique filename: img_0.png, img_1.jpg, etc.
        string resourceFileName = $"img_{args.Index}{Path.GetExtension(args.FileName)}";

        // Tell the saver where to place the file
        args.SavePath = Path.Combine(resourcesFolder, resourceFileName);
    }
};
```

**發生了什麼？**  
- `args.Index` 是從零開始的計數器，保證唯一性。  
- `Path.GetExtension(args.FileName)` 會保留原始檔案類型（PNG、JPG 等）。  
- 透過設定 `args.SavePath`，我們覆寫預設位置，讓所有檔案保持整潔。

## 步驟 4：將文件儲存為 Markdown

將選項設定好後，匯出只需要一行程式碼：

```csharp
// Step 4: Export to markdown using the configured options
string outputMarkdown = @"YOUR_DIRECTORY/Doc.md";
doc.Save(outputMarkdown, markdownSaveOptions);
```

執行完畢後，你會看到：

- `Doc.md` 包含引用圖片的 markdown 文字。  
- 與之相鄰的 `Resources` 資料夾內保存 `img_0.png`、`img_1.jpg` …  

這就是 **如何儲存 markdown** 的完整流程，並同時完成資源提取。

## 步驟 5：驗證結果（可選但建議執行）

在任何文字編輯器中開啟 `Doc.md`。你應該會看到類似以下內容：

```markdown
Hello, Markdown world!

![image](Resources/img_0.png)
```

`Resources` 資料夾會包含你剛插入的原始圖片。若在支援 markdown 的檢視器（例如 VS Code、GitHub）中開啟 markdown 檔案，圖片會正確顯示。

> **常見問題：** *如果我想把圖片放在與 markdown 檔案相同的資料夾中呢？*  
> 只要將 `resourcesFolder` 改成 `Path.GetDirectoryName(outputMarkdown)`，並相應調整 markdown 圖片路徑即可。

## 從 Markdown 提取圖片 – 進階調整

有時你需要更細緻的命名規則，或想跳過特定類型的資源。以下提供幾個實用變體。

### 5.1 跳過非圖片資源

```csharp
ResourceSavingCallback = (sender, args) =>
{
    // Only process images; ignore CSS, fonts, etc.
    if (!args.ContentType.StartsWith("image/", StringComparison.OrdinalIgnoreCase))
        return; // Let the default handling continue

    // ...same folder creation logic as before...
};
```

### 5.2 保留原始檔名

如果你偏好使用原始檔名而非 `img_0`，只要去掉 `args.Index` 那一段：

```csharp
string resourceFileName = args.FileName; // uses the name from the source document
```

### 5.3 為每個文件使用自訂子資料夾

```csharp
string docName = Path.GetFileNameWithoutExtension(outputMarkdown);
string resourcesFolder = $@"YOUR_DIRECTORY/{docName}_Resources/";
Directory.CreateDirectory(resourcesFolder);
```

這些程式碼片段示範了 **從 markdown 提取圖片** 的彈性做法，能因應不同專案慣例。

## 常見問與答 (FAQ)

| 問題 | 答案 |
|----------|--------|
| **這能在 .NET Core 上使用嗎？** | 當然可以——Aspose.Words 支援跨平台，相同程式碼可在 Windows、Linux 或 macOS 上執行。 |
| **SVG 圖片怎麼處理？** | SVG 會被視為圖片；回呼會收到 `.svg` 副檔名。請確保你的 markdown 檢視器支援 SVG。 |
| **我可以變更 markdown 語法（例如使用 HTML `<img>` 標籤）嗎？** | 將 `markdownSaveOptions.ExportImagesAsBase64 = false`，若需要原始 HTML 標籤，請調整 `ExportImagesAsHtml`。 |
| **有沒有辦法批次處理多個文件？** | 將上述邏輯包在 `foreach` 迴圈中遍歷檔案集合——只要記得為每個文件分配自己的 resources 資料夾即可。 |

## 完整可執行範例（直接 copy‑paste）

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a document and add an image
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.Writeln("Hello, Markdown world!");
        string imagePath = @"YOUR_DIRECTORY/sample-image.png"; // <-- change this
        builder.InsertImage(imagePath);

        // 2️⃣ Configure save options with a callback to extract images
        var markdownSaveOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = (sender, args) =>
            {
                string resourcesFolder = @"YOUR_DIRECTORY/Resources/";
                Directory.CreateDirectory(resourcesFolder);

                string resourceFileName = $"img_{args.Index}{Path.GetExtension(args.FileName)}";
                args.SavePath = Path.Combine(resourcesFolder, resourceFileName);
            }
        };

        // 3️⃣ Save as markdown
        string outputPath = @"YOUR_DIRECTORY/Doc.md";
        doc.Save(outputPath, markdownSaveOptions);

        Console.WriteLine("Markdown saved successfully!");
        Console.WriteLine($"Check {outputPath} and the Resources folder for images.");
    }
}
```

執行程式 (`dotnet run`) 後，你會在主控台看到確認成功的訊息。所有圖片已整齊存放，且 markdown 檔案正確指向它們。

## 結論

你剛剛學會了 **如何儲存 markdown** 同時 **從 markdown 提取圖片**，並確保文件能 **將文件儲存為 markdown**，完整掌控資源的存放位置。關鍵在於 `ResourceSavingCallback`——它讓你對匯出器產生的每個外部檔案都有細緻的控制權。

從此你可以：

- 將此流程整合到 Web 服務中，即時將使用者上傳的 DOCX 轉換為 markdown。  
- 擴充回呼，以符合 CMS 命名慣例的方式重新命名檔案。  
- 結合其他 Aspose.Words 功能，例如 `ExportImagesAsBase64`，實現內嵌圖片的 markdown。

試著跑跑看，依需求調整資料夾邏輯，讓你的 markdown 輸出在文件管線中發光發熱。

--- 

![如何儲存 markdown 範例](/assets/how-to-save-markdown.png "如何儲存 markdown 範例")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}