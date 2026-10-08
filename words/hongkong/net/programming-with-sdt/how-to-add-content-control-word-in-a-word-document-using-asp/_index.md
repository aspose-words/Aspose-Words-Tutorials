---
category: general
date: 2026-10-07
description: 了解如何使用 Aspose.Words 在 Word 文件中新增內容控制項。此指南亦說明如何為員工編號欄位建立內容控制項。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add content control word
- how to create content control
- add employee id field
- Aspose.Words content control
- C# Structured Document Tag
language: zh-hant
lastmod: 2026-10-07
og_description: 使用 Aspose.Words 在 Word 文件中新增內容控制項。跟隨本完整教學，了解如何建立內容控制項並新增員工編號欄位。
og_image_alt: Screenshot of a Word document showing an employee ID content control
  created with Aspose.Words
og_title: 使用 Aspose.Words 在 Word 中新增內容控制項 – 步驟教學
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to add content control word in a Word document with Aspose.Words.
    This guide also explains how to create content control for an employee ID field.
  headline: How to add content control word in a Word document using Aspose.Words
  type: TechArticle
- description: Learn how to add content control word in a Word document with Aspose.Words.
    This guide also explains how to create content control for an employee ID field.
  name: How to add content control word in a Word document using Aspose.Words
  steps:
  - name: Open `EmployeeForm.docx` in Word.
    text: Open `EmployeeForm.docx` in Word.
  - name: Click the gray box that says **Enter ID** – it should be replaced by **12345**.
    text: Click the gray box that says **Enter ID** – it should be replaced by **12345**.
  - name: Open the **Developer** tab → **Design Mode** to see the control’s properties
      (Title = *EmployeeID*).
    text: Open the **Developer** tab → **Design Mode** to see the control’s properties
      (Title = *EmployeeID*).
  type: HowTo
tags:
- Aspose.Words
- content control
- C#
title: 如何使用 Aspose.Words 在 Word 文件中新增內容控制項
url: /zh-hant/net/programming-with-sdt/how-to-add-content-control-word-in-a-word-document-using-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Aspose.Words 在 Word 文件中加入內容控制元件

如果您需要 **加入內容控制元件** 到 Word 檔案，本教學將會示範如何使用 Aspose.Words for .NET 函式庫完成。無論您是在建立類表單的文件或是自動化資料輸入，您都會學會 **如何建立內容控制元件**，以在單一步驟中捕捉員工的 ID。

在本指南中，您將會：

* 以程式方式建立空白的 Word 文件。  
* 插入作為內容控制元件的純文字 Structured Document Tag（SDT）。  
* 將員工 ID 填入控制元件並儲存檔案。  

唯一的前置條件是較新版的 .NET（建議 4.6 以上）以及 Aspose.Words 授權（或免費試用版）。除 `Aspose.Words` 之外，無需其他 NuGet 套件。

## 使用 Aspose.Words 加入內容控制元件

第一個主要步驟是建立內容控制元件本身。在 Aspose.Words 中，**內容控制元件** 由 `StructuredDocumentTag` 類別表示。將 SDT 加入文件即等同於 **加入內容控制元件**，之後可在 Microsoft Word 中編輯或以程式方式處理。

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

// 1️⃣ Create a new blank document and a DocumentBuilder to edit it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

*為何重要*：`DocumentBuilder` 提供類似游標的介面，讓您能在目前位置插入節點（段落、表格、SDT 等）。從空白文件開始可確保內容控制元件正確出現在您預期的位置。

## 如何為員工 ID 欄位建立內容控制元件

接下來，設定 SDT 為純文字內容控制元件，以保存員工識別碼。`Title` 屬性會在 Word 的 **Properties** 面板中顯示，而 `PlaceholderName` 則提供給使用者提示。

```csharp
// 2️⃣ Create a plain‑text Structured Document Tag (SDT) and set its metadata
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PlainText, true);
sdt.Title = "EmployeeID";            // Visible title in Word's UI
sdt.PlaceholderName = "Enter ID";    // Placeholder text shown when empty
```

