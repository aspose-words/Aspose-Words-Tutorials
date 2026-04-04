---
category: general
date: 2026-04-04
description: Capture font substitution warnings while loading Word documents with
  Aspose.Words for Java and detect missing fonts automatically. Follow this step‑by‑step
  guide.
draft: false
keywords:
- capture font substitution warnings
- detect missing fonts
language: en
og_description: Capture font substitution warnings while loading Word docs with Aspose.Words
  for Java and detect missing fonts in a few easy steps.
og_title: Capture Font Substitution Warnings – Detect Missing Fonts
tags:
- Aspose.Words
- Java
- Document Processing
title: Capture Font Substitution Warnings – Detect Missing Fonts
url: /java/document-loading-and-saving/capture-font-substitution-warnings-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Capture Font Substitution Warnings – Detect Missing Fonts

Ever needed to **capture font substitution warnings** when opening a Word file, only to discover that a crucial typeface is missing? You're not alone. In many enterprise workflows a missing font can turn a perfectly formatted report into a garbled mess, and the only clue you get is a silent warning that most developers never see.

The good news is that Aspose.Words for Java lets you hook into the loading process and **detect missing fonts** before they bite you later. In this tutorial we’ll walk through a complete, runnable example that prints every substitution warning straight to the console, so you can decide whether to embed the right font, replace it, or alert the user.

By the end of this guide you’ll know how to:

* Set up a `LoadOptions` object with a custom warning callback.
* Filter the callback so it only reacts to font‑substitution events.
* Load any `.docx` file and see the warnings instantly.
* Extend the solution to log warnings, throw exceptions, or even auto‑install missing fonts.

No external documentation required—just a few lines of Java and the Aspose.Words JAR.

## Prerequisites

Before we dive in, make sure you have:

* Java 8 or newer installed (the latest LTS version works best).
* Aspose.Words for Java 23.11 or later – you can grab the Maven artifact or the plain JAR from the Aspose website.
* A Word document that references a font you don’t have on your development machine (e.g., “MyFancyFont”).  
* An IDE or text editor of your choice – I’m using IntelliJ IDEA, but Eclipse or VS Code will do fine.

If any of those sound unfamiliar, pause and install them first; the rest of the tutorial assumes they’re ready.

---

## Capture Font Substitution Warnings Using Aspose.Words

The core of the solution lives in a `LoadOptions` instance. By assigning an `IWarningCallback` we can intercept every warning the library emits during the load phase.

```java
import com.aspose.words.*;

public class FontDiagnosticsTutorial {
    public static void main(String[] args) throws Exception {

        // Step 1️⃣: Create LoadOptions and set a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Capture only font substitution warnings.
                if (info.getWarningType() == WarningType.SUBSTITUTED_FONT) {
                    System.out.println("Font substitution: " + info.getDescription());
                }
            }
        });

        // Step 2️⃣: Load the document. The callback runs automatically.
        Document doc = new Document("YOUR_DIRECTORY/document-with-missing-font.docx", loadOptions);

        // Step 3️⃣: If you reach this line, the document is loaded.
        // Any missing‑font warnings have already been printed to the console.
        System.out.println("Document loaded successfully.");
    }
}
```

**Why this works:**  
`LoadOptions` tells Aspose.Words how to treat the incoming file. The `IWarningCallback` interface is a hook that receives a `WarningInfo` object for *every* warning. By checking `info.getWarningType()` we filter out everything except `SUBSTITUTED_FONT`. The `description` property contains a human‑readable message like “Font 'MyFancyFont' was substituted with 'Arial'”.

### Expected console output

If the source document references a font that isn’t installed, you’ll see something like:

```
Font substitution: Font 'MyFancyFont' was substituted with 'Arial'.
Document loaded successfully.
```

If the document uses only fonts that exist on the machine, the callback stays silent and you just get the final “Document loaded successfully.” line.

---

## Detect Missing Fonts in Your Document

