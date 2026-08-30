---
category: general
date: 2026-06-20
description: how to set callback in Aspose.Words Java to detect missing fonts and
  customize document loading. Learn step‑by‑step handling of font substitution warnings.
draft: false
keywords:
- how to set callback
- detect missing fonts
- handle missing fonts
- customize document loading
language: en
og_description: how to set callback in Aspose.Words Java to detect missing fonts,
  handle substitutions, and customize document loading. Complete guide with code.
og_title: how to set callback – Detect Missing Fonts in Aspose.Words Java
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: how to set callback in Aspose.Words Java to detect missing fonts and
    customize document loading. Learn step‑by‑step handling of font substitution warnings.
  headline: how to set callback in Aspose.Words Java – Detect and Handle Missing Fonts
  type: TechArticle
- description: how to set callback in Aspose.Words Java to detect missing fonts and
    customize document loading. Learn step‑by‑step handling of font substitution warnings.
  name: how to set callback in Aspose.Words Java – Detect and Handle Missing Fonts
  steps:
  - name: What if I want the program to stop loading when a font is missing?
    text: 'Throw an exception inside the `warning` method:'
  - name: Does this work for PDFs generated from DOCX?
    text: Absolutely. The callback fires during the **loading** phase, which is identical
      for all output formats (`save` to PDF, DOCX, HTML, etc.). As long as you load
      the source document with the same `LoadOptions`, you’ll catch missing fonts
      before they affect the final PDF.
  - name: Can I capture other warning types (e.g., image conversion)?
    text: Yes—`WarningInfo.getWarningType()` can be compared against other enums like
      `WarningType.IMAGE_CONVERSION`. Just add more `if` branches in the callback.
  - name: Is there a performance impact?
    text: Negligible. The callback runs synchronously during loading, and the extra
      checks are lightweight. If you’re loading thousands of documents, you might
      want to disable warnings in production by setting `loadOptions.setWarningCallback(null);`.
  - name: What’s Next?
    text: '- Explore **font substitution tables** for bulk mapping of many missing
      fonts. - Combine this callback with **document validation** to enforce style
      guides. - Try **custom warning callbacks** that write to a log file or a monitoring
      system instead of `System.out`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Processing
title: how to set callback in Aspose.Words Java – Detect and Handle Missing Fonts
url: /java/document-loading-and-saving/how-to-set-callback-in-aspose-words-java-detect-and-handle-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# how to set callback in Aspose.Words Java – Detect and Handle Missing Fonts

Ever wondered **how to set callback** in Aspose.Words Java so you can spot missing fonts before they ruin your PDF or DOCX? You're not the only one. Missing font warnings can silently corrupt layout, and without a proper warning callback you might never notice until the final document looks off.  

In this tutorial we’ll walk through a complete, ready‑to‑run example that **detects missing fonts**, **handles missing fonts** gracefully, and shows you how to **customize document loading** with a warning callback. By the end you’ll have a self‑contained Java class you can drop into any project—no extra documentation hunting required.

## What You’ll Need

- Java 8 or newer (the code works with Java 11+ as well)  
- Aspose.Words for Java library (version 23.9 or later)  
- A DOCX file that references a font you don’t have installed (e.g., a custom corporate font)  

If you haven’t added Aspose.Words to your Maven project yet, just include:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

That’s it—no extra plugins, no native dependencies.

---

## Step 1: Understand the WarningCallback Mechanism

The **warning callback** is Aspose.Words’ way of shouting at you when something unexpected happens while loading or saving a document. By implementing `IWarningCallback` you gain full control over what gets logged, ignored, or even turned into an exception.

> **Why this matters:**  
> When a font is missing, Aspose substitutes a fallback font. The visual result can be dramatically different, especially for branding‑heavy PDFs. By catching `WarningType.FONT_SUBSTITUTION`, you can log the exact font name, decide whether to abort, or substitute your own custom font programmatically.

---

## Step 2: Create a LoadOptions Instance

`LoadOptions` is the entry point for customizing document loading. You’ll attach the callback to this object before you actually load the file.

```java
// Step 2: Prepare LoadOptions
LoadOptions loadOptions = new LoadOptions();
```

At this point `loadOptions` is just a plain container—nothing happens yet. The real magic begins when we plug in the callback.

---

## Step 3: Implement and Attach the Callback

Below is a compact anonymous class that implements `IWarningCallback`. It prints a friendly line to the console whenever a font substitution occurs.

```java
// Step 3: Attach a warning callback to capture font substitution warnings
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Detect missing fonts
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("[Missing Font] " + info.getDescription());
            // Optional: you could throw an exception here to abort loading
            // throw new RuntimeException("Font missing: " + info.getDescription());
        }
    }
});
```

> **Pro tip:** If you want to **handle missing fonts** by providing a replacement, you can also set `FontSettings` on the `LoadOptions` and map missing fonts to a known fallback.

---

## Step 4: Load the Document with Your Custom Options

