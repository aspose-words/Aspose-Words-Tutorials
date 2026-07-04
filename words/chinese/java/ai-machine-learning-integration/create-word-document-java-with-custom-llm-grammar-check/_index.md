---
category: general
date: 2026-05-04
description: 使用 Aspose.Words 在 Java 中创建 Word 文档，并学习如何使用自定义大语言模型进行语法检查。面向 Java 开发者的逐步指南。
draft: false
keywords:
- create word document java
- how to create docx
- how to check grammar
- use custom llm
language: zh
og_description: 使用 Java 创建 Word 文档，并了解如何使用自定义 LLM 检查语法。完整的 Java 教程，附带可运行的代码。
og_title: 使用自定义 LLM 语法检查在 Java 中创建 Word 文档
tags:
- Java
- Aspose.Words
- LLM
title: 使用自定义 LLM 语法检查在 Java 中创建 Word 文档
url: /zh/java/ai-machine-learning-integration/create-word-document-java-with-custom-llm-grammar-check/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用自定义 LLM 语法检查创建 Java Word 文档

有没有想过如何 **创建 word document java** 项目并让它们自行校对？你并不孤单——许多开发者都希望拥有一个单一的流水线，直接输出精美的 *.docx* 文件，而无需切换多个工具。在本教程中，我们将一步步演示如何使用 Aspose.Words 创建 docx 文件，连接本地托管的 LLM，最后 **自动检查语法**。完成后，你将拥有一个自包含的 Java 程序，能够写入、验证并保存 Word 文档——全部使用你自己控制的 **自定义 LLM** 接口。

## 你需要准备的东西

在开始之前，请确保你的工作站上具备以下环境：

| 先决条件 | 原因 |
|----------|------|
| Java 17+（或任意近期 JDK） | 支持现代语言特性和更好的模块化 |
| Aspose.Words for Java（最新版本） | 让你能够 **create word document java** 程序化生成文件的库 |
| 本地托管的 LLM 服务器（如 Ollama、LMStudio），监听 `http://localhost:11434/api/generate` | 为 **use custom llm** 步骤提供语法检查所需的模型 |
| Maven 或 Gradle（示例使用 Maven） | 简化依赖管理 |
| IDE 或文本编辑器（IntelliJ IDEA、VS Code 等） | 让编码和调试更轻松 |

如果其中有不熟悉的，请不要慌——这些工具都有免费或社区版，完全适合学习使用。

## 第一步 – 创建 Maven 项目

要 **create word document java** 项目快速起步，先准备一个最小的 Maven `pom.xml`。该文件会引入 Aspose.Words 库以及你喜欢的 HTTP 客户端（这里使用 Apache HttpClient）。

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

> **专业提示：** 如果你使用 Gradle，只需在 `build.gradle` 的 `implementation` 部分加入相同的依赖即可。

运行 `mvn clean install` 下载所需 jar 包。构建成功后，即可编写 Java 代码来 **creates word document java**。

## 第二步 – 编写 **Creates word document java** 的 Java 类

下面是完整的、可直接运行的源码文件。它演示了整个流程：初始化空白文档、配置自定义 LLM 端点、调用语法检查，最后保存结果。

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

> **为什么这样做有效：**  
> * `Document` 是 Aspose.Words 的核心类，代表内存中的 *.docx*。  
> * `AiEndpoint` 告诉 Aspose 的 AI 模块将请求发送到哪里。将其指向 `localhost:11434` 即可 **use custom llm**，而不是云服务。  
> * 使用 `checkGrammar` 并指定 `AiModelType.CUSTOM` 会把文档文本发送给 LLM，获取纠正后的文本，并重写底层的 Word 节点。  
> * 最后调用 `save` 将文件写入磁盘，得到一份已润色的 Word 文档。

### 预期输出

运行 `mvn exec:java -Dexec.mainClass="com.example.wordllmdemo.SelfHostedLLMDemo"` 后，你应该看到：

```
Document saved to output/GrammarChecked.docx
```

在 Microsoft Word（或 LibreOffice）中打开生成的 `GrammarChecked.docx`。原句 *“Ths sentence has a typo and a grammer error.”* 将被更正为 *“This sentence has a typo and a grammar error.”* —— 这证明 **how to check grammar** 步骤已成功。

## 第三步 – 使用不同内容创建 docx（可选）

如果想生成更丰富的文档——表格、图片或带样式的文本，只需继续使用 `DocumentBuilder`。下面的代码片段演示了如何添加标题和表格：

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

你可以在文档创建块（步骤 2.1）和语法检查调用（步骤 2.3）之间的任意位置插入这段代码。LLM 仍会接收到完整文本，从而纠正自然语言部分，而表格等结构保持不变。

## 第四步 – 处理端点问题（安全使用自定义 LLM）

在 **using custom llm** 端点时，常会遇到以下小障碍：

| 症状 | 可能原因 | 解决办法 |
|------|----------|----------|
| `Connection refused` 错误 | LLM 服务器未启动或端口错误 | 启动 Ollama（`ollama serve`），并使用 `curl http://localhost:11434/api/generate` 验证连通性。 |
| 响应 JSON 缺少 `completion` 字段 | 模型名称不匹配 | 确认已安装并使用正确的模型（如 `llama3.1:8b`），可通过 `ollama list` 检查。 |
| 语法检查返回原始文本未改变 | 提示未被 LLM 正确识别 | 调整模型的系统提示或请求格式，使其能够识别校对指令。 |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}