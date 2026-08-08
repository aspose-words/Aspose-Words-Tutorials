---
category: general
date: 2026-08-07
description: How to edit footnote in Java with Aspose.Words – add custom dash, change
  footnote line, and set paragraph alignment for polished documents.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit footnote
- add custom dash
- change footnote line
- change footnote separator
- set paragraph alignment
language: en
lastmod: 2026-08-07
og_description: How to edit footnote in Java with Aspose.Words. Learn to add a custom
  dash, change the footnote line, and set paragraph alignment in just a few steps.
og_image_alt: Java code editing footnote separator with a custom dash and centered
  alignment
og_title: How to edit footnote in Java – add dash, change line, set alignment
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to edit footnote in Java with Aspose.Words – add custom dash, change
    footnote line, and set paragraph alignment for polished documents.
  headline: How to edit footnote in Java with Aspose.Words
  type: TechArticle
- description: How to edit footnote in Java with Aspose.Words – add custom dash, change
    footnote line, and set paragraph alignment for polished documents.
  name: How to edit footnote in Java with Aspose.Words
  steps:
  - name: '**Loading the document** – `new Document(...)` reads the DOCX file into
      memory, giving you access to all its nodes.'
    text: '**Loading the document** – `new Document(...)` reads the DOCX file into
      memory, giving you access to all its nodes.'
  - name: '**Fetching the separator** – `getFootnoteSeparator()` returns the special
      paragraph that Aspose.Words treats as the footnote line. This object is the
      only place you can safely modify the separator.'
    text: '**Fetching the separator** – `getFootnoteSeparator()` returns the special
      paragraph that Aspose.Words treats as the footnote line. This object is the
      only place you can safely modify the separator.'
  - name: '**Setting paragraph alignment** – `setAlignment(ParagraphAlignment.CENTER)`
      changes the line’s alignment. The keyword *set paragraph alignment* is applied
      directly to the separator, ensuring a centered dash.'
    text: '**Setting paragraph alignment** – `setAlignment(ParagraphAlignment.CENTER)`
      changes the line’s alignment. The keyword *set paragraph alignment* is applied
      directly to the separator, ensuring a centered dash.'
  - name: '**Adding a custom dash** – By clearing existing runs and adding a new `Run`
      with the em‑dash character (`—`), you achieve the *add custom dash* effect while
      also *change footnote line* to your desired style.'
    text: '**Adding a custom dash** – By clearing existing runs and adding a new `Run`
      with the em‑dash character (`—`), you achieve the *add custom dash* effect while
      also *change footnote line* to your desired style.'
  - name: '**Saving the document** – `doc.save(...)` writes the changes back to disk,
      producing an output file that reflects all modifications.'
    text: '**Saving the document** – `doc.save(...)` writes the changes back to disk,
      producing an output file that reflects all modifications.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Footnotes
title: How to edit footnote in Java with Aspose.Words
url: /java/document-styling/how-to-edit-footnote-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to edit footnote in Java with Aspose.Words

If you need to **how to edit footnote** in a Word document using Java, this guide shows the complete workflow. You will learn to add a custom dash, change the footnote line, and set paragraph alignment so the footnote separator looks professional.

Editing footnotes is a common requirement when preparing legal contracts, academic papers, or marketing brochures. The steps below cover everything you need—from loading the document to saving the final file—without requiring additional tools.

## Prerequisites

Before you start, make sure you have:

* Java 17 or newer installed.
* Aspose.Words for Java (latest version) added to your project’s classpath.
* A DOCX file (`input.docx`) that contains at least one footnote.

These items guarantee that the code runs without runtime errors.

## How to edit footnote separator and line

The footnote separator is the paragraph that appears between the main text and the list of footnotes. Changing its appearance improves readability and matches corporate branding.

