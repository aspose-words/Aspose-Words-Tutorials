---
title: Using Revisions in Aspose.Words for Java
linktitle: Using Revisions
second_title: Aspose.Words Java Document Processing API
description: Learn to use Aspose.Words for Java's revision efficiently. Step-by-step guide for developers. Optimize your document management.
weight: 22
url: /java/using-document-elements/using-revisions/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Using Revisions in Aspose.Words for Java


If you're a Java developer looking to work with documents and need to implement revision controls, Aspose.Words for Java provides a powerful set of tools to help you manage revisions effectively. In this tutorial, we'll guide you through using revision in Aspose.Words for Java step by step. 

## 1. Introduction to Aspose.Words for Java

Aspose.Words for Java is a robust Java API that allows you to create, modify, and manipulate Word documents without the need for Microsoft Word. It's particularly useful when you need to implement revision within your documents.

## 2. Setting Up Your Development Environment

Before we dive into using Aspose.Words for Java, you need to set up your development environment. Ensure you have the necessary Java development tools and the Aspose.Words for Java library installed.

## 3. Creating a New Document

Let's start by creating a new Word document using Aspose.Words for Java. Here's how you can do it:

```java
string outPath = "Your Output Directory";
Document doc = new Document();
Body body = doc.getFirstSection().getBody();
Paragraph para = body.getFirstParagraph();
```

## 4. Adding Content to the Document

Now that you have a blank document, you can add content to it. In this example, we'll add three paragraphs:

```java
para.appendChild(new Run(doc, "Paragraph 1. "));
body.appendParagraph("Paragraph 2. ");
body.appendParagraph("Paragraph 3. ");
```

## 5. Starting Revision Tracking

To track revisions in your document, you can use the following code:

```java
doc.startTrackRevisions("John Doe", new Date());
```

## 6. Making Revisions

Let's make a revision by adding another paragraph:

```java
para = body.appendParagraph("Paragraph 4. ");
```

## 7. Accepting and Rejecting Revisions

You can accept or reject revisions in your document using Aspose.Words for Java. Revisions can be easily managed in Microsoft Word after the document is generated.

## 8. Stopping Revision Tracking

To stop tracking revisions, use the following code:

```java
doc.stopTrackRevisions();
```

## 9. Saving the Document

Finally, save your document:

```java
doc.save(outPath + "WorkingWithRevisions.AcceptRevisions.docx");
```

## 10. Conclusion

In this tutorial, we've covered the basics of using revision in Aspose.Words for Java. You've learned how to create a document, add content, start and stop revision tracking, and save your document.

Now you have the tools you need to effectively manage revisions in your Java applications using Aspose.Words for Java.

## Complete Source Code
```java
string outPath = "Your Output Directory";
Document doc = new Document();
Body body = doc.getFirstSection().getBody();
Paragraph para = body.getFirstParagraph();
// Add text to the first paragraph, then add two more paragraphs.
para.appendChild(new Run(doc, "Paragraph 1. "));
body.appendParagraph("Paragraph 2. ");
body.appendParagraph("Paragraph 3. ");
// We have three paragraphs, none of which registered as any type of revision
// If we add/remove any content in the document while tracking revisions,
// they will be displayed as such in the document and can be accepted/rejected.
doc.startTrackRevisions("John Doe", new Date());
// This paragraph is a revision and will have the according "IsInsertRevision" flag set.
para = body.appendParagraph("Paragraph 4. ");
Assert.assertTrue(para.isInsertRevision());
// Get the document's paragraph collection and remove a paragraph.
ParagraphCollection paragraphs = body.getParagraphs();
Assert.assertEquals(4, paragraphs.getCount());
para = paragraphs.get(2);
para.remove();
// Since we are tracking revisions, the paragraph still exists in the document, will have the "IsDeleteRevision" set
// and will be displayed as a revision in Microsoft Word, until we accept or reject all revisions.
Assert.assertEquals(4, paragraphs.getCount());
Assert.assertTrue(para.isDeleteRevision());
// The delete revision paragraph is removed once we accept changes.
doc.acceptAllRevisions();
Assert.assertEquals(3, paragraphs.getCount());
Assert.assertEquals(para.getRuns().getCount(), 0); //was Is.Empty
// Stopping the tracking of revisions makes this text appear as normal text.
// Revisions are not counted when the document is changed.
doc.stopTrackRevisions();
// Save the document.
doc.save(outPath + "WorkingWithRevisions.AcceptRevisions.docx");
  
```

## FAQs

### 1. Can I use Aspose.Words for Java with other programming languages?

No, Aspose.Words for Java is specifically designed for Java development.

### 2. Is Aspose.Words for Java compatible with all versions of Microsoft Word?

Yes, Aspose.Words for Java is designed to be compatible with various versions of Microsoft Word.

### 3. Can I track revisions in existing Word documents?

Yes, you can use Aspose.Words for Java to track revisions in existing Word documents.

### 4. Are there any licensing requirements for using Aspose.Words for Java?

Yes, you'll need to acquire a license to use Aspose.Words for Java in your projects. You can [get access to a license here](https://purchase.aspose.com/buy).

### 5. Where can I find support for Aspose.Words for Java?

For any questions or issues, you can visit the [Aspose.Words for Java support forum](https://forum.aspose.com/).

Get started with Aspose.Words for Java today and streamline your document management processes.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
