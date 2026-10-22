---
category: general
date: 2026-07-06
description: Crie DocumentConfig em Java para rastrear fontes ausentes usando Aspose.Words
  – um guia completo, passo a passo, para desenvolvedores.
draft: false
keywords:
- create documentconfig
- track missing fonts
language: pt
og_description: Crie DocumentConfig em Java para rastrear fontes ausentes com Aspose.Words.
  Aprenda todo o fluxo de trabalho, desde a configuração até o tratamento de avisos.
og_title: Criar DocumentConfig em Java – Rastrear fontes ausentes
schemas:
- author: Aspose
  dateModified: '2026-07-06'
  description: Create DocumentConfig in Java to track missing fonts using Aspose.Words
    – a complete, step‑by‑step guide for developers.
  headline: Create DocumentConfig in Java – Track Missing Fonts with Aspose.Words
  type: TechArticle
- description: Create DocumentConfig in Java to track missing fonts using Aspose.Words
    – a complete, step‑by‑step guide for developers.
  name: Create DocumentConfig in Java – Track Missing Fonts with Aspose.Words
  steps:
  - name: Prerequisites
    text: '| Requirement | Reason | |-------------|--------| | Java 8 or newer | Aspose.Words
      for Java supports JDK 8+. | | Aspose.Words for Java library (latest version)
      | Provides `DocumentConfig`, `IWarningCallback`, etc. | | An IDE or build tool
      (IntelliJ, Eclipse, Maven/Gradle) | To compile and run the sa'
  - name: Maven
    text: '```xml <dependency> <groupId>com.aspose</groupId> <artifactId>aspose-words</artifactId>
      <version>23.12</version> <!-- use the latest version --> </dependency> ```'
  - name: Gradle (Kotlin DSL)
    text: '```kotlin implementation("com.aspose:aspose-words:23.12") ```'
  type: HowTo
tags:
- Aspose.Words
- Java
- Font Substitution
title: Criar DocumentConfig em Java – Rastrear fontes ausentes com Aspose.Words
url: /pt/java/licensing-and-configuration/create-documentconfig-in-java-track-missing-fonts-with-aspos/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar DocumentConfig em Java – Rastrear Fontes Ausentes com Aspose.Words

**Create DocumentConfig in Java** para monitorar avisos de substituição de fontes ao carregar um documento Word. Já se perguntou por que alguns caracteres parecem estranhos depois de abrir um DOCX? É provável que a fonte original não esteja na máquina, e o Aspose.Words a substitua silenciosamente. Neste tutorial, mostraremos exatamente como **rastrear fontes ausentes** para que você nunca seja surpreendido por um glifo fora do lugar novamente.

Vamos percorrer tudo o que você precisa: a configuração Maven/Gradle, o código que cria um `DocumentConfig`, um `IWarningCallback` personalizado que filtra apenas alertas de substituição de fontes e uma maneira rápida de registrar essas mensagens. Ao final, você terá um exemplo executável que imprime cada aviso de fonte ausente no console (ou em um arquivo, se preferir).

---

## What You’ll Learn

- Por que um `DocumentConfig` é o local correto para interceptar eventos de substituição de fontes.  
- Como **rastrear fontes ausentes** sem poluir seus logs com avisos não relacionados.  
- Um programa Java completo, pronto para copiar e colar, que demonstra a técnica.  
- Dicas para estender a solução — por exemplo, gravar avisos em um banco de dados ou enviar alertas por e‑mail.

### Prerequisites

| Requirement | Reason |
|-------------|--------|
| Java 8 or newer | Aspose.Words for Java supports JDK 8+. |
| Aspose.Words for Java library (latest version) | Provides `DocumentConfig`, `IWarningCallback`, etc. |
| An IDE or build tool (IntelliJ, Eclipse, Maven/Gradle) | To compile and run the sample. |
| A DOCX file that references fonts you don’t have installed | To see the warning in action. |

If you already have a project, just add the Aspose dependency and you’re good to go.

---

## Step 1: Add Aspose.Words to Your Build

### Maven

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- use the latest version -->
</dependency>
```

### Gradle (Kotlin DSL)

```kotlin
implementation("com.aspose:aspose-words:23.12")
```

> **Pro tip:** The free trial version works perfectly for testing, but remember to apply a license for production to remove the evaluation watermark.

---

## Step 2: Create DocumentConfig and Register a Warning Callback

The heart of the solution lives in this snippet. We **create a DocumentConfig**, attach a custom `IWarningCallback`, and tell it to **track missing fonts** only.

