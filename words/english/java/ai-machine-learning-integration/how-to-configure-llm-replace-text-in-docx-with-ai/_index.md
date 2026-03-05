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
language: en
og_description: How to configure LLM for Document AI and replace text in DOCX using
  AI – complete guide with runnable Java code.
og_title: How to Configure LLM – Replace Text in DOCX with AI
tags:
- LLM
- Document AI
- Java
- DOCX
title: How to Configure LLM – Replace Text in DOCX with AI
url: /java/ai-machine-learning-integration/how-to-configure-llm-replace-text-in-docx-with-ai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to Configure LLM – Replace Text in DOCX with AI

Ever wondered **how to configure LLM** so it can edit a Word file for you? You're not the only one. Many developers hit a wall when they need to programmatically replace a phrase inside a `.docx` without opening Microsoft Word. The good news? With a local LLM and a tiny Document AI wrapper, you can swap out text in a DOCX file in just a few lines of Java.

In this tutorial we’ll walk through the entire process: from wiring up the LLM connection, loading a DOCX, to using **Document AI** to replace a target phrase. By the end you’ll have a self‑contained, runnable example that you can drop into any Maven or Gradle project. No external API keys, no cloud fees—just your own model listening on `http://localhost:8080/v1`.

> **Quick win:** If you already have a local LLM (like Llama 3 or Mistral) exposing an OpenAI‑compatible endpoint, the code below works out‑of‑the‑box.

---

![Diagram of how to configure LLM for Document AI](/images/configure-llm-diagram.png){: .center-image alt="how to configure llm diagram"}

## What You’ll Need

- **Java 17** (or any recent JDK)  
- A **local LLM** exposing an OpenAI‑style `/v1` endpoint (e.g., Ollama, LMStudio)  
- The **Document AI Java library** (assume `com.example:document-ai:1.2.0` on Maven Central)  
- A sample DOCX file (`input.docx`) placed in a known folder  

If you’re missing any of these, spin up Ollama quickly:

```bash
ollama serve &
ollama run llama3
```

That will start a server on `http://localhost:8080/v1` ready to accept requests.

---

## How to Configure LLM for Document AI

The first thing we do is tell the `DocumentAi` client where to find the model and which model to use. This is the **how to configure LLM** step that many tutorials gloss over.

```java
// Step 1: Set up the LLM connection details
AiModelConfig modelConfig = new AiModelConfig();
modelConfig.setBaseUrl("http://localhost:8080/v1");   // Local server address
modelConfig.setApiKey("dummy");                       // Not needed for local models, but the client expects a value
modelConfig.setModelName("local-llm");                // Replace with your model's identifier
```

*Why this matters:*  
The `AiModelConfig` object abstracts away the HTTP details, letting `DocumentAi` focus on the content. If you ever switch to a hosted provider, you only change the `baseUrl` and `apiKey`—the rest of your code stays untouched.

---

## Load and Prepare the DOCX Document

Next we bring the Word file into memory. The `Document` class handles both `.docx` and `.pdf` under the hood, but here we only care about DOCX.

```java
// Step 2: Load the DOCX you want to edit
Path docPath = Paths.get("YOUR_DIRECTORY/input.docx");
Document inputDocument = new Document(docPath.toFile());
```

*Pro tip:* Use an absolute path during debugging to avoid the “file not found” surprise. Once you’re confident, switch back to a relative path for portability.

---

## Replace Text in DOCX Using AI

Now comes the heart of the tutorial—**how to replace text** in a DOCX file with AI assistance. The `replaceText` method sends the document contents to the LLM, asks it to perform the substitution, and returns the revised text.

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

*What’s happening behind the scenes?*  
`DocumentAi` serialises the DOCX into plain text, builds a prompt like:

> “In the following document, replace every occurrence of ‘old phrase’ with ‘new phrase’ and return only the updated text.”

The LLM processes the request and sends back the modified content. This approach works even when the phrase spans multiple runs or paragraphs—something plain string replacement often misses.

---

## Verify and Output the Revised Text

Finally we print the AI‑revised text to the console. In a real‑world app you’d probably write the result back to a new DOCX, but printing lets you verify quickly.

```java
// Step 5: Show the AI‑revised output
System.out.println("AI‑revised text:");
System.out.println("-----------------------------------");
System.out.println(revisedText);
```

**Expected output** (assuming the original DOCX contained “This is the old phrase we want to change.”):

```
AI‑revised text:
-----------------------------------
This is the new phrase we want to change.
```

If you see the new phrase appear, congratulations—**you’ve just learned how to use Document AI to replace a phrase with AI**.

---

## Full Working Example

Putting everything together, here’s a complete, ready‑to‑run Java class. Feel free to copy‑paste into `src/main/java/com/example/ReplaceInDocx.java`.

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

### How to Run

```bash
# Compile
mvn clean compile

# Execute
mvn exec:java -Dexec.mainClass="com.example.ReplaceInDocx"
```

Make sure the LLM server is up before you run the program; otherwise you’ll get a connection timeout.

---

## Edge Cases & Common Pitfalls

| Situation | What to Watch For | Suggested Fix |
|-----------|-------------------|---------------|
| **Phrase not found** | The LLM returns the original text unchanged. | Double‑check spelling and case‑sensitivity; you can add `ignoreCase:true` to the prompt if your wrapper supports it. |
| **Large documents (>5 MB)** | Prompt size may exceed the model’s token limit. | Split the DOCX into sections, process each separately, then concatenate the results. |
| **Local LLM returns errors** | Often caused by mismatched model name. | Verify the model name in the LLM UI (`ollama list`) matches `modelConfig.setModelName`. |
| **Unicode characters get garbled** | Encoding issues when reading the DOCX. | Ensure your Java runtime uses UTF‑8 (add `-Dfile.encoding=UTF-8` to JVM args). |

---

## Next Steps

Now that you know **how to replace text in DOCX** with AI, you might want to explore:

- **How to use Document AI** for more complex tasks like table extraction or style preservation.  
- **Replace phrase with AI** in PDFs by swapping the `Document` constructor argument.  
- **Batch processing**: loop over a directory of DOCX files and apply the same replacement.  

Each of these builds on the same `AiModelConfig` and `DocumentAi` foundation, so you won’t have to start from scratch

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}