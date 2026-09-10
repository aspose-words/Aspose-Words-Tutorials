---
category: general
date: 2025-12-29
description: Aspose 載入選項讓您在載入 DOCX 檔案時自訂字型設定並偵測缺少的字型。了解如何在完整掌控下載入 docx。
draft: false
keywords:
- aspose load options
- how to load docx
- custom font settings
- load word document
- detect missing fonts
language: zh-hant
og_description: Aspose 載入選項讓您在載入 DOCX 檔案時自訂字型設定並偵測缺少的字型。了解如何在完整控制下載入 docx。
og_title: Aspose 載入選項 – 載入具自訂字型設定的 DOCX
tags:
- Aspose.Words
- C#
- Document Processing
title: Aspose 載入選項 – 使用自訂字型設定載入 DOCX
url: /zh-hant/net/programming-with-loadoptions/aspose-load-options-load-docx-with-custom-font-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Load Options – Load DOCX with Custom Font Settings

有沒有想過如何在 C# 中載入 DOCX 檔案而不會因缺少字型而出錯？你並不孤單。**Aspose Load Options** 讓你能精確控制 Word 文件的開啟方式，設定自訂字型設定，甚至在字型缺失成為問題之前就偵測到它們。

在本教學中，我們將完整示範如何使用 Aspose.Words 載入 DOCX、設定 **custom font settings**，以及建立一個警告回呼，告訴你哪些字型遺失。完成後，你就能自信地 **load word document** 檔案，無論原作者使用了什麼字型。

> **Prerequisite** – 你需要在專案中參考最新版本的 Aspose.Words for .NET，並具備基本的 C# 知識。無需其他函式庫。

## What You’ll Learn

- 如何建立 `LoadOptions` 物件並附加警告回呼。  
- 如何設定 `FontSettings` 以實作 **custom font settings**。  
- 如何實際 **load docx** 並驗證缺少的字型是否已回報。  
- 處理邊緣案例技巧，例如嵌入字型或基於網路的字型資料夾。

## Step 1: Install Aspose.Words and Prepare the Project

首先，確保已安裝 Aspose.Words。最簡單的方式是透過 NuGet：

```bash
dotnet add package Aspose.Words
```

套件加入後，建立一個新的 C# 主控台專案（或將程式碼放入任何現有應用程式）。我們的程式碼相容於 .NET 6+ 與 .NET Framework 4.7.2+，兩者皆可使用。

> **Pro tip:** 若目標為 .NET Core，請在檔案開頭加入 `using System;`；IDE 通常會自動插入。

## Step 2: Configure Aspose Load Options with a Warning Callback

現在進入重點——**aspose load options**。`LoadOptions` 類別讓你調整文件的解析方式。我們將使用它來：

1. 附加一個回呼，當載入器找不到所請求的字型時觸發。  
2. 指定一個 `FontSettings` 實例，之後可用於 **custom font settings** 的調整。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // --------------------------------------------------------------
        // Step 2.1 – Create LoadOptions and a FontSettings object
        // --------------------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();

        // FontSettings is where you control where Aspose looks for fonts.
        // You could point it at a folder, a collection, or even a stream.
        FontSettings fontSettings = new FontSettings();

        // --------------------------------------------------------------
        // Step 2.2 – Register a warning callback to detect missing fonts
        // --------------------------------------------------------------
        fontSettings.SubstitutionSettings.WarningCallback = (sender, args) =>
        {
            // This will be called for each missing font.
            // args.FontInfo can be null, so we guard against it.
            string missingFont = args.FontInfo?.FullFontName ?? "Unknown Font";
            Console.WriteLine($"[Warning] Missing font: {missingFont}");
        };

        // Attach the FontSettings to the LoadOptions.
        loadOptions.FontSettings = fontSettings;

        // --------------------------------------------------------------
        // Step 2.3 – (Optional) Add a custom font folder
        // --------------------------------------------------------------
        // If you have a folder with corporate fonts, tell Aspose to use it.
        // Replace "C:\\MyFonts" with the actual path on your machine.
        fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);
```

**為什麼這很重要：** 若未設定警告回呼，Aspose 會默默替換缺少的字型，可能導致之後的版面配置出現意外。透過掛接回呼，你可以提前 **detect missing fonts**，並決定是嵌入備用字型或請使用者安裝缺失的字型。

## Step 3: Load the DOCX Using the Configured Options

有了 `LoadOptions` 後，載入 DOCX 只需一行程式碼。`Document` 建構子接受檔案路徑與我們剛建立的選項。

```csharp
        // --------------------------------------------------------------
        // Step 3 – Load the DOCX file while respecting our custom settings
        // --------------------------------------------------------------
        string inputPath = @"C:\Documents\input.docx";

        // The Document constructor will invoke the warning callback
        // for any font it cannot resolve.
        Document doc = new Document(inputPath, loadOptions);

        Console.WriteLine("Document loaded successfully.");
