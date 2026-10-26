---
category: general
date: 2026-10-23
description: 學習如何使用 C# 建立空白 Word 文件，並插入帶有佔位符的純文字內容控制項 (SDT)。內含逐步說明程式碼。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert control
- plain text content control
- how to add sdt
- add placeholder to tag
language: zh-hant
lastmod: 2026-10-23
og_description: 使用 C# 建立空白 Word 文件，並插入帶有佔位符的純文字內容控制項 (SDT)。請參考完整且可執行的範例。
og_image_alt: Screenshot showing a blank Word document with a highlighted plain text
  content control
og_title: 建立空白 Word 文件並加入純文字內容控制項 – C# 指南
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to create a blank Word document and insert a plain text content
    control (SDT) with a placeholder using C#. Includes step‑by‑step code.
  headline: How to create blank Word document with a plain text content control in
    C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- ContentControl
- WordAutomation
title: 如何在 C# 中建立帶有純文字內容控制項的空白 Word 文件
url: /zh-hant/java/document-manipulation/how-to-create-blank-word-document-with-a-plain-text-content/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中建立空白 Word 文件並加入純文字內容控制項

如果您需要以程式方式 **建立空白 Word 文件**，本指南將會一步步說明。使用 Aspose.Words for .NET，您可以從空檔案開始，插入純文字 StructuredDocumentTag (SDT)，為其設定標題，並加入實用的佔位文字——只需幾行 C# 程式碼。

本教學涵蓋您所需的每一步，從初始化文件到儲存最終的 `.docx`。完成後，您將擁有一段可重複使用的程式碼片段，隨時可放入任何 .NET 專案中。

## 前置條件

在開始之前，請確保您已具備：

* 已安裝 .NET 6.0（或更新版本）。
* 參考 **Aspose.Words** NuGet 套件。
* 如 Visual Studio 2022 或 Visual Studio Code 等開發環境。

不需要額外的函式庫。

## 如何建立空白 Word 文件並加入純文字內容控制項

首要任務是建立一個 **空白 Word 文件**。這會提供一個乾淨的畫布，之後您可以在上面 **插入控制項**。

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

// Step 1: Create a new blank document and a DocumentBuilder to edit it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Why this works*: `Document()` 會在記憶體中建立一個沒有頁面的 Word 檔案表示。`DocumentBuilder` 是協助您加入段落、表格與內容控制項的工具類別。

## 如何使用 DocumentBuilder 插入控制項

文件已建立後，您可以在游標所在位置直接 **插入控制項** 物件。若要插入純文字內容控制項，請使用 `InsertStructuredDocumentTag`。

```csharp
// Step 2: Insert a plain‑text StructuredDocumentTag (SDT) inline
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, MarkupLevel.Inline);
```

*Explanation*:  
* `StructuredDocumentTagType.PlainText` 告訴 Aspose.Words 建立 **純文字內容控制項**。  
* `MarkupLevel.Inline` 會將控制項放在目前段落內，使其行為如同一般文字。

## 如何為 SDT 加入標題與佔位文字

具備易於辨識的名稱可以讓日後定位控制項更方便，尤其在需要綁定資料或執行驗證時。**為標籤加入佔位文字** 的步驟亦能提升使用者體驗。

```csharp
// Step 3: Give the SDT a meaningful title (used for identification)
sdt.Title = "CustomerName";

// Step 4: Add placeholder text so the user knows what to enter
sdt.AppendChild(new Run(doc, "Enter name here"));
```

*Why this matters*:  
* `Title` 屬性是可供您使用 `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` 取得的中繼資料。  
* 佔位文字（`Run` 內的 “Enter name here”）在 Word 中會呈現為灰色，提示最終使用者替換它。

## 如何儲存含 SDT 的文件

最後，將檔案寫入磁碟。路徑可以是絕對路徑，也可以是相對於應用程式工作目錄的路徑。

