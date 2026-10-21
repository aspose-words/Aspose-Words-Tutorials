---
category: general
date: 2026-10-04
description: Edit footnote separator in Java using Aspose.Words – learn how to change
  footnote separator and add a custom separator word to Word documents.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- edit footnote separator
- change footnote separator
- custom separator word
language: en
lastmod: 2026-10-04
og_description: Edit footnote separator in Java with Aspose.Words. This tutorial shows
  how to change footnote separator and insert a custom separator word.
og_image_alt: Screenshot of a Java IDE showing code that edits a footnote separator
  in a Word document
og_title: Edit footnote separator in Java – complete Aspose.Words guide
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Edit footnote separator in Java using Aspose.Words – learn how to change
    footnote separator and add a custom separator word to Word documents.
  headline: How to edit footnote separator in Java with Aspose.Words
  type: TechArticle
- description: Edit footnote separator in Java using Aspose.Words – learn how to change
    footnote separator and add a custom separator word to Word documents.
  name: How to edit footnote separator in Java with Aspose.Words
  steps:
  - name: '**`clearChildren()`** removes any existing runs, ensuring the separator
      contains only the text you provide.'
    text: '**`clearChildren()`** removes any existing runs, ensuring the separator
      contains only the text you provide.'
  - name: '**`new Run(document, "—")`** creates a text node with the desired separator.
      The `Run` object respects the document’s style, so the separator inherits the
      formatting of the original footnote separator.'
    text: '**`new Run(document, "—")`** creates a text node with the desired separator.
      The `Run` object respects the document’s style, so the separator inherits the
      formatting of the original footnote separator.'
  - name: '**`appendChild(customRun)`** inserts the new run into the separator paragraph.'
    text: '**`appendChild(customRun)`** inserts the new run into the separator paragraph.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Footnotes
- Word processing
title: How to edit footnote separator in Java with Aspose.Words
url: /java/document-styling/how-to-edit-footnote-separator-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to edit footnote separator in Java with Aspose.Words

If you need to **edit footnote separator** in a Word document, this guide shows you exactly how to do it in Java. Whether you want to **change footnote separator** to a dash, a star, or any **custom separator word**, the steps below cover everything you need.

You’ll learn how to load a `.docx` file, retrieve the special separator section, modify its content, and save the result. No external scripts or manual editing required – everything is done programmatically with the Aspose.Words for Java library.

## Prerequisites

Before you start, make sure you have:

- Java 17 or later installed.
- Maven or Gradle to manage dependencies (the example uses Maven).
- A valid Aspose.Words for Java license (or a free evaluation key).
- A Word document that already contains footnotes (the separator exists only when footnotes are present).

## Add Aspose.Words to your project

If you use Maven, add the following dependency to your `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.11</version> <!-- Use the latest version -->
</dependency>
```

For Gradle, add:

```gradle
implementation 'com.aspose:aspose-words:24.11'
```

## Step 1: Load the document that contains footnotes

The first step is to open the Word file you want to modify. Aspose.Words reads the file into a `Document` object, which gives you full access to all parts of the document, including footnote separators.

```java
import com.aspose.words.*;

public class EditFootnoteSeparator {
    public static void main(String[] args) throws Exception {
        // Path to the source document
        String inputPath = "YOUR_DIRECTORY/docWithNotes.docx";

        // Load the document
        Document document = new Document(inputPath);
        
        // Continue with separator editing...
    }
}
```

**Why this matters:** Loading the document creates an in‑memory representation, so you can safely modify any node without touching the original file until you explicitly save it.

## Step 2: Retrieve the footnote separator section

Word stores the footnote separator as a special `Separator` node. Aspose.Words provides the `getFootnoteSeparator()` method to obtain it directly.

```java
// Get the footnote separator (the line that appears between footnotes and the main text)
Separator footnoteSeparator = document.getFootnoteSeparator();

if (footnoteSeparator == null) {
    System.out.println("The document does not contain a footnote separator.");
    return;
}
```

**Pro tip:** The separator node exists only if the document already has at least one footnote. If you try to edit a document without footnotes, `getFootnoteSeparator()` returns `null`, so always check for this condition.

## Step 3: Insert a custom separator word

Now you can change the separator’s appearance. In this example we replace the default line with an em dash (`—`). You could instead insert any **custom separator word** such as `"NOTE:"` or `"***"`.

