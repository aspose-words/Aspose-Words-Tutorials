---
category: general
date: 2026-05-04
description: 如何使用 LLM 與 Aspose 編輯文件 – 學習取代段落文字、連接本地 LLM，並使用 AI 重寫文字。
draft: false
keywords:
- how to use llm
- replace paragraph text
- connect to local llm
- rewrite text using ai
- edit document aspose
language: zh-hant
og_description: 如何使用 LLM 透過 Aspose 編輯文件。本指南說明如何連接本地 LLM、取代段落文字，並使用 AI 重寫文字。
og_title: 如何在 Aspose.Words 中使用 LLM – 用 C# 重寫段落
tags:
- Aspose.Words
- C#
- AI
- LLM
title: 如何在 Aspose.Words 中使用 LLM – 用 C# 重寫段落
url: /zh-hant/net/ai-powered-document-processing/how-to-use-llm-with-aspose-words-rewrite-paragraphs-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Aspose.Words 中使用 LLM – 以 C# 重寫段落

有沒有想過 **how to use LLM** 來在不手動開啟的情況下潤飾 Word 文件？你並不是唯一有此想法的人。許多開發者在需要以程式方式 *replace paragraph text* 時會卡住，因為缺乏乾淨的 AI 驅動工作流程。  

在本教學中，我們將連接本地大型語言模型，將 `.docx` 檔案中的片段餵入模型，請它 **rewrite text using AI**，最後儲存更新後的文件——全部使用 Aspose.Words。完成後，你將擁有一個可直接執行的 C# 主控台應用程式，示範整個流程。

> **你將獲得：** 完整、可執行的範例、每一步的說明、邊緣情況的提示，以及擴充解決方案的想法。

## 需要的環境

- **.NET 6+** (或 .NET Framework 4.7.2 – 程式碼兩者皆可執行)
- **Aspose.Words for .NET** (NuGet 套件 `Aspose.Words`)
- 一個 **local LLM server**，提供簡易的 HTTP `/generate` 端點（例如 Ollama、LMStudio，或自訂的 Flask 服務）
- 具備基本的 C# 與 HTTP 客戶端程式碼的熟悉度  

不需要額外的 SDK；其他所有內容都在我們將共同編寫的程式碼中。

## 步驟 1：How to Use LLM to Replace Paragraph Text

我們首先要做的事是找出想要修改的段落。Aspose.Words 透過提供豐富的物件模型，使這件事變得非常簡單。

```csharp
using Aspose.Words;
using Aspose.Words.AI;   // Imaginary namespace for illustration – replace with actual if needed
using System.Net.Http;
using System.Text;
using System.Text.Json;

// Load the source document
Document document = new Document("YOUR_DIRECTORY/input.docx");

// Grab the third paragraph (zero‑based index)
Paragraph targetParagraph = document.FirstSection.Body.Paragraphs[2];

// Show the original text in the console – handy for debugging
Console.WriteLine("Original paragraph:");
Console.WriteLine(targetParagraph.GetText());
```

**為什麼這很重要：**  
選擇正確的節點可避免意外覆寫標題或表格。透過使用 **replace paragraph text** 方法，我們在保持文件結構完整的同時，只修改我們關心的內容。

> **專業提示：** 若文件中有長度可變的區段，請使用 `document.GetChildNodes(NodeType.Paragraph, true)` 搭配 LINQ 依文字或樣式定位段落。

## 步驟 2：Connect to a Local LLM Endpoint

現在我們已取得文字，需要將它送到 LLM。範例使用一個簡易的封裝類別 `LocalLargeLanguageModel`，隱藏 HTTP 的細節。如果你願意，也可以改用 `HttpClient` 呼叫。