```java
import com.aspose.words.*;

public class FontSubstitutionDiagnostics {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a configuration object.
        DocumentConfig config = new DocumentConfig();

        // 2️⃣ Attach a warning callback that reacts only to font‑substitution warnings.
        config.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // 3️⃣ Filter for FONT_SUBSTITUTION type.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    // 4️⃣ This is where we **track missing fonts**.
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });

        // 5️⃣ Load the document using the configuration we just prepared.
        Document doc = new Document("YOUR_DIRECTORY/input.docx", config);

        // Optional: do something with the document, e.g., save as PDF.
        // doc.save("output.pdf");
    }
}
```

**Why this works:** When Aspose.Words parses a document, it emits `WarningInfo` objects for any irregularities. By providing a callback, you intercept those warnings *before* they disappear into the void. The `if` check guarantees we only **track missing fonts**, ignoring other warnings like deprecated tags or unsupported features.

---

## Step 3: Run the Example and Observe the Output

Place a DOCX that references a font you don’t have (e.g., “Comic Sans MS” on a Linux box). Execute the program:

```bash
$ javac -cp "aspose-words-23.12.jar" FontSubstitutionDiagnostics.java
$ java -cp ".:aspose-words-23.12.jar" FontSubstitutionDiagnostics
```

You should see something similar to:

```
Font substituted: Font "Comic Sans MS" was not found. Substituted with "Arial".
Font substituted: Font "Times New Roman" was not found. Substituted with "Liberation Serif".
```

Each line corresponds to a missing font that Aspose automatically replaced. If no missing fonts exist, the program stays silent—exactly what you want for a clean log.

---

## Step 4: Persist the Missing‑Font List (Optional)

Printing to the console is handy for demos, but in a real‑world service you’d likely store the data. Here’s a quick way to write the warnings to a text file.

```java
import java.io.FileWriter;
import java.io.IOException;

public class FontSubstitutionDiagnostics {

    private static final String LOG_PATH = "missing-fonts.log";

    public static void main(String[] args) throws Exception {
        DocumentConfig config = new DocumentConfig();

        config.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) throws IOException {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    String message = "Font substituted: " + info.getDescription();
                    System.out.println(message);
                    try (FileWriter fw = new FileWriter(LOG_PATH, true)) {
                        fw.write(message + System.lineSeparator());
                    }
                }
            }
        });

        Document doc = new Document("YOUR_DIRECTORY/input.docx", config);
    }
}
```

Now every missing‑font event appends a line to `missing-fonts.log`. You can later parse that file, feed it into a monitoring dashboard, or even trigger an alert if a critical font disappears from your server.

---

## Step 5: Common Pitfalls and How to Avoid Them

| Symptom | Likely Cause | Fix |
|---------|--------------|-----|
| No warnings appear even though the DOCX uses unknown fonts | Callback not registered or `setWarningCallback` called after loading the document | Ensure `config.setWarningCallback(...)` is executed **before** creating the `Document` instance. |
| Application crashes with `NullPointerException` | `info.getDescription()` returns `null` for some rare warning types | Guard against null: `String desc = info.getDescription(); if (desc != null) …` |
| Too many unrelated warnings flood the console | Callback filters only `FONT_SUBSTITUTION`? | Double‑check the `if (info.getWarningType() == WarningType.FONT_SUBSTITUTION)` condition. |
| Performance slowdown on large batches | Writing to file synchronously for each warning | Batch writes or use a `BufferedWriter` to reduce I/O overhead. |

---

## Step 6: Extending the Solution – From Console to Enterprise

- **Database logging:** Replace the `FileWriter` with a JDBC insert; store `documentName`, `missingFont`, and `timestamp`.  
- **Email alerts:** Hook into JavaMail; send a summary after processing a batch of documents.  
- **Custom substitution logic:** Instead of letting Aspose pick a fallback, you could load a local font collection via `FontSettings.setFontsFolder()` and re‑run the load if a substitution occurs.

These extensions keep the core idea—**create documentconfig** and **track missing fonts**—intact while scaling to production needs.

---

## Conclusion

You now have a solid, copy‑and‑paste‑ready pattern for **creating a DocumentConfig** in Java and using it to **track missing fonts** with Aspose.Words. The approach is lightweight, requires only a few lines of code, and gives you full control over how font‑substitution warnings are handled. Whether you’re building a document‑conversion service, an automated report generator, or a compliance audit tool, knowing exactly which fonts are missing can save hours of debugging.

Next steps? Try swapping the console output for a structured JSON log, or integrate the callback into a Spring Boot microservice that processes uploads in real time. And if you run into any edge cases—say, a custom OpenType font that Aspose can’t parse—drop a comment below; we’ll troubleshoot together.

Happy coding, and may your PDFs always render with the fonts you expect!

## What Should You Learn Next?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Using Fonts in Aspose.Words for Java](/words/english/java/using-document-elements/using-fonts/)
- [Customize Theme Colors & Fonts in Aspose.Words Java: A Comprehensive Guide](/words/english/java/formatting-styles/customize-theme-colors-fonts-aspose-words-java/)
- [How to Create PDF Documents with Aspose.Words for Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}