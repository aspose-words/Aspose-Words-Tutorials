---
title: Using Headers and Footers in Aspose.Words for Java
linktitle: Using Headers and Footers
second_title: Aspose.Words Java Document Processing API
description: Learn step-by-step how to use headers and footers in Aspose.Words for Java. Create professional documents effortlessly.
weight: 16
url: /java/using-document-elements/using-headers-and-footers/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Using Headers and Footers in Aspose.Words for Java


In this comprehensive guide, we will walk you through the process of working with headers and footers in Aspose.Words for Java. Headers and footers are essential elements in document formatting, and Aspose.Words provides powerful tools to create and customize them according to your needs.

Now, let's dive into each of these steps in detail.

## 1. Introduction to Aspose.Words

Aspose.Words is a powerful Java API that allows you to create, manipulate, and render Word documents programmatically. It provides extensive features for document formatting, including headers and footers.

## 2. Setting Up Your Java Environment

Before you start using Aspose.Words, make sure you have your Java development environment set up correctly. You can find the necessary setup instructions on the Aspose.Words documentation page: [Aspose.Words Java Documentation](https://reference.aspose.com/words/java/).

## 3. Creating a New Document

To work with headers and footers, you need to create a new document using Aspose.Words. The following code demonstrates how to do this:

```java
// Java code for creating a new document
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 4. Understanding Page Setup

Page setup is crucial for controlling the layout of your document. You can specify various properties related to headers and footers using the `PageSetup` class. For example:

```java
// Setting up page properties
Section currentSection = builder.getCurrentSection();
PageSetup pageSetup = currentSection.getPageSetup();
pageSetup.setDifferentFirstPageHeaderFooter(true);
pageSetup.setHeaderDistance(20.0);
```

## 5. Different First Page Header/Footer

Aspose.Words allows you to have different headers and footers for the first page of your document. Use `pageSetup.setDifferentFirstPageHeaderFooter(true);` to enable this feature.

## 6. Working with Headers

### 6.1. Adding Text to Headers

You can add text to headers using the `DocumentBuilder`. Here's an example:

```java
// Adding text to the first-page header
builder.moveToHeaderFooter(HeaderFooterType.HEADER_FIRST);
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.getFont().setName("Arial");
builder.getFont().setBold(true);
builder.getFont().setSize(14.0);
builder.write("Aspose.Words Header/Footer Creation Primer - Title Page.");
```

### 6.2. Inserting Images into Headers

To insert images into headers, you can use the `insertImage` method. Here's an example:

```java
// Inserting an image into the header
builder.insertImage(getImagesDir() + "Graphics Interchange Format.gif", RelativeHorizontalPosition.PAGE, 10.0,
    RelativeVerticalPosition.PAGE, 10.0, 50.0, 50.0, WrapType.THROUGH);
```

### 6.3. Customizing Header Styles

You can customize header styles by setting various properties such as font, alignment, and more, as shown in the examples above.

## 7. Working with Footers

### 7.1. Adding Text to Footers

Similar to headers, you can add text to footers using the `DocumentBuilder`. Here's an example:

```java
// Adding text to the primary footer
builder.moveToHeaderFooter(HeaderFooterType.FOOTER_PRIMARY);
// Insert text and fields as needed
```

### 7.2. Inserting Images into Footers

To insert images into footers, use the `insertImage` method, just like in headers.

### 7.3. Customizing Footer Styles

Customize footer styles using the `DocumentBuilder`, similar to customizing headers.

## 8. Page Numbering

You can include page numbers in your headers and footers using fields like `PAGE` and `NUMPAGES`. These fields automatically update as you add or remove pages.

## 9. Copyright Information in Footers

To add copyright information to your document's footer, you can use a table with two cells, aligning one to the left and the other to the right, as shown in the code snippet.

## 10. Working with Multiple Sections

Aspose.Words allows you to work with multiple sections within a document. You can set different page setups and headers/footers for each section.

## 11. Landscape Orientation

You can change the orientation of specific sections to landscape mode if needed.

## 12. Copying Headers/Footers from Previous Sections

Copying headers and footers from previous sections can save time when creating complex documents.

## 13. Saving Your Document

After creating and customizing your document, don't forget to save it using the `doc.save()` method.

## Complete Source Code
```java
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        Section currentSection = builder.getCurrentSection();
        PageSetup pageSetup = currentSection.getPageSetup();
        // Specify if we want headers/footers of the first page to be different from other pages.
        // You can also use PageSetup.OddAndEvenPagesHeaderFooter property to specify
        // different headers/footers for odd and even pages.
        pageSetup.setDifferentFirstPageHeaderFooter(true);
        pageSetup.setHeaderDistance(20.0);
        builder.moveToHeaderFooter(HeaderFooterType.HEADER_FIRST);
        builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
        builder.getFont().setName("Arial");
        builder.getFont().setBold(true);
        builder.getFont().setSize(14.0);
        builder.write("Aspose.Words Header/Footer Creation Primer - Title Page.");
        pageSetup.setHeaderDistance(20.0);
        builder.moveToHeaderFooter(HeaderFooterType.HEADER_PRIMARY);
        // Insert a positioned image into the top/left corner of the header.
        // Distance from the top/left edges of the page is set to 10 points.
        builder.insertImage(getImagesDir() + "Graphics Interchange Format.gif", RelativeHorizontalPosition.PAGE, 10.0,
            RelativeVerticalPosition.PAGE, 10.0, 50.0, 50.0, WrapType.THROUGH);
        builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
        builder.write("Aspose.Words Header/Footer Creation Primer.");
        builder.moveToHeaderFooter(HeaderFooterType.FOOTER_PRIMARY);
        // We use a table with two cells to make one part of the text on the line (with page numbering).
        // To be aligned left, and the other part of the text (with copyright) to be aligned right.
        builder.startTable();
        builder.getCellFormat().clearFormatting();
        builder.insertCell();
        builder.getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 / 3));
        // It uses PAGE and NUMPAGES fields to auto calculate the current page number and many pages.
        builder.write("Page ");
        builder.insertField("PAGE", "");
        builder.write(" of ");
        builder.insertField("NUMPAGES", "");
        builder.getCurrentParagraph().getParagraphFormat().setAlignment(ParagraphAlignment.LEFT);
        builder.insertCell();
        builder.getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 * 2 / 3));
        builder.write("(C) 2001 Aspose Pty Ltd. All rights reserved.");
        builder.getCurrentParagraph().getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
        builder.endRow();
        builder.endTable();
        builder.moveToDocumentEnd();
        // Make a page break to create a second page on which the primary headers/footers will be seen.
        builder.insertBreak(BreakType.PAGE_BREAK);
        builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
        currentSection = builder.getCurrentSection();
        pageSetup = currentSection.getPageSetup();
        pageSetup.setOrientation(Orientation.LANDSCAPE);
        // This section does not need a different first-page header/footer we need only one title page in the document,
        // and the header/footer for this page has already been defined in the previous section.
        pageSetup.setDifferentFirstPageHeaderFooter(false);
        // This section displays headers/footers from the previous section
        // by default call currentSection.HeadersFooters.LinkToPrevious(false) to cancel this page width
        // is different for the new section, and therefore we need to set different cell widths for a footer table.
        currentSection.getHeadersFooters().linkToPrevious(false);
        // If we want to use the already existing header/footer set for this section.
        // But with some minor modifications, then it may be expedient to copy headers/footers
        // from the previous section and apply the necessary modifications where we want them.
        copyHeadersFootersFromPreviousSection(currentSection);
        HeaderFooter primaryFooter = currentSection.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);
        Row row = primaryFooter.getTables().get(0).getFirstRow();
        row.getFirstCell().getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 / 3));
        row.getLastCell().getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 * 2 / 3));
        doc.save("Your Directory Path" + "WorkingWithHeadersAndFooters.CreateHeaderFooter.docx");
