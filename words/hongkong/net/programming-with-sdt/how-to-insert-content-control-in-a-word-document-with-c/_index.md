---
category: general
date: 2026-09-08
description: 學習如何使用 C# 與 Aspose.Words 在 Word 文件中插入內容控制項。包括建立內容控制項、設定佔位符以及儲存檔案的步驟。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert content control
- create content control
language: zh-hant
lastmod: 2026-09-08
og_description: 使用 C# 與 Aspose.Words 在 Word 檔案中插入內容控制項。請依照本指南建立內容控制項、設定佔位文字，並儲存文件。
og_image_alt: Insert content control example in a Word document
og_title: 使用 C# 在 Word 中插入內容控制項 – 步驟指南
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to insert content control in a Word document using C# and
    Aspose.Words. Includes steps to create content control, set placeholder, and save
    the file.
  headline: How to insert content control in a Word document with C#
  type: TechArticle
tags:
- content control
- Aspose.Words
- C#
- Word automation
title: 如何使用 C# 在 Word 文件中插入內容控制項
url: /zh-hant/net/programming-with-sdt/how-to-insert-content-control-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 文件中使用 C# 插入內容控制項

如果您需要 **插入內容控制項** 到 Word 文件，本指南將提供完整、可執行的解決方案。您還會學會如何以程式方式 **建立內容控制項**、設定佔位文字，並將檔案寫入磁碟。

內容控制項讓您定義使用者可以填寫、重複或鎖定的區域。它們廣泛應用於範本、表單與動態報告。以下步驟使用 Aspose.Words for .NET 函式庫，支援 .NET 6+、.NET Framework 4.6+ 與 .NET Core。

## 如何在 Word 文件中插入內容控制項

1. **將 Aspose.Words 加入您的專案**  
   在專案資料夾的終端機中執行：

   ```bash
   dotnet add package Aspose.Words
   ```

   此套件包含 `Document`、`DocumentBuilder` 與 `StructuredDocumentTag` 類別，這些都是建立內容控制項所需的。

2. **建立一個全新的空白文件**  

   ```csharp
   // Step 1: Create a new empty document and a DocumentBuilder
   Document doc = new Document();
   DocumentBuilder builder = new DocumentBuilder(doc);
   ```

   `Document` 物件代表整個 .docx 檔案，而 `DocumentBuilder` 提供方便的游標，用來插入節點。

## 使用 Aspose.Words 建立內容控制項

內容控制項以 `StructuredDocumentTag`（SDT）類別表示。以下程式碼會建立一個 **純文字** 內容控制項，並為其設定可供之後查詢的標題。

```csharp
// Step 2: Create a plain‑text StructuredDocumentTag (content control)
//         - Set a title that can be used to identify the control
//         - Provide placeholder text that appears when the control is empty
StructuredDocumentTag sdt = new StructuredDocumentTag(
    doc,
    SdtType.PlainText,      // Plain‑text control
    MarkupLevel.Block);    // Block‑level control (behaves like a paragraph)

sdt.Title = "CustomerName";
sdt.PlaceholderName = "Enter name here";
```

*為什麼這很重要：*  
- `SdtType.PlainText` 確保控制項僅接受純文字字元。  
- `MarkupLevel.Block` 使控制項的行為類似完整段落，這對表單欄位特別適合。  
- `Title` 屬性是一個穩定的識別碼，您可以在搜尋或綁定資料時使用。

## 設定佔位文字與預設文字

佔位文字會在使用者輸入前提供指引。您也可以預先填入預設內容。

```csharp
// Step 4: Optionally set default content for the control
sdt.XmlMapping.SetXmlFragment("<text>John Doe</text>");
```

XML 片段必須與控制項的資料類型相符。對於純文字控制項，需要 `<text>` 元素。若省略此步驟，先前定義的佔位文字將會顯示。

## 在指定位置插入內容控制項

`DocumentBuilder` 的游標決定控制項出現的位置。預設情況下，游標位於文件的開頭。

```csharp
// Step 3: Insert the StructuredDocumentTag into the document at the builder's current position
builder.InsertNode(sdt);
```

如果需要將控制項放入表格、頁首或現有段落之後，請先移動 Builder：