```csharp
/// <summary>
/// Minimal wrapper around a local LLM HTTP API.
/// Assumes the API accepts a JSON payload { "prompt": "..."} and returns { "response": "..." }.
/// </summary>
public class LocalLargeLanguageModel
{
    private readonly HttpClient _client;
    private readonly string _endpoint;

    public LocalLargeLanguageModel(string endpoint)
    {
        _endpoint = endpoint.TrimEnd('/');
        _client = new HttpClient();
    }

    public string GenerateText(string prompt)
    {
        var payload = new { prompt };
        var content = new StringContent(JsonSerializer.Serialize(payload), Encoding.UTF8, "application/json");

        // Synchronous call for brevity – in production use async/await
        var response = _client.PostAsync($"{_endpoint}/generate", content).Result;
        response.EnsureSuccessStatusCode();

        var json = response.Content.ReadAsStringAsync().Result;
        var result = JsonSerializer.Deserialize<Dictionary<string, string>>(json);
        return result?["response"] ?? string.Empty;
    }
}

// Step 2: Instantiate the LLM client pointing at localhost
var localLlm = new LocalLargeLanguageModel("http://localhost:5000");
```

**為什麼要這樣連接：**  
使用 **connect to local llm** 的設定可消除延遲、將資料保留在本地，且避免 API 成本。此封裝也讓後續程式碼更簡潔，讓我們能專注於 **rewrite text using ai** 的邏輯。

## 步驟 3：Rewrite Text Using AI with Aspose.Words

取得段落文字且 LLM 已就緒後，我們會構造一個提示詞，告訴模型我們的具體需求——以正式語氣重寫。你也可以調整提示詞以符合其他風格（友善、技術性等）。

```csharp
// Build the prompt – notice the newline for readability
string prompt = $"Rewrite the following in a formal tone:\n{targetParagraph.GetText()}";

// Ask the LLM to generate the revised version
string revisedText = localLlm.GenerateText(prompt);

// Show the AI‑generated text
Console.WriteLine("\nRevised paragraph:");
Console.WriteLine(revisedText);
```

**為什麼這有效：**  
LLM 以提示詞驅動；提供明確指示（「Rewrite … in a formal tone」）即可得到一致的結果。**rewrite text using ai** 步驟是本教學的核心——展示了如何將 AI 直接嵌入文件工作流程。

## 步驟 4：Edit the Document and Save Changes

現在我們將原本的 run 替換為新內容。Aspose.Words 以 `Run` 物件儲存文字，先清除它們可避免遺留的格式化痕跡。

```csharp
// Clear existing runs (pieces of text) from the paragraph
targetParagraph.Runs.Clear();

// Append a new Run containing the revised text
targetParagraph.AppendChild(new Run(document, revisedText));

// Save the updated document
document.Save("YOUR_DIRECTORY/output.docx");

// Confirmation
Console.WriteLine("\nDocument saved as output.docx");
```

**邊緣情況說明：**  
如果原始段落包含混合格式（粗體、斜體），你可能想保留樣式。此時，建立新的 `Run`，複製原始的 `Font` 設定，然後將其 `Text` 設為 `revisedText`。

## 完整範例程式

以下是完整程式碼，你可以直接複製貼上到 Console 專案。請先安裝 Aspose.Words NuGet 套件（`dotnet add package Aspose.Words`）。

