---
category: general
date: 2026-08-14
description: 如何使用 Aspose.Words 快速加入 SDT。學習在 .docx 檔案中建立 Word 佔位符並插入純文字控制項。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add sdt
- create word placeholder
- insert plain text control
- Aspose.Words SDT
- C# Word automation
language: zh-hant
lastmod: 2026-08-14
og_description: 如何在 C# 中使用 Aspose.Words 新增 SDT。請參考本教學，建立 Word 佔位符並插入純文字控制項，以製作動態文件。
og_image_alt: Screenshot of a Word document showing a plain‑text Structured Document
  Tag placeholder
og_title: 如何在 C# 中加入 SDT – 步驟式 Word 佔位符指南
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add SDT quickly with Aspose.Words. Learn to create word placeholder
    and insert plain text control in a .docx file.
  headline: How to add SDT in C# – complete guide for Word placeholders
  type: TechArticle
tags:
- Word
- C#
- Aspose.Words
- SDT
- Document Automation
title: 如何在 C# 中加入 SDT – Word 佔位符完整指南
url: /zh-hant/java/using-document-elements/how-to-add-sdt-in-c-complete-guide-for-word-placeholders/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中加入 SDT – Word 佔位符完整指南

如果您需要在 Word 檔案中 **how to add sdt**，本教學將示範使用 Aspose.Words for .NET 的完整步驟。完成本指南後，您將能夠 **create word placeholder** 標籤，讓最終使用者直接在文件中輸入文字，並且了解如何可靠地 **insert plain text control**。

使用結構化文件標記 (Structured Document Tags, SDTs) 可免除手動表單欄位的需求，並提供一種乾淨且程式化的方式來建立動態合約、報告或信函。以下範例涵蓋從專案設定到儲存最終 .docx 檔案的全部流程，您只要複製貼上程式碼即可在自己的解決方案中使用，且不會遺漏任何相依性。

## 前置條件

在開始之前，請確保您已具備：

- .NET 6.0 或更新版本（此程式碼亦相容 .NET Framework 4.6+）
- Visual Studio 2022 或您偏好的 C# IDE
- Aspose.Words for .NET 授權（測試時可使用免費暫時授權）
- 基本的 C# 語法與 SDT 概念了解

> **專業提示：** 若您計畫發佈產生的文件，請嵌入授權檔案以避免出現評估水印。

## 第一步：設定專案並匯入 Aspose.Words

建立一個新的主控台應用程式，並加入 Aspose.Words NuGet 套件：

```bash
dotnet new console -n SdtDemo
cd SdtDemo
dotnet add package Aspose.Words
```

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
```

這些 `using` 指令讓您可以存取 `Document`、`DocumentBuilder` 與 `StructuredDocumentTag` 類別，這些類別是執行 **insert plain text control** 所必需的。

## 第二步：初始化文件與建構器

第一段程式碼會建立一個空的 Word 文件，並產生一個 `DocumentBuilder`，讓您可以向其中寫入內容。

```csharp
// Step 2: Create a new document and a builder to edit it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` 的運作方式類似游標；之後的每一次呼叫都會在目前位置加入內容。初始化文件是每個 **how to add sdt** 情境的基礎，因為 SDT 必須屬於一個已存在的 `Document` 實例。

## 第三步：插入純文字 Structured Document Tag (SDT)

現在我們 **insert plain text control**，它會作為使用者可以輸入姓名、日期或任何自訂值的佔位符。

```csharp
// Step 3: Insert a plain‑text Structured Document Tag (SDT)
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
        StructuredDocumentTagType.PlainText, SdtAppearanceTags.Default);
```

- `StructuredDocumentTagType.PlainText` 告訴 Aspose.Words 建立一個簡單的文字欄位。
- `SdtAppearanceTags.Default` 為標記套用 Word 的標準視覺樣式（在 Word 中開啟時會顯示陰影方框）。

## 第四步：為 SDT 設定標題與佔位文字

具備良好命名的 SDT 能讓文件對最終使用者自說自話。此處我們 **create word placeholder** 中繼資料，並設定欄位內顯示的提示文字。

```csharp
// Step 4: Give the SDT a meaningful title and placeholder text
plainTextTag.Title = "CustomerName";
plainTextTag.PlaceholderName = "Enter name here";
```

- `Title` 為內部識別碼，您日後可在程式中提取或更新其值時使用。
- `PlaceholderName` 為 Word 中顯示的淡灰色提示，告訴使用者應輸入什麼內容。

## 第五步：加入前後文內容

