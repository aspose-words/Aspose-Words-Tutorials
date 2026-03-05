---
category: general
date: 2026-03-04
description: How to configure LLM for Document AI and replace text in DOCX using AI
  – step‑by‑step guide with full Java code.
draft: false
keywords:
- how to configure llm
- replace text in docx
- how to replace text
- how to use document ai
- replace phrase with ai
language: zh-hant
og_description: 如何為文件 AI 配置大型語言模型並使用 AI 替換 DOCX 中的文字 – 完整指南與可執行的 Java 程式碼
og_title: 如何設定 LLM – 使用 AI 替換 DOCX 文字
tags:
- LLM
- Document AI
- Java
- DOCX
title: 如何設定 LLM – 使用 AI 替換 DOCX 文字
url: /zh-hant/java/ai-machine-learning-integration/how-to-configure-llm-replace-text-in-docx-with-ai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何設定 LLM – 使用 AI 替換 DOCX 文字

有沒有想過 **如何設定 LLM** 讓它能為你編輯 Word 檔案？你並不是唯一有此疑問的人。許多開發者在需要以程式方式取代 `.docx` 內的字句卻不想開啟 Microsoft Word 時，常常卡關。好消息是，只要有本地 LLM 加上一個小型 Document AI 包裝器，你就能用幾行 Java 代碼在 DOCX 檔案中替換文字。

在本教學中，我們會一步步說明完整流程：從建立 LLM 連線、載入 DOCX，到使用 **Document AI** 替換目標字句。完成後，你將擁有一個自包含、可直接執行的範例，能放入任何 Maven 或 Gradle 專案。無需外部 API 金鑰，無需雲端費用——只要你的模型在 `http://localhost:8080/v1` 監聽即可。

> **快速上手：** 若你已經有本地 LLM（例如 Llama 3 或 Mistral）提供 OpenAI 相容的端點，以下程式碼即可直接使用。

---

![設定 LLM 用於 Document AI 的流程圖](/images/configure-llm-diagram.png){: .center-image alt="設定 LLM 流程圖"}

## 需要的環境

- **Java 17**（或任何較新的 JDK）  
- 一個 **本地 LLM**，提供 OpenAI 風格的 `/v1` 端點（例如 Ollama、LMStudio）  
- **Document AI Java 套件**（假設在 Maven Central 上為 `com.example:document-ai:1.2.0`）  
- 一個範例 DOCX 檔案（`input.docx`），放在已知資料夾內  

如果缺少上述任一項，請快速啟動 Ollama：

```bash
ollama serve &
ollama run llama3
```

此指令會在 `http://localhost:8080/v1` 啟動伺服器，準備接受請求。

---

## 如何設定 LLM 供 Document AI 使用

首先，我們要告訴 `DocumentAi` 客戶端模型的所在位置與使用的模型。這就是許多教學常常略過的 **如何設定 LLM** 步驟。

```java
// Step 1: Set up the LLM connection details
AiModelConfig modelConfig = new AiModelConfig();
modelConfig.setBaseUrl("http://localhost:8080/v1");   // Local server address
modelConfig.setApiKey("dummy");                       // Not needed for local models, but the client expects a value
modelConfig.setModelName("local-llm");                // Replace with your model's identifier
```

*為什麼這很重要：*  
`AiModelConfig` 物件抽象化了 HTTP 細節，讓 `DocumentAi` 專注於內容本身。若日後改用雲端服務，只需要更改 `baseUrl` 與 `apiKey`——其餘程式碼不需要變動。

---

## 載入並準備 DOCX 文件

接著，我們把 Word 檔案載入記憶體。`Document` 類別在底層同時支援 `.docx` 與 `.pdf`，但此處我們只關心 DOCX。

```java
// Step 2: Load the DOCX you want to edit
Path docPath = Paths.get("YOUR_DIRECTORY/input.docx");
Document inputDocument = new Document(docPath.toFile());
```

*小技巧：* 在除錯時使用絕對路徑，以避免「找不到檔案」的意外。確認無誤後，再改回相對路徑以提升可移植性。

---

## 使用 AI 替換 DOCX 文字

現在進入教學的核心——**如何使用 AI 替換文字**。`replaceText` 方法會將文件內容傳給 LLM，請求它執行取代，最後回傳修改後的文字。

```java
// Step 3: Initialise the Document AI client
DocumentAi documentAi = new DocumentAi(modelConfig);

// Step 4: Ask the LLM to replace the target phrase
String oldPhrase = "old phrase";
String newPhrase = "new phrase";

String revisedText = documentAi.replaceText(
        inputDocument,
        oldPhrase,
        newPhrase
);
```

