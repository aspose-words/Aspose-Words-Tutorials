---
category: general
date: 2026-08-04
description: 使用 Aspose.Words 於 C# 更改註腳分隔線 – 學習如何編輯註腳分隔線及更改 Word 文件中的尾註分隔線。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote separator
- edit footnote separator
- how to change footnote separator
- change endnote separator
language: zh-hant
lastmod: 2026-08-04
og_description: 在 C# 中使用 Aspose.Words 更改腳註分隔線。本指南將向您展示如何編輯腳註分隔線、自訂尾註分隔線，並儲存已更新的文件。
og_image_alt: Screenshot showing the changed footnote separator in a Word document
og_title: 更改 C# 中的腳註分隔符 – 完整 Aspose.Words 指南
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Change footnote separator in C# using Aspose.Words – learn how to edit
    footnote separator and change endnote separator in Word documents.
  headline: Change footnote separator in C# using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
- Document processing
title: 使用 Aspose.Words 在 C# 中更改腳註分隔符
url: /zh-hant/net/working-with-footnote-and-endnote/change-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 中使用 Aspose.Words 更改腳註分隔線

如果您需要在 Word 文件中**更改腳註分隔線**，本教學將以 Aspose.Words for .NET 為您示範完整步驟。無論是想將預設的線條換成符號，或是為尾註分隔線套用不同樣式，以下程式碼皆涵蓋整個工作流程。

您還會學會如何**編輯腳註分隔線**以及相關的**更改尾註分隔線**操作，讓同一文件的腳註與尾註保持一致的樣式。無需任何外部工具——只需幾行 C# 程式碼。

## 您將達成的目標

* 載入包含腳註與尾註的現有 *.docx* 檔案。  
* 取得腳註、腳註續頁以及尾註的分隔節點。  
* 替換分隔字元（例如，將預設線條改為星號 *）。  
* 儲存修改後的文件，且不遺失其他內容。  

本教學假設您具備 C# 基礎知識，且已安裝 **Aspose.Words** NuGet 套件（版本 24.9 或更新）。

---

## 前置條件

| Requirement | Reason |
|-------------|--------|
| .NET 6.0+ or .NET Framework 4.7.2+ | Aspose.Words 所需的執行環境 |
| Aspose.Words for .NET library | 提供 `Document` 與 `FootnoteOptions` API |
| An input Word file (`input.docx`) with at least one footnote or endnote | 示範分隔線變更 |

You can add Aspose.Words to your project with the following CLI command:

```bash
dotnet add package Aspose.Words --version 24.9.0
```

---

## 步驟 1：載入包含腳註的文件

第一步是將來源檔案讀入 `Document` 物件。此物件在記憶體中代表整個 Word 檔案，並讓您存取其所有節點。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

// Load the .docx file that contains footnotes and endnotes.
Document document = new Document(@"C:\Docs\input.docx");
```

**為什麼重要**：載入文件是任何操作的入口點。如果找不到檔案，Aspose.Words 會拋出 `FileNotFoundException`，因此在繼續之前請確認路徑正確。

---

## 步驟 2：存取腳註與尾註的分隔節點

`Document.FootnoteOptions` 會公開三個分隔節點：

* `Separator` – 首頁腳註集合之後出現的線條。  
* `ContinuationSeparator` – 當腳註延續至下一頁時使用的線條。  
* `EndnoteSeparator` – 將正文與尾註清單分開的線條。

您會以通用的 `Node` 物件取得這些節點，然後轉型為 `Run` 以修改文字。

```csharp
// Retrieve the three separator nodes.
Node footnoteSeparator = document.FootnoteOptions.Separator;
Node footnoteContinuation = document.FootnoteOptions.ContinuationSeparator;
Node endnoteSeparator = document.FootnoteOptions.EndnoteSeparator;
```

**為什麼重要**：這些節點是唯一存放視覺分隔字元的地方。變更其他節點（例如普通段落）不會影響腳註格式。

---

## 步驟 3：變更腳註分隔字元

最常見的需求是將預設線條換成符號，例如星號 (`*`)。由於分隔線以 `Run` 形式儲存，您可以安全地修改其 `Text` 屬性。

```csharp
// Change the primary footnote separator to an asterisk.
if (footnoteSeparator is Run footnoteRun)
{
    footnoteRun.Text = "*";
}

