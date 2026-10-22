---
category: general
date: 2026-03-25
description: 创建自定义 AI 模型来编辑 Word 文档——学习如何使文本更正式、替换段落文本，以及使用 Aspose.Words AI 重写 Word
  段落。
draft: false
keywords:
- create custom ai model
- make text more formal
- replace paragraph text
- edit paragraph with ai
- rewrite word paragraph
language: zh
og_description: 创建自定义 AI 模型来编辑 Word 文档。了解如何使文本更正式、替换段落文本，以及使用 Aspose.Words AI 重写 Word
  段落。
og_title: 创建自定义 AI 模型 – 在 Java 中编辑 Word 段落
tags:
- Aspose.Words
- Java
- AI integration
title: 创建自定义 AI 模型 – 在 Java 中编辑 Word 段落
url: /zh/java/ai-machine-learning-integration/create-custom-ai-model-edit-word-paragraphs-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 创建自定义 AI 模型 – 在 Java 中编辑 Word 段落

是否曾经需要 **创建自定义 AI 模型** 来润色 Word 文件中的段落？也许你手头有一批合同，语气稍显随意，你希望只用一行代码就能让文本更正式。好消息是，你完全可以做到——无需外部服务、无需笨重的 SDK，只需 Aspose.Words for Java 和一个兼容 OpenAI 的端点。

在本教程中，我们将逐步演示如何 **创建自定义 AI 模型**、将其连接到本地 LLM 服务器，然后使用它来 *替换段落文本* 为更正式的版本。完成后，你将拥有一个可运行的 Java 程序，能够 **使用 AI 编辑段落**，重写 Word 段落，并将结果保存回磁盘。没有冗余，只提供可直接复制到项目中的实用方案。

> **你需要准备的内容**  
> • Java 17 或更高版本（代码在更早版本也能编译，但 17 是最佳选择）  
> • Aspose.Words for Java 23.9（或最新版本）  
> • 正在运行的兼容 OpenAI 的 LLM 服务器（例如 Ollama、LocalAI），监听地址为 `http://localhost:8000/v1`  
> • 一个放置在你可控文件夹中的输入 Word 文档（`input.docx`）  

如果你在想 *为什么要自己构建模型* 而不是直接调用 OpenAI，答案在于灵活性：你可以自行控制端点，随时切换模型而无需改动代码，并且可以将 API 密钥从源码库中剔除。下面开始动手吧。

---

## 创建自定义 AI 模型 – 设置与配置

首先需要告诉 Aspose.Words 我们的 LLM 位于何处。`AiModelEndpoint` 类保存 URL 和可选的 API 密钥。由于使用的是本地服务器，密钥可以设为空字符串，但该参数是必需的。

```java
import com.aspose.words.ai.*;

public class LlmDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Define the LLM endpoint (OpenAI‑compatible)
        AiModelEndpoint llmEndpoint = new AiModelEndpoint(
                "http://localhost:8000/v1",   // URL of your LLM server
                "my-api-key");                // API key if required
```

> **小技巧：** 如果以后切换到托管模型（例如 Azure OpenAI），只需更改 URL 和密钥——无需修改其他代码。

---

## 加载 Word 文档

接下来将源文件读取到内存中。`Document` 能读取 `.docx`、`.doc`、`.rtf` 等多种格式，但本例仅使用 `.docx`。

```java
        // Step 2: Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

确保 `YOUR_DIRECTORY` 指向真实的文件夹；否则会抛出 `FileNotFoundException`。在实际项目中，你可能会将路径作为命令行参数传入，或从配置文件读取。

---

## 初始化自定义 AI 模型

我们创建一个类型为 `CUSTOM` 的 `AiModel`，并将前面定义的端点传入。这告诉 Aspose.Words 将所有 AI 调用路由到我们自己的服务器。

```java
        // Step 3: Create a custom AI model that uses the endpoint
        AiModel llmModel = new AiModel(AiModelType.CUSTOM, llmEndpoint);
```

在内部，Aspose.Words 会构建一个小型 HTTP 客户端，使用标准的 OpenAI chat/completion 结构与 LLM 通信。因此端点必须是 *兼容 OpenAI* 的。

---

## 获取并改写第一段

这里真正实现 **让文本更正式**。我们获取第一段的原始文本，连同提示一起发送给模型，随后接收编辑后的版本。

```java
        // Step 4: Retrieve the first paragraph and ask the model to rewrite it
        Paragraph firstParagraph = document.getFirstSection()
                                            .getBody()
                                            .getParagraphs()
                                            .get(0);
        String rewrittenText = llmModel.editText(
                firstParagraph.getText(),
                "Make it more formal");
