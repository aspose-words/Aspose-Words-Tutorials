---
category: general
date: 2026-02-15
description: Learn how to get missing fonts when loading a Word document in Java using
  Aspose.Words. Includes warning callbacks and font‑substitution handling.
draft: false
keywords:
- how to get missing fonts
- Aspose.Words missing font
- font substitution warning
- Java LoadOptions warning callback
- document processing Java
language: en
og_description: How to get missing fonts in Java with Aspose.Words. Discover warning
  callbacks, font substitution handling, and best practices for document processing.
og_title: How to Get Missing Fonts in Java – Aspose.Words Guide
tags:
- Aspose.Words
- Java
- Font Management
title: How to Get Missing Fonts in Java – Aspose.Words Guide
url: /java/document-loading-and-saving/how-to-get-missing-fonts-in-java-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to Get Missing Fonts in Java – Aspose.Words Guide

Ever opened a Word document in Java only to see odd font replacements and wonder **how to get missing fonts**? You're not the first to face that surprise. In many enterprise apps, missing font warnings can break the visual fidelity of reports, contracts, or marketing collateral.

The good news? Aspose.Words gives you a clean way to capture those warnings through a callback, so you can log, replace, or even alert users before the document is rendered. In this tutorial we’ll walk through a complete, runnable example that shows **how to get missing fonts**, explains why the callback matters, and covers a few edge‑case tricks you might need in real‑world projects.

> **Pro tip:** If you’re already using Aspose.Words 22.12 or newer, the API shown below works out‑of‑the‑box without extra configuration.

---

![Diagram illustrating how to get missing fonts using Aspose.Words warning callback](how-to-get-missing-fonts-diagram.png "how to get missing fonts diagram")

## What This Tutorial Covers

- Setting up a **Java LoadOptions warning callback** to capture font‑substitution warnings.  
- Filtering the warnings so you only see the ones related to missing fonts.  
- Printing a clear, human‑readable report of which fonts were substituted and what they were replaced with.  
- Tips for handling large documents, customizing the warning level, and integrating the solution into a larger processing pipeline.

By the end of this guide you’ll be able to answer the question “**how to get missing fonts**?” with a ready‑to‑run code snippet and a solid understanding of the underlying mechanics.

### Prerequisites

- Java 8 or newer installed.  
- Aspose.Words for Java library (download from the official site or add via Maven/Gradle).  
- A Word document that references a font not installed on your machine (e.g., `MissingFont.docx`).  

If you’re missing any of those, grab the library now—adding it to Maven is as simple as:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version> <!-- replace with the latest version -->
</dependency>
```

---

## Step 1: Prepare a Collection for Font‑Substitution Warnings

Before loading the document we need a place to store any warnings that Aspose.Words emits. An `ArrayList<WarningInfo>` works nicely because it preserves order and lets us iterate later.

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

// Step 1: Create a list that will hold warning information.
List<WarningInfo> fontWarnings = new ArrayList<>();
```

*Why this matters:* The warning callback can fire dozens of times for a single file—think of each missing glyph, each embedded image issue, etc. By collecting them first, you keep the loading phase fast and defer processing to a controlled loop.

---

## Step 2: Configure LoadOptions with a Warning Callback

Aspose.Words lets you plug in an `IWarningCallback`. Inside the callback we’ll add every `WarningInfo` to our list from Step 1.

```java
// Step 2: Set up LoadOptions with a custom warning callback.
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Capture every warning; we'll filter later.
        fontWarnings.add(info);
    }
});
```

*Explanation:* The `warning` method is invoked **synchronously** during document loading. By simply pushing the `WarningInfo` into `fontWarnings`, we avoid any heavy I/O (like logging to a file) that could slow down the load. This pattern—collect‑then‑process—is the recommended way to handle large batches of warnings.

---

## Step 3: Load the Document Using the Configured Options

Now we actually read the Word file. If the document contains fonts that aren’t installed, Aspose.Words will automatically substitute them and fire the warning callback we just wired up.

```java
// Step 3: Load the document with the warning‑aware LoadOptions.
String filePath = "YOUR_DIRECTORY/MissingFont.docx"; // adjust to your environment
Document doc = new Document(filePath, loadOptions);
```

*What happens under the hood?* Aspose.Words parses the file’s font table, compares it against the fonts available on the host OS, and for each missing entry it creates a `WarningInfo` with `WarningSource.FontSubstitution`. That source is the key we’ll use to isolate the missing‑font warnings.

---

## Step 4: Filter and Display Only Font‑Substitution Warnings

After loading, `fontWarnings` may contain a mix of messages (e.g., deprecated features, image issues). We only care about missing fonts, so we loop through the list and print a concise report.

