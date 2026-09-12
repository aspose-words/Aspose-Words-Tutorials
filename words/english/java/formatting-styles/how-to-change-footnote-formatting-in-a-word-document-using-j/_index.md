---
category: general
date: 2026-09-11
description: Learn how to change footnote formatting in Java with Aspose.Words. This
  guide explains how to edit footnote, update footnote style, and modify footnote
  separator.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote formatting
- how to edit footnote
- update footnote style
- modify footnote separator
language: en
lastmod: 2026-09-11
og_description: Change footnote formatting in Java with Aspose.Words. Follow this
  complete guide to edit footnote, update footnote style, and modify footnote separator.
og_image_alt: Screenshot showing change footnote formatting in a Java editor
og_title: Change footnote formatting in Java – step‑by‑step guide
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to change footnote formatting in Java with Aspose.Words.
    This guide explains how to edit footnote, update footnote style, and modify footnote
    separator.
  headline: How to change footnote formatting in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Footnote
- Document processing
title: How to change footnote formatting in a Word document using Java
url: /java/formatting-styles/how-to-change-footnote-formatting-in-a-word-document-using-j/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to change footnote formatting in a Word document using Java

If you need to **change footnote formatting** in a Word document, this tutorial walks you through the exact steps using Aspose.Words for Java. Whether you are building a publishing pipeline or just need to **how to edit footnote** appearance programmatically, the solution below covers everything from loading the file to saving the updated version.

You will learn how to **update footnote style**, make the footnote separator bold, and even **modify footnote separator** properties such as font size or color. The guide assumes you have basic Java knowledge and a working Aspose.Words for Java license.

## Prerequisites

Before you start, make sure you have:

* Java 17 or newer installed.
* Aspose.Words for Java (version 23.12 or later) added to your project’s classpath.
* A Word document (`input.docx`) that contains at least one footnote.
* An IDE or build tool (Maven/Gradle) to compile and run the code.

If you are unsure how to add Aspose.Words to a Maven project, include the following dependency in your `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

## Change footnote formatting with Aspose.Words for Java

The core of the solution is a short Java program that loads a document, accesses the footnote separator paragraph, changes its formatting, and saves the result. The code is fully self‑contained, so you can copy it into a new class and run it immediately.

```java
import com.aspose.words.*;

public class ChangeFootnoteFormatting {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Retrieve the footnote separator paragraph
        Paragraph footnoteSeparator = doc.getFootnoteSeparator();

        // Defensive check – the separator may be empty in some documents
        if (footnoteSeparator.getRuns().getCount() == 0) {
            // Create a new run so we have something to format
            Run run = new Run(doc);
            run.setText("\u2022"); // bullet character as placeholder
            footnoteSeparator.appendChild(run);
        }

        // Step 3: Change the first run's formatting – this is where we
        //          modify footnote separator appearance
        Run firstRun = footnoteSeparator.getRuns().get(0);
        Font font = firstRun.getFont();
        font.setBold(true);                // make the separator bold
        font.setItalic(true);              // optional: also italic
        font.setSize(10.0);                // set font size to 10 pt
        font.setColor(java.awt.Color.GRAY); // change color to a subtle gray

