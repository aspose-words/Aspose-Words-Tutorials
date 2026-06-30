---
category: general
date: 2026-06-30
description: 學習如何在 .NET 中使用 LoadOptions 載入字型、設定字型參數、啟用自訂字型，並透過警告回呼偵測缺少的字型。
draft: false
keywords:
- how to load fonts
- set font settings
- how to handle warnings
- enable custom fonts
- detect missing fonts
language: zh-hant
og_description: .NET 中如何載入字型？本指南會示範如何設定字型、啟用自訂字型，以及使用警告回呼偵測缺少的字型。
og_title: .NET 中如何載入字型 – 設定字型設定與警告
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Learn how to load fonts in .NET using LoadOptions, set font settings,
    enable custom fonts and detect missing fonts with warning callbacks.
  headline: How to Load Fonts in .NET – Set Font Settings & Warnings
  type: TechArticle
- description: Learn how to load fonts in .NET using LoadOptions, set font settings,
    enable custom fonts and detect missing fonts with warning callbacks.
  name: How to Load Fonts in .NET – Set Font Settings & Warnings
  steps:
  - name: Creating `LoadOptions` and configuring **set font settings**.
    text: Creating `LoadOptions` and configuring **set font settings**.
  - name: '**Enable custom fonts** by pointing to a folder of extra typefaces.'
    text: '**Enable custom fonts** by pointing to a folder of extra typefaces.'
  - name: '**How to handle warnings** with a `WarningCallback` that prints font substitution
      messages.'
    text: '**How to handle warnings** with a `WarningCallback` that prints font substitution
      messages.'
  - name: '**Detect missing fonts** by filtering `WarningType.FontSubstitution`.'
    text: '**Detect missing fonts** by filtering `WarningType.FontSubstitution`.'
  - name: Saving the document, confirming that the fallback
    text: Saving the document, confirming that the fallback
  type: HowTo
tags:
- Aspose.Words
- .NET
- Font Management
title: 在 .NET 中載入字型 – 設定字型設定與警示
url: /zh-hant/net/working-with-fonts/how-to-load-fonts-in-net-set-font-settings-warnings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 .NET 中載入字型 – 設定字型設定與警告

有沒有想過 **如何在 .NET 文件中載入字型** 而不讓人抓狂？你並不是唯一遇到這種情況的人。缺少字形、靜默的備用字型以及難以理解的警告，可能會把一個簡單的報表產生器變成噩夢。  

在本教學中，我們將逐步示範一個完整、可直接執行的範例，說明 **如何載入字型**、設定 **字型設定**、**啟用自訂字型**，以及透過處理警告 **偵測缺少的字型**。完成後，你將擁有一套可直接套用於任何 Aspose.Words 或類似函式庫專案的可靠模式。

> **快速概覽：** 我們將建立一個 `LoadOptions` 物件、附加警告回呼，並載入一個特意引用缺失字型的 DOCX。每當引擎替換字型時，主控台都會印出清晰的訊息。

## 需要的環境

- .NET 6.0 或更新版本（此程式碼亦可在 .NET Framework 4.6+ 上執行）  
- Aspose.Words for .NET（使用免費試用版 NuGet 套件即可）  
- 一個引用了你 *未* 安裝字型的 DOCX 檔案（例如 `MissingFont.docx`）  

就這樣——不需要額外服務，也不需要複雜的設定檔。只要具備上述三項，你就可以跟著操作了。

