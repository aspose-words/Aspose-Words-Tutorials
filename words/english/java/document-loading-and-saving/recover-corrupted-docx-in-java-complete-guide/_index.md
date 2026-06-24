---
category: general
date: 2026-06-20
description: Recover corrupted docx files in Java with Aspose.Words. Learn how to
  set recovery mode and load document with recovery for seamless opening.
draft: false
keywords:
- recover corrupted docx
- set recovery mode
- load document with recovery
- open word with recovery
- open corrupted docx
language: en
og_description: Recover corrupted docx files in Java using Aspose.Words. This tutorial
  shows how to set recovery mode, load document with recovery, and open corrupted
  docx safely.
og_title: Recover corrupted docx in Java – Complete Guide
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Recover corrupted docx files in Java with Aspose.Words. Learn how to
    set recovery mode and load document with recovery for seamless opening.
  headline: Recover corrupted docx in Java – Complete Guide
  type: TechArticle
- description: Recover corrupted docx files in Java with Aspose.Words. Learn how to
    set recovery mode and load document with recovery for seamless opening.
  name: Recover corrupted docx in Java – Complete Guide
  steps:
  - name: '**Instantiate `LoadOptions`** – this object holds all the flags you want
      the loader to respect.'
    text: '**Instantiate `LoadOptions`** – this object holds all the flags you want
      the loader to respect.'
  - name: '**Call `setRecoveryMode`** – we chose `RECOVER` because we want the best
      chance of opening the file.'
    text: '**Call `setRecoveryMode`** – we chose `RECOVER` because we want the best
      chance of opening the file.'
  - name: '**Pass the options to the `Document` constructor** – Aspose.Words reads
      the file, applies the recovery logic, and returns a usable `Document` object.'
    text: '**Pass the options to the `Document` constructor** – Aspose.Words reads
      the file, applies the recovery logic, and returns a usable `Document` object.'
  - name: Open Word → *File* → *Open*.
    text: Open Word → *File* → *Open*.
  - name: Select the corrupted `.docx`.
    text: Select the corrupted `.docx`.
  - name: Click the dropdown arrow next to *Open* and choose **Open and Repair**.
    text: Click the dropdown arrow next to *Open* and choose **Open and Repair**.
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Recovery
- DOCX
title: Recover corrupted docx in Java – Complete Guide
url: /java/document-loading-and-saving/recover-corrupted-docx-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Recover corrupted docx in Java – Complete Guide

Ever tried to **recover corrupted docx** files and hit a wall? In this tutorial we’ll show you how to **recover corrupted docx** using Aspose.Words for Java by **set recovery mode** and **load document with recovery** so the file opens just like a healthy Word document.  

If you’ve ever wondered why some DOCX files refuse to open in Word, the answer is often hidden damage that the normal loader can’t handle. We’ll walk through the exact steps you need, from adding the library to verifying the page count, and you’ll end up with a clean, usable document—no more “file is corrupted” pop‑ups.

## What You’ll Learn

- How to **set recovery mode** to instruct Aspose.Words how aggressively it should repair a broken file.  
- The exact code required to **load document with recovery** and gracefully handle severe damage.  
- Tips for **open word with recovery** scenarios and what to do when the file can’t be salvaged.  
- A complete, runnable example you can copy‑paste into your IDE.  

### Prerequisites

- Java 8 or newer installed.  
- Maven or Gradle to manage dependencies (we’ll cover Maven).  
- A corrupted `.docx` file you want to test (any file that refuses to open in Microsoft Word will do).  

No deep knowledge of the Aspose API is required—just basic Java skills. Let’s get started.

![recover corrupted docx example](recover_corrupted_docx.png "recover corrupted docx screenshot")

## Step 1: Add Aspose.Words for Java to Your Project

First things first—your project needs the Aspose.Words JAR. If you’re using Maven, drop this into your `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version available -->
</dependency>
```

Gradle users can add:

```gradle
implementation 'com.aspose:aspose-words:24.10'
```

**Pro tip:** Always check the Aspose website for the most recent version; newer releases often include better recovery algorithms.

## Step 2: Set Recovery Mode – The Key to Fixing Damaged Files

Now that the library is in place, you need to tell it **how** to behave when it encounters corruption. That’s where `setRecoveryMode` comes into play. The `RecoveryMode` enum offers two options:

| Mode | Description |
|------|-------------|
| `RECOVER` | Attempts to fix as much as possible, returning a partially repaired document. |
| `REJECT` | Throws an exception on any serious issue, useful when you need a clean slate. |

Here’s the code that **set recovery mode** to the forgiving `RECOVER` option:

```java
import com.aspose.words.*;

public class RecoverCorruptedDocx {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create LoadOptions and set the desired recovery mode
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER); // Use RECOVER to attempt fixing,
                                                          // REJECT to fail on severe damage

        // Step 2.2: Load the possibly corrupted document using the configured options
        Document doc = new Document("C:/files/corrupted.docx", loadOptions);

        // Step 2.3: Work with the loaded document (e.g., display page count)
        System.out.println("Loaded with " + doc.getPageCount() + " pages");
    }
}
```

