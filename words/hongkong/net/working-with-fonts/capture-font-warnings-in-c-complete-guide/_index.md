---
category: general
date: 2026-03-06
description: 在 C# 中載入 Word 文件時捕捉字型警告。學習偵測缺失字型、檢查文件字型，並有效處理缺失字型。
draft: false
keywords:
- capture font warnings
- detect missing fonts
- load word document
- check document fonts
- handle missing fonts
language: zh-hant
og_description: 在 C# 載入 Word 文件時捕捉字型警告。本教學示範如何偵測缺失字型、檢查文件字型，並處理缺失字型。
og_title: 捕捉 C# 中的字型警告 – 完整指南
tags:
- Aspose.Words
- C#
- Font Management
title: 捕捉 C# 中的字型警告 – 完整指南
url: /zh-hant/net/working-with-fonts/capture-font-warnings-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 中捕獲字體警告 – 完整指南

有沒有需要在處理 Word 文件時**捕獲字體警告**？捕獲字體警告對於**偵測缺失字體**以及確保最終輸出與您預期完全相同至關重要。  

在本教學中，我們將逐步示範一個實用的端到端範例，載入 `.docx` 檔案、監控載入過程，並回報任何字體替換。完成後，您將了解如何安全地**load word document**、**check document fonts**，以及在不會出現意外執行時錯誤的情況下**handle missing fonts**。

## 您將學到

- 如何將警告收集器附加到 Aspose.Words `Document`。
- 哪些警告類型表示缺失或已替換的字體。
- 在正式應用程式中記錄或回應這些警告的方法。
- 如果需要優雅地**handle missing fonts**，設定自訂字體來源的技巧。

> **先決條件：** 您已擁有有效的 Aspose.Words for .NET 授權（或使用免費試用版），並具備 .NET 開發環境（Visual Studio、Rider 或 VS Code）。不需要其他函式庫。

---

## 捕獲字體警告 – 步驟說明

以下是完整可執行的程式碼。每個部分都拆分為獨立步驟，方便您複製貼上、實驗與擴充邏輯。

![捕獲字體警告示意圖](image.png "Diagram showing warning collection"){: alt="捕獲字體警告示意圖"}

### 步驟 1：載入 Word 文件

