---
category: general
date: 2026-02-21
description: 如何在 C# 中載入 DOCX、將其文字傳送至本地 LLM 進行文法檢查，並寫回修正後的版本。包括如何使用 LLM 以及讀取 Word 文件文字。
draft: false
keywords:
- how to check grammar
- how to use llm
- read word document text
- load docx in c#
language: zh-hant
og_description: 如何在 C# 中載入 DOCX，將文字傳送至本地 LLM 進行語法檢查，並寫回修正後的版本。學習如何使用 LLM 以及讀取 Word
  文件文字。
og_title: 如何使用本地大型語言模型在 C# 中檢查語法
tags:
- C#
- LLM
- Aspose.Words
title: 如何在 C# 中使用本地 LLM 檢查語法
url: /zh-hant/net/ai-powered-document-processing/how-to-check-grammar-in-c-using-a-local-llm/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中使用本地 LLM 檢查文法

有沒有想過 **如何在 Word 文件中檢查文法**，而不必離開 C# 專案？你並不是唯一有此疑問的開發者——大家常問：「能否用同樣的程式碼自動校對，像聊天機器人一樣？」簡短的答案是可以。只要載入 DOCX、抽取文字，並將其送到本機部署的大型語言模型（LLM），就能即時取得文法修正，並把潤飾後的結果直接寫回檔案。

在本教學中，我們將逐步說明整個流程：使用 **load docx in c#** 讀取 `.docx`、呼叫 **how to use llm** 進行文法校正，最後儲存整理好的文件。完成後，你將擁有一個可直接執行的 Console 應用程式，完全符合需求——不需要手動複製貼上、也不需要外部 API，僅靠純 C# 與本地 LLM 端點。

