---
category: general
date: 2026-05-04
description: 使用 Aspose.Words 於 Java 建立 Word 文件，並學習如何以自訂大型語言模型檢查文法。針對 Java 開發者的逐步指南。
draft: false
keywords:
- create word document java
- how to create docx
- how to check grammar
- use custom llm
language: zh-hant
og_description: 使用 Java 建立 Word 文件，並了解如何使用自訂 LLM 檢查文法。完整的 Java 教學，附可執行程式碼。
og_title: 使用自訂 LLM 文法檢查的 Java 建立 Word 文件
tags:
- Java
- Aspose.Words
- LLM
title: 使用自訂 LLM 文法檢查的 Java 建立 Word 文件
url: /zh-hant/java/ai-machine-learning-integration/create-word-document-java-with-custom-llm-grammar-check/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用自訂 LLM 文法檢查建立 Java Word 文件

有沒有想過如何 **create word document java** 專案同時自動校對？你並不孤單——許多開發者希望有一條單一的流程，直接產出精緻的 *.docx* 檔案，而不必切換多種工具。在本教學中，我們將一步步示範，教你使用 Aspose.Words 產生 **how to create docx** 檔案，連接本機託管的 LLM，最後自動 **how to check grammar**。完成後，你將擁有一個自給自足的 Java 程式，能寫入、驗證並儲存 Word 文件——同時 **using custom LLM** 你自行控制的端點。

## 需要的條件

在開始之前，請確保你的工作站已具備以下項目：

| 前置條件 | 重要原因 |
|--------------|----------------|
| Java 17+（或任何較新的 JDK） | 現代語言功能與更佳的模組支援 |
| Aspose.Words for Java（最新版本） | 提供程式化 **create word document java** 檔案的函式庫 |
| 本機託管的 LLM 伺服器（例如 Ollama、LMStudio），監聽 `http://localhost:11434/api/generate` | 用於 **use custom llm** 步驟，提供文法檢查功能 |
| Maven 或 Gradle（本教學以 Maven 為例） | 簡化相依性管理 |
| IDE 或文字編輯器（IntelliJ IDEA、VS Code 等） | 讓程式編寫與除錯更輕鬆 |

如果上述任一項目聽起來陌生，別慌——每項都可以免費取得，或有社群版可供學習使用。

## 步驟 1 – 設定 Maven 專案

要快速 **create word document java** 專案，請先建立最小的 Maven `pom.xml`。此檔案會引入 Aspose.Words 函式庫以及你偏好的 HTTP 客戶端（本教學使用 Apache HttpClient）。

```xml
<!-- pom.xml -->
<project xmlns="http://maven.apache.org/POM/4.0.0" 
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>word-llm-demo</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>17</maven.compiler.source>
        <maven.compiler.target>17</maven.compiler.target>
    </properties>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- replace with the latest -->
        </dependency>

        <!-- Apache HttpClient for calling the LLM endpoint -->
        <dependency>
            <groupId>org.apache.httpcomponents.client5</groupId>
            <artifactId>httpclient5</artifactId>
            <version>5.2</version>
        </dependency>
    </dependencies>
</project>
```

> **Pro tip:** 如果你使用 Gradle，請將相同的相依性放在 `build.gradle` 的 `implementation` 區塊中。

現在執行 `mvn clean install` 以下載 jar 檔。建置成功後，你就可以撰寫 Java 程式碼來 **creates word document java** 檔案。

## 步驟 2 – 撰寫 **Creates word document java** 的 Java 類別

以下是完整、可直接執行的原始碼檔案。它示範了整個流程：初始化空白文件、設定自訂 LLM 端點、呼叫文法檢查，最後儲存結果。

