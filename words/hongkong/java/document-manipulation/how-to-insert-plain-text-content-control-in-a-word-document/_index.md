---
category: general
date: 2026-10-26
description: 學習如何在 C# 中使用 Aspose.Words 插入純文字內容控制項。一步一步的指南，涵蓋 StructuredDocumentTag、標題和標籤
  ID。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert plain text content control
- structured document tag
- Aspose.Words DocumentBuilder
- C# content control
- SDT appearance
language: zh-hant
lastmod: 2026-10-26
og_description: 使用 Aspose.Words 於 C# 插入純文字內容控制項。按照本指南新增標題、標籤 ID，並自訂外觀。
og_image_alt: Screenshot of a Word document showing an inserted plain text content
  control
og_title: 使用 C# 在 Word 中插入純文字內容控制項 – 完整指南
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn to insert plain text content control using Aspose.Words in C#.
    Step‑by‑step guide covering StructuredDocumentTag, titles, and tag IDs.
  headline: How to insert plain text content control in a Word document with C#
  type: TechArticle
- description: Learn to insert plain text content control using Aspose.Words in C#.
    Step‑by‑step guide covering StructuredDocumentTag, titles, and tag IDs.
  name: How to insert plain text content control in a Word document with C#
  steps:
  - name: Initialize the document and builder
    text: '```csharp using System; using Aspose.Words; using Aspose.Words.Markup;'
  - name: Insert the plain‑text content control (SDT)
    text: '```csharp // Insert a plain‑text Structured Document Tag (SDT) with the
      default appearance. StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
      SdtType.PlainText, // The control type – plain text. SdtAppearance.Default);
      // Visual style; Default shows a light gray shading. ```'
  - name: Set a title and a tag identifier
    text: '```csharp // Give the SDT a friendly title that appears in the Content
      Controls pane. sdt.Title = "MyTag";'
  - name: Variations you might need
    text: '| Scenario | Code change | |----------|-------------| | **No visual shading**
      (border‑less) | Use `SdtAppearance.Hidden` instead of `Default`. | | **Read‑only
      field** | After insertion, set `sdt.LockContentControl = true`. | | **Pre‑populate
      with data** | Set `sdt.Text = "John Doe";` after creating '
  - name: What’s next?
    text: '- Explore other SDT types such as `RichText` or `ComboBox` for dropdowns.
      - Combine multiple content controls inside tables or repeat them using `RepeatingSection`.
      - Use `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` to read or modify
      control values programmatically.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: 如何使用 C# 在 Word 文件中插入純文字內容控制項
url: /zh-hant/java/document-manipulation/how-to-insert-plain-text-content-control-in-a-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 文件中使用 C# 插入純文字內容控制項

如果您需要在 Word 檔案中 **插入純文字內容控制項**，本教學將會示範如何使用 Aspose.Words for .NET 完成。無論您是建立文件產生服務或自動化表單建立，以下步驟都能讓您加入可重複使用、可編輯的區域，讓最終使用者填寫。

您將學會如何建立 `Document`、使用 `DocumentBuilder` 放置純文字結構化文件標記 (SDT)、設定友好的標題，並指派唯一的標籤識別碼。本指南亦說明常見變化，例如變更外觀或巢狀控制項，讓您能將此解決方案套用於任何專案。

## 前置條件

- .NET 6.0 或更新版本（此程式碼亦可於 .NET Framework 4.6+ 執行）
- 有效的 Aspose.Words for .NET 授權（或免費評估金鑰）
- Visual Studio 2022 或任何相容 C# 的 IDE
- 具備基本的 C# 語法知識

> **專業提示：** 若您使用免費評估版，請記得輸出文件會包含浮水印。授權版會自動移除浮水印。

## 使用 Aspose.Words 插入純文字內容控制項的方法

此解決方案的核心是一個三步驟流程：

1. **建立 `Document` 與 `DocumentBuilder`。**  
2. **插入具有預設外觀的純文字結構化文件標記 (SDT)。**  
3. **為 SDT 指派標題與標籤識別碼。**  

以下將分別說明每個步驟，並提供完整可執行的程式碼。

### 步驟 1：初始化文件與建構器

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Create a new empty document.
        Document doc = new Document();

        // DocumentBuilder lets you insert content into the document.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` 代表整個 Word 檔案，而 `DocumentBuilder` 提供如 `InsertParagraph`、`InsertImage`，以及本教學最關鍵的 `InsertStructuredDocumentTag` 等方法。先行初始化它們即可取得一個畫布，用以放置 **純文字內容控制項**。

### 步驟 2：插入純文字內容控制項 (SDT)

```csharp
        // Insert a plain‑text Structured Document Tag (SDT) with the default appearance.
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            SdtType.PlainText,          // The control type – plain text.
            SdtAppearance.Default);    // Visual style; Default shows a light gray shading.
```

`SdtType.PlainText` 告訴 Aspose.Words 建立 **純文字內容控制項**，其行為類似使用者可編輯的簡易文字方塊。`SdtAppearance.Default` 會以淡淡的背景呈現控制項，使文件中此區域明顯可編輯。

> **為何使用 `SdtAppearance.Default`？**  
> 預設外觀是跨 Word 版本最具相容性的樣式。如果您需要無框線的外觀，之後可以改用 `SdtAppearance.Hidden`。

### 步驟 3：設定標題與標籤識別碼

```csharp
        // Give the SDT a friendly title that appears in the Content Controls pane.
        sdt.Title = "MyTag";

        // Assign a unique tag identifier; this is useful for programmatic access later.
        sdt.Tag = "TagId";

        // (Optional) Add placeholder text inside the control.
        sdt.PlaceholderName = "Enter your text here";

        // Save the document to verify the result.
        doc.Save("output.docx");
    }
}
```

