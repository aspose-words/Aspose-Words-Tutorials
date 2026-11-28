---
category: general
date: 2026-08-23
description: 在 C# 中使用 Aspose.Words AI Translator 及 Google 提供者將字串翻譯成西班牙文。遵循逐步指南，快速在
  C# 中翻譯字串。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate string to spanish
- translate string in c#
language: zh-hant
lastmod: 2026-08-23
og_description: 使用 Aspose.Words AI 在 C# 中將字串翻譯成西班牙文。本教學展示如何設定 Google 供應商、翻譯字串以及顯示結果。
og_image_alt: Console screenshot showing translate string to spanish output in a C#
  application
og_title: 在 C# 中將字串翻譯成西班牙文 – 完整程式碼範例
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Translate string to Spanish in C# using Aspose.Words AI Translator
    and Google provider. Follow the step‑by‑step guide to translate string in C# quickly.
  headline: Translate string to Spanish in C# with Aspose.Words AI
  type: TechArticle
- description: Translate string to Spanish in C# using Aspose.Words AI Translator
    and Google provider. Follow the step‑by‑step guide to translate string in C# quickly.
  name: Translate string to Spanish in C# with Aspose.Words AI
  steps:
  - name: '**Obtain an API key** from the Google Cloud Console → APIs & Services →
      Credentials.'
    text: '**Obtain an API key** from the Google Cloud Console → APIs & Services →
      Credentials.'
  - name: '**Enable the Cloud Translation API** for your project.'
    text: '**Enable the Cloud Translation API** for your project.'
  - name: Store the key securely (environment variable, secret manager, etc.). The
      example uses a literal for clarity, but production code should avoid hard‑coding
      secrets.
    text: Store the key securely (environment variable, secret manager, etc.). The
      example uses a literal for clarity, but production code should avoid hard‑coding
      secrets.
  - name: Open a terminal in the project folder.
    text: Open a terminal in the project folder.
  - name: Execute `dotnet run`.
    text: Execute `dotnet run`.
  - name: Confirm that the console displays the Spanish phrase.
    text: Confirm that the console displays the Spanish phrase.
  type: HowTo
tags:
- Aspose.Words
- C#
- Localization
title: 使用 Aspose.Words AI 在 C# 中將字串翻譯成西班牙語
url: /zh-hant/net/ai-powered-document-processing/translate-string-to-spanish-in-c-with-aspose-words-ai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 中使用 Aspose.Words AI 將字串翻譯成西班牙文

如果您需要在 .NET 應用程式中 **將字串翻譯成西班牙文**，本指南將逐步說明如何操作。您將看到一個完整、可執行的範例，建立翻譯器、呼叫 Google 服務，並輸出西班牙文文字。

本教學亦涵蓋使用 Aspose.Words AI 函式庫 **在 C# 中翻譯字串**，讓您能直接在程式碼中整合本地化，而無需外部腳本。

## 您需要的環境

- .NET 6.0 SDK 或更新版本（此程式碼可在 .NET Core 與 .NET Framework 上編譯）
- 有效的 Google Cloud Translation API 金鑰
- NuGet 套件 `Aspose.Words.AI`（使用 `dotnet add package Aspose.Words.AI` 安裝）
- 代碼編輯器或 IDE，例如 Visual Studio 2022

這些前置條件可確保範例即開即用。

## 使用 Aspose.Words AI 將字串翻譯成西班牙文

本節會建立配置為 Google 提供者的 `Translator` 物件。該提供者負責向 Google 翻譯端點發送 HTTP 請求。

```csharp
using System;
using Aspose.Words.AI;          // Namespace for Translator
using Aspose.Words.AI.Translator; // Contains TranslationProvider and Language enums

class Program
{
    static void Main()
    {
        // Step 1: Create a translator that uses Google as the provider
        var translator = new Translator(
            provider: TranslationProvider.Google,
            apiKey: "YOUR_GOOGLE_KEY");   // Replace with your real API key

        // Step 2: Translate the source text into Spanish
        string spanishText = translator.Translate(
            "Hello world",
            Language.Spanish);

        // Step 3: Use the translated text (display it in the console)
        Console.WriteLine(spanishText);
    }
}
```

