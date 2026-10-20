---
category: general
date: 2026-10-20
description: 使用 Aspose.Words 程式化建立 Word 文件，並加入指令按鈕。學習插入 ActiveX 控制項及設定按鈕標題。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add command button
- add activex control
- insert activex button
- set button caption
language: zh-hant
lastmod: 2026-10-20
og_description: 程式化建立 Word 文件並嵌入 ActiveX 命令按鈕。本教學說明如何插入控制項並使用 Aspose.Words 設定其標題。
og_image_alt: Word file showing an ActiveX command button inserted by Aspose.Words
og_title: 以程式方式建立 Word 文件 – 加入 ActiveX 按鈕
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  headline: Create Word document programmatically with an ActiveX button
  type: TechArticle
- description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  name: Create Word document programmatically with an ActiveX button
  steps:
  - name: 'Open a terminal or Visual Studio and create a new console project:'
    text: 'Open a terminal or Visual Studio and create a new console project:'
  - name: 'Add the Aspose.Words package:'
    text: 'Add the Aspose.Words package:'
  - name: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
    text: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
  - name: Open `ActiveXCommandButton.docx` in Microsoft Word.
    text: Open `ActiveXCommandButton.docx` in Microsoft Word.
  - name: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
    text: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
  - name: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
    text: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
  - name: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
    text: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: 使用 ActiveX 按鈕程式化建立 Word 文件
url: /zh-hant/net/working-with-oleobjects-and-activex/create-word-document-programmatically-with-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 ActiveX 按鈕以程式方式建立 Word 文件

以 Aspose.Words 程式方式建立 Word 文件，然後加入使用者可點擊的指令按鈕。本教學將逐步說明如何插入 ActiveX 控制項、設定其屬性，並將結果儲存為 **.docx** 檔案。

您將看到一個完整、可執行的範例，您可以將其複製到 Console 應用程式中。完成本教學後，您即可產生包含完整功能指令按鈕的 Word 檔，並了解如何 **add command button**、**add activex control**、**insert activex button**、**set button caption**，全部在 C# 程式碼內完成。

## Prerequisites

在開始之前，請確保您已具備：

* .NET 6.0 SDK 或更新版本  
* Visual Studio 2022（或任何相容 C# 的 IDE）  
* Aspose.Words for .NET 授權檔（免費試用版亦可執行本範例）  
* 基本的 C# 與 .NET 專案系統概念  

除了 **Aspose.Words** 之外，無需額外的 NuGet 套件，因為 ActiveX 支援已內建於此函式庫。

## Step 1: Set up the project and add Aspose.Words

1. 在終端機或 Visual Studio 中建立新的 Console 專案：

   ```bash
   dotnet new console -n WordActiveXDemo
   cd WordActiveXDemo
   ```

2. 新增 Aspose.Words 套件：

   ```bash
   dotnet add package Aspose.Words
   ```

3. （可選）若您有授權檔，請將其放在專案根目錄，並在 `Program.cs` 開頭加入以下程式碼，以避免評估水印：

   ```csharp
   Aspose.Words.License license = new Aspose.Words.License();
   license.SetLicense("Aspose.Words.lic");
   ```

## Step 2: Create Word document programmatically – initialize the document

第一步是 **create Word document programmatically**。您只需實例化 `Document` 物件，並使用 `DocumentBuilder` 來編輯文件內容。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;   // Provides ActiveX control types
using System.Drawing;        // For Point and Size structs

// Initialize a new blank document
Document document = new Document();

// DocumentBuilder gives a cursor‑based API for inserting elements
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` 代表整個檔案，而 `DocumentBuilder` 則維持一個游標，您可以將它移動到文件中的任意位置。此分離設計讓 API 更加清晰，也方便日後 **add activex control**，而不必手動處理底層結構。

## Step 3: Add command button – inserting an ActiveX control

接下來您將透過插入 `OleControlType.CommandButton` 類型的 ActiveX 控制項來 **add command button**。`InsertForms2OleControl` 方法需要傳入控制項類型、位置（`Point`）以及大小（`Size`）。

```csharp
// Define where the button will appear (X = 100 pt, Y = 150 pt)
Point buttonPosition = new Point(100, 150);

// Define the button dimensions (width = 120 pt, height = 30 pt)
Size buttonSize = new Size(120, 30);

// Insert the ActiveX command button at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton, // control type
    buttonPosition,              // position
    buttonSize);                 // size
```

上述呼叫會 **insert activex button** 到您指定的座標位置。座標單位為點（1 pt ≈ 1/72 in）。若您希望按鈕位於特定段落，請先移動 Builder 的游標：

```csharp
builder.Writeln("Click the button below:");
builder.MoveToDocumentEnd(); // places the cursor after the paragraph
```

## Step 4: Set button caption – customizing the command button text

沒有標籤的按鈕會讓使用者感到困惑，因此您需要 **set button caption** 為具意義的文字。`Caption` 屬性定義按鈕上顯示的文字，而 `Name` 則提供程式內的識別名稱。

```csharp
// Give the button a unique name for later reference
commandButton.Name = "btnSubmit";

// Set the visible text on the button
commandButton.Caption = "Submit";

// Optional: assign a macro name that Word will call when the button is clicked
commandButton.OnClick = "SubmitForm()";
```

若日後將文件匯出為支援巨集的格式（`.docm`），`OnClick` 的值必須對應到 VBA 巨集名稱。對於純 `.docx`，此屬性仍會被儲存，但不會執行，這對大多數自動化情境已足夠。

## Step 5: Save the document containing the ActiveX button

設定完控制項後，您可以 **save the document**。請選擇具有寫入權限的目錄，並使用 `.docx` 副檔名以取得最高相容性。

```csharp
// Replace with your desired output folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ActiveXCommandButton.docx");

// Save the document to disk
document.Save(outputPath);
```

當您在 Microsoft Word 中開啟產生的檔案時，會看到一個標示為 **Submit** 的按鈕，位於您先前指定的座標。若在桌面版 Word 中點擊該按鈕，系統會嘗試執行 `SubmitForm` 巨集（若該巨集存在）。

## Step 6: Verify the result and troubleshoot common issues

1. 在 Microsoft Word 中開啟 `ActiveXCommandButton.docx`。  
2. 切換至 **Design Mode**（開發人員索引標籤 → **Design Mode**）以檢視按鈕邊框。  
3. 若按鈕未顯示，請確認已啟用 **Developer** 索引標籤，且您的 Word 版本支援 ActiveX 控制項。  
4. 對於支援巨集的檔案（`.docm`），請確保 `OnClick` 中的巨集名稱與 VBA 程序相符，否則 Word 會顯示安全性警告。

### Pro tip

ActiveX 控制項僅限 Windows 使用。若您需要跨平台的互動功能，建議改用 **Content Controls**（`RichTextContentControl`）取代 ActiveX 按鈕。

## Full source code

以下為完整、可直接執行的程式碼。請將其複製到 `Program.cs`，然後執行 `dotnet run`。



## What Should You Learn Next?

以下教學與本指南緊密相關，能進一步深化您所學的技巧。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您掌握更多 API 功能，並在專案中探索其他實作方式。

- [Create Word Document with ActiveX Button – C# Guide](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)
- [Add Command Button to Word Document with Aspose.Words – Complete Guide](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)
- [create word document button with Aspose.Words – Full Code Example](/words/english/net/working-with-oleobjects-and-activex/create-word-document-button-with-aspose-words-full-code-exam/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}