// Optionally, change the continuation separator as well.
if (footnoteContinuation is Run continuationRun)
{
    continuationRun.Text = "*";
}
```

**為什麼重要**：直接編輯 `Run.Text` 會在最終文件中更新視覺呈現，且不會影響其他腳註內容。相同的做法亦可套用任何字串，包括 Unicode 符號。

---

## 步驟 4：變更尾註分隔線（可選）

如果您同時需要**變更尾註分隔線**，流程與腳註相同。將 `endnoteSeparator` 的文字替換為您想要的字元即可。

```csharp
// Change the endnote separator to a dash.
if (endnoteSeparator is Run endnoteRun)
{
    endnoteRun.Text = "-";
}
```

**為什麼重要**：尾註的樣式通常與腳註不同。提供獨立的分隔線可讓您依照文件設計指南維持視覺一致性。

---

## 步驟 5：儲存修改後的文件

完成所有修改後，使用 `Document.Save` 來寫入變更。您可以覆寫原始檔案或儲存至新位置。

```csharp
// Save the updated document.
document.Save(@"C:\Docs\ModifiedSeparators.docx");
```

**為什麼重要**：`Save` 會將記憶體中的表示寫入磁碟，保持其他所有元素（樣式、圖片、表格）不變。

---

## 完整、可執行範例

將所有步驟組合起來，以下是一個獨立的 Console 應用程式，示範完整工作流程：

```csharp
using System;
using Aspose.Words;

namespace FootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source document.
            string inputPath = @"C:\Docs\input.docx";
            Document doc = new Document(inputPath);

            // 2️⃣ Access separator nodes.
            Node footnoteSep = doc.FootnoteOptions.Separator;
            Node footnoteCont = doc.FootnoteOptions.ContinuationSeparator;
            Node endnoteSep = doc.FootnoteOptions.EndnoteSeparator;

            // 3️⃣ Change footnote separator to an asterisk.
            if (footnoteSep is Run footnoteRun)
                footnoteRun.Text = "*";

            // Optional: also change the continuation separator.
            if (footnoteCont is Run contRun)
                contRun.Text = "*";

            // 4️⃣ Change endnote separator to a dash.
            if (endnoteSep is Run endnoteRun)
                endnoteRun.Text = "-";

            // 5️⃣ Save the result.
            string outputPath = @"C:\Docs\ModifiedSeparators.docx";
            doc.Save(outputPath);

            Console.WriteLine("Document saved to " + outputPath);
        }
    }
}
```

**預期結果**：在 Microsoft Word 中開啟 *ModifiedSeparators.docx*。第一頁腳註底部的分隔線將變為單一星號 (`*`)。若文件包含尾註，分隔正文與尾註清單的線條將顯示為破折號 (`-`)。其他所有內容（文字、圖片、表格）保持不變。

---

## 常見問題與邊緣案例處理

| Question | Answer |
|----------|--------|
| **如果文件沒有腳註怎麼辦？** | `FootnoteOptions.Separator` 仍會回傳一個 `Run` 節點，但其文字可能為空。程式碼在修改前會安全檢查節點類型。 |
| **我可以使用多字元字串（例如 "***"）嗎？** | 可以。`Run.Text` 屬性接受任何字串，包括 Unicode 字元。 |
| **變更分隔線會影響現有的腳註編號嗎？** | 不會。分隔線與編號機制相互獨立。 |
| **需要釋放 `Document` 物件嗎？** | `Document` 透過 `Node` 隱式實作 `IDisposable`。在短暫的 Console 應用程式中可選擇性使用，但對於長時間執行的服務，建議以 `using` 區塊包住。 |
| **在 .NET Core 與 .NET Framework 上的運作有何差異？** | API 在各執行環境中完全相同；唯一需要注意的是目標框架版本必須受到 Aspose.Words 套件支援。 |

**小技巧**：如果需要為不同章節套用不同的分隔線，您可以遍歷 `doc.GetChildNodes(NodeType.Footnote, true)`，並逐一調整每個腳註的 `Separator` 屬性。此方式較進階，但對於複雜文件相當實用。

---

## 結論

您現在已掌握如何使用 Aspose.Words for C# 在 Word 檔案中**更改腳註分隔線**與**更改尾註分隔線**。本指南說明了載入文件、取得相關分隔節點、修改其文字以及儲存結果的完整流程——全部於單一獨立程式中完成。

接下來您可以探索相關主題，例如**編輯腳註分隔線樣式**、自訂腳註編號，或根據頁面版面套用條件格式化。同樣的模式（取得節點、轉型為 `Run`、修改 `Text`）可應用於許多其他 Word 處理情境。

祝開發順利，歡迎嘗試不同符號，甚至將圖片嵌入作為分隔線，打造獨一無二的文件版面！

## 接下來該學什麼？

以下教學涵蓋與本指南緊密相關的主題，建立在此處示範的技巧之上。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在自己的專案中探索替代實作方式。

- [使用腳註與尾註的文字處理](/words/english/net/working-with-footnote-and-endnote/)
- [取得 Word 文件段落樣式分隔線](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [在 Word 中插入文件樣式分隔線](/words/english/net/programming-with-styles-and-themes/insert-style-separator/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}