文件很少只包含單一 SDT。通常需要在佔位符前後加入一般段落。使用建構器的 `WriteLine` 方法加入靜態文字。

```csharp
// Step 5: Add regular content before and after the SDT
builder.Writeln("Dear ");
builder.InsertNode(plainTextTag);   // Re‑insert the tag at the current cursor position
builder.Writeln(",");
builder.Writeln("After the SDT");
```

呼叫 `InsertNode` 會將先前建立的 SDT 正確放置於所需位置，並保留前後文字的流向。

## 第六步：將文件儲存為 .docx 檔案

最後，將文件寫入磁碟。路徑可以是絕對路徑，也可以是相對於專案資料夾的路徑。

```csharp
// Step 6: Save the document to a file
string outputPath = Path.Combine(Environment.CurrentDirectory, "SDT.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

在 Microsoft Word 中開啟 `SDT.docx` 時，會看到一個灰色佔位符，顯示 **Enter name here**。使用者點擊欄位後即可輸入值，文件在再次儲存時會保留該值。

## 完整、可執行範例

將所有片段組合起來，即可得到一個自包含的程式，直接執行即可：

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a plain‑text SDT
        StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
            StructuredDocumentTagType.PlainText, SdtAppearanceTags.Default);

        // Configure the SDT
        plainTextTag.Title = "CustomerName";
        plainTextTag.PlaceholderName = "Enter name here";

        // Add surrounding content
        builder.Writeln("Dear ");
        builder.InsertNode(plainTextTag);
        builder.Writeln(",");
        builder.Writeln("After the SDT");

        // Save the file
        string outputPath = Path.Combine(Environment.CurrentDirectory, "SDT.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**預期輸出**（執行程式時）：

```
Document saved to C:\YourProject\bin\Debug\net6.0\SDT.docx
```

開啟產生的 `SDT.docx` 會看到：

```
Dear [Enter name here],
After the SDT
```

方括號內的文字即為 **insert plain text control** 佔位符，使用者可以自行取代。

## 常見變形與邊緣情況

| 情況 | 如何調整程式碼 |
|-----------|-----------------------|
| **多個佔位符** | 重複呼叫 `InsertStructuredDocumentTag`，並為每個標籤指定唯一的 `Title`。 |
| **富文字 SDT** | 使用 `StructuredDocumentTagType.RichText` 取代 `PlainText`。 |
| **鎖定佔位符** | 設定 `plainTextTag.LockContentControl = true;` 以防止使用者刪除該欄位。 |
| **預先填入值** | 在儲存前指派 `plainTextTag.Text = "John Doe";`。 |
| **條件外觀** | 使用 `plainTextTag.SdtType = StructuredDocumentTagType.CheckBox;` 以建立核取方塊控制項。 |

這些變形讓您 **create word placeholder** 結構，幾乎能符合任何表單式的情境。

## 疑難排解技巧

- **Placeholder not visible** – 確認您是使用 Microsoft Word（或相容的檢視器）開啟檔案。部分輕量編輯器會隱藏 SDT。
- **License warning** – 若看到評估水印，請確認授權檔案已正確載入 (`License license = new License(); license.SetLicense("Aspose.Words.lic");`)。
- **Incorrect cursor position** – 插入 SDT 後，建構器的游標會停留在*標記之後*。若需在標記內加入文字，請在寫入前使用 `builder.MoveTo(plainTextTag);`。

## 結論

您現在已掌握如何使用 Aspose.Words for .NET **how to add sdt** 到 Word 文件、如何 **create word placeholder** 標籤，以及如何 **insert plain text control** 讓使用者直接在 Word 中編輯。完整範例示範了初始化、標記插入、設定、前後文加入與儲存——全部於單一可執行程式中完成。

接下來，您可以探索相關主題，例如 **insert rich text control**、**populate SDTs from a database**，或 **convert the final document to PDF**。所有這些皆建立在本指南所闡述的基礎上，讓您能自信地擴充文件自動化流程。

祝開發順利，歡迎隨意嘗試不同的 SDT 類型，以符合您的文件自動化需求！

## 接下來該學什麼？

以下教學與本指南所示技術緊密相關，並提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在自己的專案中探索替代實作方式。

- [如何使用 DocumentBuilder 在 Aspose.Words for Java 中建立表單欄位並加入內容](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [如何在 Aspose.Words for Java 中的唯讀文件建立可編輯範圍](/words/english/java/security-protection/editable-ranges-aspose-words-java/)
- [在 Aspose.Words for Java 中新增書籤 – 插入、更新、刪除](/words/english/java/content-management/aspose-words-java-manage-bookmarks/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}