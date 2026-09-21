---
category: general
date: 2026-09-21
description: 學習如何使用 C# 產生文件範本、填充 Word 範本及取代 DOCX 檔案中的佔位符——一步一步的指南。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- generate document template
- populate word template
- how to replace placeholder
- fill docx template
- replace text docx
language: zh-hant
lastmod: 2026-09-21
og_description: 在 C# 中透過填充 Word 範本、取代佔位符，產生文件範本並儲存已填寫的 DOCX 檔案。請遵循本完整指南。
og_image_alt: Screenshot of a C# program generating and filling a DOCX template
og_title: 在 C# 中產生文件範本 – 用資料填入 DOCX 檔案
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to generate document template, populate word template and
    replace placeholders in a DOCX file using C# – step‑by‑step guide.
  headline: How to generate document template and fill it with data in C#
  type: TechArticle
tags:
- C#
- DOCX
- template processing
title: 如何在 C# 中產生文件範本並填入資料
url: /zh-hant/net/find-and-replace-text/how-to-generate-document-template-and-fill-it-with-data-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中產生文件範本並填入資料

如果您需要 **generate document template** 檔案，且這些檔案可在發票、合約或報告中重複使用，本指南會精確說明如何操作。您將學會 **populate word template** 中的佔位符，將其替換為真實值，最後以程式方式 **fill docx template** 檔案。

建立可重複使用的範本可避免手動複製貼上，並確保所有產生的文件保持一致。以下步驟適用於任何包含簡單佔位符（例如 `{{Name}}`）的 `.docx` 檔案。

## 前置條件

* 已安裝 .NET 6.0 SDK 或更新版本  
* Visual Studio 2022（或您偏好的任何 IDE）  
* **Aspose.Words for .NET** NuGet 套件 – 它提供範例中使用的 `Document` 類別  

您可以使用以下指令加入套件：

```bash
dotnet add package Aspose.Words
```

## 步驟 1：準備 Word 範本

建立一個 Word 文件（`Template.docx`），其中包含動態資料應出現的佔位符。常見的慣例是使用雙大括號：

```
Dear {{Name}},

Your order #{{OrderId}} has been shipped on {{ShipDate}}.
```

將檔案儲存於程式碼可參考的資料夾，例如 `C:\Docs\Template.docx`。

## 步驟 2：載入範本文件

第一個程式化動作是將範本載入記憶體。`Document` 建構子會讀取檔案並建立可供操作的物件模型。

```csharp
using System;
using Aspose.Words;

class Program
{
    static void Main()
    {
        // Load the template document from disk
        string templatePath = @"C:\Docs\Template.docx";
        Document doc = new Document(templatePath);
```

**Why this matters:** 載入檔案會每次產生乾淨的副本，確保原始範本在未來的執行中保持未被修改。

## 步驟 3：以實際資料取代佔位符

Aspose.Words 提供簡易的 `Range.Replace` 方法，可掃描文件中指定的字串並進行替換。將此呼叫包裝在輔助方法中，以保持主要流程的整潔。

```csharp
        // Helper to replace a single placeholder
        void ReplacePlaceholder(string placeholder, string value)
        {
            // The placeholder includes the curly braces exactly as they appear in the template
            doc.Range.Replace(placeholder, value, new FindReplaceOptions());
        }

        // Populate the template with real values
        ReplacePlaceholder("{{Name}}", "John Doe");
        ReplacePlaceholder("{{OrderId}}", "A12345");
        ReplacePlaceholder("{{ShipDate}}", DateTime.Today.ToString("MMMM d, yyyy"));
```

**How it works:** `Range.Replace` 會遍歷每個段落、表格儲存格、頁首與頁尾，確保所有出現的代符皆被更新。這是 **how to replace placeholder**（取代佔位符）文字於 DOCX 檔案中最可靠的方式。

### 處理多次出現與缺失的代符

* 若佔位符出現多於一次，`Replace` 會自動更新所有實例。  
* 若佔位符不存在，該方法僅不執行任何動作——不會拋出例外。  
* 對於大型文件，可在完成所有替換之前停用 `doc.UpdateFields()` 以提升效能。

## 步驟 4：儲存已填寫的文件

當所有佔位符皆已替換後，將結果寫入新檔案。將輸出與原始範本分開，可保留原範本以供未來使用。