```csharp
builder.MoveToDocumentEnd();   // Example: place the control at the end of the file
builder.InsertNode(sdt);
```

## 儲存已插入內容控制項的文件

```csharp
// Step 5: Save the document with the content control
doc.Save(@"C:\Temp\SDT.docx");
```

檔案 `SDT.docx` 現在包含一個標題為 **CustomerName**、佔位文字為「Enter name here」、預設文字為「John Doe」的純文字內容控制項。

![在 Word 文件中插入內容控制項的範例圖](insert-content-control.png)

*圖片替代文字:* 在 Word 文件中插入內容控制項的範例圖

### 預期結果

在 Microsoft Word 中開啟 `SDT.docx` 時：

- 若刪除預設文字，會出現灰色佔位文字「Enter name here」。  
- 點擊控制項內部時會被高亮，表示可編輯。  
- **開發人員** 索引標籤（若已啟用）會在「屬性」窗格中顯示控制項的標題 **CustomerName**。

## 完整可執行範例

以下是一個單一、獨立的程式，您可以直接複製、編譯並執行。它示範了從專案設定到儲存檔案的每一步。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class InsertContentControlDemo
{
    static void Main()
    {
        // 1. Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Create a plain‑text content control (StructuredDocumentTag)
        StructuredDocumentTag sdt = new StructuredDocumentTag(
            doc,
            SdtType.PlainText,
            MarkupLevel.Block);

        sdt.Title = "CustomerName";          // Identifier for later use
        sdt.PlaceholderName = "Enter name here";

        // 3. Insert the control at the current cursor position
        builder.InsertNode(sdt);

        // 4. Set default text (optional)
        sdt.XmlMapping.SetXmlFragment("<text>John Doe</text>");

        // 5. Save the document
        string outputPath = @"C:\Temp\SDT.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

使用 `dotnet run` 執行程式。執行完畢後，開啟產生的檔案以驗證內容控制項是否如預期顯示。

## 實務技巧與常見陷阱

| 情境 | 推薦做法 |
|-----------|----------------------|
| **同類型的多個控制項** | 為每個控制項設定唯一的 `Title`。之後可使用 `doc.GetChildNodes(NodeType.StructuredDocumentTag, true).Cast<StructuredDocumentTag>().FirstOrDefault(s => s.Title == "YourTitle")` 取得特定控制項。 |
| **控制項在 Word 中看不到** | 確認已使用 `.docx` 副檔名儲存文件，且 Aspose.Words 版本與您的 Office 版本相容。 |
| **需要富文字控制項** | 使用 `SdtType.RichText` 取代 `PlainText`。此時 XML 片段需使用 `<w:richText>` 元素。 |
| **將控制項放入表格儲存格** | 先將 Builder 移至儲存格：`builder.MoveTo(cell.FirstParagraph); builder.InsertNode(sdt);`。 |
| **大型文件的效能** | 若需要大量相同的控制項，請只建立一次 `StructuredDocumentTag`，之後使用 `sdt.Clone(true)` 複製。 |

## 往後的步驟

- **建立可重複的內容控制項**（`SdtType.RepeatingSection`）以動態增長表格。  
- **將內容控制項綁定至 XML 資料**，使用 `sdt.XmlMapping.LoadXml(xmlString)`。  
- **鎖定控制項**（`sdt.LockContentControl = true`），防止使用者編輯，同時仍允許程式碼更新。  

探索上述主題將提升您使用 Aspose.Words 建立穩健 Word 範本的能力。

---

**結論**  
現在您已掌握如何使用 C# **插入內容控制項** 到 Word 文件。本教學涵蓋了建立控制項、設定佔位與預設文字、在指定位置插入以及儲存最終檔案。具備這些基礎後，您可以打造複雜的表單、合併列印範本與自動化報告，充分利用 Word 原生的內容控制功能。

## 接下來您應該學習什麼？

以下教學與本指南的技術密切相關，能進一步深化您對 API 功能的掌握，並探索在專案中實作的其他方式。

- [Set Content Control Style](/words/english/net/programming-with-sdt/set-content-control-style/)
- [Set Content Control Color](/words/english/net/programming-with-sdt/set-content-control-color/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}