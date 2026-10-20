---
category: general
date: 2026-10-20
description: 使用 C# 在 Word 文件中設定佔位文字。了解如何使用 Aspose.Words for .NET 快速新增控制項並設定佔位文字。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set placeholder text
- how to add control
- how to set placeholder
- generate word c#
language: zh-hant
lastmod: 2026-10-20
og_description: 使用 C# 在 Word 文件中設定佔位文字。本教學示範如何加入控制項、設定佔位文字，以及以程式方式產生 Word 檔案。
og_image_alt: Screenshot of a Word document showing placeholder text created with
  C# code
og_title: 使用 C# 在 Word 文件中設定佔位文字 – 步驟指南
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Set placeholder text in a Word document using C#. Learn how to add
    control and set placeholder quickly with Aspose.Words for .NET.
  headline: Set placeholder text in a Word document using C#
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for .NET is compatible with .NET Core, .NET 5, and .NET
      6+. The same code runs unchanged.
    question: Does this work with .NET Core?
  - answer: Use `sdt.SetText("Default value")` after creating the SDT. The placeholder
      disappears once a value is set.
    question: Can I set a default value in addition to the placeholder?
  - answer: 'Load the document, locate the SDT by its `Title` (`doc.GetChildNodes(NodeType.StructuredDocumentTag,
      true)`) and read `sdt.GetText()`. ## Conclusion You now know how to **set placeholder
      text** in a Word document using C#. By creating a plain‑text `StructuredDocumentTag`,
      assigning a title and place'
    question: What if I need to retrieve the entered value later?
  type: FAQPage
tags:
- C#
- Aspose.Words
- Word automation
- Content control
title: 使用 C# 在 Word 文件中設定佔位文字
url: /zh-hant/net/programming-with-sdt/set-placeholder-text-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 C# 在 Word 文件中設定 placeholder text

如果您需要在使用 C# 產生的 Microsoft Word 檔案中 **設定 placeholder text**，本指南將完整說明如何操作。您將看到一個簡潔、端對端的解決方案，該方案會新增 content control、定義其 placeholder，並儲存文件——全部使用 Aspose.Words for .NET。

許多開發者會好奇 **如何在 Word 文件中加入 control** 或 **如何設定 placeholder** 而不必手動開啟 Word。本教學將回答這些問題，並示範一種乾淨的方式來 **產生 Word C#** 檔案，讓使用者可以直接輸入。

## 您將完成的工作

* 以程式方式建立空白的 Word 文件。
* 插入純文字的 Structured Document Tag (SDT)，這是 content control 的技術名稱。
* 為 SDT 指定有意義的 title 與 placeholder text。
* 將產生的 `.docx` 檔案儲存至磁碟。

除了 Aspose.Words 函式庫與 .NET 6（或更新）開發環境外，無需其他工具。

## 前置條件

* .NET 6 SDK 或更新版本已安裝。  
* Visual Studio 2022（或任何支援 .NET 的 IDE）。  
* Aspose.Words for .NET NuGet 套件（`Install-Package Aspose.Words`）。  

> **專業提示：** 若您僅在測試，請使用 Aspose.Words 的免費評估版；它會加入浮水印，但功能與正式授權版相同。

## 步驟 1：設定專案並匯入命名空間

建立一個新的 console 專案，並加入所需的 `using` 指令。這些指令會將核心的 Aspose.Words 類別與 markup 命名空間匯入作用域。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // The complete solution starts here.
        }
    }
}
```

*此步驟的重要性：* 匯入 `Aspose.Words.Markup` 可讓您存取 `StructuredDocumentTag`、`SdtType` 與 `MarkupLevel`——這些物件是 **add control** 與 **set placeholder** 所必需的。

## 步驟 2：建立空白文件與 DocumentBuilder

`Document` 代表整個 Word 檔案，而 `DocumentBuilder` 則提供一個方便的游標，用於插入元素。

```csharp
// Step 2: Initialize a new empty document.
Document doc = new Document();

// DocumentBuilder starts at the beginning of the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*此步驟的重要性：* 從空白文件開始，可確保您設定的 placeholder 正確出現在預期位置，不會受到現有內容的干擾。

## 步驟 3：建立 content control（Structured Document Tag）

在此，我們建立一個純文字的 SDT，為其設定 title，並設定使用者在 control 為空時會看到的 placeholder text。

```csharp
// Step 3: Build a plain‑text Structured Document Tag (SDT).
StructuredDocumentTag sdt = new StructuredDocumentTag(
    doc,                     // Parent document
    SdtType.PlainText,       // Control type – plain text box
    MarkupLevel.Inline);     // Inline placement (behaves like a word)