*背後發生了什麼？*  
`DocumentAi` 會將 DOCX 序列化為純文字，並組成類似以下的提示語：

> 「在下列文件中，將所有出現的 ‘old phrase’ 替換為 ‘new phrase’，僅回傳更新後的文字。」

LLM 處理請求後回傳修改過的內容。此方式即使字句跨越多個 run 或段落，也能正確取代，這是純字串替換常常無法做到的。

---

## 驗證並輸出修正後的文字

最後，我們把 AI 修正過的文字印到主控台。實務上可能會把結果寫回新 DOCX，但先印出來可以快速驗證。

```java
// Step 5: Show the AI‑revised output
System.out.println("AI‑revised text:");
System.out.println("-----------------------------------");
System.out.println(revisedText);
```

**預期輸出**（假設原始 DOCX 內含 “This is the old phrase we want to change.”）：

```
AI‑revised text:
-----------------------------------
This is the new phrase we want to change.
```

如果看到新字句出現，恭喜你——**已學會使用 Document AI 以 AI 替換字句**。

---

## 完整可執行範例

將所有程式碼整合在一起，以下是一個完整、可直接執行的 Java 類別。可直接複製貼上至 `src/main/java/com/example/ReplaceInDocx.java`。

```java
package com.example;

import com.example.documentai.AiModelConfig;
import com.example.documentai.DocumentAi;
import com.example.documentai.Document;

import java.nio.file.Path;
import java.nio.file.Paths;

/**
 * Demonstrates how to configure LLM, load a DOCX, and replace a phrase using Document AI.
 */
public class ReplaceInDocx {

    public static void main(String[] args) {
        // 1️⃣ Configure the local LLM connection
        AiModelConfig modelConfig = new AiModelConfig();
        modelConfig.setBaseUrl("http://localhost:8080/v1");
        modelConfig.setApiKey("dummy");               // Not required for local models
        modelConfig.setModelName("local-llm");        // Change if needed

        // 2️⃣ Load the DOCX you want to modify
        Path docPath = Paths.get("YOUR_DIRECTORY/input.docx");
        Document inputDocument = new Document(docPath.toFile());

        // 3️⃣ Create the Document AI client using the configuration
        DocumentAi documentAi = new DocumentAi(modelConfig);

        // 4️⃣ Replace the target phrase with the new phrase using the AI model
        String oldPhrase = "old phrase";
        String newPhrase = "new phrase";

        String revisedText = documentAi.replaceText(
                inputDocument,
                oldPhrase,
                newPhrase
        );

        // 5️⃣ Output the AI‑revised text
        System.out.println("AI‑revised text:");
        System.out.println("-----------------------------------");
        System.out.println(revisedText);
    }
}
```

### 執行方式

```bash
# Compile
mvn clean compile

# Execute
mvn exec:java -Dexec.mainClass="com.example.ReplaceInDocx"
```

執行程式前請確保 LLM 伺服器已啟動；否則會收到連線逾時的錯誤。

---

## 邊緣情況與常見陷阱

| 情況 | 需要注意的地方 | 建議解決方式 |
|-----------|-------------------|---------------|
| **找不到字句** | LLM 回傳原始文字未變更。 | 再次確認拼寫與大小寫；若你的 wrapper 支援，可在提示語加入 `ignoreCase:true`。 |
| **大型文件（>5 MB）** | 提示字數可能超過模型的 token 限制。 | 將 DOCX 切分為多段，分別處理後再合併結果。 |
| **本地 LLM 回傳錯誤** | 常因模型名稱不符所致。 | 確認 LLM 介面（`ollama list`）中的模型名稱與 `modelConfig.setModelName` 設定相同。 |
| **Unicode 字元亂碼** | 讀取 DOCX 時的編碼問題。 | 確保 Java 執行環境使用 UTF‑8（在 JVM 參數加入 `-Dfile.encoding=UTF-8`）。 |

---

## 後續步驟

既然已掌握 **如何使用 AI 替換 DOCX 文字**，你可以進一步探索：

- **如何使用 Document AI** 進行更複雜的任務，例如表格抽取或樣式保留。  
- **以 AI 替換 PDF 文字**，只要改變 `Document` 建構子傳入的參數即可。  
- **批次處理**：遍歷資料夾中的多個 DOCX 檔案，套用相同的取代作業。  

以上皆建立在相同的 `AiModelConfig` 與 `DocumentAi` 基礎上，無需從頭開始。

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}