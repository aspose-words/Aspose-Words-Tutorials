---
category: general
date: 2026-05-23
description: 在 C# 中呼叫 OpenAI API 以正式語氣改寫句子。學習如何載入 Word 文件、呼叫本地 LLM，並使用 Aspose.Words
  以正式語氣改寫段落。
draft: false
keywords:
- call openai api
- call local llm
- rewrite sentence formal
- rewrite paragraph formal
- load word document
language: zh-hant
og_description: 使用 C# 呼叫 OpenAI API 以正式語氣改寫句子。完整逐步教學，包含程式碼、說明與技巧。
og_title: 從 C# 呼叫 OpenAI API – 改寫 Word 段落
schemas:
- author: Aspose
  dateModified: '2026-05-23'
  description: Call OpenAI API in C# to rewrite sentence formal style. Learn how to
    load word document, call local LLM, and rewrite paragraph formal with Aspose.Words.
  headline: Call OpenAI API from C# – Complete Guide to Rewrite Word Paragraphs
  type: TechArticle
- description: Call OpenAI API in C# to rewrite sentence formal style. Learn how to
    load word document, call local LLM, and rewrite paragraph formal with Aspose.Words.
  name: Call OpenAI API from C# – Complete Guide to Rewrite Word Paragraphs
  steps:
  - name: Why This Works
    text: '- **LocalLargeLanguageModel** abstracts the HTTP details, letting you **call
      local llm** exactly the same way you would a cloud OpenAI endpoint. - The prompt
      we send (`Rewrite the following sentence in formal tone:`) is concise, which
      helps the model focus on a **rewrite sentence formal** transforma'
  - name: Expected Output Example
    text: '| Original (informal) | Rewritten (formal) | |---------------------|--------------------|
      | *Hey team, can we get the results ASAP?* | *Dear team, could you please provide
      the results at your earliest convenience?* |'
  - name: Empty Paragraphs
    text: 'Sometimes a Word file contains empty paragraphs that throw off the LLM.
      Guard against this:'
  - name: Large Documents
    text: 'Processing a 100‑page report paragraph‑by‑paragraph can be slow. Batch
      the calls:'
  type: HowTo
tags:
- Aspose.Words
- C#
- LLM
- OpenAI
- Word Automation
title: 從 C# 呼叫 OpenAI API – 完整指南：改寫 Word 段落
url: /zh-hant/net/ai-powered-document-processing/call-openai-api-from-c-complete-guide-to-rewrite-word-paragr/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 從 C# 呼叫 OpenAI API – 完整的 Word 段落改寫指南

有沒有想過如何從 .NET 應用程式 **call OpenAI API** 並即時潤飾文字？或許你有一個 Word 檔需要以更正式的語氣呈現給客戶報告，而你不想自己重新打字。在本教學中，我們將一步步示範：載入 Word 文件、將段落傳送至本機部署的 LLM（模擬 OpenAI 相容 API），並取得 **rewrite paragraph formal** 版本。完成後，你將擁有一個可執行的 C# 主控台應用程式，只需幾行程式碼即可完成全部工作。

我們會涵蓋所有必備內容：所需的 NuGet 套件、如何使用 Aspose.Words **load word document**、**call local llm** 的細節，以及為何提示語 “Rewrite the following sentence in formal tone” 能穩定產生 **rewrite sentence formal** 的結果。無需外部文件，只要一份可直接複製貼上執行的完整指南。

## 你將達成的目標

- 使用 Aspose.Words 載入 *.docx* 檔案。  
- 建立一個客戶端，能 **call OpenAI API**‑compatible 端點，即使它們在本機執行。  
- 將段落傳送至 LLM，並取得 **rewrite paragraph formal** 回應。  
- 替換 Word 檔中的原始文字，並儲存更新後的文件。  

前置條件相當簡單：.NET 6+ SDK、Visual Studio 或 VS Code，以及一個提供 OpenAI‑compatible HTTP 端點的本機 LLM（例如 Ollama、LM Studio）。如果你已有雲端金鑰，只需切換端點與 API 金鑰——程式碼保持不變。

---

## 步驟 1：設定專案並安裝套件

首先，建立一個新的主控台專案：

```bash
dotnet new console -n WordLlmRewrite
cd WordLlmRewrite
```

接著加入我們需要的兩個 NuGet 套件：

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

> **專業提示：** Aspose.Words.AI 附帶一個輕量級的封裝，能夠 **call OpenAI API**‑style 服務，讓你不必自行手動編寫 HTTP 請求。

## 步驟 2：編寫 **Call OpenAI API**（或本機 LLM）程式碼

開啟 `Program.cs`，將內容取代為以下程式碼。每一行都在下方說明，讓你不會迷失。

