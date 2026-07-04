---
category: general
date: 2026-06-24
description: 本機 LLM 教學，示範如何呼叫本機 LLM、載入 Word 文件，並在 C# 中使用 AI 文法檢查執行文法校正。
draft: false
keywords:
- local llm tutorial
- run grammar check
- ai grammar check
- call local llm
- load word document
language: zh-hant
og_description: 本地 LLM 教學逐步說明如何呼叫本地 LLM、載入 Word 文件，並在 C# 中執行 AI 文法檢查。
og_title: 本地 LLM 教學 – 呼叫本地 LLM 並執行文法檢查
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: Local LLM tutorial that shows you how to call a local LLM, load a Word
    document and run grammar check using AI grammar check in C#.
  headline: Local LLM Tutorial – How to Call a Local LLM and Run Grammar Check
  type: TechArticle
- description: Local LLM tutorial that shows you how to call a local LLM, load a Word
    document and run grammar check using AI grammar check in C#.
  name: Local LLM Tutorial – How to Call a Local LLM and Run Grammar Check
  steps:
  - name: How to Run
    text: 1. Open a terminal in the project folder. 2. Run `dotnet run`. 3. Watch
      the console print the corrected text.
  - name: Can I use a different LLM brand?
    text: Absolutely. As long as the server respects the OpenAI v1 API schema, just
      change `Endpoint` and pick the corresponding `AiModelType` enum value (e.g.,
      `AiModelType.Llama2`). The rest of the code stays identical.
  - name: What if my document is huge (10 MB+)?
    text: Large payloads can exceed the default request size of many servers. Split
      the document into sections and call `CheckGrammar` per section, then concatenate
      the results. This also reduces the chance of a timeout.
  - name: How do I write the corrected output back to a `.docx` file?
    text: 'The `Document` class usually provides a `Save(string path, string content)`
      method. After you get `result.CorrectedText`, call:'
  - name: Is the dummy API key a security risk?
    text: No. The key is ignored by self‑hosted endpoints, but some SDKs enforce a
      non‑null string. Using a placeholder like `"dummy"` satisfies the SDK without
      exposing any secrets.
  type: HowTo
tags:
- LLM
- C#
- GrammarCheck
- AI
title: 本地 LLM 教學 – 如何調用本地 LLM 並執行文法檢查
url: /zh-hant/net/ai-powered-document-processing/local-llm-tutorial-how-to-call-a-local-llm-and-run-grammar-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 本地 LLM 教學 – 呼叫本地 LLM 並執行文法檢查

有沒有想過如何在不將任何資料傳到雲端的情況下 **執行文法檢查** Word 檔案？在本 **本地 llm 教學** 中，我們會連接自我託管的大型語言模型，載入 `.docx` 檔案，讓 AI 整理文字。無需 API 金鑰，無外部流量——全由你的機器自行處理。

我們會逐行說明程式碼，解釋每個部分為何重要，甚至示範如何處理常見的陷阱（例如檔案遺失或端點無法連線）。完成後，你將擁有一個可直接執行的 C# 主控台應用程式，使用本地託管的模型執行 **ai 文法檢查**。

> **你將獲得：** 完整、可執行的程式、每一步的清晰說明，以及將解決方案擴展至更大文件或不同 LLM 供應商的技巧。

