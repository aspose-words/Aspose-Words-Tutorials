---
category: general
date: 2026-03-25
description: Create custom AI model to edit Word documents – learn how to make text
  more formal, replace paragraph text, and rewrite a Word paragraph using Aspose.Words
  AI.
draft: false
keywords:
- create custom ai model
- make text more formal
- replace paragraph text
- edit paragraph with ai
- rewrite word paragraph
language: en
og_description: Create custom AI model to edit Word documents. Learn how to make text
  more formal, replace paragraph text, and rewrite a Word paragraph using Aspose.Words
  AI.
og_title: Create Custom AI Model – Edit Word Paragraphs in Java
tags:
- Aspose.Words
- Java
- AI integration
title: Create Custom AI Model – Edit Word Paragraphs in Java
url: /java/ai-machine-learning-integration/create-custom-ai-model-edit-word-paragraphs-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create Custom AI Model – Edit Word Paragraphs in Java

Ever needed to **create custom AI model** that can polish a paragraph inside a Word file? Maybe you have a batch of contracts that all sound a little too casual, and you’d love to make text more formal with a single line of code. The good news is you can do exactly that—no external services, no heavyweight SDKs, just Aspose.Words for Java and an OpenAI‑compatible endpoint.

In this tutorial we’ll walk through every step required to **create custom AI model**, hook it up to a local LLM server, and then use it to *replace paragraph text* with a more formal version. By the end you’ll have a runnable Java program that **edit paragraph with AI**, rewrites a Word paragraph, and saves the result back to disk. No fluff, just a practical solution you can copy‑paste into your own project.

> **What you’ll need**  
> • Java 17 or newer (the code compiles with earlier versions, but 17 is the sweet spot)  
> • Aspose.Words for Java 23.9 (or the latest release)  
> • A running OpenAI‑compatible LLM server (e.g., Ollama, LocalAI) listening on `http://localhost:8000/v1`  
> • An input Word document (`input.docx`) placed in a folder you control  

If you’re wondering *why bother building a custom model* instead of calling OpenAI directly, the answer is flexibility: you control the endpoint, you can swap models without code changes, and you keep any API keys out of your source repository. Let’s dive in.

---

## Create Custom AI Model – Setup and Configuration

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

## Load the Word Document

Now we bring the source file into memory. `Document` can read `.docx`, `.doc`, `.rtf`, and many other formats, but for this example we stick with `.docx`.

```java
        // Step 2: Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

Make sure `YOUR_DIRECTORY` points to a real folder; otherwise you’ll hit a `FileNotFoundException`. In a real‑world app you might pass the path as a command‑line argument or read it from a config file.

---

## Initialize the Custom AI Model

We create an `AiModel` of type `CUSTOM` and give it the endpoint we defined earlier. This tells Aspose.Words to route all AI calls through our own server.

```java
        // Step 3: Create a custom AI model that uses the endpoint
        AiModel llmModel = new AiModel(AiModelType.CUSTOM, llmEndpoint);
```

Behind the scenes Aspose.Words builds a tiny HTTP client that talks to the LLM using the standard OpenAI chat/completion schema. That’s why the endpoint must be *OpenAI‑compatible*.

---

## Retrieve and Rewrite the First Paragraph

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

## Replace the Original Paragraph Content

Now we **replace paragraph text** inside the Word object model. We clear out any existing runs (the low‑level pieces of text) and insert a new `Run` containing the AI‑generated string.

```java
        // Step 5: Replace the original paragraph content with the rewritten text
        firstParagraph.removeAllChildren();
        firstParagraph.appendChild(new Run(document, rewrittenText));
```

Be careful not to call `firstParagraph.setText()`—that method would strip out any formatting. Using `Run` preserves the paragraph’s style (heading, bullet, etc.) while swapping the actual characters.

---

## Save the Edited Document

Finally, we write the modified document back to disk. You can overwrite the original file or, as we do here, create a fresh copy.

```java
        // Step 6: Save the edited document
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

When you open `output.docx` you should see the first paragraph now sounding considerably more formal. If the LLM didn’t follow the instruction perfectly, you can tweak the prompt or try a different model version.

---

## Full Working Example

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

## Common Questions & Edge Cases

### What if my document has multiple sections?

The code above only touches the *first* paragraph of the *first* section. To **edit paragraph with AI** across the whole file, loop through `document.getSections()` and then each `section.getBody().getParagraphs()`. Remember to skip empty paragraphs, otherwise the LLM receives an empty string and returns nothing.

### How do I handle large paragraphs that exceed token limits?

Most LLMs cap input at around 4 000 tokens. If a paragraph is unusually long, split it into smaller chunks before calling `editText`. You can reuse the same `AiModel` instance; just be mindful of rate limits on your local server.

### Can I use a different instruction, like “summarize” or “translate to French”?

Absolutely. The second argument to `editText` is free‑form. For a summary you might pass `"Summarize in one sentence"`. For translation, `"Translate to French, keep the tone formal"` works just as well. This flexibility lets you **replace paragraph text** for many scenarios without changing any code.

### Does the model preserve paragraph styling (fonts, colors)?

Because we only replace the `Run` inside the same `Paragraph` object, existing styles (heading level, bullet list, indentation) stay intact. If you need to change the style itself, you can manipulate `Paragraph.getParagraphFormat()` after the replacement.

### What if my LLM server requires HTTPS with a self‑signed certificate?

`AiModelEndpoint` accepts a URL with `https://`. If the certificate isn’t trusted, you’ll need to configure Java’s SSL context to trust it, or run the server with a valid cert. That setup is outside the scope of this tutorial but well‑documented in the Java SSL guides.

---

## Tips for Production‑Ready Integration

| Tip | Why it matters |
|-----|----------------|
| **Cache the endpoint** | Re‑creating `AiModelEndpoint` on every request adds overhead. |
| **Batch edits** | If you have many paragraphs, send them in a single request (e.g., JSON array) to reduce latency. |
| **Validate LLM output** | Always check the returned string for null or empty values before inserting. |
| **Log prompts and responses** | Helpful for debugging and for compliance when you’re rewriting legal text. |
| **Graceful fallback** | If the LLM is down, fall back to the original paragraph or a simple heuristic rewrite. |

---

## Conclusion

We’ve shown you how to **create custom AI model** with Aspose.Words, connect it to an OpenAI‑compatible endpoint, and then **edit paragraph with AI** to **make text more formal**. By following the six steps—define the endpoint, load the document, initialize the model,

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}