```csharp
        // Save the filled document to a new file
        string outputPath = @"C:\Docs\FilledTemplate.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Result:** `FilledTemplate.docx` 現在包含個人化內容：

```
Dear John Doe,

Your order #A12345 has been shipped on September 21, 2026.
```

## 步驟 5：驗證輸出（可選）

若您想以程式方式確認替換是否成功，可重新讀取已儲存的檔案並搜尋預期的值：

```csharp
        Document verifyDoc = new Document(outputPath);
        bool nameReplaced = verifyDoc.Range.Text.Contains("John Doe");
        Console.WriteLine($"Name replacement successful: {nameReplaced}");
```

執行驗證步驟時，若佔位符正確替換，會印出 `true`。

## 常見陷阱與最佳實踐提示

| Issue | Why it happens | Recommended fix |
|-------|----------------|-----------------|
| **Placeholders contain extra spaces** | `"{{ Name }}"` 不符合 `"{{Name}}"`。 | 請確保佔位符代符沒有空白，或在替換前兩側皆執行 trim。 |
| **Word adds hidden formatting** | Word 可能將佔位符分散在多個 run 中，導致 `Replace` 無法偵測。 | 使用 `Document.Range.Replace`，並將 `FindReplaceOptions` 的 `MatchCase = false` 與 `FindWholeWordsOnly = false` 設定。 |
| **Large documents cause slowdown** | 逐一替換代符會每次觸發完整文件掃描，導致緩慢。 | 在儲存前一次性批次替換，對每個代符呼叫 `Range.Replace`。 |
| **Saving to a read‑only folder** | `doc.Save` 會拋出 `UnauthorizedAccessException`。 | 確認目標目錄具寫入權限，或選擇使用者可寫入的路徑（例如 `%TEMP%`）。 |

## 完整範例程式

以下是完整、獨立的程式，您可以直接複製、貼上並執行。

```csharp
using System;
using Aspose.Words;

class Program
{
    static void Main()
    {
        // Paths – adjust to your environment
        string templatePath = @"C:\Docs\Template.docx";
        string outputPath   = @"C:\Docs\FilledTemplate.docx";

        // 1️⃣ Load the template document
        Document doc = new Document(templatePath);

        // 2️⃣ Replace placeholders
        void Replace(string placeholder, string value) =>
            doc.Range.Replace(placeholder, value, new FindReplaceOptions());

        Replace("{{Name}}", "John Doe");
        Replace("{{OrderId}}", "A12345");
        Replace("{{ShipDate}}", DateTime.Today.ToString("MMMM d, yyyy"));

        // 3️⃣ Save the filled document
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");

        // 4️⃣ (Optional) Verify replacement
        Document verify = new Document(outputPath);
        Console.WriteLine($"Verification – name found: {verify.Range.Text.Contains("John Doe")}");
    }
}
```

**預期的主控台輸出**

```
Document saved to C:\Docs\FilledTemplate.docx
Verification – name found: True
```

在 Microsoft Word 中開啟 `FilledTemplate.docx`，即可看到個人化的文字。

## 結論

您現在已了解如何 **generate document template**、**populate word template**，以及透過 **how to replace placeholder** 代符以真實資料 **fill docx template** 檔案。只要遵循最佳實踐提示，此方法即可處理任意數量的佔位符，且在大型文件中亦能良好擴充。

### 接下來？

* **Dynamic tables**：使用 `DocumentBuilder` 依集合插入列。  
* **Conditional sections**：使用 `IF` 欄位隱藏或顯示範本的部分內容。  
* **PDF export**：呼叫 `doc.Save("output.pdf")` 以產生已填寫文件的 PDF 版本。  

試著運用這些變化，打造功能完整的文件產生引擎，適用於發票、合約或任何可重複的報告。

---

## 接下來該學什麼？

以下教學涵蓋與本指南技術緊密相關的主題。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通其他 API 功能，並在專案中探索替代實作方式。

- [Word 文件 - 尋找與取代文字](/words/english/net/find-and-replace-text/)
- [產生 Word 文件](/words/english/java/word-processing/generate-word-document/)
- [修復損毀的 DOCX – 開啟與載入 Word 文件](/words/english/python-net/document-operations/recover-corrupted-docx-open-load-word-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}