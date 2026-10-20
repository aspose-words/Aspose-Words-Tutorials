---
category: general
date: 2026-03-04
description: 如何为文档 AI 配置大型语言模型并使用 AI 替换 DOCX 中的文本——一步一步的完整 Java 代码指南。
draft: false
keywords:
- how to configure llm
- replace text in docx
- how to replace text
- how to use document ai
- replace phrase with ai
language: zh
og_description: How to configure LLM for Document AI and replace text in DOCX using
  AI – complete guide with runnable Java code.
og_title: How to Configure LLM – Replace Text in DOCX with AI
tags:
- LLM
- Document AI
- Java
- DOCX
title: 如何配置 LLM – 使用 AI 替换 DOCX 文本
url: /zh/java/ai-machine-learning-integration/how-to-configure-llm-replace-text-in-docx-with-ai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何配置 LLM – 使用 AI 替换 DOCX 中的文本

Ever wondered **how to configure LLM** so it can edit a Word file for you? You're not the only one. Many developers hit a wall when they need to programmatically replace a phrase inside a `.docx` without opening Microsoft Word. The good news? With a local LLM and a tiny Document AI wrapper, you can swap out text in a DOCX file in just a few lines of Java.

In this tutorial we’ll walk through the entire process: from wiring up the LLM connection, loading a DOCX, to using **Document AI** to replace a target phrase. By the end you’ll have a self‑contained, runnable example that you can drop into any Maven or Gradle project. No external API keys, no cloud fees—just your own model listening on `http://localhost:8080/v1`.

> **Quick win:** If you already have a local LLM (like Llama 3 or Mistral) exposing an OpenAI‑compatible endpoint, the code below works out‑of‑the‑box.

---

![如何配置 LLM 进行 Document AI](/images/configure-llm-diagram.png){: .center-image alt="如何配置 llm 图示"}

## 您需要的环境

- **Java 17**（或任何近期的 JDK）  
- 一个 **本地 LLM**，提供 OpenAI 风格的 `/v1` 接口（例如 Ollama、LMStudio）  
- **Document AI Java 库**（假设在 Maven Central 上的 `com.example:document-ai:1.2.0`）  
- 一个示例 DOCX 文件（`input.docx`），放置在已知文件夹中  

如果缺少上述任意项，请快速启动 Ollama：

```bash
ollama serve &
ollama run llama3
```

这将启动一个监听在 `http://localhost:8080/v1` 的服务器，准备接受请求。

---

## 如何为 Document AI 配置 LLM

我们首先要告诉 `DocumentAi` 客户端模型所在位置以及使用哪个模型。这就是许多教程略过的 **how to configure LLM** 步骤。

```java
// Step 1: Set up the LLM connection details
AiModelConfig modelConfig = new AiModelConfig();
modelConfig.setBaseUrl("http://localhost:8080/v1");   // Local server address
modelConfig.setApiKey("dummy");                       // Not needed for local models, but the client expects a value
modelConfig.setModelName("local-llm");                // Replace with your model's identifier
```

*为什么重要：*  
`AiModelConfig` 对象抽象了 HTTP 细节，让 `DocumentAi` 专注于内容本身。如果以后切换到托管服务，只需更改 `baseUrl` 和 `apiKey`——其余代码保持不变。

---

## 加载并准备 DOCX 文档

接下来将 Word 文件读取到内存中。`Document` 类在内部同时支持 `.docx` 和 `.pdf`，但这里我们只关心 DOCX。

```java
// Step 2: Load the DOCX you want to edit
Path docPath = Paths.get("YOUR_DIRECTORY/input.docx");
Document inputDocument = new Document(docPath.toFile());
```

*小技巧：* 调试时使用绝对路径可以避免 “文件未找到” 的意外。确认无误后再改回相对路径，以提升可移植性。

---

## 使用 AI 替换 DOCX 中的文本

下面进入本教程的核心——**how to replace text** 在 DOCX 文件中使用 AI 辅助。`replaceText` 方法会把文档内容发送给 LLM，要求它执行替换并返回修改后的文本。

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

*背后发生了什么？*  
`DocumentAi` 将 DOCX 序列化为纯文本，构造类似以下的提示：

> “在下面的文档中，将所有出现的 ‘old phrase’ 替换为 ‘new phrase’，并仅返回更新后的文本。”

LLM 处理请求后返回修改后的内容。这种方式即使短语跨越多个 run 或段落也能正常工作，而普通的字符串替换往往会漏掉。

---

## 验证并输出修订后的文本

最后我们将 AI 修订后的文本打印到控制台。实际项目中通常会把结果写回新的 DOCX，但直接打印可以快速验证。

```java
// Step 5: Show the AI‑revised output
System.out.println("AI‑revised text:");
System.out.println("-----------------------------------");
System.out.println(revisedText);
```

**预期输出**（假设原始 DOCX 包含 “This is the old phrase we want to change.”）：

```
AI‑revised text:
-----------------------------------
This is the new phrase we want to change.
```

如果看到新短语出现，恭喜你——**你已经学会如何使用 Document AI 用 AI 替换短语**。

---

## 完整可运行示例

将所有代码组合在一起，下面是一个完整、可直接运行的 Java 类。可复制粘贴到 `src/main/java/com/example/ReplaceInDocx.java`。

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

### 如何运行

```bash
# Compile
mvn clean compile

# Execute
mvn exec:java -Dexec.mainClass="com.example.ReplaceInDocx"
```

确保在运行程序前 LLM 服务器已启动；否则会出现连接超时。

---

## 边缘情况与常见陷阱

| 情况 | 需要注意的点 | 建议的解决方案 |
|-----------|-------------------|---------------|
| **未找到短语** | LLM 返回的文本未改变。 | 检查拼写和大小写；如果包装器支持，可在提示中加入 `ignoreCase:true`。 |
| **大文档（>5 MB）** | 提示长度可能超出模型的 token 限制。 | 将 DOCX 拆分为多个章节，分别处理后再拼接结果。 |
| **本地 LLM 返回错误** | 通常是模型名称不匹配导致。 | 确认 LLM UI（`ollama list`）中的模型名称与 `modelConfig.setModelName` 设置一致。 |
| **Unicode 字符乱码** | 读取 DOCX 时的编码问题。 | 确保 Java 运行时使用 UTF‑8（在 JVM 参数中添加 `-Dfile.encoding=UTF-8`）。 |

---

## 后续步骤

既然已经掌握了 **how to replace text in DOCX** with AI，接下来可以探索：

- **How to use Document AI** 进行更复杂的任务，如表格抽取或样式保留。  
- **Replace phrase with AI** 在 PDF 中实现，只需更换 `Document` 构造函数的参数。  
- **Batch processing**：遍历目录下的多个 DOCX 文件并执行相同的替换。  

这些都基于相同的 `AiModelConfig` 与 `DocumentAi` 基础，无需从头开始。

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}