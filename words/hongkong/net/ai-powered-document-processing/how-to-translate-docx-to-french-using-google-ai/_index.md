---
category: general
date: 2026-11-18
description: 學習如何使用 Google AI 翻譯將 docx 轉譯成法文，翻譯整份文件，並在僅三個步驟內儲存翻譯後的文件。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate docx to french
- google ai translation
- translate entire document
- save translated document
- how to translate docx
language: zh-hant
lastmod: 2026-11-18
og_description: 使用 Google AI 翻譯即時將 docx 轉譯成法文。按照本指南即可輕鬆翻譯整份文件並儲存翻譯後的文件。
og_image_alt: Screenshot showing a DOCX file translated to French using Google AI
og_title: 使用 Google AI 將 docx 轉譯成法文 – 快速指南
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Learn how to translate docx to French with Google AI translation, translate
    entire document, and save translated document in just three steps.
  headline: How to translate docx to French using Google AI
  type: TechArticle
- description: Learn how to translate docx to French with Google AI translation, translate
    entire document, and save translated document in just three steps.
  name: How to translate docx to French using Google AI
  steps:
  - name: 'Create a new console project:'
    text: 'Create a new console project:'
  - name: 'Add the NuGet packages that the tutorial relies on:'
    text: 'Add the NuGet packages that the tutorial relies on:'
  - name: '(Optional) If you prefer a higher‑level wrapper, you can also install `GroupDocs.Translator`:'
    text: '(Optional) If you prefer a higher‑level wrapper, you can also install `GroupDocs.Translator`:'
  type: HowTo
tags:
- C#
- Google AI
- Document translation
- Localization
title: 如何使用 Google AI 將 docx 翻譯成法文
url: /zh-hant/net/ai-powered-document-processing/how-to-translate-docx-to-french-using-google-ai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Google AI 將 docx 翻譯成法文

如果您需要 **將 docx 翻譯成法文**，Google AI 翻譯讓您只需幾行 C# 程式碼即可翻譯整個文件。本教學將精確示範如何翻譯 DOCX 檔案、翻譯整個文件內容，並以可靠的方式儲存翻譯後的文件。

您將學習如何設定 Google Cloud Translation 客戶端、載入 Word 檔案、呼叫 API 以翻譯每個段落，最後執行 **儲存翻譯文件** 步驟。無需外部腳本或手動複製貼上——所有操作皆在您的 .NET 應用程式內執行。

## 您需要的條件

* 已安裝 .NET 6.0 SDK 或更新版本  
* 已啟用 **Cloud Translation API** 的 Google Cloud 專案  
* 服務帳戶 JSON 金鑰檔案（從 Google Cloud 控制台下載）  
* Visual Studio 2022（或您偏好的任何 C# IDE）  

這些前置條件可確保 **google ai translation** 呼叫成功，且您能使用 Open XML SDK 讀寫 DOCX 檔案。

## 設定專案並安裝所需 SDK

1. 建立一個新的主控台專案：

   ```bash
   dotnet new console -n DocxFrenchTranslator
   cd DocxFrenchTranslator
   ```

2. 加入本教學所依賴的 NuGet 套件：

   ```bash
   dotnet add package Google.Cloud.Translate.V3
   dotnet add package DocumentFormat.OpenXml
   ```

   *`Google.Cloud.Translate.V3`* 提供 **google ai translation** 客戶端，而 *`DocumentFormat.OpenXml`* 讓您在不需要安裝 Microsoft Office 的情況下處理 DOCX 檔案。

3. (可選) 若您偏好較高層級的封裝，也可以安裝 `GroupDocs.Translator`：

   ```bash
   dotnet add package GroupDocs.Translator
   ```

   以下的程式碼範例兩種方式皆可使用；此處完整展示 Open XML 版本以保持透明。

## 載入來源 DOCX 檔案

第一個功能步驟是讀取您想要翻譯的 Word 文件。使用 Open XML SDK，您可以將每個段落的文字提取到清單中。

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using DocumentFormat.OpenXml.Packaging;
using DocumentFormat.OpenXml.Wordprocessing;

namespace DocxFrenchTranslator
{
    /// <summary>
    /// Reads all paragraph texts from a DOCX file.
    /// </summary>
    public static class DocxReader
    {
        public static List<string> GetParagraphs(string path)
        {
            var paragraphs = new List<string>();

            using (WordprocessingDocument wordDoc = WordprocessingDocument.Open(path, false))
            {
                Body body = wordDoc.MainDocumentPart.Document.Body;
                foreach (Paragraph para in body.Elements<Paragraph>())
                {
                    paragraphs.Add(para.InnerText);
                }
            }

            return paragraphs;
        }
    }
}
```

**為什麼這很重要：** 只載入一次檔案並將文字保留在記憶體中，使您能以每段落一次 API 呼叫的方式 **翻譯整個文件** 內容，避免重複的檔案 I/O。

## 執行 Google AI 翻譯

現在您已取得原始段落，呼叫 Translation API 將每個字串從英文（或任何來源語言）轉換為法文。若傳入 `null`，客戶端會自動偵測來源語言。

```csharp
using Google.Cloud.Translate.V3;
using System.Collections.Generic;
using System.Threading.Tasks;

namespace DocxFrenchTranslator
{
    /// <summary>
    /// Handles translation using Google Cloud Translation (v3).
    /// </summary>
    public static class Translator
    {
        private static readonly TranslationServiceClient client;