```java
// Access the first paragraph of the separator (there is usually only one)
Paragraph separatorParagraph = footnoteSeparator.getParagraphs().get(0);

// Clear any existing runs (text fragments) to avoid mixing old and new content
separatorParagraph.clearChildren();

// Append a new Run that contains the custom separator word
Run customRun = new Run(document, "—");   // Replace "—" with any text you need
separatorParagraph.appendChild(customRun);
```

### What the code does

1. **`clearChildren()`** removes any existing runs, ensuring the separator contains only the text you provide.
2. **`new Run(document, "—")`** creates a text node with the desired separator. The `Run` object respects the document’s style, so the separator inherits the formatting of the original footnote separator.
3. **`appendChild(customRun)`** inserts the new run into the separator paragraph.

You can also apply formatting to the run, for example:

```java
customRun.getFont().setBold(true);
customRun.getFont().setSize(10);
customRun.getFont().setColor(Color.BLUE);
```

## Step 4: Save the modified document

After editing the separator, write the document back to disk. Choose a new file name to keep the original file untouched.

```java
// Path to the output document
String outputPath = "YOUR_DIRECTORY/ModifiedNotes.docx";

// Save the changes
document.save(outputPath);

System.out.println("Footnote separator edited successfully. Saved to " + outputPath);
```

**Result verification:** Open `ModifiedNotes.docx` in Microsoft Word. The footnote separator should now display the custom dash (or whatever word you chose) instead of the default line.

## Handling multiple footnote separators

Word supports three special separator types:

| Separator type | Method                     |
|----------------|----------------------------|
| Footnote separator | `getFootnoteSeparator()` |
| Footnote continuation separator | `getFootnoteContinuationSeparator()` |
| Footnote separator for the first page | `getFootnoteSeparatorForFirstPage()` |

If you need to edit all of them, repeat **Step 2** and **Step 3** for each method. Example:

```java
Separator continuation = document.getFootnoteContinuationSeparator();
if (continuation != null) {
    // Apply the same custom run or a different one
    Paragraph p = continuation.getParagraphs().get(0);
    p.clearChildren();
    p.appendChild(new Run(document, "*"));
}
```

## Common pitfalls and how to avoid them

| Issue | Cause | Fix |
|-------|-------|-----|
| No separator appears after saving | Document had no footnotes → separator node is `null` | Add at least one footnote before editing, or create a dummy footnote programmatically. |
| Separator shows extra spaces | Existing runs were not cleared | Call `clearChildren()` before appending the new run. |
| Formatting looks different | Run inherits style from the original separator | Explicitly set font properties on the `Run` if you need a specific appearance. |

## Full working example

Putting all pieces together, here’s a self‑contained Java class you can copy, compile, and run:

```java
import com.aspose.words.*;
import java.awt.Color;

public class EditFootnoteSeparator {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the document
        String inputPath = "YOUR_DIRECTORY/docWithNotes.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Retrieve the footnote separator
        Separator footnoteSeparator = doc.getFootnoteSeparator();
        if (footnoteSeparator == null) {
            System.out.println("Document has no footnote separator.");
            return;
        }

        // 3️⃣ Replace the separator with a custom word (e.g., an em dash)
        Paragraph para = footnoteSeparator.getParagraphs().get(0);
        para.clearChildren();                       // Remove old runs
        Run customRun = new Run(doc, "—");          // Change "—" to any word you need
        customRun.getFont().setBold(true);         // Optional styling
        customRun.getFont().setSize(9);
        customRun.getFont().setColor(Color.DARK_GRAY);
        para.appendChild(customRun);

        // 4️⃣ Save the modified document
        String outputPath = "YOUR_DIRECTORY/ModifiedNotes.docx";
        doc.save(outputPath);

        System.out.println("Footnote separator edited successfully.");
    }
}
```

Run the program, then open `ModifiedNotes.docx` to confirm the separator has been updated.

## Conclusion

You now know how to **edit footnote separator** in a Word document using Java and Aspose.Words. The tutorial covered loading a document, retrieving the special separator node, inserting a **custom separator word**, and saving the result. By following these steps you can also **change footnote separator** for continuation sections or first‑page footnotes.

Next, you might explore:

- Adding different separators for first‑page footnotes (`getFootnoteSeparatorForFirstPage()`).
- Programmatically creating footnotes when none exist.
- Using Aspose.Words to style footnote text (fonts, colors, indentation).

Feel free to experiment with other characters or words to match your document’s branding. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Insert Document Style Separator in Word](/words/english/net/programming-with-styles-and-themes/insert-style-separator/)
- [Get Paragraph Style Separator In Word Document](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [How to Load Word Documents with Aspose.Words Java: Comprehensive Guide](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}