Now that the callback is wired up, load the document. If the file references a font you don’t have, you’ll see the warning printed.

```java
// Step 4: Load the document using the configured LoadOptions
String docPath = "YOUR_DIRECTORY/doc-with-missing-font.docx";
Document document = new Document(docPath, loadOptions);
```

When you run the program, the console might show:

```
[Missing Font] Font substitution: The font "MyCustomFont" was not found. Substituted with "Arial".
```

That line proves you’ve successfully **detected missing fonts** and are now in a position to **handle missing fonts** however you see fit.

---

## Step 5: Optional – Replace Missing Fonts with a Known Font

If you prefer to automatically replace any missing font with, say, `Times New Roman`, you can add a `FontSettings` object:

```java
// Optional Step 5: Map missing fonts to a fallback
FontSettings fontSettings = new FontSettings();
fontSettings.setMissingFontNotification(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // This will be called for each missing font
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("[Auto‑Replace] " + info.getDescription());
        }
    }
});
// Force substitution to Times New Roman
fontSettings.getSubstitutionSettings().getTableSubstitution().addSubstitutes("MyCustomFont", new String[]{"Times New Roman"});
loadOptions.setFontSettings(fontSettings);
```

Now the document loads, and any reference to `MyCustomFont` is silently swapped for `Times New Roman`. The console will still tell you what was replaced, keeping you in the loop.

---

## Full Working Example

Below is a single Java class that incorporates all the steps above. Copy‑paste it into your IDE, adjust `docPath`, and run.

```java
import com.aspose.words.*;

public class DetectMissingFontsDemo {
    public static void main(String[] args) {
        try {
            // 1️⃣ Create LoadOptions
            LoadOptions loadOptions = new LoadOptions();

            // 2️⃣ Attach warning callback (detect missing fonts)
            loadOptions.setWarningCallback(new IWarningCallback() {
                @Override
                public void warning(WarningInfo info) {
                    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                        System.out.println("[Missing Font] " + info.getDescription());
                    }
                }
            });

            // 3️⃣ (Optional) Set up automatic font substitution
            FontSettings fontSettings = new FontSettings();
            fontSettings.getSubstitutionSettings()
                        .getTableSubstitution()
                        .addSubstitutes("MyCustomFont", new String[]{"Times New Roman"});
            loadOptions.setFontSettings(fontSettings);

            // 4️⃣ Load the document with custom loading behavior
            String docPath = "YOUR_DIRECTORY/doc-with-missing-font.docx";
            Document doc = new Document(docPath, loadOptions);

            // 5️⃣ Save to PDF to see the final result (optional)
            doc.save("output.pdf");
            System.out.println("Document loaded and saved successfully.");

        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Expected output**

```
[Missing Font] Font substitution: The font "MyCustomFont" was not found. Substituted with "Times New Roman".
Document loaded and saved successfully.
```

You now have a reproducible way to **detect missing fonts**, **handle missing fonts**, and **customize document loading**—all by learning **how to set callback** correctly.

---

## Frequently Asked Questions

### What if I want the program to stop loading when a font is missing?

Throw an exception inside the `warning` method:

```java
throw new RuntimeException("Critical: Missing font - " + info.getDescription());
```

The catch block at the bottom will capture it, and you can decide how to log or alert the user.

### Does this work for PDFs generated from DOCX?

Absolutely. The callback fires during the **loading** phase, which is identical for all output formats (`save` to PDF, DOCX, HTML, etc.). As long as you load the source document with the same `LoadOptions`, you’ll catch missing fonts before they affect the final PDF.

### Can I capture other warning types (e.g., image conversion)?

Yes—`WarningInfo.getWarningType()` can be compared against other enums like `WarningType.IMAGE_CONVERSION`. Just add more `if` branches in the callback.

### Is there a performance impact?

Negligible. The callback runs synchronously during loading, and the extra checks are lightweight. If you’re loading thousands of documents, you might want to disable warnings in production by setting `loadOptions.setWarningCallback(null);`.

---

## Visual Overview

![how to set callback example in Aspose.Words Java](https://example.com/images/callback-diagram.png "how to set callback")

*The diagram illustrates the flow: `LoadOptions` → `IWarningCallback` → Document loading → Font substitution handling.*

---

## Wrap‑Up

We’ve covered **how to set callback** in Aspose.Words Java, demonstrated **detect missing fonts**, shown practical ways to **handle missing fonts**, and explained how to **customize document loading** with `LoadOptions`.  

Armed with this knowledge, you can now safeguard your document pipelines against silent font swaps, keep branding intact, and give your users clear feedback when something goes awry.

### What’s Next?

- Explore **font substitution tables** for bulk mapping of many missing fonts.  
- Combine this callback with **document validation** to enforce style guides.  
- Try **custom warning callbacks** that write to a log file or a monitoring system instead of `System.out`.  

Feel free to experiment, and let us know how you customized the callback for your own projects. Happy coding!

---


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [How to Capture Fonts in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}