```

如果來源檔案引用了系統或自訂資料夾中不存在的字型，你會看到類似以下的輸出：

```
[Warning] Missing font: Times New Roman
[Warning] Missing font: Calibri
Document loaded successfully.
```

在建構必須保證視覺一致性的批次處理流程時，這種即時回饋非常寶貴。

## Step 4: Verify the Loaded Document (Optional but Helpful)

載入後，你想確認文件內容是否可存取。作為快速檢查，我們輸出第一段的文字。

```csharp
        // --------------------------------------------------------------
        // Step 4 – Quick sanity check: print the first paragraph
        // --------------------------------------------------------------
        string firstParagraph = doc.FirstSection.Body.Paragraphs[0].GetText();
        Console.WriteLine($"First paragraph text: {firstParagraph}");
    }
}
```

執行程式後會得到：

```
[Warning] Missing font: Times New Roman
Document loaded successfully.
First paragraph text: This is the first line of my DOCX file.
```

## Step 5: Edge Cases & Advanced Tips

### 5.1 Handling Embedded Fonts

某些 DOCX 直接嵌入所型。Aspose.Words 會自動使用這些字型，因此不會顯示警告。但若你刻意 **load word document** 並移除嵌入字型（例如轉換後），可能需要如前所示透過 `SetFontsFolder` 提供缺失的字型。

### 5.2 Using a Memory Stream Instead of a File Path

如果 DOCX 存放於資料庫或來自 HTTP 請求，你可以從 `MemoryStream` 載入：

```csharp
using (var stream = new MemoryStream(byteArrayFromDb))
{
    Document docFromStream = new Document(stream, loadOptions);
    // Continue processing...
}
```

相同的 **aspose load options** 仍然適用，警告回呼仍會運作。

### 5.3 Overriding Font Substitution Globally

如果你想將缺失的字型替換為特定的備用字型（例如 Arial），可以加入替換規則：

```csharp
fontSettings.SubstitutionSettings.FontSubstitution.AddSubstitutes("MissingFontName", new[] { "Arial" });
```

將此與警告回呼結合，可記錄替換事件，確保輸出一致。

## Step 6: Full Working Example

以下是完整、可直接複製貼上的程式範例，涵蓋上述所有步驟。將其儲存為 `Program.cs`，還原 NuGet 套件後執行。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // --------------------------------------------------------------
        // Create LoadOptions with custom font settings and warning callback
        // --------------------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();
        FontSettings fontSettings = new FontSettings();

        // Warn about missing fonts
        fontSettings.SubstitutionSettings.WarningCallback = (sender, args) =>
        {
            string missing = args.FontInfo?.FullFontName ?? "Unknown Font";
            Console.WriteLine($"[Warning] Missing font: {missing}");
        };

        // Optional: point to a folder with corporate fonts
        fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

        // Attach settings to load options
        loadOptions.FontSettings = fontSettings;

        // --------------------------------------------------------------
        // Load the DOCX file
        // --------------------------------------------------------------
        string inputPath = @"C:\Documents\input.docx";
        Document doc = new Document(inputPath, loadOptions);
        Console.WriteLine("Document loaded successfully.");

        // --------------------------------------------------------------
        // Quick sanity check – print first paragraph
        // --------------------------------------------------------------
        string firstParagraph = doc.FirstSection.Body.Paragraphs[0].GetText();
        Console.WriteLine($"First paragraph text: {firstParagraph}");

        // --------------------------------------------------------------
        // (Optional) Demonstrate loading from a stream
        // --------------------------------------------------------------
        // byte[] bytes = File.ReadAllBytes(inputPath);
        // using var ms = new MemoryStream(bytes);
        // Document docFromStream = new Document(ms, loadOptions);
        // Console.WriteLine("Loaded from stream.");
    }
}
```

### Expected Output

```
[Warning] Missing font: Times New Roman
[Warning] Missing font: Calibri
Document loaded successfully.
First paragraph text: This is the first line of my DOCX file.
```

若沒有缺少字型，警告行將不會出現。

## Visual Overview

![aspose load options example](/images/aspose-load-options.png "Diagram showing Aspose Load Options workflow")

*此圖示說明 **Aspose Load Options** 位於檔案來源與 `Document` 物件之間，負責字型解析與缺失字型偵測。*

## Conclusion

我們已完整說明 **aspose load options** 的解決方案，示範如何 **how to load docx** 同時套用 **custom font settings** 與 **detect missing fonts**。透過設定警告回呼，並可選擇將 Aspose 指向自訂字型資料夾，你即可在字型問題影響渲染前取得完整可見性。

接下來你可以探索相關主題，例如 **load word document** 轉 PDF、加入浮水印，或在資料夾中批次理數十個檔案。相同的模式——建立 `LoadOptions`、附加回呼，然後呼叫 `new Document(...)`——適用於整個 Aspose.Words API。

對於特定邊緣案例有疑問，例如處理從右至左語言或加密的 DOCX 檔案？歡迎留言或查閱 Aspose.Words 文件以深入了解。祝程式開發順利，願你的文件始終如預期般正確呈現！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}