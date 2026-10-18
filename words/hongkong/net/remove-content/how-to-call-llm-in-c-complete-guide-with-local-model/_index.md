---
category: general
date: 2026-01-13
description: 學習如何使用本地 LLM 端點從 C# 呼叫 LLM、編輯 Word 檔案、移除全部內容，並儲存 docx——一次完整教學。
draft: false
keywords:
- how to call llm
- use local llm
- remove all content
- how to edit word
- how to save docx
language: zh-hant
og_description: 如何在 C# 中使用本地模型呼叫 LLM、編輯 Word 文件、刪除所有內容，並有效地儲存 docx。
og_title: 如何在 C# 中呼叫 LLM – 步驟教學
tags:
- Aspose.Words
- C#
- LLM Integration
title: 如何在 C# 中呼叫 LLM – 本機模型完整指南
url: /zh-hant/net/remove-content/how-to-call-llm-in-c-complete-guide-with-local-model/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中呼叫 LLM – 完整本地模型指南

有沒有想過 **如何在 .NET 應用程式中呼叫 LLM**，卻不把資料傳到雲端？你並不孤單。許多開發者希望將提示詞與文件保留在本機，特別是處理機密文字時。於本教學中，我們將示範一個實務情境：使用自行部署的 LLM 端點改寫 Word 文件、移除全部內容、編輯檔案，最後 **如何將 docx 儲存** 回磁碟。

我們也會說明 **使用本地 LLM**，提供完整程式碼示範 **如何從 Aspose.Words `Document` 中移除全部內容**，並解釋以程式方式編輯 Word 檔的細節。完成後，你將擁有一套可直接複製貼上的解決方案，適用於 Aspose.Words 7+ 以及任何相容 OpenAI 的本地模型。

## 前置條件 – 開始前需要的項目

- **.NET 6+**（或若偏好傳統框架，可使用 .NET Framework 4.7.2）
- **Aspose.Words for .NET** NuGet 套件（`Aspose.Words` 與 `Aspose.Words.AI`）
- 一個 **本地 LLM**，提供相容 OpenAI 的 `/v1` 端點（例如在 `http://localhost:8000/v1` 上的 GPT‑Neo 伺服器）
- 放置於可自行管理資料夾中的範例 `input.docx`
- Visual Studio、Rider，或任何你喜歡的編輯器 – 本文以 VS Code 為截圖示範

> **專業小技巧：** 若尚未有本地模型，可參考免費的 GPT‑Neo 2.7B Docker 映像檔，只要不到一分鐘即可啟動，且遵循與本文相同的 API 合約。

## 步驟 1 – 設定本地 LLM 端點（如何呼叫 LLM）

當你想要 **如何在 C# 中呼叫 llm** 時，第一件事就是建立指向自行部署服務的客戶端物件。Aspose.Words.AI 內建 `LocalLargeLanguageModel` 輔助類別，負責抽象化 HTTP 呼叫。

```csharp
using Aspose.Words;
using Aspose.Words.AI;

// Configure the self‑hosted LLM endpoint
var llm = new LocalLargeLanguageModel
{
    Endpoint = "http://localhost:8000/v1",   // your local server
    ModelName = "my-gpt-neo"                // name as registered in the server
};
```

> **為什麼重要：** 透過自行設定端點，你可以完整掌控請求內容、驗證方式與延遲時間。這正是 **如何呼叫 llm** 而不依賴外部服務的核心。

## 步驟 2 – 載入來源 Word 文件（如何編輯 Word）

接下來，我們把原始的 `.docx` 載入 Aspose `Document`。這就是經典的 **如何編輯 word** 步驟：檔案進入記憶體後，即可查詢、修改，甚至完全取代其內容。

```csharp
// Load the source document from disk
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

若檔案不存在，會拋出 `FileNotFoundException`，請務必確認路徑正確。若是處理上傳的情況，也可以從 `Stream` 載入。

## 步驟 3 – 使用本地 LLM 產生修訂文字（如何呼叫 LLM）

現在進入重點：我們請 LLM 以正式語氣改寫整段文字。提示詞是將簡短指示與透過 `document.GetText()` 取得的原始文字串接而成。

```csharp
// Ask the model to rewrite the whole document in a formal tone
string prompt = "Rewrite the following in formal tone:\n" + document.GetText();

