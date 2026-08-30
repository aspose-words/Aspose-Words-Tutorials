---
category: general
date: 2026-06-27
description: Learn how to capture font substitution warnings in Java using Aspose.Words.
  This step‑by‑step tutorial also covers warning callbacks and LoadOptions usage.
draft: false
keywords:
- capture font substitution warnings
- Aspose.Words warning callback
- Java LoadOptions example
- font substitution handling
- document processing with Aspose
language: en
og_description: Capture font substitution warnings in Java with Aspose.Words. Follow
  this guide to set up warning callbacks, use LoadOptions, and handle missing fonts.
og_title: Capture Font Substitution Warnings in Java – Aspose.Words Tutorial
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to capture font substitution warnings in Java using Aspose.Words.
    This step‑by‑step tutorial also covers warning callbacks and LoadOptions usage.
  headline: Capture Font Substitution Warnings in Java with Aspose.Words – Complete
    Guide
  type: TechArticle
- questions:
  - answer: Yes. The warning callback is format‑agnostic; it fires for any document
      type that Aspose.Words loads (DOC, DOCX, RTF, HTML, etc.). The only difference
      is the set of warnings that may appear.
    question: Does this work with PDF or other formats?
  - answer: Absolutely. Inside the `warning` method, inspect `info.getWarningType()`
      for other enum values such as `WarningType.IMAGE_RESOLUTION`. Then handle them
      accordingly.
    question: Can I capture other warning types, like *image resolution* warnings?
  - answer: 'Store each `info.getDescription()` in a `List<String>` inside the callback.
      After loading, you’ll have a collection you can log, send to a monitoring service,
      or use to trigger a font‑download routine. ## Conclusion You now know **how
      to capture font substitution warnings** in Java using Aspose.Word'
    question: What if I need the list of substituted fonts after the document loads?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Document Conversion
title: Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide
url: /java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide

Ever needed to **capture font substitution warnings** while loading a DOCX that uses exotic typefaces? You're not the only one. In many real‑world projects—think automated report generators or batch document converters—missing fonts trigger silent substitutions that can ruin layout fidelity.  

Fortunately, Aspose.Words gives you a clean way to listen for those warnings. In this tutorial we'll walk through configuring **LoadOptions**, wiring an **Aspose.Words warning callback**, and printing every *font substitution* notice to the console. By the end you'll know exactly when a font has been swapped and how to react programmatically.

> **What you'll get:** a fully runnable Java snippet, an explanation of *why* each piece matters, and tips for handling edge cases like custom font directories.

## Prerequisites & What You’ll Need

Before we dive in, make sure you have:

- Java 8 or newer installed (the code works with Java 11+ as well).
- The latest Aspose.Words for Java JAR (download from the official site or Maven Central).
- A DOCX file that references fonts not installed on your machine (e.g., a *font‑rich.docx* you can find in the Aspose demo set).
- A decent IDE (IntelliJ IDEA, Eclipse, or even VS Code with Java extensions).

No external libraries beyond Aspose.Words are required, and the example runs in a plain `main` method.

## Step 1: Set Up LoadOptions – The Entry Point for Custom Loading

`LoadOptions` is Aspose.Words’ configuration bag that tells the library *how* to read a document. By default it silently substitutes missing fonts, but you can change that behavior with a warning callback.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions to customize loading behavior
        LoadOptions loadOptions = new LoadOptions();
```

**Why this matters:** Without `LoadOptions`, the document loads quietly, and you lose visibility into missing fonts. By creating an instance you gain a hook for the warning system.

## Step 2: Define a Warning Callback to *Capture Font Substitution Warnings*

Aspose.Words pushes warning events through the `IWarningCallback` interface. Implement it inline (or as a separate class) and filter for `WarningType.FONT_SUBSTITUTION`.

```java
        // Step 2: Define a warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Only react to font substitution warnings
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });
```

**Explanation:**  
- `info.getWarningType()` tells you the category of the warning.  
- `WarningType.FONT_SUBSTITUTION` is the enum value we care about.  
- `info.getDescription()` contains a human‑readable message, e.g., *“Font 'Comic Sans MS' not found, substituted with 'Arial'.”*  

By printing the description, you **capture font substitution warnings** in real time.

## Step 3: Load the Document Using the Configured LoadOptions

Now that the callback is in place, load your DOCX. The warning callback fires automatically during parsing.

```java
        // Step 3: Load the document using the configured LoadOptions
        Document document = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);