```

第二个参数（`"Make it more formal"`）即是我们给模型的指令。你可以将其替换为任意指令——**替换段落文本**、**摘要**、**翻译** 等。该方法返回普通字符串，稍后会插回文档中。

> **原理说明：** `editText` 会发送类似 `{ "model": "...", "messages": [{ "role":"user", "content":"<text>\nMake it more formal"}] }` 的 JSON 负载。LLM 看到原始段落和指令后，返回修改后的文本。

---

## 替换原始段落内容

现在我们在 Word 对象模型中 **替换段落文本**。先清除段落中已有的 `Run`（文本的低层单元），再插入一个包含 AI 生成字符串的新 `Run`。

```java
        // Step 5: Replace the original paragraph content with the rewritten text
        firstParagraph.removeAllChildren();
        firstParagraph.appendChild(new Run(document, rewrittenText));
```

注意不要调用 `firstParagraph.setText()`——该方法会去除所有格式。使用 `Run` 可以在更换字符的同时保留段落的样式（标题、项目符号等）。

---

## 保存编辑后的文档

最后，将修改后的文档写回磁盘。你可以覆盖原文件，也可以像这里演示的那样生成一个新副本。

```java
        // Step 6: Save the edited document
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

打开 `output.docx` 时，你应该会看到第一段的语气明显更正式。如果 LLM 没有完全遵循指令，可微调提示或尝试不同的模型版本。

---

## 完整工作示例

下面是完整的程序代码——复制到 `LlmDemo.java`，调整路径后，用 `javac` + `java` 编译运行。

```java
import com.aspose.words.*;
import com.aspose.words.ai.*;

public class LlmDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Define the LLM endpoint (OpenAI‑compatible)
        AiModelEndpoint llmEndpoint = new AiModelEndpoint(
                "http://localhost:8000/v1",   // URL of your LLM server
                "my-api-key");                // API key if required

        // Step 2: Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // Step 3: Create a custom AI model that uses the endpoint
        AiModel llmModel = new AiModel(AiModelType.CUSTOM, llmEndpoint);

        // Step 4: Retrieve the first paragraph and ask the model to rewrite it
        Paragraph firstParagraph = document.getFirstSection()
                                            .getBody()
                                            .getParagraphs()
                                            .get(0);
        String rewrittenText = llmModel.editText(
                firstParagraph.getText(),
                "Make it more formal");

        // Step 5: Replace the original paragraph content with the rewritten text
        firstParagraph.removeAllChildren();
        firstParagraph.appendChild(new Run(document, rewrittenText));

        // Step 6: Save the edited document
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**预期输出：** 打开 `output.docx`，你会看到原始段落已被改写。例如，随意的句子 “We’ll get the thing done soon.” 可能会变为 “We shall complete the task promptly.” 具体措辞取决于所使用的模型。

---

## 常见问题与边缘情况

### 文档有多个章节怎么办？

上述代码仅处理 *第一个章节的第一段*。若要在整个文件中 **使用 AI 编辑段落**，可遍历 `document.getSections()`，随后遍历每个 `section.getBody().getParagraphs()`。记得跳过空段落，否则 LLM 会收到空字符串并返回空结果。

### 大段落超出 token 限制怎么办？

大多数 LLM 对输入限制在约 4 000 token。如果段落异常长，需要在调用 `editText` 前将其拆分为更小的块。`AiModel` 实例可以复用，只需注意本地服务器的速率限制。

### 能否使用其他指令，如 “summarize” 或 “translate to French”？

完全可以。`editText` 的第二个参数是自由文本。要生成摘要，可传入 `"Summarize in one sentence"`；要翻译，可传入 `"Translate to French, keep the tone formal"`。这种灵活性让你在不改动代码的前提下 **替换段落文本** 用于多种场景。

### 模型会保留段落的样式（字体、颜色）吗？

因为我们仅替换同一 `Paragraph` 对象内部的 `Run`，原有样式（标题级别、项目符号、缩进等）保持不变。如果需要更改样式，可在替换后操作 `Paragraph.getParagraphFormat()`。

### 我的 LLM 服务器要求使用自签名 HTTPS 证书怎么办？

`AiModelEndpoint` 支持 `https://` URL。如果证书不受信任，需要配置 Java 的 SSL 上下文以信任该证书，或让服务器使用有效证书。此设置超出本教程范围，但在 Java SSL 文档中有详细说明。

---

## 生产环境集成技巧

| 技巧 | 重要原因 |
|-----|----------|
| **缓存端点实例** | 每次请求重新创建 `AiModelEndpoint` 会增加开销。 |
| **批量编辑** | 若需处理大量段落，可一次性发送多个段落（如 JSON 数组），降低延迟。 |
| **校验 LLM 输出** | 在插入前务必检查返回的字符串是否为 null 或空。 |
| **记录提示与响应** | 有助于调试，也方便在处理法律文本时满足合规要求。 |
| **优雅降级** | 当 LLM 不可用时，可回退使用原段落或简单的启发式改写。 |

---

## 结论

我们展示了如何使用 Aspose.Words **创建自定义 AI 模型**，将其连接到兼容 OpenAI 的端点，并 **使用 AI 编辑段落** 以 **让文本更正式**。只需遵循以下六个步骤——定义端点、加载文档、初始化模型、获取并改写段落、替换段落内容、保存文档，即可在自己的项目中实现这一功能。

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}