```java
// Step 4: Output any font‑substitution warnings that were captured.
for (WarningInfo warning : fontWarnings) {
    if (warning.getSource() == WarningSource.FontSubstitution) {
        System.out.println("Substituted '" + warning.getDescription() + "' with '" +
                           warning.getAdditionalInfo() + "'");
    }
}
```

**Sample output**

```
Substituted 'Comic Sans MS' with 'Arial'
Substituted 'Times New Roman PS' with 'Times New Roman'
```

*Why this is useful:* The `description` field tells you which font the document asked for, while `additionalInfo` tells you what Aspose.Words actually used. Armed with that data you can:

- Prompt the user to install the missing font.  
- Programmatically embed a substitute font into the document (`doc.getFontInfos().add(...)`).  
- Log the event for compliance audits.

---

## Handling Edge Cases and Common Variations

### 1. Suppressing Non‑Font Warnings

If you only want font‑related messages, you can tighten the callback:

```java
loadOptions.setWarningCallback(info -> {
    if (info.getSource() == WarningSource.FontSubstitution) {
        fontWarnings.add(info);
    }
});
```

This reduces memory churn when processing huge batches.

### 2. Adjusting Warning Severity

Aspose.Words categorises warnings by `WarningType`. For missing fonts you’ll typically see `WarningType.FontSubstitution`. If you need to treat them as errors (e.g., abort loading), throw an exception inside the callback:

```java
loadOptions.setWarningCallback(info -> {
    if (info.getSource() == WarningSource.FontSubstitution) {
        throw new RuntimeException("Missing font detected: " + info.getDescription());
    }
});
```

### 3. Working with Streams Instead of Files

Sometimes documents come from a database or an HTTP request. The same approach works with an `InputStream`:

```java
InputStream docStream = new ByteArrayInputStream(bytesFromDb);
Document doc = new Document(docStream, loadOptions);
```

Just remember to close the stream after loading.

### 4. Using a Custom Font Folder

If you have a collection of corporate fonts stored on a shared drive, point Aspose.Words to that folder:

```java
loadOptions.setFontSettings(new FontSettings());
loadOptions.getFontSettings().setFontsFolder("C:/CorporateFonts", true);
```

Now the library will look there *before* falling back to system fonts, dramatically reducing the number of missing‑font warnings.

---

## Full Working Example

Putting everything together, here’s a self‑contained class you can drop into any Java project:

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

public class MissingFontDetector {

    public static void main(String[] args) {
        // 1️⃣ Prepare a collection for warnings.
        List<WarningInfo> fontWarnings = new ArrayList<>();

        // 2️⃣ Create LoadOptions with a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(info -> fontWarnings.add(info));

        // (Optional) Point to a custom font folder.
        // FontSettings fontSettings = new FontSettings();
        // fontSettings.setFontsFolder("C:/CorporateFonts", true);
        // loadOptions.setFontSettings(fontSettings);

        // 3️⃣ Load the document.
        String docPath = "YOUR_DIRECTORY/MissingFont.docx";
        Document doc;
        try {
            doc = new Document(docPath, loadOptions);
        } catch (Exception e) {
            System.err.println("Failed to load document: " + e.getMessage());
            return;
        }

        // 4️⃣ Print missing‑font warnings.
        System.out.println("=== Missing Font Report ===");
        for (WarningInfo warning : fontWarnings) {
            if (warning.getSource() == WarningSource.FontSubstitution) {
                System.out.println("Substituted '" + warning.getDescription() + "' with '" +
                                   warning.getAdditionalInfo() + "'");
            }
        }
        System.out.println("=== End of Report ===");
    }
}
```

Run this program, and you’ll see a tidy list of every font that Aspose.Words had to replace. No extra libraries, no hidden magic—just pure Java and the power of the **Aspose.Words missing font** API.

---

## Conclusion

We’ve answered the core question **how to get missing fonts** in a Java environment using Aspose.Words. By attaching a `LoadOptions` warning callback, collecting `WarningInfo` objects, and filtering for `FontSubstitution` sources, you gain complete visibility into font‑related issues before any rendering occurs. The approach scales from single‑file utilities to massive batch processors, and it’s flexible enough to accommodate custom font folders, severity handling, or stream‑based inputs.

Next steps? Try embedding the substituted fonts directly into the document (`doc.getFontInfos().add(...)`) so the final file is truly self‑contained, or integrate the warning report into a monitoring dashboard. You might also explore related topics such as **document processing Java**, **Aspose.Words font substitution warning**, and **Java LoadOptions warning callback** to deepen your expertise.

Happy coding, and may your documents always render with the fonts you expect!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}