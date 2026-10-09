---
category: general
date: 2026-03-19
description: 學習如何在 Word 中使用本機大型語言模型檢查語法、註冊模型，並儲存已更正的文件——全部於單一 C# 教學中完成。
draft: false
keywords:
- how to check grammar
- set up local llm
- check grammar in word
- how to register llm
- how to save corrected
language: zh-hant
og_description: 如何在 Word 中使用本地 LLM 檢查文法、註冊模型並儲存已校正的文件——一步一步指南。
og_title: 如何在 C# 中使用本地 LLM 檢查語法
tags:
- Aspose.Words
- AI
- C#
title: 如何在 C# 中使用本地 LLM 檢查語法
url: /zh-hant/net/ai-powered-document-processing/how-to-check-grammar-with-a-local-llm-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中使用本地 LLM 檢查文法

有沒有想過 **如何在 Word 文件中檢查文法**，卻不必將文字傳到雲端？你並不孤單。許多開發者希望在保有自託管模型的私隱的同時，仍能取得 AI 驅動的建議。在本指南中，我們將逐步說明如何註冊自訂 LLM、設定 Aspose.Words 使用它，最後 **如何儲存已校正** 的檔案——全部使用純 C#。

我們也會說明 **設置本地 llm** 的細節，示範 **如何註冊 llm** 端點，並展示 **在 word 文件中檢查文法** 的完整步驟。完成後，你將擁有一個可直接放入任何 .NET 專案的可執行範例。

## 前置條件

- .NET 6+ SDK（此程式碼可在 .NET Core 與 .NET Framework 上執行）
- Visual Studio 2022 或搭配 C# 擴充功能的 VS Code
- Aspose.Words for .NET（v24.12 或更新版本）— 可從 NuGet 取得
- 本機執行的 LLM，支援 OpenAI 相容 API（例如 Ollama，埠號 11434）

> **小技巧：** 若你使用 Ollama，指令 `ollama serve` 會自動啟動端點 `http://localhost:11434/api/generate`。

## 步驟 1 – 如何註冊 llm：將自訂模型加入 Aspose.Words

我們首先需要告訴 Aspose.Words 我們的 **本地 llm**。此步驟在應用程式啟動時只需執行一次。

```csharp
using Aspose.Words;
using Aspose.Words.AI;

// Register a custom LLM endpoint – no API key required for local servers
AiEngine.RegisterModel(
    modelName: "local-llm",                         // identifier we’ll reference later
    endpoint: new Uri("http://localhost:11434/api/generate"),
    apiKey: null,                                   // local server doesn’t need a key
    provider: AiProvider.Custom);
```

**為什麼這很重要：** 透過註冊模型，你為 Aspose.Words 提供了一個命名的句柄（`"local-llm"`）。之後呼叫 `CheckGrammar` 時，函式庫就會知道要連接哪個端點。若省略此步驟，函式庫會退回使用內建的雲端服務，失去私有 LLM 的意義。

## 步驟 2 – 載入要分析的 Word 文件

現在我們將檔案載入記憶體。你可以指向任何 `.docx`、`.doc`，甚至 `.rtf` 檔案。

```csharp
// Replace YOUR_DIRECTORY with the actual folder path on your machine
Document sourceDocument = new Document("YOUR_DIRECTORY/input.docx");

// Quick sanity check – print the number of paragraphs we just loaded
Console.WriteLine($"Loaded document with {sourceDocument.GetChildNodes(NodeType.Paragraph, true).Count} paragraphs.");
```

**發生了什麼：** `Document` 是 Aspose.Words 的核心物件模型。它會解析檔案並建立節點樹（段落、表格、圖片等），讓 AI 引擎能針對特定文字範圍進行文法分析。

## 步驟 3 – 設定文法檢查選項（設置本地 llm）

在此我們將先前註冊的模型與文法檢查操作關聯起來。

```csharp
AiGrammarCheckOptions grammarOptions = new AiGrammarCheckOptions
{
    Model = "local-llm",               // references the name we used in RegisterModel
    // Optional: you can tweak temperature, maxTokens, etc. if your LLM supports them
    // Temperature = 0.7,
    // MaxTokens = 512
};
```

**為什麼提供這些選項：** 不同的 LLM 具備不同的行為。透過公開 `Model`，Aspose.Words 允許你在本地模型與雲端模型之間切換，而不必更改其他程式碼。當 **設置本地 llm** 以符合合規或離線情境時，此彈性尤為重要。