sdt.Title = "CustomerName";                 // Logical name for the control
sdt.PlaceholderName = "Enter name here";    // Text shown when empty
```

*此步驟的重要性：* `Title` 屬性讓您之後可以引用此 control（例如資料繫結）。`PlaceholderName` 正是您想要顯示的 **set placeholder text**，可指引最終使用者。

## 步驟 4：在目前游標位置插入 control

使用 `DocumentBuilder`，將 SDT 插入文件中 builder 目前所在的位置。

```csharp
// Step 4: Insert the SDT into the document.
builder.InsertNode(sdt);
```

*此步驟的重要性：* 插入節點會將 control 附加到文件的 DOM。若需加入多個 placeholder，您可以移動 builder 的游標並重複此步驟。

## 步驟 5：儲存文件

最後，將文件寫入磁碟。將 `YOUR_DIRECTORY` 替換為您機器上的實際路徑。

```csharp
// Step 5: Save the .docx file.
string outputPath = @"C:\Temp\SDT.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

當您在 Microsoft Word 中開啟 `SDT.docx` 時，會看到一個灰色陰影的行內文字方塊，內含 **Enter name here**。點擊方塊內部會清除 placeholder，讓使用者輸入客戶名稱。

### 預期輸出

| File location | Content preview |
|---------------|-----------------|
| `C:\Temp\SDT.docx` | 在標題為 *CustomerName* 的純文字 content control 內的行內 placeholder **Enter name here**。 |

## 邊緣情況與變體

| Situation | Recommended adjustment |
|-----------|------------------------|
| **Multiple placeholders** | 建立額外的 `StructuredDocumentTag` 物件，設定不同的 `Title` 與 `PlaceholderName` 值，然後在需要的地方插入。 |
| **Rich‑text placeholder** | 使用 `SdtType.RichText` 取代 `PlainText`，以允許在 placeholder 內進行格式設定。 |
| **Block‑level control** | 將 `MarkupLevel.Inline` 改為 `MarkupLevel.Block`，使 control 行為類似完整段落。 |
| **Placeholder not visible** | 確保 Word 中的文件檢視設定未隱藏 content controls（`File → Options → Advanced → Show content controls`）。 |
| **Saving to a stream** | 若需透過 HTTP 傳送檔案而非寫入磁碟，請呼叫 `doc.Save(stream, SaveFormat.Docx)`。 |

## 完整、可執行的範例

以下是完整的程式碼，您可以複製、貼上並執行。它在單一的 `Main` 方法中包含上述所有步驟。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank document.
            Document doc = new Document();

            // 2️⃣ Position a builder at the start of the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Define a plain‑text content control (SDT) with placeholder text.
            StructuredDocumentTag sdt = new StructuredDocumentTag(
                doc,
                SdtType.PlainText,
                MarkupLevel.Inline);

            sdt.Title = "CustomerName";                 // Logical identifier
            sdt.PlaceholderName = "Enter name here";    // The placeholder you see in Word

            // 4️⃣ Insert the SDT into the document.
            builder.InsertNode(sdt);

            // 5️⃣ Save the document to disk.
            string outputPath = @"C:\Temp\SDT.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document successfully saved to {outputPath}");
        }
    }
}
```

執行程式後，開啟產生的檔案，您會看到已準備好供使用者輸入的 placeholder text。

## 常見問題解答

**Q: 這能在 .NET Core 上運作嗎？**  
A: 可以。Aspose.Words for .NET 相容於 .NET Core、.NET 5 與 .NET 6+。相同程式碼可直接執行。

**Q: 我可以在 placeholder 之外設定預設值嗎？**  
A: 在建立 SDT 後使用 `sdt.SetText("Default value")`。一旦設定值，placeholder 會消失。

**Q: 若日後需要取得使用者輸入的值該怎麼做？**  
A: 載入文件，依 `Title` 取得 SDT（`doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`），然後讀取 `sdt.GetText()`。

## 結論

現在您已了解如何使用 C# 在 Word 文件中 **設定 placeholder text**。透過建立純文字的 `StructuredDocumentTag`、指定 title 與 placeholder、使用 `DocumentBuilder` 插入，最後儲存檔案，您即可以程式方式 **加入 control** 並 **產生 Word C#** 檔案。  

接下來您可以探索：

* 新增 rich‑text 或下拉清單 control（`SdtType.RichText`、`SdtType.DropDownList`）。  
* 從資料庫填充多個 placeholder。  
* 使用 Aspose.Words 將產生的 `.docx` 轉換為 PDF。

嘗試不同的 control 類型與 placeholder 風格，以符合您的應用需求。祝開發順利！

## 接下來您可以學習什麼？

以下教學涵蓋與本指南緊密相關的主題，並在此基礎上延伸技術。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在自己的專案中探索其他實作方式。

- [Set Placeholder Text in Aspose.Words – Complete C# Guide](/words/english/net/programming-with-sdt/set-placeholder-text-in-aspose-words-complete-c-guide/)
- [Create word document programmatically – add content control and placeholder](/words/english/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/)
- [How to Add Content Control and Create Word Document with Aspose – Complete](/words/english/net/programming-with-sdt/how-to-add-content-control-and-create-word-document-with-asp/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}