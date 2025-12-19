---
category: general
date: 2025-12-19
description: Markdown 與 LaTeX 方程式指南 – 學習如何將 docx 轉換為 markdown、將方程式匯出為 LaTeX，並使用 Aspose.Words
  在 C# 中將圖片儲存至資料夾且使用唯一名稱。
draft: false
keywords:
- markdown with latex equations
- convert docx to markdown
- save images to folder
- export equations to latex
- generate unique image names
language: zh-hant
og_description: 含 LaTeX 方程式的 Markdown 教學示範如何將 docx 轉換為 Markdown、將方程式匯出為 LaTeX，並為已儲存的圖片產生唯一的檔名。
og_title: 含 LaTeX 方程式的 Markdown – 完整 C# 轉換指南
tags:
- Aspose.Words
- C#
- Markdown
- LaTeX
title: Markdown 與 LaTeX 方程式：將 DOCX 轉換為 Markdown 並匯出圖片
url: /zh-hant/net/programming-with-markdownsaveoptions/markdown-with-latex-equations-convert-docx-to-markdown-and-e/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# markdown 與 latex 方程式：將 DOCX 轉換為 Markdown 並匯出圖片

是否曾需要 **markdown with latex equations**，卻不確定該如何從 Word 檔案中提取？你並不孤單——許多開發者在將文件從 Office 移轉至靜態網站產生器時，都會遇到這個問題。

在本教學中，我們將逐步說明一個完整的端對端解決方案，**converts docx to markdown**、**exports equations to latex**，以及 **saves images to folder**，並使用 **generate unique image names** 邏輯，全部透過 Aspose.Words for .NET 完成。

完成後，你將擁有一個可直接執行的 C# 程式，能產生乾淨的 Markdown 檔案、LaTeX 可用的數學式，以及整齊的圖片目錄——無需手動複製貼上。

## 需要的條件

- .NET 6（或任何較新的 .NET 執行環境）  
- Aspose.Words for .NET 23.10 或更新版本（NuGet 套件 `Aspose.Words`）  
- 一個範例 `input.docx`，內含一般文字、Office Math 物件與少量圖片  
- 你喜歡的 IDE（Visual Studio、Rider 或 VS Code）  

就這樣。沒有額外的函式庫，也不需要繁雜的命令列工具——只有純粹的 C#。

## 步驟 1：安全載入文件（Recovery Mode）

當你處理可能經過多人編輯的檔案時，損毀是一個真實的風險。Aspose.Words 允許你啟用 *RecoveryMode*，讓載入器嘗試修復損壞的部分，而不是拋出例外。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class DocxToMarkdown
{
    static void Main()
    {
        // Load the document with recovery mode – this handles possible corruption.
        var loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
        Document doc = new Document(@"YOUR_DIRECTORY/input.docx", loadOptions);
```

**為什麼這很重要：**  
如果來源檔案包含多餘的 XML 節點或損壞的影像串流，RecoveryMode 仍會提供可用的 `Document` 物件。跳過此步驟可能導致嚴重崩潰，尤其在 CI 流程中你無法掌控每一次上傳時。

> **專業提示：** 在批次處理時，將載入動作包在 `try/catch` 中，並記錄任何 `DocumentCorruptedException` 以供日後檢查。

## 步驟 2：將 DOCX 轉換為含 LaTeX 方程式的 Markdown

現在進入本教學的核心：我們希望得到 **markdown with latex equations**。Aspose.Words 的 `MarkdownSaveOptions` 允許你設定 `OfficeMathExportMode.LaTeX`，將每個 Office Math 物件轉換為以 `$…$` 或 `$$…$$` 包裹的 LaTeX 字串。

```csharp
        // Export Office Math equations to LaTeX while saving as Markdown.
        var markdownMathOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };
        doc.Save(@"YOUR_DIRECTORY/output_math.md", markdownMathOptions);
```

產生的 `output_math.md` 會類似以下內容：

```markdown
Here is an inline equation $E = mc^2$ inside a sentence.

And a displayed equation:

$$
\int_{a}^{b} f(x)\,dx = F(b) - F(a)
$$
```

**為什麼需要這樣做：**  
大多數靜態網站產生器（Hugo、Jekyll、MkDocs）在啟用 MathJax 或 KaTeX 外掛後已能辨識 LaTeX 分隔符。直接匯出為 LaTeX 可避免後續需要使用正則表達式的處理步驟。

### 邊緣情況

- **Complex equations（複雜方程式）：** 即使是非常深層的巢狀結構仍能正確呈現，但若遭遇 `OutOfMemoryException`，可能需要提升 `MathRenderer` 的記憶體上限。  
- **Mixed content（混合內容）：** 若段落同時包含一般文字與方程式，Aspose.Words 會自動將它們分割，保留前後的 markdown。

## 步驟 3：以唯一名稱儲存圖片至資料夾

如果你的 Word 文件包含圖片，你可能希望將它們作為獨立的影像檔案，讓 markdown 能引用。`MarkdownSaveOptions` 上的 `ResourceSavingCallback` 讓你完全掌控每張圖片的寫入方式。

```csharp
        // Customize image handling during Markdown export.
        var markdownImageOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = (resource, stream) =>
            {
                // Generate a unique file name for each image.
                string imageFileName = $"img_{Guid.NewGuid()}.png";
                string imagePath = Path.Combine(@"YOUR_DIRECTORY/Images", imageFileName);

                // Ensure the Images folder exists.
                Directory.CreateDirectory(Path.GetDirectoryName(imagePath)!);

                // Save the image to the file system.
                using var imageFile = File.Create(imagePath);
                resource.Save(imageFile);
            }
        };
        doc.Save(@"YOUR_DIRECTORY/output_images.md", markdownImageOptions);
