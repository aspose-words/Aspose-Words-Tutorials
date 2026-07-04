---
category: general
date: 2026-05-04
description: Create word document java using Aspose.Words and learn how to check grammar
  with a custom LLM. Step‑by‑step guide for Java developers.
draft: false
keywords:
- create word document java
- how to create docx
- how to check grammar
- use custom llm
language: en
og_description: Create word document java and see how to check grammar using a custom
  LLM. Complete Java tutorial with runnable code.
og_title: Create word document java with Custom LLM Grammar Check
tags:
- Java
- Aspose.Words
- LLM
title: Create word document java with Custom LLM Grammar Check
url: /java/ai-machine-learning-integration/create-word-document-java-with-custom-llm-grammar-check/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create word document java with Custom LLM Grammar Check

Ever wondered how to **create word document java** projects that also proofread themselves? You're not alone—many developers want a single pipeline that spits out a polished *.docx* file without juggling multiple tools. In this tutorial we’ll walk through exactly that, showing you **how to create docx** files with Aspose.Words, hook up a locally hosted LLM, and finally **how to check grammar** automatically. By the end you’ll have a self‑contained Java program that writes, validates, and saves a Word document—all while **using custom LLM** endpoints you control.

## What You’ll Need

Before we dive in, make sure you have the following on your workstation:

| Prerequisite | Why it matters |
|--------------|----------------|
| Java 17+ (or any recent JDK) | Modern language features and better module support |
| Aspose.Words for Java (latest version) | The library that lets you **create word document java** files programmatically |
| A locally hosted LLM server (e.g., Ollama, LMStudio) listening on `http://localhost:11434/api/generate` | Required for the **use custom llm** step that powers grammar checking |
| Maven or Gradle (we’ll use Maven in examples) | Simplifies dependency management |
| An IDE or text editor (IntelliJ IDEA, VS Code, etc.) | Makes coding and debugging easier |

If any of these sound unfamiliar, don’t panic—each item is free or has a community‑edition that works perfectly for learning purposes.

## Step 1 – Set Up Your Maven Project

To **create word document java** projects quickly, start with a minimal Maven `pom.xml`. This file pulls in the Aspose.Words library and any HTTP client you prefer (we’ll use Apache HttpClient).

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

> **Pro tip:** If you’re using Gradle, the same dependencies go under `implementation` in `build.gradle`.

Now run `mvn clean install` to pull the jars. Once the build succeeds you’re ready to write Java code that **creates word document java** files.

## Step 2 – Write the Java Class that **Creates word document java**

Below is the full, ready‑to‑run source file. It demonstrates the whole flow: initialize a blank document, configure a custom LLM endpoint, invoke grammar checking, and finally save the result.

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
> * `Document` is the core Aspose.Words class that represents a *.docx* in memory.  
> * `AiEndpoint` tells Aspose’s AI module where to send the prompt. By pointing it at `localhost:11434` we **use custom llm** instead of a cloud service.  
> * `checkGrammar` with `AiModelType.CUSTOM` forwards the document’s text to the LLM, receives corrected text, and rewrites the underlying Word nodes.  
> * Finally we call `save` to write the file to disk, giving you a polished Word file.

### Expected Output

After running `mvn exec:java -Dexec.mainClass="com.example.wordllmdemo.SelfHostedLLMDemo"` you should see:

```
Document saved to output/GrammarChecked.docx
```

Open the resulting `GrammarChecked.docx` in Microsoft Word (or LibreOffice). The original sentence *“Ths sentence has a typo and a grammer error.”* will now read *“This sentence has a typo and a grammar error.”* – proof that the **how to check grammar** step succeeded.

## Step 3 – How to create docx with Different Content (Optional)

If you want to generate richer documents—tables, images, or styled text—just keep using `DocumentBuilder`. Here’s a quick snippet that demonstrates adding a heading and a table:

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

You can sprinkle this code anywhere between the document‑creation block (Step 2.1) and the grammar‑check call (Step 2.3). The LLM will still receive the full text, so it can correct any natural‑language parts while leaving tables untouched.

## Step 4 – Dealing with Endpoint Issues (Use Custom LLM Safely)

When **using custom llm** endpoints, a few hiccups are common:

| Symptom | Likely cause | Fix |
|---------|--------------|-----|
| `Connection refused` error | LLM server not running or wrong port | Start Ollama (`ollama serve`) and verify `http://localhost:11434/api/generate` works with `curl`. |
| Response JSON missing `completion` field | Model name mismatch | Ensure the model you set (`llama3.1:8b`) is installed (`ollama list`). |
| Grammar check returns the original text unchanged | Prompt not recognized by LLM | Adjust the model’s system

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}