string revisedText = llm.GenerateText(prompt);
```

> **邊緣情況：** 若來源文件過大（超過 10 k 代幣），可能會觸及模型的上下文限制。此時請將文字切分為段落，分別呼叫 `GenerateText` 處理每個區塊。

## 步驟 4 – 移除所有既有內容（Remove All Content）

在插入新文字之前，我們必須先清空文件。Aspose 提供 `RemoveAllChildren()`，可一次清除節、段落、表格——全部內容。這是 **從 Word 檔案中移除所有內容** 的標準作法。

```csharp
// Clear the document completely
document.RemoveAllChildren();
```

> **如果只想刪除正文而保留頁首？** 可使用 `document.Sections.Clear()`，然後自行重建需要的節。

## 步驟 5 – 插入修訂文字（如何編輯 Word）

清空後，我們即可將LM 產生的文字寫回。`DocumentBuilder` 是友善的封裝，可讓你加入段落、表格、圖片等。此處僅將整段字串作為單一段落寫入。

```csharp
// Re‑populate the document with the revised text
DocumentBuilder builder = new DocumentBuilder(document);
builder.Writeln(revisedText);
```

若需要更豐富的格式（粗體、標題），可自行解析 LLM 輸出的 Markdown 標記，並依據 `builder.Font` 設定套用樣式。

## 步驟 6 – 儲存更新後的文件（如何儲存 Docx）

最後，我們把變更寫入新檔。這示範了 **如何在程式編輯後儲存 docx**。

```csharp
// Save the edited document
document.Save("YOUR_DIRECTORY/output.docx");
```

`Save` 方法會自動依檔案副檔名偵測格式，因此只要改一行程式碼，即可匯出為 PDF、HTML 或 ODT。

### 預期結果

開啟 `output.docx` 時，應看到原始內容已全部以精緻、正式的風格重新寫過。文件中不會留下任何來源的表格、頁首或頁腳——只有 LLM 產生的全新文字。

---

![Screenshot of output.docx opened in Word, showing formal rewritten text – how to call llm](/images/output-docx.png "how to call llm example")

*圖片替代文字:* **呼叫 llm 範例 – 顯示已改寫的 Word 文件**

## 常見問題與除錯

### 1. 「如果我的 LLM 回傳錯誤怎麼辦？」

`GenerateText` 方法會在非 2xx 回應時拋出 `HttpRequestException`。請將呼叫包在 `try/catch` 中，檢查 `ex.Message`。常見問題包括缺少 API 金鑰標頭或超過模型的代幣上限。

```csharp
try
{
    string revisedText = llm.GenerateText(prompt);
}
catch (HttpRequestException ex)
{
    Console.WriteLine($"LLM call failed: {ex.Message}");
    // fallback logic, e.g., return the original text
}
```

### 2. 「我可以只編輯文件的特定部份，而不是全部清除嗎？」

當然可以。使用 `document.GetChildNodes(NodeType.Paragraph, true)` 取得所有段落，然後只在需要的段落上修改 `Paragraph.Text` 屬性。此方式讓你 **如何編輯 word** 時保留樣式，僅在粒度層面進行變更。

### 3. 「有沒有方法保留原始格式？」

若想保留樣式，可先將 LLM 輸出為純文字，然後根據你的模板使用 `builder.Font.StyleIdentifier` 為每段落套用樣式。或者，若 LLM 能輸出 HTML，直接使用 `DocumentBuilder.InsertHtml()`。

### 4. 「如何處理大型文件？」

將文件切分為節（`document.Sections`），分別處理每一節。這不僅避免代幣上限，也能減少記憶體壓力。

## 效能小技巧

- **在多次呼叫間重複使用 `LocalLargeLanguageModel` 實例**；底層的 `HttpClient` 會保持連線。
- **快取修訂文字**，若同一提示會被多次使用，因為本地 LLM 呼叫仍可能耗費資源。
- **平行處理**：在多核心 CPU 且 LLM 客戶端支援執行緒安全時，可使用 `Parallel.ForEach` 同時處理多個節。

## 後續步驟 – 擴充工作流程

既然你已掌握 **如何呼叫 llm**、**使用本地 llm**、**移除所有內容**、**如何編輯 word**，以及 **如何儲存 docx**，接下來可以探索：

- **批次處理**：遍歷資料夾內所有 `.docx`，套用相同的改寫邏輯。
- **自訂提示**：調整指示詞以產生摘要、項目符號或翻譯。
- **結合 ASP.NET Core**：建立 HTTP 端點，接受檔案上傳、執行 LLM，最後回傳編輯後的文件。
- **進階樣式**：將 LLM 輸出的 Markdown 解析為 Word 樣式，使用 `DocumentBuilder` 完成映射。

以上每項延伸都建立在本教學的核心模式上，讓你能以最小的工作量調整程式碼。

---

## 結論

本指南說明了 **如何在 C# 中呼叫 llm**（使用自行部署的端點），示範 **使用本地 llm**，展示 **如何從 Word 檔案中移除所有內容**，說明 **如何編輯 word** 程式化的步驟，並以 **如何儲存 docx** 為例完整收尾。完整可執行的範例已可直接放入任何 .NET 專案，說明亦提供了每一步的「為什麼」，讓你能自信地調整、擴充或除錯。

快試試看，變換不同的提示詞，讓本地 LLM 為你的文件自動化流程加速。若遇到任何問題，除錯章節會指引你找到解決方案。祝開發順利，盡情體驗本機 LLM 的威力！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}