*為何重要*：將 `Title` 設為 **EmployeeID** 使控制元件具備自說明性，之後使用 `StructuredDocumentTag.GetText()` 取值時會更方便。Placeholder 透過指示預期格式提升最終使用者體驗。

### 在內容控制元件內加入員工 ID 欄位

現在在 builder 目前位置插入 SDT，並寫入預設的員工編號。

```csharp
// 3️⃣ Insert the SDT into the document at the current builder position
builder.InsertNode(sdt);

// 4️⃣ Add default content inside the SDT (e.g., an employee ID)
builder.Writeln("12345");   // This text becomes the initial value of the control
```

*為何重要*：`InsertNode` 將 SDT 放入文件樹中。隨後的 `Writeln` 會在控制元件 **內部** 寫入內容，因為 builder 的游標仍在 SDT 節點內。若在插入 SDT 前呼叫 `Writeln`，文字會出現在控制元件外部。

## 儲存文件並驗證內容控制元件

最後，將文件寫入磁碟。儲存的 `.docx` 檔案將包含內容控制元件，您可在 Microsoft Word 中開啟，看到 placeholder 以及預設的員工 ID。

```csharp
// 5️⃣ Save the document with the SDT to a file
doc.Save(@"C:\Temp\EmployeeForm.docx");
```

*為何重要*：使用絕對或相對路徑可控制檔案儲存位置。Aspose.Words 會自動寫入內容控制元件所需的 XML 部分，無需額外步驟。

### 快速驗證步驟

1. 在 Word 中開啟 `EmployeeForm.docx`。  
2. 點擊顯示 **Enter ID** 的灰色方框——它應該會被 **12345** 取代。  
3. 開啟 **Developer**（開發人員）索引標籤 → **Design Mode**（設計模式），檢視控制元件的屬性（Title = *EmployeeID*）。

若控制元件未出現，請再次確認您使用的 Aspose.Words 版本為 ≥ 23.10；較早的版本對 `StructuredDocumentTag` 的建構子簽名不同。

## 可選變體與邊緣情況

| 情境 | 如何調整程式碼 |
|----------|-----------------------|
| **使用富文字控制元件** 取代純文字 | 將 `SdtType.PlainText` 改為 `SdtType.RichText`。 |
| **將控制元件加入現有文件** | 使用 `new Document("Existing.docx")` 載入檔案，並在插入 SDT 前將 builder 移至目標書籤位置。 |
| **鎖定內容控制元件，使使用者無法編輯其值** | 在建立 SDT 後設定 `sdt.LockContentControl = true;`。 |
| **套用自訂標籤以供之後擷取** | 使用 `sdt.Tag = "EmpIdTag";`，之後可透過 `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` 取得。 |
| **設定可重複的內容控制元件（多個 ID）** | 在表格列中建立 SDT，並依需求複製該列。 |

**小技巧**：在長時間執行的服務中使用完 `Document` 物件後，務必釋放（或以 `using` 區塊包住），以即時釋放原生資源。

## 結論

您現在已了解如何使用 Aspose.Words **加入內容控制元件** 到 Word 文件、如何 **建立內容控制元件** 以捕捉員工識別碼，以及如何以程式方式 **加入員工 ID 欄位**。依照上述步驟，您即可在任何產生的文件中嵌入結構化、可編輯的欄位，輕鬆以一致的格式收集或顯示資料。

接下來，您可以探索相關主題，例如 **將內容控制元件繫結至 XML 資料**、**為表格建立可重複的內容控制元件**，或 **使用 Aspose.Words API 從已填寫的控制元件中擷取值**。這些延伸功能讓您在不必手動開啟檔案的情況下，建立完整、資料驅動的 Word 表單。祝開發順利！

## 接下來該學什麼？

以下教學涵蓋與本指南緊密相關的主題，建立在所示技巧之上。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在專案中探索替代實作方式。

- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Add a Combo Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Add a Check Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}