![本地 llm 教學圖示](https://example.com/local-llm-tutorial-diagram.png "說明本地 llm 教學流程的圖表")

## 前置條件

- .NET 6.0 SDK 或更新版本（可從 Microsoft 官方網站下載）
- 本機執行的 LLM 伺服器，提供相容 OpenAI 的端點（例如 Ollama、LM Studio，或自訂的 FastAPI 包裝器）
- `AiGrammar` NuGet 套件（或任何提供 `LocalLargeLanguageModel`、`Document`、`AiModelType` 類別的函式庫）
- 一個範例 Word 文件（`input.docx`），放置於稍後會引用的資料夾中

就這樣——不需要額外的雲端憑證。

## 步驟 1：本地 LLM 教學 – 設定端點

我們首先需要一個 **call local llm** 物件，讓它知道要將請求發送到哪裡。可以把它想像成通話前必須撥打的電話號碼。

```csharp
using System;
using AiGrammar;   // Hypothetical library containing the LLM helpers

// Step 1: Configure a local large language model (LLM) endpoint
var llm = new LocalLargeLanguageModel
{
    Endpoint = "http://localhost:8000/v1",
    ApiKey = "dummy"   // Not required for self‑hosted models, but the property is mandatory
};
```

**為何重要：** 大多數 LLM SDK 需要符合 OpenAI API 規範的 HTTP 端點。將 `Endpoint` 指向 `http://localhost:8000/v1`，即告訴函式庫 **call local llm**，而非連接 OpenAI 伺服器。虛擬的 API 金鑰僅作為佔位符——某些客戶端不接受 null 值，所以我們提供一個無害的字串。

> **專業提示：** 若將 LLM 放在反向代理之後，將 `Endpoint` 設為代理的 URL，讓代理負責 TLS 終止。這樣可讓你的主控台應用程式保持簡潔且安全。

## 步驟 2：載入 Word 文件以進行文法檢查

現在模型已可連線，我們需要將 **load word document** 內容載入記憶體。`Document` 類別為我們抽象化 `.docx` 解析。

```csharp
// Step 2: Load the document you want to check
var docPath = @"C:\Projects\GrammarDemo\YOUR_DIRECTORY\input.docx";
if (!System.IO.File.Exists(docPath))
{
    Console.Error.WriteLine($"Error: The file '{docPath}' does not exist.");
    return;
}

var doc = new Document(docPath);
```

**為何重要：** 直接將二進位 `.docx` 檔案送給 LLM 會讓它困惑。`Document` 輔助工具會提取純文字並保留段落換行，為 **ai grammar check** 提供乾淨的輸入。存在性檢查可防止 `FileNotFoundException` 之類的錯誤導致程式崩潰。

## 步驟 3：使用 LLM 執行文法檢查

以下是本教學的核心：我們請求本地模型校對文字。`CheckGrammar` 方法隱藏了 HTTP 通訊細節，並回傳結果物件。

```csharp
// Step 3: Run the grammar‑check operation using the LLM
var result = doc.CheckGrammar(
    llm,
    AiModelType.Gpt4   // You can swap this for any model supported by AiModelType
);
```

**為何重要：** `AiModelType.Gpt4` 只是一個標籤，用來告訴遠端服務使用哪個提示範本。若使用較小的模型（例如 `Llama2`），請相應替換。函式庫會序列化文件文字，送至 `http://localhost:8000/v1/completions`，並解析校正後的輸出。

> **邊緣情況：** 若 LLM 超時，`CheckGrammar` 會拋出 `TimeoutException`。若預期處理大型文件或伺服器繁忙，請將呼叫包在 `try/catch` 區塊中。

## 步驟 4：輸出校正後的文字

最後，我們顯示整理過的版本。實際應用中你可能會將其寫回新的 `.docx` 檔案，但在本教學中只需在主控台輸出即可。

```csharp
// Step 4: Output the corrected text
Console.WriteLine("=== Corrected Text ===");
Console.WriteLine(result.CorrectedText);
```

**預期輸出**（假設原始檔案包含幾個刻意的錯誤）：

```
=== Corrected Text ===
The quick brown fox jumps over the lazy dog. 
She doesn't like apples, but she loves oranges.
```

如果 LLM 沒有發現任何錯誤，輸出將與輸入相同，這仍是一個有用的訊號。

## 完整範例程式

將所有部份組合起來，以下是完整程式碼，你可以直接複製貼上到新的主控台專案中：

```csharp
using System;
using AiGrammar;   // Replace with the actual namespace of your grammar library

namespace LocalLlmGrammarDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Configure the local LLM endpoint
            var llm = new LocalLargeLanguageModel
            {
                Endpoint = "http://localhost:8000/v1",
                ApiKey = "dummy"
            };

            // Path to the Word document you want to check
            var docPath = @"C:\Projects\GrammarDemo\YOUR_DIRECTORY\input.docx";

            // Verify the file exists before proceeding
            if (!System.IO.File.Exists(docPath))
            {
                Console.Error.WriteLine($"Error: The file '{docPath}' does not exist.");
                return;
            }

            // Load the document (this also extracts plain text)
            var doc = new Document(docPath);

            // Perform the AI grammar check using the local LLM
            GrammarCheckResult result;
            try
            {
                result = doc.CheckGrammar(llm, AiModelType.Gpt4);
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Grammar check failed: {ex.Message}");
                return;
            }

            // Show the corrected text
            Console.WriteLine("=== Corrected Text ===");
            Console.WriteLine(result.CorrectedText);
        }
    }
}
```

### 如何執行

1. 在專案資料夾中開啟終端機。  
2. 執行 `dotnet run`。  
3. 觀察主控台印出校正後的文字。

這就是全部 **local llm tutorial**，不到 100 行程式碼即可完成。

## 常見問題 (FAQ)

### 我可以使用不同的 LLM 品牌嗎？

當然可以。只要伺服器遵守 OpenAI v1 API 規範，變更 `Endpoint` 並選擇相對應的 `AiModelType` 列舉值（例如 `AiModelType.Llama2`），其餘程式碼保持不變。

### 如果我的文件很大（10 MB+）怎麼辦？

大型負載可能超過許多伺服器的預設請求大小。將文件切分為多個段落，對每個段落呼叫 `CheckGrammar`，再將結果串接。這同時也降低超時的機會。

### 如何將校正後的輸出寫回 `.docx` 檔案？

`Document` 類別通常提供 `Save(string path, string content)` 方法。取得 `result.CorrectedText` 後，呼叫：

```csharp
doc.Save(@"C:\Projects\GrammarDemo\output_corrected.docx", result.CorrectedText);
```

請參考函式庫文件以取得正確的簽名。

### 虛擬 API 金鑰會有安全風險嗎？

不會。此金鑰會被自我託管的端點忽略，但某些 SDK 需要非 null 的字串。使用類似 `"dummy"` 的佔位符即可滿足 SDK 要求，且不會洩漏任何機密。

## 往後步驟與相關主題

- **Fine‑tune your local LLM** 用於領域特定的文法（例如法律或醫療寫作）。  
- **Run a batch job** 處理整個 Word 檔案資料夾——適合出版流程。  
- 若希望使用者輸入時即時建議，可探索 **streaming responses**。  
- 將此與 **spell‑checking libraries** 結合，形成雙層品質門檻。

上述想法皆建立在本 **local llm tutorial** 的核心概念之上，你會在整篇中看到相同的模式——**call local llm**、**load word document**、**run grammar check**、以及 **handle results**——不斷重複。

---

*祝程式開發愉快！若遇到問題，請在下方留言，我們會一起排除故障。*

## 接下來該學什麼？

以下教學涵蓋與本指南緊密相關的主題，並以此為基礎。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助你精通更多 API 功能，並在自己的專案中探索替代實作方式。

- [在 Word 文件中使用編碼載入](/words/english/net/programming-with-loadoptions/load-with-encoding/)
- [載入加密的 Word 文件](/words/english/net/programming-with-loadoptions/load-encrypted-document/)
- [修復損壞的 DOCX – 開啟與載入 Word 文件](/words/english/python-net/document-operations/recover-corrupted-docx-open-load-word-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}