```

**現在的 markdown 會是這樣：**

```markdown
![Image description](Images/img_3f9c2a1e-7b5d-4c8f-9d6e-2b5c7a9e1f0a.png)
```

**為什麼要產生唯一名稱？**  
如果同一張圖片出現多次，使用原始名稱會導致覆寫。基於 GUID 的名稱可保證每個檔案皆為唯一，這在平行執行轉換工作時特別方便。

### 小技巧與注意事項

- **Performance（能）：** 為每張圖片產生 GUID 的開銷可忽略不計，但若處理數千張圖片，可改用決定性的雜湊（例如影像位元組的 SHA‑256）。  
- **File format（檔案格式）：** `resource.Save` 會以原始格式寫入影像。若需要全部為 PNG，請將 `resource.Save(imageFile);` 替換為 `resource.Save(imageFile, ImageSaveOptions.CreateSaveOptions(SaveFormat.Png));`。

## 步驟 4：匯出含內嵌圖形的 PDF（可選）

有時仍需要相同文件的 PDF 版本，可能是為了法律審查。設定 `ExportFloatingShapesAsInlineTag` 可將浮動物件（如文字方塊）在 PDF 中保留為內嵌標籤，維持版面忠實度。

```csharp
        // Save the document as PDF, exporting floating shapes as inline tags.
        var pdfOptions = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true
        };
        doc.Save(@"YOUR_DIRECTORY/output_shapes.pdf", pdfOptions);
    }
}
```

如果你的工作流程不需要 PDF 輸出，可略過此步驟——省略也不會造成錯誤。

## 完整可執行範例（結合所有步驟）

以下是完整程式碼，你可以直接複製貼上至 console 應用程式。記得將 `YOUR_DIRECTORY` 替換為實際的絕對或相對路徑。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class DocxToMarkdown
{
    static void Main()
    {
        // 1️⃣ Load with recovery mode.
        var loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
        Document doc = new Document(@"YOUR_DIRECTORY/input.docx", loadOptions);

        // 2️⃣ Export markdown with LaTeX equations.
        var markdownMathOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };
        doc.Save(@"YOUR_DIRECTORY/output_math.md", markdownMathOptions);

        // 3️⃣ Save images to a folder, using unique GUID names.
        var markdownImageOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = (resource, stream) =>
            {
                string imageFileName = $"img_{Guid.NewGuid()}.png";
                string imagePath = Path.Combine(@"YOUR_DIRECTORY/Images", imageFileName);
                Directory.CreateDirectory(Path.GetDirectoryName(imagePath)!);
                using var imageFile = File.Create(imagePath);
                resource.Save(imageFile);
            }
        };
        doc.Save(@"YOUR_DIRECTORY/output_images.md", markdownImageOptions);

        // 4️⃣ (Optional) Export PDF with inline shape tags.
        var pdfOptions = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true
        };
        doc.Save(@"YOUR_DIRECTORY/output_shapes.pdf", pdfOptions);
    }
}
```

執行此程式會產生三個檔案：

| 檔案 | 用途 |
|------|---------|
| `output_math.md` | 含 LaTeX‑ready 方程式的 Markdown |
| `output_images.md` | 含指向唯一命名 PNG 圖片連結的 Markdown |
| `output_shapes.pdf` | 保留浮動圖形為內嵌標籤的 PDF 版本（可選） |

## 結論

你現在擁有一條 **markdown with latex equations** 流程，能 **convert docx to markdown**、**export equations to latex**，並 **save images to folder**，同時為每張圖片 **generate unique image names**。此方法完整自給自足，適用於任何現代 .NET 專案，且僅需 Aspose.Words NuGet 套件。

接下來要做什麼？試著將產生的 markdown 放入像 Hugo 這樣的靜態網站產生器，啟用 MathJax，觀賞你的文件從封閉的 Office 格式轉變為美觀、即時上線的網站。需要表格嗎？Aspose.Words 也支援 `MarkdownSaveOptions.ExportTableAsHtml`，讓你保留複雜的版面配置。

If

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}