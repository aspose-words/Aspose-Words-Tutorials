---
category: general
date: 2026-04-28
description: Iterate document warnings in a Word file to detect missing fonts, retrieve
  missing font names and print missing font details using Aspose.Words for Java.
draft: false
keywords:
- iterate document warnings
- detect missing fonts
- load word document
- retrieve missing font
- print missing font
language: en
og_description: Iterate document warnings to find missing fonts, retrieve missing
  font names, and print missing font details with a complete Java example.
og_title: 'Iterate document warnings: Detect Missing Fonts in Java'
tags:
- Aspose.Words
- Java
- Document Processing
title: 'Iterate document warnings: Detect Missing Fonts in Java'
url: /java/document-operations/iterate-document-warnings-detect-missing-fonts-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Iterate document warnings – Detect Missing Fonts in Java

Ever needed to **iterate document warnings** when opening a Word file and wondered which fonts are missing? You're not the only one. Missing fonts can break the look of a report, and without a way to spot them you might ship a document that looks nothing like the original.  

In this tutorial we’ll show you how to **detect missing fonts** by loading a Word document, iterating its warnings, retrieving the missing font names, and finally printing the missing font information—all with Aspose.Words for Java.  

We'll cover everything from the very first line of code to the expected console output, so you can copy‑paste a working solution into your project right now. No extra docs required.

## Prerequisites

- Java 8 or newer installed.
- Aspose.Words for Java library (the latest version as of 2026‑04‑28).
- A Word file that potentially contains fonts not installed on your machine (e.g., `doc-with-missing-font.docx`).

If you already have those, great—you’re ready to **load word document** and start iterating.

## Step 1 – Load Word Document with Default Options

Before we can **iterate document warnings**, the file must be loaded into memory. Aspose.Words lets you do this with a single constructor call. Using the default `LoadOptions` is usually enough, but we’ll show the explicit creation for clarity.

```java
import com.aspose.words.*;

public class MissingFontDetector {
    public static void main(String[] args) throws Exception {

        // Step 1: Prepare load options (default settings are fine for this example)
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/doc-with-missing-font.docx", loadOptions);
```

> **Why this matters:**  
> Loading the document triggers Aspose.Words to scan the file for any resources it can’t resolve, such as fonts that aren’t installed locally. Those issues are stored as **warnings**, which we’ll **iterate document warnings** over in the next step.

## Step 2 – Iterate Document Warnings to Find Font Issues

Now comes the heart of the solution: we loop through every warning that the library collected while loading. The `WarningInfo` objects tell us what went wrong, and we can filter for `FontSubstitutionWarning` to **detect missing fonts**.

```java
        // Step 3: Iterate over all warnings generated during loading
        for (WarningInfo warningInfo : document.getWarnings()) {
            // Step 4: Identify font substitution warnings
            if (warningInfo instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fontWarning = (FontSubstitutionWarning) warningInfo;

                // Step 5: Output the missing font name and the font that was used as a substitute
                System.out.println("Missing font: " + fontWarning.getMissingFontName());
                System.out.println("Substituted with: " + fontWarning.getSubstitutedFontName());
            }
        }
    }
}
```

> **Pro tip:** The `instanceof` check ensures we only handle font‑related warnings, ignoring others like image‑loading problems. This makes the loop efficient and keeps the output focused on the fonts you actually need to **retrieve missing font** information for.

### Expected Console Output

```
Missing font: Arial Black
Substituted with: Liberation Sans
Missing font: Calibri
Substituted with: Liberation Sans
```

If the document contains no missing fonts, the loop simply finishes silently—nothing to **print missing font**.

## Step 3 – Why Not Just Catch an Exception?

You might wonder, “Why not wrap the `new Document(...)` call in a try‑catch and look for an exception?” The answer is two‑fold:

1. **Granular Information:** Exceptions only tell you that something failed. Warnings give you the exact font name and the fallback that Aspose.Words chose.
2. **Non‑Fatal Issues:** Missing fonts are usually non‑fatal; the document still loads, but the visual fidelity is compromised. By **iterating document warnings**, you preserve the ability to process the rest of the file.

## Step 4 – Extending the Example: Collecting Missing Fonts into a List

Sometimes you need the missing fonts for further processing—maybe to embed them or to alert a user via UI. Here’s a quick tweak that gathers the names into a `Set<String>`.

```java
        // Collect missing fonts for later use
        Set<String> missingFonts = new HashSet<>();

        for (WarningInfo warningInfo : document.getWarnings()) {
            if (warningInfo instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fontWarning = (FontSubstitutionWarning) warningInfo;
                missingFonts.add(fontWarning.getMissingFontName());

                // Still print for immediate feedback
                System.out.println("Missing font: " + fontWarning.getMissingFontName());
                System.out.println("Substituted with: " + fontWarning.getSubstitutedFontName());
            }
        }

        // Example of using the collected data
        System.out.println("Total missing fonts: " + missingFonts.size());
```

Now you have a clean way to **retrieve missing font** data programmatically, which you can feed into a reporting module or a font‑installation wizard.

## Step 5 – Real‑World Considerations

- **Multiple Substitutions:** A single missing font can be substituted by different fonts in different parts of the document. The warning list will contain each occurrence, so you may see duplicate missing‑font entries.
- **Performance:** Loading very large documents may generate thousands of warnings. If you only care about fonts, filter early as shown to keep the loop fast.
- **Cross‑Platform Fonts:** On Linux, the default substitution font is often *Liberation Sans*. On Windows, it could be *Arial*. Knowing the fallback helps you decide whether you need to ship custom fonts with your application.

## Step 6 – Visual Aid

Below is a screenshot of the console output (alt text includes the primary keyword for SEO).

![Iterate document warnings console output showing missing fonts and their substitutes](/images/iterate-document-warnings.png)

*Alt text:* *iterate document warnings example displaying missing font names and substitution details.*

## Conclusion

You’ve just learned how to **iterate document warnings** in Aspose.Words for Java, **detect missing fonts**, **load word document** safely, **retrieve missing font** information, and **print missing font** details to the console. The complete code snippet runs as‑is, and you can adapt it to log to a file, show a UI dialog, or even embed the missing fonts automatically.

Next, you might want to explore how to **load word document** with custom font sources (e.g., adding a folder of corporate fonts) or how to embed missing fonts directly into the file to preserve layout across machines. Both topics build naturally on what we covered here.

Happy coding, and may your PDFs always look exactly as you intended!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}