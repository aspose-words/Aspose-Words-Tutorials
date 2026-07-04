---
category: general
date: 2026-04-28
description: 從 C# 連接本機 LLM，提示大型語言模型載入 Word 文件，呼叫本機 LLM 自動改寫文字，並附有逐步程式碼示例。
draft: false
keywords:
- connect to local llm
- prompt large language model
- load word document
- call local llm
- rewrite text automatically
language: zh-hant
og_description: 從 C# 連接本地 LLM，了解如何提示大型語言模型、載入 Word 文件、呼叫本地 LLM，並在數分鐘內自動重寫文字。
og_title: 在 C# 中連接本地 LLM – 完整程式設計指南
tags:
- Aspose.Words
- C#
- LLM
- AI Automation
title: 在 C# 中連接本地 LLM – 完整程式設計指南
url: /zh-hant/net/ai-powered-document-processing/connect-to-local-llm-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 中連接本地 LLM – 完整程式開發指南

是否曾經需要 **連接本地 llm** 從 .NET 應用程式，卻不知如何讓它與 Word 檔案互動？你並不孤單。在本指南中，我們將完整說明整個流程——連接本地 llm、**提示大型語言模型**、載入 Word 文件、**呼叫本地 llm**，最後 **自動改寫文字**。完成後，你將擁有一個可執行的範例，能將任意段落轉換為正式語氣，且不需要任何外部 API 金鑰。

## 本教學涵蓋內容

我們會先安裝必要的 NuGet 套件，接著啟動一個簡易的本地 LLM 端點（例如 Ollama 在 11434 埠）。之後，我們會使用 Aspose.Words 載入 `.docx` 檔案，將段落送給 LLM，取得改寫後的版本，並寫回同一份文件。你還會看到如何處理常見的陷阱——空段落、非同步釋放、編碼問題——讓程式碼在正式環境中也能穩定運作，而不只是示範用。

### 前置條件

- .NET 6.0 SDK 或更新版本（如果喜歡也可以使用 .NET 8）
- Visual Studio 2022 或搭配 C# 擴充功能的 VS Code
- **Aspose.Words for .NET**（免費試用版即可）
- 一個支援 `/api/generate` 合約的本地 LLM（例如 Ollama、LMStudio）
- 基本的 C# async/await 使用經驗

> **專業小技巧：** 若尚未安裝 Ollama，可執行 `ollama serve`，並使用 `ollama pull llama3` 下載模型。預設的 HTTP 端點為 `http://localhost:11434/api/generate`。

---

## 步驟 1：安裝必要套件

首先，將 Aspose.Words 與 Aspose.Words.AI NuGet 套件加入專案。

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

這兩個函式庫提供 **載入 Word 文件** 的功能，並且有一層薄薄的包裝，讓你 **呼叫本地 llm** 時不必自行手寫 HTTP 請求。

---

## 步驟 2：連接本地 LLM 端點

連接本機模型只需要實例化 `LocalLargeLanguageModel`。建構子接受完整的產生端點 URL。

```csharp
using Aspose.Words.AI;
using Aspose.Words;
using System.Threading.Tasks;

// Create a client that talks to the LLM running on localhost
var localLlm = new LocalLargeLanguageModel("http://localhost:11434/api/generate");
```

為什麼要把端點包在類別裡？`LocalLargeLanguageModel` 會幫你處理 JSON 序列化、重試機制與串流回應——讓你可以專注於提示邏輯，而不必與 `HttpClient` 纏鬥。

---

## 步驟 3：載入來源 Word 文件

接下來，我們把文件載入記憶體。Aspose.Words 支援幾乎所有的 Word 格式，因此 `Document` 能在不安裝 Office 的情況下解析 `input.docx`。

```csharp
// Path to the source file – adjust as needed
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document; throws if the file is missing or corrupted
Document sourceDocument = new Document(inputPath);
```

如果需要使用串流（例如 ASP.NET 上傳的檔案），只要把檔案路徑換成 `MemoryStream`，再傳給 `Document` 建構子即可。

---

## 步驟 4：取得目前段落文字

我們會使用 `DocumentBuilder` 在文件中導航。此範例改寫 **第一個段落**，但你也可以遍歷 `sourceDocument.GetChildNodes(NodeType.Paragraph, true)` 來處理多個段落。

```csharp
// Builder gives us a cursor inside the document
DocumentBuilder docBuilder = new DocumentBuilder(sourceDocument);

// Grab the text of the paragraph where the builder is currently positioned
string originalParagraph = docBuilder.CurrentParagraph?.GetText() ?? string.Empty;

// Safety check – avoid sending empty strings to the LLM
if (string.IsNullOrWhiteSpace(originalParagraph))
{
    Console.WriteLine("No paragraph found at the current cursor position.");
    return;
}
```

`?.` 運算子可防止在文件為空時拋出 `NullReferenceException`。這是新手常碰到的 **邊緣案例**。

---

## 步驟 5：提示 LLM 改寫段落

現在正式 **提示大型語言模型**。提示內容為純英文；包裝器會把它以 JSON 送到本地端點。

```csharp
// Build a friendly instruction for the model
string prompt = $"Rewrite the following sentence in a more formal tone:\n{originalParagraph}";

// Await the model's response – this is an async call
string rewrittenParagraph = await localLlm.PromptAsync(prompt);
```

為什麼要這樣寫請求？LLM 最擅長回應清晰、單一任務的指示。冒號後加一個換行，可把指示與內容分開，降低模型直接回傳提示本身的機率。

**預期輸出** – 若 `originalParagraph` 為 `"Hey, what's up?"`，LLM 可能回傳：

