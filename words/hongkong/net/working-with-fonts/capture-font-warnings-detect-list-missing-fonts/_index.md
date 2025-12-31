---
category: general
date: 2025-12-31
description: 捕捉 Aspose.Words 中的字型警告，以偵測缺少的字型，並在您的 .NET 應用程式中列出缺少的字型。了解一步一步的 C# 解決方案。
draft: false
keywords:
- capture font warnings
- detect missing fonts
- list missing fonts
- Aspose.Words font warnings
- C# document loading
language: zh-hant
og_description: 在 Aspose.Words 中捕捉字型警告，以偵測缺失的字型並列出缺少的字型。完整的 C# 教學，附上程式碼與技巧。
og_title: 擷取字型警告 – 偵測並列出缺失字型
tags:
- Aspose.Words
- C#
- .NET
- Font Substitution
title: 捕捉字型警告 – 偵測及列出缺失字型
url: /zh-hant/net/working-with-fonts/capture-font-warnings-detect-list-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 捕捉字體警告 – 偵測與列出缺失字體

是否曾在載入 Word 文件時**捕捉字體警告**，卻不曉得如何取得缺失字體的詳細資訊？你並不孤單。在許多實務專案中，缺失字體會導致版面錯亂，若沒有適當的警告，你只能不斷追蹤難以定位的錯誤。

在本教學中，我們將示範如何使用 Aspose.Words for .NET **偵測缺失字體** 並 **列出缺失字體**。完成後，你將擁有一段可直接執行的 C# 程式碼，能印出每一筆替換警告，讓你可以記錄、提醒，甚至自動替換字體。

---

## 為何捕捉字體警告很重要

當 Aspose.Words 開啟一個引用了伺服器上未安裝字體的 DOCX 時，會悄悄使用備用字體取代。文件看起來仍然正常，但視覺一致性已受影響——想像一下企業品牌標誌被渲染成了錯誤的字型。

捕捉這些警告可以讓你：

* **維持品牌一致性** – 立即知道哪些字體缺失。  
* **自動化修復** – 程式化地替換缺失字體。  
* **合規稽核** – 為法律或設計審查產生報告。

簡言之，**捕捉字體警告** 是防止靜默字體替換的第一道防線。

---

## 設定 LoadOptions 以偵測缺失字體

顯示警告的關鍵在於 `LoadOptions.FontSubstitutionWarning` 屬性。預設為 `None`，表示 Aspose.Words 會吞掉訊息。將其改為 `All` 即可讓程式庫記錄每一次的替換事件。

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Configure LoadOptions so every font‑substitution warning is stored
LoadOptions loadOptions = new LoadOptions
{
    // Provide a fresh FontSettings instance – you can also pre‑load custom fonts here
    FontSettings = new FontSettings(),

    // This flag tells Aspose.Words to capture *all* font‑related warnings
    FontSubstitutionWarning = FontSubstitutionWarning.All
};
```

> **小技巧：** 若你已有自訂字體資料夾，可在載入文件前使用 `FontSettings.SetFontsFolder("path")` 指定。如此一來，系統就能**偵測不在系統目錄中的缺失字體**。

---

## 載入文件並列出缺失字體

`LoadOptions` 設定完成後，接下來就可以載入 Word 檔案。建構子接受這個選項物件，任何字體替換都會記錄在文件的 `WarningInfoCollection` 中。

```csharp
// Path to the DOCX that may contain unknown fonts
string docPath = @"C:\Docs\UnknownFonts.docx";

// Load the document with the warning‑capture options
Document document = new Document(docPath, loadOptions);
```

如果檔案引用了不存在的字體，每個缺失字體都會產生一筆 `WarningInfo`。透過遍歷該集合，即可**列出缺失字體**。

```csharp
// Iterate through the warnings and output them to the console
foreach (WarningInfo warning in document.WarningInfoCollection)
{
    // The warning.Type will be FontSubstitution, and Description contains details
    Console.WriteLine($"{warning.Type}: {warning.Description}");
}
```

典型輸出如下：

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

每一行都精確指出缺失的字體，滿足 **列出缺失字體** 的需求。

---

## 讀取與解析 WarningInfoCollection

`WarningInfoCollection` 可能包含多種警告類型（例如 `DocumentStructure`、`ImageLoading`）。若只想關注字體問題，可依 `WarningType.FontSubstitution` 進行過濾。

```csharp
var fontWarnings = document.WarningInfoCollection
                           .Where(w => w.Type == WarningType.FontSubstitution);