```csharp
using Aspose.Words;
using Aspose.Words.AI;
using System;

// ------------------------------------------------------------
// 1️⃣ Create a client for the local LLM that follows the
//    OpenAI‑compatible API. This is the heart of the
//    “call openai api” step.
// ------------------------------------------------------------
var localLlm = new LocalLargeLanguageModel(
    endpoint: "http://localhost:8000/v1", // change if your server runs elsewhere
    apiKey: "dummy",                      // dummy because the local server usually skips auth
    model: "my-llm");                     // name of the model you want to use

// ------------------------------------------------------------
// 2️⃣ Load the source Word document.
// ------------------------------------------------------------
Document doc = new Document("YOUR_DIRECTORY/source.docx");

// ------------------------------------------------------------
// 3️⃣ Grab the first paragraph that we want to rewrite.
// ------------------------------------------------------------
Paragraph paragraph = doc.FirstSection.Body.FirstParagraph;

// ------------------------------------------------------------
// 4️⃣ Ask the LLM to rewrite the paragraph in a formal tone.
//    This is where we “rewrite paragraph formal”.
// ------------------------------------------------------------
string revisedText = localLlm.GenerateText(
    $"Rewrite the following sentence in formal tone:\n{paragraph.GetText()}");

// ------------------------------------------------------------
// 5️⃣ Replace the original paragraph text with the revised version.
// ------------------------------------------------------------
paragraph.Runs.Clear();                     // remove old runs
paragraph.AppendChild(new Run(doc, revisedText));

// ------------------------------------------------------------
// 6️⃣ Save the updated document.
// ------------------------------------------------------------
doc.Save("YOUR_DIRECTORY/rewritten.docx");

// ------------------------------------------------------------
// 7️⃣ Confirmation output.
// ------------------------------------------------------------
Console.WriteLine("✅ Document rewritten and saved as rewritten.docx");
```

### 為什麼這樣可行

- **LocalLargeLanguageModel** 抽象化 HTTP 細節，讓你 **call local llm** 的方式與呼叫雲端 OpenAI 端點完全相同。  
- 我們傳送的提示語 (`Rewrite the following sentence in formal tone:`) 簡潔明瞭，有助於模型專注於 **rewrite sentence formal** 的轉換，而不會加入不相關的內容。  
- 透過清除 `paragraph.Runs` 並新增一個 `Run`，確保 Word 檔只保留全新的正式文字。

## 步驟 3：執行應用程式

確保本機 LLM 伺服器已啟動並監聽於 `http://localhost:8000/v1`。然後執行：

```bash
dotnet run
```

如果一切設定正確，你會看到：

```
✅ Document rewritten and saved as rewritten.docx
```

開啟 `rewritten.docx` —— 首段現在應該以潤飾過的正式風格呈現。

### 預期輸出範例

| 原始（非正式） | 改寫（正式） |
|---------------------|--------------------|
| *Hey team, can we get the results ASAP?* | *Dear team, could you please provide the results at your earliest convenience?* |

此轉換示範了乾淨的 **rewrite sentence formal** 轉換，非常適合商業溝通。

## 步驟 4：調整提示語以取得不同語氣

如果你需要更隨意的改寫，只要更改提示語：

```csharp
string revisedText = localLlm.GenerateText(
    $"Rewrite the following sentence in a casual tone:\n{paragraph.GetText()}");
```

同樣地，你也可以請模型對較長段落執行 **rewrite paragraph formal**，甚至摘要整份文件。相同的 **call openai api** 模式仍然適用——只要更換提示語，客戶端程式碼保持不變。

## 步驟 5：處理例外情況

### 空段落

有時 Word 檔會包含空段落，會干擾 LLM。請防範此情況：

```csharp
if (string.IsNullOrWhiteSpace(paragraph.GetText()))
{
    Console.WriteLine("Skipped empty paragraph.");
}
else
{
    // generate and replace as before
}
```

### 大型文件

逐段處理 100 頁報告可能會很慢。請批次呼叫：

```csharp
foreach (Paragraph p in doc.GetChildNodes(NodeType.Paragraph, true))
{
    // same rewrite logic for each paragraph
}
```

留意本機伺服器的速率限制；可能需要在呼叫之間加入 `Thread.Sleep(200)` 的小延遲。

## 步驟 6：部署至正式環境

1. 若改用 Azure OpenAI 或 OpenAI SaaS，請將虛擬 API 金鑰換成正式金鑰。  
2. 將端點與金鑰存放於環境變數 (`OPENAI_ENDPOINT`, `OPENAI_KEY`)，並透過 `Environment.GetEnvironmentVariable` 讀取。  
3. 在 **call openai api** 區塊周圍加入日誌（例如 Serilog），以追蹤請求/回應的內容。

## 步驟 7：額外加分 – 加入簡易 UI

如果你想要快速的 Windows Forms 前端介面：

```csharp
// inside a button click handler
var filePath = openFileDialog1.FileName;
Document doc = new Document(filePath);
// reuse the same rewriting logic...
```

如此一來，非技術同事也能拖放檔案，即可取得正式改寫，無需接觸程式碼。

---

## 結論

我們剛剛建立了一個小巧卻功能強大的 C# 工具，可 **call openai api**（或任何相容的本機 LLM）在 Word 檔中 **rewrite paragraph formal**。透過 **load word document**、傳送簡潔的提示語，並替換段落文字，即可在數秒內得到潤飾過的文件。

從此你可以：

- 擴充工具以處理表格與圖片。  
- 與 SharePoint 整合，實現文件自動潤飾。  
- 嘗試其他語氣——**rewrite sentence formal**、**rewrite sentence casual**，甚至 **rewrite sentence persuasive**。

試試看，調整提示語，讓 LLM 為你完成繁重的工作。祝開發愉快！

## 相關教學

- [在 Aspose.Words for .NET 中建立與樣式化 Word 文件](/words/english/net/document-styling/apply-paragraph-style/)
- [在 Word 文件中套用段落樣式](/words/english/net/document-formatting/apply-paragraph-style/)
- [在 Word 文件中移動到段落](/words/english/net/add-content-using-documentbuilder/move-to-paragraph/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}