        // Step 4: Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Why each step matters

* **Loading the document** (`new Document`) creates an in‑memory representation that Aspose.Words can manipulate.  
* **Retrieving the footnote separator** (`getFootnoteSeparator`) gives you direct access to the paragraph that separates footnotes from the main text. This is the element you need to target when you want to **change footnote formatting**.  
* **Formatting the run** (`setBold`, `setItalic`, `setSize`, `setColor`) demonstrates how to **modify footnote separator** properties. You can add any additional font attributes here, such as underline or highlight, to fully control the appearance.  
* **Saving the document** writes the changes back to disk, producing a new file (`output.docx`) that reflects the updated footnote style.

> **Pro tip:** If your source document uses a custom footnote separator that contains multiple runs (e.g., a combination of symbols), loop through `footnoteSeparator.getRuns()` and apply the same `Font` settings to each run for consistent styling.

## How to edit footnote separator programmatically

Sometimes you may need to edit not only the separator but also the footnote text itself. The same API can be used to access each footnote, adjust its paragraph formatting, or change the numbering style.

```java
for (Footnote footnote : (Iterable<Footnote>) doc.getFootnotes()) {
    // Example: make all footnote text italic and 9 pt
    for (Paragraph para : (Iterable<Paragraph>) footnote.getParagraphs()) {
        para.getParagraphFormat().setStyleIdentifier(StyleIdentifier.FOOTNOTE_TEXT);
        para.getRuns().forEach(run -> {
            Font f = run.getFont();
            f.setItalic(true);
            f.setSize(9.0);
        });
    }
}
```

The snippet above shows **how to edit footnote** bodies after you have already **changed footnote formatting** for the separator. By iterating over `doc.getFootnotes()`, you ensure every footnote inherits the same style, which is essential for a professional‑looking document.

## Update footnote style for consistent document appearance

If you prefer to work with styles rather than individual runs, Aspose.Words lets you create or modify a `Style` object and then apply it to footnotes and the separator. This approach is useful when you need to **update footnote style** across many documents.

```java
// Create or retrieve a style named "MyFootnoteStyle"
Style footnoteStyle = doc.getStyles().add(StyleType.PARAGRAPH, "MyFootnoteStyle");
footnoteStyle.getFont().setBold(true);
footnoteStyle.getFont().setSize(10);
footnoteStyle.getFont().setColor(java.awt.Color.DARK_GRAY);

// Apply the style to the separator
footnoteSeparator.getParagraphFormat().setStyle(footnoteStyle);

// Apply the same style to every footnote paragraph
for (Footnote fn : (Iterable<Footnote>) doc.getFootnotes()) {
    for (Paragraph p : (Iterable<Paragraph>) fn.getParagraphs()) {
        p.getParagraphFormat().setStyle(footnoteStyle);
    }
}
```

Using a dedicated style makes future maintenance easier—change the style once, and every footnote and separator updates automatically. This technique is the recommended way to **update footnote style** in large‑scale publishing workflows.

## Modify footnote separator to match your branding

Brand guidelines sometimes dictate that the footnote separator use a specific character (e.g., an asterisk) or a custom line. Aspose.Words allows you to replace the default separator content entirely.

```java
// Remove existing runs
footnoteSeparator.getRuns().clear();

// Insert a custom separator line
Run customRun = new Run(doc);
customRun.setText("--- Custom Separator ---");
Font customFont = customRun.getFont();
customFont.setBold(true);
customFont.setSize(8);
customFont.setColor(java.awt.Color.BLUE);
footnoteSeparator.appendChild(customRun);
```

The code above **modifies footnote separator** by clearing any existing runs and inserting a new run with the desired text and formatting. You can also use Unicode characters such as `\u2022` (bullet) or `\u2014` (em dash) to achieve the exact visual effect required by your brand.

## Expected result

After running the program:

* The footnote separator in `output.docx` appears **bold**, **italic**, 10 pt, and gray (or whatever color you set).  
* All footnote paragraphs adopt the style you defined, ensuring a uniform look throughout the document.  
* If you replaced the separator text, the new custom line is visible exactly where the original line used to be.

Open the resulting file in Microsoft Word or LibreOffice Writer to verify the changes. You should see the updated separator right above the first footnote, and the footnote text should reflect any style modifications you applied.

## Common pitfalls and how to avoid them

| Issue | Why it happens | Fix |
|-------|----------------|-----|
| `footnoteSeparator.getRuns().getCount() == 0` throws an exception | Some documents have an empty separator paragraph. | Add a defensive check and create a run if none exist (see the code example). |
| Font changes are not visible | The document uses a theme that overrides direct formatting. | Set `font.setThemeFont(null)` or apply a custom style instead of direct formatting. |
| Saved file does not reflect changes | The original file is still open in Word, locking the output path. | Close any instances of the file before running the program, or


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Words Processing with Footnote and Endnote](/words/english/net/working-with-footnote-and-endnote/)
- [Set Footnote And End Note Position](/words/english/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [How to Display Aspose.Words Version Info in Java: A Comprehensive Guide](/words/english/java/getting-started/aspose-words-java-version-info/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}