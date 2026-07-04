---
category: general
date: 2026-05-29
description: 使用 Aspose.Words 將 docx 儲存為 Markdown，並學習在單一工作流程中從 docx 中提取圖片。一步一步的程式碼與技巧。
draft: false
keywords:
- save docx as markdown
- extract images from docx
- convert word to markdown
- convert docx to markdown
- how to extract images
language: zh-hant
og_description: 使用 Aspose.Words 將 docx 另存為 markdown。了解在將 Word 轉換為 markdown 時如何從 docx
  中提取圖片，並附上完整程式碼。
og_title: 將 docx 另存為 markdown – 完整教學與圖片提取
schemas:
- author: Aspose
  dateModified: '2026-05-29'
  description: Save docx as markdown using Aspose.Words and learn how to extract images
    from docx in a single workflow. Step‑by‑step code and tips.
  headline: Save docx as markdown – Complete Guide with Image Extraction
  type: TechArticle
- description: Save docx as markdown using Aspose.Words and learn how to extract images
    from docx in a single workflow. Step‑by‑step code and tips.
  name: Save docx as markdown – Complete Guide with Image Extraction
  steps:
  - name: – Load the source document
    text: First we need a `Document` object that points at the Word file we want to
      transform.
  - name: – Define a callback that extracts images from docx
    text: The magic lives in `IResourceSavingCallback`. Aspose.Words calls `ResourceSaving`
      for every external resource (images, fonts, etc.) it needs to write out. By
      providing our own implementation we gain total control over the file name, folder,
      and even the stream used.
  - name: – Wire the callback into Markdown save options
    text: Now we create a `MarkdownSaveOptions` instance and assign our custom saver.
  - name: – Save the document as markdown
    text: Finally, we ask Aspose.Words to write out the markdown file. The images
      are saved automatically by the callback we just hooked.
  type: HowTo
tags:
- Aspose.Words
- C#
- Document Conversion
title: 將 docx 另存為 markdown – 完整指南（含圖片提取）
url: /zh-hant/net/programming-with-markdownsaveoptions/save-docx-as-markdown-complete-guide-with-image-extraction/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 將 docx 儲存為 markdown – 完整指南與圖片提取

有沒有想過如何 **save docx as markdown** 而不遺失藏在 Word 檔案中的圖片？你並不是唯一有此疑問的人。許多開發者在嘗試將富文字文件轉換成純淨的 markdown 時，常會碰到斷裂的圖片連結。  

在本教學中，我們將逐步說明一個實用的解決方案，不僅能 **convert docx to markdown**，還能自動 **extract images from docx**。完成後，你將擁有一段可直接執行的 C# 程式碼片段、一些最佳實踐技巧，以及對執行程式時會發生什麼的清晰概念。

## 你將學到什麼

- 設定 Aspose.Words for .NET 以處理 Word‑to‑markdown 轉換。  
- 實作自訂的 `IResourceSavingCallback`，將每個內嵌圖片儲存至你指定的資料夾。  
- 了解為何此回呼很重要，以及它如何在產生的 markdown 中保持圖片參照完整。  
- 查看完整、可執行的範例以及你將得到的精確 markdown 輸出。  

**Prerequisites** – 你需要 .NET 6（或任何較新的 .NET 版本）、Visual Studio 2022（或 VS Code），以及有效的 Aspose.Words for .NET 授權（免費試用版可用於測試）。不需要其他第三方函式庫。

---

## 使用 Aspose.Words 將 docx 儲存為 markdown 的方法

以下是我們將遵循的高階流程：

1. 載入包含圖片的來源 `.docx` 檔案。  
2. 建立一個回呼類別，決定每個提取的圖片應寫入哪個位置。  
3. 將回呼插入 `MarkdownSaveOptions`。  
4. 儲存文件 – markdown 會寫入磁碟，圖片則存放於你指定的資料夾。  

每個步驟都會詳細說明，程式碼緊跟說明之後顯示。

### 步驟 1 – 載入來源文件

首先，我們需要一個指向欲轉換之 Word 檔案的 `Document` 物件。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// Load the source .docx that contains images.
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Why this matters:** Aspose.Words 會解析 DOCX 套件，建立內部物件模型，並讓每個段落、表格與圖片皆可存取。若檔案無法載入，後續的流程將不會執行。