```java
import com.aspose.words.*;

public class FootnoteSeparatorDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the document containing footnotes
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Get the footnote separator paragraph (the line before the footnote list)
        Paragraph separator = doc.getFootnoteSeparator();

        // Step 3: Center‑align the separator for better appearance
        separator.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

        // Step 4: Replace the default separator line with a custom dash
        separator.getRuns().clear();                 // Remove existing runs
        separator.getRuns().add(new Run(doc, "—"));   // Add a custom dash character

        // Step 5: Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Why each line matters

1. **Loading the document** – `new Document(...)` reads the DOCX file into memory, giving you access to all its nodes.
2. **Fetching the separator** – `getFootnoteSeparator()` returns the special paragraph that Aspose.Words treats as the footnote line. This object is the only place you can safely modify the separator.
3. **Setting paragraph alignment** – `setAlignment(ParagraphAlignment.CENTER)` changes the line’s alignment. The keyword *set paragraph alignment* is applied directly to the separator, ensuring a centered dash.
4. **Adding a custom dash** – By clearing existing runs and adding a new `Run` with the em‑dash character (`—`), you achieve the *add custom dash* effect while also *change footnote line* to your desired style.
5. **Saving the document** – `doc.save(...)` writes the changes back to disk, producing an output file that reflects all modifications.

## Add custom dash to the footnote separator

The code in **Step 4** demonstrates the *add custom dash* technique. You can replace the em‑dash with any string, such as `"***"` or `"---"`, to match your document’s visual language.

```java
separator.getRuns().clear();                     // Remove default line
separator.getRuns().add(new Run(doc, "***"));    // Insert three asterisks as a custom dash
```

Using a custom dash is especially helpful when the default thin line does not meet branding guidelines.

## Change footnote line style

If you prefer a solid line instead of a dash, you can insert a Unicode box‑drawing character or a repeated underscore.

```java
separator.getRuns().clear();
separator.getRuns().add(new Run(doc, "_____")); // Five underscores create a solid line
```

The *change footnote line* step works the same way regardless of the character you choose, because the separator paragraph merely renders the text it contains.

## Set paragraph alignment for footnote separator

The *set paragraph alignment* operation is not limited to center alignment. You can align left, right, or justify according to your layout needs.

```java
separator.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT); // Right‑align
```

Aligning the separator to the right can be useful for documents that use right‑aligned footnotes, such as bilingual publications.

## Full, runnable example

Below is the complete program that incorporates all the concepts—loading a document, editing the footnote separator, adding a custom dash, changing the line style, and setting alignment.

```java
import com.aspose.words.*;

public class FootnoteSeparatorDemo {
    public static void main(String[] args) throws Exception {
        // Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Retrieve the footnote separator paragraph
        Paragraph separator = doc.getFootnoteSeparator();

        // Set the desired alignment (center, left, right, or justify)
        separator.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

        // Clear any existing content in the separator
        separator.getRuns().clear();

        // Add a custom dash – replace with any string to change footnote line
        separator.getRuns().add(new Run(doc, "—")); // Em‑dash as the custom dash

        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**Expected output:** The `output.docx` file contains a centered em‑dash where the original thin line once was. All footnotes remain intact, and the document’s layout reflects the new separator style.

## Common pitfalls and how to avoid them

| Issue | Reason | Fix |
|-------|--------|-----|
| Separator not found | Document has no footnotes or uses a custom footnote style | Ensure the source DOCX contains at least one footnote before calling `getFootnoteSeparator()` |
| Custom dash not visible | Font does not support the chosen character | Use a Unicode character that is supported by the document’s default font, or embed a compatible font |
| Alignment appears unchanged | Paragraph format is overridden later in the code | Apply alignment **after** any other formatting calls that might reset it |

Addressing these points prevents runtime errors and guarantees that the *how to edit footnote* process works reliably.

## Next steps

Now that you know **how to edit footnote** elements, you can explore related tasks:

* **Add custom footnote reference style** – modify `FootnoteReference` nodes to change numbering or symbols.
* **Programmatically insert new footnotes** – use `DocumentBuilder.insertFootnote()` for dynamic content.
* **Apply conditional formatting** – change footnote appearance based on paragraph style or content length.

Each of these extensions builds on the same API surface you used to *add custom dash*, *change footnote line*, and *set paragraph alignment*.

---

*Happy coding! If the tutorial helped you master footnote editing, consider sharing it with your team or contributing a pull request to improve the example further.*


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Set Footnote And End Note Position](/words/hindi/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}