```csharp
// ---------------------------------------------------------------
// Complete C# console app: how to use llm to edit a Word doc
// ---------------------------------------------------------------
using Aspose.Words;
using Aspose.Words.AI;   // Replace with real namespace if needed
using System;
using System.Collections.Generic;
using System.Net.Http;
using System.Text;
using System.Text.Json;

namespace LlmAsposeDemo
{
    public class LocalLargeLanguageModel
    {
        private readonly HttpClient _client;
        private readonly string _endpoint;

        public LocalLargeLanguageModel(string endpoint)
        {
            _endpoint = endpoint.TrimEnd('/');
            _client = new HttpClient();
        }

        public string GenerateText(string prompt)
        {
            var payload = new { prompt };
            var content = new StringContent(JsonSerializer.Serialize(payload), Encoding.UTF8, "application/json");

            var response = _client.PostAsync($"{_endpoint}/generate", content).Result;
            response.EnsureSuccessStatusCode();

            var json = response.Content.ReadAsStringAsync().Result;
            var result = JsonSerializer.Deserialize<Dictionary<string, string>>(json);
            return result?["response"] ?? string.Empty;
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the document
            Document document = new Document("YOUR_DIRECTORY/input.docx");

            // 2️⃣ Pick the third paragraph (index 2)
            Paragraph targetParagraph = document.FirstSection.Body.Paragraphs[2];
            Console.WriteLine("Original paragraph:");
            Console.WriteLine(targetParagraph.GetText());

            // 3️⃣ Connect to the local LLM
            var localLlm = new LocalLargeLanguageModel("http://localhost:5000");

            // 4️⃣ Ask the model to rewrite it formally
            string prompt = $"Rewrite the following in a formal tone:\n{targetParagraph.GetText()}";
            string revisedText = localLlm.GenerateText(prompt);
            Console.WriteLine("\nRevised paragraph:");
            Console.WriteLine(revisedText);

            // 5️⃣ Replace the paragraph contents
            targetParagraph.Runs.Clear();
            targetParagraph.AppendChild(new Run(document, revisedText));

            // 6️⃣ Save the file
            document.Save("YOUR_DIRECTORY/output.docx");
            Console.WriteLine("\nDocument saved as output.docx");
        }
    }
}
```

### 預期輸出

```
Original paragraph:
the quick brown fox jumps over the lazy dog.

Revised paragraph:
The quick brown fox leaps over the lazy dog in a formal manner.

Document saved as output.docx
```

開啟 `output.docx` —— 你會看到第三段已變成潤飾過的版本。

## 常見問題與注意事項

| Question | Answer |
|----------|--------|
| **如果我的 LLM 回傳含有額外欄位的 JSON 會怎樣？** | 調整 `GenerateText` 以反序列化正確的屬性，或手動解析回應。 |
| **我可以一次處理多個段落嗎？** | 可以——遍歷 `document.FirstSection.Body.Paragraphs`，套用相同的提示詞邏輯，必要時在提示詞中加入段落索引以提供上下文。 |
| **我的 LLM 伺服器需要驗證嗎？** | 在 POST 前於 `HttpClient` 加入標頭：`_client.DefaultRequestHeaders.Add("Authorization", "Bearer YOUR_TOKEN");`。 |
| **替換後格式遺失。** | 保留原始 `Run.Font` 設定：建立新的 `Run`，複製 `originalRun.Font.Clone()`，再設定其 `Text`。 |
| **LLM 有時會回傳空字串。** | 實作備援機制——若 `revisedText.Trim().Length == 0`，則保留原始文字或以更簡單的提示詞重試。 |

## 擴充解決方案

既然你已掌握 **how to use llm** 於單一段落的技巧，請考慮以下後續步驟：

- **批次處理：** 迴圈遍歷每個段落，並以選定的風格重寫（例如「使所有文字更簡潔」）。  
- **樣式感知重寫：** 在提示詞中傳入原始段落的樣式名稱，讓 LLM 能區分標題與正文。  
- **整合至 CI 流程：** 將文件潤飾自動化，作為文件建置流程的一部份。  
- **替代提示詞：** 嘗試「summarize this paragraph」或「translate this paragraph to Spanish」以探索 **rewrite text using ai** 的完整威力。

## 結論

我們已完整說明 **how to use llm** 搭配 Aspose.Words 的全流程：載入文件、**connect to local llm**、擷取段落、**rewrite text using ai**、**replace paragraph text**，最後儲存結果。程式碼自包含、即插即用，展示了將 AI 與傳統文件自動化結合的實用方式。

試著執行、調整提示詞，並讓

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}