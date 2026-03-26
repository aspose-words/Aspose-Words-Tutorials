---
category: general
date: 2026-03-25
description: 建立自訂 AI 模型以編輯 Word 文件——學習如何使文字更正式、取代段落文字，以及使用 Aspose.Words AI 重新撰寫 Word
  段落。
draft: false
keywords:
- create custom ai model
- make text more formal
- replace paragraph text
- edit paragraph with ai
- rewrite word paragraph
language: zh-hant
og_description: 建立自訂 AI 模型以編輯 Word 文件。了解如何讓文字更正式、取代段落文字，以及使用 Aspose.Words AI 重新撰寫
  Word 段落。
og_title: 建立自訂 AI 模型 – 在 Java 中編輯 Word 段落
tags:
- Aspose.Words
- Java
- AI integration
title: 建立自訂 AI 模型 – 在 Java 中編輯 Word 段落
url: /zh-hant/java/ai-machine-learning-integration/create-custom-ai-model-edit-word-paragraphs-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 建立自訂 AI 模型 – 在 Java 中編輯 Word 段落

Ever needed to **create custom AI model** that can polish a paragraph inside a Word file? Maybe you have a batch of contracts that all sound a little too casual, and you’d love to make text more formal with a single line of code. The good news is you can do exactly that—no external services, no heavyweight SDKs, just Aspose.Words for Java and an OpenAI‑compatible endpoint.

In this tutorial we’ll walk through every step required to **create custom AI model**, hook it up to a local LLM server, and then use it to *replace paragraph text* with a more formal version. By the end you’ll have a runnable Java program that **edit paragraph with AI**, rewrites a Word paragraph, and saves the result back to disk. No fluff, just a practical solution you can copy‑paste into your own project.

> **What you’ll need**  
> • Java 17 or newer (the code compiles with earlier versions, but 17 is the sweet spot)  
> • Aspose.Words for Java 23.9 (or the latest release)  
> • A running OpenAI‑compatible LLM server (e.g., Ollama, LocalAI) listening on `http://localhost:8000/v1`  
> • An input Word document (`input.docx`) placed in a folder you control  

If you’re wondering *why bother building a custom model* instead of calling OpenAI directly, the answer is flexibility: you control the endpoint, you can swap models without code changes, and you keep any API keys out of your source repository. Let’s dive in.

---

## 建立自訂 AI 模型 – 設定與配置

First we need to tell Aspose.Words where our LLM lives. The `AiModelEndpoint` class holds the URL and optional API key. Because we’re using a local server, the key can be an empty string, but the parameter is required.

```java
import com.aspose.words.ai.*;

public class LlmDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Define the LLM endpoint (OpenAI‑compatible)
        AiModelEndpoint llmEndpoint = new AiModelEndpoint(
                "http://localhost:8000/v1",   // URL of your LLM server
                "my-api-key");                // API key if required
```

> **Pro tip:** If you ever switch to a hosted model (e.g., Azure OpenAI), just change the URL and key—no other code changes needed.

---

## 載入 Word 文件

Now we bring the source file into memory. `Document` can read `.docx`, `.doc`, `.rtf`, and many other formats, but for this example we stick with `.docx`.

```java
        // Step 2: Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

Make sure `YOUR_DIRECTORY` points to a real folder; otherwise you’ll hit a `FileNotFoundException`. In a real‑world app you might pass the path as a command‑line argument or read it from a config file.

---

## 初始化自訂 AI 模型

We create an `AiModel` of type `CUSTOM` and give it the endpoint we defined earlier. This tells Aspose.Words to route all AI calls through our own server.

```java
        // Step 3: Create a custom AI model that uses the endpoint
        AiModel llmModel = new AiModel(AiModelType.CUSTOM, llmEndpoint);