![載入字型範例圖示](https://example.com/how-to-load-fonts-diagram.png)

*圖片說明：載入字型範例圖示*

## 步驟 1：建立 Load Options 並啟用自訂字型設定  

當你想要 **設定字型設定** 時，第一件事就是實例化一個 `LoadOptions` 物件。於其中放入指向包含任何自訂 .ttf 或 .otf 檔案的資料夾的 `FontSettings` 實例。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // Step 1: Create load options and enable custom font settings
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // Point to a folder that holds extra fonts (optional but useful)
        loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", false);
```

**為什麼這很重要：** 預設情況下 Aspose.Words 只會檢查系統已安裝的字型。如果你的文件使用了存放於網路共享上的企業品牌字型，你必須告訴函式庫字型所在位置。這就是 **啟用自訂字型** 的核心。

## 步驟 2：附加警告處理程式以偵測缺少的字型  

如果省略警告處理，缺少的字形會悄悄被替換為備用字型——通常是 Times New Roman。這可能破壞品牌形象，甚至導致版面移位。要 **如何處理警告**，請附加一個回呼，檢查 `WarningType.FontSubstitution`。

```csharp
        // Step 2: Attach a warning handler to capture font substitution warnings
        loadOptions.WarningCallback = (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ Font substitution detected: {args.Description}");
        };
```

**小技巧：** `WarningCallback` 會對 *所有* 警告觸發，而不僅限於缺少字型。透過 `WarningType.FontSubstitution` 進行過濾，可保持輸出整潔，直接回應 **偵測缺少字型** 的需求。

## 步驟 3：使用已設定的選項載入文件  

現在我們已經準備好選項，終於可以 **載入字型** 到文件中。`Document` 建構子接受檔案路徑以及剛剛建立的 `LoadOptions`。

```csharp
        // Step 3: Load the document using the configured options
        Document doc = new Document(@"C:\Docs\DocWithMissingFont.docx", loadOptions);
```

如果來源檔案引用的字型不在系統資料夾 *或* 先前設定的自訂資料夾中，步驟 2 的警告回呼會在主控台印出有用的訊息。

## 步驟 4：驗證已載入的字型集合（可選但有助於了解）  

有時你會想再次確認實際解析到哪些字型。Aspose.Words 會公開你傳入的 `FontSettings`，因此你可以列舉已解析的字型來源。

```csharp
        // Step 4: (Optional) List all font sources that were used
        FontSourcesCollection sources = loadOptions.FontSettings.GetFontSources();
        Console.WriteLine("\nLoaded font sources:");
        foreach (var source in sources)
            Console.WriteLine($"- {source.GetType().Name}");
```

在載入後執行此程式碼片段會印出類似以下內容：

```
⚠️ Font substitution detected: Font 'Comic Sans MS' was substituted with 'Arial'.
Loaded font sources:
- FolderFontSource
- SystemFontSource
```

警告訊息證實我們成功 **偵測缺少字型**，而列表則顯示系統資料夾與自訂資料夾皆已被查詢。

## 步驟 5：儲存或轉譯文件  

文件載入且字型驗證完畢後，你可以繼續進行任何處理——儲存為 PDF、轉譯成影像，或操作 DOM。為了完整性，以下是一行程式碼示範，將結果儲存為 PDF：

```csharp
        // Step 5: Save the document as PDF (fonts now embedded where possible)
        doc.Save(@"C:\Docs\Result.pdf");
        Console.WriteLine("\n✅ Document saved as PDF.");
    }
}
```

當開啟 PDF 時，任何缺失的字形都會被你在主控台輸出中看到的備用字型取代。如果你將缺少的字型加入 `C:\MyCustomFonts`，重新執行程式後警告即會消失——證明 **啟用自訂字型** 確實有效。

---

## 完整範例

將下方整段程式碼複製到新的 Console 專案中，加入 Aspose.Words NuGet 套件，然後按 **Run**。依照你的環境調整檔案路徑。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Create load options and enable custom font settings
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };
        // Point to a folder with extra fonts (if you have any)
        loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", false);

        // 2️⃣ Attach a warning handler to capture font substitution warnings
        loadOptions.WarningCallback = (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ Font substitution: {args.Description}");
        };

        // 3️⃣ Load the document using the configured options
        Document doc = new Document(@"C:\Docs\DocWithMissingFont.docx", loadOptions);

        // 4️⃣ (Optional) List loaded font sources for debugging
        FontSourcesCollection sources = loadOptions.FontSettings.GetFontSources();
        Console.WriteLine("\nLoaded font sources:");
        foreach (var source in sources)
            Console.WriteLine($"- {source.GetType().Name}");

        // 5️⃣ Save as PDF – you’ll see the same warnings if fonts were missing
        doc.Save(@"C:\Docs\Result.pdf");
        Console.WriteLine("\n✅ PDF saved successfully.");
    }
}
```

### 預期輸出

```
⚠️ Font substitution: Font 'Papyrus' was substituted with 'Arial'.

Loaded font sources:
- FolderFontSource
- SystemFontSource

✅ PDF saved successfully.
```

如果將缺少的 `Papyrus.ttf` 檔案放入 `C:\MyCustomFonts`，再執行程式，警告訊息即會消失，證實已正確查詢自訂資料夾。

---

## 常見問題與注意事項

| Question | Answer |
|----------|--------|
| **如果我沒有警告回呼會怎樣？** | 文件仍會載入，但你不會知道何時發生了字型替換。加入回呼是最簡單的 **如何處理警告** 方法。 |
| **我可以從 zip 檔載入字型嗎？** | 可以——使用 `new FolderFontSource(zipPath, true)` 或自行實作 `IFontSource`。這仍屬於 **啟用自訂字型** 的範疇。 |
| **我需要在 PDF 中嵌入字型嗎？** | 在儲存之前設定 `doc.SaveOptions.PdfSaveOptions.EmbedFullFonts = true;`。嵌入字型可確保 PDF 在任何機器上顯示一致。 |
| **如果文件使用的字型受授權且不可再分發，該怎麼辦？** | 你仍然可以透過警告 *偵測* 缺少的字型，但除非取得授權，否則不應嵌入。可考慮改用相似的開源字型作為替代。 |

## 重點回顧

我們已說明在 .NET 中 **如何載入字型**，步驟如下：

1. 建立 `LoadOptions` 並設定 **字型設定**。  
2. 透過指向額外字型資料夾來 **啟用自訂字型**。  
3. 使用 `WarningCallback` **如何處理警告**，印出字型替換訊息。  
4. 透過過濾 `WarningType.FontSubstitution` **偵測缺少字型**。  
5. 儲存文件，確認已使用備用字型

## 接下來該學什麼？

以下教學涵蓋與本指南密切相關的主題，並以此為基礎延伸技術。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助你精通其他 API 功能，並在自己的專案中探索替代實作方式。

- [設定字型資料夾（系統與自訂資料夾}](/words/english/net/working-with-fonts/set-fonts-folders-system-and-custom-folder/)
- [如何在 Aspose.Words 中偵測字型 – 處理警告與設定](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [如何在 Aspose.Words 中捕獲字型 – 完整指南](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}