**Why this matters:** Without setting the recovery mode, Aspose.Words defaults to `REJECT`, which means your program would throw an exception the moment it spots a broken part. By explicitly **set recovery mode**, you give the library permission to patch missing XML nodes, restore missing relationships, and generally “clean up” the file.

## Step 3: Load Document with Recovery – Putting It All Together

The snippet above already demonstrates **load document with recovery**, but let’s break it down for clarity:

1. **Instantiate `LoadOptions`** – this object holds all the flags you want the loader to respect.  
2. **Call `setRecoveryMode`** – we chose `RECOVER` because we want the best chance of opening the file.  
3. **Pass the options to the `Document` constructor** – Aspose.Words reads the file, applies the recovery logic, and returns a usable `Document` object.

If you prefer a more defensive approach, you can wrap the loading in a try‑catch block and fall back to `REJECT` if `RECOVER` produces an unsatisfactory result:

```java
try {
    Document doc = new Document("C:/files/corrupted.docx", loadOptions);
    System.out.println("Recovered document has " + doc.getPageCount() + " pages.");
} catch (Exception e) {
    System.err.println("Recovery failed: " + e.getMessage());
    // Optional: retry with REJECT mode to see if the file is beyond repair
}
```

## Step 4: Verify the Repaired Document

Once the document is loaded, you’ll want to make sure the content looks sane. Common checks include:

- **Page count** – a quick sanity check (`doc.getPageCount()`).  
- **Text extraction** – `doc.getText()` to see if the main body is intact.  
- **Saving a copy** – write the recovered version to disk for later inspection.

```java
// Save the recovered file for manual verification
doc.save("C:/files/recovered.docx");

// Print first 200 characters of text to the console
String preview = doc.getText().substring(0, Math.min(200, doc.getText().length()));
System.out.println("Preview of recovered text:\n" + preview);
```

If the preview looks garbled, the file may have suffered irreversible damage. In that case, consider using the `REJECT` mode to avoid propagating corrupted data.

## Step 5: Optional – Open Word with Recovery (Manual Approach)

Sometimes you don’t want to write code; you just need to **open word with recovery** manually. Microsoft Word itself offers a “Open and Repair” feature:

1. Open Word → *File* → *Open*.  
2. Select the corrupted `.docx`.  
3. Click the dropdown arrow next to *Open* and choose **Open and Repair**.

While this works for many users, it lacks the automation and batch‑processing capabilities of the Java approach we just covered. Use the manual method for occasional fixes; rely on Aspose.Words when you need to process dozens or hundreds of files programmatically.

## Edge Cases & Common Pitfalls

- **Severe corruption** – If the file is missing its core `[Content_Types].xml`, even `RECOVER` can’t help. Expect an exception and fallback to notifying the user.  
- **Password‑protected files** – Recovery mode does not bypass encryption. You must supply the password via `LoadOptions.setPassword("yourPwd")` before attempting recovery.  
- **Large documents** – Loading a massive DOCX with `RECOVER` may consume more memory. Consider increasing the JVM heap (`-Xmx2g`) if you run into `OutOfMemoryError`.  

## Full Working Example

Below is the complete program you can compile and run directly. Replace the file path with the location of your corrupted DOCX.

```java
import com.aspose.words.*;

public class RecoverCorruptedDocx {
    public static void main(String[] args) {
        try {
            // Create LoadOptions and set recovery mode
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setRecoveryMode(RecoveryMode.RECOVER); // Attempt to fix

            // Load the corrupted document
            Document doc = new Document("C:/files/corrupted.docx", loadOptions);

            // Verify and display basic info
            System.out.println("Recovered document loaded successfully.");
            System.out.println("Page count: " + doc.getPageCount());

            // Save a clean copy
            doc.save("C:/files/recovered.docx");
            System.out.println("Recovered file saved as recovered.docx");

            // Show a short text preview
            String text = doc.getText();
            System.out.println("Text preview (first 200 chars):");
            System.out.println(text.substring(0, Math.min(200, text.length())));
        } catch (Exception ex) {
            System.err.println("Failed to recover the document: " + ex.getMessage());
        }
    }
}
```

**Expected output (when recovery succeeds):**

```
Recovered document loaded successfully.
Page count: 12
Recovered file saved as recovered.docx
Text preview (first 200 chars):
Lorem ipsum dolor sit amet, consectetur adipiscing elit...
```

If the document is beyond repair, you’ll see a clear error message instead of a stack trace, thanks to the surrounding `try‑catch`.

## Conclusion

You now know how to **recover corrupted docx** files in Java using Aspose.Words. By **set recovery mode** to `RECOVER` and then **load document with recovery**, you can automatically repair many common issues that would otherwise prevent a Word file from opening. Whether you need to **open word with recovery** programmatically or just want to **open corrupted docx** manually, the techniques covered here give you a solid foundation.

**Next steps:**  

- Experiment


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Recover corrupted docx – Complete Guide to Fix and Process Documents](/words/english/java/document-loading-and-saving/recover-corrupted-docx-complete-guide-to-fix-and-process-doc/)
- [How to Load HTML and Save as DOCX using Aspose.Words for Java](/words/english/java/document-loading-and-saving/loading-and-saving-html-documents/)
- [How to Merge Multiple DOCX Files Using Aspose.Words for Java](/words/english/java/document-merging/using-document-merging/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}