> “Good day, how may I assist you?”

你可以透過列印結果來驗證：

```csharp
Console.WriteLine("Original:  " + originalParagraph);
Console.WriteLine("Rewritten: " + rewrittenParagraph);
```

---

## 步驟 6：將改寫後的文字寫回文件

取得新文字後，我們替換舊段落。`DocumentBuilder.Writeln` 會寫入新行並將游標往前移，適合用來追加。如果想 **直接取代** 同一段落，可在寫入前呼叫 `docBuilder.CurrentParagraph.RemoveAllChildren()`。

```csharp
// Option A – Append a new paragraph (keeps the original)
docBuilder.Writeln(rewrittenParagraph);

// Option B – Replace the existing paragraph (uncomment to use)
// docBuilder.CurrentParagraph.RemoveAllChildren();
// docBuilder.CurrentParagraph.AppendChild(new Run(docBuilder.Document, rewrittenParagraph));
```

兩種寫法都有示範，讓你依需求選擇最合適的方式。

---

## 步驟 7：儲存更新後的文件

最後，我們把變更寫入新檔。Aspose.Words 會根據副檔名自動決定格式。

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
sourceDocument.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

開啟 `output.docx`，你會看到段落已變成正式語氣。

---

## 完整可執行範例

以下是 **完整、獨立** 的程式。直接貼到 Console 專案、還原 NuGet 套件、執行即可——只要本地 LLM 正在執行，無需額外設定。

```csharp
using Aspose.Words.AI;
using Aspose.Words;
using System;
using System.IO;
using System.Threading.Tasks;

class Program
{
    static async Task Main()
    {
        // -------------------------------------------------
        // Step 1: Connect to the locally hosted LLM endpoint
        // -------------------------------------------------
        var localLlm = new LocalLargeLanguageModel("http://localhost:11434/api/generate");

        // -------------------------------------------------
        // Step 2: Load the source Word document
        // -------------------------------------------------
        string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        Document sourceDocument = new Document(inputPath);

        // -------------------------------------------------
        // Step 3: Retrieve the text of the current paragraph
        // -------------------------------------------------
        DocumentBuilder docBuilder = new DocumentBuilder(sourceDocument);
        string originalParagraph = docBuilder.CurrentParagraph?.GetText() ?? string.Empty;

        if (string.IsNullOrWhiteSpace(originalParagraph))
        {
            Console.WriteLine("No paragraph found at the current cursor position.");
            return;
        }

        // -------------------------------------------------
        // Step 4: Ask the LLM to rewrite the paragraph in a formal tone
        // -------------------------------------------------
        string prompt = $"Rewrite the following sentence in a more formal tone:\n{originalParagraph}";
        string rewrittenParagraph = await localLlm.PromptAsync(prompt);

        // -------------------------------------------------
        // Step 5: Insert the rewritten text back into the document
        // -------------------------------------------------
        docBuilder.Writeln(rewrittenParagraph);

        // -------------------------------------------------
        // Step 6: Save the updated document
        // -------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
        sourceDocument.Save(outputPath);

        Console.WriteLine("Original paragraph:");
        Console.WriteLine(originalParagraph);
        Console.WriteLine("\nRewritten paragraph:");
        Console.WriteLine(rewrittenParagraph);
        Console.WriteLine($"\nDocument saved to {outputPath}");
    }
}
```

### 執行時的預期結果

1. 主控台會印出原始段落與改寫後的段落。  
2. `output.docx` 會與 `input.docx` 同目錄出現。  
3. 開啟檔案後，可看到新正式段落已插入（或若使用替換程式碼則已取代）。

---

## 常見邊緣案例處理

| 情境 | 解決方案 |
|-----------|----------|
| **段落為空或僅有空白** | 在提示前使用 `string.IsNullOrWhiteSpace` 檢查（見 Step 3）。 |
| **LLM 回傳錯誤或空字串** | 將 `PromptAsync` 包在 `try/catch`，若失敗則回退使用原始文字。 |
| **需要改寫多個段落** | 迭代 `sourceDocument.GetChildNodes(NodeType.Paragraph, true)`，對每個段落套用相同的提示邏輯。 |
| **大型文件造成延遲** | 將段落批次處理，單次請求最多傳送約 4 KB（視模型限制而定）。 |
| **非 ASCII 字元出現亂碼** | 確認 LLM 端點使用 UTF-8（大多數現代模型皆如此）。 |

---

## 後續步驟與相關主題

- 使用更豐富的指示 **提示大型語言模型**（例如風格指南、長度限制）。  
- 在 Web API 中 **呼叫本地 llm**，將文件自動化服務化。  
- 探索在平行串流中 **載入 Word 文件**，以因應高吞吐量情境。  
- 結合 **自動改寫文字**，用於大量電子郵件產生或報告標準化。  

想更深入了解，可參考 Aspose 文件中的 **文件合併** 章節，以及 Ollama API 參考文件中的自訂抽樣參數說明。

---

## 結論

我們已示範如何在 C# 中 **連接本地 llm**、**提示大型語言模型**、**載入 Word 文件**、**呼叫本地 llm**，以及 **自動改寫文字**——全部於一個可執行的 Console 應用程式中完成。此模式具備可擴充性：只要更換提示、遍歷段落，或將邏輯封裝成 ASP.NET 端點，即可靈活運用。關鍵在於，本地 AI 模型可以與傳統文件處理函式庫緊密結合，讓你在可信的本地環境中實現強大自動化，而不必依賴外部服務。

如有執行緒相關問題，歡迎提出。

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}