- **Title** (`sdt.Title`) 會顯示於 Word 的 *Content Controls* 面板，協助最終使用者了解欄位的用途。  
- **Tag** (`sdt.Tag`) 為開發者導向的識別碼，您可稍後透過 `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` 取得。  
- **PlaceholderName** 提供灰色提示文字，提升使用者體驗。  

上述完整程式碼片段構成一個可自行編譯執行的程式。執行後，`output.docx` 會包含一個純文字內容控制項，標題為 *MyTag*，標籤為 *TagId*。

![圖示說明在 Word 文件中插入純文字內容控制項](image.png){alt="insert plain text content control"}

## 了解 StructuredDocumentTag (SDT) 及其屬性

**Structured Document Tag** (SDT) 是 Word 內容控制項的底層物件模型。插入純文字控制項時最相關的屬性如下：

| 屬性 | 用途 | 典型值 |
|----------|---------|----------------|
| `SdtType` | 決定控制項類型（純文字、富文字、圖片等） | `PlainText`, `RichText`, `ComboBox`, `DatePicker` |
| `SdtAppearance` | 控制項的視覺樣式 | `Default`, `Hidden`, `BoundingBox`, `Tags` |
| `Title` | 在 *Content Controls* 面板中顯示的可讀名稱 | Any short string |
| `Tag` | 程式碼中使用的機器可讀識別碼 | Alphanumeric string |
| `PlaceholderName` | 控制項為空時顯示的文字 | Custom hint text |

當您設定 `SdtType.PlainText` 時，Word 會限制內容僅為純文字字元，防止富格式。這使得此控制項非常適合簡單的表單欄位，如 *Name*、*Email* 或 *Phone Number*。

### 可能需要的變化

| Scenario | Code change |
|----------|-------------|
| **無視覺陰影**（無框線） | Use `SdtAppearance.Hidden` instead of `Default`. |
| **唯讀欄位** | After insertion, set `sdt.LockContentControl = true`. |
| **預先填入資料** | Set `sdt.Text = "John Doe";` after creating the tag. |
| **在表格中放置多個控制項** | Insert the SDT inside a table cell using `builder.InsertCell();` before the `InsertStructuredDocumentTag` call. |

## 常見陷阱與避免方法

1. **忘記設定標題** – Word 仍會建立控制項，但使用者在 *Content Controls* 面板中不會看到有意義的描述。請務必指派 `sdt.Title`。  
2. **使用錯誤的 `SdtType`** – 若您需要純文字卻不小心選擇了 `RichText`，控制項將允許格式化，可能會破壞後續處理。請再次確認列舉值。  
3. **儲存至唯讀資料夾** – `doc.Save` 會拋出 `UnauthorizedAccessException`。請確保目標目錄可寫入，或在測試時使用 `Path.GetTempPath()`。  
4. **未套用授權** – 若未使用有效授權，輸出文件會包含評估浮水印。請在程式一開始即套用授權：

```csharp
License lic = new License();
lic.SetLicense("Aspose.Words.lic");
```

## 完整、可執行的範例

以下為完整程式碼，可直接複製貼上至新的 Console 專案中。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace InsertPlainTextContentControl
{
    class Program
    {
        static void Main()
        {
            // Apply license (optional for evaluation)
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // 1️⃣ Create a new document and a builder to edit it
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a plain‑text Structured Document Tag (SDT) with default appearance
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText,          // Plain text control
                SdtAppearance.Default);    // Light gray shading

            // 3️⃣ Assign a title and a tag identifier to the SDT
            sdt.Title = "MyTag";          // Human‑readable title
            sdt.Tag = "TagId";            // Unique machine identifier
            sdt.PlaceholderName = "Enter your text here";

            // (Optional) Add some introductory text before the control
            builder.MoveToDocumentStart();
            builder.Writeln("Please fill in the following field:");

            // 4️⃣ Save the document
            string outputPath = "output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**預期輸出：** 在 Microsoft Word 開啟 `output.docx` 時，會看到一行文字 *“Please fill in the following field:”*，其後是一個淡灰色方框區域，標籤為 *MyTag*。佔位文字 *Enter your text here* 以淡灰色顯示，直至使用者輸入內容。

## 結論

您現在已了解如何使用 Aspose.Words for .NET **插入純文字內容控制項** 到 Word 文件中。教學涵蓋了初始化 `Document`、插入 `PlainText` 類型的 `StructuredDocumentTag`，以及自訂其標題、標籤與佔位文字。透過了解 `SdtAppearance` 選項與常見陷阱，您可以自信地建立依賴可編輯內容控制項的表單、範本與自動化報告。

### 接下來？

- 探索其他 SDT 類型，例如用於下拉選單的 `RichText` 或 `ComboBox`。  
- 在表格內結合多個內容控制項，或使用 `RepeatingSection` 進行重複。  
- 使用 `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` 程式化讀取或修改控制項值。  

歡迎嘗試前述變化，並將此模式整合至更大的文件產生流程中。祝程式開發愉快！

## 接下來該學什麼？

以下教學涵蓋與本指南緊密相關的主題，並以此為基礎。每個資源皆提供完整可運作的程式碼範例與逐步說明，協助您精通其他 API 功能，並在專案中探索替代實作方式。

- [如何在 C# 使用 Aspose.Words 建立內容控制項](/words/english/net/programming-with-sdt/how-to-create-content-control-in-c-with-aspose-words/)
- [在 C# 建立新 Word 文件並插入內容控制項](/words/english/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/)
- [在 Aspose.Words for .NET 中使用 Document Builder 添加內容](/words/english/net/add-content-using-document-builder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}