> **你需要的環境**
> - .NET 6.0 或更新版本（程式碼在 .NET Framework 也可執行，但 .NET 6 是最佳選擇）
> - [Aspose.Words for .NET](https://products.aspose.com/words/net/) 套件（免費試用版即可測試）
> - 一個可提供 `CheckGrammar(string)` 簡易端點的 LLM 伺服器（例如 Ollama、LM Studio，或自行包裝的 FastAPI 服務）
> - 基本的 async/await 概念（非必須，但建議熟悉）

如果你在想 **為什麼要在意這件事**，請想想在產生報告後手動修正錯字所花的時間。將這一步自動化不僅能加速整個流程，還能保證大量文件的一致性。現在就一起來實作吧。

---

## How to Check Grammar – Overview

在正式動手之前，先快速瀏覽一下流程圖：

1. **建立一個 client**，用來與本地 LLM 端點通訊。  
2. **使用 Aspose.Words 讀取 Word 文件**——這是 C# 中 **read word document text** 的經典做法。  
3. **將原始文字送給 LLM**，取得校正後的版本。  
4. **把文件中的原始內容換成校正過的文字**。  
5. **儲存** 更新後的檔案（視需求而定，通常都需要）。

每個步驟都寫在獨立的方法裡，方便日後重複使用或替換。完整原始碼會放在文章最後。

---

## Step 1: Set Up the LLM Client (How to Use LLM)

為了保持程式碼整潔，我們會把 HTTP 呼叫封裝在一個小型的 wrapper 類別中。此類別假設 LLM 服務接受 JSON payload `{ "prompt": "…"}` 的 POST 請求，並回傳 `{ "response": "…" }`。若你的服務格式不同，請自行調整序列化方式。

```csharp
using System.Net.Http;
using System.Text;
using System.Text.Json;
using System.Threading.Tasks;

/// <summary>
/// Minimal client for a local LLM that offers a grammar‑checking endpoint.
/// </summary>
public class LocalLargeLanguageModel
{
    private readonly HttpClient _http;
    private readonly string _baseUrl;

    public LocalLargeLanguageModel(string baseUrl)
    {
        _baseUrl = baseUrl.TrimEnd('/');
        _http = new HttpClient();
    }

    /// <summary>
    /// Sends the input text to the LLM and returns the corrected version.
    /// </summary>
    public async Task<string> CheckGrammarAsync(string input)
    {
        var payload = new { prompt = $"Correct the grammar and punctuation:\n\n{input}" };
        var content = new StringContent(JsonSerializer.Serialize(payload), Encoding.UTF8, "application/json");

        // The endpoint is assumed to be /grammar
        var response = await _http.PostAsync($"{_baseUrl}/grammar", content);
        response.EnsureSuccessStatusCode();

        var json = await response.Content.ReadAsStringAsync();
        var result = JsonSerializer.Deserialize<Dictionary<string, string>>(json);
        return result != null && result.TryGetValue("response", out var corrected) ? corrected : input;
    }
}
```

**為什麼這麼做很重要：**  
- **解耦** – 未來若要從 Ollama 換成 LM Studio，只需要更改 URL 或 payload 格式。  
- **支援非同步** – 網路 I/O 不會阻塞 UI 或背景工作。  
- **錯誤處理** – `EnsureSuccessStatusCode` 會在 LLM 無回應時拋出明確例外，我們稍後會捕捉。

> **小技巧：** 若你的 LLM 在 GPU 上執行，請將請求大小控制在約 4 KB 以下，以免出現延遲尖峰。

---

## Step 2: Load the DOCX and Extract Text (Read Word Document Text)

Aspose.Words 讓讀取 Word 檔案變得非常簡單。`Document.GetText()` 會回傳完整的可見文字，並保留換行。若需要更豐富的格式（例如表格、註腳），就必須自行遍歷節點樹，但對於純文法檢查而言，純文字已足夠。

```csharp
using Aspose.Words;

/// <summary>
/// Loads a .docx file and returns its raw textual content.
/// </summary>
public static string ReadDocumentText(string filePath)
{
    if (!File.Exists(filePath))
        throw new FileNotFoundException($"Document not found: {filePath}");

    var doc = new Document(filePath);
    return doc.GetText(); // Returns text with line breaks
}
```

**邊緣情況說明：**  
如果文件內含非英文字符或特殊符號，請確保所使用的 LLM 模型支援 Unicode。大多數現代模型都支援，但較舊的模型可能會截斷或誤解這些字符。

---

## Step 3: Replace Content with the Corrected Text

Aspose.Words 沒有直接「一次取代整個正文」的方法，但清空節點樹後插入單一段落的做法相當好用。這同時也能確保任何隱藏的標記（例如追蹤變更）被移除。

```csharp
/// <summary>
/// Overwrites the document with the supplied corrected text.
/// </summary>
public static void WriteCorrectedText(string filePath, string correctedText)
{
    var doc = new Document(filePath);
    doc.RemoveAllChildren(); // Clears sections, paragraphs, tables, etc.

    var builder = new DocumentBuilder(doc);
    builder.Writeln(correctedText); // Writes as a single paragraph; you can split by "\n" if you want multiple paragraphs.

    doc.Save(filePath); // Overwrites the original file
}
```

**為什麼要移除所有子節點：**  
- 確保乾淨的起點，避免舊有格式干擾新內容。  
- 簡化程式碼——不必逐一搜尋特定節點進行取代。

如果你想保留原始標題，可以先解析原始節點樹，只取代 `Run` 節點，但這會增加教學之外的複雜度。

---

## Step 4: Wire Everything Together – Full Working Example

以下是完整的 Console 程式碼範例，示範 **how to check grammar** 從頭到尾的流程，包含基本錯誤處理與可選的命令列參數。

```csharp
using System;
using System.IO;
using System.Threading.Tasks;
using Aspose.Words;

// Ensure you have a license or are okay with the evaluation watermark.
class Program
{
    // Adjust these paths to match your environment.
    private const string InputPath = @"YOUR_DIRECTORY\input.docx";
    private const string OutputPath = @"YOUR_DIRECTORY\output.docx";
    private const string LlmEndpoint = "http://localhost:5000";

    static async Task Main(string[] args)
    {
        try
        {
            // 1️⃣ Create the LLM client.
            var llm = new LocalLargeLanguageModel(LlmEndpoint);

            // 2️⃣ Load the DOCX and read its text.
            Console.WriteLine("Reading document...");
            string originalText = ReadDocumentText(InputPath);

            // 3️⃣ Send text to the LLM for grammar correction.
            Console.WriteLine("Sending text to LLM for grammar check...");
            string correctedText = await llm.CheckGrammarAsync(originalText);

            // 4️⃣ Write the corrected text back into a new file.
            Console.WriteLine("Writing corrected text to new document...");
            // We copy the original file first so the original remains untouched.
            File.Copy(InputPath, OutputPath, overwrite: true);
            WriteCorrectedText(OutputPath, correctedText);

            Console.WriteLine($"✅ Grammar check complete! Updated file saved to: {OutputPath}");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"❌ An error occurred: {ex.Message}");
            // For real‑world apps, consider logging the stack trace.
        }
    }

    // --- Helper methods from earlier steps ---
    public static string ReadDocumentText(string filePath)
    {
        if (!File.Exists(filePath))
            throw new FileNotFoundException($"Document not found: {filePath}");

        var doc = new Document(filePath);
        return doc.GetText();
    }

    public static void WriteCorrectedText(string filePath, string correctedText)
    {
        var doc = new Document(filePath);
        doc.RemoveAllChildren();

        var builder = new DocumentBuilder(doc);
        // Preserve line breaks by splitting and writing each line.
        foreach (var line in correctedText.Split(new[] { "\r\n", "\n" }, StringSplitOptions.None))
        {
            builder.Writeln(line);
        }

        doc.Save(filePath);
    }
}
```

### Expected Output

執行程式 (`dotnet run`) 後，主控台會顯示類似以下內容：

```
Reading document...
Sending text to LLM for grammar check...
Writing corrected text to new document...
✅ Grammar check complete! Updated file saved to: YOUR_DIRECTORY\output.docx
```

開啟 `output.docx`，你會看到相同的內容，但標點、主詞與動詞的一致性，以及明顯的拼寫錯誤，都已由 LLM 修正。

---

## Common Questions & Edge Cases

### 如果 LLM 回傳 `null` 或空字串怎麼辦？

`CheckGrammarAsync` 會在回應 payload 缺少 `response` 欄位時，退回原始輸入。這樣可以避免意外把文件內容清空。

### 文件太大會導致請求逾時嗎？

大多數本地 LLM 伺服器能舒適處理數千字元。若檔案較大（例如 100 KB 以上），建議將文字切成段落，分別送出，每段約 2 KB 為佳，最後再把校正後的片段重新組合。

### 這樣會保留圖片、表格或註腳嗎？

不會。因為我們清除了所有子節點，所有非文字元素都會遺失。若需要保留這些元素，必須遍歷節點樹，只取代 `Run` 節點（文字片段），其餘節點保持不變。這屬於較進階的情境，可自行探索 Aspose.Words 的 `NodeCollection` 操作方式。

### 可以改用雲端 LLM 嗎？

當然可以。只要在 `LocalLargeLanguageModel` 中更換端點 URL 與 payload 格式即可。需要注意的是，雲端服務通常有速率限制與費用，而本地模型則可離線運行且在初始 GPU/CPU 設定後免除額外成本。

---

## Pro Tips & Best Practices

- **Cache the client**: Re‑using the same `HttpClient` instance avoids

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}