### 步驟 2 – 定義一個從 docx 提取圖片的回呼

魔法就藏在 `IResourceSavingCallback` 中。Aspose.Words 會對每個需要寫出的外部資源（圖片、字型等）呼叫 `ResourceSaving`。透過提供自訂實作，我們即可完全掌控檔名、資料夾，甚至使用的串流。

```csharp
// Step 2: Define a callback that stores each extracted image in a sub‑folder
// and gives it a unique name.
class MyResourceSaver : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Create (or reuse) a folder for the images.
        string folder = "YOUR_DIRECTORY/markdown_images";
        Directory.CreateDirectory(folder);

        // Build a new file name like "img_0.png", "img_1.jpg", etc.
        string newName = Path.Combine(folder,
            $"img_{args.Index}{Path.GetExtension(args.ResourceFileName)}");

        // Tell Aspose.Words where to write the image.
        args.ResourceFileName = newName;
        args.Stream = new FileStream(newName, FileMode.Create, FileAccess.Write);

        // Allow the default saving process to continue.
        args.Cancel = false;
    }
}
```

> **Pro tip:** `args.Index` 為零基索引，即使兩張圖片共享相同的原始檔名，也能保證唯一性。這可避免在多次執行轉換時出現令人頭痛的「duplicate file name」錯誤。

### 步驟 3 – 將回呼接入 Markdown 儲存選項

現在，我們建立 `MarkdownSaveOptions` 實例，並指派自訂的 saver。

```csharp
// Step 3: Configure Markdown save options to use the custom resource saver.
MarkdownSaveOptions opts = new MarkdownSaveOptions
{
    ResourceSavingCallback = new MyResourceSaver()
};
```

> **Why this is essential:** 若未使用回呼，Aspose.Words 會根據預設設定將圖片以 base‑64 字串嵌入 markdown，或直接省略。自訂回呼可強制使用乾淨的檔案參照，適用於任何靜態網站產生器。

### 步驟 4 – 將文件儲存為 markdown

最後，我們請 Aspose.Words 輸出 markdown 檔案。圖片會由剛剛掛接的回呼自動儲存。

```csharp
// Step 4: Save the document as Markdown; images will be written to the folder above.
doc.Save("YOUR_DIRECTORY/output.md", opts);
```

執行完程式碼後，你會看到：

- `output.md` – 原始 Word 檔案的 markdown 表示。  
- `markdown_images/` – 一個資料夾，內含 `img_0.png`、`img_1.jpg`… 等每張 DOCX 中的圖片。  

#### 預期的 markdown 片段

```markdown
# Sample Title

Here is some introductory text.

![Image 1](markdown_images/img_0.png)

More text after the picture.
```

圖片連結指向步驟 2 中儲存的檔案，因此任何 markdown 檢視器都會正確顯示圖片。

---

## 在轉換為 markdown 時從 docx 提取圖片

如果你的唯一目標是 **how to extract images** 從 Word 文件，你可以重複使用相同的回呼，甚至不儲存 markdown。只要呼叫 `doc.Save("dummy.md", opts)` 或使用 `doc.GetChildNodes(NodeType.Shape, true)` 列舉圖片即可。回呼會對每張圖片觸發，讓你自行決定儲存位置。

```csharp
// Example: extract images only – we still need a save call to trigger the callback.
doc.Save("YOUR_DIRECTORY/placeholder.md", opts);
```

> **Note:** 抽取完成後，佔位的 markdown 檔案可刪除；回呼已將圖片寫入磁碟。

---

## 使用自訂圖片處理將 Word 轉換為 markdown

關鍵字 **convert word to markdown** 常與「preserve formatting」一起搜尋。Aspose.Words 在保留標題、清單、表格與程式碼區塊方面表現良好。唯一需要留意的是圖片縮放。預設情況下，產生的 markdown 會使用原始圖片尺寸。若需要縮圖，可在寫入前於回呼中調整圖片大小（例如使用 `System.Drawing` 或 `ImageSharp`）。

```csharp
// Inside ResourceSaving, you could resize before saving:
using (var original = Image.Load(args.Stream))
{
    var thumbnail = original.Clone(ctx => ctx.Resize(new ResizeOptions
    {
        Size = new Size(300, 0),
        Mode = ResizeMode.Max
    }));
    thumbnail.Save(newName);
}
```