```

Replace `YOUR_DIRECTORY` with the actual path to your test file. When the `Document` constructor runs, any missing font triggers the callback defined earlier, and you’ll see the substitution messages on the console.

## Step 4: Verify the Loaded Document (Optional but Helpful)

After loading, you might want to confirm the document's integrity—page count, text extraction, etc. This step isn’t required for capturing warnings, but it helps you see the impact of substitutions.

```java
        // Optional: Output basic document info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + document.getPageCount());
```

If a font was substituted, the layout may shift slightly; checking the page count can reveal such changes.

## Step 5: Advanced – Handling Substituted Fonts Programmatically

Sometimes you don’t just want to log the warning—you might need to embed a fallback font or adjust styling. Below is a quick pattern you can adopt.

```java
        // Advanced: Register a fallback font folder to reduce substitutions
        FontSettings fontSettings = new FontSettings();
        // Point to a folder that contains the missing fonts
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);
```

By pointing Aspose.Words to a folder that contains the original fonts, you can *prevent* substitution altogether. If the folder is missing, the warning callback still captures the event, giving you a fallback strategy.

## Full Working Example

Putting it all together, here’s the complete, ready‑to‑run program:

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Initialize LoadOptions
        LoadOptions loadOptions = new LoadOptions();

        // Set up warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });

        // OPTIONAL: Register a custom fonts folder to avoid substitution
        FontSettings fontSettings = new FontSettings();
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);

        // Load the document – warnings will be printed automatically
        Document doc = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);

        // Verify basic info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + doc.getPageCount());
    }
}
```

**Expected console output** (when a missing font is encountered):

```
Font substituted: Font 'Pacifico' not found, substituted with 'Arial'.
Document loaded successfully.
Page count: 3
```

If all fonts are present, the callback remains silent—nothing is printed, which is exactly what you’d expect.

## Common Pitfalls & Pro Tips

| Pitfall | Why it happens | Fix |
|---------|----------------|-----|
| **Callback never fires** | You forgot to attach the callback to `LoadOptions` **or** used the default constructor of `Document` without passing `loadOptions`. | Always call `loadOptions.setWarningCallback(...)` **and** use the `new Document(path, loadOptions)` overload. |
| **Too many warnings clutter the log** | Large documents with many missing fonts generate a warning per substitution. | Filter further by checking `info.getDescription()` for specific font names, or aggregate warnings in a list for later processing. |
| **Substituted fonts affect layout** | The fallback font may have a different metric (size, spacing). | Provide a custom fonts folder (see Step 5) or adjust the document’s style after loading. |
| **Running on a headless server** | The default font fallback may rely on system fonts not installed on the server. | Ship the required fonts with your application and point `FontSettings` to that folder. |

## Frequently Asked Questions

**Q: Does this work with PDF or other formats?**  
A: Yes. The warning callback is format‑agnostic; it fires for any document type that Aspose.Words loads (DOC, DOCX, RTF, HTML, etc.). The only difference is the set of warnings that may appear.

**Q: Can I capture other warning types, like *image resolution* warnings?**  
A: Absolutely. Inside the `warning` method, inspect `info.getWarningType()` for other enum values such as `WarningType.IMAGE_RESOLUTION`. Then handle them accordingly.

**Q: What if I need the list of substituted fonts after the document loads?**  
A: Store each `info.getDescription()` in a `List<String>` inside the callback. After loading, you’ll have a collection you can log, send to a monitoring service, or use to trigger a font‑download routine.

## Conclusion

You now know **how to capture font substitution warnings** in Java using Aspose.Words, why each piece of the puzzle matters, and how to extend the solution for real‑world scenarios. By leveraging `LoadOptions`, an `Aspose.Words warning callback`, and optional `FontSettings`, you gain full visibility into missing fonts and can keep your document conversion pipelines reliable.

Ready for the next step? Try swapping out the `System.out.println` with a logger like SLF4J, or integrate the warning list into a UI that alerts users before they finalize a batch conversion. You could also explore the **Aspose.Words warning callback** for other warning types, such as *unsupported features* or *high‑resolution image* alerts.  

Happy coding, and may your PDFs never suffer from unexpected font swaps again! 

![Screenshot showing console output of captured font substitution warnings](image-placeholder.png "capture font substitution warnings")


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [How to Create PDF Documents with Aspose.Words for Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}