**為什麼這樣可行：**  
- `Translator` 抽象化 HTTP 呼叫，並使用您提供的 API 金鑰處理驗證。  
- `TranslationProvider.Google` 告訴 SDK 將請求導向 Google Cloud Translation。  
- `Language.Spanish` 選擇目標語言代碼（`es`）。  
- `Translate` 方法回傳翻譯後的字串，您可在應用程式的任何地方使用。

## 設定 Google 翻譯提供者

1. **從 Google Cloud Console 取得 API 金鑰** → APIs & Services → Credentials。  
2. **為您的專案啟用 Cloud Translation API**。  
3. 安全地儲存金鑰（環境變數、密鑰管理服務等）。範例為了說明使用文字常數，但正式程式碼應避免硬編碼機密。

## 在 C# 中翻譯字串 – 步驟說明

| 步驟 | 操作 | 原因 |
|------|--------|--------|
| 1 | 建立 `Translator` 並使用 `TranslationProvider.Google` | 將 SDK 連接至 Google 服務 |
| 2 | 呼叫 `Translate(source, Language.Spanish)` | 傳送來源文字並取得西班牙文結果 |
| 3 | 使用 `Console.WriteLine` 輸出結果 | 驗證翻譯並示範使用方式 |

執行程式會輸出：

```
¡Hola mundo!
```

> **注意：** 具體輸出可能會因 Google 的翻譯模型略有差異（例如「Hola mundo」與「¡Hola mundo!」），兩者皆為有效的西班牙文等價。

## 執行並驗證輸出

1. 在專案資料夾中開啟終端機。  
2. 執行 `dotnet run`。  
3. 確認主控台顯示西班牙語句子。

如果主控台顯示類似 *“401 Unauthorized”* 的錯誤，請再次確認 API 金鑰正確且已為專案啟用 Cloud Translation API。

## 常見陷阱與最佳實踐

- **API 配額限制** – Google 依計費帳戶實施請求上限。請在 Cloud Console 監控使用量，以免發生意外的節流。  
- **網路延遲** – 翻譯呼叫為遠端 HTTP 請求。建議快取常用的翻譯字串以降低延遲。  
- **編碼問題** – SDK 使用 UTF‑8 字串；確保您的原始檔案以 UTF‑8 編碼儲存，以保留特殊字元。  
- **錯誤處理** – 將 `Translate` 呼叫包裹於 try‑catch 區塊，以處理 `ApiException` 並提供備援文字。

```csharp
try
{
    string spanishText = translator.Translate("Hello world", Language.Spanish);
    Console.WriteLine(spanishText);
}
catch (ApiException ex)
{
    Console.Error.WriteLine($"Translation failed: {ex.Message}");
    // Fallback to original text
    Console.WriteLine("Hello world");
}
```

## 擴充範例

- **翻譯成其他語言** – 將 `Language.Spanish` 替換為 `Language.French`、`Language.German` 等。  
- **批次翻譯** – 在迴圈中呼叫 `Translate` 以處理字串清單。  
- **整合至 UI** – 在 ASP.NET Core Razor 頁面、Windows Forms 或 WPF 應用程式中使用翻譯後的字串。

## 結論

現在您已了解如何在 C# 中使用 Aspose.Words AI 與 Google 翻譯服務 **將字串翻譯成西班牙文**。完整解決方案涵蓋提供者設定、翻譯呼叫、錯誤處理與輸出驗證。

接下來，您可以嘗試其他語言、快取結果以提升效能，並將翻譯器整合至更大的本地化工作流程中。

--- 

*想要本地化更多內容嗎？請參考下一篇教學 **在 C# 中使用 Azure Cognitive Services 翻譯字串**，了解另一個雲端提供者。*


## 接下來您可以學習什麼？

以下教學涵蓋與本指南技術緊密相關的主題，並在此基礎上延伸。每個資源皆提供完整可執行的程式碼範例與步驟說明，協助您精通更多 API 功能，並在專案中探索替代實作方式。

- [以字串取代](/words/spanish/net/find-and-replace-text/replace-with-string/)
- [以字串取代](/words/english/net/find-and-replace-text/replace-with-string/)
- [使用 Aspose.Words 建立 Word 文件 – 步驟說明指南](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}