```csharp
// Step 5: Save the document with the SDT to a file
doc.Save("SDTExample.docx");
```

當您在 Microsoft Word 中開啟 **SDTExample.docx** 時，會看到一行文字，裡面有一個帶灰色佔位文字的方框——正是您剛建立的 **純文字內容控制項**。

### 預期輸出

| 位置 | 視覺提示 |
|----------|------------|
| 第一段落內 | 標示為「Enter name here」的矩形方框（佔位文字） |

您可以直接在方框內輸入姓名；Word 會將輸入的文字視為 SDT 的內容。

## 新增多個控制項（可選）

如果需要多於一個 **純文字內容控制項**，請以新的 `DocumentBuilder` 位置重複第 2‑4 步。例如，加入地址欄位：

```csharp
builder.Writeln(); // Move to a new paragraph
StructuredDocumentTag addressSdt = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, MarkupLevel.Inline);
addressSdt.Title = "CustomerAddress";
addressSdt.AppendChild(new Run(doc, "Enter address here"));
```

*Tip*: 使用 `builder.Writeln()` 先建立新段落，再插入另一個 SDT，能保持版面整齊。

## 常見問題與避免方式

| 問題 | 原因 | 解決方式 |
|-------|-------|-----|
| 儲存後佔位文字消失 | SDT 使用 `MarkupLevel.Block` 而非 `Inline` 建立 | 使用 `MarkupLevel.Inline` 以取得行內佔位文字 |
| 標題無法搜尋 | 標題未設定或在儲存後才設定 | 在呼叫 `doc.Save()` 之前 **先設定** `sdt.Title` |
| Word 中文件顯示為空白 | 建立文件後未加入任何內容 | 確保在儲存前至少加入一個段落或控制項 |

## 專業技巧：將程式碼片段封裝成工具方法

將邏輯封裝起來，可在多個專案中重複使用：

```csharp
public static Document CreateDocumentWithPlainTextControl(string title, string placeholder)
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);

    StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
        StructuredDocumentTagType.PlainText, MarkupLevel.Inline);
    sdt.Title = title;
    sdt.AppendChild(new Run(doc, placeholder));

    return doc;
}

// Usage
Document myDoc = CreateDocumentWithPlainTextControl("OrderNumber", "Enter order #");
myDoc.Save("OrderForm.docx");
```

*Why this helps*: 此方法將 **建立空白 Word 文件** 的流程獨立，使您能在不重複程式碼的情況下，產生不同標題與佔位文字的多個範本。

## 後續步驟

現在您已掌握 **如何插入控制項** 與 **為標籤加入佔位文字**，可以進一步探索：

* 將 SDT 綁定至自訂 XML 部分 (`doc.CustomXmlParts`)——適用於資料驅動的範本。  
* 在保留內容控制項的前提下，將文件轉換為 PDF。  
* 使用其他 `StructuredDocumentTagType`（如 `Date`、`ComboBox`、`CheckBox`）打造更豐富的表單。

上述主題皆以本教學示範的核心模式為基礎。

---

**Summary**

本教學帶您完成 **建立空白 Word 文件**、插入 **純文字內容控制項**、設定標題以及加入實用的佔位文字。完整、可執行的範例可直接複製到任何 .NET 專案中，且可選的工具方法示範了如何擴充此作法。掌握這些基礎後，您即可在 C# 中構建更複雜的 Word 表單與範本。

---

## 接下來該學什麼？

以下教學與本指南緊密相關，並在此基礎上延伸技術。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在自己的專案中探索替代實作方式。

- [在 C# 中建立新 Word 文件並插入內容控制項](/words/english/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/)
- [以程式方式建立 Word 文件 – 加入內容控制項與佔位文字](/words/english/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/)
- [使用 Aspose 完整示範：加入內容控制項並建立 Word 文件](/words/english/net/programming-with-sdt/how-to-add-content-control-and-create-word-document-with-asp/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}