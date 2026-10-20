---
category: general
date: 2026-08-07
description: 使用 C# 的 AI 文件翻譯將 docx 轉譯為法文。了解如何設定目標語言、翻譯 Word 文件，以及高效批次翻譯文件。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate docx to french
- translate word document
- ai document translation
- set target language
- batch translate documents
language: zh-hant
lastmod: 2026-08-07
og_description: 使用 AI 將 docx 轉譯成法文。本指南說明如何設定目標語言、翻譯 Word 文件，以及使用 C# 批量翻譯文件。
og_image_alt: Screenshot of C# code translating a DOCX file to French
og_title: 使用 AI 將 docx 轉譯成法文 – 完整 C# 指南
schemas:
- author: GroupDocs
  dateModified: '2026-08-07'
  description: Translate docx to French using AI document translation in C#. Learn
    how to set target language, translate word document, and batch translate documents
    efficiently.
  headline: Translate docx to French with AI in C#
  type: TechArticle
tags:
- C#
- AI translation
- Office automation
title: 在 C# 中使用 AI 將 docx 翻譯成法文
url: /zh-hant/net/ai-powered-document-processing/translate-docx-to-french-with-ai-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 AI 在 C# 中將 docx 翻譯成法文

如果您需要快速 **將 docx 翻譯成法文**，本指南將展示一個完整的 C# 解決方案，利用 AI 文件翻譯。您將看到如何設定目標語言、翻譯 Word 文件，甚至在不離開 IDE 的情況下批次翻譯文件。

本教學涵蓋您開始所需的一切：必須的 NuGet 套件、Google AI 供應商的設定，以及可直接執行的程式碼範例。完成後，您將能夠在單一方法呼叫中將任何 `.docx` 檔案翻譯成法文。

## 前置條件

* 已安裝 .NET 6.0 SDK 或更新版本  
* Google Cloud Translation API 金鑰（`ApiKey` 值）  
* `GroupDocs.Translator` NuGet 套件（或任何提供 `AiTranslatorOptions` 與 `DocumentTranslator` 的函式庫）  

這些前置條件可確保 **ai document translation** 程式碼能編譯並在無外部相依性的情況下執行。

## 第一步：安裝翻譯函式庫

在專案資料夾中開啟終端機並執行：

```bash
dotnet add package GroupDocs.Translator
```

此套件會加入在教學後續使用的 `AiTranslatorOptions`、`AiProvider`、`Language` 與 `DocumentTranslator` 類型。

## 第二步：載入來源 DOCX 檔案

```csharp
using GroupDocs.Translator;
using GroupDocs.Translator.Options;

// Load the Word document you want to translate
Document sourceDoc = new Document("YOUR_DIRECTORY/input.docx");
```

`Document` 代表一個 Word 檔案（`.docx`）。一次載入檔案後即可重複使用同一個物件進行多次翻譯，這在 **批次翻譯文件** 時非常有用。

## 第三步：設定 AI 翻譯選項（設定目標語言）

```csharp
// Configure the AI provider and target language
AiTranslatorOptions translatorOptions = new AiTranslatorOptions
{
    Provider        = AiProvider.Google,   // Use Google Translation API
    ApiKey          = "YOUR_GOOGLE_API_KEY",
    TargetLanguage  = Language.French     // Set target language to French
};
```

**設定目標語言** 步驟告訴服務要翻譯成哪種語言。`Language.French` 是函式庫認可的列舉值，但您可以改為任何支援的語言代碼。

## 第四步：執行翻譯

```csharp
// Translate the entire document using the configured options
DocumentTranslator.Translate(sourceDoc, translatorOptions);
```

`DocumentTranslator.Translate` 會在 **翻譯 Word 文件** 的過程中處理每個段落、表格、頁首與頁尾。函式庫負責將文字傳送至 Google API，並以法文版本取代原始內容。

## 第五步：儲存已翻譯的 DOCX

```csharp
// Save the translated document
sourceDoc.Save("YOUR_DIRECTORY/Translated_French.docx");
```

翻譯完成後，同一個 `Document` 實例現在包含法文文字。儲存它會產生一個新檔案，您可以在 Microsoft Word 或任何相容的檢視器中開啟。

## 完整可執行範例