foreach (var fw in fontWarnings)
{
    Console.WriteLine($"Missing font detected: {fw.Description}");
}
```

為什麼要過濾？大型文件常會同時產生圖像損毀或不支援功能的警告。縮小集合範圍即可避免噪音，讓 **捕捉字體警告** 的輸出更乾淨。

---

## 完整範例 – 捕捉字體警告實作

以下程式碼為完整、獨立的範例，可直接放入任何 .NET 主控台專案。它示範了從設定 `LoadOptions` 到印出整潔的缺失字體清單的每一步。

```csharp
// ------------------------------------------------------------
// Complete C# example: Capture Font Warnings, Detect & List Missing Fonts
// ------------------------------------------------------------
using System;
using System.Linq;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare LoadOptions to capture all font‑substitution warnings
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings(),
            FontSubstitutionWarning = FontSubstitutionWarning.All
        };

        // OPTIONAL: If you have a custom font folder, point Aspose.Words to it
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyFonts", true);

        // 2️⃣ Load the document with the configured options
        string docPath = @"C:\Docs\UnknownFonts.docx";
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Filter only font‑substitution warnings
        var fontWarnings = doc.WarningInfoCollection
                               .Where(w => w.Type == WarningType.FontSubstitution);

        // 4️⃣ Output the missing‑font details
        Console.WriteLine("=== Missing Font Report ===");
        foreach (var warning in fontWarnings)
        {
            Console.WriteLine(warning.Description);
        }

        // 5️⃣ If no warnings were found, let the user know
        if (!fontWarnings.Any())
            Console.WriteLine("All referenced fonts are available – no warnings captured.");
    }
}
```

**預期的主控台輸出**

```
=== Missing Font Report ===
Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

若文件中沒有缺失字體，則會看到：

```
All referenced fonts are available – no warnings captured.
```

---

## 常見邊緣案例與處理方式

| 情境 | 為何會發生 | 推薦解決方案 |
|-----------|----------------|-----------------|
| **文件使用嵌入式 OpenType 字體** | Aspose.Words 能讀取嵌入字體，但前提是檔案未損毀。 | 先在 Word 中檢查 DOCX；必要時重新嵌入字體。 |
| **大量警告**（例如 200+ 缺失字體） | 從舊系統批次匯入時常會引用廣泛的字體組合。 | 批次處理警告：將資料寫入資料庫，再執行字體安裝腳本。 |
| **WarningInfoCollection 為空** | 文件本身已具備全部字體，或 `FontSubstitutionWarning` 仍為 `None`。 | 再次確認 `LoadOptions` 設定，並確保載入的路徑正確。 |
| **自訂字體位於網路共享** | 網路延遲可能導致字體查找逾時。 | 使用 `SetFontsFolder` 先行載入字體，並將 `CacheFontData = true`。 |

以上技巧可協助你在複雜環境中**可靠偵測缺失字體**。

---

## 圖示說明

![捕捉字體警告範例](https://example.com/images/capture-font-warnings.png "capture font warnings example")

*螢幕截圖顯示主控台執行時報告了兩個缺失字體。*

---

## 往後的步驟 – 超越簡易報告

既然已能**捕捉字體警告**，不妨考慮自動化修復：

1. **自動字體替換** – 透過修改 `FontSettings.SubstitutionSettings`，將缺失字體替換為公司批准的備用字體。  
2. **寫入監控系統** – 將警告訊息導入 Serilog、ELK 或 Azure Application Insights。  
3. **使用者報告** – 產生 HTML 或 PDF 摘要，讓設計師檢視哪些字體需安裝。

所有這些延伸功能皆建立在本教學的基礎上：設定 `LoadOptions`、載入文件、讀取 `WarningInfoCollection`。

---

## 結論

你現在已掌握在 Aspose.Words 中**捕捉字體警告**、**偵測缺失字體**以及**列出缺失字體**的完整流程，且輸出簡潔、適合主控台顯示。此僅需少量 C# 程式碼，且相容於支援 Aspose.Words 23.x 以上的任何 .NET 版本。

不妨在一個特意移除字體的測試 DOCX 上試試看——警告會即時出現。之後，你可以決定安裝缺失字體、以程式方式替換，或僅將問題記錄下來以供日後處理。

祝開發順利，願你的文件永遠以正確字體呈現！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}