首先，我們需要**load word document**，該文件可能包含當前機器未安裝的字體。`Document` 建構函式負責主要工作，但我們會將呼叫獨立，讓您日後可以改為使用串流或位元組陣列。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class FontWarningDemo
{
    static void Main()
    {
        // 👉 Replace the path with the location of your .docx file.
        string inputPath = @"YOUR_DIRECTORY\input.docx";

        // Step 1: Load the Word document.
        Document doc = LoadDocument(inputPath);

        // Step 2 and 3 are performed inside LoadDocument – see below.
    }

    /// <summary>
    /// Loads a document while attaching a warning collector.
    /// Returns the Document instance ready for further processing.
    /// </summary>
    private static Document LoadDocument(string path)
    {
        // Create the warning collector before the load.
        var warningCollector = new WarningInfoCollector();

        // Attach the collector to the document’s warning callback.
        // This ensures that any font‑related warnings are captured.
        Document tempDoc = new Document();
        tempDoc.WarningCallback = warningCollector;

        // Load the file – this is where Aspose.Words may discover missing fonts.
        tempDoc = new Document(path);

        // After loading, iterate over warnings and report them.
        ReportFontWarnings(warningCollector);

        return tempDoc;
    }
```

**為什麼這很重要：** 若在載入文件時未設定警告處理程式，任何字體替換都會被靜默忽略。透過在載入前設定 `WarningCallback`，我們即可確保看到所有發生的 `FontSubstitution` 警告。

### 步驟 2：附加警告收集器

`WarningInfoCollector` 類別是 `IWarningCallback` 的內建實作。它會將每個警告儲存於清單中，供稍後檢查。

```csharp
    /// <summary>
    /// Scans the collected warnings and prints information about missing fonts.
    /// </summary>
    private static void ReportFontWarnings(WarningInfoCollector collector)
    {
        foreach (WarningInfo warning in collector.Warnings)
        {
            // We’re only interested in font‑related warnings.
            if (warning.Type == WarningType.FontSubstitution)
            {
                // warning.Description contains the original font name.
                // warning.Subtype holds the name of the font that was actually used.
                Console.WriteLine(
                    $"Font '{warning.Description}' was substituted with '{warning.Subtype}'.");
            }
        }
    }
}
```

**專業提示：** 若您需要更積極地**handle missing fonts**（例如，中止載入或以特定備援字體替換），可以將 `Console.WriteLine` 換成自訂邏輯——拋出例外、寫入檔案日誌，甚至加入自訂字體來源。

### 步驟 3：驗證輸出

在終端機執行程式。若您的 `input.docx` 使用了未安裝的字體，您會看到類似以下的行：

```
Font 'Comic Sans MS' was substituted with 'Arial'.
Font 'MyCustomFont' was substituted with 'Times New Roman'.
```

若沒有任何輸出，表示文件僅使用已安裝的字體，**或** Aspose.Words 在其內建備援集合中找到相符的字體。無論哪種情況，您都已成功**check document fonts**。

---

## 在未取得授權的情況下偵測缺失字體（免費試用）

即使您使用 30 天試用版，警告機制仍完全相同。唯一差異是試用版會在產生的輸出上加上浮水印，但這**不會**影響警告收集。因此，您可以在決定購買正式授權前安全地**detect missing fonts**。

---

## 處理缺失字體 – 進階選項

有時您希望提供自訂字體檔案（例如公司品牌字體），以避免發生替換。Aspose.Words 允許您註冊自訂字體資料夾：

```csharp
// Register a folder that contains all your custom .ttf/.otf files.
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
doc.FontSettings = fontSettings;
```

若希望載入器在初始解析階段即考慮這些字體，請將上述程式碼**放在**載入文件之前。這是最可靠的**handle missing fonts**方式，無需依賴預設系統字體。

---

## 常見陷阱與避免方法

| 陷阱 | 發生原因 | 解決方式 |
|------|----------|----------|
| **在載入後才附加警告收集器** | 文件已經被解析，因此不會記錄任何警告。 | 在呼叫 `new Document(path)` 之前**附加** `WarningCallback`。 |
| **只出現一般警告** | 您篩選了錯誤的 `WarningType`。 | 使用 `WarningType.FontSubstitution` 以聚焦字體問題。 |
| **即使缺少字體仍無輸出** | Aspose.Words 找到內建備援字體（例如 Arial）。 | 透過 `fontSettings.SubstitutionSettings.DefaultFontSubstitution = false;` 停用內建備援。 |
| **掃描大型文件時效能下降** | 收集所有警告會增加開銷。 | 僅限制收集 `FontSubstitution`，或分批處理警告。 |

---

## 完整可執行範例（可直接複製貼上）

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class FontWarningDemo
{
    static void Main()
    {
        string inputPath = @"YOUR_DIRECTORY\input.docx";

        // Load the document and capture any font warnings.
        Document doc = LoadDocument(inputPath);

        // At this point you can continue processing the document,
        // knowing that you’ve already reported any missing fonts.
        Console.WriteLine("Document loaded successfully.");
    }

    private static Document LoadDocument(string path)
    {
        var warningCollector = new WarningInfoCollector();

        // IMPORTANT: set the callback BEFORE the load.
        Document tempDoc = new Document();
        tempDoc.WarningCallback = warningCollector;

        // OPTIONAL: register custom font folder to reduce substitutions.
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
        tempDoc.FontSettings = fontSettings;

        // Load the document – this triggers warning collection.
        tempDoc = new Document(path);

        // Report any font substitutions.
        ReportFontWarnings(warningCollector);

        return tempDoc;
    }

    private static void ReportFontWarnings(WarningInfoCollector collector)
    {
        foreach (WarningInfo warning in collector.Warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine(
                    $"Font '{warning.Description}' was substituted with '{warning.Subtype}'.");
            }
        }
    }
}
```

**預期的終端機輸出**（假設缺少兩種字體）：

```
Font 'Comic Sans MS' was substituted with 'Arial'.
Font 'MyCustomFont' was substituted with 'Times New Roman'.
Document loaded successfully.
```

如果終端機除了顯示「Document loaded successfully」外保持沉默，表示您已**check document fonts**，且未發現缺失字體。

---

## 結論

我們示範了如何在 C# 中使用 Aspose.Words **capture font warnings**，這是一種可靠的**detect missing fonts**、安全**load word document**、**check document fonts**，以及透過自訂字體來源**handle missing fonts**的方法。

有了這套模式，您即可將字體驗證整合至任何自動化流程——無論是產生 PDF、轉換為 HTML，或僅是歸檔 Word 檔案。

### 接下來？

- 探索 **FontSettings.SubstitutionSettings** API，以定義自訂備援規則。
- 將警告收集與日誌框架（Serilog、NLog）結合，以進行正式環境監控。
- 使用相同方法捕獲其他警告類型，例如影像解析度或不支援的功能。

對字體處理或 Aspose.Words 有其他問題嗎？歡迎留言或前往 Aspose 社群論壇。祝開發愉快，願您的文件永遠以預期的字體呈現！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}