You might wonder, *“Is a substitution warning the same as a missing font?”* In most cases, yes—Aspose.Words substitutes a missing font with a fallback and reports it via `SUBSTITUTED_FONT`. However, there are edge cases where a font is present but the exact style (bold‑italic, specific OpenType features) isn’t, leading to a subtle substitution.

To be absolutely certain you’ve caught every gap, you can combine the warning callback with a post‑load inspection:

```java
// After loading the document, iterate through all runs.
for (Paragraph para : (Iterable<Paragraph>) doc.getFirstSection().getBody().getChildNodes(NodeType.PARAGRAPH, true)) {
    for (Run run : (Iterable<Run>) para.getChildNodes(NodeType.RUN, true)) {
        Font font = run.getFont();
        if (font.getName().equalsIgnoreCase("MyFancyFont")) {
            System.out.println("Run still uses the missing font: " + font.getName());
        }
    }
}
```

**Pro tip:** If you find any runs still referencing the missing font, you can replace them on the fly:

```java
font.setName("Arial"); // fallback
```

That way you guarantee a consistent visual result, even if the original warning was suppressed.

---

## Common Pitfalls & How to Avoid Them

| Pitfall | Why it Happens | Fix |
|---------|----------------|-----|
| **Forgetting to set the callback** | `LoadOptions` defaults to a no‑op callback, so warnings vanish. | Always call `loadOptions.setWarningCallback(...)` before loading. |
| **Using the wrong warning type** | `WarningType.SUBSTITUTED_FONT` is the only enum that signals missing fonts. | Filter on `WarningType.SUBSTITUTED_FONT` *exactly*; other types (e.g., `UNKNOWN_FILE_FORMAT`) are unrelated. |
| **Hard‑coding file paths** | Works locally but breaks on CI/CD pipelines. | Use a relative path or pass the file location as a command‑line argument. |
| **Ignoring Unicode fonts** | Some missing fonts are only a problem for certain characters. | Test with a document containing the full character set you expect to support. |
| **Running on a headless server without font config** | The server may lack any fallback fonts, causing unexpected substitutions. | Install a minimal set of common fonts (Arial, Times New Roman) on the server. |

---

## Extending the Solution

Now that you can **capture font substitution warnings**, you might want to:

* **Log warnings to a file** – replace `System.out.println` with a logger like SLF4J.
* **Throw an exception** – useful in automated pipelines where a missing font should fail the build:

```java
if (info.getWarningType() == WarningType.SUBSTITUTED_FONT) {
    throw new RuntimeException("Missing font detected: " + info.getDescription());
}
```

* **Auto‑install missing fonts** – download the required TTF/OTF at runtime and add it to the Java `GraphicsEnvironment`. That’s a more advanced scenario, but entirely possible.

---

## Diagram (optional)

![Capture font substitution warnings flow diagram showing LoadOptions → WarningCallback → Console output](capture-font-substitution-warnings-diagram.png)

*Alt text:* “Capture font substitution warnings flow diagram illustrating how Aspose.Words routes missing‑font warnings to a custom callback.”

---

## Conclusion

We’ve just covered how to **capture font substitution warnings** and **detect missing fonts** when loading Word documents with Aspose.Words for Java. By configuring a `LoadOptions` object and implementing a tiny `IWarningCallback`, you gain full visibility into the font‑fallback process, enabling you to log, replace, or abort on missing typefaces.

In a nutshell: set the callback, filter for `SUBSTITUTED_FONT`, load the document, and handle the output however your application needs. From here you can expand to logging frameworks, CI checks, or even automated font provisioning.

Want to go further? Try:

* **Embedding fonts** directly into the saved document (`doc.save(..., SaveOptions.createSaveOptions(SaveFormat.DOCX))` with `FontEmbeddingMode.EMBED_ALL`).
* **Generating a PDF** after fixing fonts, ensuring the final output looks exactly as intended.
* **Scanning an entire folder** of documents for missing fonts and producing a summary report.

That’s all for now—happy coding, and may your documents always render with the right typeface!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}