```	
Source code of copyHeadersFootersFromPreviousSection method
```java
    /// <summary>
    /// Clones and copies headers/footers form the previous section to the specified section.
    /// </summary>
    private void copyHeadersFootersFromPreviousSection(Section section)
    {
        Section previousSection = (Section)section.getPreviousSibling();
        if (previousSection == null)
            return;
        section.getHeadersFooters().clear();
        for (HeaderFooter headerFooter : (Iterable<HeaderFooter>) previousSection.getHeadersFooters())
            section.getHeadersFooters().add(headerFooter.deepClone(true));
	}
```

## Conclusion

In this tutorial, we've covered the basics of working with headers and footers in Aspose.Words for Java. You've learned how to create, customize, and style headers and footers, as well as other essential document formatting techniques.

For further details and advanced features, refer to the [Aspose.Words Java Documentation](https://reference.aspose.com/words/java/).

## FAQs

### 1. How can I add page numbers to my document's footer?
You can add page numbers by inserting the `PAGE` field into the footer using Aspose.Words.

### 2. Is Aspose.Words compatible with Java development environments?
Yes, Aspose.Words provides support for Java development. Ensure you have the necessary setup in place.

### 3. Can I customize the font and style of headers and footers?
Absolutely, you can customize fonts, alignment, and other styles to make your headers and footers visually appealing.

### 4. Is it possible to have different headers for odd and even pages?
Yes, you can use `PageSetup.OddAndEvenPagesHeaderFooter` to specify different headers for odd and even pages.

### 5. How do I get started with Aspose.Words for Java?
To begin, visit the [Aspose.Words Java Documentation](https://reference.aspose.com/words/java/) for comprehensive guidance on using the API.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