```

Behind the scenes Aspose.Words builds a tiny HTTP client that talks to the LLM using the standard OpenAI chat/completion schema. That’s why the endpoint must be *OpenAI‑compatible*.

---

## 取得並改寫第一段落

Here’s where we actually **make text more formal**. We grab the first paragraph, send its raw text to the model with a prompt, and receive the edited version.

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

The second argument (`"Make it more formal"`) is the instruction we give the model. You can replace it with any directive—**replace paragraph text**, **summarize**, **translate**, etc. The method returns a plain string, which we’ll later insert back into the document.

> **Why this works:** `editText` sends a JSON payload like `{ "model": "...", "messages": [{ "role":"user", "content":"<text>\nMake it more formal"}] }`. The LLM sees the original paragraph and the instruction, then replies with the revised text.

---

## 取代原始段落內容

Now we **replace paragraph text** inside the Word object model. We clear out any existing runs (the low‑level pieces of text) and insert a new `Run` containing the AI‑generated string.

```java
        // Step 5: Replace the original paragraph content with the rewritten text
        firstParagraph.removeAllChildren();
        firstParagraph.appendChild(new Run(document, rewrittenText));
```

Be careful not to call `firstParagraph.setText()`—that method would strip out any formatting. Using `Run` preserves the paragraph’s style (heading, bullet, etc.) while swapping the actual characters.

---

## 儲存已編輯的文件

Finally, we write the modified document back to disk. You can overwrite the original file or, as we do here, create a fresh copy.

```java
        // Step 6: Save the edited document
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

When you open `output.docx` you should see the first paragraph now sounding considerably more formal. If the LLM didn’t follow the instruction perfectly, you can tweak the prompt or try a different model version.

---

## 完整範例程式

Below is the complete program—copy it into `LlmDemo.java`, adjust the paths, and run it with `javac` + `java`.

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

**Expected output:** Open `output.docx` and you’ll see the original paragraph transformed. For example, a casual sentence like “We’ll get the thing done soon.” might become “We shall complete the task promptly.” The exact wording depends on the model you’re using.

---

## 常見問題與邊緣情況

### 如果我的文件有多個節？

The code above only touches the *first* paragraph of the *first* section. To **edit paragraph with AI** across the whole file, loop through `document.getSections()` and then each `section.getBody().getParagraphs()`. Remember to skip empty paragraphs, otherwise the LLM receives an empty string and returns nothing.

### 如何處理超過 token 限制的大段落？

Most LLMs cap input at around 4 000 tokens. If a paragraph is unusually long, split it into smaller chunks before calling `editText`. You can reuse the same `AiModel` instance; just be mindful of rate limits on your local server.

### 我可以使用不同的指示，例如「summarize」或「translate to French」嗎？

Absolutely. The second argument to `editText` is free‑form. For a summary you might pass `"Summarize in one sentence"`. For translation, `"Translate to French, keep the tone formal"` works just as well. This flexibility lets you **replace paragraph text** for many scenarios without changing any code.

### 模型會保留段落樣式（字型、顏色）嗎？

Because we only replace the `Run` inside the same `Paragraph` object, existing styles (heading level, bullet list, indentation) stay intact. If you need to change the style itself, you can manipulate `Paragraph.getParagraphFormat()` after the replacement.

### 如果我的 LLM 伺服器需要使用自簽憑證的 HTTPS？

`AiModelEndpoint` accepts a URL with `https://`. If the certificate isn’t trusted, you’ll need to configure Java’s SSL context to trust it, or run the server with a valid cert. That setup is outside the scope of this tutorial but well‑documented in the Java SSL guides.

---

## 生產環境整合技巧

| Tip | Why it matters |
|-----|----------------|
| **Cache the endpoint** | Re‑creating `AiModelEndpoint` on every request adds overhead. |
| **Batch edits** | If you have many paragraphs, send them in a single request (e.g., JSON array) to reduce latency. |
| **Validate LLM output** | Always check the returned string for null or empty values before inserting. |
| **Log prompts and responses** | Helpful for debugging and for compliance when you’re rewriting legal text. |
| **Graceful fallback** | If the LLM is down, fall back to the original paragraph or a simple heuristic rewrite. |

---

## 結論

We’ve shown you how to **create custom AI model** with Aspose.Words, connect it to an OpenAI‑compatible endpoint, and then **edit paragraph with AI** to **make text more formal**. By following the six steps—define the endpoint, load the document, initialize the model,

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}