```csharp
using System;
using GroupDocs.Translator;
using GroupDocs.Translator.Options;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the source document
        Document sourceDoc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Set up AI translation options (Google provider, French target)
        AiTranslatorOptions translatorOptions = new AiTranslatorOptions
        {
            Provider        = AiProvider.Google,
            ApiKey          = "YOUR_GOOGLE_API_KEY",
            TargetLanguage  = Language.French
        };

        // 3️⃣ Translate the entire document
        DocumentTranslator.Translate(sourceDoc, translatorOptions);

        // 4️⃣ Save the translated file
        sourceDoc.Save("YOUR_DIRECTORY/Translated_French.docx");

        Console.WriteLine("✅ Document translated to French and saved successfully.");
    }
}
```

**預期輸出**（顯示於主控台）：

```
✅ Document translated to French and saved successfully.
```

在 Word 中開啟 `Translated_French.docx`，確認所有英文句子已被法文等價句取代。

## 可選：批次翻譯多個 DOCX 檔案

如果您需要 **批次翻譯文件**，請將先前的邏輯包在迴圈中：

```csharp
string[] files = Directory.GetFiles("YOUR_DIRECTORY", "*.docx");

foreach (var file in files)
{
    Document doc = new Document(file);
    DocumentTranslator.Translate(doc, translatorOptions);
    string outputPath = Path.Combine(
        "YOUR_DIRECTORY",
        Path.GetFileNameWithoutExtension(file) + "_French.docx");
    doc.Save(outputPath);
    Console.WriteLine($"Translated {Path.GetFileName(file)} → {Path.GetFileName(outputPath)}");
}
```

此程式碼會遍歷資料夾中的每個 `.docx` 檔案，**將 docx 翻譯成法文**，並以 `_French` 加在檔名後儲存新版本。相同的 `translatorOptions` 物件會被重複使用，減少 API 金鑰處理的負擔。

## 常見問題與避免方法

| 問題 | 發生原因 | 解決方式 |
|------|----------|----------|
| **API 金鑰無效** | Google 端點回傳 401 錯誤。 | 確認 `YOUR_GOOGLE_API_KEY` 已啟用且已開通 Cloud Translation API。 |
| **大型文件超出配額** | Google 對每次請求的大小有限制。 | 在呼叫 `Translate` 前，將文件切分成較小的區塊（例如逐段落）。 |
| **格式遺失** | 某些函式庫會剝除複雜的 Word 樣式。 | 使用最新版本的 `GroupDocs.Translator`，它能保留大部分格式。 |
| **不支援的語言** | `Language.French` 為有效值，但拼寫錯誤會導致例外。 | 使用 `Language` 列舉值，或在函式庫接受字串時使用 ISO‑639‑1 代碼 `"fr"`。 |

## 專業提示：快取翻譯結果

當您 **批次翻譯文件** 且其中包含重複句子時，請將 API 回應快取於字典中：

```csharp
var cache = new Dictionary<string, string>();

string TranslateWithCache(string text)
{
    if (cache.TryGetValue(text, out var cached)) return cached;
    string translated = /* call Google API */;
    cache[text] = translated;
    return translated;
}
```

快取可減少 API 呼叫、節省成本，並加速整體批次處理。

## 結論

您現在擁有一套完整、可投入生產的方式，使用 C# 中的 AI 文件翻譯 **將 docx 翻譯成法文**。本指南說明了如何 **設定目標語言**、**翻譯 Word 文件**，以及以最少程式碼 **批次翻譯文件**。

接下來，您可以透過變更 `TargetLanguage` 來探索其他目標語言，或將翻譯器整合至 Web API，提供使用者上傳即時翻譯。若需更深入的客製化，請參閱 `GroupDocs.Translator` 文件，了解如何處理表格、圖片與自訂格式。

祝開發順利！

## 接下來該學什麼？

以下教學涵蓋與本指南技術密切相關的主題。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在專案中探索替代實作方式。

- [將文件另存為 TXT – 完整 C# 教學：將 DOCX 轉換為純文字](/words/english/net/programming-with-txtsaveoptions/save-document-as-txt-complete-c-guide-to-convert-docx-to-pla/)
- [在 Word 文件中使用佈景主題與樣式](/words/english/net/programming-with-styles-and-themes/)
- [設定 Word 文件的佈景主題屬性](/words/english/net/programming-with-styles-and-themes/set-theme-properties/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}