## 步驟 4 – 執行 AI 驅動的文法檢查（在 word 中檢查文法）

所有設定完成後，實際的文法檢查只需要一行程式碼。

```csharp
// This mutates sourceDocument in place, inserting suggestions and corrections
sourceDocument.CheckGrammar(grammarOptions);
Console.WriteLine("Grammar check completed.");
```

**內部運作：** Aspose.Words 會抽取每個句子，送至 LLM 端點，接收包含建議編輯的 JSON 資料，然後將這些編輯套用回文件樹。此處為簡化起見採同步執行；若偏好非阻塞 I/O，也可呼叫非同步重載 `CheckGrammarAsync`。

## 步驟 5 – 如何儲存已校正的文件

AI 完成校正後，你會想要將變更寫回檔案。

```csharp
// Save the corrected file – you can change the format to PDF, HTML, etc.
sourceDocument.Save("YOUR_DIRECTORY/checked.docx");
Console.WriteLine("Corrected document saved as checked.docx");
```

**預期結果：** 在 Word 中開啟 `checked.docx`，你會看到文法問題被標示（或依 `AiGrammarCheckOptions` 設定自動校正）。若啟用了追蹤，亦會看到修訂標記。

## 完整可執行範例

將上述所有步驟整合起來，以下是一個可直接執行的主控台應用程式：

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.AI;

class Program
{
    static void Main()
    {
        // 1️⃣ Register the local LLM
        AiEngine.RegisterModel(
            modelName: "local-llm",
            endpoint: new Uri("http://localhost:11434/api/generate"),
            apiKey: null,
            provider: AiProvider.Custom);

        // 2️⃣ Load the source document
        string inputPath = "YOUR_DIRECTORY/input.docx";
        Document sourceDocument = new Document(inputPath);
        Console.WriteLine($"Loaded: {inputPath}");

        // 3️⃣ Set up grammar‑check options (using the local model)
        AiGrammarCheckOptions grammarOptions = new AiGrammarCheckOptions
        {
            Model = "local-llm"
        };

        // 4️⃣ Perform the AI‑driven grammar check
        sourceDocument.CheckGrammar(grammarOptions);
        Console.WriteLine("Grammar analysis finished.");

        // 5️⃣ Save the corrected document
        string outputPath = "YOUR_DIRECTORY/checked.docx";
        sourceDocument.Save(outputPath);
        Console.WriteLine($"Corrected file saved to: {outputPath}");
    }
}
```

**預期在主控台的輸出：**

```
Loaded: YOUR_DIRECTORY/input.docx
Grammar analysis finished.
Corrected file saved to: YOUR_DIRECTORY/checked.docx
```

開啟 `checked.docx`，即可看到文法改進已自動套用。

## 常見問題與邊緣情況

| Question | Answer |
|----------|--------|
| *如果我的 LLM 需要 API 金鑰怎麼辦？* | 將金鑰傳入 `RegisterModel` 的 `apiKey` 參數。相同的程式碼同時適用於需要金鑰與不需要金鑰的服務。 |
| *我可以使用其他檔案格式嗎？* | 當然可以。`Document.Save` 支援 `.pdf`、`.html`、`.txt` 等格式，只需更改副檔名即可。 |
| *如果 LLM 回傳錯誤怎麼辦？* | 將 `CheckGrammar` 包在 try/catch 中，檢查 `AiException` 以取得詳細資訊。通常是逾時導致——可考慮增大 `grammarOptions.Timeout`。 |
| *此操作是執行緒安全的嗎？* | 註冊步驟是全域性的，應於啟動時執行一次。之後的 `CheckGrammar` 呼叫只要各自使用自己的 `Document` 實例，即可安全平行執行。 |

## 後續步驟

既然你已了解如何使用 **本地 llm** 進行 **文法檢查**，接下來可以探索：

- **批次處理**：遍歷資料夾中的文件，執行相同的流程。
- **自訂提示詞**：透過設定 `grammarOptions.PromptTemplate` 來調整請求內容，以進行特定風格的檢查。
- **整合至 ASP.NET Core**：提供 API 端點，接受上傳的 `.docx` 檔案，執行文法檢查，並回傳已校正的檔案。

這些擴充功能讓你能在本地環境建置完整的「文法即服務」平台，無需將資料送出。

---

*祝開發順利！若遇到任何問題，歡迎在下方留言，我很樂意協助你微調設定。*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}