```java
package com.example.wordllmdemo;

import com.aspose.words.*;
import com.aspose.words.ai.*;

import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;

/**
 * Demonstrates how to create a Word document in Java and run a grammar‑check
 * using a self‑hosted LLM (e.g., Ollama). This example is fully self‑contained
 * and can be executed with a single `java -cp` command after Maven builds.
 */
public class SelfHostedLLMDemo {

    public static void main(String[] args) throws Exception {
        // -----------------------------------------------------------------
        // Step 2.1 – Create an empty Word document
        // -----------------------------------------------------------------
        Document document = new Document(); // this is the object that will become your .docx

        // Add a simple paragraph so the grammar engine has something to work with
        DocumentBuilder builder = new DocumentBuilder(document);
        builder.writeln("Ths sentence has a typo and a grammer error.");

        // -----------------------------------------------------------------
        // Step 2.2 – Configure the custom LLM endpoint (use custom llm)
        // -----------------------------------------------------------------
        AiEndpoint llmEndpoint = new AiEndpoint();
        llmEndpoint.setBaseUrl("http://localhost:11434/api/generate");
        llmEndpoint.setModel("llama3.1:8b"); // make sure this model is available locally

        // Initialise the Document AI engine with the endpoint we just set up
        DocumentAi documentAi = new DocumentAi(llmEndpoint);

        // -----------------------------------------------------------------
        // Step 2.3 – Run grammar checking (how to check grammar)
        // -----------------------------------------------------------------
        // AiModelType.CUSTOM tells the API to forward the request to our LLM
        documentAi.checkGrammar(document, AiModelType.CUSTOM);

        // -----------------------------------------------------------------
        // Step 2.4 – Save the corrected file
        // -----------------------------------------------------------------
        String outputPath = "output/GrammarChecked.docx";
        // Ensure the directory exists
        Files.createDirectories(Path.of("output"));
        document.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

> **Why this works:**  
> * `Document` 是 Aspose.Words 的核心類別，代表記憶體中的 *.docx*。  
> * `AiEndpoint` 告訴 Aspose 的 AI 模組要將提示發送至何處。將其指向 `localhost:11434` 後，我們 **use custom llm** 取代雲端服務。  
> * `checkGrammar` 搭配 `AiModelType.CUSTOM` 會將文件文字傳送至 LLM，取得校正後的文字，並重新寫入底層的 Word 節點。  
> * 最後呼叫 `save` 將檔案寫入磁碟，為你產生精緻的 Word 檔案。

### 預期輸出

執行 `mvn exec:java -Dexec.mainClass="com.example.wordllmdemo.SelfHostedLLMDemo"` 後，你應該會看到：

```
Document saved to output/GrammarChecked.docx
```

在 Microsoft Word（或 LibreOffice）中開啟產生的 `GrammarChecked.docx`。原本的句子 *“Ths sentence has a typo and a grammer error.”* 現在會變成 *“This sentence has a typo and a grammar error.”* —— 證明 **how to check grammar** 步驟已成功。

## 步驟 3 – 使用不同內容建立 docx（可選）

如果想產生更豐富的文件——表格、圖片或樣式化文字，只需持續使用 `DocumentBuilder`。以下是一段快速程式碼示例，展示如何加入標題與表格：

```java
// Adding a heading
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Demo Report");

// Adding a 2x2 table
Table table = builder.startTable();
builder.insertCell();
builder.write("Item");
builder.insertCell();
builder.write("Quantity");
builder.endRow();

builder.insertCell();
builder.write("Apples");
builder.insertCell();
builder.write("42");
builder.endRow();
builder.endTable();
```

你可以將此程式碼插入文件建立區塊（Step 2.1）與文法檢查呼叫（Step 2.3）之間的任何位置。LLM 仍會收到完整文字，因而能校正所有自然語言部分，同時保持表格不變。

## 步驟 4 – 處理端點問題（安全使用自訂 LLM）

使用 **using custom llm** 端點時，常會遇到以下問題：

| 症狀 | 可能原因 | 解決方法 |
|---------|--------------|-----|
| `Connection refused` 錯誤 | LLM 伺服器未啟動或埠號錯誤 | 啟動 Ollama (`ollama serve`) 並使用 `curl` 確認 `http://localhost:11434/api/generate` 可用。 |
| 回應 JSON 缺少 `completion` 欄位 | 模型名稱不匹配 | 確保已安裝所設定的模型（`llama3.1:8b`），可使用 `ollama list` 檢查。 |
| 文法檢查回傳原始文字未變更 | LLM 未辨識提示 | 調整模型的 system |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}