        static Translator()
        {
            // The GOOGLE_APPLICATION_CREDENTIALS environment variable should point to your JSON key.
            client = TranslationServiceClient.Create();
        }

        /// <summary>
        /// Translates a list of strings to French.
        /// </summary>
        public static async Task<List<string>> TranslateToFrenchAsync(List<string> texts)
        {
            var request = new TranslateTextRequest
            {
                Parent = $"projects/{client.ProjectId}/locations/global",
                TargetLanguageCode = "fr",
                // SourceLanguageCode can be omitted for auto‑detection.
            };

            // Add all texts to the request.
            request.Contents.AddRange(texts);

            // Execute the translation.
            TranslateTextResponse response = await client.TranslateTextAsync(request);

            var translated = new List<string>();
            foreach (Translation translation in response.Translations)
            {
                translated.Add(translation.TranslatedText);
            }

            return translated;
        }
    }
}
```

**為什麼這很重要：** 在批次請求中使用 **google ai translation** 可降低延遲與成本，較之於每段落一次呼叫的迴圈。此方法亦示範了以程式方式 **如何翻譯 docx**。

## 使用翻譯後的文字建立新 DOCX

取得法文字串後，將它們寫回全新的 DOCX 檔案。以下的輔助類別會從翻譯後的段落建立新文件。

```csharp
using DocumentFormat.OpenXml.Packaging;
using DocumentFormat.OpenXml.Wordprocessing;

namespace DocxFrenchTranslator
{
    /// <summary>
    /// Writes a list of paragraphs to a new DOCX file.
    /// </summary>
    public static class DocxWriter
    {
        public static void Write(string outputPath, List<string> frenchParagraphs)
        {
            // Ensure the directory exists.
            Directory.CreateDirectory(Path.GetDirectoryName(outputPath)!);

            // Create a new document.
            using (WordprocessingDocument wordDoc = WordprocessingDocument.Create(outputPath, DocumentFormat.OpenXml.WordprocessingDocumentType.Document))
            {
                MainDocumentPart mainPart = wordDoc.AddMainDocumentPart();
                mainPart.Document = new Document();
                Body body = mainPart.Document.AppendChild(new Body());

                foreach (string paraText in frenchParagraphs)
                {
                    Paragraph para = new Paragraph(new Run(new Text(paraText)));
                    body.AppendChild(para);
                }

                mainPart.Document.Save();
            }
        }
    }
}
```

## 組合全部 – 完整程式

以下是完整、可執行的主控台應用程式，將先前的程式碼片段結合起來。它示範了 **將 docx 翻譯成法文**、執行 **google ai translation**，最後 **儲存翻譯文件**。

```csharp
using System;
using System.IO;
using System.Threading.Tasks;

namespace DocxFrenchTranslator
{
    class Program
    {
        static async Task Main(string[] args)
        {
            // ------------------------------------------------------------------
            // 1️⃣ Load the source document
            // ------------------------------------------------------------------
            string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
            if (!File.Exists(inputPath))
            {
                Console.WriteLine($"Input file not found: {inputPath}");
                return;
            }

            var originalParagraphs = DocxReader.GetParagraphs(inputPath);
            Console.WriteLine($"Loaded {originalParagraphs.Count} paragraphs from input.docx.");

            // ------------------------------------------------------------------
            // 2️⃣ Translate the entire document to French using Google AI
            // ------------------------------------------------------------------
            var frenchParagraphs = await Translator.TranslateToFrenchAsync(originalParagraphs);
            Console.WriteLine("Translation completed – document is now in French.");

            // ------------------------------------------------------------------
            // 3️⃣ Save the translated document
            // ------------------------------------------------------------------
            string outputPath = Path.Combine(Environment.CurrentDirectory, "output_fr.docx");
            DocxWriter.Write(outputPath, frenchParagraphs);
            Console.WriteLine($"Saved translated document to: {outputPath}");
        }
    }
}
```

### 預期輸出

執行程式 (`dotnet run`) 後，主控台會印出類似以下的內容：

```
Loaded 12 paragraphs from input.docx.
Translation completed – document is now in French.
Saved translated document to: C:\Path\To\Your\Project\output_fr.docx
```

使用 Word、LibreOffice 或任何檢視器開啟 `output_fr.docx`，您會看到原本的英文內容已被法文翻譯取代。

## 將 docx 翻譯成法文 – 步驟概覽

### 1. 安全設定 Google 憑證

* 將服務帳戶 JSON 檔案放在安全的位置，例如

## 接下來您應該學習什麼？

以下教學涵蓋與本指南緊密相關的主題，並以此為基礎。每個資源皆提供完整可運作的程式碼範例與步驟說明，協助您精通更多 API 功能，並在自己的專案中探索其他實作方式。

- [如何在 C# 中使用 Google AI 儲存翻譯後的 Word 文件](/words/english/net/ai-powered-document-processing/how-to-save-translated-word-document-in-c-with-google-ai/)
- [如何將 DOCX 翻譯成法文並自動化文件翻譯](/words/english/net/ai-powered-document-processing/how-to-translate-docx-to-french-and-automate-document-transl/)
- [使用 Aspose.Words 與 Google API 將 docx 翻譯成法文](/words/english/net/ai-powered-document-processing/translate-docx-to-french-with-aspose-words-and-google-api/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}