（上方程式碼片段使用 ImageSharp – 若走此路線需自行加入 NuGet 套件。）

---

## 轉換 docx 為 markdown 時的常見陷阱

| 問題 | 發生原因 | 避免方法 |
|---------|----------------|-----------------|
| 圖片變成 **base64** 字串 | 未設定預設的 `ResourceSavingCallback` | 始終提供自訂的 `IResourceSavingCallback` |
| 搬移 markdown 檔案後連結失效 | 相對路徑指向已不存在的資料夾 | 將 `markdown_images` 資料夾保留在 `.md` 檔案旁，或在 `MarkdownSaveOptions.ImageFolder` 中調整路徑 |
| 圖片名稱重複 | 兩張圖片共享相同的原始名稱 | 使用 `args.Index`（如同本範例）或在檔名中使用 GUID |
| 大型文件導致記憶體不足 | 儲存大型圖片時未使用串流 | 使用 `args.Stream = new FileStream(..., FileMode.Create, FileAccess.Write, FileShare.None, 4096, FileOptions.SequentialScan)` 以有效串流 |

---

## 如何提取圖片 – 進階情境

有時你需要 **without** 任何 markdown 的圖片，可能是要供機器學習模型使用。在此情況下，你可以：

1. 設定 `opts.SaveFormat = SaveFormat.Png`（或任何圖片格式）以強制僅輸出圖片。  
2. 或是重複使用相同的 `MyResourceSaver`，但呼叫 `doc.Save("dummy.docx", SaveFormat.Docx)` 只為觸發回呼。  

兩種方式皆可重複使用相同的邏輯，讓程式碼保持 DRY（Don't Repeat Yourself）。

---

## 完整、可執行範例

以下是完整程式碼，你可以直接複製貼上到 Console 應用程式中。將 `YOUR_DIRECTORY` 替換為你機器上存在的絕對或相對路徑。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

namespace DocxToMarkdownDemo
{
    // Step 2 – custom callback that saves each image.
    class MyResourceSaver : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            string folder = "YOUR_DIRECTORY/markdown_images";
            Directory.CreateDirectory(folder);

            string newName = Path.Combine(folder,
                $"img_{args.Index}{Path.GetExtension(args.ResourceFileName)}");

            args.ResourceFileName = newName;
            args.Stream = new FileStream(newName, FileMode.Create, FileAccess.Write);
            args.Cancel = false;
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // Step 1 – load the .docx.
            Document doc = new Document("YOUR_DIRECTORY/input.docx");

            // Step 3 – set up save options with our callback.
            MarkdownSaveOptions opts = new MarkdownSaveOptions
            {
                ResourceSavingCallback = new MyResourceSaver()
            };

            // Step 4 – save as markdown; images will be extracted automatically.
            doc.Save("YOUR_DIRECTORY/output.md", opts);

            System.Console.WriteLine("Conversion complete! Check output.md and the markdown_images folder.");
        }
    }
}
```

**執行後應看到的結果：**  

- `output.md` 包含如 `![Image](markdown_images/img_0.png)` 的 markdown 文字與圖片連結。  
- 一個 `markdown_images` 資料夾，內有每張內嵌圖片的檔案。

---

## 結論

現在你已掌握完整的步驟，能在 **save docx as markdown** 的同時乾淨地 **extract images from docx**。關鍵在於 `IResourceSavingCallback`，它讓你完全掌控每張圖片的儲存位置與方式。  

接下來，你可以：

- 微調回呼，以有意義的標題（例如根據 alt‑text）重新命名檔案。  
- 加入後處理，將 markdown 轉換為靜態 HTML  

## 接下來該學什麼？

- [如何在轉換 DOCX 時於 Markdown 中嵌入圖片](/words/english/java/document-conversion-and-export/how-to-embed-images-in-markdown-when-converting-docx/)
- [儲存 Word 圖片 – 使用 Aspose 將 Word 轉換為 Markdown](/words/english/net/programming-with-markdownsaveoptions/save-word-images-convert-word-to-markdown-with-aspose/)
- [如何在將 DOCX 轉換為 Markdown 時重新命名圖片](/words/english/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}